---
title: 第 2 章 - Azure RTOS NetX Secure のインストールと使用
description: この章では、NetX Secure コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d11e50b2ab74ee147f682567d142768de6108fc18264e9d8bc69bbfc8a32cc0a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801871"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-secure"></a>第 2 章 - Azure RTOS NetX Secure のインストールと使用

この章では、Azure RTOS NetX Secure コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。

## <a name="product-version-number"></a>製品バージョン番号

ユーザーは nx_secure_tls.h で次のシンボルを見つけて、製品のバージョン番号を確認できます。

***NETX_SECURE_MAJOR_VERSION***

***NETX_SECURE_MINOR_VERSION***

サービス パックのリリースでは、サービス パック番号を示す次のシンボルが定義されています。

***NETX_SECURE_SERVICE_PACK_VERSION***

## <a name="product-distribution"></a>製品ディストリビューション

NetX Secure は [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。 パッケージに含まれているソース ファイル、インクルード ファイル、このドキュメントを含む PDF ファイルを以下に示します。

- **nx_secure_tls_api.h** NetX Secure TLS のパブリック API ヘッダー ファイル
- **nx_secure_tls_user.h** NetX Secure TLS のユーザー定義ヘッダー ファイル
- **nx_secure_tls_port.h** NetX Secure のプラットフォーム固有の定義
- **nx_secure_tls.h** NetX Secure TLS のヘッダーファイル
- **nx_secure_tls&#42;.c/h** NetX Secure TLS の C/H ソース ファイル
- **nx_crypto&#42;.c/h** NetX Secure Cryptography の C/H ソース ファイル
- **nx_secure_x509&#42;.c/h** X.509 デジタル証明書の C/H ソース ファイル。
- **demo_netx_secure_tls.c** NetX Secure TLS Demo の C ソース ファイル
- **NetX_Secure_User_Guide.pdf** NetX Secure 製品の PDF 説明書

> [!NOTE]
> さまざまなハードウェア プラットフォームのための nx_crypto* ファイルが、NetX Secure 親ディレクトリのサブディレクトリに用意されています。

## <a name="netx-secure-installation"></a>NetX Secure のインストール

NetX Secure を使用するためには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリ レベルにコピーする必要があります。 たとえば、NetX がディレクトリ " *\threadx\arm7\NetX*" にインストールされている場合は、*nx_secure**.* ディレクトリを " *\threadx\arm7\NetXSecure*" にコピーする必要があります。

## <a name="using-netx-secure"></a>NetX Secure を使用する

NetX Secure TLS の使用は簡単です。 基本的に、ThreadX と NetX を使用するために、アプリケーション コードには、*tx_api.h* と *nx_api.h* をインクルードした後に *nx_secure_tls_api.h* を含める必要があります。 *nx_secure_tls_api.h* をインクルードすると、アプリケーション コードは、このガイドの後半で指定している NetX Secure 関数呼び出しができるようになります。 アプリケーションは *nx_secure**.* ファイルを NetXSecure ライブラリにインポートし、プラットフォーム固有の *nx_crypto**.* ファイルを NetXCrypto ライブラリにインポートする必要もあります。

## <a name="small-example-system-tls-client"></a>小さなシステム例 (TLS クライアント)

NetX Secure の使用がいかに簡単であるかを示す例について、下の図 1.1 で説明しています。 これは、ソフトウェア暗号化モジュール (ハードウェア固有でない) を暗号化で使用する単純な TLS クライアントを示しています。 OpenSSL リバースエコー サーバー (openssl s_server -rev) と連携するように設計されています。

この例を実行するために、x.509 CA 証明書を使用してターゲット サーバーの証明書を認証する必要があることに注意してください。 OpenSSL の例では、単純な 2 レベル PKI (ルート CA 証明書 -> >サーバー証明書) で十分です。 "trusted_ca_data" 配列に DER エンコード バイナリ バージョンの CA 証明書を入力し、"trusted_ca_length" 変数を証明書の実際の長さが反映されるよう更新する必要があります。

また、ハードウェアのネットワーク ドライバーも必要になります (nx_ip_create 呼び出しで "nx_driver_xx" パラメーターを置き換えます)。

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

/* Define the size of our application stack. */
#define     DEMO_STACK_SIZE             4096

/* Define the remote server IP address using NetX IP_ADDRESS macro. */
#define     REMOTE_SERVER_IP_ADDRESS    IP_ADDRESS(192, 168, 1, 1)

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS           IP_ADDRESS(192, 168, 1, 2)

/* Define the remote server port. 443 is the HTTPS default. */
#define     REMOTE_SERVER_PORT          443

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define an HTTP request to be sent to the HTTPS web server not defined here but
  represented by the ellipsis. */
UCHAR http_request[] = { "GET /example.html HTTP/1.1"  };

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];

