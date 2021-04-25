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
# <a name="chapter-3---description-of-azure-rtos-netx-duo-dns-client-services"></a><span data-ttu-id="39e56-103">第 3 章 - Azure RTOS NetX Duo DNS クライアント サービスの説明</span><span class="sxs-lookup"><span data-stu-id="39e56-103">Chapter 3 - Description of Azure RTOS NetX Duo DNS Client Services</span></span>

<span data-ttu-id="39e56-104">この章では、すべての Azure RTOS NetX DNS サービス (以下に記載) をアルファベット順に説明します。</span><span class="sxs-lookup"><span data-stu-id="39e56-104">This chapter contains a description of all Azure RTOS NetX DNS services (listed below) in alphabetic order.</span></span>

<span data-ttu-id="39e56-105">以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。</span><span class="sxs-lookup"><span data-stu-id="39e56-105">In the “Return Values” section in the following API descriptions, values in **BOLD** are not affected by the **NX_DISABLE_ERROR_CHECKING** define that is used to disable API error checking, while non-bold values are completely disabled.</span></span>

- <span data-ttu-id="39e56-106">**nx_dns_authority_zone_start_get** *指定されたホスト名に関連付けられている権限のゾーンの開始を検索します。*</span><span class="sxs-lookup"><span data-stu-id="39e56-106">**nx_dns_authority_zone_start_get** *Look up the start of a zone of authority associated with the specified host name*</span></span>

- <span data-ttu-id="39e56-107">**nx_dns_cache_initialize** *DNS キャッシュを初期化します。*</span><span class="sxs-lookup"><span data-stu-id="39e56-107">**nx_dns_cache_initialize** *Initialize a DNS Cache.*</span></span>

- <span data-ttu-id="39e56-108">**nx_dns_cache_notify_clear** *キャッシュの完全な通知機能をクリアします。*</span><span class="sxs-lookup"><span data-stu-id="39e56-108">**nx_dns_cache_notify_clear** *Clear the cache full notify function.*</span></span>

- <span data-ttu-id="39e56-109">**nx_dns_cache_notify_set** *キャッシュの完全な通知機能を設定します。*</span><span class="sxs-lookup"><span data-stu-id="39e56-109">**nx_dns_cache_notify_set** *Set the cache full notify function.*</span></span>

- <span data-ttu-id="39e56-110">**nx_dns_cname_get** *入力ドメイン名の別名の正規のドメイン名を検索します*</span><span class="sxs-lookup"><span data-stu-id="39e56-110">**nx_dns_cname_get** *Look up the canonical domain name for the input domain name alias*</span></span>

- <span data-ttu-id="39e56-111">**nx_dns_create** *DNS クライアント インスタンスを作成します*</span><span class="sxs-lookup"><span data-stu-id="39e56-111">**nx_dns_create** *Create a DNS Client instance*</span></span>

- <span data-ttu-id="39e56-112">**nx_dns_delete** *DNS クライアント インスタンスを削除します*</span><span class="sxs-lookup"><span data-stu-id="39e56-112">**nx_dns_delete** *Delete a DNS Client instance*</span></span>

- <span data-ttu-id="39e56-113">**nx_dns_domain_name_server_get** *入力ドメイン ゾーンの権限のあるネーム サーバーを検索します*</span><span class="sxs-lookup"><span data-stu-id="39e56-113">**nx_dns_domain_name_server_get** *Look up the authoritative name servers for the input domain zone*</span></span>

- <span data-ttu-id="39e56-114">**nx_dns_domain_mail_exchange_get** *指定したホスト名に関連付けられているメール交換を検索します。*</span><span class="sxs-lookup"><span data-stu-id="39e56-114">**nx_dns_domain_mail_exchange_get** *Look up the mail exchange associated the specified host name.*</span></span>

- <span data-ttu-id="39e56-115">**nx_dns_domain_service_get** *指定したホスト名に関連付けられているサービスを検索します*</span><span class="sxs-lookup"><span data-stu-id="39e56-115">**nx_dns_domain_service_get** *Look up the service(s) associated with the specified host name*</span></span>

- <span data-ttu-id="39e56-116">**nx_dns_get_serverlist_size** *DNS クライアント サーバ リストのサイズを返します*</span><span class="sxs-lookup"><span data-stu-id="39e56-116">**nx_dns_get_serverlist_size** *Return the size of the DNS Client server list*</span></span>

- <span data-ttu-id="39e56-117">**nx_dns_info_by_name_get** *入力ホスト名に対してクエリを実行し、IP アドレス、ポートを返します*</span><span class="sxs-lookup"><span data-stu-id="39e56-117">**nx_dns_info_by_name_get** *Return IP address, port querying on input host name*</span></span>

- <span data-ttu-id="39e56-118">**nx_dns_ipv4_address_by_name_get** *指定したホスト名から IPv4 アドレスを検索します*</span><span class="sxs-lookup"><span data-stu-id="39e56-118">**nx_dns_ipv4_address_by_name_get** *Look up the IPv4 address from the specified host name*</span></span>

- <span data-ttu-id="39e56-119">**nxd_dns_ipv6_address_by_name_get** *指定したホスト名から IPv6 アドレスを検索します*</span><span class="sxs-lookup"><span data-stu-id="39e56-119">**nxd_dns_ipv6_address_by_name_get** *Look up the IPv6 address from the specified host name*</span></span>

