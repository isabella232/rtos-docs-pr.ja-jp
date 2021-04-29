---
title: 第 2 章 - Azure RTOS NetX DNS クライアントのインストールと使用
description: この章では、Azure RTOS NetX DNS クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 054b7366eb9a28bc0dc2fb8c4b2479c12532499b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811570"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-dns-client"></a>第 2 章 - Azure RTOS NetX DNS クライアントのインストールと使用

この章では、Azure RTOS NetX DNS クライアントのインストール、セットアップ、使用に関するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

NetX DNS クライアントは <https://github.com/azure-rtos/netx> で入手できます。 パッケージには、次のファイルが含まれています。

- **nx_dns.h**: NetX DNS クライアントのヘッダー ファイル
- **nx_dns.c**: NetX DNS クライアントの C 言語のソース ファイル
- **nx_dns.pdf**: NetX DNS クライアントの説明書の PDF ファイル

## <a name="dns-client-installation"></a>DNS クライアントのインストール

NetX DNS クライアントを使用するには、ソース コード ファイル *nxd_dns.c* と *nxd_dns.h* を NetX がインストールされているのと同じディレクトリにコピーします。 たとえば、NetX がディレクトリ " *\threadx\arm7\green*" にインストールされている場合は、*nx_dns.h* および *nx_dns.c* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-the-dns-client"></a>DNS クライアントの使用

NetX DNS クライアントの使用方法は簡単です。 基本的に、ThreadX と NetX を使用するには、アプリケーション コードに、それぞれ *tx_api.h* と *nx_api.h* をインクルードした後に *nx_dns.h* をインクルードする必要があります。 *nx_dns.h* をインクルードすると、このガイドで後述する DNS の関数を、そのアプリケーションのコードで呼び出せるようになります。 また、アプリケーションのビルドには *nx_dns.c* を追加する必要があります。 このファイルは、他のアプリケーション ファイルと同様にコンパイルする必要があり、そのオブジェクト形式は、アプリケーションのファイルと一緒にリンクする必要があります。 NetX DNS を使用するために必要なことはこれだけです。

>[!NOTE]
> DNS では NetX UDP のサービスを使用するため、DNS を使用するときは、前もって *nx_udp_enable* を呼び出して UDP を有効にしておく必要があります。

## <a name="small-example-system-for-dns-client"></a>DNS クライアントの小規模なシステム例 

このセクションで示す DNS アプリケーション プログラムの例では、6 行目で *nx_dns.h* をインクルードします。 21 から 23 行目では NX_DNS_CLIENT_USER_CREATE_PACKET_POOL を宣言し、DNS クライアント アプリケーションが DNS クライアントのパケット プールを作成できるようにしています。 このパケット プールは、DNS メッセージの送信に使用するパケットを割り当てるのに使用します。 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が定義されている場合、71 から 91 行目でパケット プールを作成します。 このオプションが有効でない場合、DNS クライアントは、*nx_dns.h* の構成パラメーターで設定されるパケットのペイロードとパケット プールのサイズに応じて、専用のパケット プールを作成します。パケットのペイロードとパケット プールのサイズの設定については、この章の他の箇所で説明します。

NetX Duo の内部操作に使用するクライアントの IP インスタンスのために、93 から 105 行目でもう 1 つパケット プールを作成します。 次に、107 から 119 行目で *nx_ip_create* を呼び出して IP インスタンスを作成します。 IP タスクと DNS クライアントでは同じパケット プールを共有できますが、通常、DNS クライアントから送信されるメッセージの方が IP タスクが送信する制御パケットよりも大きいため、別々のパケット プールを使用する方が効率的にメモリを使用できます。

122 行目と 134 行目で ARP と UDP (IPv4 ネットワークで使用) をそれぞれ有効にします。

>[!NOTE]
> このデモでは、37 行目で "ram" ドライバーを宣言し、*nx_ip_create* の呼び出しでこれを使用しています。 この RAM ドライバーは、NetX のソース コードと合わせて配布されています。 DNS クライアントを実行するには、実際に使用する物理ネットワーク ドライバーをアプリケーションで指定して、DNS サーバーに対しパケットを送受信する必要があります。