/* Define the TLS Client thread.  */
ULONG             tls_client_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_client_thread;
void              client_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Client X.509 trusted root CA certificate, ASN.1 DER-
   encoded. A trusted certificate must be provided for TLS Client applications
   (unless X.509 authentication is disabled) or TLS will treat all certificates as
   untrusted and the handshake will fail.
*/

/* DER-encoded binary certificate, not defined here but represented by the ellipsis,
   for the sake of brevity. */
const UCHAR trusted_ca_data[] = { … };
const UINT trusted_ca_length = 0x574;

/* Define the application – initialize drivers and TCP/IP setup.
   NOTE: the variable “status” should be checked after every API call. Most error
         checking has been omitted for clarity. */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;

   /* Initialize the NetX system.  */
   nx_system_initialize();

   /* Create a packet pool. Check status for errors. */
   status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                   (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                   NX_PACKET_POOL_SIZE);

   /* Create an IP instance for the specific target. Check status for errors. This
      call is not completely defined. Please see other demo files for proper usage
      of the nx_ip_create call. */
   status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                         DEVICE_IP_ADDRESS ,
                         0xFFFFFF00UL,
                         &pool_0, nx_driver_xx,
                         (UCHAR*)ip_thread_stack,
                         sizeof(ip_thread_stack),
                         1);

   /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
       errors. */
   status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

   /* Enable TCP traffic. Check status for errors. */
   status =  nx_tcp_enable(&ip_0);

   status =  nx_ip_fragment_enable(&ip_0);

   /* Initialize the NetX Secure TLS system.  */
   nx_secure_tls_initialize();

    /* Create the TLS client thread to start handling incoming requests. */
   tx_thread_create(&tls_client_thread, "TLS Client thread", client_thread_entry, 0,
                     tls_client_thread_stack, sizeof(tls_client_thread_stack),
                     16, 16, 4, TX_AUTO_START);
   return;
}