- <span data-ttu-id="39e56-120">**nx_dns_host_by_address_get** *指定した IP アドレスからホスト名を検索するための nxd_dns_host_by_address_get のラッパー関数 (IPv4 アドレスのみをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-120">**nx_dns_host_by_address_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from a specified IP address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="39e56-121">**nxd_dns_host_by_address_get** *入力ホスト名から IP アドレスを検索します (IPv4 と IPv6 の両方のアドレスをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-121">**nxd_dns_host_by_address_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="39e56-122">**nx_dns_host_by_name_get** *指定したアドレスからホスト名を検索するための nxd_dns_host_by_address_get のラッパー関数 (IPv4 アドレスのみをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-122">**nx_dns_host_by_name_get** *Wrapper function for nxd_dns_host_by_address_get to look up a host name from the specified address (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="39e56-123">**nxd_dns_host_by_name_get** *入力ホスト名から IP アドレスを検索します (IPv4 と IPv6 の両方のアドレスをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-123">**nxd_dns_host_by_name_get** *Look up an IP address from the input host name (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="39e56-124">**nx_dns_host_text_get** *入力ドメイン名からテキスト データを検索します*</span><span class="sxs-lookup"><span data-stu-id="39e56-124">**nx_dns_host_text_get** *Look up the text data for the input domain name*</span></span>

- <span data-ttu-id="39e56-125">**nx_dns_packet_pool_set** *DNS クライアント パケット プールを設定します*</span><span class="sxs-lookup"><span data-stu-id="39e56-125">**nx_dns_packet_pool_set** *Set the DNS Client packet pool*</span></span>

- <span data-ttu-id="39e56-126">**nx_dns_server_add** *指定したアドレスでクライアント リストに DNS サーバーを追加するための*  nxd_dns_server_add  *のラッパー関数 (IPv4 のみをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-126">**nx_dns_server_add** *Wrapper function for* nxd_dns_server_add *to add a DNS Server at the specified address to the Client list (supports only IPv4)*</span></span>

- <span data-ttu-id="39e56-127">**nxd_dns_server_add** *指定した IP アドレスの DNS サーバーをクライアント サーバー リストに追加します (IPv4 と IPv6 の両方のアドレスをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-127">**nxd_dns_server_add** *Add a DNS Server of the specified IP address to the Client server list (supports both IPv4 or IPv6 addresses)*</span></span>

- <span data-ttu-id="39e56-128">**nx_dns_server_get** *クライアント リストで DNS サーバーを返します (IPv4 アドレスのみをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-128">**nx_dns_server_get** *Return the DNS Server in the Client list (supports only IPv4 addresses)*</span></span>

- <span data-ttu-id="39e56-129">**nx_dns_server_get** *クライアント リストで DNS サーバーを返します (IPv4 と IPv6 の両方のアドレスのみをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-129">**nxd_dns_server_get** *Return the DNS Server in the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="39e56-130">**nx_dns_server_remove** *クライアント リストから DNS サーバーを削除するための nxd_dns_server_remove のラッパー関数*</span><span class="sxs-lookup"><span data-stu-id="39e56-130">**nx_dns_server_remove** *Wrapper function for nxd_dns_server_remove to remove a DNS Server from the Client list*</span></span>

- <span data-ttu-id="39e56-131">**nxd_dns_server_remove** *指定した IP アドレスの DNS サーバーをクライアント リストから削除します (IPv4 と IPv6 の両方のアドレスをサポートします)*</span><span class="sxs-lookup"><span data-stu-id="39e56-131">**nxd_dns_server_remove** *Remove a DNS Server of the specified IP address from the Client list (supports both IPv4 and IPv6 addresses)*</span></span>

- <span data-ttu-id="39e56-132">**nx_dns_server_remove_all** *クライアント リストからすべての DNS サーバーを削除します*</span><span class="sxs-lookup"><span data-stu-id="39e56-132">**nx_dns_server_remove_all** *Remove all DNS Servers from the Client list*</span></span>

## <a name="nx_dns_authority_zone_start_get"></a><span data-ttu-id="39e56-133">nx_dns_authority_zone_start_get</span><span class="sxs-lookup"><span data-stu-id="39e56-133">nx_dns_authority_zone_start_get</span></span>

<span data-ttu-id="39e56-134">入力ホストの権限のゾーンの開始を検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-134">Look up the start of the zone of authority for the input host</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-135">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-135">Prototype</span></span>
```C
UINT nx_dns_authority_zone_start_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                      VOID *record_buffer,                                        
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```
### <a name="description"></a><span data-ttu-id="39e56-136">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-136">Description</span></span>

<span data-ttu-id="39e56-137">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名の SOA 型のクエリが送信され、入力ドメイン名の権限のゾーンの開始が取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-137">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SOA with the specified domain name to obtain the start of the zone of authority for the input domain name.</span></span> <span data-ttu-id="39e56-138">DNS クライアントによって、DNS サーバーの応答で返された SOA レコードが *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-138">The DNS Client copies the SOA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="39e56-139">データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-139">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="39e56-140">NetX Duo DNS クライアントでは、SOA レコードの種類 NX_DNS_SOA_ENTRY が 7 個の 4 バイトのパラメーター (合計 28 バイト) として保存されます</span><span class="sxs-lookup"><span data-stu-id="39e56-140">In NetX Duo DNS Client, the SOA record type, NX_DNS_SOA_ENTRY, is saved as seven 4 byte parameters, totaling 28 bytes:</span></span>

- <span data-ttu-id="39e56-141">**nx_dns_soa_host_mname_ptr** このゾーンのデータのプライマリ ソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-141">**nx_dns_soa_host_mname_ptr** Pointer to primary source of data for this zone.</span></span>
- <span data-ttu-id="39e56-142">**nx_dns_soa_host_rname_ptr** このゾーンを処理するメールボックスへのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-142">**nx_dns_soa_host_rname_ptr** Pointer to mailbox responsible for this zone</span></span>
- <span data-ttu-id="39e56-143">**nx_dns_soa_serial** ゾーンのバージョン番号</span><span class="sxs-lookup"><span data-stu-id="39e56-143">**nx_dns_soa_serial** Zone version number</span></span>
- <span data-ttu-id="39e56-144">**nx_dns_soa_refresh** 更新間隔</span><span class="sxs-lookup"><span data-stu-id="39e56-144">**nx_dns_soa_refresh** Refresh interval</span></span>
- <span data-ttu-id="39e56-145">**nx_dns_soa_retry** SOA クエリ再試行の間隔</span><span class="sxs-lookup"><span data-stu-id="39e56-145">**nx_dns_soa_retry** Interval between SOA query retries</span></span>
- <span data-ttu-id="39e56-146">**nx_dns_soa_expire** SOA の有効期限が切れるまでの期間</span><span class="sxs-lookup"><span data-stu-id="39e56-146">**nx_dns_soa_expire** Time duration when SOA expires</span></span>
- <span data-ttu-id="39e56-147">**nx_dns_soa_minmum** SOA ホスト名 DNS 応答メッセージの最小 TTL フィールド</span><span class="sxs-lookup"><span data-stu-id="39e56-147">**nx_dns_soa_minmum** Minimum TTL field in SOA hostname DNS reply messages</span></span>

<span data-ttu-id="39e56-148">2 つの SOA レコードのストレージは次のようになります。</span><span class="sxs-lookup"><span data-stu-id="39e56-148">The storage of a two SOA records is shown below.</span></span> <span data-ttu-id="39e56-149">固定長データを含む SOA レコードは、バッファーの先頭から入力を開始されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-149">The SOA records containing fixed length data are entered starting at the top of the buffer.</span></span> <span data-ttu-id="39e56-150">ポインター MNAME および RNAME は、バッファーの末尾に格納されている可変長データ (ホスト名) を指します。</span><span class="sxs-lookup"><span data-stu-id="39e56-150">The pointers MNAME and RNAME point to the variable length data (host names) which are stored at the bottom of the buffer.</span></span> <span data-ttu-id="39e56-151">最初のレコードの後に追加の SOA レコードが入力され (“additional SOA records…”)、その可変長データが最後のエントリの可変長データの上に格納されます (“additional SOA variable length data”)</span><span class="sxs-lookup"><span data-stu-id="39e56-151">Additional SOA records are entered after the first record (“additional SOA records…”) and their variable length data is stored above the last entry’s variable length data (“additional SOA variable length data”):</span></span>

![2 つの SOA レコードのストレージ](media/image4.png)

<span data-ttu-id="39e56-153">入力 *record_buffer* にサーバー応答内のすべての SOA データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-153">If the input *record_buffer* cannot hold all the SOA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="39e56-154">\**Record_count* で返された SOA レコードの数を使用することで、アプリケーションで *record_buffer* からのデータを解析し、ゾーンの権限ホスト名の文字列の先頭を抽出できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-154">With the number of SOA records returned in \**record_count,* the application can parse the data from *record_buffer* and extract the start of zone authority host name strings.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-155">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-155">Input Parameters</span></span>

- <span data-ttu-id="39e56-156">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-156">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-157">**host_name** SOA データを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-157">**host_name** Pointer to host name to obtain SOA data for</span></span>
- <span data-ttu-id="39e56-158">**record_buffer** SOA データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-158">**record_buffer** Pointer to location to extract SOA data into</span></span>
- <span data-ttu-id="39e56-159">**buffer_size** SOA データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-159">**buffer_size** Size of buffer to hold SOA data</span></span>
- <span data-ttu-id="39e56-160">**record_count** 取得した SOA レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-160">**record_count** Pointer to the number of SOA records retrieved</span></span>
- <span data-ttu-id="39e56-161">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-161">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-162">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-162">Return Values</span></span>

- <span data-ttu-id="39e56-163">**NX_SUCCESS** (0x00): SOA データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-163">**NX_SUCCESS** (0x00) Successfully obtained SOA data</span></span>
- <span data-ttu-id="39e56-164">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-164">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-165">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-165">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-166">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-166">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-167">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-167">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-168">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-168">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-169">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-169">Allowed From</span></span>

<span data-ttu-id="39e56-170">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-170">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-171">例</span><span class="sxs-lookup"><span data-stu-id="39e56-171">Example</span></span>
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

## <a name="nx_dns_cache_initialize"></a><span data-ttu-id="39e56-172">nx_dns_cache_initialize</span><span class="sxs-lookup"><span data-stu-id="39e56-172">nx_dns_cache_initialize</span></span>

<span data-ttu-id="39e56-173">DNS キャッシュを初期化します</span><span class="sxs-lookup"><span data-stu-id="39e56-173">Initialize the DNS Cache</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-174">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-174">Prototype</span></span>
```C
UINT nx_dns_cache_initialize(NX_DNS *dns_ptr,
                            VOID *cache_ptr, UINT cache_size);
```

### <a name="description"></a><span data-ttu-id="39e56-175">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-175">Description</span></span>

<span data-ttu-id="39e56-176">このサービスを使用すると、DNS キャッシュが作成されて初期化されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-176">This service creates and initializes a DNS Cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-177">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-177">Input Parameters</span></span>

- <span data-ttu-id="39e56-178">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-178">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="39e56-179">**cache_ptr** DNS キャッシュへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-179">**cache_ptr** Pointer to DNS Cache.</span></span>
- <span data-ttu-id="39e56-180">**cache_size** DNS キャッシュのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="39e56-180">**cache_size** Size of DNS Cache, in bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-181">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-181">Return Values</span></span>

- <span data-ttu-id="39e56-182">**NX_SUCCESS** (0x00) DNS キャッシュの初期化に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-182">**NX_SUCCESS** (0x00) DNS Cache successfully initialized</span></span>
- <span data-ttu-id="39e56-183">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-183">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="39e56-184">NX_DNS_CACHE_ERROR (0xB7) キャッシュ ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-184">NX_DNS_CACHE_ERROR (0xB7) Invalid Cache pointer.</span></span>
- <span data-ttu-id="39e56-185">NX_PTR_ERROR (0x07) DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-185">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span> 
- <span data-ttu-id="39e56-186">NX_DNS_ERROR (0xA0) キャッシュが 4 バイトで配置されていません。</span><span class="sxs-lookup"><span data-stu-id="39e56-186">NX_DNS_ERROR (0xA0) Cache is not 4-byte aligned.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-187">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-187">Allowed From</span></span>

<span data-ttu-id="39e56-188">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-188">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-189">例</span><span class="sxs-lookup"><span data-stu-id="39e56-189">Example</span></span>
```C
/* Initialize the DNS Cache.  */
status =  nx_dns_cache_initialize(&my_dns, &dns_cache, 2048);

/* If status is NX_SUCCESS DNS Cache was successfully initialized.  */
```

## <a name="nx_dns_cache_notify_clear"></a><span data-ttu-id="39e56-190">nx_dns_cache_notify_clear</span><span class="sxs-lookup"><span data-stu-id="39e56-190">nx_dns_cache_notify_clear</span></span>

<span data-ttu-id="39e56-191">DNS キャッシュの完全な通知機能をクリアします</span><span class="sxs-lookup"><span data-stu-id="39e56-191">Clear the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-192">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-192">Prototype</span></span>
```C
UINT nx_dns_cache_notify_clear(NX_DNS *dns_ptr);
```

### <a name="description"></a><span data-ttu-id="39e56-193">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-193">Description</span></span>

<span data-ttu-id="39e56-194">このサービスを使用すると、キャッシュの完全な通知機能がクリアされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-194">This service clears the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-195">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-195">Input Parameters</span></span>

- <span data-ttu-id="39e56-196">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-196">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-197">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-197">Return Values</span></span>

- <span data-ttu-id="39e56-198">**NX_SUCCESS** (0x00) DNS キャッシュ通知の設定に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-198">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="39e56-199">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-199">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="39e56-200">NX_PTR_ERROR (0x07) DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-200">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-201">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-201">Allowed From</span></span>

<span data-ttu-id="39e56-202">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-202">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-203">例</span><span class="sxs-lookup"><span data-stu-id="39e56-203">Example</span></span>
```C
/* Clear the DNS Cache full notify function. */
status =  nx_dns_cache_notify_clear(&my_dns);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully cleared. */
```

## <a name="nx_dns_cache_notify_set"></a><span data-ttu-id="39e56-204">nx_dns_cache_notify_set</span><span class="sxs-lookup"><span data-stu-id="39e56-204">nx_dns_cache_notify_set</span></span>

<span data-ttu-id="39e56-205">DNS キャッシュの完全な通知機能を設定します</span><span class="sxs-lookup"><span data-stu-id="39e56-205">Set the DNS Cache full notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-206">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-206">Prototype</span></span>
```C
UINT nx_dns_cache_notify_set(NX_DNS *dns_ptr,
                            VOID (*cache_full_notify_cb)(NX_DNS *dns_ptr));
```

### <a name="description"></a><span data-ttu-id="39e56-207">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-207">Description</span></span>

<span data-ttu-id="39e56-208">このサービスを使用すると、キャッシュの完全な通知機能が設定されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-208">This service sets the cache full notify function.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-209">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-209">Input Parameters</span></span>

- <span data-ttu-id="39e56-210">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-210">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="39e56-211">**cache_full_notify_cb** キャッシュがいっぱいになったときに呼び出されるコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="39e56-211">**cache_full_notify_cb** The callback function to be invoked when cache become full.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-212">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-212">Return Values</span></span>

- <span data-ttu-id="39e56-213">**NX_SUCCESS** (0x00) DNS キャッシュ通知の設定に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-213">**NX_SUCCESS** (0x00) DNS cache notify successfully set</span></span>
- <span data-ttu-id="39e56-214">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-214">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="39e56-215">NX_PTR_ERROR (0x07) DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-215">NX_PTR_ERROR (0x07) Invalid DNS pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-216">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-216">Allowed From</span></span>

<span data-ttu-id="39e56-217">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-217">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-218">例</span><span class="sxs-lookup"><span data-stu-id="39e56-218">Example</span></span>
```C
/* Set the DNS Cache full notify function. */
status =  nx_dns_cache_notify_set(&my_dns, cache_full_notify_cb);

/* If status is NX_SUCCESS DNS Cache full notify function was successfully set. */
```

## <a name="nx_dns_cname_get"></a><span data-ttu-id="39e56-219">nx_dns_cname_get</span><span class="sxs-lookup"><span data-stu-id="39e56-219">nx_dns_cname_get</span></span>

<span data-ttu-id="39e56-220">入力ホスト名の正規名を検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-220">Look up the canonical name for the input hostname</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-221">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-221">Prototype</span></span>
```C
UINT nx_dns_cname_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                     UCHAR *record_buffer, UINT buffer_size, 
                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-222">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-222">Description</span></span>

<span data-ttu-id="39e56-223">*nxd_dns.h* で NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって、指定されたドメイン名を持つ CNAME 型のクエリが送信され、正規のドメイン名が取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-223">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined in *nxd_dns.h*, this service sends a query of type CNAME with the specified domain name to obtain the canonical domain name.</span></span> <span data-ttu-id="39e56-224">DNS クライアントによって、DNS サーバーの応答で返された CNAME 文字列が *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-224">The DNS Client copies the CNAME string returned in the DNS Server response into the *record_buffer* memory location.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-225">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-225">Input Parameters</span></span>

- <span data-ttu-id="39e56-226">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-226">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-227">**host_name** CNAME データを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-227">**host_name** Pointer to host name to obtain CNAME data for</span></span>
- <span data-ttu-id="39e56-228">**record_buffer** CNAME データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-228">**record_buffer** Pointer to location to extract CNAME data into</span></span>
- <span data-ttu-id="39e56-229">**buffer_size** CNAME データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-229">**buffer_size** Size of buffer to hold CNAME data</span></span>
- <span data-ttu-id="39e56-230">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-230">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-231">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-231">Return Values</span></span>

- <span data-ttu-id="39e56-232">**NX_SUCCESS** (0x00): CNAME データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-232">**NX_SUCCESS** (0x00) Successfully obtained CNAME data</span></span>
- <span data-ttu-id="39e56-233">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-233">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-234">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-234">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-235">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-235">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-236">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-236">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-237">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-237">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-238">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-238">Allowed From</span></span>

<span data-ttu-id="39e56-239">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-239">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-240">例</span><span class="sxs-lookup"><span data-stu-id="39e56-240">Example</span></span>
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

##  <a name="nx_dns_create"></a><span data-ttu-id="39e56-241">nx_dns_create</span><span class="sxs-lookup"><span data-stu-id="39e56-241">nx_dns_create</span></span>

<span data-ttu-id="39e56-242">DNS クライアント インスタンスを作成します</span><span class="sxs-lookup"><span data-stu-id="39e56-242">Create a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-243">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-243">Prototype</span></span>
```C
UINT nx_dns_create(NX_DNS *dns_ptr, NX_IP *ip_ptr, CHAR *domain_name);
```
### <a name="description"></a><span data-ttu-id="39e56-244">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-244">Description</span></span>

<span data-ttu-id="39e56-245">このサービスを使用すると、以前に作成された IP インスタンスの DNS クライアント インスタンスが作成されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-245">This service creates a DNS Client instance for the previously created IP instance.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="39e56-246">アプリケーションは、DNS クライアントによって使用されるパケット プールのパケット ペイロードが、最大 512 バイトの DNS メッセージに加えて、UDP、IP、およびイーサネット ヘッダーに対して十分な大きさであることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-246">The application must ensure that the packet payload of the packet pool used by the DNS Client is large enough for the maximum 512 byte DNS message, plus UDP, IP and Ethernet headers.</span></span> <span data-ttu-id="39e56-247">DNS クライアントによって独自のパケット プールが作成された場合、これは、NX_DNS_PACKET_PAYLOAD と NX_DNS_PACKET_POOL_SIZE によって定義されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-247">If the DNS Client creates its own packet pool, this is defined by NX_DNS_PACKET_PAYLOAD and NX_DNS_PACKET_POOL_SIZE.</span></span>

<span data-ttu-id="39e56-248">DNS クライアント アプリケーションで、以前に作成されたパケット プールを提供することが優先される場合、IPv4 DNS クライアントのペイロードは、最大 DNS 用の 512 バイトに加えて、IP ヘッダー用の 20 バイト、UDP ヘッダー用の 8 バイト、イーサネット ヘッダー用の 14 バイトになります。</span><span class="sxs-lookup"><span data-stu-id="39e56-248">If the DNS Client application prefers to supply a previously created packet pool, the payload for IPv4 DNS Client should be 512 bytes for the maximum DNS plus 20 bytes for the IP header, 8 bytes for the UDP header and 14 bytes for the Ethernet header.</span></span> <span data-ttu-id="39e56-249">IPv6 の場合、唯一の違いは、IP ヘッダーが 40 バイトであるため、パケットは 40 バイトの IPv6 ヘッダーを収容できる必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-249">For IPv6 the only difference is the IP header is 40 bytes, therefore the packet needs to accommodate the IPv6 header of 40 bytes.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-250">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-250">Input Parameters</span></span>

- <span data-ttu-id="39e56-251">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-251">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-252">**ip_ptr** 以前に作成された IP インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-252">**ip_ptr** Pointer to previously created IP instance.</span></span>  
- <span data-ttu-id="39e56-253">**domain_name** DNS インスタンスのドメイン名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-253">**domain_name** Pointer to domain name for DNS instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-254">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-254">Return Values</span></span>

- <span data-ttu-id="39e56-255">**NX_SUCCESS** (0x00) DNS の作成に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-255">**NX_SUCCESS** (0x00) Successful DNS create</span></span>
- <span data-ttu-id="39e56-256">**NX_DNS_ERROR** (0xA0) DNS 作成エラー</span><span class="sxs-lookup"><span data-stu-id="39e56-256">**NX_DNS_ERROR** (0xA0) DNS create error</span></span>
- <span data-ttu-id="39e56-257">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-257">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-258">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-258">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-259">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-259">Allowed From</span></span>

<span data-ttu-id="39e56-260">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-260">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-261">例</span><span class="sxs-lookup"><span data-stu-id="39e56-261">Example</span></span>
```C
/* Create a DNS Client instance. */
status =  nx_dns_create(&my_dns, &my_ip, "My DNS");

/* If status is NX_SUCCESS a DNS Client instance was successfully
   created. */
```

## <a name="nx_dns_delete"></a><span data-ttu-id="39e56-262">nx_dns_delete</span><span class="sxs-lookup"><span data-stu-id="39e56-262">nx_dns_delete</span></span>

<span data-ttu-id="39e56-263">DNS クライアント インスタンスを削除します</span><span class="sxs-lookup"><span data-stu-id="39e56-263">Delete a DNS Client instance</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-264">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-264">Prototype</span></span>
```C
UINT nx_dns_delete(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="39e56-265">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-265">Description</span></span>

<span data-ttu-id="39e56-266">このサービスを使用すると、以前に作成された DNS クライアント インスタンスが削除され、リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-266">This service deletes a previously created DNS Client instance and frees up its resources.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-267">NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されていて、DNS クライアントにユーザー定義のパケット プールが割り当てられている場合、不要になった DNS クライアントのパケット プールの削除はアプリケーションが行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-267">If NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined and the DNS Client was assigned a user defined packet pool, it is up to the application to delete the DNS Client packet pool if it no longer needs it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-268">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-268">Input Parameters</span></span>

- <span data-ttu-id="39e56-269">**dns_ptr** 以前に作成した DNS クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-269">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-270">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-270">Return Values</span></span>

- <span data-ttu-id="39e56-271">**NX_SUCCESS** (0x00) DNS クライアントの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="39e56-271">**NX_SUCCESS** (0x00) Successful DNS Client delete.</span></span>
- <span data-ttu-id="39e56-272">NX_PTR_ERROR (0x07) IP または DNS クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-272">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="39e56-273">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-273">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-274">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-274">Allowed From</span></span>

<span data-ttu-id="39e56-275">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-275">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-276">例</span><span class="sxs-lookup"><span data-stu-id="39e56-276">Example</span></span>
```C
/* Delete a DNS Client instance. */
status =  nx_dns_delete(&my_dns);

/* If status is NX_SUCCESS the DNS Client instance was successfully
   deleted. */
```

## <a name="nx_dns_domain_name_server_get"></a><span data-ttu-id="39e56-277">nx_dns_domain_name_server_get</span><span class="sxs-lookup"><span data-stu-id="39e56-277">nx_dns_domain_name_server_get</span></span>

<span data-ttu-id="39e56-278">入力ドメイン ゾーンの権限のあるネーム サーバーを検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-278">Look up the authoritative name servers for the input domain zone</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-279">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-279">Prototype</span></span>
```C
UINT nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                   VOID *record_buffer, UINT buffer_size, 
                                   UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-280">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-280">Description</span></span>

<span data-ttu-id="39e56-281">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名の NS 型のクエリが送信され、入力ドメイン名のネーム サーバーが取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-281">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type NS with the specified domain name to obtain the name servers for the input domain name.</span></span> <span data-ttu-id="39e56-282">DNS クライアントによって、DNS サーバーの応答で返された NS レコードが *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-282">The DNS Client copies the NS record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="39e56-283">データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-283">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="39e56-284">NetX Duo DNS クライアントでは、NS データ型の NX_DNS_NS_ENTRY は、2 つの 4 バイトのパラメーターとして保存されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-284">In NetX Duo DNS Client the NS data type, NX_DNS_NS_ENTRY, is saved as two 4-byte parameters:</span></span>

- <span data-ttu-id="39e56-285">**nx_dns_ns_ipv4_address** ネーム サーバーの IPv4 アドレス</span><span class="sxs-lookup"><span data-stu-id="39e56-285">**nx_dns_ns_ipv4_address** Name server’s IPv4 address</span></span>
- <span data-ttu-id="39e56-286">**nx_dns_ns_hostname_ptr** ネーム サーバーのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-286">**nx_dns_ns_hostname_ptr** Pointer to the name server’s hostname</span></span>

<span data-ttu-id="39e56-287">次に示すバッファーには、4 つの NX_DNS_NS_ENTRY レコードが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39e56-287">The buffer shown below contains four NX_DNS_NS_ENTRY records.</span></span> <span data-ttu-id="39e56-288">各エントリのホスト名文字列へのポインターは、バッファーの下半分にある対応するホスト名文字列を指します。</span><span class="sxs-lookup"><span data-stu-id="39e56-288">The pointer to host name string in each entry points to the corresponding host name string in the bottom half of the buffer:</span></span>

![4 つの NX_DNS_NS_ENTRY レコードが含まれます](media/image5.png)

<span data-ttu-id="39e56-290">入力 *record_buffer* にサーバー応答内のすべての NS データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-290">If the input *record_buffer* cannot hold all the NS data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="39e56-291">\**record_countt* で返された NS レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードの IP アドレスとホスト名を解析できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-291">With the number of NS records returned in \**record_count,* the application can parse the IP address and host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-292">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-292">Input Parameters</span></span>

- <span data-ttu-id="39e56-293">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-293">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-294">**host_name** NS データを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-294">**host_name** Pointer to host name to obtain NS data for</span></span>
- <span data-ttu-id="39e56-295">**record_buffer** NS データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-295">**record_buffer** Pointer to location to extract NS data into</span></span>
- <span data-ttu-id="39e56-296">**buffer_size** NS データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-296">**buffer_size** Size of buffer to hold NS data</span></span>
- <span data-ttu-id="39e56-297">**record_count** 取得した NS レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-297">**record_count** Pointer to the number of NS records retrieved</span></span>
- <span data-ttu-id="39e56-298">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-298">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-299">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-299">Return Values</span></span>

- <span data-ttu-id="39e56-300">**NX_SUCCESS** (0x00): NS データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-300">**NX_SUCCESS** (0x00) Successfully obtained NS data</span></span>
- <span data-ttu-id="39e56-301">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-301">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-302">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-302">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-303">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-303">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="39e56-304">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-304">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-305">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-305">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-306">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-306">Allowed From</span></span>

<span data-ttu-id="39e56-307">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-307">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-308">例</span><span class="sxs-lookup"><span data-stu-id="39e56-308">Example</span></span>
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

## <a name="nx_dns_domain_mail_exchange_get"></a><span data-ttu-id="39e56-309">nx_dns_domain_mail_exchange_get</span><span class="sxs-lookup"><span data-stu-id="39e56-309">nx_dns_domain_mail_exchange_get</span></span>

<span data-ttu-id="39e56-310">入力ホスト名のメール交換を検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-310">Look up the mail exchange(s) for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-311">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-311">Prototype</span></span>
```C
UINT nx_dns_domain_mail_exchange_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                                     VOID *record_buffer,                                        
                                     UINT buffer_size, 
                                     UINT *record_count, 
                                     ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-312">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-312">Description</span></span>

<span data-ttu-id="39e56-313">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名の MX 型のクエリが送信され、入力ドメイン名のメール交換が取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-313">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type MX with the specified domain name to obtain the mail exchange for the input domain name.</span></span> <span data-ttu-id="39e56-314">DNS クライアントによって、DNS サーバーの応答で返された MX レコードが *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-314">The DNS Client copies the MX record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-315">データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-315">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="39e56-316">NetX Duo DNS クライアントでは、メール交換レコードの種類 NX_DNS_MAIL_EXCHANGE_ENTRY が、次の 4 つのパラメーター (合計 12 バイト) として保存されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-316">In NetX Duo DNS Client, the mail exchange record type, NX_DNS_MAIL_EXCHANGE_ENTRY, is saved as four parameters, totaling 12 bytes:</span></span>

- <span data-ttu-id="39e56-317">**nx_dns_mx_ipv4_address** メール交換 IPv4 アドレス (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-317">**nx_dns_mx_ipv4_address** Mail exchange IPv4 address 4 bytes</span></span>
- <span data-ttu-id="39e56-318">**nx_dns_mx_preference** 優先順位 (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-318">**nx_dns_mx_preference** Preference 2 bytes</span></span>
- <span data-ttu-id="39e56-319">**nx_dns_mx_reserved0** 予約済み (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-319">**nx_dns_mx_reserved0** Reserved 2 bytes</span></span>
- <span data-ttu-id="39e56-320">**nx_dns_mx_hostname_ptr** メール交換サーバー ホスト名へのポインター (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-320">**nx_dns_mx_hostname_ptr** Pointer to mail exchange server host name 4 bytes</span></span>

<span data-ttu-id="39e56-321">次に、4 つの MX レコードを含むバッファーを示します。</span><span class="sxs-lookup"><span data-stu-id="39e56-321">A buffer containing four MX records is shown below.</span></span> <span data-ttu-id="39e56-322">各レコードには、上記のリストの固定長データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="39e56-322">Each record contains the fixed length data from the list above.</span></span> <span data-ttu-id="39e56-323">メール交換サーバー ホスト名へのポインターは、バッファーの下部にある対応するホスト名を指します。</span><span class="sxs-lookup"><span data-stu-id="39e56-323">The pointer to the mail exchange server host name points to the corresponding host name at the bottom of the buffer.</span></span>

![4 つの MX レコードを含むバッファー](media/image6.png)

<span data-ttu-id="39e56-325">入力 *record_buffer* にサーバー応答内のすべての MX データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-325">If the input *record_buffer* cannot hold all the MX data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="39e56-326">\**record_countt* で返された MX レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードのメール ホスト名を含む MX パラメーターの解析を行うことができます。</span><span class="sxs-lookup"><span data-stu-id="39e56-326">With the number of MX records returned in \**record_count,* the application can parse the MX parameters, including the mail host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-327">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-327">Input Parameters</span></span>

- <span data-ttu-id="39e56-328">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-328">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-329">**host_name** MX データを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-329">**host_name** Pointer to host name to obtain MX data for</span></span>
- <span data-ttu-id="39e56-330">**record_buffer** MX データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-330">**record_buffer** Pointer to location to extract MX data into</span></span>
- <span data-ttu-id="39e56-331">**buffer_size** MX データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-331">**buffer_size** Size of buffer to hold MX data</span></span>
- <span data-ttu-id="39e56-332">**record_count** 取得した MX レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-332">**record_count** Pointer to the number of MX records retrieved</span></span>
- <span data-ttu-id="39e56-333">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-333">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-334">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-334">Return Values</span></span>

- <span data-ttu-id="39e56-335">**NX_SUCCESS** (0x00): MX データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-335">**NX_SUCCESS** (0x00) Successfully obtained MX data</span></span>
- <span data-ttu-id="39e56-336">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-336">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-337">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-337">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-338">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-338">NX_DNS_PARAM_ERROR (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="39e56-339">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-339">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-340">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-340">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-341">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-341">Allowed From</span></span>

<span data-ttu-id="39e56-342">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-342">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-343">例</span><span class="sxs-lookup"><span data-stu-id="39e56-343">Example</span></span>
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

## <a name="nx_dns_domain_service_get"></a><span data-ttu-id="39e56-344">nx_dns_domain_service_get</span><span class="sxs-lookup"><span data-stu-id="39e56-344">nx_dns_domain_service_get</span></span>

<span data-ttu-id="39e56-345">入力ホスト名で提供されるサービスを検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-345">Look up the service(s) provided by the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-346">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-346">Prototype</span></span>
```C
UINT nx_dns_domain_service_get (NX_DNS *dns_ptr, UCHAR *host_name, 
                                VOID *record_buffer, UINT buffer_size, 
                                UINT *record_count, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-347">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-347">Description</span></span>

<span data-ttu-id="39e56-348">NX_DNS_ENABLE_EXTENDED_RR_TYPES が定義されている場合、このサービスによって指定したドメイン名が使用されて SRV 型のクエリが送信され、指定したドメインに関連付けられているサービスとそのポート番号が検索されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-348">If NX_DNS_ENABLE_EXTENDED_RR_TYPES is defined, this service sends a query of type SRV with the specified domain name to look up the service(s) and their port number associated with the specified domain.</span></span> <span data-ttu-id="39e56-349">DNS クライアントによって、DNS サーバーの応答で返された SRV レコードが *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-349">The DNS Client copies the SRV record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-350">データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-350">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="39e56-351">NetX Duo DNS クライアントでは、サービス レコードの種類 NX_DNS_SRV_ ENTRY が 6 個のパラメーター (合計 16 バイト) として保存されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-351">In NetX Duo DNS Client, the service record type, NX_DNS_SRV_ ENTRY, is saved as six parameters, totaling 16 bytes.</span></span> <span data-ttu-id="39e56-352">これにより、可変長の SRV データをメモリ効率の高い方法で格納できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-352">This enables variable length SRV data to be stored in a memory efficient manner:</span></span>

- <span data-ttu-id="39e56-353">**サーバー IPv4 アドレス** nx_dns_srv_ipv4_address (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-353">**Server IPv4 address** nx_dns_srv_ipv4_address 4 bytes</span></span>
- <span data-ttu-id="39e56-354">**サーバーの優先度** nx_dns_srv_priority (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-354">**Server priority** nx_dns_srv_priority 2 bytes</span></span>
- <span data-ttu-id="39e56-355">**サーバーの重み** nx_dns_srv_weight (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-355">**Server weight** nx_dns_srv_weight 2 bytes</span></span>
- <span data-ttu-id="39e56-356">**サービス ポート番号** nx_dns_srv_port_number (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-356">**Service port number** nx_dns_srv_port_number 2 bytes</span></span>
- <span data-ttu-id="39e56-357">**4 バイトの配置用に予約済み** nx_dns_srv_reserved0 (2 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-357">**Reserved for 4-byte alignment** nx_dns_srv_reserved0 2 bytes</span></span>
- <span data-ttu-id="39e56-358">**サーバー ホスト名へのポインター** \*nx_dns_srv_hostname_ptr (4 バイト)</span><span class="sxs-lookup"><span data-stu-id="39e56-358">**Pointer to server host name** \*nx_dns_srv_hostname_ptr 4 bytes</span></span>

<span data-ttu-id="39e56-359">4 つの SRV レコードが、提供されるバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-359">Four SRV records are stored in the supplied buffer.</span></span> <span data-ttu-id="39e56-360">各 NX_DNS_SRV_ENTRY レコードには、レコード バッファーの一番下にある対応するホスト名文字列を指すポインター (*nx_dns_srv_hostname_ptr*) が含まれています。</span><span class="sxs-lookup"><span data-stu-id="39e56-360">Each NX_DNS_SRV_ENTRY record contains a pointer, *nx_dns_srv_hostname_ptr*, that points to the corresponding host name string in the bottom of the record buffer:</span></span>

![SRV レコード用](media/image7.png)

<span data-ttu-id="39e56-362">入力 *record_buffer* にサーバー応答内のすべての SRV データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-362">If the input *record_buffer* cannot hold all the SRV data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="39e56-363">\**record_count* で返された SRV レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードのサーバー ホスト名を含む SRV パラメーターを解析できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-363">With the number of SRV records returned in \**record_count,* the application can parse the SRV parameters, including the server host name of each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-364">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-364">Input Parameters</span></span>

- <span data-ttu-id="39e56-365">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-365">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-366">**host_name** SRV データを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-366">**host_name** Pointer to host name to obtain SRV data for</span></span>
- <span data-ttu-id="39e56-367">**record_buffer** SRV データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-367">**record_buffer** Pointer to location to extract SRV data into</span></span>
- <span data-ttu-id="39e56-368">**buffer_size** SRV データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-368">**buffer_size** Size of buffer to hold SRV data</span></span>
- <span data-ttu-id="39e56-369">**record_count** 取得した SRV レコードの数へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-369">**record_count** Pointer to the number of SRV records retrieved</span></span>
- <span data-ttu-id="39e56-370">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-370">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-371">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-371">Return Values</span></span>

- <span data-ttu-id="39e56-372">**NX_SUCCESS** (0x00): SRV データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-372">**NX_SUCCESS** (0x00) Successfully obtained SRV data</span></span>
- <span data-ttu-id="39e56-373">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-373">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-374">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-374">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-375">NX_DNS_PARAM_ERROR (0xA8) 非ポインター パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-375">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>
- <span data-ttu-id="39e56-376">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-376">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-377">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-377">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-378">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-378">Allowed From</span></span>

<span data-ttu-id="39e56-379">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-379">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-380">例</span><span class="sxs-lookup"><span data-stu-id="39e56-380">Example</span></span>
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

## <a name="nx_dns_get_serverlist_size"></a><span data-ttu-id="39e56-381">nx_dns_get_serverlist_size</span><span class="sxs-lookup"><span data-stu-id="39e56-381">nx_dns_get_serverlist_size</span></span>

<span data-ttu-id="39e56-382">DNS クライアントのサーバー リストのサイズを返します</span><span class="sxs-lookup"><span data-stu-id="39e56-382">Return the size of the DNS Client’s Server list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-383">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-383">Prototype</span></span>
```C
UINT nx_dns_get_serverlist_size (NX_DNS *dns_ptr, UINT *size);
```
### <a name="description"></a><span data-ttu-id="39e56-384">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-384">Description</span></span>

<span data-ttu-id="39e56-385">このサービスを使用すると、クライアント リストの有効な DNS サーバー (IPv4 と IPv6 の両方) の数が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-385">This service returns the number of valid DNS Servers (both IPv4 and IPv6) in the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-386">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-386">Input Parameters</span></span>

- <span data-ttu-id="39e56-387">**mdns_ptr**: DNS 制御ブロックを指すポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-387">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="39e56-388">**size** リスト内のサーバーの数を返します</span><span class="sxs-lookup"><span data-stu-id="39e56-388">**size** Returns the number of servers in the list</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-389">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-389">Return Values</span></span>

- <span data-ttu-id="39e56-390">**NX_SUCCESS** (0x00) DNS サーバー リストのサイズが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="39e56-390">**NX_SUCCESS** (0x00) DNS Server list size successfully returned</span></span>
- <span data-ttu-id="39e56-391">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-391">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="39e56-392">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-392">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-393">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-393">Allowed From</span></span>

<span data-ttu-id="39e56-394">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-394">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-395">例</span><span class="sxs-lookup"><span data-stu-id="39e56-395">Example</span></span>
```C
UINT my_listsize;

/* Get the number of non null DNS Servers in the Client list. */
status =  nx_dns_get_serverlist_size (&my_dns, 5, &my_listsize);

/* If status is NX_SUCCESS the size of the DNS Server list was successfully
   returned. */
```

## <a name="nx_dns_info_by_name_get"></a><span data-ttu-id="39e56-396">nx_dns_info_by_name_get</span><span class="sxs-lookup"><span data-stu-id="39e56-396">nx_dns_info_by_name_get</span></span>

<span data-ttu-id="39e56-397">DNS サーバーの IP アドレスとポートをホスト名別に返します</span><span class="sxs-lookup"><span data-stu-id="39e56-397">Return ip address and port of DNS server by host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-398">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-398">Prototype</span></span>
```C
UINT nx_dns_info_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr,  
                             USHORT *host_port_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-399">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-399">Description</span></span>

<span data-ttu-id="39e56-400">このサービスを使用すると、DNS クエリによる入力ホスト名に基づいて、サーバーの IP とポート (サービス レコード) が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-400">This service returns the Server IP and port (service record) based on the input host name by DNS query.</span></span> <span data-ttu-id="39e56-401">サービス レコードが見つからない場合、このルーチンは、入力アドレス ポインターでゼロの IP アドレスを返し、0 以外のエラー状態を返してエラーを通知します。</span><span class="sxs-lookup"><span data-stu-id="39e56-401">If a service record is not found, this routine returns a zero IP address in the input address pointer and a non-zero error status return to signal an error.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-402">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-402">Input Parameters</span></span>

- <span data-ttu-id="39e56-403">**mdns_ptr**: DNS 制御ブロックを指すポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-403">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="39e56-404">**host_name**: ホスト名バッファーを指すポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-404">**host_name** Pointer to host name buffer</span></span>
- <span data-ttu-id="39e56-405">**host_address_ptr** 返されるアドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-405">**host_address_ptr** Pointer to address to return</span></span>
- <span data-ttu-id="39e56-406">**host_address_ptr** 返されるポートへのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-406">**host_port_ptr** Pointer to port to return</span></span>
- <span data-ttu-id="39e56-407">**wait_option** DNS 応答の待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-407">**wait_option** Wait option for the DNS response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-408">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-408">Return Values</span></span>

- <span data-ttu-id="39e56-409">**NX_SUCCESS** (0x00) DNS サーバー レコードが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="39e56-409">**NX_SUCCESS** (0x00) DNS Server record successfully returned</span></span>
- <span data-ttu-id="39e56-410">**NX_DNS_NO_SERVER** (0xA1) ホスト名のクエリを送信するためにクライアントに登録されている DNS サーバーがありません</span><span class="sxs-lookup"><span data-stu-id="39e56-410">**NX_DNS_NO_SERVER** (0xA1) No DNS Server registered with Client to send query on hostname</span></span>
- <span data-ttu-id="39e56-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS クエリが失敗しました。クライアント リストに DN サーバーからの応答がないか、入力ホスト名に使用できるサービス レコードがありません。</span><span class="sxs-lookup"><span data-stu-id="39e56-411">**NX_DNS_QUERY_FAILED** (0xA3) DNS query failed; no response from any DNS servers in Client list or no service record is available for the input hostname.</span></span>
- <span data-ttu-id="39e56-412">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-412">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-413">NX_CALLER_ERROR: (0x11) 呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-413">NX_CALLER_ERROR (0x11) Invalid caller</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-414">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-414">Allowed From</span></span>

<span data-ttu-id="39e56-415">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-415">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-416">例</span><span class="sxs-lookup"><span data-stu-id="39e56-416">Example</span></span>
```C
ULONG ip_address
USHORT port;

/* Attempt to resolve the IP address and ports for this host name. */
status =  nx_dns_info_by_name_get(&my_dns, “www.abc1234.com”, &ip_address, &port, 200);

/* If status is NX_SUCCESS the DNS query was successful and the IP address and
   report for the hostname are returned. */
```

## <a name="nx_dns_ipv4_address_by_name_get"></a><span data-ttu-id="39e56-417">nx_dns_ipv4_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="39e56-417">nx_dns_ipv4_address_by_name_get</span></span>

<span data-ttu-id="39e56-418">入力ホスト名の IPv4 アドレスを検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-418">Look up the IPv4 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-419">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-419">Prototype</span></span>
```C
UINT nx_ dns_ipv4_address_by_name_get (NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-420">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-420">Description</span></span>

<span data-ttu-id="39e56-421">このサービスを使用すると、指定されたホスト名で A 型のクエリが送信され、入力ホスト名の IP アドレスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-421">This service sends a query of Type A with the specified host name to obtain the IP addresses for the input host name.</span></span> <span data-ttu-id="39e56-422">DNS クライアントによって、DNS サーバーの応答で返された A レコードからの IPv4 アドレスが *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-422">The DNS Client copies the IPv4 address from the A record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span>

> [!NOTE]
> <span data-ttu-id="39e56-423">データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-423">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="39e56-424">次に示すように、複数の IPv4 アドレスが 4 バイトで配置されたバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-424">Multiple IPv4 addresses are stored in the 4-byte aligned buffer as shown below:</span></span>

![複数のアドレスが 4 バイトで配置されたバッファー](media/image8.png)

<span data-ttu-id="39e56-426">提供されたバッファーがすべての IP アドレス データを保持できない場合、残りの A レコードは *record_buffer* に格納されません。</span><span class="sxs-lookup"><span data-stu-id="39e56-426">If the supplied buffer cannot hold all the IP address data, the remaining A records are not stored in *record_buffer*.</span></span> <span data-ttu-id="39e56-427">これにより、アプリケーションは、サーバーの応答で使用可能な IP アドレス データの 1 つ、一部、またはすべてを取得できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-427">This enables the application to retrieve one, some or all of the available IP address data in the server reply.</span></span>

<span data-ttu-id="39e56-428">\**Record_count* で返される A レコードの数を使用することで、アプリケーションで *record_buffer* からの IPv4 アドレス データを解析できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-428">With the number of A records returned in \**record_count* the application can parse the IPv4 address data from the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-429">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-429">Input Parameters</span></span>

- <span data-ttu-id="39e56-430">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-430">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-431">**host_name_ptr** IPv4 アドレスを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-431">**host_name_ptr** Pointer to host name to obtain IPv4 address</span></span>
- <span data-ttu-id="39e56-432">**buffer** IPv4 データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-432">**buffer** Pointer to location to extract IPv4 data into</span></span>
- <span data-ttu-id="39e56-433">**buffer_size** IPv4 データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-433">**buffer_size** Size of buffer to hold IPv4 data</span></span>
- <span data-ttu-id="39e56-434">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-434">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-435">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-435">Return Values</span></span>

- <span data-ttu-id="39e56-436">**NX_SUCCESS** (0x00): IPv4 データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-436">**NX_SUCCESS** (0x00) Successfully obtained IPv4 data</span></span>
- <span data-ttu-id="39e56-437">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-437">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-438">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-438">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-439">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-439">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-440">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-440">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-441">NX_DNS_PARAM_ERROR (0xA8) 非ポインター パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-441">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-442">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-442">Allowed From</span></span>

<span data-ttu-id="39e56-443">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-444">例</span><span class="sxs-lookup"><span data-stu-id="39e56-444">Example</span></span>
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

## <a name="nxd_dns_ipv6_address_by_name_get"></a><span data-ttu-id="39e56-445">nxd_dns_ipv6_address_by_name_get</span><span class="sxs-lookup"><span data-stu-id="39e56-445">nxd_dns_ipv6_address_by_name_get</span></span>

<span data-ttu-id="39e56-446">入力ホスト名の IPv6 アドレスを検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-446">Look up the IPv6 address for the input host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-447">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-447">Prototype</span></span>
```C
UINT nxd_ dns_ipv6_address_by_name_get(NX_DNS *dns_ptr, 
                                      UCHAR *host_name_ptr, VOID *buffer, 
                                      UINT buffer_size, 
                                      UINT *record_count, 
                                      ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-448">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-448">Description</span></span>

<span data-ttu-id="39e56-449">このサービスを使用すると、指定されたドメイン名で AAAA 型のクエリが送信され、入力ドメイン名の IP アドレスが取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-449">This service sends a query of type AAAA with the specified domain name to obtain the IP addresses for the input domain name.</span></span> <span data-ttu-id="39e56-450">DNS クライアントによって、DNS サーバーの応答で返された AAAA レコードからの IPv6 アドレスが *record_buffer* のメモリの場所にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-450">The DNS Client copies the IPv6 address from the AAAA record(s) returned in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-451">データを受信するには、*record_buffer* が 4 バイトで配置されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-451">The *record_buffer* must be 4-byte aligned to receive the data.</span></span>

<span data-ttu-id="39e56-452">4 バイトで配置されたバッファーに格納されている IPv6 アドレスの形式を次に示します。</span><span class="sxs-lookup"><span data-stu-id="39e56-452">The format of IPv6 addresses stored in the 4-byte aligned buffer is shown below:</span></span>

![IPv6 形式の 4 バイト配置バッファー](media/image9.png)

<span data-ttu-id="39e56-454">入力 *record_buffer* にサーバー応答内のすべての AAAA データを保持できない場合、*record_buffer* には収まるだけのレコードが保持され、バッファー内のレコードの数が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-454">If the input *record_buffer* cannot hold all the AAAA data in the server reply, the the *record_buffer* holds as many records as will fit and returns the number of records in the buffer.</span></span>

<span data-ttu-id="39e56-455">\**record_countt* で返された AAAA レコードの数を使用することで、アプリケーションで *record_buffer* 内の各レコードの IPv6 アドレスを解析できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-455">With the number of AAAA records returned in \**record_count,* the application can parse the IPv6 addresses from each record in the *record_buffer*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-456">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-456">Input Parameters</span></span>

- <span data-ttu-id="39e56-457">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-457">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-458">**host_name_ptr** IPv6 アドレスを取得するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-458">**host_name_ptr** Pointer to host name to obtain IPv6 address</span></span>
- <span data-ttu-id="39e56-459">**buffer** IPv6 データの情報を抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-459">**buffer** Pointer to location to extract IPv6 data into</span></span>
- <span data-ttu-id="39e56-460">**buffer_size** IPv6 データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-460">**buffer_size** Size of buffer to hold IPv6 data</span></span>
- <span data-ttu-id="39e56-461">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-461">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-462">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-462">Return Values</span></span>

- <span data-ttu-id="39e56-463">**NX_SUCCESS** (0x00): IPv6 データの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-463">**NX_SUCCESS** (0x00) Successfully obtained IPv6 data</span></span>
- <span data-ttu-id="39e56-464">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-464">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-465">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-465">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-466">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-466">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-467">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-467">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-468">NX_DNS_PARAM_ERROR (0xA8) 非ポインター パラメーターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-468">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer parameter.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-469">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-469">Allowed From</span></span>

<span data-ttu-id="39e56-470">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-470">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-471">例</span><span class="sxs-lookup"><span data-stu-id="39e56-471">Example</span></span>
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

## <a name="nx_dns_host_by_address_get"></a><span data-ttu-id="39e56-472">nx_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="39e56-472">nx_dns_host_by_address_get</span></span>

<span data-ttu-id="39e56-473">IP アドレスからホスト名を検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-473">Look up a host name from an IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-474">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-474">Prototype</span></span>
```C
UINT nx_dns_host_by_address_get(NX_DNS *dns_ptr, ULONG ip_address, 
                                ULONG *host_name_ptr, 
                                ULONG max_host_name_size, 
                                ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-475">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-475">Description</span></span>

<span data-ttu-id="39e56-476">このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーから提供された IP アドレスの名前解決が要求されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-476">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="39e56-477">成功した場合は、*host_name_ptr* によって指定された文字列で NULL で終了するホスト名が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-477">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span> <span data-ttu-id="39e56-478">これは *nxd_dns_host_by_address_get* サービスのラッパー関数であり、IPv6 アドレスは指定できません。</span><span class="sxs-lookup"><span data-stu-id="39e56-478">This is a wrapper function for *nxd_dns_host_by_address_get* service and does not accept IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-479">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-479">Input Parameters</span></span>

- <span data-ttu-id="39e56-480">**dns_ptr** 以前に作成された DNS インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-480">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="39e56-481">**ip_address** 名前に解決する IP アドレス</span><span class="sxs-lookup"><span data-stu-id="39e56-481">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="39e56-482">**host_name_ptr** ホスト名の宛先領域へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-482">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="39e56-483">**max_host_name_size** ホスト名の宛先領域のサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-483">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="39e56-484">**wait_option** 各 DNS クエリおよびクエリ再試行の後に、サービスで DNS サーバーの応答を待機する時間をタイマー刻みで定義します。</span><span class="sxs-lookup"><span data-stu-id="39e56-484">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="39e56-485">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-485">The wait options are defined as follows:</span></span>

  <span data-ttu-id="39e56-486">タイムアウト値 (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="39e56-486">timeout value (0x00000001-0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="39e56-487">TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-487">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="39e56-488">数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-488">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-489">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-489">Return Values</span></span>

- <span data-ttu-id="39e56-490">**NX_SUCCESS**: (0x00) DNS の解決に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-490">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="39e56-491">**NX_DNS_TIMEOUT** (0xA2) DNS ミューテックスの取得がタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="39e56-491">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="39e56-492">**NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません</span><span class="sxs-lookup"><span data-stu-id="39e56-492">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="39e56-493">**NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="39e56-493">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="39e56-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) 入力アドレスが Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-494">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="39e56-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-495">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="39e56-496">**NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-496">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="39e56-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-497">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-498">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-498">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="39e56-499">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-499">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-500">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-500">Allowed From</span></span>

<span data-ttu-id="39e56-501">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-501">Threads</span></span>

<span data-ttu-id="39e56-502">**例**</span><span class="sxs-lookup"><span data-stu-id="39e56-502">**Example**</span></span>
```C
#define BUFFER_SIZE   200

UCHAR   resolved_name[200];

/* Get the name associated with IP address 192.2.2.10.  */
status =  nx_dns_host_by_address_get(&my_dns, IP_ADDRESS(192.2.2.10),
                                     &resolved_name[0], BUFFER_SIZE, 450);

/* If status is NX_SUCCESS the name associated with the IP address
   can be found in the resolved_name variable.  */
```

## <a name="nxd_dns_host_by_address_get"></a><span data-ttu-id="39e56-503">nxd_dns_host_by_address_get</span><span class="sxs-lookup"><span data-stu-id="39e56-503">nxd_dns_host_by_address_get</span></span>

<span data-ttu-id="39e56-504">IP アドレスからホスト名を検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-504">Look up a host name from the IP address</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-505">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-505">Prototype</span></span>
```C
UINT nxd_dns_host_by_address_get(NX_DNS *dns_ptr, 
                                 NXD_ADDRESS ip_address, 
                                 ULONG *host_name_ptr, 
                                 ULONG max_host_name_size, 
                                 ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-506">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-506">Description</span></span>

<span data-ttu-id="39e56-507">このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーからの IPv6 または IPv4 アドレスの名前解決を、*ip_address* 入力引数で要求します。</span><span class="sxs-lookup"><span data-stu-id="39e56-507">This service requests name resolution of the IPv6 or IPv4 address in the *ip_address* input argument from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="39e56-508">成功した場合は、*host_name_ptr* によって指定された文字列で NULL で終了するホスト名が返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-508">If successful, the NULL-terminated host name is returned in the string specified by *host_name_ptr*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-509">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-509">Input Parameters</span></span>

- <span data-ttu-id="39e56-510">**dns_ptr** 以前に作成された DNS インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-510">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="39e56-511">**ip_address** 名前に解決する IP アドレス</span><span class="sxs-lookup"><span data-stu-id="39e56-511">**ip_address** IP address to resolve into a name</span></span>
- <span data-ttu-id="39e56-512">**host_name_ptr** ホスト名の宛先領域へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-512">**host_name_ptr** Pointer to destination area for host name</span></span>
- <span data-ttu-id="39e56-513">**max_host_name_size** ホスト名の宛先領域のサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-513">**max_host_name_size** Size of destination area for host name</span></span>
- <span data-ttu-id="39e56-514">**wait_option** 各 DNS クエリおよびクエリ再試行の後に、サービスで DNS サーバーの応答を待機する時間をタイマー刻みで定義します。</span><span class="sxs-lookup"><span data-stu-id="39e56-514">**wait_option** Defines how long the service will wait in timer ticks for a DNS server response after each DNS query and query retry.</span></span> <span data-ttu-id="39e56-515">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-515">The wait options are defined as follows:</span></span>

  <span data-ttu-id="39e56-516">タイムアウト値 (0x00000001～0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="39e56-516">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="39e56-517">TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-517">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="39e56-518">数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-518">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-519">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-519">Return Values</span></span>

- <span data-ttu-id="39e56-520">**NX_SUCCESS**: (0x00) DNS の解決に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-520">**NX_SUCCESS** (0x00) Successful DNS resolution</span></span>  
- <span data-ttu-id="39e56-521">**NX_DNS_TIMEOUT** (0xA2) DNS ミューテックスの取得がタイムアウトになりました</span><span class="sxs-lookup"><span data-stu-id="39e56-521">**NX_DNS_TIMEOUT** (0xA2) Timed out on obtaining DNS mutex</span></span>
- <span data-ttu-id="39e56-522">**NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません</span><span class="sxs-lookup"><span data-stu-id="39e56-522">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="39e56-523">**NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="39e56-523">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="39e56-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) 入力アドレスが Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-524">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="39e56-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-525">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-526">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-526">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer</span></span>
- <span data-ttu-id="39e56-527">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-527">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-528">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-528">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-529">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-529">Allowed From</span></span>

<span data-ttu-id="39e56-530">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-530">Threads</span></span>

<span data-ttu-id="39e56-531">**例**</span><span class="sxs-lookup"><span data-stu-id="39e56-531">**Example**</span></span>
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

## <a name="nx_dns_host_by_name_get"></a><span data-ttu-id="39e56-532">nx_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="39e56-532">nx_dns_host_by_name_get</span></span>

<span data-ttu-id="39e56-533">ホスト名から IP アドレスを検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-533">Look up an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-534">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-534">Prototype</span></span>
```C
UINT nx_dns_host_by_name_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                             ULONG *host_address_ptr, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-535">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-535">Description</span></span>

<span data-ttu-id="39e56-536">このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーから提供された名前の名前解決が要求されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-536">This service requests name resolution of the supplied name from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="39e56-537">成功した場合、関連付けられた IP アドレスが、host_address_ptr によって指定された宛先に返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-537">If successful, the associated IP address is returned in the destination pointed to by host_address_ptr.</span></span> <span data-ttu-id="39e56-538">これは、*nxd_dns_host_by_name_get* サービスのラッパー関数であり、入力は IPv4 アドレスに限定されています。</span><span class="sxs-lookup"><span data-stu-id="39e56-538">This is a wrapper function for the *nxd_dns_host_by_name_get* service, and is limited to IPv4 address input.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-539">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-539">Input Parameters</span></span>

- <span data-ttu-id="39e56-540">**dns_ptr** 以前に作成された DNS インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-540">**dns_ptr** Pointer to previously created DNS instance.</span></span>
- <span data-ttu-id="39e56-541">**host_name**: ホスト名を指すポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-541">**host_name** Pointer to host name</span></span>
- <span data-ttu-id="39e56-542">**host_address_ptr** 返された DNS サーバーの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="39e56-542">**host_address_ptr** DNS Server IP address returned</span></span>
- <span data-ttu-id="39e56-543">**wait_option** サービスで DNS 解決を待機する時間を定義します。</span><span class="sxs-lookup"><span data-stu-id="39e56-543">**wait_option** Defines how long the service will wait for the DNS resolution.</span></span> <span data-ttu-id="39e56-544">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-544">The wait options are defined as follows:</span></span>

  <span data-ttu-id="39e56-545">タイムアウト値 (0x00000001～0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="39e56-545">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>

  <span data-ttu-id="39e56-546">TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-546">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS server responds to the request.</span></span>

  <span data-ttu-id="39e56-547">数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-547">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-548">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-548">Return Values</span></span>

- <span data-ttu-id="39e56-549">**NX_SUCCESS** (0x00) DNS の解決に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-549">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="39e56-550">**NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません</span><span class="sxs-lookup"><span data-stu-id="39e56-550">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="39e56-551">**NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="39e56-551">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="39e56-552">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-552">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="39e56-553">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-553">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="39e56-554">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-554">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-555">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-555">Allowed From</span></span>

<span data-ttu-id="39e56-556">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-556">Threads</span></span>

<span data-ttu-id="39e56-557">**例**</span><span class="sxs-lookup"><span data-stu-id="39e56-557">**Example**</span></span>
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

## <a name="nxd_dns_host_by_name_get"></a><span data-ttu-id="39e56-558">nxd_dns_host_by_name_get</span><span class="sxs-lookup"><span data-stu-id="39e56-558">nxd_dns_host_by_name_get</span></span>

<span data-ttu-id="39e56-559">ホスト名から IP アドレスを検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-559">Lookup an IP address from the host name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-560">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-560">Prototype</span></span>
```C
UINT nxd_dns_host_by_name_get(NX_DNS *dns_ptr, ULONG *host_name, 
                              NXD_ADDRESS *host_address_ptr, 
                              ULONG wait_option, UINT lookup_type);
```

### <a name="description"></a><span data-ttu-id="39e56-561">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-561">Description</span></span>

<span data-ttu-id="39e56-562">このサービスを使用すると、アプリケーションによって以前に指定された 1 つまたは複数の DNS サーバーから提供された IP アドレスの名前解決が要求されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-562">This service requests name resolution of the supplied IP address from one or more DNS Servers previously specified by the application.</span></span> <span data-ttu-id="39e56-563">成功した場合、関連付けられた IP アドレスが、*host_address_ptr* によって指定された NXD_ADDRESS に返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-563">If successful, the associated IP address is returned in an NXD_ADDRESS pointed to by *host_address_ptr*.</span></span> <span data-ttu-id="39e56-564">呼び出し元が lookup_type 入力を NX_IP_VERSION_V6 に明示的に設定した場合、このサービスによってホスト IPv6 アドレス (AAAA レコード) のクエリが送信されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-564">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V6, this service will send out query for a host IPv6 address (AAAA record).</span></span> <span data-ttu-id="39e56-565">呼び出し元が lookup_type 入力を NX_IP_VERSION_V4 に明示的に設定した場合、このサービスによってホスト IPv4 アドレス (A レコード) のクエリが送信されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-565">If the caller specifically sets the lookup_type input to NX_IP_VERSION_V4, this service will send out query for a host IPv4 address (A record).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-566">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-566">Input Parameters</span></span>

- <span data-ttu-id="39e56-567">**dns_ptr** 以前に作成した DNS クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-567">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="39e56-568">**host_name** IP アドレスを検索するためのホスト名へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-568">**host_name** Pointer to host name to find an IP address of</span></span>
- <span data-ttu-id="39e56-569">**host_address_ptr** IP アドレスを含む NXD_ADDRESS の宛先へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-569">**host_address_ptr** Pointer to destination for NXD_ADDRESS containing the IP address</span></span>
- <span data-ttu-id="39e56-570">**wait_option** クエリの送信と再送信ごとに、サービスが DNS サーバーの応答を待機する時間をタイマー刻みで定義します。</span><span class="sxs-lookup"><span data-stu-id="39e56-570">**wait_option** Defines how long the service will wait in timer ticks for the DNS Server response for each query transmission and retransmission.</span></span> <span data-ttu-id="39e56-571">この待機オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-571">The wait options are defined as follows:</span></span>

  <span data-ttu-id="39e56-572">タイムアウト値 (0x00000001～0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span><span class="sxs-lookup"><span data-stu-id="39e56-572">timeout value (0x00000001 through 0xFFFFFFFE) TX_WAIT_FOREVER (0xFFFFFFFF)</span></span>  

  <span data-ttu-id="39e56-573">TX_WAIT_FOREVER を選択すると、DNS サーバーが要求に応答するまで、呼び出しスレッドが無期限に停止されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-573">Selecting TX_WAIT_FOREVER causes the calling thread to suspend indefinitely until a DNS Server responds to the request.</span></span>

  <span data-ttu-id="39e56-574">数値 (1-0xFFFFFFFE) を選択すると、DNS 解決を待機して停止を続ける時間 (タイマー刻みの最大数) が指定されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-574">Selecting a numeric value (1-0xFFFFFFFE) specifies the maximum number of timer-ticks to stay suspended while waiting for the DNS resolution.</span></span>

- <span data-ttu-id="39e56-575">**lookup_type** 検索の種類 (A または AAAA) を示します。</span><span class="sxs-lookup"><span data-stu-id="39e56-575">**lookup_type** Indicate type of lookup (A vs AAAA).</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-576">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-576">Return Values</span></span>

- <span data-ttu-id="39e56-577">**NX_SUCCESS** (0x00) DNS の解決に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-577">**NX_SUCCESS** (0x00) Successful DNS resolution.</span></span>
- <span data-ttu-id="39e56-578">**NX_DNS_NO_SERVER** (0xA1) DNS サーバー アドレスが指定されていません</span><span class="sxs-lookup"><span data-stu-id="39e56-578">**NX_DNS_NO_SERVER** (0xA1) No DNS Server address specified</span></span>
- <span data-ttu-id="39e56-579">**NX_DNS_QUERY_FAILED** (0xA3) クエリの応答を受信しませんでした</span><span class="sxs-lookup"><span data-stu-id="39e56-579">**NX_DNS_QUERY_FAILED** (0xA3) Received no response to query</span></span>
- <span data-ttu-id="39e56-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) 入力アドレスが Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-580">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null input address</span></span>
- <span data-ttu-id="39e56-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-581">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-582">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-582">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="39e56-583">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-583">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-584">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-584">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-585">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-585">Allowed From</span></span>

<span data-ttu-id="39e56-586">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-586">Threads</span></span>

<span data-ttu-id="39e56-587">**例**</span><span class="sxs-lookup"><span data-stu-id="39e56-587">**Example**</span></span>
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

<span data-ttu-id="39e56-588">このタイム サービスを使用するもう 1 つの例を次に示します。ここでは、IPv4 アドレスと A レコード型を使用しています。</span><span class="sxs-lookup"><span data-stu-id="39e56-588">Another example of using this time service, this time using IPv4 addresses and A record types, is shown below:</span></span>
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

## <a name="nx_dns_host_text_get"></a><span data-ttu-id="39e56-589">nx_dns_host_text_get</span><span class="sxs-lookup"><span data-stu-id="39e56-589">nx_dns_host_text_get</span></span>

<span data-ttu-id="39e56-590">入力ドメイン名のテキスト文字列を検索します</span><span class="sxs-lookup"><span data-stu-id="39e56-590">Look up the text string for the input domain name</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-591">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-591">Prototype</span></span>
```C
UINT nx_dns_host_text_get(NX_DNS *dns_ptr, UCHAR *host_name, 
                          UCHAR *record_buffer, 
                          UINT buffer_size, ULONG wait_option);
```

### <a name="description"></a><span data-ttu-id="39e56-592">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-592">Description</span></span>

<span data-ttu-id="39e56-593">このサービスを使用すると、指定されたドメイン名とバッファーを使用して TXT 型のクエリが送信され、任意の文字列データが取得されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-593">This service sends a query of type TXT with the specified domain name and buffer to obtain the arbitrary string data.</span></span>

<span data-ttu-id="39e56-594">DNS クライアントによって、DNS サーバーの応答の TXT レコードのテキスト文字列が *record_buffer* のメモリ位置にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="39e56-594">The DNS Client copies the text string in the TXT record in the DNS Server response into the *record_buffer* memory location.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-595">データを受信するために record_buffer が 4 バイトで配置されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="39e56-595">The record_buffer does not need to be 4-byte aligned to receive the data.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-596">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-596">Input Parameters</span></span>

- <span data-ttu-id="39e56-597">**dns_ptr** DNS クライアントへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-597">**dns_ptr** Pointer to DNS Client.</span></span>  
- <span data-ttu-id="39e56-598">**host_name** 検索するホストの名前へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-598">**host_name** Pointer to name of host to search on</span></span>
- <span data-ttu-id="39e56-599">**record_buffer** TXT データを抽出する場所へのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-599">**record_buffer** Pointer to location to extract TXT data into</span></span>
- <span data-ttu-id="39e56-600">**buffer_size** TXT データを保持するバッファーのサイズ</span><span class="sxs-lookup"><span data-stu-id="39e56-600">**buffer_size** Size of buffer to hold TXT data</span></span>
- <span data-ttu-id="39e56-601">**wait_option** DNS サーバーの応答を受信するための待機オプション</span><span class="sxs-lookup"><span data-stu-id="39e56-601">**wait_option** Wait option to receive DNS Server response</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-602">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-602">Return Values</span></span>

- <span data-ttu-id="39e56-603">**NX_SUCCESS** (0x00) TXT 文字列の取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-603">**NX_SUCCESS** (0x00) Successfully TXT string obtained</span></span>
- <span data-ttu-id="39e56-604">**NX_DNS_NO_SERVER** (0xA1) クライアント サーバー リストが空です</span><span class="sxs-lookup"><span data-stu-id="39e56-604">**NX_DNS_NO_SERVER** (0xA1) Client server list is empty</span></span>
- <span data-ttu-id="39e56-605">**NX_DNS_QUERY_FAILED** (0xA3) 有効な DNS 応答を受信していません</span><span class="sxs-lookup"><span data-stu-id="39e56-605">**NX_DNS_QUERY_FAILED** (0xA3) No valid DNS response received</span></span>
- <span data-ttu-id="39e56-606">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-606">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="39e56-607">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-607">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-608">NX_DNS_PARAM_ERROR (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-608">NX_DNS_PARAM_ERROR (0xA8) Invalid non pointer input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-609">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-609">Allowed From</span></span>

<span data-ttu-id="39e56-610">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-610">Threads</span></span>

######   
<span data-ttu-id="39e56-611">例</span><span class="sxs-lookup"><span data-stu-id="39e56-611">Example</span></span>
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

## <a name="nx_dns_packet_pool_set"></a><span data-ttu-id="39e56-612">nx_dns_packet_pool_set</span><span class="sxs-lookup"><span data-stu-id="39e56-612">nx_dns_packet_pool_set</span></span>

<span data-ttu-id="39e56-613">DNS クライアントのパケット プールを設定します</span><span class="sxs-lookup"><span data-stu-id="39e56-613">Set the DNS Client packet pool</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-614">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-614">Prototype</span></span>
```C
UINT nx_dns_packet_pool_set(NX_DNS *dns_ptr, NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a><span data-ttu-id="39e56-615">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-615">Description</span></span>

<span data-ttu-id="39e56-616">このサービスを使用すると、以前に作成したパケット プールが DNS クライアント パケット プールとして設定されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-616">This service sets a previously created packet pool as the DNS Client packet pool.</span></span> <span data-ttu-id="39e56-617">DNS クライアントによってこのパケット プールが使用されて DNS クエリが送信されます。そのため、パケット ペイロードは、イーサネット、IP、および UDP ヘッダーを含み、*nxd_dns* で定義されている NX_DNS_PACKET_PAYLOAD よりも小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="39e56-617">The DNS Client will use this packet pool to send DNS queries, so the packet payload should not be less than NX_DNS_PACKET_PAYLOAD which includes the Ethernet, IP and UDP headers and is defined in *nxd_dns.h.*</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-618">*D* NS クライアントが削除された場合、パケット プールは削除されず、不要になったパケット プールの削除はアプリケーションの役割になります。</span><span class="sxs-lookup"><span data-stu-id="39e56-618">*W* hen the DNS Client is deleted, the packet pool is not deleted with it and it is the responsibility of the application to delete the packet pool when it no longer needs it.</span></span>
>
> <span data-ttu-id="39e56-619">このサービスは、構成オプション NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が *nxd_dns.h* に定義されている場合にのみ使用できます</span><span class="sxs-lookup"><span data-stu-id="39e56-619">This service is only available if the configuration option NX_DNS_CLIENT_USER_CREATE_PACKET_POOL is defined in *nxd_dns.h*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-620">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-620">Input Parameters</span></span>

- <span data-ttu-id="39e56-621">**dns_ptr** 以前に作成した DNS クライアント インスタンスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-621">**dns_ptr** Pointer to previously created DNS Client instance.</span></span>
- <span data-ttu-id="39e56-622">**pool_ptr** 以前に作成されたパケット プールへのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-622">**pool_ptr** Pointer to previously created packet pool</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-623">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-623">Return Values</span></span>

- <span data-ttu-id="39e56-624">**NX_SUCCESS** (0x00) 正常に完了しました。</span><span class="sxs-lookup"><span data-stu-id="39e56-624">**NX_SUCCESS** (0x00) Successful completion.</span></span>
- <span data-ttu-id="39e56-625">**NX_NOT_ENABLED** (0x14) クライアントがこのオプション用に構成されていません</span><span class="sxs-lookup"><span data-stu-id="39e56-625">**NX_NOT_ENABLED** (0x14) Client not configured for this option</span></span>
- <span data-ttu-id="39e56-626">NX_PTR_ERROR (0x07) IP または DNS クライアント ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-626">NX_PTR_ERROR (0x07) Invalid IP or DNS Client pointer.</span></span>
- <span data-ttu-id="39e56-627">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-627">NX_CALLER_ERROR (0x11) Invalid caller of this service.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-628">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-628">Allowed From</span></span>

<span data-ttu-id="39e56-629">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-629">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-630">例</span><span class="sxs-lookup"><span data-stu-id="39e56-630">Example</span></span>
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

## <a name="nx_dns_server_add"></a><span data-ttu-id="39e56-631">nx_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="39e56-631">nx_dns_server_add</span></span>

<span data-ttu-id="39e56-632">DNS サーバーの IP アドレスを追加します</span><span class="sxs-lookup"><span data-stu-id="39e56-632">Add DNS Server IP Address</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-633">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-633">Prototype</span></span>
```C
UINT nx_dns_server_add(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="39e56-634">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-634">Description</span></span>

<span data-ttu-id="39e56-635">このサービスを使用すると、サーバー リストに IPv4 DNS サーバーが追加されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-635">This service adds an IPv4 DNS Server to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-636">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-636">Input Parameters</span></span>

- <span data-ttu-id="39e56-637">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-637">**dns_ptr** Pointer to DNS control block.</span></span>  
- <span data-ttu-id="39e56-638">**server_address** DNS サーバーの IP アドレス</span><span class="sxs-lookup"><span data-stu-id="39e56-638">**server_address** IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-639">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-639">Return Values</span></span>

- <span data-ttu-id="39e56-640">**NX_SUCCESS** (0x00) サーバーの追加に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-640">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="39e56-641">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="39e56-641">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="39e56-642">**NX_NO_MORE_ENTRIES** (0x17) これ以上の DNS サーバーは許可されません (リストがいっぱいです)</span><span class="sxs-lookup"><span data-stu-id="39e56-642">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers Allowed (list is full)</span></span>
- <span data-ttu-id="39e56-643">**NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-643">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="39e56-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-644">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-645">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-645">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="39e56-646">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-646">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) サーバー アドレスの入力が Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-647">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-648">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-648">Allowed From</span></span>

<span data-ttu-id="39e56-649">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-649">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-650">例</span><span class="sxs-lookup"><span data-stu-id="39e56-650">Example</span></span>
```C
/* Add a DNS Server at IP address 202.2.2.13. */
status =  nx_dns_server_add(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully added. */
```

## <a name="nxd_dns_server_add"></a><span data-ttu-id="39e56-651">nxd_dns_server_add</span><span class="sxs-lookup"><span data-stu-id="39e56-651">nxd_dns_server_add</span></span>

<span data-ttu-id="39e56-652">DNS サーバーをクライアント リストに追加します</span><span class="sxs-lookup"><span data-stu-id="39e56-652">Add DNS Server to the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-653">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-653">Prototype</span></span>
```C
UINT nxd_dns_server_add(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="39e56-654">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-654">Description</span></span>

<span data-ttu-id="39e56-655">このサービスを使用すると、DNS サーバーの IP アドレスが DNS クライアント サーバー リストに追加されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-655">This service adds the IP address of a DNS server to the DNS Client server list.</span></span> <span data-ttu-id="39e56-656">server_address には、IPv4 または IPv6 アドレスを指定できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-656">The server_address may be either an IPv4 or IPv6 address.</span></span> <span data-ttu-id="39e56-657">クライアントから IPv4 アドレスまたは IPv6 アドレスのいずれかで同じサーバーにアクセスできるようにする場合は、両方の IP アドレスをエントリとしてサーバー リストに追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="39e56-657">If the Client wishes to be able to access the same server by either its IPv4 address or IPv6 address it should add both IP addresses as entries to the server list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-658">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-658">Input Parameters</span></span>

- <span data-ttu-id="39e56-659">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-659">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="39e56-660">**server_address** DNS サーバーの IP アドレスが含まれている NXD_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-660">**server_address** Pointer to the NXD_ADDRESS containing the server IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-661">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-661">Return Values</span></span>

- <span data-ttu-id="39e56-662">**NX_SUCCESS** (0x00) サーバーの追加に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-662">**NX_SUCCESS** (0x00) Server successfully added</span></span>
- <span data-ttu-id="39e56-663">**NX_DNS_DUPLICATE_ENTRY**</span><span class="sxs-lookup"><span data-stu-id="39e56-663">**NX_DNS_DUPLICATE_ENTRY**</span></span>  
<span data-ttu-id="39e56-664">**NX_NO_MORE_ENTRIES** (0x17) これ以上の DNS サーバーは許可されません (リストがいっぱいです)</span><span class="sxs-lookup"><span data-stu-id="39e56-664">**NX_NO_MORE_ENTRIES** (0x17) No more DNS Servers allowed (list is full)</span></span> 
- <span data-ttu-id="39e56-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-665">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-666">**NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-666">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="39e56-667">NX_PTR_ERROR (0x07) ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-667">NX_PTR_ERROR (0x07) Invalid pointer input</span></span>
- <span data-ttu-id="39e56-668">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-668">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) サーバー アドレスの入力が Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-669">NX_DNS_BAD_ADDRESS_ERROR (0xA4) Null server address input</span></span>
- <span data-ttu-id="39e56-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-670">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-671">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-671">Allowed From</span></span>

<span data-ttu-id="39e56-672">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-672">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-673">例</span><span class="sxs-lookup"><span data-stu-id="39e56-673">Example</span></span>
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

## <a name="nx_dns_server_get"></a><span data-ttu-id="39e56-674">nx_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="39e56-674">nx_dns_server_get</span></span>

<span data-ttu-id="39e56-675">クライアント リストから IPv4 DNS サーバーを返します</span><span class="sxs-lookup"><span data-stu-id="39e56-675">Return an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-676">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-676">Prototype</span></span>
```C
UINT nx_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        ULONG *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="39e56-677">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-677">Description</span></span>

<span data-ttu-id="39e56-678">このサービスを使用すると、指定されたインデックス位置にあるサーバー リストから IPv4 DNS サーバー アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-678">This service returns the IPv4 DNS Server address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-679">インデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="39e56-679">The index is zero based.</span></span> <span data-ttu-id="39e56-680">入力インデックスが DNS クライアント リストのサイズを超えた場合は、そのインデックスで IPv6 アドレスが見つかるか、または指定されたインデックスで null アドレスが見つかると、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-680">If the input index exceeds the size of the DNS Client list, an IPv6 address is found at that index or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="39e56-681">クライアント リスト内の DNS サーバーの数を取得するため、*Nx_dns_get_serverlist_size* サービスを最初に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39e56-681">The *nx_dns_get_serverlist_size* service may be called first obtain the number of DNS servers in the Client list.</span></span>

<span data-ttu-id="39e56-682">このサービスでは、IPv4 アドレスのみがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="39e56-682">This service does only supports IPv4 addresses.</span></span> <span data-ttu-id="39e56-683">IPv4 アドレスと IPv6 アドレスの両方をサポートする *nxd_dns_server_get* サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="39e56-683">It calls the *nxd_dns_server_get* service which supports both IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-684">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-684">Input Parameters</span></span>

- <span data-ttu-id="39e56-685">**mdns_ptr**: DNS 制御ブロックを指すポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-685">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="39e56-686">**index** DNS クライアントのサーバーのリストにインデックスを作成します</span><span class="sxs-lookup"><span data-stu-id="39e56-686">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="39e56-687">**dns_server_address** DNS サーバーの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-687">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-688">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-688">Return Values</span></span>

- <span data-ttu-id="39e56-689">**NX_SUCCESS** (0x00) サーバーが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="39e56-689">**NX_SUCCESS** (0x00) Successful server returned</span></span>
- <span data-ttu-id="39e56-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) インデックスが空のスロットを指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-690">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="39e56-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) インデックスが Null アドレスを指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-691">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to Null address</span></span>
- <span data-ttu-id="39e56-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-692">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="39e56-693">**NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-693">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non-pointer input</span></span>
- <span data-ttu-id="39e56-694">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-694">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="39e56-695">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-695">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-696">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-696">Allowed From</span></span>

<span data-ttu-id="39e56-697">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-697">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-698">例</span><span class="sxs-lookup"><span data-stu-id="39e56-698">Example</span></span>
```C
ULONG my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nx_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nxd_dns_server_get"></a><span data-ttu-id="39e56-699">nxd_dns_server_get</span><span class="sxs-lookup"><span data-stu-id="39e56-699">nxd_dns_server_get</span></span>

<span data-ttu-id="39e56-700">クライアント リストから DNS サーバーを返します</span><span class="sxs-lookup"><span data-stu-id="39e56-700">Return a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-701">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-701">Prototype</span></span>
```C
UINT nxd_dns_server_get(NX_DNS *dns_ptr, UINT index, 
                        NXD_ADDRESS *dns_server_address);
```

### <a name="description"></a><span data-ttu-id="39e56-702">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-702">Description</span></span>

<span data-ttu-id="39e56-703">このサービスを使用すると、指定されたインデックス位置にあるサーバー リストから DNS サーバー IP アドレスが返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-703">This service returns the DNS Server IP address from the server list at the specified index.</span></span> 

> [!NOTE]
> <span data-ttu-id="39e56-704">インデックスは 0 から始まります。</span><span class="sxs-lookup"><span data-stu-id="39e56-704">The index is zero based.</span></span> <span data-ttu-id="39e56-705">入力インデックスが DNS クライアント リストのサイズを超えた場合、または指定されたインデックスで null アドレスが見つかった場合、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-705">If the input index exceeds the size of the DNS Client list, or a null address is found at the specified index, an error is returned.</span></span> <span data-ttu-id="39e56-706">サーバー リスト内の DNS サーバーの数を取得するため、*Nx_dns_get_serverlist_size* サービスを最初に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="39e56-706">The *nx_dns_get_serverlist_size* service may be called first to obtain the number of DNS servers in the server list.</span></span>

<span data-ttu-id="39e56-707">このサービスでは、IPv4 および IPv6 アドレスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="39e56-707">This service supports IPv4 and IPv6 addresses.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-708">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-708">Input Parameters</span></span>

- <span data-ttu-id="39e56-709">**mdns_ptr**: DNS 制御ブロックを指すポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-709">**dns_ptr** Pointer to DNS control block</span></span>  
- <span data-ttu-id="39e56-710">**index** DNS クライアントのサーバーのリストにインデックスを作成します</span><span class="sxs-lookup"><span data-stu-id="39e56-710">**index** Index into DNS Client’s list of servers</span></span>
- <span data-ttu-id="39e56-711">**dns_server_address** DNS サーバーの IP アドレスへのポインター</span><span class="sxs-lookup"><span data-stu-id="39e56-711">**dns_server_address** Pointer to IP address of DNS Server</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-712">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-712">Return Values</span></span>

- <span data-ttu-id="39e56-713">**NX_SUCCESS** (0x00) サーバーの IP アドレスが正常に返されました</span><span class="sxs-lookup"><span data-stu-id="39e56-713">**NX_SUCCESS** (0x00) Successfully returned server IP address</span></span>
- <span data-ttu-id="39e56-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) インデックスが空のスロットを指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-714">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Index points to empty slot</span></span>
- <span data-ttu-id="39e56-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) インデックスが Null サーバー アドレスを指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-715">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Index points to null server address</span></span>
- <span data-ttu-id="39e56-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-716">**NX_DNS_INVALID_ADDRESS_TYPE** (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>
- <span data-ttu-id="39e56-717">**NX_DNS_PARAM_ERROR** (0xA8) 非ポインター入力が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-717">**NX_DNS_PARAM_ERROR** (0xA8) Invalid non pointer input</span></span>
- <span data-ttu-id="39e56-718">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-718">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="39e56-719">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-719">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-720">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-720">Allowed From</span></span>

<span data-ttu-id="39e56-721">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-721">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-722">例</span><span class="sxs-lookup"><span data-stu-id="39e56-722">Example</span></span>
```C
NXD_ADDRESS my_server_address;

/* Get the DNS Server at index 5 (zero based) into the Client list. */
status =  nxd_dns_server_get(&my_dns, 5, &my_server_addres);

/* If status is NX_SUCCESS a DNS Server was successfully
   returned. */
```

## <a name="nx_dns_server_remove"></a><span data-ttu-id="39e56-723">nx_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="39e56-723">nx_dns_server_remove</span></span>

<span data-ttu-id="39e56-724">クライアント リストから IPv4 DNS サーバーを削除します</span><span class="sxs-lookup"><span data-stu-id="39e56-724">Remove an IPv4 DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-725">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-725">Prototype</span></span>
```C
UINT nx_dns_server_remove(NX_DNS *dns_ptr, ULONG server_address);
```
### <a name="description"></a><span data-ttu-id="39e56-726">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-726">Description</span></span>

<span data-ttu-id="39e56-727">このサービスを使用すると、クライアント リストから IPv4 DNS サーバーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-727">This service removes an IPv4 DNS Server from the Client list.</span></span> <span data-ttu-id="39e56-728">これは *nxd_dns_server_remove* のラッパー関数です。</span><span class="sxs-lookup"><span data-stu-id="39e56-728">It is a wrapper function for *nxd_dns_server_remove*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-729">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-729">Input Parameters</span></span>

- <span data-ttu-id="39e56-730">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-730">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="39e56-731">**server_address** DNS サーバーの IP アドレス。</span><span class="sxs-lookup"><span data-stu-id="39e56-731">**server_address** IP address of DNS Server.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-732">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-732">Return Values</span></span>

- <span data-ttu-id="39e56-733">**NX_SUCCESS** (0x00) DNS サーバーの削除に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-733">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="39e56-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) サーバーがクライアント リストにありません</span><span class="sxs-lookup"><span data-stu-id="39e56-734">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="39e56-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) サーバー アドレスの入力が Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-735">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="39e56-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-736">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-737">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-737">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="39e56-738">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-738">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-739">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-739">Allowed From</span></span>

<span data-ttu-id="39e56-740">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-740">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-741">例</span><span class="sxs-lookup"><span data-stu-id="39e56-741">Example</span></span>
```C
/* Remove the DNS Server at IP address is 202.2.2.13.  */
status =  nx_dns_server_remove(&my_dns, IP_ADDRESS(202,2,2,13));

/* If status is NX_SUCCESS a DNS Server was successfully
   removed.  */
```

## <a name="nxd_dns_server_remove"></a><span data-ttu-id="39e56-742">nxd_dns_server_remove</span><span class="sxs-lookup"><span data-stu-id="39e56-742">nxd_dns_server_remove</span></span>

<span data-ttu-id="39e56-743">クライアント リストから DNS サーバーを削除します</span><span class="sxs-lookup"><span data-stu-id="39e56-743">Remove a DNS Server from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-744">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-744">Prototype</span></span>
```C
UINT nxd_dns_server_remove(NX_DNS *dns_ptr, NXD_ADDRESS *server_address);
```
### <a name="description"></a><span data-ttu-id="39e56-745">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-745">Description</span></span>

<span data-ttu-id="39e56-746">このサービスを使用すると、指定された IP アドレスの DNS サーバーがクライアント リストから削除されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-746">This service removes a DNS Server of the specified IP address from the Client list.</span></span> <span data-ttu-id="39e56-747">入力 IP アドレスには、IPv4 アドレスと IPv6 アドレスの両方を指定できます。</span><span class="sxs-lookup"><span data-stu-id="39e56-747">The input IP address accepts both IPv4 and IPv6 addresses.</span></span> <span data-ttu-id="39e56-748">サーバーを削除すると、空いているスロットを埋めるために、残っているサーバーは、リスト内の 1 つ下のインデックスに移動します。</span><span class="sxs-lookup"><span data-stu-id="39e56-748">After the server is removed, the remaining servers move down one index in the list to fill the vacated slot.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-749">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-749">Input Parameters</span></span>

- <span data-ttu-id="39e56-750">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-750">**dns_ptr** Pointer to DNS control block.</span></span>
- <span data-ttu-id="39e56-751">**server_address** サーバーの IP アドレスを含む DNS サーバー NXD_ADDRESS へのポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-751">**server_address** Pointer to DNS Server NXD_ADDRESS data containing server IP address.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-752">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-752">Return Values</span></span>

- <span data-ttu-id="39e56-753">**NX_SUCCESS** (0x00) DNS サーバーの削除に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-753">**NX_SUCCESS** (0x00) DNS Server successfully removed</span></span>
- <span data-ttu-id="39e56-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) サーバーがクライアント リストにありません</span><span class="sxs-lookup"><span data-stu-id="39e56-754">**NX_DNS_SERVER_NOT_FOUND** (0xA9) Server not in Client list</span></span>
- <span data-ttu-id="39e56-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) サーバー アドレスの入力が Null です</span><span class="sxs-lookup"><span data-stu-id="39e56-755">**NX_DNS_BAD_ADDRESS_ERROR** (0xA4) Null server address input</span></span>
- <span data-ttu-id="39e56-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) IPv6 が無効になっているレコードは処理できません</span><span class="sxs-lookup"><span data-stu-id="39e56-756">**NX_DNS_IPV6_NOT_SUPPORTED** (0xB3) Cannot process record with IPv6 disabled</span></span>
- <span data-ttu-id="39e56-757">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-757">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="39e56-758">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-758">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>
- <span data-ttu-id="39e56-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) インデックスが無効なアドレスの種類 (IPv6 など) を指しています</span><span class="sxs-lookup"><span data-stu-id="39e56-759">NX_DNS_INVALID_ADDRESS_TYPE (0xB2) Index points to invalid address type (e.g. IPv6)</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-760">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-760">Allowed From</span></span>

<span data-ttu-id="39e56-761">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-761">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-762">例</span><span class="sxs-lookup"><span data-stu-id="39e56-762">Example</span></span>
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

## <a name="nx_dns_server_remove_all"></a><span data-ttu-id="39e56-763">nx_dns_server_remove_all</span><span class="sxs-lookup"><span data-stu-id="39e56-763">nx_dns_server_remove_all</span></span>

<span data-ttu-id="39e56-764">すべての DNS サーバーをクライアント リストから削除します</span><span class="sxs-lookup"><span data-stu-id="39e56-764">Remove all DNS Servers from the Client list</span></span>

### <a name="prototype"></a><span data-ttu-id="39e56-765">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="39e56-765">Prototype</span></span>
```C
UINT nx_dns_server_remove_all(NX_DNS *dns_ptr);
```
### <a name="description"></a><span data-ttu-id="39e56-766">説明</span><span class="sxs-lookup"><span data-stu-id="39e56-766">Description</span></span>

<span data-ttu-id="39e56-767">このサービスを使用すると、クライアント リストからすべての DNS サーバーが削除されます。</span><span class="sxs-lookup"><span data-stu-id="39e56-767">This service removes all DNS Servers from the Client list.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="39e56-768">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="39e56-768">Input Parameters</span></span>

- <span data-ttu-id="39e56-769">**mdns_ptr**: DNS 制御ブロックを指すポインター。</span><span class="sxs-lookup"><span data-stu-id="39e56-769">**dns_ptr** Pointer to DNS control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="39e56-770">戻り値</span><span class="sxs-lookup"><span data-stu-id="39e56-770">Return Values</span></span>

- <span data-ttu-id="39e56-771">**NX_SUCCESS** (0x00) DNS サーバーの削除に成功しました</span><span class="sxs-lookup"><span data-stu-id="39e56-771">**NX_SUCCESS** (0x00) DNS Servers successfully removed</span></span>
- <span data-ttu-id="39e56-772">**NX_DNS_ERROR** (0xA0) 保護ミューテックスを取得できません</span><span class="sxs-lookup"><span data-stu-id="39e56-772">**NX_DNS_ERROR** (0xA0) Unable to obtain protection mutex</span></span>
- <span data-ttu-id="39e56-773">NX_PTR_ERROR (0x07) IP または DNS ポインターが無効です。</span><span class="sxs-lookup"><span data-stu-id="39e56-773">NX_PTR_ERROR (0x07) Invalid IP or DNS pointer.</span></span>
- <span data-ttu-id="39e56-774">NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です</span><span class="sxs-lookup"><span data-stu-id="39e56-774">NX_CALLER_ERROR (0x11) Invalid caller of this service</span></span>

### <a name="allowed-from"></a><span data-ttu-id="39e56-775">許可元</span><span class="sxs-lookup"><span data-stu-id="39e56-775">Allowed From</span></span>

<span data-ttu-id="39e56-776">Threads</span><span class="sxs-lookup"><span data-stu-id="39e56-776">Threads</span></span>

### <a name="example"></a><span data-ttu-id="39e56-777">例</span><span class="sxs-lookup"><span data-stu-id="39e56-777">Example</span></span>
```C
/* Remove all DNS Servers from the Client list. */
status =  nx_dns_server_remove_all(&my_dns);

/* If status is NX_SUCCESS all DNS Servers were successfully removed. */
```