クライアント スレッド エントリ関数 *thread_client_entry* を *tx_application_define* 関数の下で定義します。 ここでは最初にシステムの制御を放棄し、ネットワーク ドライバーで IP タスク スレッドを初期化できるようにします。

次に、176 から 187 行目で DNS クライアントを作成し、189 から 200 行目でキャッシュを初期化し、202 から 217 行目で、先に作成したパケット プールを DNS クライアント インスタンスに割り当てます。 次に、220 から 229 行目で IPv4 DNS サーバーを追加します。

サンプル プログラムの残りの部分では、DNS クライアントのサービスを使用して DNS クエリを実行しています。 240 行目と 262 行目でホストの IP アドレスの検索が実行されます。 これら 2 つのサービス (*nx_dns_host_by_name_get* と *nx_dns_ipv4_address_by_name_get*) の違いは、前者の場合 1 つの IP アドレスのみが保存されるのに対し、後者の場合は DNS サーバーから応答された場合に複数のアドレスが保存されるという点です。

(IP アドレスからホスト名の) 逆引き参照は、354 行目 (*nx_dns_host_by_address_get* ) で実行されます。

375 行目と 420 行目では、別の 2 つの DNS 検索サービス CNAME と TXT を使用して、入力したドメイン名に対する CNAME と TXT を取得する方法を、それぞれ例示しています。 NetX DNS クライアントには、NS、MX、SRV、SOA など他の種類のレコードに対しても同様のサービスが存在します。 NetX DNS クライアントで検索できるレコードの種類すべての詳しい説明については、第 3 章を参照してください。

594 行目で *nx_dns_delete* サービスを使用して DNS クライアントを削除するとき、専用のパケット プールを作成した場合を除き、この DNS クライアントのパケット プールは削除されません。 その他の場合、それ以上使用しないパケット プールを削除するかどうかはアプリケーションに任されています。

