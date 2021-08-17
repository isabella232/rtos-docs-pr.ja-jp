---
title: 第 4 章 - Azure RTOS NetX Secure DTLS サービスの説明
description: この章では、すべての Azure RTOS NetX Secure DTLS サービスをアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 45966e7c8ea9be18bf294e8a7540e7226e803f29ae4f3ad3faaa29e4939c2ed8
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116801845"
---
# <a name="chapter-4-description-of-azure-rtos-netx-secure-dtls-services"></a>第 4 章: Azure RTOS NetX Secure DTLS サービスの説明

この章では、すべての Azure RTOS NetX Secure DTLS サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は API エラー チェックを無効にする際に使用される **NX_SECURE_DISABLE_ERROR_CHECKING** マクロの影響を受けませんが、太字以外の値は完全に無効になります。

- [nx_secure_dtls_client_session_start](#nx_secure_dtls_client_session_start)
- [nx_secure_dtls_packet_allocate](#nx_secure_dtls_packet_allocate)
- [nx_secure_dtls_psk_add](#nx_secure_dtls_psk_add)
- [nx_secure_dtls_server_create](#nx_secure_dtls_server_create)
- [nx_secure_dtls_server_delete](#nx_secure_dtls_server_delete)
- [nx_secure_dtls_server_local_certificate_add](#nx_secure_dtls_server_local_certificate_add)
- [nx_secure_dtls_server_local_certificate_remove](#nx_secure_dtls_server_local_certificate_remove)
- [nx_secure_dtls_server_notify_set](#nx_secure_dtls_server_notify_set)
- [nx_secure_dtls_server_psk_add](#nx_secure_dtls_server_psk_add)
- [nx_secure_dtls_server_session_send](#nx_secure_dtls_server_session_send)
- [nx_secure_dtls_server_session_start](#nx_secure_dtls_server_session_start)
- [nx_secure_dtls_server_start](#nx_secure_dtls_server_start)
- [nx_secure_dtls_server_stop](#nx_secure_dtls_server_stop)
- [nx_secure_dtls_server_trusted_certificate_add](#nx_secure_dtls_server_trusted_certificate_add)
- [nx_secure_dtls_server_trusted_certificate_remove](#nx_secure_dtls_server_trusted_certificate_remove)
- [nx_secure_dtls_server_x509_client_verify_configure](#nx_secure_dtls_server_x509_client_verify_configure)
- [nx_secure_dtls_server_x509_client_verify_disable](#nx_secure_dtls_server_x509_client_verify_disable)
- [nx_secure_dtls_session_client_info_get](#nx_secure_dtls_session_client_info_get)
- [nx_secure_dtls_session_create](#nx_secure_dtls_session_create)
- [nx_secure_dtls_session_delete](#nx_secure_dtls_session_delete)
- [nx_secure_dtls_session_end](#nx_secure_dtls_session_end)
- [nx_secure_dtls_session_local_certificate_add](#nx_secure_dtls_session_local_certificate_add)
- [nx_secure_dtls_session_local_certificate_remove](#nx_secure_dtls_session_local_certificate_remove)
- [nx_secure_dtls_session_receive](#nx_secure_dtls_session_receive)
- [nx_secure_dtls_session_reset](#nx_secure_dtls_session_reset)
- [nx_secure_dtls_ session_send](#nx_secure_dtls_-session_send)
- [nx_secure_dtls_session_trusted_certificate_add](#nx_secure_dtls_session_trusted_certificate_add)
- [nx_secure_dtls_session_trusted_certificate_remove](#nx_secure_dtls_session_trusted_certificate_remove)


## <a name="nx_secure_dtls_client_session_start"></a>nx_secure_dtls_client_session_start

NetX Secure DTLS Client のセッションを開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_client_session_start(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        NX_UDP_SOCKET *udp_socket,
                        NXD_ADDRESS *ip_address, UINT port,
                        UINT wait_option);

```

### <a name="description"></a>説明

このサービスでは、DTLS Client のセッションを開始し、指定された IP アドレスと UDP ポートでサーバーに接続します。ネットワーク通信には、指定された UDP ソケットが使用されます。

このサービスを呼び出す前に、nx_secure_dtls_session_create を使用して DTLS セッションの制御ブロックを初期化する必要があります。 さらに、DTLS Client では、nx_secure_dtls_session_trusted_certificate_add を使用して少なくとも 1 つの信頼された CA 証明書がセッションに追加されているか、事前共有キーが有効で構成されている必要があります。

### <a name="parameters"></a>パラメーター

- **dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。
- **udp_socket** リモート DTLS サーバーとのネットワーク通信を確立するために使用される、初期化された UDP ソケット。
- **ip_address** リモート DTLS サーバーのアドレスを含む IP アドレス構造へのポインター。
- **port** リモート DTLS サーバーとのネットワーク通信を確立するために使用される、初期化された UDP ソケット。
- **wait_option** 接続試行の中断オプション。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) セッションへの証明書の割り当てに成功しました。
- **NX_NOT_CONNECTED** (0x38) 指定されたアドレスとポートでサーバーに到達できません。
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 受信した TLS/DTLS メッセージの種類が正しくありません。
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** (0x106) リモート ホストによって提供された暗号はサポートされていません。
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) TLS ハンドシェイク中のメッセージの処理に失敗しました。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信メッセージがハッシュ MAC チェックに失敗しました。
- **NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） 基になる TCP ソケットの送信に失敗しました。
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 受信メッセージに無効な長さのフィールドがありました。
- **NX_SECURE_TLS_BAD_CIPHERSPEC** (0x10B) 受信した ChangeCipherSpec メッセージが正しくありませんでした。
- **NX_SECURE_TLS_INVALID_SERVER_CERT** (0x10C) 受信した TLS 証明書は、リモート DTLS サーバーの識別に使用できません。
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** (0x10D) リモート ホストによって提供された公開キー暗号はサポートされていません。
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) NetX Secure DTLS スタックによってサポートされている暗号スイートがないことがリモート ホストによって示されています。
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** (0x10F) 受信した DTLS メッセージのヘッダーの DTLS バージョンが不明です。
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** (0x110) 受信した DTLS メッセージのヘッダーの DTLS バージョンは、既知ですがサポートされていません。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 内部 TLS パケットの割り当てに失敗しました。
- **NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） リモート ホストが無効な証明書を提供しました。
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) リモート ホストによって、エラーを通知して TLS セッションを終了するアラートが送信されました。
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** (0x13B) 暗号スイート テーブル内のエントリに NULL 関数のポインターがありました。
- **NX_PTR_ERROR** (0x07) セッション、ソケット、またはアドレス ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                           &nx_crypto_tls_ciphers,
                                           crypto_metadata,
                                           sizeof(crypto_metadata),
                                           packet_buffer,
                                           sizeof(packet_buffer),
                                           REMOTE_CERT_NUMBER,
                                           remote_certs_buffer,
                                           sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
       Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                      trusted_cert_der,
                                      trusted_cert_der_len,
                                      NX_NULL, 0, NX_NULL, 0,
                                      NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                   &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                  &udp_socket, &server_ip,
                                                  4443,
                                                  NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
      /* Error! */
      return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_session_receive、nx_secure_dtls_session_send
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_packet_allocate"></a>nx_secure_dtls_packet_allocate

NetX Secure DTLS Session にパケットを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_packet_allocate(
                              NX_SECURE_DTLS_SESSION *session_ptr,
                         NX_PACKET_POOL *pool_ptr,
                         NX_PACKET **packet_ptr,
                              ULONG wait_option);

```

### <a name="description"></a>説明

このサービスでは、指定された NX_PACKET_POOL から、指定されたアクティブな DTLS セッションに NX_PACKET が割り当てられます。 このサービスは、DTLS 接続を介して送信されるデータ パケットを割り当てる際に、アプリケーションによって呼び出される必要があります。 DTLS セッションは、このサービスが呼び出される前に初期化される必要があります。

パケット データが移入された後に DTLS ヘッダーとフッターのデータを追加できるように、割り当てられたパケットは適切に初期化されます。 それ以外の動作は、*nx_packet_allocate* と同じです。

### <a name="parameters"></a>パラメーター

- **session_ptr** DTLS Session インスタンスへのポインター。
- **pool_ptr** パケットの割り当て元である NX_PACKET_POOL へのポインター。
- **packet_ptr** 新しく割り当てられたパケットへの出力ポインター。
- **wait_option** パケット割り当ての中断オプション。


### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） パケットの割り当てに成功。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) 基になるパケットの割り当てに失敗しました。
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** (0x101) 指定された DTLS セッションは初期化されていませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Allocate a new DTLS packet from the previously created packet pool and
previously initialized DTLS session.   */

status = nx_secure_dtls_packet_allocate(&dtls_session, &pool_0, &packet_ptr,
                                                              NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in
the variable packet_ptr.  */

```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize、nx_secure_dtls_session_create
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_dtls_session_send、nx_secure_dtls_session_receive
- nx_secure_dtls_session_end、nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_psk_add"></a>nx_secure_dtls_psk_add

NetX Secure DTLS Session に事前共有キーを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_psk_add(NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>説明

このサービスでは、事前共有キー (PSK)、その ID 文字列、ID ヒントが DTLS Session の制御ブロックに追加されます。 PSK 暗号スイートが有効にされて使用されている場合、PSK はデジタル証明書の代わりに使用されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。
- **pre_shared_key** 実際の PSK 値。
- **psk_length** PSK 値の長さ。
- **psk_identity** この PSK 値を識別するために使用される文字列。
- **identity_length** PSK ID の長さ。
- **hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。
- **hint_length** ヒントの文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) PSK が正常に追加されました。
- **NX_PTR_ERROR** (0x07) DTLS セッションのポインターが無効です。
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 別の PSK を追加できません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_psk_add(&dtls_session, psk,
                            sizeof(psk), “psk_1”, 4,
                            “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */


```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_psk_add、nx_secure_dtls_client_session_create

## <a name="nx_secure_dtls_server_create"></a>nx_secure_dtls_server_create

NetX Secure DTLS サーバーを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_create(
                NX_SECURE_DTLS_SERVER *server_ptr, NX_IP *ip_ptr,
                UINT port, ULONG timeout, VOID *session_buffer,
                UINT session_buffer_size,
                const NX_SECURE_TLS_CRYPTO *crypto_table,
                VOID *crypto_metadata_buffer, ULONG crypto_metadata_size,
                UCHAR *packet_reassembly_buffer,
                UINT packet_reassembly_buffer_size,
                UINT (*connect_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session,
                              NXD_ADDRESS *ip_address, UINT port),
                UINT (*receive_notify)(
                              NX_SECURE_DTLS_SESSION *dtls_session)));

```

### <a name="description"></a>説明

このサービスでは、特定の UDP ポートで受信された DTLS 要求を処理するために、DTLS サーバーのインスタンスが作成されます。 UDP はステートレスであるため、他の DTLS セッションがアクティブなときにも、複数のクライアントからの DTLS 要求を 1 つのポートで受信できます。 このため、アクティブなセッションを管理し、受信メッセージを適切なハンドラーに適切にルーティングするために、サーバーが必要となります。

ip_ptr パラメーターは、DTLS サーバーに関連付けられている内部 UDP ソケットに使用される NX_IP インスタンスを指します (これは NX_SECURE_DTLS_SERVER 制御ブロックに格納されます)。 IP インスタンスとポートは、nx_secure_dtls_server_start サービスを使用してサーバーをインスタンス化する UDP インターフェイスを定義するために使用されます。

セッション バッファー パラメーターは、DTLS サーバーのすべての可能な同時 DTLS セッションの制御ブロックを保持するために使用されます。 これは、NX_SECURE_DTLS_SESSION 制御ブロック構造体のサイズの偶数倍のサイズで割り当てる必要があります。

必要なメタデータのサイズを計算するには、API nx_secure_tls_metadata_size_calculate を使用できます。

packet_reassembly_buffer パラメーターは、暗号化を解除するために、UDP データグラムを完全な DTLS レコードに再構築するときに DTLS によって使用されます。これは、予想される最大の DTLS レコードを格納するために十分な大きさである必要があります (DTLS のレコードの最大サイズは 16 KB ですが、多くのアプリケーションでは 1 レコードでそれほど大きいデータは送信されません)。

connect_notify コールバック ルーチンは、新しい DTLS クライアントがサーバーに接続されるたびに呼び出されます。 その後、サービス *nx_secure_dtls_server_session_start* を使用して DTLS セッションを開始するのはアプリケーションの責任です。 このコールバック自体でセッションを開始することができますが、このコールバックはすべての下位レベルのネットワーク処理 (UDP など) を処理するために使用される IP スレッドによって呼び出されるため、接続のアプリケーション スレッド (またはアプリケーションによって作成される専用の DTLS スレッド) を通知するためにのみこのコールバックを使用することをお勧めします。 これは、DTLS セッション パラメーターを保存し (コールバックにパラメーターとして指定します)、もう一方のスレッドで nx_secure_dtls_server_session_start を呼び出すことによって簡単に行うことができます。 通常、connect_notify コールバックでは NX_SUCCESS が返されます。

receive_notify コールバック ルーチンは、確立された既存の DTLS セッションと一致する DTLS レコードが受信されるたびに呼び出されます (既存のセッションを識別するために、リモート ホストの IP アドレスとポートが使用されます)。 これは、DTLS で暗号化されて送信される "アプリケーション データ" を表します。 アプリケーションで、受信したデータを取得するには、指定された DTLS セッションでサービス *nx_secure_dtls_session_receive* を呼び出す必要があります。 connect_receive コールバックと同様に、セッションを別のスレッドに渡してメッセージ処理を行うことをお勧めします。これは、コールバックがその IP スレッドから呼び出されるためです。 通常、receive_notify コールバックでは NX_SUCCESS が返されます。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **ip_ptr** DTLS サーバーのネットワーク インターフェイスとして使用する、初期化された NX_IP 制御ブロックへのポインター。
- **port** DTLS サーバーの UDP ソケットがバインドされているローカル UDP ポート。
- **timeout** ネットワーク操作に使用されるタイムアウト値。
- **session_buffer** この DTLS Server インスタンスに割り当てられている NX_SECURE_DTLS_SESSION のすべてのインスタンスの制御ブロックを保持するためのバッファー領域。
- **session_buffer_size** セッション バッファーのサイズ。 これにより、DTLS Server に割り当てられる DTLS セッションの数が決まります。
- **crypto_table** すべての暗号化操作に使用される TLS/DTLS 暗号化テーブル構造体へのポインター。
- **crypto_metadata_buffer** 暗号化操作の計算と状態の情報を保持するためのバッファー領域。
- **crypto_metadata_size** メタデータ バッファーのサイズ。
- **packet_reassembly_buffer** 暗号化の解除で UDP データを DTLS レコードに再構築するために DTLS によって使用されるバッファー。
- **packet_reassembly_buffer_size** 再構築バッファーのサイズ。 通常は 16 KB を超えるサイズにする必要がありますが、アプリケーションによっては小さくすることができます。
- **connect_notify** リモート DTLS Client でこの DTLS サーバーに接続しようとするたびに呼び出されるコールバック ルーチン。
- **receive_notify** 既存の DTLS セッションを介してアプリケーション データが受信されるたびに呼び出されるコールバック。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーが正常に作成されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_PARAMETERS** (0x4D) セッション、パケットの再構築、または暗号化のための十分なバッファー領域がありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
    *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE, dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                        device_cert_der_len, NX_NULL, 0,
                        device_cert_key_der, device_cert_key_der_len,
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                           NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                                                   &send_packet, NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data,
        let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done, stop the server
    instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_delete"></a>nx_secure_dtls_server_delete

NetX Secure DTLS Server によって使用されるリソースを解放する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_delete(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>説明

このサービスでは、サーバーによって使用される内部 UDP ソケットを含む、DTLS サーバー インスタンスに割り当てられているリソースが解放されます。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に削除されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_STILL_BOUND** (0x42) UDP ソケットがまだバインドされています。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
*ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer, sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);


    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                         NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                        &packet_pool,
                                                        &send_packet,
                                                        NX_IP_PERIODIC_RATE);

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_local_certificate_add"></a>nx_secure_dtls_server_local_certificate_add

NetX Secure DTLS Server にローカル サーバーの ID 証明書を追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_local_certificate_add(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                 NX_SECURE_X509_CERT *certificate,
                                 UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、ローカル サーバーの ID 証明書が DTLS Server インスタンスに追加されます。 代替の認証メカニズム (事前共有キーなど) を使用する場合を除き、クライアントで DTLS サーバーに接続するには、少なくとも 1 つの ID 証明書が必要です。

cert_id パラメーターは、証明書の 0 以外の数値の識別子です。 これにより、DTLS サーバー ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。 X.509 サーバー証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **certificate** 以前に初期化された X.509 証明書構造体へのポインター。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーに証明書が正常に追加されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

*より完全な例については、*nx_secure_dtls_server_create* のリファレンスを参照してください。

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                            certificate_der_data,
                            sizeof(certificate_der_data),
                            NX_NULL, 0,
                            certificate_key_der_data,
                            sizeof(certificate_key_der_data),
                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_local_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_local_certificate_remove"></a>nx_secure_dtls_server_local_certificate_remove

NetX Secure DTLS Server からローカル サーバーの ID 証明書を削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_local_certificate_remove(
                                   NX_SECURE_DTLS_SERVER *server_ptr,
                                   UCHAR *common_name,
                                   UINT common_name_length,
                                   UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、DTLS Server インスタンスからローカル サーバーの ID 証明書が削除されます。 代替の認証メカニズム (事前共有キーなど) を使用する場合を除き、クライアントで DTLS サーバーに接続するには、少なくとも 1 つの ID 証明書が必要です。

削除する証明書は、X.509 の共通名、または *nx_secure_dtls_server_local_certificate_add* への呼び出しで割り当てられた数値である cert_id によって識別できます。 cert_id は証明書の識別にのみ使用され、アプリケーションによって管理されます。 数値の証明書 ID の代わりに共通名を使用する場合は、cert_id パラメーターを 0 に設定する必要があります。

> [!NOTE]
> DTLS ハンドシェイクの処理中に証明書を削除すると、予期しない動作が発生します。 証明書を削除する前に、サービス *nx_secure_dtls_server_stop* を呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **common_name** 削除する証明書の X.509 CommonName。 これを使用する場合は、cert_id を 0 として渡します。
- **common_name_length** common_name 文字列の長さ (バイト単位)。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。 これを使用する場合は、common_name パラメーターに NX_NULL を渡します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーから証明書が正常に削除されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS サーバーで cert_id または common_name に一致する証明書が見つかりませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        certificate_der_data,
                                        sizeof(certificate_der_data),
                                        NX_NULL, 0, certificate_key_der_data,
                                        sizeof(certificate_key_der_data),
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                     &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);

    /* At some point in the future we decide to remove the certificate we added.
    We can use the certificate identifier we passed into the call to
    nx_secure_dtls_local_certificate_add (value = 1); */
    status = nx_secure_dtls_server_local_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_notify_set"></a>nx_secure_dtls_server_notify_set

NetX Secure DTLS Server にオプションの通知コールバック ルーチンを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_notify_set(
                         NX_SECURE_DTLS_SERVER *server_ptr,
                         UINT (*disconnect_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session),
                         UINT (*error_notify)(
                                      NX_SECURE_DTLS_SESSION *dtls_session,
                                      UINT error_code));

```

### <a name="description"></a>説明

このサービスを使用すると、DTLS サーバーにオプションの通知コールバック ルーチンを追加できます。 コールバックが 1 つだけ必要な場合は、いずれかのコールバック パラメーターを NX_NULL として渡すことができます。

リモート クライアントで DTLS セッションを終了するときには、disconnect_notify コールバックが呼び出されます。 dtls_session パラメーターは、閉じられたセッション インスタンスです。 通常、このコールバックでは NX_SUCCESS が返されます。

error_notify コールバックは、DTLS エラーまたはタイムアウトが発生するたびに呼び出されます。 dtls_session パラメーターは、エラーが発生したセッション インスタンスです。error_code は、問題の原因となったエラーの数値の状態コードです（

返される可能性があるエラー コードの一覧については、付録 A NetX Secure のリターン/エラー コードに関するページを参照してください）。 通常、このコールバックでは NX_SUCCESS が返されます。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **disconnect_notify** リモート クライアントのホストで DTLS セッションが閉じられるたびに呼び出されるコールバック ルーチン。
- **error_notify** DTLS でエラーまたはタイムアウトが発生するたびに呼び出されるコールバック ルーチン。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバック ルーチンが正常に割り当てられました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

UINT disconnect_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
NXD_ADDRESS client_ip_addr;
UINT client_port;
UINT local_port;

    /* We have received a disconnection notice (CloseNotify message) from a
       remote client. Application can use the dtls_session parameter for any
       desired processing. */

    /* See what client disconnected by extracting its IP address and port.
       NOTE: depending on how the session ended, the client information may
             no longer be available. */
    status  = nx_secure_dtls_session_client_info_get(dtls_session,
                                                    &ip_addr,
                                                    &client_port,
                                                    &local_port);

    return(NX_SUCCESS);
}

UINT error_notify(NX_SECURE_DTLS_SESSION *dtls_session, UINT error_code)
{
    /* The DTLS server has encountered an error or timeout condition. We
    can use the error_code parameter to determine the error and we
    can insect the dtls_session for more information. */

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Other setup (e.g. certificates) goes here … */

    status = nx_secure_dtls_server_notify_set(&dtls_server, disconnect_notify,
                                                                 error_notify);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop

## <a name="nx_secure_dtls_server_psk_add"></a>nx_secure_dtls_server_psk_add

NetX Secure DTLS Server に事前共有キーを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_psk_add(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *pre_shared_key, UINT psk_length,
                                UCHAR *psk_identity,
                                UINT identity_length, UCHAR *hint,
                                UINT hint_length);

```

### <a name="description"></a>説明

このサービスでは、事前共有キー (PSK)、その ID 文字列、ID ヒントが DTLS サーバーの制御ブロックに追加されます。 PSK 暗号スイートが有効にされて使用されている場合、PSK はデジタル証明書の代わりに使用されます。

追加された PSK は、(nx_secure_dtls_server_create の呼び出しで指定されたセッション バッファーを介して) DTLS Server に割り当てられているすべての DTLS セッションにレプリケートされます。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **pre_shared_key** 実際の PSK 値。
- **psk_length** PSK 値の長さ。
- **psk_identity** この PSK 値を識別するために使用される文字列。
- **identity_length** PSK ID の長さ。
- **hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。
- **hint_length** ヒントの文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) PSK が正常に追加されました。
- **NX_PTR_ERROR** (0x07) DTLS サーバーへのポインターが無効です。
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** (0x125) 別の PSK を追加できません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to DTLS session.  */
status =  nx_secure_dtls_server_psk_add(&dtls_server, psk, sizeof(psk), “psk_1”,
   4, “Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */

```

### <a name="see-also"></a>参照

- nx_secure_dtls_psk_add、nx_secure_dtls_server_create

## <a name="nx_secure_dtls_server_session_send"></a>nx_secure_dtls_server_session_send

NetX Secure DTLS Server と確立された DTLS セッション経由でデータを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_session_send(
                                NX_SECURE_DTLS_SESSION *session_ptr,
                               NX_PACKET *packet_ptr);

```

### <a name="description"></a>説明

このサービスでは、確立された DTLS Server セッションを介して、リモートの DTLS Client のホストにデータのパケットが送信されます。 使用されるセッションは、nx_secure_dtls_session_create に指定された receive_notify コールバック ルーチンで取得されます。

パケットで提供されるデータは、*nx_secure_dtls_packet_allocate* を使用して割り当てる必要があります。このデータは、DTLS Session の暗号化パラメーターとルーチンを使用して暗号化され、DTLS Server の内部 UDP ポートを介してリモート ホスト (接続されているクライアントの IP アドレスとポート (DTLS Session に格納されています)) に送信されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** アプリケーションによって提供される receive_notify コールバック ルーチンから取得された、DTLS セッション インスタンスへのポインター。
- **packet_ptr** 以前に割り当てられ、アプリケーション データが移入された NX_PACKET インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーが正常に作成されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる UDP の送信操作でエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;


/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key
    and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                        device_cert_der,
                                        device_cert_der_len,
                                        NX_NULL,
                                        0, device_cert_key_der,
                                        device_cert_key_der_len,
                                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
        status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

        /* Check for errors and prepare response data
        (e.g. nx_packet_data_append). */

        /* Send response to client. */
        status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                            send_packet);

}

/* If not processing connections or received data, let the thread sleep. */
if(!connect_flag && !receive_flag)
{
    tx_thread_sleep(100);
}
    }

    /* Server processing is done, stop the server instance
    from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_create
- nx_secure_dtls_server_session_start、nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_session_start"></a>nx_secure_dtls_server_session_start

NetX Secure DTLS Server から DTLS Session を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_session_start(
                 NX_SECURE_DTLS_SESSION *session_ptr, UINT wait_option);

```

### <a name="description"></a>説明

このサービスでは、リモートの DTLS Client がサーバーに接続して DTLS 接続を要求したときに、サーバー側の DTLS ハンドシェイクが実行され、DTLS Server セッションが開始されます。

DTLS Session は、nx_secure_dtls_server_create に指定された connect_notify コールバック ルーチンで取得されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** DTLS Server の connect_notify コールバックから取得された DTLS Session インスタンスへのポインター。
- **wait_option** ネットワーク操作に使用される ThreadX の待機値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーが正常に作成されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) DTLS ハンドシェイクのパケットを割り当てることができませんでした (パケット プールが空です)。
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) 有効な DTLS レコードではないデータを受信しました。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS レコードを正しくハッシュ化できませんでした (暗号化エラー)。
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 暗号化のパディング チェックに失敗しました。
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) DTLS ハンドシェイク中にリモート ホストからアラートを受信しました。
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) DTLS ハンドシェイク中に認識されないメッセージを受信しました。
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 長さが無効な DTLS レコードを受信しました。
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** (0x10E) サポートされていない DTLS 暗号スイートの ClientHello を受信しました。
- **NX_SECURE_TLS_BAD_COMPRESSION_METHOD** (0x118) 不明な圧縮方法の ClientHello を受信しました。
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** (0x107) 全般的な (詳細不明の) ハンドシェイク エラー。通常は拡張処理の問題が原因です。
- **NX_SECURE_TLS_UNSUPPORTED_FEATURE** (0x130) DTLS ハンドシェイク中に、まだサポートされていない機能が呼び出されました。
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 不明な暗号スイートが見つかりました (内部暗号化エラーを示しています)。
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) DTLS バージョンが一致しない DTLS レコードを受信しました。
- **NX_SECURE_TLS_FINISHED_HASH_FAILURE** (0x115) DTLS ハンドシェイクのハッシュの検証に失敗しました。セッションは無効です。
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 内部の UDP 送信に失敗しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
* DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT, NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table, crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer), packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len, NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                    &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                                    NX_IP_PERIODIC_RATE);
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                    &packet_pool, &send_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                                                                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* Server processing is done,
    stop the server instance from accepting requests. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_create、nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_local_certificate_add

## <a name="nx_secure_dtls_server_start"></a>nx_secure_dtls_server_start

構成された UDP ポートでリッスンする NetX Secure DTLS Server インスタンスを開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_start(
                  NX_SECURE_DTLS_SERVER *server_ptr);

```

### <a name="description"></a>説明

このサービスでは DTLS Server が開始されます。 呼び出しから制御が戻ると、サーバーがアクティブになり、DTLS クライアントからの受信要求の処理が開始されます。 サーバー インスタンスは、サービス *nx_secure_dtls_server_create* を使用して構成されている必要があります。

> [!NOTE]
> このサービスでは、内部 DTLS Server の UDP ポートが構成済みのローカル ポートにバインドされます。このため、発生するほとんどの問題は UDP 通信とネットワーク構成に関係するものになります。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に開始されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_NOT_ENABLED** (0x14) UDP が有効になっていません。
- **NX_NO_FREE_PORTS** (0x45) 使用可能な UDP ポートがありません。
- **NX_INVALID_PORT** (0x46) UDP ポートが無効です。
- **NX_ALREADY_BOUND** (0x22) UDP ポートは既にバインドされています。
- **NX_PORT_UNAVAILABLE** (0x23) UDP ポートを使用できません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                        &receive_packet,
                                                        NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session, &packet_pool,
                &send_packet, NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
                (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_stop、nx_secure_dtls_server_create
- nx_secure_dtls_server_delete、nx_secure_dtls_session_receive
- nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_stop"></a>nx_secure_dtls_server_stop

アクティブな NetX Secure DTLS Server インスタンスを停止する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_stop(NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>説明

このサービスでは、構成されている UDP ポートでの DTLS Server によるリスニングが停止され、関連付けられているすべての DTLS セッションがリセットされ、進行中の DTLS 通信が停止されます。

### <a name="parameters"></a>パラメーター

- **server_ptr** アクティブな DTLS Server インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に停止されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array or list in case a new connection is
         attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
   NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session,
                                    NXD_ADDRESS *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate, device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);

        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* We have exited the processing loop, stop the server. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_server_delete、nx_secure_dtls_session_receive
- nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_server_trusted_certificate_add"></a>nx_secure_dtls_server_trusted_certificate_add

NetX Secure DTLS Server に信頼された CA 証明書を追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_trusted_certificate_add(
                                         NX_SECURE_DTLS_SERVER *server_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、信頼された CA 証明書または中間 CA 証明書が DTLS Server インスタンスに追加され、すべての内部 DTLS サーバー セッションに割り当てられます。 これは、*nx_secure_dtls_server_x509_client_verify_configure* を使用して X.509 クライアント証明書の認証が有効にされている場合にのみ必要となります。 追加された証明書は、受信したクライアントの X.509 証明書の検証に使用されます。

cert_id パラメーターは、証明書の 0 以外の数値の識別子です。 これにより、DTLS サーバー ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。 X.509 サーバー証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **certificate** 以前に初期化された X.509 証明書構造体へのポインター。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーに証明書が正常に追加されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

*より完全な例については、*nx_secure_dtls_server_create* のリファレンスを参照してください。

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                LOCAL_SERVER_PORT,
                                NX_IP_PERIODIC_RATE,
                                dtls_server_session_buffer,
                                sizeof(dtls_server_session_buffer),
                                &tls_crypto_table,
                                crypto_metadata_buffer,
                                sizeof(crypto_metadata_buffer),
                                packet_buffer,
                                sizeof(packet_buffer),
                                dtls_server_connect_notify,
                                dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0, NX_NULL,
                                            0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add trusted CA certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Process incoming requests and data. */
    }

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_local_certificate_add
- nx_secure_dtls_server_trusted_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_trusted_certificate_remove"></a>nx_secure_dtls_server_trusted_certificate_remove

NetX Secure DTLS Server から信頼された CA 証明書を削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_server_trusted_certificate_remove(
                                NX_SECURE_DTLS_SERVER *server_ptr,
                                UCHAR *common_name,
                                UINT common_name_length,
                                UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、DTLS Server インスタンスから信頼された CA 証明書が削除されます。 信頼された CA 証明書が必要になるのは、*nx_secure_dtls_server_x509_client_verify_configure* を呼び出されて X.509 クライアント証明書の検証が有効になっている DTLS Server だけです。

削除する証明書は、X.509 の共通名、または *nx_secure_dtls_server_trusted_certificate_add* への呼び出しで割り当てられた数値である cert_id によって識別できます。 cert_id は証明書の識別にのみ使用され、アプリケーションによって管理されます。 数値の証明書 ID の代わりに共通名を使用する場合は、cert_id パラメーターを 0 に設定する必要があります。

> [!NOTE]
> DTLS ハンドシェイクの処理中に証明書を削除すると、予期しない動作が発生することがあります。 証明書を削除する前に、サービス *nx_secure_dtls_server_stop* を呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **common_name** 削除する証明書の X.509 CommonName。 これを使用する場合は、cert_id を 0 として渡します。
- **common_name_length** common_name 文字列の長さ (バイト単位)。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。 これを使用する場合は、common_name パラメーターに NX_NULL を渡します。


### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS サーバーから証明書が正常に削除されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS サーバーで cert_id または common_name に一致する証明書が見つかりませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                                    certificate_der_data,
                                                    sizeof(certificate_der_data),
                                                    NX_NULL, 0, NX_NULL, 0,
                                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                       &trusted_ca_certificate, 1);

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before removing a certificate. */
    Status = nx_secure_dtls_server_stop(&dtls_server);


/* At some point in the future we decide to remove the certificate we added. We can
       use the certificate identifier we passed into the call to
       nx_secure_dtls_trusted_certificate_add (value = 1); */
    status = nx_secure_dtls_server_trusted_certificate_remove(&dtls_server,
                                                          NX_NULL, 0, 1);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_configure"></a>nx_secure_dtls_server_x509_client_verify_configure

クライアント証明書を要求して確認するように NetX Secure DTLS Server を構成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_server_x509_client_verify_configure(
                           NX_SECURE_DTLS_SERVER *server_ptr,
                               UINT certs_per_session,
                               UCHAR *certs_buffer, ULONG buffer_size);

```

### <a name="description"></a>説明

このサービスでは、DTLS Client 証明書を要求して確認するように DTLS Server が構成されます。 このオプションの機能は、クライアント認証に他のメカニズム (事前共有キーなど) ではなく X.509 証明書が望ましい場合に使用されます。

> [!IMPORTANT]
> *DTLS Server がこのサービスを使用してクライアント証明書を検証するように構成されている場合、nx_secure_dtls_server_trusted_certificate_add を使用して少なくとも 1 つの信頼された CA 証明書をサーバーに追加する必要があります。そうしないと、信頼されたストアに対してクライアント証明書を検証できないため、すべての受信クライアント接続がサーバーで拒否されます。*

このサービスを呼び出すと、DTLS Server インスタンスでは (開始された後に)、DTLS ハンドシェイクの一環としてクライアント証明書を要求します。 クライアントが ID 証明書 (および該当する場合は関連する証明書チェーン) を使用して適切に構成されていると想定し、DTLS Server では、クライアント証明書のデータを処理するためにメモリを割り当てる必要があります。 このメモリは *certs_buffer* パラメーターとして渡されます。

DTLS Client からの予想される最大の証明書チェーン ("*DTLS クライアント x DTLS サーバーのセッション数*") を格納できるように、certs_buffer のサイズを設定する必要があります。 バッファーは、クライアント証明書チェーンで予想される最大の証明書数を表す *certs_per_session* パラメーターを使用して、使用可能なセッション間で分割されます。 また、このバッファーでは、証明書データを解析するために使用される NX_SECURE_X509_CERT データ構造のための領域が提供される必要があります。

適切なバッファー サイズを計算するには、次の式を使用します。

```C
buffer_size = (# of DTLS sessions in server) *
                (certs_per_session) *
                (    maximum expected certificate size +
                      sizeof(NX_SECURE_X509_CERT)    )

```

- DTLS セッションの数は、nx_secure_dtls_server_create に渡されるセッション バッファーのサイズによって決まります。
- certs_per_session は、クライアント証明書チェーンで予想される最大の証明書数に設定する必要があります。
- 予想される証明書の最大サイズは、アプリケーション、キーのサイズ、およびその他の要因によって異なりますが、通常は 2 KB で十分です。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。
- **certs_per_session** 各 DTLS サーバー セッションに割り当てる証明書の数。
- **certs_buffer** 受信証明書データ用のバッファー領域。
- **buffer_size** 証明書バッファーのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) X.509 クライアント検証が正常に構成されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_PARAMETERS** (0x4D) 証明書ストアが無効です (DTLS サーバー インスタンスが初期化されていない?)。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                                    sizeof(certificate_der_data),
                                    NX_NULL, 0,
                                    NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                                &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_x509_client_verify_disable
- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_server_x509_client_verify_disable"></a>nx_secure_dtls_server_x509_client_verify_disable

NetX Secure DTLS Server のクライアント X.509 証明書の検証を無効にする

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_server_x509_client_verify_disable(
                           NX_SECURE_DTLS_SERVER *server_ptr);
```

### <a name="description"></a>説明

このサービスでは、DTLS Server での X.509 クライアント証明書の検証が無効にされます。 X.509 クライアント証明書の検証が有効になっていない場合、このサービスは効果がありません。

> [!NOTE]
> アクティブな DTLS Server インスタンスでクライアント認証を無効にすると、予期しない動作が発生する可能性があります。 サーバーの状態を変更する前に、nx_secure_dtls_server_stop サービスを呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **server_ptr** 以前に作成された DTLS サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) X.509 クライアント認証が正常に無効にされました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Configure number of sessions per server. */
#define DTLS_SERVER_SESSIONS 3

/* Define parameters for X.509 client verification. */
#define MAX_CERT_SIZE         (2000)       /* 2KB expected maximum certificate size. */
#define CERTS_PER_SESSION (3)            /* Assume maximum chain length of 3 certificates. */
#define CERT_BUFFER_SIZE     (DTLS_SERVER_SESSIONS * CERTS_PER_SESSION * \
 (MAX_CERT_SIZE + sizeof(NX_SECURE_X509_CERT))

/* Define our incoming certificate buffer. */
UCHAR client_certs_buffer[CERT_BUFFER_SIZE];

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Certificate control block and data. */
NX_SECURE_X509_CERT trusted_ca_certificate;
UCHAR certificate_der_data[] = { … };

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                    LOCAL_SERVER_PORT,
                                    NX_IP_PERIODIC_RATE,
                                    dtls_server_session_buffer,
                                    sizeof(dtls_server_session_buffer),
                                    &tls_crypto_table,
                                    crypto_metadata_buffer,
                                    sizeof(crypto_metadata_buffer),
                                    packet_buffer,
                                    sizeof(packet_buffer),
                                    dtls_server_connect_notify,
                                    dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize trusted certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&trusted_ca_certificate,
                                    certificate_der_data,
                        sizeof(certificate_der_data), NX_NULL, 0,
                        NX_NULL, 0, NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_trusted_certificate_add(&dtls_server,
                                            &trusted_ca_certificate, 1);

    /* Configure client X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_configure(&dtls_server,
        CERTS_PER_SESSION,
        client_certs_buffer,
        sizeof(client_certs_buffer));

    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Process client requests, etc… */

    /* Stop the server before changing state. */
    status = nx_secure_dtls_server_stop(&dtls_server);

    /* Disable X.509 authentication and verification. */
    status = nx_secure_dtls_server_x509_client_verify_disable(&dtls_server);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_x509_client_verify_configure
- nx_secure_dtls_server_start、nx_secure_dtls_server_create
- nx_secure_dtls_server_session_start
- nx_secure_dtls_server_session_stop
- nx_secure_dtls_server_trusted_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_client_info_get"></a>nx_secure_dtls_session_client_info_get

DTLS Server セッションからリモート クライアントの情報を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_session_client_info_get(
                                    NX_SECURE_DTLS_SESSION *session_ptr,
                                    NXD_ADDRESS *client_ip_address,
                                    UINT *client_port, UINT *local_port);

```

### <a name="description"></a>説明

このサービスでは、特定の DTLS Server セッションに接続されている DTLS Client に関するネットワーク情報が返されます。 返される情報は、リモート クライアントの IP アドレスと UDP ポート、およびクライアントが接続されているローカル サーバーのポートで構成されます。

一般に、DTLS セッション インスタンスは、いずれかの DTLS 通知コールバック ルーチン (nx_secure_dtls_server_create に渡される connect_notify または receive_notify コールバックなど) の呼び出しで取得されたものです。

### <a name="parameters"></a>パラメーター

- **session_ptr** アクティブな DTLS サーバー セッション インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に削除されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_SOCKET** (0x13) 関連付けられている UDP ソケットが有効ではありません (セッションが初期化されていない?)。
- **NX_NOT_CONNECTED** (0x38) UDP ソケットが接続されていません – クライアント接続が切断されたか、まだ確立されていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define DTLS_SERVER_SESSION (3)

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SERVER dtls_server;

/* Allocate space for DTLS sessions in the DTLS server. */
UCHAR dtls_server_session_buffer[sizeof(NX_SECURE_DTLS_SESSION)
                                        * DTLS_SERVER_SESSIONS];

/* Flag used to indicate that a DTLS Client has connected. */
UINT connect_flag = 0;

/* Flag used to indicate application data reception. */
UINT receive_flag = 0;

/* Pointer to newly-connected DTLS session.
   NOTE: In practice this should be an array
   or list in case a new connection is
   attempted while a previous session is being started. */
NX_SECURE_DTLS_SESSION *new_dtls_session;

/* Pointer to session for application data receive.
NOTE: Should be an array or list as
   with new_dtls_session */
NX_SECURE_DTLS_SESSION *receive_dtls_session;

/* Connect notify callback routine. */
UINT dtls_server_connect_notify(NX_SECURE_DTLS_SESSION *dtls_session, NXD_ADDRESS
                                                            *ip_address, UINT port)
{
    /* NOTE: proper inter-thread communication procedures (e.g. mutex handling)
             Omitted for clarity. */

    /* Notify application thread that a connection request has been received. */
    connect_flag = 1;
    new_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Receive notify callback routine invoked when DTLS application data is received
   on an existing DTLS server session. */
UINT dtls_server_receive_notify(NX_SECURE_DTLS_SESSION *dtls_session)
{
    NXD_ADDRESS client_ip;
    UINT client_port, server_port;

    /* Get DTLS client information which can be used in filtering or associating
       the DTLS session with application data (e.g. a session pointer table). */
    status = nx_secure_dtls_session_client_info_get(dtls_session, &client_ip,
   &client_port, &server_port);

    /* Receive and process DTLS record.
       NOTE: Mutex handling omitted for clarity. */
    receive_flag = 1;
    receive_dtls_session = dtls_session;

    return(NX_SUCCESS);
}

/* Primary application thread for handling DTLS server operations. */
void dtls_server_thread(void)
{
    NX_PACKET *send_packet;
    NX_PACKET *receive_packet;
    UINT status;

    /* Setup DTLS Server instance. */
    status = nx_secure_dtls_server_create(&dtls_server, &ip_instance,
                                            LOCAL_SERVER_PORT,
                                            NX_IP_PERIODIC_RATE,
                                            dtls_server_session_buffer,
                                            sizeof(dtls_server_session_buffer),
                                            &tls_crypto_table,
                                            crypto_metadata_buffer,
                                            sizeof(crypto_metadata_buffer),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            dtls_server_connect_notify,
                                            dtls_server_receive_notify);

    /* Check for errors. */

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            device_cert_der,
                                            device_cert_der_len,
                                            NX_NULL, 0,
                                            device_cert_key_der,
                                            device_cert_key_der_len,
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_server_local_certificate_add(&dtls_server,
                                                        &certificate, 1);


    /* Start server. */
    status = nx_secure_dtls_server_start(&dtls_server);

    /* Loop continuously to handle incoming data. */
    while(1)
    {
        /* Check for new connections. Muxtex handling omitted for clarity. */
        if(connect_flag)
        {
            /* We have a new connection attempt, start the DTLS session. */
            status = nx_secure_dtls_server_session_start(new_dtls_session,
                                            NX_IP_PERIODIC_RATE);

            /* Check for errors. */
        }

        /* Check for received application data. */
        if(receive_flag)
        {
            /* We have received data over a previously-established DTLS session.
               Mutex handling omitted for clarity. */
            Status = nx_secure_dtls_session_receive(receive_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

            /* Process received data… */

            /* Prepare and send response to client. */
            status = nx_secure_dtls_packet_allocate(receive_dtls_session,
                                                &packet_pool,
                                                &send_packet,
                                                NX_IP_PERIODIC_RATE);

            /* Check for errors and prepare response data
            (e.g. nx_packet_data_append). */

            /* Send response to client. */
            status = nx_secure_dtls_server_session_send(receive_dtls_session,
                send_packet);
        }

        /* If not processing connections or received data, let the thread sleep. */
        if(!connect_flag && !receive_flag)
        {
            tx_thread_sleep(100);
        }
    }

    /* If we exit the processing loop, clean up the server. */
    status = nx_secure_dtls_server_delete(&dtls_server);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_server_start、nx_secure_dtls_server_stop
- nx_secure_dtls_server_create、nx_secure_dtls_server_delete
- nx_secure_dtls_session_receive、nx_secure_dtls_server_session_send
- nx_secure_dtls_server_session_start

## <a name="nx_secure_dtls_session_create"></a>nx_secure_dtls_session_create

NetX Secure DTLS Session を作成して構成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_session_create(
                        NX_SECURE_DTLS_SESSION *dtls_session,
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        VOID *metadata_buffer, ULONG metadata_size,
                        UCHAR *packet_reassembly_buffer,
                        UINT packet_reassembly_buffer_size,
                        UINT certs_number,
                        UCHAR *remote_certificate_buffer,
                        ULONG remote_certificate_buffer_size));

```

### <a name="description"></a>説明

このサービスでは、DTLS セッションを作成して構成します。 DTLS Server セッションは DTLS Server のメカニズムで管理されるため、通常、これは DTLS Client のセッションを作成するために使用されます (*nx_secure_dtls_server_create* を参照してください)。ただし、アプリケーションで 1 つのスタンドアロン DTLS Server セッション インスタンスを作成する必要がある場合に、このサービスを使用できます <sup>7</sup>。

パラメーターによって、DTLS セッションをインスタンス化するために必要な情報とメモリの割り当てが構成されます。 crypto_table パラメーターは、TLS/DTLS の暗号化と認証に必要なすべての暗号化ルーチンを含む TLS テーブルです。 metadata_buffer は、暗号化の計算に使用されます (『NetX Secure TLS ユーザー ガイド』の nx_secure_tls_metadata_size_calculate を参照してください)。また、packet_reassembly_buffer は、暗号化の解除で UDP データグラムを完全な DTLS レコードに再構築するために使用されます。

DTLS Client には、受信した DTLS Server の証明書チェーンを格納して処理するための領域が必要であり、certs_number と remote_certificate_buffer が必要となります。 このバッファーでは、接続先のすべてのサーバーの証明書チェーンで予想される最大サイズを格納できる必要があります。 このバッファーは、予想される証明書の数 (certs_number パラメーター) によって分割されます。また、証明書ごとに 1 つの NX_SECURE_X509_CERT 構造体を保持するのに十分な大きさである必要があります。 バッファーのサイズは、次の式を使用して判別できます。

```C
remote_certificate_buffer_size = (certs_number) *
                 (maximum cert size + sizeof(NX_SECURE_X509_CERT))
```

- certs_number は、サーバーの証明書チェーンで予想される証明書の最大数です
- 証明書の最大サイズは、使用されるキーのサイズと証明書の情報によって異なりますが、通常は 2 KB で十分です。

**7** このルーチンを使用して DTLS Server のセッションを作成することは推奨されておらず、いくつかの制限があります。 主な問題は、セッションで追加のクライアント接続が正常に処理されないことです。UDP はコネクションレスであるため、2 番目のクライアントでは、以前の DTLS セッションがまだアクティブな状態で、そのセッションによりサーバー セッションがエラーで終了する可能性があるときに、サーバーの UDP ポートに対して正当にデータを送信できます。

### <a name="parameters"></a>パラメーター

- **dtls_session** 初期化されていない DTLS Session 構造体へのポインター。
- **crypto_table** すべての暗号化操作に使用される TLS/DTLS 暗号化テーブル構造体へのポインター。
- **crypto_metadata_buffer** 暗号化操作の計算と状態の情報を保持するためのバッファー領域。
- **crypto_metadata_size** メタデータ バッファーのサイズ。
- **packet_reassembly_buffer** 暗号化の解除で UDP データを DTLS レコードに再構築するために DTLS によって使用されるバッファー。
- **packet_reassembly_buffer_size** 再構築バッファーのサイズ。 通常は 16 KB を超えるサイズにする必要がありますが、アプリケーションによっては小さくすることができます。
- **certs_number** リモート サーバーの証明書チェーンで予想される証明書の最大数。
- **remote_certificate_buffer** 受信証明書データ用のバッファー領域。
- **remote_certificate_buffer_size** 証明書バッファーのサイズ。


### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) セッションが正常に作成されました。
- **NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。
- **NX_INVALID_PARAMETERS** (0x4D) は、パケットの再構築、証明書、または暗号化のための十分なバッファー領域がありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
    &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                            &udp_socket, &server_ip,
                                            4443,
                                            NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session,
                                            &receive_packet,
                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_client_session_start,nx_secure_dtls_session_receive
- nx_secure_dtls_session_send

## <a name="nx_secure_dtls_session_delete"></a>nx_secure_dtls_session_delete

NetX Secure DTLS Session によって使用されているリソースを解放する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_session_delete(
                        NX_SECURE_DTLS_SESSION *dtls_session);

```

### <a name="description"></a>説明

このサービスでは、DTLS セッションが削除され、その作成時に割り当てられたすべてのリソースが解放されます。

### <a name="parameters"></a>パラメーター

- **dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) セッションが正常に削除されました。
- **NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                        trusted_cert_der,
                                        trusted_cert_der_len,
                                        NX_NULL, 0, NX_NULL, 0,
                                        NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                                    &udp_socket,
                                                    &server_ip, 4443,
                                                    NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                &receive_packet,
                                                NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_end"></a>nx_secure_dtls_session_end

Active NetX Secure DTLS Session を停止する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_session_end(NX_SECURE_DTLS_SESSION *dtls_session,
                                UINT wait_option);

```

### <a name="description"></a>説明

このサービスでは、TLS/DTLS の CloseNotify アラートをリモート ホストに送信することによって、アクティブな DTLS セッションが終了されます。 使用される IP アドレスとポートは、以前に nx_secure_dtls_session_send を呼び出したときに使用されたものです。

### <a name="parameters"></a>パラメーター

- **dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。
- **wait_option** ネットワーク操作に使用される ThreadX の待機値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) セッションが正常に削除されました。
- **NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** (0x111) CloseNotify アラートのパケットを割り当てることができませんでした。
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105): 内部エラーが発生した可能性があります - 暗号化ルーチンが認識されません。
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる UDP の送信に失敗しました。
- **NX_IP_ADDRESS_ERROR** (0x21) リモート ホストの IP アドレスでエラーが発生しました。
- **NX_NOT_BOUND** (0x24) 基になる UDP ソケットがポートにバインドされていません。
- **NX_INVALID_PORT** (0x46) UDP ポートが無効です。
- **NX_PORT_UNAVAILABLE** (0x23) UDP ポートを使用できません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session,
                                                &send_packet,
                                                &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session,
                                        NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

    }

```

### <a name="see-also"></a>参照

- nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_local_certificate_add"></a>nx_secure_dtls_session_local_certificate_add

NetX Secure DTLS Session にローカル ID 証明書を追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_session_local_certificate_add(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            NX_SECURE_X509_CERT *certificate,
                            UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、ローカル ID 証明書が DTLS Session インスタンスに追加されます。 一般に、このサービスは、DTLS Client セッションでリモート サーバー ホストに ID 証明書を提示する必要がある場合に使用されます。 これは DTLS のオプションの構成であり、通常、DTLS Client には証明書は必要ありません。 ID 証明書には、関連付けられた秘密キーが必要です。

cert_id パラメーターは、証明書の 0 以外の数値の識別子です。 これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。 X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

### <a name="parameters"></a>パラメーター

- **session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。
- **certificate** 以前に初期化された X.509 証明書構造体へのポインター。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS セッションに証明書が正常に追加されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

*より完全な例については、*nx_secure_dtls_session_create* のリファレンスを参照してください。

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity
certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

/* Create a TLS session for our socket. Ciphers and metadata defined
   elsewhere. See nx_secure_tls_session_create reference for more
   information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
{
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
}

/* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len,
                                    NX_NULL, 0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

/* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                              &certificate, 1);

    /* Initialize local server identity certificate with key and
    add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                        certificate_der_data,
                        sizeof(certificate_der_data),
                        NX_NULL, 0,
                        certificate_key_der_data,
                        sizeof(certificate_key_der_data),
                        NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                    &certificate, 1);

/* Set up IP address of remote host. */
server_ip.nxd_ip_version = NX_IP_VERSION_V4;
server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


/* Now we can start the DTLS session as normal. */
status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                    &udp_socket, &server_ip, 4443,
                                    NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_session_create、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_start
- nx_secure_dtls_session_local_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_local_certificate_remove"></a>nx_secure_dtls_session_local_certificate_remove

NetX Secure DTLS Session からローカル ID 証明書を削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_session_local_certificate_remove(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         UCHAR *common_name,
                                         UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、証明書 ID 番号 (nx_secure_dtls_session_local_certificate_add を使用して証明書が追加されたときに割り当てられた) または X.509 の CommonName フィールドを使用して、DTLS Session インスタンスからローカル ID 証明書が削除されます。

証明書の照合に common_name が使用される場合は、cert_id パラメーターを 0 に設定する必要があります。 cert_id を使用する場合は、common_name に NX_NULL を値として渡す必要があります。

cert_id パラメーターは、証明書の 0 以外の数値の識別子です。 これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。 X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

### <a name="parameters"></a>パラメーター

- **session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。
- **common_name** 照合する CommonName 文字列へのポインター。
- **common_name_length** common_name 文字列の長さ。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS セッションから証明書が正常に削除されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS セッションで cert_id または common_name に一致する証明書が見つかりませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

*より完全な例については、*nx_secure_dtls_session_create* のリファレンスを参照してください。

```C

/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

        /* Initialize local server identity certificate with key
        and add to server. */
        status = nx_secure_x509_certificate_initialize(&certificate,
                                certificate_der_data,
                                sizeof(certificate_der_data),
                                NX_NULL, 0,
                                certificate_key_der_data,
                                sizeof(certificate_key_der_data),
                                NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

        /* Add local server identity certificate to DTLS server with ID of 1. */
        status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                            &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
        &udp_socket, &server_ip, 4443,
        NX_IP_PERIODIC_RATE);

        /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
        status = nx_secure_dtls_session_local_certificate_remove(&client_dtls_session,
                                                                NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_session_create、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_start
- nx_secure_dtls_session_local_certificate_add
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_receive"></a>nx_secure_dtls_session_receive

確立された NetX Secure DTLS Session 経由でアプリケーション データを受信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_session_receive(
                                NX_SECURE_DTLS_SESSION *dtls_session,
                                NX_PACKET **packet_ptr_ptr,
                                UINT wait_option);

```

### <a name="description"></a>説明

このサービスでは、アクティブな DTLS Session によって受信されたアプリケーション データが返されます。 DTLS Session は、DTLS Server セッション (DTLS Server インスタンスによって管理されます) または DTLS Client セッションのいずれかです。 返されるパケットは、任意の NX_PACKET API サービスを使用して処理できます (詳細については、NetX のドキュメントを参照してください)。

### <a name="parameters"></a>パラメーター

- **dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。
- **packet_ptr_ptr** 戻りパケットの NX_PACKET ポインターへのポインター。
- **wait_option** ネットワーク操作に使用される ThreadX の待機値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) アプリケーション データのパケットが正常に受信されました。
- **NX_PTR_ERROR** (0x07) セッションまたはパケットのポインターが無効です。
- **NX_NOT_ENABLED** (0x14) UDP が有効になっていません。
- **NX_NOT_BOUND** (0x24) UDP ソケットがポートにバインドされていません。
- **NX_SECURE_TLS_INVALID_PACKET** (0x104) 有効な DTLS レコードではないデータを受信しました。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** (0x108) DTLS レコードを正しくハッシュ化できませんでした (暗号化エラー)。
- **NX_SECURE_TLS_PADDING_CHECK_FAILED** (0x12A) 暗号化のパディング チェックに失敗しました。
- **NX_SECURE_TLS_ALERT_RECEIVED** (0x114) リモート ホストからアラートを受信しました。
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** (0x102) 認識されないメッセージを受信しました。
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** (0x10A) 長さが無効な DTLS レコードを受信しました。
- **NX_SECURE_TLS_UNKNOWN_CIPHERSUITE** (0x105) 不明な暗号スイートが見つかりました (内部暗号化エラーを示しています)。
- **NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED** (0x12E) DTLS バージョンが一致しない DTLS レコードを受信しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
    status = nx_secure_dtls_session_receive(&client_dtls_session, &receive_packet,
                                                            NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_end(&client_dtls_session, NX_IP_PERIODIC_RATE);

    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_client_session_start、nx_secure_dtls_session_end
- nx_secure_dtls_session_send、nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_session_reset"></a>nx_secure_dtls_session_reset

NetX Secure DTLS Session インスタンスのデータをクリアする

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_dtls_session_reset(NX_SECURE_DTLS_SESSION *dtls_session);
```

### <a name="description"></a>説明

このサービスでは、DTLS セッションをリセットし、すべての一時暗号化データをクリアし、その構造体を新しいセッションに再利用できるようにします。 nx_secure_dtls_session_create を繰り返し呼び出す必要がないように、永続データ (証明書ストアなど) は維持されます。

### <a name="parameters"></a>パラメーター

- **dtls_session** 以前に初期化された DTLS Session の構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) セッションが正常にリセットされました。
- **NX_PTR_ERROR** (0x07) セッションまたはバッファーのポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                        &nx_crypto_tls_ciphers,
                                        crypto_metadata,
                                        sizeof(crypto_metadata),
                                        packet_buffer,
                                        sizeof(packet_buffer),
                                        REMOTE_CERT_NUMBER,
                                        remote_certs_buffer,
                                        sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
    printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
            Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
        /* Error! */
        return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

    /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
    status = nx_secure_dtls_session_reset(&client_dtls_session);

    /* A new session can now be started using the same structure. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,



    /* Clean up. */
    status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_delete

## <a name="nx_secure_dtls_-session_send"></a>nx_secure_dtls_ session_send

DTLS セッション経由でデータを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_session_send(NX_SECURE_DTLS_SESSION *session_ptr,
                                          NX_PACKET *packet_ptr,
                                          NXD_ADDRESS *ip_address, UINT port);

```

### <a name="description"></a>説明

このサービスでは、確立された DTLS Session を介して、指定された IP アドレスとポートのリモート DTLS ホストにデータのパケットが送信されます。 使用されるセッションは、アクティブな DTLS Client セッションです。 IP アドレスとポートは、UDP のステートレスな性質のために提供されますが、通常は nx_secure_dtls_session_start でセッションを開始するために使用されるアドレスとポートと一致している必要があります。

パケットで提供されるデータは、*nx_secure_dtls_packet_allocate* を使用して割り当てる必要があります。このデータは、DTLS セッションの暗号化パラメーターとルーチンを使用して暗号化され、DTLS Session の UDP ソケットを介してリモート ホストに送信されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** アクティブな DTLS クライアント セッション インスタンスへのポインター。
- **packet_ptr** 以前に割り当てられ、アプリケーション データが移入された NX_PACKET インスタンスへのポインター。
- **ip_address** リモート ホストの IP アドレスが含まれている NXD_ADDRESS 構造体へのポインター。
- **port** リモート ホストの UDP ポート。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットが正常に送信されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_TCP_SEND_FAILED** (0x109) 基になる UDP の送信操作でエラーが発生しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_DTLS_SESSION client_dtls_session;

/* Trusted certificate structure and raw data. */
NX_SECURE_X509_CERT trusted_cert;
const UCHAR trusted_cert_der = { … };

/* Cryptography routines and crypto work buffers. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;
UCHAR crypto_metadata[9000];

/* Packet reassembly buffer for decryption. */
UCHAR packet_buffer[4000];

/* Remote certificate buffer for incoming certificates. */
#define REMOTE_CERT_SIZE (sizeof(NX_SECURE_X509_CERT) + 2000)
#define REMOTE_CERT_NUMBER  (3)
UCHAR remote_certs_buffer[REMOTE_CERT_SIZE * REMOTE_CERT_NUMBER];

/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL,
                                    0, NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    if(status != NX_SUCCESS)
    {
    /* Error! */
    return(status);
    }

    /* Add data to send packet as usual for NX_PACKET and send to server.  */
    status = nx_secure_dtls_session_send(&client_dtls_session, &send_packet,
                                                        &server_ip, 4443);

        /* Receive response from server. */
        status = nx_secure_dtls_session_receive(&client_dtls_session,
                                                    &receive_packet,
                                                    NX_IP_PERIODIC_RATE);

    /* Process response. */

    /* Shut down DTLS session. */
        status = nx_secure_dtls_session_end(&client_dtls_session,
                                            NX_IP_PERIODIC_RATE);

    /* Clean up. */
        status = nx_secure_dtls_session_delete(&client_dtls_session);

}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_client_session_start、nx_secure_dtls_session_receive
- nx_secure_dtls_session_create

## <a name="nx_secure_dtls_session_trusted_certificate_add"></a>nx_secure_dtls_session_trusted_certificate_add

NetX Secure DTLS Session に信頼された CA 証明書を追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_session_trusted_certificate_add(
                                         NX_SECURE_DTLS_SESSION *session_ptr,
                                         NX_SECURE_X509_CERT *certificate,
                                         UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、信頼された CA または中間 CA の X.509 証明書が DTLS Session インスタンスに追加されます。 DTLS Client では、別の認証メカニズム (事前共有キーなど) が使用されている場合を除き、リモート サーバー証明書を検証するために、少なくとも 1 つの信頼された証明書が必要です。 通常、信頼された証明書には秘密キーがありません。

cert_id パラメーターは、証明書の 0 以外の数値の識別子です。 これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。 X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

### <a name="parameters"></a>パラメーター

- **session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。
- **certificate** 以前に初期化された X.509 証明書構造体へのポインター。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS セッションに証明書が正常に追加されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_INVALID_PARAMETERS** (0x4D) 証明書 ID として 0 が渡されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

*より完全な例については、*nx_secure_dtls_session_create* のリファレンスを参照してください。

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data.
Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
   Certificates into NetX Secure” for more information. */
    nx_secure_x509_certificate_initialize(&trusted_certificate,
                                            trusted_cert_der,
                                            trusted_cert_der_len,
                                            NX_NULL, 0, NX_NULL, 0,
                                            NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the trusted store using a numeric ID. */
    nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                      &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);

    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
         &udp_socket, &server_ip, 4443,
         NX_IP_PERIODIC_RATE);


    /* Process responses, etc…*/
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_session_create、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_start
- nx_secure_dtls_session_trusted_certificate_remove
- nx_secure_x509_certificate_initialize

## <a name="nx_secure_dtls_session_trusted_certificate_remove"></a>nx_secure_dtls_session_trusted_certificate_remove

NetX Secure DTLS Session から信頼された CA 証明書を削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_dtls_session_trusted_certificate_remove(
                            NX_SECURE_DTLS_SESSION *session_ptr,
                            UCHAR *common_name,
                            UINT common_name_length, UINT cert_id);

```

### <a name="description"></a>説明

このサービスでは、証明書 ID 番号 (nx_secure_dtls_session_trusted_certificate_add を使用して証明書が追加されたときに割り当てられた) または X.509 の CommonName フィールドを使用して、DTLS Session インスタンスから信頼された CA 証明書が削除されます。

証明書の照合に common_name が使用される場合は、cert_id パラメーターを 0 に設定する必要があります。 cert_id を使用する場合は、common_name に NX_NULL を値として渡す必要があります。

cert_id パラメーターは、証明書の 0 以外の数値の識別子です。 これにより、DTLS 証明書ストアに同じ X.509 の共通名を持つ複数の ID 証明書がある場合に、証明書を簡単に削除したり、見つけたりすることができます。 X.509 証明書の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

### <a name="parameters"></a>パラメーター

- **session_ptr** 以前に作成された DTLS Session インスタンスへのポインター。
- **common_name** 照合する CommonName 文字列へのポインター。
- **common_name_length** common_name 文字列の長さ。
- **cert_id** この DTLS サーバー内のこの証明書に対する 0 以外の数値の一意の識別子。


### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DTLS セッションから証明書が正常に削除されました。
- **NX_PTR_ERROR** (0x07) 無効なポインターが渡されました。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** (0x119) 指定された DTLS セッションで cert_id または common_name に一致する証明書が見つかりませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

*より完全な例については、*nx_secure_dtls_session_create* のリファレンスを参照してください。

```C
/* Our DTLS Server instance. */
NX_SECURE_DTLS_SESSION dtls_client;

/* Certificate control block and data. Identity certificates require a private key. */
NX_SECURE_X509_CERT certificate;
UCHAR certificate_der_data[] = { … };
UCHAR certificate_key_der_data[] = { … };


/* Application thread where TLS session is started. */
void application_thread()
{
    NXD_ADDRESS server_ip;

    /* Create a TLS session for our socket. Ciphers and metadata defined
    elsewhere. See nx_secure_tls_session_create reference for more
    information. */
        status =  nx_secure_dtls_session_create(&client_dtls_session,
                                            &nx_crypto_tls_ciphers,
                                            crypto_metadata,
                                            sizeof(crypto_metadata),
                                            packet_buffer,
                                            sizeof(packet_buffer),
                                            REMOTE_CERT_NUMBER,
                                            remote_certs_buffer,
                                            sizeof(remote_certs_buffer));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_dtls_session_create: 0x%x\n", status);
    }

    /* Initialize our trusted certificate. See section “Importing X.509
    Certificates into NetX Secure” for more information. */
        nx_secure_x509_certificate_initialize(&trusted_certificate,
                                    trusted_cert_der,
                                    trusted_cert_der_len, NX_NULL, 0,
                                    NX_NULL, 0,
                                    NX_SECURE_X509_KEY_TYPE_NONE);

    /* Add the certificate to the local store using a numeric ID. */
        nx_secure_dtls_session_trusted_certificate_add(&client_dtls_session,
                                                            &certificate, 1);

    /* Initialize local server identity certificate with key and add to server. */
    status = nx_secure_x509_certificate_initialize(&certificate,
                                            certificate_der_data,
                                            sizeof(certificate_der_data),
                                            NX_NULL, 0,
                                            certificate_key_der_data,
                                            sizeof(certificate_key_der_data),
                                            NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add local server identity certificate to DTLS server with ID of 1. */
    status = nx_secure_dtls_session_local_certificate_add(&dtls_client,
                                                        &certificate, 1);

    /* Set up IP address of remote host. */
    server_ip.nxd_ip_version = NX_IP_VERSION_V4;
    server_ip.nxd_ip_address.v4 = IP_ADDRESS(192, 168, 1, 150);


    /* Now we can start the DTLS session as normal. */
    status =  nx_secure_dtls_client_session_start(&client_dtls_session,
                                        &udp_socket, &server_ip, 4443,
                                        NX_IP_PERIODIC_RATE);

    /* Process responses, etc…*/

    /* At some point in the future,
    we decide to remove the certificate using the ID of 1
    when it was added to the session. */
    status = nx_secure_dtls_session_trusted_certificate_remove(&client_dtls_session,
                                                                    NX_NULL, 0, 1);
}

```

### <a name="see-also"></a>参照

- nx_secure_dtls_session_create、nx_secure_dtls_session_receive
- nx_secure_dtls_session_send、nx_secure_dtls_session_start
- nx_secure_dtls_session_trusted_certificate_add
- nx_secure_x509_certificate_initialize