/* Thread to handle the TLS Client instance. */
void client_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG       actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;
ULONG server_ipv4_address;

    /* We are not using the thread input parameter so suppress compiler warning. */
    NX_PARAMETER_NOT_USED(thread_input);

   /* Ensure the IP instance has been initialized.  */
   status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

   /* Create a TCP socket to use for our TLS session.  */
   status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Client Socket",
                                  NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                  NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

   /* Create a TLS session for our socket. This sets up the TLS session object for
          later use */
   status =  nx_secure_tls_session_create(&tls_session,
                                          &nx_crypto_tls_ciphers_ecc,
                                          tls_crypto_metadata,
                                          sizeof(tls_crypto_metadata));

   /* Initialize ECC parameters for this session. */
   status = nx_secure_tls_ecc_initialize(&tls_session,
                                             nx_crypto_ecc_supported_groups,
                                             nx_crypto_ecc_supported_groups_size,
                                             nx_crypto_ecc_curves);

   /* Set the packet reassembly buffer for this TLS session. */
   status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                    sizeof(tls_packet_buffer));

   /* Initialize an X.509 certificate with our CA root certificate data. */
   nx_secure_x509_certificate_initialize(&certificate, trusted_ca_data,
                                         trusted_ca_length, NX_NULL, 0, NX_NULL, 0,
                                         NX_SECURE_X509_KEY_TYPE_NONE);

   /* Add the initialized certificate as a trusted root certificate. */
   nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);

   /* Setup this thread to open a connection on the TCP socket to a remote server.
      The IP address can be used directly or it can be obtained via DNS or other
      means.*/
   server_ipv4_address = REMOTE_SERVER_IP_ADDRESS;
   status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
                                         REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

   /* Start the TLS Session using the connected TCP socket. This function will
      ascertain from the TCP socket state that this is a TLS Client session. */
   status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                         NX_WAIT_FOREVER);

    /* Allocate a TLS packet to send an HTTP request over TLS (HTTPS). */
    status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                          NX_WAIT_FOREVER);

    /* Populate the packet with our HTTP request. */
    nx_packet_data_append(send_packet, http_request, sizeof(http_request), &pool_0,
                          NX_WAIT_FOREVER);


   /* Send the HTTP request over the TLS Session, turning it into HTTPS. */
   status = nx_secure_tls_session_send(&tls_session, send_packet, NX_WAIT_FOREVER);

   /* If the send fails, you must release the packet.  */
   if (status != NX_SUCCESS)
   {
         /* Release the packet since the packet was not sent.  */
         nx_packet_release(send_packet);
   }

   /* Receive the HTTP response and any data from the server. */
   status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
   NX_WAIT_FOREVER);
   if (status == NX_SUCCESS)
   {
       /* Extract the data we received from the remote server. */
       status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                             100,  &bytes);
        /* Display the response data. */
       receive_buffer[bytes] = 0;
       printf("Received data: %s\n", receive_buffer);

        /* Release the packet when done with it. */
       nx_packet_release(receive_packet);
   }

   /* End the TLS session now that we have received our HTTPS/HTML response. */
   status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

   /* Check for errors to make sure the session ended cleanly. */

   /* Disconnect the TCP socket. */
   status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

}
```

**図 1.1 NetX を使用した NetX Secure の使用例**

## <a name="small-example-system-tls-web-server"></a>小さなシステム例 (TLS Web サーバー)

NetX Secure の使用がいかに簡単であるかの例を、下の図 1.1 で説明しています。これは、単純な TLS Web サーバー (HTTPS) を示しています。

この例を実行するためには、サーバーを TLS クライアントに識別させるための X.509 証明書が必要です。 ほとんどの Web ブラウザーでは、単純な自己署名証明書で十分です。 ブラウザーでサーバーを認証できないというメッセージが表示され、場合によってはサーバーと TLS/HTTPS 接続を確立できない場合があります<sup>3</sup>。 "certificate_data" 配列に DER エンコード バイナリ バージョンのサーバー証明書を入力し、"certificate_length" 変数を証明書の実際の長さが反映されるよう更新する必要があります。 また、"private_key" 配列に、RSA キーの場合は PKCS#1、ECC キーの場合は RFC 5915 を使用して書式設定された、DER エンコード バージョンの証明書の秘密キーを入力する必要があります。 "private_key_length" 変数にキー データの実際の長さを入力します。

> [!IMPORTANT]
> 一部のブラウザー (特に Chrome ブラウザーの一部のバージョン) が、自己署名証明書を拒否する場合があります。 この場合、サーバー証明書の署名に使用するルート CA 証明書を使用した 2 レベルの PKI を作成できます。 この場合、ルート CA 証明書は、信頼されたルート証明書としてブラウザーにインストールされます。 !!! 重要 - 終わったらルート CA 証明書をブラウザーから削除して、運用アプリケーションで使用しないようにしてください!!!

また、ハードウェアのネットワーク ドライバーも必要になります (nx_ip_create 呼び出しで "nx_driver_xx" パラメーターを置き換えます)。

```C
#include "tx_api.h"
#include "nx_api.h"
#include "nx_secure_tls_api.h"
#include "nx_secure_x509.h"

#define     DEMO_STACK_SIZE         4096

/* Define the IP address for this device. */
#define     DEVICE_IP_ADDRESS             IP_ADDRESS(192, 168, 1, 2)

/* Define the ThreadX and NetX object control blocks...  */