```c
/* This is a small demo of DNS Client for the high-performance NetX TCP/IP stack.*/
#include "tx_api.h"
#include "nx_api.h"
#include "nx_udp.h"
#include "nx_dns.h"

#define     DEMO_STACK_SIZE         4096
#define     NX_PACKET_PAYLOAD       1536
#define     NX_PACKET_POOL_SIZE     30 * NX_PACKET_PAYLOAD
#define     LOCAL_CACHE_SIZE        2048

/* Define the ThreadX and NetX object control blocks... */

NX_DNS             client_dns;
TX_THREAD          client_thread;
NX_IP              client_ip;
NX_PACKET_POOL     main_pool;

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL
    NX_PACKET_POOL client_pool;
#endif

UCHAR       local_cache[LOCAL_CACHE_SIZE];
UINT        error_counter = 0;
#define     CLIENT_ADDRESS IP_ADDRESS(192,168,0,11)
#define     DNS_SERVER_ADDRESS IP_ADDRESS(192,168,0,1)

/* Define thread prototypes. */
void        thread_client_entry(ULONG thread_input);

/***** Substitute your ethernet driver entry function here *********/
extern     VOID _nx_ram_network_driver(NX_IP_DRIVER *driver_req_ptr);

/* Define main entry point. */
int main()
{
/* Enter the ThreadX kernel. */
    tx_kernel_enter();
}
/* Define what the initial system looks like. */
void tx_application_define(void *first_unused_memory)
{
    CHAR     *pointer;
    UINT     status;
    /* Setup the working pointer. */
    pointer = (CHAR *) first_unused_memory;
    /* Create the main thread. */
    tx_thread_create(&client_thread, "Client thread", 
                     thread_client_entry, 0, pointer, 
                     DEMO_STACK_SIZE, 4, 4, TX_NO_TIME_SLICE, 
                     TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system. */
    nx_system_initialize();

#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /*Create the packet pool for the DNS Client to send packets. If the DNS Client is configured for letting the host application create the DNS packet pool, 
        (see NX_DNS_CLIENT_USER_CREATE_PACKET_POOL option), see 77 nx_dns_create() for guidelines on packet payload size and pool size. 
        packet traffic for NetX processes.
    */

    status = nx_packet_pool_create(&client_pool, "DNS Client Packet Pool", 
                                   NX_DNS_PACKET_PAYLOAD, pointer, 
                                   NX_DNS_PACKET_POOL_SIZE);

    pointer = pointer + NX_DNS_PACKET_POOL_SIZE;
    /* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

#endif
/* Create the packet pool which the IP task will use to send packets. Also available to the host 94 application to send packet. */

    status = nx_packet_pool_create(&main_pool, "Main Packet Pool", 
                                   NX_PACKET_PAYLOAD, pointer, 
                                   NX_PACKET_POOL_SIZE);
    pointer = pointer + NX_PACKET_POOL_SIZE;

/* Check for pool creation error. */
    if (status)
    {
        error_counter++;
        return;
    }

/* Create an IP instance for the DNS Client. */
    status = nx_ip_create(&client_ip, "DNS Client IP Instance", 
                          CLIENT_ADDRESS, 0xFFFFFF00UL, 
                          &main_pool, _nx_ram_network_driver, 
                          pointer, 2048, 1);
    pointer = pointer + 2048;

/* Check for IP create errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable ARP and supply ARP cache memory for the DNS Client IP. */
    status = nx_arp_enable(&client_ip, (void *) pointer, 1024);
    pointer = pointer + 1024;

/* Check for ARP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }
/* Enable UDP traffic because DNS is a UDP based protocol. */

    status = nx_udp_enable(&client_ip);
/* Check for UDP enable errors. */
    if (status)
    {
        error_counter++;
        return;
    }

}

#define BUFFER_SIZE 200
#define RECORD_COUNT 10

/* Define the Client thread. */
void thread_client_entry(ULONG thread_input)
{
    UCHAR         record_buffer[200];
    UINT          record_count;
    UINT          status;
    ULONG         host_ip_address;
    UINT          i;
    ULONG         *ipv4_address_ptr[RECORD_COUNT];

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
    NX_DNS_NS_ENTRY    *nx_dns_ns_entry_ptr[RECORD_COUNT];
    NX_DNS_MX_ENTRY    *nx_dns_mx_entry_ptr[RECORD_COUNT];
    NX_DNS_SRV_ENTRY    *nx_dns_srv_entry_ptr[RECORD_COUNT];
    NX_DNS_SOA_ENTRY    *nx_dns_soa_entry_ptr;
    ULONG                host_address;
    USHORT               host_port;
#endif

    /* Give NetX IP task a chance to get initialized . */
    tx_thread_sleep(100);
    /* Create a DNS instance for the Client. Note this function will create the DNS Client packet pool for creating DNS message packets intended for querying its DNS server. */
    status = nx_dns_create(&client_dns, &client_ip, (UCHAR *)"DNS Client");

    /* Check for DNS create error. */
    if (status)
    {
        error_counter++;
        return;
    }

#ifdef NX_DNS_CACHE_ENABLE
    /* Initialize the cache. */
    status = nx_dns_cache_initialize(&client_dns, local_cache, LOCAL_CACHE_SIZE);

    /* Check for DNS cache error. */
    if (status)
    {
        error_counter++;
        return;
    }
#endif

/* Is the DNS client configured for the host application to create the pecket pool? */
#ifdef NX_DNS_CLIENT_USER_CREATE_PACKET_POOL

    /* Yes, use the packet pool created above which has appropriate payload size for DNS messages. */
    status = nx_dns_packet_pool_set(&client_dns, &client_pool);
    /* Check for set DNS packet pool error. */
        
    if (status)
    {
        error_counter++;
        return;
    }
#endif /* NX_DNS_CLIENT_USER_CREATE_PACKET_POOL */

    /* Add an IPv4 server address to the Client list. */
    status = nx_dns_server_add(&client_dns, DNS_SERVER_ADDRESS);
    /* Check for DNS add server error. */
    if (status)
    {
        error_counter++;
        return;
    }
/********************************************************************************/
/* Type A */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/

    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }
    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
               *ipv4_address_ptr[i] >> 24,
               *ipv4_address_ptr[i] >> 16 & 0xFF,
               *ipv4_address_ptr[i] >> 8 & 0xFF,
               *ipv4_address_ptr[i] & 0xFF);
    }
/********************************************************************************/
/* Type A + CNAME response */
/* Send A type DNS Query to its DNS server and get the IPv4 address. */
/********************************************************************************/
    
    /* Look up an IPv4 address over IPv4. */
    status = nx_dns_host_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", &host_ip_address, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test A + CNAME response: \n");
        printf("IP address: %lu.%lu.%lu.%lu\n",
        host_ip_address >> 24,
        host_ip_address >> 16 & 0xFF,
        host_ip_address >> 8 & 0xFF,
        host_ip_address & 0xFF);
    }

    /* Look up IPv4 addresses to record multiple IPv4 addresses in record_buffer and return the IPv4 address count. */
    status = nx_dns_ipv4_address_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 
                                             &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test Test A + CNAME response: ");
        printf("record_count = %d \n", record_count);
    }
    
    /* Get the IPv4 addresses of host. */
    for(i =0; i< record_count; i++)
    {
        ipv4_address_ptr[i] = (ULONG *)(record_buffer + i * sizeof(ULONG));
        printf("record %d: IP address: %lu.%lu.%lu.%lu\n", i,
                *ipv4_address_ptr[i] >> 24,
                *ipv4_address_ptr[i] >> 16 & 0xFF,
                *ipv4_address_ptr[i] >> 8 & 0xFF,
                *ipv4_address_ptr[i] & 0xFF);
    }

/********************************************************************************/
/* Type PTR */
/* Send PTR type DNS Query to its DNS server and get the host name. */
/********************************************************************************/

    /* Look up host name over IPv4. */
    host_ip_address = IP_ADDRESS(74, 125, 71, 106);
    status = nx_dns_host_by_address_get(&client_dns, host_ip_address, &record_buffer[0], BUFFER_SIZE, 450);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test PTR: %s\n", record_buffer);
    }

#ifdef NX_DNS_ENABLE_EXTENDED_RR_TYPES
/********************************************************************************/
/* Type CNAME */
/* Send CNAME type DNS Query to its DNS server and get the canonical name . */
/********************************************************************************/

    /* Send CNAME type to record the canonical name of host in record_buffer. */

    status = nx_dns_cname_get(&client_dns, (UCHAR *)"www.my_example.com", 
                              &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test CNAME: %s\n", record_buffer);
    }
/********************************************************************************/
/* Type TXT */
/* Send TXT type DNS Query to its DNS server and get descriptive text. */
/********************************************************************************/

    /* Send TXT type to record the descriptive test of host in record_buffer. */
    status = nx_dns_host_text_get(&client_dns, (UCHAR *)"www.my_example.com", &record_buffer[0], BUFFER_SIZE, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test TXT: %s\n", record_buffer);
    }

/********************************************************************************/
/* Type NS */
/* Send NS type DNS Query to its DNS server and get the domain name server. */
/********************************************************************************/

    /* Send NS type to record multiple name servers in record_buffer and return the name server count. If the DNS response includes the IPv4 addresses of name server, record it similarly in record_buffer. */

    status = nx_dns_domain_name_server_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                           &record_buffer[0], BUFFER_SIZE, 
                                           &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test NS: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the name server. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_ns_entry_ptr[i] = (NX_DNS_NS_ENTRY *)(record_buffer + i * sizeof(NX_DNS_NS_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 24,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 16 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address >> 8 & 0xFF,
                nx_dns_ns_entry_ptr[i] -> nx_dns_ns_ipv4_address & 0xFF);
        
        if(nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr)
            printf("hostname = %s\n", nx_dns_ns_entry_ptr[i] -> nx_dns_ns_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

/********************************************************************************/
/* Type MX */
/* Send MX type DNS Query to its DNS server and get the domain mail exchange. */
/********************************************************************************/

    /* Send MX DNS query type to record multiple mail exchanges in record_buffer and return the mail exchange count. If the DNS response includes the IPv4 addresses of mail exchange, record it similarly in record_buffer. */

    status = nx_dns_domain_mail_exchange_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, &record_count, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test MX: ");
        printf("record_count = %d \n", record_count);
    }
    /* Get the mail exchange. */
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

/********************************************************************************/
/* Type SRV */
/* Send SRV type DNS Query to its DNS server and get the location of services. */
/********************************************************************************/

    /* Send SRV DNS query type to record the location of services in record_buffer and return count. If the DNS response includes the IPv4 addresses of service name, record it similarly in record_buffer. */

    status = nx_dns_domain_service_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                       &record_buffer[0], BUFFER_SIZE, &record_count, 400);
    
    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("record_count = %d \n", record_count);
    }
    
    /* Get the location of services. */
    for(i =0; i< record_count; i++)
    {
        nx_dns_srv_entry_ptr[i] = (NX_DNS_SRV_ENTRY *)(record_buffer + i * sizeof(NX_DNS_SRV_ENTRY));
        printf("record %d: IP address: %d.%d.%d.%d\n", i,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 24,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 16 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address >> 8 & 0xFF,
                nx_dns_srv_entry_ptr[i] -> nx_dns_srv_ipv4_address & 0xFF);

        printf("port number = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_port_number );
        printf("priority = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_priority );
        printf("weight = %d\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_weight );

        if(nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr)
            printf("hostname = %s\n", nx_dns_srv_entry_ptr[i] -> nx_dns_srv_hostname_ptr);
        else
            printf("hostname is not set\n");
    }

    /* Get the service info, NetX old API.*/
    status = nx_dns_info_by_name_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                     &host_address, &host_port, 200);
    /* Check for DNS add server error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    else
    {
        printf("------------------------------------------------------> n");
        printf("Test SRV: ");
        printf("IP address: %d.%d.%d.%d\n",
                host_address >> 24,
                host_address >> 16 & 0xFF,
                host_address >> 8 & 0xFF,
                host_address & 0xFF);
        printf("port number = %d\n", host_port);
    }
    
/********************************************************************************/
/* Type SOA */
/* Send SOA type DNS Query to its DNS server and get zone of start of authority.*/
/********************************************************************************/

    /* Send SOA DNS query type to record the zone of start of authority in record_buffer. */

    status = nx_dns_authority_zone_start_get(&client_dns, (UCHAR *)"www.my_example.com", 
                                             &record_buffer[0], BUFFER_SIZE, 400);

    /* Check for DNS query error. */
    if (status != NX_SUCCESS)
    {
        error_counter++;
    }
    
    /* Get the loc*/
    nx_dns_soa_entry_ptr = (NX_DNS_SOA_ENTRY *) record_buffer;
    printf("------------------------------------------------------> n");
    printf("Test SOA: \n");
    printf("serial = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_serial );
    printf("refresh = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_refresh );
    printf("retry = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_retry );
    printf("expire = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_expire );
    printf("minmum = %d\n", nx_dns_soa_entry_ptr -> nx_dns_soa_minmum );
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr)
        printf("host mname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_mname_ptr);
    else
        printf("host mame is not set\n");
    if(nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr)
        printf("host rname = %s\n", nx_dns_soa_entry_ptr -> nx_dns_soa_host_rname_ptr);
    else
        printf("host rname is not set\n");
    #endif

    /* Shutting down...*/
    /* Terminate the DNS Client thread. */
    status = nx_dns_delete(&client_dns);
    return;
}
```

