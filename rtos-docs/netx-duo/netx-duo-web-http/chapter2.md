---
title: 第 2 章 - HTTP と HTTPS のインストールと使用
description: この章では、NetX Web HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 99e649781588b56e72b509c2aa077c38423379d1
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810520"
---
# <a name="chapter-2---installation-and-use-of-http-and-https"></a><span data-ttu-id="02b3b-103">第 2 章 - HTTP と HTTPS のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="02b3b-103">Chapter 2 - Installation and use of HTTP and HTTPS</span></span>

<span data-ttu-id="02b3b-104">この章では、NetX Web HTTP コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-104">This chapter contains a description of various issues related to installation, setup, and usage of the NetX Web HTTP component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="02b3b-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="02b3b-105">Product Distribution</span></span>

<span data-ttu-id="02b3b-106">HTTP for NetX は、[https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-106">HTTP for NetX is available at [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo).</span></span> <span data-ttu-id="02b3b-107">このパッケージには、以下に示すように、3 つのソース ファイル、2 つのインクルード ファイル、およびこのドキュメントを含む 1 つのファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="02b3b-107">The package includes three source files, two include files, and a file that contains this document, as follows:</span></span>

- <span data-ttu-id="02b3b-108">**nx_web_http_common.h** NetX Web HTTP 用の共通ヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-108">**nx_web_http_common.h** Common header file for NetX Web HTTP</span></span>
- <span data-ttu-id="02b3b-109">**nx_web_http_client.h** NetX Web 用 HTTP Client のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-109">**nx_web_http_client.h** Header file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="02b3b-110">**nx_web_http_server.h** NetX Web 用 HTTP Server のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-110">**nx_web_http_server.h** Header file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="02b3b-111">**nx_web_http_client.c** NetX Web 用 HTTP Client の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-111">**nx_web_http_client.c** C Source file for HTTP Client for NetX Web</span></span>
- <span data-ttu-id="02b3b-112">**nx_web_http_server.c** NetX Web 用 HTTP Server の C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-112">**nx_web_http_server.c** C Source file for HTTP Server for NetX Web</span></span>
- <span data-ttu-id="02b3b-113">**nx_tcpserver.c** 複数の TCP ソケットの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-113">**nx_tcpserver.c** C Source file for multiple TCP sockets</span></span>
- <span data-ttu-id="02b3b-114">**nx_tcpserver.h** HTTPS Server のシンボルを定義するためのヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-114">**nx_tcpserver.h** Header file for defining HTTPS Server symbols</span></span>
- <span data-ttu-id="02b3b-115">**nx_md5.c** MD5 ダイジェスト アルゴリズム</span><span class="sxs-lookup"><span data-stu-id="02b3b-115">**nx_md5.c** MD5 digest algorithms</span></span>
- <span data-ttu-id="02b3b-116">**filex_stub.h** FileX が存在しない場合のスタブ ファイル</span><span class="sxs-lookup"><span data-stu-id="02b3b-116">**filex_stub.h** Stub file if FileX is not present</span></span>
- <span data-ttu-id="02b3b-117">**nx_web_http.pdf** HTTP for NetX Web の説明</span><span class="sxs-lookup"><span data-stu-id="02b3b-117">**nx_web_http.pdf** Description of HTTP for NetX Web</span></span>
- <span data-ttu-id="02b3b-118">**demo_netx_web_http.c** NetX Web HTTP のデモンストレーション</span><span class="sxs-lookup"><span data-stu-id="02b3b-118">**demo_netx_web_http.c** NetX Web HTTP demonstration</span></span>

## <a name="http-installation"></a><span data-ttu-id="02b3b-119">HTTP のインストール</span><span class="sxs-lookup"><span data-stu-id="02b3b-119">HTTP Installation</span></span>

<span data-ttu-id="02b3b-120">NetX Web HTTP を使用するためには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-120">In order to use NetX Web HTTP, the entire distribution mentioned previously should be copied to the same directory where NetX Duo is installed.</span></span> <span data-ttu-id="02b3b-121">たとえば、NetX Duo が " *\threadx\arm7\green*" ディレクトリにインストールされているとき、NetX Web HTTP Client アプリケーションの場合は *nx_web_http_client.h* と *nx_web_http_client.c、NetX Web HTTP Server アプリケーションの場合は nx_web_http_server.h*、*nx_web_http_server.c、nx_tcpserver.c、nx_tcpserver.h です。クライアントとサーバーの両方のアプリケーションで、このディレクトリに nx_web_http_common.h も必要です。ダイジェスト認証が使用されている場合は、nx_md5.c* もこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-121">For example, if NetX Duo is installed in the directory “*\threadx\arm7\green*” then the *nx_web_http_client.h* and *nx_web_http_client.c for NetX Web HTTP Client applications, and nx_web_http_server.h*, *nx_web_http_server.c, nx_tcpserver.c and nx_tcpserver.h for NetX Web HTTP Server applications. For both client and server applications, nx_web_http_common.h must be in this directory as well. nx_md5.c* should also be copied into this directory if digest authentication is being used.</span></span> <span data-ttu-id="02b3b-122">デモの "RAM ドライバー" アプリケーションの場合は、HTTP Client と Server のファイルを同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-122">For the demo ‘ram driver’ application HTTP Client and Server files should be copied into the same directory.</span></span>

<span data-ttu-id="02b3b-123">TLS を使用する場合は、TLS ソース ファイルを含む別の NetX Secure ディレクトリが必要です。</span><span class="sxs-lookup"><span data-stu-id="02b3b-123">If using TLS, you should have a separate NetX Secure directory containing the TLS source files.</span></span>

## <a name="using-http"></a><span data-ttu-id="02b3b-124">HTTP の使用</span><span class="sxs-lookup"><span data-stu-id="02b3b-124">Using HTTP</span></span>

<span data-ttu-id="02b3b-125">NetX Web HTTP は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-125">Using NetX Web HTTP is easy.</span></span> <span data-ttu-id="02b3b-126">基本的に、アプリケーション コードでは、*tx_api.h、fx_api.h* と *nx_api* をインクルードした後に、*nx_web_http_client.h* または *nx_web_http_server.h* (あるいはその両方) をインクルードする必要があります (*nx_web_http_common.h* は自動的にインクルードされます)。</span><span class="sxs-lookup"><span data-stu-id="02b3b-126">Basically, the application code must include *nx_web_http_client.h* and/or *nx_web_http_server.h* after it includes *tx_api.h, fx_api.h,* and *nx_api.h* (*nx_web_http_common.h* is automatically included).</span></span> <span data-ttu-id="02b3b-127">これらのヘッダーにより、アプリケーションで ThreadX、FileX、NetX Duo をそれぞれ使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-127">Those headers enable the application to use ThreadX, FileX, and NetX Duo, respectively.</span></span> <span data-ttu-id="02b3b-128">HTTPS をサポートする場合は、TLS サポートを取り込むために *nx_secure_tls.h* ファイルをインクルードした後に、これらのヘッダーをインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-128">For HTTPS support, the headers must be included after the *nx_secure_tls.h* file is included to bring in TLS support.</span></span>

<span data-ttu-id="02b3b-129">HTTP ヘッダー ファイルをインクルードすると、アプリケーション コードで、このガイドで後述する HTTP 関数呼び出しを行うことができるようになります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-129">Once the HTTP header files are included, the application code is then able to make the HTTP function calls specified later in this guide.</span></span> <span data-ttu-id="02b3b-130">また、アプリケーションでは、*HTTP(S) クライアントの場合は nx_web_http_client.c*、*HTTP(S) サーバーの場合は nx_web_http_server.c と nx_tcpserver.c*、ビルド処理では *nx_md5.c (ダイジェスト認証用)* をリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-130">The application must also link with *nx_web_http_client.c for HTTP(S) clients*, *nx_web_http_server.c and nx_tcpserver.c for HTTP(S) servers*, and *nx_md5.c (for digest authentication)* in the build process.</span></span> <span data-ttu-id="02b3b-131">これらのファイルは他のアプリケーション ファイルと同じ方法でコンパイルする必要があり、そのオブジェクト フォームをアプリケーションのファイルと一緒にリンクする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-131">These files must be compiled in the same manner as other application files and its object form must be linked along with the files of the application.</span></span> <span data-ttu-id="02b3b-132">NetX Web HTTP を使用するために必要なものはこれだけです。</span><span class="sxs-lookup"><span data-stu-id="02b3b-132">This is all that is required to use NetX Web HTTP.</span></span>

> [!NOTE]
> <span data-ttu-id="02b3b-133">ビルド処理に NX_WEB_HTTP_DIGEST_ENABLE が指定されていない場合は、アプリケーションに *md5.c* ファイルを追加する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-133">If NX_WEB_HTTP_DIGEST_ENABLE is not specified in the build process, the *md5.c* file does not need to be added to the application.</span></span> <span data-ttu-id="02b3b-134">同様に、HTTP Client 機能が不要な場合は、*nx_web_http_client.c* ファイルを省略できます。HTTP Server 機能が不要な場合は、*nx_web_http_server.c* を省略できます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-134">Similarly, if no HTTP Client capabilities are required, the *nx_web_http_client.c* file may be omitted and if no HTTP Server capabilities are required, *nx_web_http_server.c* may be omitted.</span></span>
>
> <span data-ttu-id="02b3b-135">(プレーンテキストの HTTP のみを使用するのではなく) HTTPS を有効にするための NX_WEB_HTTPS_ENABLE が定義されていない場合は、NetX Secure TLS がビルド内にある必要はありません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-135">Unless NX_WEB_HTTPS_ENABLE is defined in order to enable HTTPS (instead of using only plaintext HTTP) then NetX Secure TLS does not need to be in the build.</span></span>
>
> <span data-ttu-id="02b3b-136">HTTP では NetX TCP サービスが利用されるため、HTTP を使用する前に、*nx_tcp_enable()* を呼び出して TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-136">Since HTTP utilizes NetX TCP services, TCP must be enabled with the *nx_tcp_enable()* call prior to using HTTP.</span></span>
>
> <span data-ttu-id="02b3b-137">NetX Secure TLS で HTTPS を使用する場合は、HTTPS ルーチンを呼び出す前に、*nx_secure_tls_initialize()* を使用して TLS を初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-137">When using HTTPS with NetX Secure TLS, TLS must be initialized with *nx_secure_tls_initialize()* prior to calling HTTPS routines.</span></span>

## <a name="small-example-system"></a><span data-ttu-id="02b3b-138">小規模システムの例</span><span class="sxs-lookup"><span data-stu-id="02b3b-138">Small Example System</span></span>

<span data-ttu-id="02b3b-139">NetX Web HTTP の使用方法の例を以下の図 1.1 に示します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-139">An example of how to use NetX Web HTTP is described in Figure 1.1 below.</span></span>

> [!CAUTION]
> <span data-ttu-id="02b3b-140">これはデモンストレーションのみを目的として提供されており、そのままコンパイルして実行することは保証されていません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-140">This is provided for demonstration purposes only and is not guaranteed to compile and run as is.</span></span>
>
> <span data-ttu-id="02b3b-141">ネイティブな Express Logic 環境で適切にビルドされるデモ ソース コード ファイルについては、NetX Duo HTTPS リリース コードのディストリビューションを参照してください。</span><span class="sxs-lookup"><span data-stu-id="02b3b-141">Please refer to the NetX Duo HTTPS release code distribution for  demo source code file(s) that will properly build in the native Express Logic environment.</span></span>  <span data-ttu-id="02b3b-142">また、これらのデモは、HTTPS や NetX Duo HTTPS アプリケーションを新しいユーザーに紹介することが目的であるため、意図的に非常に単純化されていることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="02b3b-142">Also be aware that these demos are intentionally kept very simple as they are intended to introduce HTTPS and/or NetX Duo HTTPS application to new users.</span></span>

<span data-ttu-id="02b3b-143">この例では、HTTP インクルード ファイル *nx_web_http_client.h および nx_web_http_server.h* が取り込まれます (*netx_web_http_common.h* は自動的にインクルードされます)。</span><span class="sxs-lookup"><span data-stu-id="02b3b-143">In this example, the HTTP include file *nx_web_http_client.h and nx_web_http_server.h are* brought in (*netx_web_http_common.h* is included automatically).</span></span> <span data-ttu-id="02b3b-144">次に、HTTP Server が "*tx_application_define*" に作成されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-144">Next, the HTTP Server is created in “*tx_application_define*”.</span></span> <span data-ttu-id="02b3b-145">HTTP Server の制御ブロック "*Server*" は、以前はグローバル変数として定義されていたことに注意してください。</span><span class="sxs-lookup"><span data-stu-id="02b3b-145">Note that the HTTP Server control block “*Server*” was defined as a global variable previously.</span></span> <span data-ttu-id="02b3b-146">正常に作成されると、HTTPS Server が開始されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-146">After successful creation, the HTTPS Server is started.</span></span> <span data-ttu-id="02b3b-147">その後、HTTPS Client が作成されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-147">The HTTPS Client is then created.</span></span> <span data-ttu-id="02b3b-148">ファイルに書き込み、そのファイルを読み取ります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-148">It writes the file and reads the file back.</span></span>

> [!NOTE]
> <span data-ttu-id="02b3b-149">このシステムには NX_WEB_HTTPS_ENABLE が定義されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-149">NX_WEB_HTTPS_ENABLE is defined on this system.</span></span>

```c
/* This is a small demo of HTTPS on the high-performance NetX Duo TCP/IP stack.
   This demo relies on ThreadX, NetX Duo, and FileX to show an HTML
   transfer from the client and then back from the server.  */

#include  "tx_api.h"
#include  "fx_api.h"
#include  "nx_api.h"
#include  “nx_crypto.h”
#include  “nx_secure_tls_api.h”
#include  “nx_secure_x509.h”
#include  "nx_web_http_client.h"
#include  "nx_web_http_server.h"
#define    DEMO_STACK_SIZE         4096


/* Define the ThreadX and NetX object control blocks...  */

TX_THREAD               thread_0;
TX_THREAD               thread_1;
NX_PACKET_POOL          pool_0;
NX_PACKET_POOL          pool_1;
NX_IP                   ip_0;
NX_IP                   ip_1;
FX_MEDIA                ram_disk;

/* Define HTTP objects.  */

NX_WEB_HTTP_SERVER      my_server;
NX_WEB_HTTP_CLIENT      my_client;

/* Define the counters used in the demo application...  */

ULONG                   error_counter;


/* Define the RAM disk memory.  */

UCHAR                   ram_disk_memory[32000];

/* Include cryptographic routines for TLS. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Define TLS data for HTTPS. */
CHAR crypto_metadata[8928 * NX_WEB_HTTP_SESSION_MAX];
UCHAR tls_packet_buffer[16500];

/* NX_WEB_HTTP_SERVER_SESSION_MAX defaults to 2 in nx_web_http_server.h */
UCHAR server_tls_packet_buffer[16500 * NX_WEB_HTTP_SERVER_SESSION_MAX];

/* Define certificate containers. The server certificate is used to identify the NetX
   Web HTTPS server and the trusted certificate is used by the client to verify the
   server’s identity certificate.  */
NX_SECURE_X509_CERT server_certificate;
NX_SECURE_X509_CERT trusted_certificate;

/* Remote certificates need both an NX_SECURE_X509_CERT container and an associated
   buffer. The number of certificates depends on the remote host, but usually at least
   two certificates will be sent – the identity certificate for the host and the
   certificate that issued the identity certificate. */
NX_SECURE_X509_CERT remote_certificate, remote_issuer;

UCHAR remote_cert_buffer[2000];
UCHAR remote_issuer_buffer[2000];

/* Certificate information for server and client (see NetX Secure TLS reference on X.509
    certificates for more information). Arrays are populated with binary versions Of
    certificates and keys and the corresponding “len” variables are assigned the lengths
    of that data. Trusted certificates do not need a private key. */
const UCHAR server_cert_der[] = { … };
const UINT  server_cert_derlen = … ;
const UCHAR server_cert_key_der[] = { … };
const UINT  server_cert_key_derlen = … ;

const UCHAR trusted_cert_der[] = { … };
const UINT  trusted_cert_derlen = … ;


/* Define function prototypes.  */

void    thread_0_entry(ULONG thread_input);
VOID    _fx_ram_driver(FX_MEDIA *media_ptr) ;
void    _nx_ram_network_driver(struct NX_IP_DRIVER_STRUCT *driver_req);
UINT    authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
             CHAR *resource, CHAR **name, CHAR **password, CHAR **realm);
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
   NX_SECURE_TLS_SESSION *tls_session);

/* Define the application's authentication check.  This is called by
   the HTTP server whenever a new request is received.  */
UINT  authentication_check(NX_WEB_HTTP_SERVER *server_ptr, UINT request_type,
            CHAR *resource, CHAR **name, CHAR **password, CHAR **realm)
{
    /* Just use a simple name, password, and realm for all
       requests and resources.  */
    *name =     "name";
    *password = "password";
    *realm =    "NetX Web HTTP demo";

    /* Request basic authentication.  */
    return(NX_WEB_HTTP_BASIC_AUTHENTICATE);
}

/* Define the TLS setup callback for HTTPS Client. This function is invoked when the
   HTTPS client is started – all TLS per-session initialization should go in here. */
UINT tls_setup_callback(NX_WEB_HTTP_CLIENT *client_ptr,
  NX_SECURE_TLS_SESSION *tls_session)
{
    UINT status;

    /* Initialize and create TLS session. */
    nx_secure_tls_session_create(tls_session, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata));

    /* Allocate space for packet reassembly. */
    nx_secure_tls_session_packet_buffer_set(tls_session, tls_packet_buffer,
        sizeof(tls_packet_buffer));


    /* Add a CA Certificate to our trusted store for verifying incoming server
        certificates. */
    nx_secure_x509_certificate_initialize(&trusted_certificate, trusted_cert_der,
        trusted_cert_der_len, NX_NULL, 0, NULL, 0,
        NX_SECURE_X509_KEY_TYPE_NONE);
    nx_secure_tls_trusted_certificate_add(tls_session, &trusted_certificate);

    /* Need to allocate space for the certificate coming in from the remote host. */
    nx_secure_tls_remote_certificate_allocate(tls_session, &remote_certificate,
        remote_cert_buffer, sizeof(remote_cert_buffer));
    nx_secure_tls_remote_certificate_allocate(tls_session,
        &remote_issuer, remote_issuer_buffer,
        sizeof(remote_issuer_buffer));

    return(NX_SUCCESS);
 }

/* Define main entry point.  */

 int main()
 {
     /* Enter the ThreadX kernel.  */
     tx_kernel_enter();
 }

/* Define what the initial system looks like.  */
void    tx_application_define(void *first_unused_memory)
{

    CHAR    *pointer;

    /* Setup the working pointer.  */
    pointer =  (CHAR *) first_unused_memory;

    /* Create the main thread.  */
    tx_thread_create(&thread_0, "thread 0", thread_0_entry, 0,
        pointer, DEMO_STACK_SIZE,
        2, 2, TX_NO_TIME_SLICE, TX_AUTO_START);
    pointer = pointer + DEMO_STACK_SIZE;

    /* Initialize the NetX system.  */
    nx_system_initialize();

    /* Create packet pool.  */
    nx_packet_pool_create(&pool_0, "NetX Packet Pool 0",
        600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create an IP instance.  */
    nx_ip_create(&ip_0, "NetX IP Instance 0", IP_ADDRESS(1, 2, 3, 4),
        0xFFFFFF00UL, &pool_0, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer =  pointer + 4096;

    /* Create another packet pool. */
    nx_packet_pool_create(&pool_1, "NetX Packet Pool 1", 600, pointer, 8192);
    pointer = pointer + 8192;

    /* Create another IP instance.  */
    nx_ip_create(&ip_1, "NetX IP Instance 1", IP_ADDRESS(1, 2, 3, 5),
        0xFFFFFF00UL, &pool_1, _nx_ram_network_driver,
        pointer, 4096, 1);
    pointer = pointer + 4096;

    /* Enable ARP and supply ARP cache memory for IP Instance 0.  */
    nx_arp_enable(&ip_0, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable ARP and supply ARP cache memory for IP Instance 1.  */
    nx_arp_enable(&ip_1, (void *) pointer, 1024);
    pointer = pointer + 1024;

    /* Enable TCP processing for both IP instances.  */
    nx_tcp_enable(&ip_0);
    nx_tcp_enable(&ip_1);

    /* Open the RAM disk.  */
    fx_media_open(&ram_disk, "RAM DISK",
        _fx_ram_driver, ram_disk_memory, pointer, 4096);
    pointer += 4096;

    /* Create the NetX Web HTTP Server.  */
    nx_web_http_server_create(&my_server, "My HTTP Server", &ip_1,
        NX_WEB_HTTPS_SERVER_PORT, &ram_disk,
        pointer, 4096, &pool_1, authentication_check, NX_NULL);
    pointer = pointer + 4096;

    /* The TLS server needs an identity certificate which is imported as a binary DER-
        encoded X.509 certificate and its associated private key (e.g. DER-encoded PKCS#1
        RSA private key). */
    nx_secure_x509_certificate_initialize(&server_certificate, server_cert_der,
        server_cert_der_len, NX_NULL, 0,
        server_cert_key_der, server_cert_key_der_len,
        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Setup TLS session data for the TCP server.
        This enables TLS and HTTPS for the server.  */
    nx_web_http_server_secure_configure(&my_server, &nx_crypto_tls_ciphers,
        crypto_metadata, sizeof(crypto_metadata), server_tls_packet_buffer,
        sizeof(server_tls_packet_buffer), &server_certificate, NX_NULL, 0,
        NX_NULL, 0, NX_NULL, 0);

    /* Start the HTTP Server.  */
    nx_web_http_server_start(&my_server);
}

/* Define the test thread.  */
void    thread_0_entry(ULONG thread_input)
{
    NX_PACKET   *my_packet;
    UINT        status;

    /* Create an HTTP client instance.  */
    status = nx_web_http_client_create(&my_client, "My Client", &ip_0, &pool_0, 600);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Prepare to send the simple 103-byte HTML file to the Server over HTTPS.  */
    status = nx_web_http_client_put_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm", "name", "password", 103, tls_setup_callback, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Allocate a packet.  */
     tatus = nx_web_http_client_request_packet_allocate(&pool_0, &my_packet,
        NX_TCP_PACKET, NX_WAIT_FOREVER);

    /* Check status.  */
    if (status != NX_SUCCESS)
        return;

    /* Build a simple 103-byte HTML page.  */
    nx_packet_data_append(my_packet, "<HTML>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet,
        "<HEAD><TITLE>NetX HTTP Test</TITLE></HEAD>\r\n", 44,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<BODY>\r\n", 8,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "<H1>NetX Test Page</H1>\r\n", 25,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</BODY>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);
    nx_packet_data_append(my_packet, "</HTML>\r\n", 9,
        &pool_0, NX_WAIT_FOREVER);

    /* Complete the PUT by writing the total length.  */
    status =  nx_web_http_client_put_packet(&my_client, my_packet, 50);

    /* Check status.  */
    if (status)
        error_counter++;

    /* Now GET the file back!  */
    status =  nx_web_http_client_get_secure_start(&my_client, IP_ADDRESS(1,2,3,5),
        NX_WEB_HTTPS_SERVER_PORT, "/test.htm",
        "name", "password", tls_setup_callback, 50);
 
    /* Check status.  */
    if (status)
        error_counter++;

    /* Get a packet.  */
    status =  nx_web_http_client_response_body_get(&my_client, &my_packet, 20);

    /* Check for an error.  */
    if ((status) || (my_packet -> nx_packet_length != 103))
        error_counter++;

    /* Check to see if we have a packet.  */
    if (status == NX_SUCCESS)
    {

        /* Yes, release it!  */
        nx_packet_release(my_packet);
    }

    /* Make sure TLS shuts down properly. */
    nx_web_http_client_delete(&my_client);

    /* Flush the media.  */
    fx_media_flush(&ram_disk);
}
```

<span data-ttu-id="02b3b-150">**図 1.1 NetX および NetX Secure TLS と共に HTTPS を使用する例**</span><span class="sxs-lookup"><span data-stu-id="02b3b-150">**Figure 1.1 Example of HTTPS use with NetX and NetX Secure TLS**</span></span>

## <a name="configuration-options"></a><span data-ttu-id="02b3b-151">構成オプション</span><span class="sxs-lookup"><span data-stu-id="02b3b-151">Configuration Options</span></span>

<span data-ttu-id="02b3b-152">HTTP for NetX を構築するための構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-152">There are several configuration options for building HTTP for NetX.</span></span> <span data-ttu-id="02b3b-153">すべてのオプションの一覧を以下に示します。それぞれのオプションが詳細に説明されています。</span><span class="sxs-lookup"><span data-stu-id="02b3b-153">Following is a list of all options, where each is described in detail.</span></span> <span data-ttu-id="02b3b-154">既定値は示されていますが、*nx_web_http_client.h と nx_web_http_server.h* をインクルードする前に再定義することができます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-154">The default values are listed but can be redefined prior to inclusion of *nx_web_http_client.h and nx_web_http_server.h*:</span></span>

- <span data-ttu-id="02b3b-155">**NX_DISABLE_ERROR_CHECKING** このオプションを定義すると、基本的な HTTP エラー チェックが削除されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-155">**NX_DISABLE_ERROR_CHECKING** Defined, this option removes the basic HTTP error checking.</span></span> <span data-ttu-id="02b3b-156">通常は、アプリケーションがデバッグされた後に使用します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-156">It is typically used after the application has been debugged.</span></span>
- <span data-ttu-id="02b3b-157">**NX_WEB_HTTP_DIGEST_ENABLE** 定義した場合、MD5 ダイジェストを使用した認証が HTTPS Server で有効になります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-157">**NX_WEB_HTTP_DIGEST_ENABLE** If defined, authentication using the MD5 digest is enabled on the HTTPS Server.</span></span> <span data-ttu-id="02b3b-158">これは、既定では定義されていません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-158">By default it is not defined.</span></span>
- <span data-ttu-id="02b3b-159">**NX_WEB_HTTP_SERVER_PRIORITY** HTTPS Server のスレッドの優先順位。</span><span class="sxs-lookup"><span data-stu-id="02b3b-159">**NX_WEB_HTTP_SERVER_PRIORITY** The priority of the HTTPS Server thread.</span></span> <span data-ttu-id="02b3b-160">既定では、この値は 16 番目の優先順位を示す 16 に定義されています。</span><span class="sxs-lookup"><span data-stu-id="02b3b-160">By default, this value is defined as 16 to specify priority 16.</span></span>
- <span data-ttu-id="02b3b-161">**NX_WEB_HTTP_NO_FILEX** このオプションを定義すると、FileX の依存関係のスタブが提供されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-161">**NX_WEB_HTTP_NO_FILEX** Defined, this option provides a stub for FileX dependencies.</span></span> <span data-ttu-id="02b3b-162">このオプションを定義しても、HTTPS Client は変更なしで機能します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-162">The HTTPS Client will function without any change if this option is defined.</span></span> <span data-ttu-id="02b3b-163">HTTPS Server は、適切に機能させるためには、変更するか、ユーザーがいくつかの FileX サービスを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-163">The HTTPS Server will need to either be modified or the user will have to create a handful of FileX services in order to function properly.</span></span>
- <span data-ttu-id="02b3b-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** HTTPS TCP 要求に必要なサービスの種類。</span><span class="sxs-lookup"><span data-stu-id="02b3b-164">**NX_WEB_HTTP_TYPE_OF_SERVICE** Type of service required for the HTTPS TCP requests.</span></span> <span data-ttu-id="02b3b-165">既定では、この値は通常の IP パケット サービスを示す NX_IP_NORMAL に定義されています。</span><span class="sxs-lookup"><span data-stu-id="02b3b-165">By default, this value is defined as NX_IP_NORMAL to indicate normal IP packet service.</span></span>
- <span data-ttu-id="02b3b-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** 同じ優先順位のスレッドに生成される前に、サーバー スレッドが許可されるタイマー刻みの数。</span><span class="sxs-lookup"><span data-stu-id="02b3b-166">**NX_WEB_HTTP_SERVER_THREAD_TIME_SLICE** The number of timer ticks the Server thread is allowed to run before yielding to threads of the same priority.</span></span> <span data-ttu-id="02b3b-167">既定値は 2 です。</span><span class="sxs-lookup"><span data-stu-id="02b3b-167">The default value is 2.</span></span> <span data-ttu-id="02b3b-168">このオプションは非推奨です。</span><span class="sxs-lookup"><span data-stu-id="02b3b-168">Note this option is deprecated.</span></span>
- <span data-ttu-id="02b3b-169">**NX_WEB_HTTP_FRAGMENT_OPTION** HTTP TCP 要求のフラグメントを有効にします。</span><span class="sxs-lookup"><span data-stu-id="02b3b-169">**NX_WEB_HTTP_FRAGMENT_OPTION** Fragment enable for HTTP TCP requests.</span></span> <span data-ttu-id="02b3b-170">既定では、この値は NX_DONT_FRAGMENT で、HTTP TCP のフラグメント化が無効になります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-170">By default, this value is NX_DONT_FRAGMENT to disable HTTP TCP fragmenting.</span></span>
- <span data-ttu-id="02b3b-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** サーバー ソケットのウィンドウのサイズ。</span><span class="sxs-lookup"><span data-stu-id="02b3b-171">**NX_WEB_HTTP_SERVER_WINDOW_SIZE** Server socket window size.</span></span> <span data-ttu-id="02b3b-172">既定では、この値は 2048 バイトです。</span><span class="sxs-lookup"><span data-stu-id="02b3b-172">By default, this value is 2048 bytes.</span></span>
- <span data-ttu-id="02b3b-173">**NX_WEB_HTTP_TIME_TO_LIVE** このパケットが破棄されるまでに通過できるルーターの数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-173">**NX_WEB_HTTP_TIME_TO_LIVE** Specifies the number of routers this packet can pass before it is discarded.</span></span> <span data-ttu-id="02b3b-174">既定値は 0x80 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-174">The default value is set to 0x80.</span></span>
- <span data-ttu-id="02b3b-175">**NX_WEB_HTTP_SERVER_TIMEOUT** 内部サービスが中断される ThreadX のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-175">**NX_WEB_HTTP_SERVER_TIMEOUT** Specifies the number of ThreadX ticks that internal services will suspend for.</span></span> <span data-ttu-id="02b3b-176">既定値は 10 秒 (10 \* *NX_IP_PERIODIC_RATE*) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-176">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="02b3b-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** 内部 *nx_tcp_server_socket_accept()* 呼び出しで内部サービスが中断される ThreadX のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-177">**NX_WEB_HTTP_SERVER_TIMEOUT_ACCEPT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_server_socket_accept()* calls.</span></span> <span data-ttu-id="02b3b-178">既定値は (10 \* *NX_IP_PERIODIC_RATE*) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-178">The default value is set to (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="02b3b-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** 内部 *nx_tcp_socket_disconnect()* 呼び出しで内部サービスが中断される ThreadX のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-179">**NX_WEB_HTTP_SERVER_TIMEOUT_DISCONNECT** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_disconnect()* calls.</span></span> <span data-ttu-id="02b3b-180">既定値は 10 秒 (10 \* *NX_IP_PERIODIC_RATE*) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-180">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="02b3b-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** 内部 *nx_tcp_socket_receive()* 呼び出しで内部サービスが中断される ThreadX のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-181">**NX_WEB_HTTP_SERVER_TIMEOUT_RECEIVE** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_receive()* calls.</span></span> <span data-ttu-id="02b3b-182">既定値は 10 秒 (10 \* *NX_IP_PERIODIC_RATE*) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-182">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="02b3b-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** 内部 *nx_tcp_socket_send()* 呼び出しで内部サービスが中断される ThreadX のティック数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-183">**NX_WEB_HTTP_SERVER_TIMEOUT_SEND** Specifies the number of ThreadX ticks that internal services will suspend for in internal *nx_tcp_socket_send()* calls.</span></span> <span data-ttu-id="02b3b-184">既定値は 10 秒 (10 \* *NX_IP_PERIODIC_RATE*) に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-184">The default value is set to 10 seconds (10 \* *NX_IP_PERIODIC_RATE*).</span></span>
- <span data-ttu-id="02b3b-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **HTTP ヘッダー フィールドの最大サイズを指定します。既定値は 256 です。**</span><span class="sxs-lookup"><span data-stu-id="02b3b-185">**NX_WEB_HTTP_MAX_HEADER_FIELD** **Specifies the maximum size of the HTTP header field. The default value is 256.**</span></span>
- <span data-ttu-id="02b3b-186">**NX_WEB_HTTP_MULTIPART_ENABLE** \*\* 定義した場合、HTTPS Server でマルチパート HTTP 要求をサポートできるようになります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-186">\*\*NX_WEB_HTTP_MULTIPART_ENABLE \*\* \*\*If defined, enables HTTPS Server to support multipart HTTP requests.</span></span> **
- <span data-ttu-id="02b3b-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** HTTPS Server のキューに登録できる接続の数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-187">**NX_WEB_HTTP_SERVER_MAX_PENDING** Specifies the number of connections that can be queued for the HTTPS Server.</span></span> <span data-ttu-id="02b3b-188">既定値では、サーバー セッションの最大数の 2 倍に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-188">The default value is set to twice the maximum number of server sessions.</span></span>
- <span data-ttu-id="02b3b-189">**NX_WEB_HTTP_MAX_RESOURCE** クライアントで指定される "*リソース名*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-189">**NX_WEB_HTTP_MAX_RESOURCE** Specifies the number of bytes allowed in a client supplied *resource name*.</span></span> <span data-ttu-id="02b3b-190">既定値では 40 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-190">The default value is set to 40.</span></span>
- <span data-ttu-id="02b3b-191">**NX_WEB_HTTP_MAX_NAME** クライアントで指定される "*ユーザー名*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-191">**NX_WEB_HTTP_MAX_NAME** Specifies the number of bytes allowed in a client supplied *username*.</span></span> <span data-ttu-id="02b3b-192">既定値では 20 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-192">The default value is set to 20.</span></span>
- <span data-ttu-id="02b3b-193">**NX_WEB_HTTP_MAX_PASSWORD** クライアントで指定される "*パスワード*" に許容されるバイト数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-193">**NX_WEB_HTTP_MAX_PASSWORD** Specifies the number of bytes allowed in a client supplied *password*.</span></span> <span data-ttu-id="02b3b-194">既定値では 20 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-194">The default value is set to 20.</span></span>
- <span data-ttu-id="02b3b-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** HTTP または HTTPS Server の同時セッション数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-195">**NX_WEB_HTTP_SERVER_SESSION_MAX** Specifies the number of simultaneous sessions for an HTTP or HTTPS Server.</span></span> <span data-ttu-id="02b3b-196">TCP ソケットと TLS セッション (HTTPS が有効になっている場合) は、各セッションに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-196">A TCP socket and a TLS session (if HTTPS is enabled) are allocated for each session.</span></span> <span data-ttu-id="02b3b-197">既定値では 2 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-197">The default value is set to 2.</span></span>
- <span data-ttu-id="02b3b-198">**NX_WEB_HTTPS_ENABLE** 定義した場合、このマクロによって TLS と HTTPS が有効になります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-198">**NX_WEB_HTTPS_ENABLE** If defined, this macro enables TLS and HTTPS.</span></span> <span data-ttu-id="02b3b-199">プレーンテキスト HTTP のみが望ましい場合は、未定義のままにしてリソースを解放します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-199">Leave undefined to free up resources if only plaintext HTTP is desired.</span></span> <span data-ttu-id="02b3b-200">既定では、このマクロは定義されません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-200">By default, this macro is not defined.</span></span>
- <span data-ttu-id="02b3b-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** 定義した場合、このマクロによって HTTP キープアライブ機能が無効になります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-201">**NX_WEB_HTTPS_KEEPALIVE_DISABLE** If defined, this macro disables HTTP keep-alive feature.</span></span> <span data-ttu-id="02b3b-202">既定では、このマクロは定義されません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-202">By default, this macro is not defined.</span></span>
- <span data-ttu-id="02b3b-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** サーバーの作成時に指定されたプール内のパケットの最小サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-203">**NX_WEB_HTTP_SERVER_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at server creation.</span></span> <span data-ttu-id="02b3b-204">最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="02b3b-204">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="02b3b-205">既定値では 600 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-205">The default value is set to 600.</span></span>
- <span data-ttu-id="02b3b-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** クライアントの作成時に指定されたプール内のパケットの最小サイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-206">**NX_WEB_HTTP_CLIENT_MIN_PACKET_SIZE** Specifies the minimum size of the packets in the pool specified at Client creation.</span></span> <span data-ttu-id="02b3b-207">最小サイズは、完全な HTTP ヘッダーを 1 つのパケットに含めることができるようにするために必要です。</span><span class="sxs-lookup"><span data-stu-id="02b3b-207">The minimum size is needed to ensure the complete HTTP header can be contained in one packet.</span></span> <span data-ttu-id="02b3b-208">既定値では 600 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-208">The default value is set to 600.</span></span>
- <span data-ttu-id="02b3b-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** サーバー ソケットの再転送タイムアウトを秒単位で設定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-209">**NX_WEB_HTTP_SERVER_RETRY_SECONDS** Set the Server socket retransmission timeout in seconds.</span></span> <span data-ttu-id="02b3b-210">既定値では 2 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-210">The default value is set to 2.</span></span>
- <span data-ttu-id="02b3b-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** サーバー ソケットの再転送の最大数を設定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-211">**NX_WEB_HTTP_ SERVER_RETRY_MAX** This sets the maximum number of retransmissions on Server socket.</span></span> <span data-ttu-id="02b3b-212">既定値では 10 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-212">The default value is set to 10.</span></span>
- <span data-ttu-id="02b3b-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** この値は、次の再送信タイムアウトを設定するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-213">**NX_WEB_HTTP_ SERVER_RETRY_SHIFT** This value is used to set the next retransmission timeout.</span></span> <span data-ttu-id="02b3b-214">現在のタイムアウトには、これまでの再転送回数が乗算され、ソケット タイムアウト シフトの値によってシフトされます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-214">The current timeout is multiplied by the number of retransmissions thus far, shifted by the value of the socket timeout shift.</span></span> <span data-ttu-id="02b3b-215">既定値では 1 に設定され、タイムアウトが 2 倍になります。</span><span class="sxs-lookup"><span data-stu-id="02b3b-215">The default value is set to 1 for doubling the timeout.</span></span>
- <span data-ttu-id="02b3b-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** これは、サーバー ソケット再転送キューに登録できるパケットの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="02b3b-216">**NX_WEB_HTTP_SERVER_RETRY_TRANSMIT_QUEUE_DEPTH** This specifies the maximum number of packets that can be enqueued on the Server socket retransmission queue.</span></span> <span data-ttu-id="02b3b-217">エンキューされたパケットの数がこの数に達した場合、1 つまたは複数のエンキューされたパケットが解放されるまで、これ以上パケットを送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="02b3b-217">If the number of packets enqueued reaches this number, no more packets can be sent until one or more enqueued packets are released.</span></span> <span data-ttu-id="02b3b-218">既定値では 20 に設定されます。</span><span class="sxs-lookup"><span data-stu-id="02b3b-218">The default value is set to 20.</span></span>