NX_PACKET_POOL          pool_0;
NX_IP                   ip_0;
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Define the IP thread's stack area.  */
ULONG ip_thread_stack[3 * 1024 / sizeof(ULONG)];

/* Define packet pool for the demonstration.  */
#define NX_PACKET_POOL_SIZE ((1536 + sizeof(NX_PACKET)) * 32)

ULONG packet_pool_area[NX_PACKET_POOL_SIZE/sizeof(ULONG) + 64 / sizeof(ULONG)];

/* Define the ARP cache area.  */
ULONG arp_space_area[512 / sizeof(ULONG)];


/* Define the TLS Server thread.  */
ULONG             tls_server_thread_stack[6 * 1024 / sizeof(ULONG)];
TX_THREAD         tls_server_thread;
void              server_thread_entry(ULONG thread_input);

/* Define the TLS packet reassembly buffer. */
UCHAR tls_packet_buffer[18000];

/* Define the metadata area for TLS cryptography. The actual size needed can be
   Ascertained by calling nx_secure_tls_metadata_size_calculate.
*/
UCHAR tls_crypto_metadata[18000];

/* Pointer to the TLS ciphersuite table that is included in the platform-specific
   cryptography subdirectory. The table maps the cryptographic routines for the
   platform to function pointers usable by the TLS library.
*/
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers_ecc;
extern const USHORT nx_crypto_ecc_supported_groups[];
extern const NX_CRYPTO_METHOD *nx_crypto_ecc_curves[];
extern const UINT nx_crypto_ecc_supported_groups_size;

/* Binary data for the TLS Server X.509 certificate, ASN.1 DER-encoded. Note that the
   certificate data and private key data is represented by an ellipsis for the sake
   of brevity.
*/
const UCHAR certificate_data[] = { … }; /* DER-encoded binary certificate. */
const UINT certificate_length = 0x574;

/* Binary data for the TLS Server Private Key, from private key
   file generated at the time of the X.509 certificate creation. ASN.1 DER-encoded. */
const UCHAR private_key[] = { … }; /* DER-encoded private key file (PKCS#1 RSA or ECC) */
const UINT private_key_length = 0x40;

/* Define some HTML data (web page) with an HTTPS header to serve to connecting
   clients. */
UCHAR html_data[] = { "HTTP/1.1 200 OK\r\n" \
        "Date: Tue, 19 May 2020 23:59:59 GMT\r\n" \
        "Content-Type: text/html\r\n" \
        "Content-Length: 200\r\n\r\n" \
        "<html>\r\n"\
        "<body>\r\n"\
        "<b>Hello NetX Secure User!</b>\r\n"\
        "This is a simple webpage\r\n"\
        "served up using NetX Secure!\r\n"\
        "</body>\r\n"\
        "</html>\r\n" };

/* Define the application – initialize drivers and TCP/IP setup.  */
void    tx_application_define(void *first_unused_memory)
{
UINT  status;


    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create a packet pool. Check status for errors. */
    status =  nx_packet_pool_create(&pool_0, "NetX Main Packet Pool", 1536,
                                    (ULONG*)(((int)packet_pool_area + 64) & ~63) ,
                                    NX_PACKET_POOL_SIZE);

    /* Create an IP instance for the specific target. Check status for errors. */
    status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                          DEVICE_IP_ADDRESS,
                          0xFFFFFF00UL,
                          &pool_0, nx_driver_xx,
                          (UCHAR*)ip_thread_stack,
                          sizeof(ip_thread_stack),
                          1);

    /* Enable ARP and supply ARP cache memory for IP Instance 0. Check status for
         errors. */
    status =  nx_arp_enable(&ip_0, (void *)arp_space_area, sizeof(arp_space_area));

    /* Enable TCP traffic. Check status for errors. */
    status =  nx_tcp_enable(&ip_0);

    status =  nx_ip_fragment_enable(&ip_0);

    /* Initialize the NetX Secure TLS system.  */
    nx_secure_tls_initialize();

    /* Create the TLS server thread to start handling incoming requests. */
    tx_thread_create(&tls_server_thread, "TLS Server thread", server_thread_entry, 0,
                   tls_server_thread_stack, sizeof(tls_server_thread_stack),
                   16, 16, 4, TX_AUTO_START);
    return;
}