## <a name="configuration-options"></a>構成オプション

NetX 用に DNS を構築するための構成オプションはいくつかあります。 それらのオプションは *nx_dns.h* で再設定できます。 次の一覧で、それぞれについて詳しく説明します。  

- **NX_DNS_TYPE_OF_SERVICE**: DNS UDP 要求に必要なサービスの種類です。 既定値は、通常の IP パケット サービスを表す NX_IP_NORMAL です。

- **NX_DNS_TIME_TO_LIVE**: パケットが通過できるルーターの最大数を指定します。この数を超えるとパケットは破棄されます。 既定値は 0x80 です。

- **NX_DNS_FRAGMENT_OPTION**: 送信パケットのフラグメント化を許可または拒否するようにソケットのプロパティを設定します。 既定値は NX_DONT_FRAGMENT です。

- **NX_DNS_QUEUE_DEPTH**: ソケットの受信キューに保持できるパケットの最大数を設定します。 既定値は 5 です。

- **NX_DNS_MAX_SERVERS**: クライアント サーバー リストの DNS サーバーの最大数を指定します。

- **NX_DNS_MESSAGE_MAX**: DNS クエリを送信する DNS メッセージの最大サイズです。 既定値は 512 です。これは RFC 1035 セクション 2.3.4 で指定されている最大サイズです。