/* Thread to handle the TLS Server instance. */
void server_thread_entry(ULONG thread_input)
{
UINT       status;
ULONG      actual_status;
NX_PACKET *send_packet;
NX_PACKET *receive_packet;
UCHAR receive_buffer[100];
ULONG bytes;

    NX_PARAMETER_NOT_USED(thread_input);

    /* Ensure the IP instance has been initialized.  */
    status =  nx_ip_status_check(&ip_0, NX_IP_INITIALIZE_DONE, &actual_status,
                                 NX_IP_PERIODIC_RATE);

    /* Create a TCP socket to use for our TLS session.  */
    status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket",
                                   NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                   NX_IP_TIME_TO_LIVE, 8192, NX_NULL, NX_NULL);

    /* Create a TLS session for our socket.  */
    status =  nx_secure_tls_session_create(&tls_session,
                                        &nx_crypto_tls_ciphers_ecc,
                                        tls_crypto_metadata,
                                        sizeof(tls_crypto_metadata));

    status = nx_secure_tls_ecc_initialize(&tls_session,
                                          nx_crypto_ecc_supported_groups,
                                          nx_crypto_ecc_supported_groups_size,
                                          nx_crypto_ecc_curves);

     /* Set the packet reassembly buffer for this TLS session. */
     status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                      sizeof(tls_packet_buffer));

    /* Initialize an X.509 certificate and private ECC key for our TLS Session. */
    nx_secure_x509_certificate_initialize(&certificate, certificate_data, NX_NULL, 0,
                                          certificate_length, private_key,
                                          private_key_length,
                                          NX_SECURE_X509_KEY_TYPE_EC_DER);

    /* Add the initialized certificate as a local identity certificate. */
    nx_secure_tls_local_certificate_add(&tls_session, &certificate);


    /* Setup this thread to listen on the TCP socket.
       Port 443 is standard for HTTPS. */
    status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

    while(1)
     {
         /* Accept a client TCP socket connection.  */
         status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

         /* Start the TLS Session using the connected TCP socket. */
         status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                              NX_WAIT_FOREVER);

         /* Receive the HTTPS request. */
         status = nx_secure_tls_session_receive(&tls_session, &receive_packet,
                                                NX_WAIT_FOREVER);

if (status == NX_SUCCESS)
      {
         /* Extract the HTTP request information from the HTTPS request. */
            status = nx_packet_data_extract_offset(receive_packet, 0, receive_buffer,
                                                  100, &bytes);
         /* Display the HTTP request data. */
            receive_buffer[bytes] = 0;
            printf("Received data: %s\n", receive_buffer);

         /* Release the packet when done with it */
            nx_packet_release(receive_packet);
      }

         /* Allocate a TLS packet to send HTML data back to client. */
         status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                                NX_WAIT_FOREVER);

         /* Populate the packet with our HTTP response and HTML web page data. */
         nx_packet_data_append(send_packet, html_data, sizeof(html_data), &pool_0,
                               NX_WAIT_FOREVER);

         /* Send the HTTP response over the TLS Session, turning it into HTTPS. */
         status = nx_secure_tls_session_send(&tls_session, send_packet,
                                                 NX_WAIT_FOREVER);

         /* If the send fails, you must release the packet.  */
         if (status != NX_SUCCESS)
         {
              /* Release the packet since it was not sent.  */
              nx_packet_release(send_packet);
         }

         /* End the TLS session now that we have sent our HTTPS/HTML response. */
         status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

         /* Check for errors to make sure the session ended cleanly! */

         /* Disconnect the TCP socket so we can be ready for the next request. */
         status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

         /* Unaccept the server socket.  */
         status =  nx_tcp_server_socket_unaccept(&tcp_socket);

         /* Setup server socket for listening again.  */
         status =  nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
     }
}
```

**図 1.2 NetX を使用した NetX Secure の使用例**

## <a name="a-note-on-tls-session-error-recovery"></a>TLS セッション エラー回復に関する注意事項

上記のシステム例は、TLS クライアントとサーバーそれぞれの基本的な概要を示していますが、わかりやすいように、エラー処理は省略しています。 ただし、TLS が提供するセキュリティの一部は、エラー状況の適切な処理に依存します。 一般に、最も深刻な潜在的問題は TLS スタック自体の中で処理されますが、重要なのは TLS アプリケーションが TLS 実装内で処理されない TLS エラーに対して適切に対応して復旧することです。

適切なエラー処理に必要なロジックを説明するために、次の関数は、TLS エラーを適切に処理して、エラー状態が発生した後の TLS 状態をクリーン リセットするために使用できる一般的な API サービスを示しています。 ここで説明したセクション以外に、このロジックは TLS クライアントと TLS サーバーの両インスタンスに適用されます。

関数の中で最も重要な API 呼び出しは、TLS セッションまたはハンドシェイクを完全に終了する *nx_secure_tls_session_end* サービスに対する呼び出しと、 TLS セッション状態をクリアして tls_session 制御構造インスタンスを新しい TLS セッションで再利用できるようにする *nx_secure_tls_session_reset* サービスに対する呼び出しです。 また、*nx_secure_tls_session_reset* では証明書や割り当てバッファーなどのユーザーが構成した状態がクリアされないため、*nx_secure_tls_session_create* を再度呼び出すことなくセッションを再利用できます。 すべての TLS セッション状態を完全クリアするには、*nx_secure_tls_session_delete* サービスを代わりに使用できます。

```C
/* Define a helper function to clean up a broken TLS session (to be called on any
   error from nx_secure_tls_session_start onwards). Note that the variables
   tls_session, tcp_socket, and ip_0 are global in the above examples. */
VOID tls_session_error_cleanup(VOID)
{
UINT status;
UINT alert_level, alert_value;

      /* If we got an error back from a TLS API call, there may be an alert from the
         remote host. Extract the alert level and value to print out. Note that the TLS
         API will return NX_SECURE_TLS_ALERT_RECEIVED (0x114) if an alert was received.
         For other error codes the alert value and level are not valid. */
      status = nx_secure_tls_session_alert_value_get(&tls_session, &alert_level,
                                                     &alert_value);
      if(status)
      {
         printf("Pointer error in getting alert value.\n");
      }
      else
      {
         printf("Alert recieved. Value: %d, Level: %d\n", alert_value, alert_level);
      }

      /* End the TLS session. This is required to properly shut down the TLS
         connection. */
      status = nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

      /* If the session did not shut down cleanly, this is a possible security issue. */
      if (status)
      {
         printf("Error in TLS session end: %x\n", status);
      }

      /* Reset the TLS session to re-use the control structure for the next connection.
         This API service resets the TLS session state but does not remove user-
         configured options such as certificates, PSKs, buffers, and cipher routines. */
      nx_secure_tls_session_reset(&tls_session);

      /* Disconnect the TCP socket, closing the connection. */
      status =  nx_tcp_socket_disconnect(&tcp_socket, NX_WAIT_FOREVER);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket close: %x\n", status);
      }

   /* The following code applies only to a TLS server instance. */
   #if NX_SECURE_TLS_SERVER
      /* Unaccept the server socket.  */
      status =  nx_tcp_server_socket_unaccept(&tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket unaccept: %x\n", status);
      }

      /* Setup server socket for listening again.  */
      status =  nx_tcp_server_socket_relisten(&ip_0, DEVICE_SERVER_PORT, &tcp_socket);

      /* Check for error.  */
      if (status)
      {
           printf("Error in TCP socket relisten: %x\n", status);
      }