- **NX_DNS_PACKET_PAYLOAD_UNALIGNED**: これを指定しない場合、クライアント パケットのペイロードのサイズに、イーサネット、IP (または IPv6)、UDP ヘッダー、NX_DNS_MESSAGE_MAX で指定された DNS メッセージの最大サイズを含むサイズを使用します。 指定されているかどうかにかかわらず、パケットのペイロードは 4 バイトでアラインされ NX_DNS_PACKET_PAYLOAD に保存されます。

- **NX_DNS_PACKET_POOL_SIZE**: NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が指定されていない場合に、DNS クエリの送信に使用するクライアントのパケット プールのサイズを指定します。 既定値は、NX_DNS_PACKET_PAYLOAD で指定されたサイズのペイロードのパケット 16 個を処理するのに十分な大きさであり、アライメントは 4 バイトです。

- **NX_DNS_MAX_RETRIES**: DNS クライアントが現在の DNS サーバーにクエリを送信する最大回数です。この回数を超えると他のサーバーを試すか DNS クエリを破棄します。

- **NX_DNS_MAX_RETRANS_TIMEOUT**: DNS クエリを特定の DNS サーバーに再送信する際の最長タイムアウト時間です。 既定値は 64 秒 (64 *NX_IP_PERIODIC_RATE) です。

- **NX_DNS_IP_GATEWAY_AND_DNS_SERVER**: これが指定され、かつクライアントの IPv4 ゲートウェイのアドレスが 0 以外に設定されている場合、DNS クライアントでその IPv4 ゲートウェイが優先 DNS サーバーに設定されます。 既定値は、無効です。

- **NX_DNS_PACKET_ALLOCATE_TIMEOUT**: DNS クライアントのパケット プールからパケットを割り当てる際のタイムアウト オプションを設定します。 既定値は 1 秒 (1*NX_IP_PERIODIC_RATE) です。

- **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL**: DNS クライアントで、アプリケーションによる DNS クライアントのパケット プールの作成と設定を有効にします。 このオプションは既定で無効になっており、DNS クライアントは *nx_dns_create* で独自のパケット プールを作成します。

- **NX_DNS_CLIENT_CLEAR_QUEUE**: DNS クライアントで、新しいクエリを送信する前に、受信キューの古い DNS メッセージを削除できるようにします。 DNS クエリの古いパケットを削除すると、DNS クライアントのソケット キューでオーバーフローが起こることと有効なパケットが破棄されることを防止できます。

- **NX_DNS_ENABLE_EXTENDED_RR_TYPES**: DNS クライアントでクエリを実行できるレコードの種類を追加します (CNAME、NS、MX、SOA、SRV、TXT など)。

- **NX_DNS_CACHE_ENABLE**: DNS クライアントで応答レコードを DNS キャッシュに保存できるようにします。