#endif
} /* End function. */
```

## <a name="configuration-options"></a>構成オプション

NetX Secure を構築するためのいくつかの構成オプションがあります。 以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。

| 定義 | 意味 |
|----------------------|------------------------------------------------|
| **NX_SECURE_DISABLE_ERROR_CHECKING**                | このオプションを定義すると、基本的な NetX Secure エラー チェックが削除されます。 通常は、アプリケーションがデバッグされた後に使用します。 |
| **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**                  | このオプションを定義すると、予想される RSA 最大係数がビット単位で提供されます。 4096 ビット係数の既定値は 4096 です。 他に 3072、2048、または 1024 の値を指定できます (推奨されません)。 |
| **NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES**        | このオプションを定義すると、TLS がリモート ホストから自己署名証明書を受け取ることができます。 既定では、TLS はセキュリティ上の理由で自己署名サーバー証明書を拒否します。 このマクロが定義されている場合は、自己署名証明書を信頼ストアに追加して、受け入れられるようにする必要があります。 |
| **NX_SECURE_ENABLE_CLIENT_CERTIFICATE_VERIFY**      | このオプションを定義すると、オプションの X.509 クライアント証明書検証が TLS サーバーに対して有効になります<sup>4</sup>。  |
| **NX_SECURE_ENABLE_PSK_CIPHERSUITES**               | このオプションを定義すると、事前共有キー (PSK) 機能が有効になります。 デジタル証明書は無効になりません。 |
| **NX_SECURE_TLS_CLIENT_DISABLED**                   | このオプションを定義すると、TLS クライアント モードに関連するすべての TLS スタック コードが削除され、コードとデータの使用量が減ります。 |
| **NX_SECURE_TLS_SERVER_DISABLED**                   | このオプションを定義すると、TLS サーバー モードに関連するすべての TLS スタック コードが削除され、コードとデータの使用量が減ります。  |
| **NX_SECURE_DISABLE_ECC_CIPHERSUITE**               | このオプションを定義すると、楕円曲線暗号 (ECC) 暗号スイートのすべての TLS ロジックが削除されます。 これらの暗号スイートは TLS 1.2 以前では省略可能であり、無効にすると、コードとデータのサイズが大きく減る可能性があります。|
| **NX_SECURE_TLS_ENABLE_TLS_1_3**                    | このオプションを定義すると、TLSv1.3 モードが有効になります。 TLS 1.3 は最新バージョンの TLS であり、既定では無効になっています。 |
| **NX_SECURE_TLS_ENABLE_TLS_1_0**                    | このオプションを定義すると、従来の TLSv1.0 モードが有効になります。 TLSv1.0 は廃止と見なされているため、有効にするのは古いアプリケーションとの下位互換性のためだけにしてください。 |
| **NX_SECURE_TLS_ENABLE_TLS_1_1**                    | このオプションを定義すると、従来の TLSv1.1 モードが有効になります。 TLSv1.1 は廃止と見なされているため、有効にするのは古いアプリケーションとの下位互換性のためだけにしてください。 |
| **NX_SECURE_TLS_DISABLE_TLS_1_1**                   | このオプションを定義すると、TLSv1.1 モードが無効になります。 既定では定義されています。 TLSv 1.1 が無効になっているのは、より安全な TLSv1.2 だけを使用することを優先しているためです<sup>5</sup>。  |
| **NX_SECURE_X509_STRICT_NAME_COMPARE**              | このオプションを定義すると、証明書の検索と検証で X.509 証明書の厳密な識別名の比較が可能になります。 既定では、識別名の「共通名」フィールドの比較だけが行われます。|
| **NX_SECURE_X509_USE_EXTENDED_DISTINGUISHED_NAMES** | このオプションを定義するとオプションの「X.509 識別名」フィールドが有効になり、余分なメモリが X.509 証明書で消費されます。 |

4. このオプションで有効になるのは、コードがアプリケーションにリンクされることだけです。 この機能は API サービス nx_secure_tls_session_client_verify_enable で有効にするか、クライアント証明書検証を使用するために nx_secure_tls_session_x509_client_verify_configure を使用して構成する必要があります。

5. TLS 1.0 または TLS 1.1 のみを使用している場合は、TLSv1.2 も無効にすることが可能です。 ただし、これは推奨されておらず、直接サポートされているわけでありません。
