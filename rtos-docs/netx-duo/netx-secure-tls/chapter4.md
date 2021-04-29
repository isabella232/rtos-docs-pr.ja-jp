---
title: 第 4 章 - Azure RTOS NetX Secure サービスの説明
description: この章では、すべての NetX Secure サービス （以下に記載） をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 89761ec3438b1b16c1a603764bf7d4e1eac1b4ea
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811765"
---
# <a name="chapter-4---description-of-azure-rtos-netx-secure-services"></a>第 4 章 - Azure RTOS NetX Secure サービスの説明

この章では、すべての Azure RTOS NetX Secure サービス （以下に記載） をアルファベット順に説明します。

次の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にする際に使用される **NX_SECURE_DISABLE_ERROR_CHECKING** マクロの影響を受けません。一方、太字以外の値は完全に無効になっています。

- [nx_secure_crypto_table_self_test](#nx_secure_crypto_table_self_test)
  - 暗号化メソッドで自己テストを実行します
- [nx_secure_module_hash_compute](#nx_secure_module_hash_compute)
  - user_supplied ハッシュ関数を使用してハッシュ値を計算します
- [nx_secure_tls_active_certificate_set](#nx_secure_tls_active_certificate_set)
  - NetX Secure TLS セッションに対してアクティブな ID 証明書を設定します
- [nx_secure_tls_client_psk_set](#nx_secure_tls_client_psk_set)
  - NetX Secure TLS クライアント セッションに対して事前共有キーを設定します
- [nx_secure_tls_initialize](#nx_secure_tls_initialize)
  - NetX Secure TLS モジュールを初期化します
- [nx_secure_tls_local_certificate_add](#nx_secure_tls_local_certificate_add)
  - NetX Secure TLS セッションにローカル証明書を追加します
- [nx_secure_tls_local_certificate_find](#nx_secure_tls_local_certificate_find)
  - NetX Secure TLS セッション内で共通名によってローカル証明書を検索します
- [nx_secure_tls_local_certificate_remove](#nx_secure_tls_local_certificate_remove)
  - NetX Secure TLS セッションからローカル証明書を削除します
- [nx_secure_tls_metadata_size_calculate](#nx_secure_tls_metadata_size_calculate)
  - NetX Secure TLS セッション用の暗号化メタデータのサイズを計算します
- [nx_secure_tls_packet_allocate](#nx_secure_tls_packet_allocate)
  - NetX Secure TLS セッション用のパケットを割り当てます
- [nx_secure_tls_psk_add](#nx_secure_tls_psk_add)
  - NetX Secure TLS セッションに事前共有キーを追加します
- [nx_secure_tls_remote_certificate_allocate](#nx_secure_tls_remote_certificate_allocate)
  - リモート TLS ホストによって提供された証明書用の領域を割り当てます
- [nx_secure_tls_remote_certificate_buffer_allocate](#nx_secure_tls_remote_certificate_buffer_allocate)
  - リモート TLS ホストによって提供されたすべての証明書用の領域を割り当てます
- [nx_secure_tls_remote_certificate_free_all](#nx_secure_tls_remote_certificate_free_all)
  - 受信証明書用に割り当てられた領域を解放します
- [nx_secure_tls_server_certificate_add](#nx_secure_tls_server_certificate_add)
  - 数値識別子を使用して TLS サーバー専用の証明書を追加します
- [nx_secure_tls_server_certificate_find](#nx_secure_tls_server_certificate_find)
  - 数値識別子を使用して証明書を検索します
- [nx_secure_tls_server_certificate_remove](#nx_secure_tls_server_certificate_remove)
  - 数値識別子を使用してローカル サーバー証明書を削除します
- [nx_secure_tls_session_certificate_callback_set](#nx_secure_tls_session_certificate_callback_set)
  - 追加の証明書検証に使用する TLS 用のコールバックを設定します
- [nx_secure_tls_session_client_callback_set](#nx_secure_tls_session_client_callback_set)
  - TLS クライアント ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します
- [nx_secure_tls_session_x509_client_verify_configure](#nx_secure_tls_session_x509_client_verify_configure)
  - クライアント X.509 検証を有効にし、クライアント証明書用の領域を割り当てます
- [nx_secure_tls_session_client_verify_disable](#nx_secure_tls_session_client_verify_disable)
  - NetX Secure TLS セッション用のクライアント証明書認証を無効にします
- [nx_secure_tls_session_client_verify_enable](#nx_secure_tls_session_client_verify_enable)
  - NetX Secure TLS セッション用のクライアント証明書認証を有効にします
- [nx_secure_tls_session_create](#nx_secure_tls_session_create)
  - セキュリティで保護された通信用の NetX Secure TLS セッションを作成します
- [nx_secure_tls_session_delete](#nx_secure_tls_session_delete)
  - NetX Secure TLS セッションを削除します
- [nx_secure_tls_session_end](#nx_secure_tls_session_end)
  - アクティブな NetX Secure TLS セッションを終了します
- [nx_secure_tls_session_packet_buffer_set](#nx_secure_tls_session_packet_buffer_set)
  - NetX Secure TLS セッション用のパケット再構築バッファーを設定します
- [nx_secure_tls_session_protocol_version_override](#nx_secure_tls_session_protocol_version_override)
  - NetX Secure TLS セッション用の既定の TLS プロトコル バージョンをオーバーライドします
- [nx_secure_tls_session_receive](#nx_secure_tls_session_receive)
  - NetX Secure TLS セッションからデータを受信します
- [nx_secure_tls_session_renegotiate_callback_set](#nx_secure_tls_session_renegotiate_callback_set)
  - セッションの再ネゴシエーションの開始時に呼び出されるコールバックを割り当てます
- [nx_secure_tls_session_renegotiate](#nx_secure_tls_session_renegotiate)
  - リモート ホストでセッション再ネゴシエーション ハンドシェイクを開始します
- [nx_secure_tls_session_reset](#nx_secure_tls_session_reset)
  - NetX Secure TLS セッションのクリアし、リセットします
- [nx_secure_tls_session_send](#nx_secure_tls_session_send)
  - NetX Secure TLS セッションを介してデータを送信します
- [nx_secure_tls_session_server_callback_set](#nx_secure_tls_session_server_callback_set)
  - TLS サーバー ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します
- [nx_secure_tls_session_sni_extension_parse](#nx_secure_tls_session_sni_extension_parse)
  - TLS クライアントから受信した Server Name Indication （SNI） 拡張機能を解析します
- [nx_secure_tls_session_sni_extension_set](#nx_secure_tls_session_sni_extension_set)
  - リモートサーバーに送信する Server Name Indication （SNI） 拡張機能の DNS 名を設定します
- [nx_secure_tls_session_start](#nx_secure_tls_session_start)
  - NetX Secure TLS セッションを開始します
- [nx_secure_tls_session_time_function_set](#nx_secure_tls_session_time_function_set)
  - NetX Secure TLS セッションにタイムスタンプ関数を割り当てます
- [nx_secure_tls_trusted_certificate_add](#nx_secure_tls_trusted_certificate_add)
  - 信頼された証明書を NetX Secure TLS セッションに追加します
- [nx_secure_tls_trusted_certificate_remove](#nx_secure_tls_trusted_certificate_remove)
  - 信頼された証明書を NetX Secure TLS セッションから削除します
- [nx_secure_x509_certificate_initialize](#nx_secure_x509_certificate_initialize)
  - NetX Secure TLS 用の X.509 証明書を初期化します
- [nx_secure_x509_common_name_dns_check](#nx_secure_x509_common_name_dns_check)
  - DNS 名を X.509 証明書と照合して確認します
- [nx_secure_x509_crl_revocation_check](#nx_secure_x509_crl_revocation_check)
  - X.509 証明書を指定された証明書失効リスト （CRL） と照合して確認します
- [nx_secure_x509_dns_name_initialize](#nx_secure_x509_dns_name_initialize)
  - X.509 DNS 名の構造体を初期化します
- [nx_secure_x509_extended_key_usage_extension_parse](#nx_secure_x509_extended_key_usage_extension_parse)
  - X.509 証明書内で X.509 拡張キー使用拡張機能を検索して解析します
- [nx_secure_x509_extension_find](#nx_secure_x509_extension_find)
  - X.509 証明書内で X.509 拡張機能を検索して返します
- [nx_secure_x509_key_usage_extension_parse](#nx_secure_x509_key_usage_extension_parse)
  - X.509 証明書内で X.509 キー使用法拡張機能を検索して解析します

## <a name="nx_secure_crypto_table_self_test"></a>nx_secure_crypto_table_self_test

暗号化メソッドで自己テストを実行します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_crypto_table_self_test(
                                  const NX_SECURE_TLS_CRYPTO *crypto_table,
                                  VOID *metadata, UINT metadata_size);
```

### <a name="description"></a>説明

このサービスは、検証する暗号化メソッドの自己テストを実行します。 自己テストは、シンボル NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK が定義された状態で、NetX Secure ライブラリが構築されている場合にのみ使用できます。

自己テストは、サポートされている暗号化メソッドごとに、事前定義された入力データを提供し、出力が、その事前定義された期待値と一致することを確認します。

NetX Secure 暗号化自己テストは、次のアルゴリズムとキー サイズをサポートしています。

- DES: 暗号化と解読
- Triple DES （3DES）: 暗号化と解読
- AES: CBC モードおよびカウンター モードでの 128 ビット、192 ビット、256 ビットのキー サイズ、暗号化と解読。
- HMAC-MD5: 認証とハッシュ計算
- HMAC-SHA: SHA1-96、SHA1-160、SHA2-256、SHA2-384、SHA2- 512、認証とハッシュ計算
- MD5: 認証
- 擬似乱数関数 （PRF）: PRF_HMAC_SHA1 および PRF_HMAC_SHA2-256
- RSA: 1024 ビット、2048 ビット、4096 ビットの RSA 累乗剰余演算
- SHA: SHA1 （96 ビットおよび 160 ビット）、SHA2 （256 ビット、384 ビット、512 ビット） 認証

この関数には、上に示した暗号アルゴリズム用の組み込みベクターがあります。 ただし、テスト対象は、この関数に渡される *cipher_table* 内に示されているものだけです。 たとえば、暗号スイート TLS_RSA_WITH_AES_128_CBC_SHA のみが使用される TLS セッションの場合、この関数は、RSA （1024 ビット、2048 ビット、4096 ビット）、AES-CBC （128 ビット）、および SHA1 上で自己テストを実行します。

### <a name="parameters"></a>パラメーター

- **crypto_table** TLS セッションによって使用されている暗号化テーブルへのポインター。 これは **_nx_secure_tls_session_create （）_** 呼び出しに渡される crypto_table と同じです。
- **metadata** 暗号メタデータ領域用のスペースへのポインター。 .
- **metadata_size** メタデータ バッファーのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SECURE_TLS_SUCCESS** （0x00） 指定された暗号化メソッドを正常にテストしました。
- **NX_PTR_ERROR** （0x07） 無効な暗号化メソッド構造体
- **NX_NOT_SUCCESSFUL** （0x43） 暗号化自己テストに失敗しました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* crypto_tls_ciphers is the cipher table for the TLS session. */
/* metadata_buffer is the memory area used by the cipher functions. */

/* The following function verifies the supplied ciphersuties using the built-in
   self test. */

if (nx_secure_crypto_table_self_test(&crypto_tls_ciphers, metadata_buffer,
    sizeof(metadata_buffer)))
{
    printf("Crypto self test failed!\r\n");
    exit(0);
}
else
{
    printf("Crypto self test succeed!\r\n");
}

/* Now the ciphersuites are successfully test, it can be used in
   nx_secure_tls_session_create() */
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

user-supplied ハッシュ関数を使用してハッシュ値を計算します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_secure_module_hash_compute(
                      NX_CRYPTO_METHOD *hamc_ptr,
                      UINT start_address, UINT end_address,
                      UCHAR *key, UINT key_length,
                      VOID *metadata, UINT metadata_size,
                      UCHAR *output_buffer, UINT output_buffer_size,
                      UINT *actual_size);
```

### <a name="description"></a>説明

この関数は、指定された HMAC 暗号化メソッドとキー文字列を使用して、指定されたメモリ領域内のデータ ストリームのハッシュ値を計算します。 モジュール ハッシュ計算関数は、シンボル NX_SECURE_POWER_ON_SELF_TEST_MODULE_INTEGRITY_CHECK が定義された状態で、NetX Secure ライブラリが構築されている場合にのみ使用できます

### <a name="parameters"></a>パラメーター

- **hmac_ptr** ハッシュ値の計算に使用されている HMAC 暗号化メソッドへのポインター。
- **start_address** データ バッファーの開始アドレス
- **end_address** データ バッファーの終了アドレス。 ハッシュ計算は、この end_address のデータに対応していないことに注意してください。
- **key** HMAC 計算内で使用されているキー文字列。
- **key_length** キー文字列のサイズ （バイト単位）
- **metadata** HMAC アルゴリズムによって使用されている領域へのポインター。
- **metadata_size** メタデータ バッファーのサイズ。
- **output_buffer** ハッシュ出力が格納されているメモリ位置。
- **output_buffer_size** 出力バッファーの使用可能な領域 （バイト単位）
- **actual_size** output_buffer に書き込まれている実際のバイト数を示す関数によって返されます。

### <a name="return-values"></a>戻り値

- **0** ハッシュ値が正常に計算されました。
- **1** ハッシュ計算が失敗しました。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Define the HMAC SHA256 method */
NX_CRYPTO_METHOD hmac_sha256 =
{
    NX_CRYPTO_AUTHENTICATION_HMAC_SHA2_256,    /* HMAC SHA256 algorithm  */
    0,                                         /* Key size, not used     */
    0,                                         /* IV size, not used      */
    NX_CRYPTO_HMAC_SHA256_ICV_FULL_LEN_IN_BITS,/* Transmitted ICV size   */
    NX_CRYPTO_SHA2_BLOCK_SIZE_IN_BYTES,        /* Block size in bytes    */
    sizeof(NX_CRYPTO_SHA256_HMAC),             /* Metadata size in bytes */
    _nx_crypto_method_hmac_sha256_init,        /* HMAC SHA256 init       */
    _nx_crypto_method_hmac_sha256_cleanup,     /* HMAC SHA256 cleanup    */
    _nx_crypto_method_hmac_sha256_operation    /* HMAC SHA256 operation  */
};

/* Define the hash key being used. */
const CHAR hash_key = “my hash key”;

/* Define starting address. */
UINT starting_address = 0x10000;

/* Define the ending address.
   Note that the hash computation covers the memory location
   before the ending address. */
UINT ending_address = 0x11000;

/* Declare the output buffer. */
#define OUTPUT_BUFFER_SIZE
UCHAR output_buffer[OUTPUT_BUFFER_SIZE];

UINT actual_size;

/* Declare 1K bytes of metadata buffer area. */
UCHAR metadata_buffer[1024];

/* Compute the hash value of the data between 0x10000 – 0x10FFF */
nx_secure_module_hash_compute(&hmac_sha256,
                              starting_address, ending_address,
                              hash_key, strlen(hash_key),
                              metadata_buffer, sizeof(metadata_buffer),
                              output_buffer, OUTPUT_BUFFER_SIZE, &actual_size);

/* If this function returns “0”, the hash value has been computed and is stored
   in output_buffer. */
```

### <a name="see-also"></a>参照

- nx_secure_crypto_method_self_test

## <a name="nx_secure_tls_active_certificate_set"></a>nx_secure_tls_active_certificate_set

NetX Secure TLS セッションに対してアクティブな ID 証明書を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_active_certificate_set(
                   NX_SECURE_TLS_SESSION *tls_session,
                   NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>説明

このサービスは、セッション コールバック内から呼び出されるように意図されています （nx_secure_tls_session_client_callback_set　および　nx_secure_tls_session_server_callback_set　をご覧ください）。 前に初期化された NX_SECURE_X509_CERT 構造体を使って呼び出されたときは、既定の ID 証明書ではなく、その証明書が使用されます。 ほとんどの場合、証明書はローカル ストアに追加されている必要があります （nx_secure_tls_local_certificate_add をご覧ください）。そうでない場合、TLS ハンドシェイクは失敗する可能性があります。

このサービスは、TLS が複数の ID 証明書をサポートできるようにすることを目的としています。 これは、複数のネットワーク アドレスにサービスを提供する TLS サーバーにとって便利な機能で、サーバーは、クライアントのエントリポイントに応じて、適切な証明書を選択してリモート クライアントに提供することができます。 TLS クライアントの場合は、サーバーが TLS ハンドシェイク内で自身を特定した後に、このルーチンを使用して、実行時にリモート サーバーに送信された証明書を変更できます （これは TLS サーバーの使用例よりもまれです）。

複数の証明書が同じ X.509 識別名を共有している可能性がある場合は、nx_secure_tls_server_certificate_add を使用して、証明書を追加する必要があります。これにより、証明書とは別に数値の識別子が導入されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** セッション コールバックに渡される TLS セッション インスタンスへのポインター。
- **certificate** 現在のセッションに使用される初期化済み X.509 証明書へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） セッションへの証明書の割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define TLS_SNI_SERVER_NAME “www.example.com”
#define TLS_DEFAULT_SERVER_CERT_ID 2
#define TLS_EXAMPLE_CERT_ID 3


/* Callback for ClientHello extensions processing. */
static ULONG tls_server_callback(NX_SECURE_TLS_SESSION *tls_session,
                                 NX_SECURE_TLS_HELLO_EXTENSION *extensions,
                                 UINT num_extensions)
{
NX_SECURE_X509_DNS_NAME dns_name;
INT compare_value;
UINT status;
NX_SECURE_X509_CERT *cert_ptr;

    /* Grab a pointer to our default certificate in case the SNI extension is not
       available or the specified server name is unknown. */
    nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                     TLS_DEFAULT_SERVER_CERT_ID);


    /* Process Server Name Indication extension. */
    status = _nx_secure_tls_session_sni_extension_parse(tls_session, extensions,
                                                    num_extensions, &dns_name);

    /* If no extension found, that is OK. Use default certificate. */
    if(status == NX_SUCCESS)
    {
          /* SNI extension found, select an active certificate based on the server
             name. */

          /* Make sure our SNI name matches. */
          compare_value = memcmp(dns_name.nx_secure_x509_dns_name,
                                TLS_SNI_SERVER_NAME, strlen(TLS_SNI_SERVER_NAME));

          if(compare_value == 0 && dns_name.nx_secure_x509_dns_name_length !=
             strlen(TLS_SNI_SERVER_NAME))
          {
             /* Found a match, find the certificate we want to use. */
             _nx_secure_tls_server_certificate_find(tls_session, &cert_ptr,
                                                      TLS_EXAMPLE_CERT_ID);
          }
          else
          {
             /* No matching server name found. The application may choose to simply
                provide the default certificate (and probably resulting in an error
                in the remote client) or returning an error here to end the
                handshake. A user-defined non-zero error code will be sufficient –
                the error code will abort the TLS handshake and be returned to the
                caller that started the server. */
                return(0x500);
          }
      }
      else
      {
      }
      /* Set the certificate we want to use. */
      nx_secure_tls_active_certificate_set(tls_session, cert_ptr);

      /* Return success to continue TLS handshake. */
      return(NX_SUCCESS);
}

/* Sockets, sessions, certificates defined in global static space to preserve
   application stack. */
NX_SECURE_TLS_SESSION server_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&server_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));

    /* Check for error.  */
    if(status)
    {
        printf("Error in function nx_secure_tls_session_create: 0x%x\n", status);
    }

    /* Setup our packet reassembly buffer. See
       nx_secure_tls_session_packet_buffer_set for more information. */
    nx_secure_tls_session_packet_buffer_set(&server_tls_session,
                                      server_packet_buffer,
                                      sizeof(server_packet_buffer));


    /* Set callback for server TLS extension handling. */
    _nx_secure_tls_session_server_callback_set(&server_tls_session,
                                              tls_server_callback);

    /* Initialize our certificates – certificate data defined elsewhere. See
       section “Importing X.509 Certificates into NetX Secure” for more
       information. */
    nx_secure_x509_certificate_initialize(&default_certificate,
                                      default_cert_der,
                                      default _cert_der_len, NX_NULL, 0,
                                      default_cert_key_der,
                                      default_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &default_certificate,
                                         TLS_DEFAULT_SERVER_CERT_ID);

    /* Alternative identity certificate, needs to have a private key! */
    nx_secure_x509_certificate_initialize(&example_certificate,
                                      example_cert_der,
                                      example cert_der_len, NX_NULL, 0,
                                      example_cert_key_der,
                                      example_cert_key_der_len,
                                      NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);

    /* Add the certificate to the local store using a numeric ID. */
    nx_secure_tls_server_certificate_add(&server_tls_session,
                                         &example_certificate,
                                         TLS_EXAMPLE_CERT_ID);

    /* Now we can start the TLS session as normal. */
       …
}
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_client_psk_set"></a>nx_secure_tls_client_psk_set

NetX Secure TLS クライアント セッションに対して事前共有キーを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_client_psk_set(NX_SECURE_TLS_SESSION *session_ptr,
                              UCHAR *pre_shared_key, UINT psk_length,
                              UCHAR *psk_identity, UINT identity_length,
                              UCHAR *hint, UINT hint_length);
```

### <a name="description"></a>説明

このサービスは、事前共有キー （PSK）、その ID文字列、および ID ヒントを TLS セッション制御ブロックに追加し、その PSK が、それ以降の TLS クライアント接続内で使用されるように設定します。 PSK 暗号スイートが有効で、使用されている場合、PSK はデジタル証明書の代わりに使用されます。

この場合、PSK は、TLS クライアントが通信する特定のリモート TLS サーバーに関連付けられています。 この API を使用して設定された PSK は、次の TLS ハンドシェイク中にリモート TLS サーバー ホストに提供されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **pre_shared_key** 実際の PSK 値。
- **psk_length** PSK 値の長さ。
- **psk_identity** この PSK 値を識別するために使用される文字列。
- **identity_length** PSK ID の長さ。
- **hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。
- **hint_length** ヒントの文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） PSK の追加に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** （0x125） 別の PSK を追加できません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_client_psk_set(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_secure_tls_psk_add
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_initialize"></a>nx_secure_tls_initialize

NetX Secure TLS モジュールを初期化します

### <a name="prototype"></a>プロトタイプ

```C
VOID nx_secure_tls_initialize(VOID);
```

### <a name="description"></a>説明

このサービスは、NetX Secure TLS モジュールを初期化します。 これは、他の NetX Secure サービスにアクセスする前に呼び出す必要があります。

### <a name="parameters"></a>パラメーター

None

### <a name="return-values"></a>戻り値

None

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create

## <a name="nx_secure_tls_local_certificate_add"></a>nx_secure_tls_local_certificate_add

NetX Secure TLS セッションにローカル証明書を追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_local_certificate_add(
              NX_SECURE_TLS_SESSION *session_ptr,
              NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>説明

このサービスは、初期化された NX_SECURE_X509_CERT 構造体インスタンスを、TLS セッションのローカル ストアに追加します。 この証明書は、TLS ハンドシェイク中、TLS スタックがデバイスを識別するために使用できます （nx_secure_x509_certificate_initialize を使用して証明書構造体を初期化中、ID 証明書としてマークされた場合）。または、発行者として、TLS ハンドシェイク中にリモート ホストに提供される証明書チェーンの一部として使用できます。

同じ共通名を持つ複数のローカル証明書が必要な場合は、*nx_secure_tls_server_certificate_add* サービスを使用して証明書を追加できます （以下の警告をご覧ください）。

TLS サーバー モードに証明書が **必要** です。

TLS クライアント モードの場合、証明書は 「*省略可能*」 です。

> [!IMPORTANT]
> *nx_secure_tls_server_certificate_add を使用する場合、この API は、同じ TLS セッションで使用しないでください。サーバー証明書 API は、証明書ごとに一意の数値識別子を使用し、nx_secure_tls_local_certificate_add は、X.509 共通名に基づいてインデックスを作成します。ローカル証明書サービスは、単一の ID 証明書のみを使用するアプリケーションに対して、数値識別子に代わる便利な手段を提供します。共通名を使用すると、アプリケーションは数値識別子を追跡する必要がありません。*

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certificate_ptr** 初期化された TLS 証明書インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の追加に成功。
- **NX_INVALID_PARAMETERS** （0x4D） 無効または重複する証明書を追加しようとしました。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_find

## <a name="nx_secure_tls_local_certificate_find"></a>nx_secure_tls_local_certificate_find

NetX Secure TLS セッション内で共通名によってローカル証明書を検索します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_local_certificate_find(NX_SECURE_TLS_SESSION
                        *session_ptr, NX_SECURE_X509_CERT
                        **certificate, UCHAR *common_name, UINT
                        name_length);
```

### <a name="description"></a>説明

このサービスは、TLS セッションのローカル デバイス証明書ストア内の証明書を検索し、ストア内の NX_SECURE_X509_CERT 構造体へのポインターを返します。 common_name パラメーターとその長さ （name_length） は、証明書の X.509 サブジェクト共通名フィールドを照合することで、ストア内の証明書を識別するために使用されます。

同じ共通名の証明書が複数存在する場合は、最初のものだけが返されます。代わりに *nx_secure_tls_server_certificate_find* を使用してください。

> [!IMPORTANT]
> *nx_secure_tls_server_certificate_add を使用する場合、この API は、同じ TLS セッションで使用しないでください。サーバー証明書 API は、証明書ごとに一意の数値識別子を使用し、nx_secure_tls_local_certificate_add は、X.509 共通名に基づいてインデックスを作成します。ローカル証明書サービスは、単一の ID 証明書のみを使用するアプリケーションに対して、数値識別子に代わる便利な手段を提供します。共通名を使用すると、アプリケーションは数値識別子を追跡する必要がありません。*

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certificate** 一致した証明書へのポインターを返します。
- **common_name** 一致する共通名の文字列 （DNS 名）。
- **name_length** common_name 文字列データの長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書が見つかり、「certificate」 パラメーター内でポインターが返されました。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 指定された共通名の証明書が見つかりませんでした。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション、証明書ポインター、または共通名の文字列。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_SECURE_X509_CERT *certificate_ptr;

/* Initialize certificate structure. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */

status = nx_secure_tls_local_certificate_find(&tls_session, &certificate_ptr,
                                      “common name”, strlen(“common name”));

/* If status is NX_SUCCESS the variable “certificate_ptr” points to a certificate
   structure containing a certificate with the Common Name “common name”. */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_remove
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_local_certificate_remove"></a>nx_secure_tls_local_certificate_remove

NetX Secure TLS セッションからローカル証明書を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_local_certificate_remove(NX_SECURE_TLS_SESSION
                  *session_ptr, UCHAR *common_name, UINT
                  common_name_length);
```

### <a name="description"></a>説明

このサービスは、証明書内の共通名フィールドをキーとして、TLS セッションからローカル証明書インスタンスを削除します。

> [!IMPORTANT]
> *nx_secure_tls_server_certificate_add を使用する場合、この API は、同じ TLS セッションで使用しないでください。サーバー証明書 API は、証明書ごとに一意の数値識別子を使用し、nx_secure_tls_local_certificate_add は、X.509 共通名に基づいてインデックスを作成します。ローカル証明書サービスは、単一の ID 証明書のみを使用するアプリケーションに対して、数値識別子に代わる便利な手段を提供します。共通名を使用すると、アプリケーションは数値識別子を追跡する必要がありません。*

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **common_name** 削除する証明書の共通名の値。
- **common_name_length** 共通名の文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の追加に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 証明書が見つかりませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Add certificate to TLS session.  */
status =  nx_secure_tls_local_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_metadata_size_calculate"></a>nx_secure_tls_metadata_size_calculate

NetX Secure TLS セッション用の暗号化メタデータのサイズを計算します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_metadata_size_calculate(
                        const NX_SECURE_TLS_CRYPTO *crypto_table,
                        ULONG *metadata_size);
```

### <a name="description"></a>説明

このサービスは、特定の TLS セッションおよび TLS 暗号テーブルに必要な暗号化メタデータのサイズを計算し、返します （暗号化テーブルの詳細については、暗号化メソッドを使用した TLS の初期化に関するセクションをご覧ください）。

このサービスは、nx_secure_tls_session_create に渡されるメタデータ バッファーのサイズを計算する際に、必要な暗号化テーブルを使用して呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **crypto_table** 完全な NetX Secure TLS 暗号テーブルへのポインター。
- **metadata_size** サイズ計算の出力 （バイト単位）。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） メタデータ サイズの計算に成功。
- **NX_PTR_ERROR** （0x07） 無効な暗号化テーブルまたは戻り値のサイズのポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Pointer to the platform-specific cipher table. */
extern nx_crypto_tls_ciphers;

/* Return variable for metadata size. */
ULONG crypto_metadata_size;

/* Calculate metadata size.  */
status =  nx_secure_tls_metadata_size_calculate(&nx_crypto_tls_ciphers,
                                                &crypto_metadata_size);


/* If status is NX_SUCCESS then crypto_metadata_size contains the size of the
   metadata buffer for the table nx_crypto_tls_ciphers.  */
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create

## <a name="nx_secure_module_hash_compute"></a>nx_secure_module_hash_compute

NetX Secure ライブラリ ルーチンのハッシュ値を計算します

### <a name="prototype"></a>プロトタイプ

```C
VOID nx_secure_module_hash_compute(VOID);
```

### <a name="description"></a>説明

このサービスは、NetX Secure TLS モジュールを初期化します。 これは、他の NetX Secure サービスにアクセスする前に呼び出す必要があります。

### <a name="parameters"></a>パラメーター

None

### <a name="return-values"></a>戻り値

None

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Initializes the TLS module. */
Nx_secure_tls_initialize();
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create

## <a name="nx_secure_tls_packet_allocate"></a>nx_secure_tls_packet_allocate

NetX Secure TLS セッション用のパケットを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_packet_allocate(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET_POOL *pool_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、指定された NX_PACKET_POOL から、指定されたアクティブな TLS セッション用に NX_PACKET を割り当てます。 このサービスは、TLS 接続を介して送信されるデータ パケットを割り当てる際に、アプリケーションによって呼び出される必要があります。 TLS セッションは、このサービスが呼び出される前に初期化される必要があります。

割り当てられたパケットは適切に初期化されるため、パケット データが入力された後、TLS ヘッダーとフッターのデータが追加される可能性があります。 それ以外の動作は、*nx_packet_allocate* と同じです。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **pool_ptr** パケットの割り当て元となる NX_PACKET_POOL へのポインター。
- **packet_ptr** 新しく割り当てられたパケットへの出力ポインター。
- **wait_option** パケット割り当ての中断オプション。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） パケットの割り当てに成功。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 基になるパケットの割り当てに失敗しました。
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Allocate a new TLS packet from the previously created packet pool and
previously initialized TLS session.   */

status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &packet_ptr,
                                       NX_WAIT_FOREVER);

/* If status is NX_SUCCESS, the newly allocated packet pointer is found in the
variable packet_ptr.  */
```

### <a name="see-also"></a>参照

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_psk_add"></a>nx_secure_tls_psk_add

NetX Secure TLS セッションに事前共有キーを追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_psk_add(NX_SECURE_TLS_SESSION *session_ptr,
                            UCHAR *pre_shared_key, UINT psk_length,
                            UCHAR *psk_identity, UINT
                            identity_length, UCHAR *hint, UINT
                            hint_length);
```

### <a name="description"></a>説明

このサービスは、事前共有キー （PSK）、その ID 文字列、および ID ヒントを TLS セッション制御ブロックに追加します。 PSK 暗号スイートが有効で、使用されている場合、PSK はデジタル証明書の代わりに使用されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **pre_shared_key** 実際の PSK 値。
- **psk_length** PSK 値の長さ。
- **psk_identity** この PSK 値を識別するために使用される文字列。
- **identity_length** PSK ID の長さ。
- **hint** TLS サーバー上のどの PSK グループから選択するかを示すために使用される文字列。
- **hint_length** ヒントの文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） PSK の追加に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_SECURE_TLS_NO_MORE_PSK_SPACE** （0x125） 別の PSK を追加できません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* PSK value.  */
UCHAR psk[] = { 0x1a, 0x2b, 0x3c, 0x4d };

/* Add PSK to TLS session.  */
status =  nx_secure_tls_psk_add(&tls_session, psk, sizeof(psk), “psk_1”, 4,
“Client_identity”, 15);


/* If status is NX_SUCCESS the PSK was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_secure_tls_client_psk_set
- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_local_certificate_add

## <a name="nx_secure_tls_remote_certificate_allocate"></a>nx_secure_tls_remote_certificate_allocate

リモート TLS ホストによって提供された証明書用の領域を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_remote_certificate_allocate(
                 NX_SECURE_TLS_SESSION *session_ptr,
                 NX_SECURE_X509_CERT *certificate_ptr,
                 UCHAR *raw_certificate_buffer,
                 UINT raw_buffer_size);
```

### <a name="description"></a>説明

このサービスは、TLS セッション中にリモート ホストによって提供される証明書の領域を割り当てる目的で、初期化されていない NX_SECURE_X509_CERT 構造体インスタンスを TLS セッションに追加します。 リモート証明書のデータは NetX Secure TLS によって解析され、その情報を使用して、この関数に提供される証明書構造体のインスタンスが設定されます。 この方法で追加された証明書は、リンク リストに配置されます。

リモート ホストが複数の証明書を提供することが予想される場合は、この関数を繰り返し呼び出して、すべての証明書の領域を割り当てる必要があります。 追加の証明書は、証明書のリンク リストの最後に追加されます。

リモート証明書の割り当てに失敗すると、事前共有キー （PSK） 暗号スイートが使用されていない限り、TLS ハンドシェイク中に TLS クライアント モードが失敗します。

*raw_certificate_buffer* パラメーターは、受信リモート証明書を格納するために割り当てられた領域を指します。 署名に SHA-256 を使用する 2048 ビットの RSA キーを持つ一般的な証明書の範囲は、1000 バイトから 2000 バイトです。 バッファーは、少なくともそのサイズを保持できるだけの大きさが必要ですが、リモート ホスト証明書によっては、大幅に小さい、または大きいことがあります。 バッファーが小さすぎて受信証明書を保持できない場合、TLS ハンドシェイクはエラーで終了します。

TLS サーバー モードの場合、クライアント証明書の認証が有効になっている場合にのみ、リモート証明書の割り当てが必要です。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certificate_ptr** 初期化されていない X.509 証明書インスタンスへのポインター。
- **raw_certificate_buffer** リモート ホストから受信した解析されていない証明書を保持するバッファーへのポインター。
- **buffer_size** 生の証明書バッファーのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** （0x12D） 指定されたバッファーが小さすぎました。
- **NX_INVALID_PARAMETERS** （0x4D） 無効な証明書を追加しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_buffer_allocate"></a>nx_secure_tls_remote_certificate_buffer_allocate

リモート TLS ホストによって提供されたすべての証明書用の領域を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_remote_certificate_buffer_allocate(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>説明

このサービスは、TLS クライアント インスタンス内で X.509 認証と検証を実行するために、リモート サーバー ホストからの受信証明書チェーンを処理する目的で領域を割り当てます。 TLS サーバー モードの場合、クライアントの X.509 証明書の認証が有効になっている場合にのみ、リモート証明書の割り当てが必要です。TLS サーバー インスタンスについては、サービス *nx_secure_tls_session_x509_client_verify_configure* を代わりに使用する必要があります。

リモート証明書の割り当てに失敗すると、事前共有キー （PSK） 暗号スイートが使用されていない限り、TLS ハンドシェイク中に TLS クライアントモードが失敗します。

*certificate_buffer* パラメーターは、受信リモート証明書とそれらの証明書に必要な制御ブロックを格納するために割り当てられた領域を指します。 バッファーは、証明書の数 （*certs_number*） で除算され、各証明書に均等に指定されます。 *Buffer_size* パラメーターは、バッファーのサイズを示します。 必要な領域を見つけるには、次の数式を使用します。

```C
buffer_size = (<expected max number of certificates in chain>) *
                 (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

署名に SHA-256 を使用する 2048 ビットの RSA キーを持つ一般的な証明書の範囲は、1000 バイトから 2000 バイトです。 バッファーは、証明書ごとに少なくともそのサイズを保持できるだけの大きさが必要ですが、リモート ホスト証明書によっては、大幅に小さい、または大きいことがあります。 バッファーが小さすぎて受信証明書を保持できない場合、TLS ハンドシェイクはエラーで終了します。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certs_number** 指定されたバッファーから割り当てる証明書の数。
- **certificate_buffer** リモート ホストから受信した証明書を保持するバッファーへのポインター。
- **buffer_size** 証明書バッファーのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッションまたはバッファー ポインター。
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** （0x12D） 指定されたバッファーが小さすぎました。
- **NX_INVALID_PARAMETERS** （0x4D） バッファーが小さすぎて、必要な数の証明書を保持できませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE           (CERTIFICATE_NUMBER * \
                              (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_buffer_allocate(&tls_session,
                                                      CERTIFICATE_NUMBER,
                                                      certificate_buffer,
                                                      BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create

## <a name="nx_secure_tls_remote_certificate_free_all"></a>nx_secure_tls_remote_certificate_free_all

受信証明書用に割り当てられた領域を解放します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_remote_certificate_free_all(
                  NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、nx_secure_tls_remote_certificate_allocated によって特定の TLS セッションに割り当てられたすべての証明書バッファーを、そのセッションの空き証明書領域に返すことによって解放できます。 これは、アプリケーションが、nx_secure_tls_session_delete と nx_secure_tls_session_create を使って TLS セッション オブジェクトを削除および再作成せずに、再利用する場合に必要になることがあります。

nx_secure_tls_session_end の場合のように、リモート証明書スペースは、TLS セッションがリセットされるときに自動的に復旧されるため、ほとんどのアプリケーションは、このサービスを呼び出す必要がありません。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 操作に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_INVALID_PARAMETERS** （0x4D） 内部エラー - 証明書ストアが壊れている可能性があります。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;

/* Buffer space to hold the incoming certificate. */
UCHAR certificate_buffer[2000];

/* Add certificate to TLS session.  */
status =  nx_secure_tls_remote_certificate_allocate(&tls_session, &certificate,
                                                    certificate_buffer,
                                                    sizeof(certificate_buffer));


/* If status is NX_SUCCESS the certificate was successfully allocated.  */

/* … TLS session setup, TCP connection, etc… */

/* End TLS session. */
nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);

/* Free up certificate buffers for next connection. */
nx_secure_tls_remote_certificate_free_all(&tls_session);
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_end

## <a name="nx_secure_tls_server_certificate_add"></a>nx_secure_tls_server_certificate_add

数値識別子を使用して TLS サーバー専用の証明書を追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_server_certificate_add(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT *certificate, UINT cert_id);
```

### <a name="description"></a>説明

このサービスを使用すると、証明書内で X.509 サブジェクト （共通名） を使用してストアにインデックスを作成するのではなく、数値識別子を使用して、証明書を TLS セッションのローカル ストアに追加できます （nx_secure_tls_local_certificate_add をご覧ください）。 数値識別子は証明書とは別のもので、これにより複数の証明書を ID 証明書として TLS サーバーに追加したり、同じ共通名を持つ複数の証明書を、同じ TLS セッション ローカル ストアに追加したりできます。 この同じサービスをクライアント証明書に使用することもできますが、TLS クライアントが複数の ID 証明書を持つことはめったにありません。

cert_id パラメーターは、アプリケーションによって割り当てられる 0 以外の正の整数です。 実際の値は重要ではありませんが （0 以外）、指定された TLS セッションに対するストア内で一意である必要があります。 cert_id 値を使用すると、nx_secure_tls_server_certificate_find と nx_secure_tls_server_certificate_remove を使用して、ローカル ストアから証明書を検索し、削除することができます。

> [!IMPORTANT]
> *nx_secure_tls_local_certificate_add を使用している場合、この API を同じ TLS セッションで使用することはできません。nx_secure_tls_server_certificate_add API は、証明書ごとに一意の数値識別子と、X.509 共通名に基づくローカル証明書サービス インデックスを使用します。サーバー証明書サービスを使用すると、共有データ （特に共通名） を持つ複数の証明書を同じローカル ストアに存在させることができます。これは、複数の ID を持つサーバーに便利です。*

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certificate** 前に初期化された X.509 証明書インスタンスへのポインター。
- **cert_id** 0 以外の正で比較的一意の証明書 ID 番号。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 操作に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。
- **NX_SECURE_TLS_CERT_ID_INVALID** （0x138） 指定された証明書 ID に無効な値が含まれています （0 の可能性があります）。
- **NX_SECURE_TLS_CERT_ID_DUPLICATE** （0x139） 指定された証明書 ID は既にローカル ストアに存在しています。
- **NX_INVALID_PARAMETERS** （0x4D） 内部エラー - 証明書ストアが壊れている可能性があります。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully added with the ID
0x12.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_find
- nx_secure_tls_server_certificate_remove

## <a name="nx_secure_tls_server_certificate_find"></a>nx_secure_tls_server_certificate_find

数値識別子を使用して証明書を検索します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_server_certificate_find(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  NX_SECURE_X509_CERT **certificate, UINT cert_id);
```

### <a name="description"></a>説明

このサービスを使用すると、証明書内で X.509 サブジェクト （共通名） を使用してストアにインデックスを作成するのではなく、数値識別子を使用して、証明書を TLS セッションのローカル ストア内で検索できます （nx_secure_tls_local_certificate_add をご覧ください）。

cert_id パラメーターは、nx_secure_tls_server_certificate_add を使用して証明書が TLS セッション ローカル ストアに追加されるときに、アプリケーションによって割り当てられる 0 以外の正の整数です。

> [!IMPORTANT]
> *nx_secure_tls_local_certificate_add を使用している場合、この API を同じ TLS セッションで使用することはできません。nx_secure_tls_server_certificate_add API は、証明書ごとに一意の数値識別子と、X.509 共通名に基づくローカル証明書サービス インデックスを使用します。サーバー証明書サービスを使用すると、共有データ （特に共通名） を持つ複数の証明書を同じローカル ストアに存在させることができます。これは、複数の ID を持つサーバーに便利です。*

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certificate** 見つかった証明書への参照を返す X.509 証明書ポインターへのポインター。
- **cert_id** 0 以外の正の証明書 ID 値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 操作に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッションまたは証明書ポインター。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 指定された証明書 ID が、指定された TLS セッションのローカル ストア内のいずれとも一致しませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_SECURE_X509_CERT *certificate;


/* Find certificate in TLS session.  */
status =  nx_secure_tls_server_certificate_find(&tls_session, &certificate, 0x12);


/* If status is NX_SUCCESS the certificate was successfully found and a reference
returned in the certificate parameter.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_remove

##  <a name="nx_secure_tls_server_certificate_remove"></a>nx_secure_tls_server_certificate_remove

数値識別子を使用してローカル サーバー証明書を削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_server_certificate_remove(
                  NX_SECURE_TLS_SESSION *session_ptr, UINT cert_id);
```

### <a name="description"></a>説明

このサービスを使用すると、証明書内で X.509 サブジェクト （共通名） を使用してストアにインデックスを作成するのではなく、数値識別子を使用して、証明書を TLS セッションのローカル ストアから削除できます （nx_secure_tls_local_certificate_add をご覧ください）。

cert_id パラメーターは、nx_secure_tls_server_certificate_add を使用して証明書が TLS セッション ローカル ストアに追加されるときに、アプリケーションによって割り当てられる 0 以外の正の整数です。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **cert_id** 0 以外の正の証明書 ID 値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 操作に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 指定された証明書 ID が、指定された TLS セッションのローカル ストア内のいずれとも一致しませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Certificate control block. */
NX_SECURE_X509_CERT certificate;


/* Add certificate to TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_add(&tls_session, &certificate, 0x12);
/* Use certificate in TLS session, etc… */

/* Remove certificate from TLS session with id 0x12.  */
status =  nx_secure_tls_server_certificate_remove(&tls_session, 0x12);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_local_certificate_add
- nx_secure_tls_active_certificate_set
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_alert_value_get"></a>nx_secure_tls_session_alert_value_get

リモート ホストによって送信された TLS アラートの値とレベルを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_alert_value_get(
                   NX_SECURE_TLS_SESSION *session_ptr,
                   UINT *alert_level, UINT *alert_value);
```

### <a name="description"></a>説明

このサービスは、何らかの問題またはエラーへの応答としてリモート ホストがアラートを送信するときに、TLS アラート レベルと値を取得する際に使用されます。

alert_level パラメーターと alert_value パラメーターの値は、リモート ホストからアラートを受信したことを示す NX_SECURE_TLS_ALERT_RECEIVED （0x114） の状態を返した TLS API 呼び出しの直後に、この関数が呼び出された場合にのみ有効です。

TLS アラート値は、ある種の攻撃 （「パディング オラクル」 攻撃など） を防ぐために意図的にあいまいなままになっているため、ローカル ホスト TLS がアラートを送信した場合、返されるエラー コードは、TLS アラート自体よりも実際のエラーをわかりやすく説明していることに注意してください。

アラート レベルの値は、NX_SECURE_TLS_ALERT_LEVEL_WARNING （0x1） または NX_SECURE_TLS_ALERT_LEVEL_FATAL （0x2） の 2 つの値のいずれかです。 一般的に、CloseNotify アラート （TLS セッションの正常終了を示すために使用） にのみ 「警告」 レベルが提供されますが、一部の拡張機能の構成状況が警告と見なされることもあります。 アラートの大部分が 「致命的」 で、潜在的なセキュリティ障害を示しているため、TLS 接続 （ハンドシェイクまたはセッション） が直ちに終了します。

TLS アラート値は TLS RFC 内で定義されています。参照用の RFC 5246 （TLSv1.2） の一覧を次に示します。

| アラート名                     | 値 | 説明                                                                                                                                                  |
| ---------------------------------- | --------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| close_notify                  | 0     | エラーなし。セッションが正常に終了したことを示します                                                                                                                   |
| unexpected_message            | 10    | TLS が予期しないメッセージまたは順番を無視したメッセージを受信しました                                                                                                           |
| bad_record_mac               | 20    | 解読、MAC 検証、またはその両方に失敗しました                                                                                                                    |
| decryption_failed_RESERVED   | 21    | **非推奨** 解読に失敗しました （パディング オラクル攻撃により非推奨）                                                                                      |
| record_overflow               | 22    | TLS 最大レコード サイズを超えるレコードを受信しました                                                                                        |
| decompression_failure         | 30    | TLS レコードの圧縮/圧縮解除内で問題が発生しました                                                                                       |
| handshake_failure             | 40    | 別のアラートの対象となっていない未指定のハンドシェイク エラーが発生しました                                                                            |
| no_certificate_RESERVED      | 41    | TLS で **非推奨** （SSL のみ）                                                                                                                                 |
| bad_certificate               | 42    | 受信した証明書に無効な書式または署名が含まれています                                                                                   |
| unsupported_certificate       | 43    | 無効な種類の証明書を受信しました （例: TLS サーバー認証に使用される署名専用証明書）                                    |
| certificate_revoked           | 44    | 証明書の状態 （CRL または OCSP によって提供） が 「失効」 として示されました                                                                       |
| certificate_expired           | 45    | 受信した証明書の日付が有効な日付範囲外です （まだ有効でないか期限切れ）                                                                 |
| certificate_unknown           | 46    | 他のアラートの対象とならなかった不明な証明書の問題が発生しました                                                                          |
| illegal_parameter             | 47    | TLS ハンドシェイク内の構成またはネゴシエートされた値の一部が無効または範囲外です                                                                      |
| unknown_ca                    | 48    | 受信した ID 証明書は、信頼されたルート CA 証明書への証明書チェーンを使用してトレースできませんでした。                                              |
| access_denied                 | 49    | 有効な証明書を受信したが、要求されたリソースに対してその証明書が無効であったことが、アプリケーションのアクセス制御により示されたことを示します。            |
| decode_error                  | 50    | TLS ヘッダーまたはハンドシェイク メッセージの一部のフィールドまたは値が範囲外であるか無効であるため、TLS レコードのデコードに失敗しました。                      |
| decrypt_error                 | 51    | TLS ハンドシェイク中に署名または完了したメッセージ ハッシュを検証できませんでした。                                                                         |
| export_restriction_RESERVED  | 60    | TLSv1.2 で非推奨になりました                                                                                                                                        |
| protocol_version              | 70    | ハンドシェイク中にネゴシエートされた TLS プロトコルのバージョンは、認識されますが、サポートされていません （例: TLSv1.0 が示されたが、有効になっていない）。                       |
| insufficient_security         | 71    | セキュリティで保護された暗号がないことが原因でハンドシェイクが失敗したときに必ず送信されます （例: キー サイズがアプリケーション要件に対して小さすぎる）                                |
| internal_error                | 80    | 一部の非 TLS エラー （メモリ割り当ての問題、アプリケーションの問題など） が発生したため、TLS セッションが中断されました。                                         |
| user_canceled                 | 90    | ハンドシェイクが完了する前にユーザーまたはアプリケーションによって TLS セッションがキャンセルされた場合に返されます （CloseNotify と同様）。                                 |
| no_renegotiation              | 100   | 再ネゴシエーション要求に応答して、リモート ホストが TLS 再ネゴシエーション ハンドシェイクを実行しないことを示します。                                 |
| unsupported_extension         | 110   | 明示的に要求されていない拡張機能を含む ServerHello を、TLS クライアントが最初の ClientHello 内で受信した場合に送信されます （これは、サーバーに問題があることを示します）。 |

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **alert_level** 受信したアラートのレベル （警告または致命的） を返します。
- **alert_value** 受信したアラートの値を返します （表をご覧ください）。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 操作に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Return values. */
UINT status, alert_level, alert_value;


/* Start a TLS session.  */
status =  nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Check for “alert received” error. */
if(status == NX_SECURE_TLS_ALERT_RECEIVED)
{

        /* Get the alert level and value. */
        status =  nx_secure_tls_session_alert_value_get(&tls_session,
                                             &alert_level, &alert_value);

        /* Print out the received alert level and value. */
        printf("Alert recieved. Value: %d, Level: %d\n", alert_value,
                alert_level);
}
else if(status != NX_SUCCESS)
{
    /* Additional error handling. */
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_start
- nx_secure_tls_session_send
- nx_secure_tls_session_receive

## <a name="nx_secure_tls_session_certificate_callback_set"></a>nx_secure_tls_session_certificate_callback_set

追加の証明書検証に使用する TLS 用のコールバックを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_ session_certificate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *session,
                                    NX_SECURE_X509_CERT *certificate));
```

### <a name="description"></a>説明

このサービスは、TLS セッションに関数ポインターを割り当てます。これは、リモート ホストから証明書を受信したときに TLS によって呼び出されます。これにより、アプリケーションは、DNS 検証、証明書失効、証明書ポリシーの適用などの検証チェックを実行できます。

NetX Secure TLS は、コールバックを呼び出す前に証明書に対して基本的な X.509 パス検証を実行して、その証明書を、TLS の信頼された証明書ストア内の証明書にトレースできることを確認しますが、その他の検証はすべて、このコールバックによって処理されます。

コールバックは、TLS セッション ポインターと、リモート ホスト ID 証明書 （証明書チェーン内のリーフ） へのポインターを提供します。 すべての検証が成功した場合、コールバックは NX_SUCCESS を返します。それ以外の場合は、検証エラーを示すエラー コードを返します。 NX_SUCCESS 以外の値の場合は、TLS ハンドシェイクは直ちに中止されます。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **func_ptr** 証明書検証コールバック関数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 関数ポインターの割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
    /* Certificate validation checking goes here. */
    return(NX_SUCCESS);
}

/* In TLS setup routine. */
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                            certificate_callback);

        /* If status is NX_SUCCESS the certificate callback was added.  */
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_tls_session_client_callback_set"></a>nx_secure_tls_session_client_callback_set

TLS クライアント ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_ session_client_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions, UINT num_extensions));
```

### <a name="description"></a>説明

このサービスは、TLS セッションに関数ポインターを割り当てます。これは、TLS クライアント ハンドシェイクが ServerHelloDone メッセージを受信したときに TLS によって呼び出されます。 コールバック関数を使用すると、アプリケーションが、入力または意思決定を必要とする受信した ServerHello メッセージから、任意の TLS 拡張機能を処理できます。

コールバックは、呼び出し元の TLS セッション制御ブロックと NX_SECURE_TLS_HELLO_EXTENSION オブジェクトの配列を使用して実行されます。 拡張オブジェクトの配列は、特定の拡張機能を検索して解析するヘルパー関数に渡されるように意図されています。 現在、TLS クライアント入力を必要とする、サポートされている特定の拡張機能は NetX Secure 内にありませんが、コールバックは、使用可能になる可能性があるカスタムまたは新しい拡張機能を処理するために、アプリケーション設計者が使用できます。 hello メッセージで提供されている TLS 拡張を解析するヘルパー関数の例については、「*nx_secure_tls_session_sni_extension_parse*」をご覧ください。

また、リモート サーバーが証明書を要求して情報を提供し、TLS クライアントが特定の証明書を選択できるようにした場合は、TLS クライアントに対して *nx_secure_tls_active_certificate_set* を使用して、アクティブな ID 証明書を選択するためにクライアント コールバックを使うこともできます。 詳細については、「nx_secure_tls_active_certificate_set」のリファレンスをご覧ください。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **func_ptr** TLS クライアント コールバック関数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 関数ポインターの割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Callback routine used to process ServerHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the server). */

ULONG tls_client_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{

    /* Extension parsing would go here. */

    /* Set an active identity certificate – the certificate should have been added
       to the local store at application start with
       nx_secure_tls_local_certificate_add. */
    nx_secure_tls_active_certificate_set(session, &global_identity_certificate);

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
    /* Add callback to TLS session.  */
    status =  nx_secure_tls_session_client_callback_set(tls_session,
                                                        client_callback);

    /* If status is NX_SUCCESS the callback was added and will be invoked once
       a ServerHelloDone message is received. */

    return(status);
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_x509_client_verify_configure"></a>nx_secure_tls_session_x509_client_verify_configure

クライアント X.509 検証を有効にし、クライアント証明書用の領域を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_x509_client_verify_configure(
                  NX_SECURE_TLS_SESSION *session_ptr,
                  UINT certs_number, VOID *certificate_buffer,
                  ULONG buffer_size);
```

### <a name="description"></a>説明

このサービスを使用すると、TLS サーバー インスタンスに対するオプションの X.509 クライアント認証が有効になります。 また、リモート クライアント ホストからの受信証明書チェーンの処理に必要な領域も割り当てられます。 リモート クライアントによって提供される証明書は、サービス *nx_secure_tls_trusted_certificate_add* を使用して割り当てられた、TLS サーバー インスタンスの信頼された証明書と照合して検証され ます。

TLS クライアント モードの場合は、リモート証明書の割り当てが必要なので、代わりにサービス *nx_secure_tls_remote_certificate_buffer_allocate* を使用する必要があります。 TLS クライアント インスタンス上で X.509 クライアント認証を有効にしても何の影響もありません。

*certificate_buffer* パラメーターは、受信リモート証明書とそれらの証明書に必要な制御ブロックを格納するために割り当てられた領域を指します。 バッファーは、証明書の数 （*certs_number*） で除算され、各証明書に均等に指定されます。 *buffer_size* パラメーターは、バッファーのサイズを示します。 必要な領域を見つけるには、次の数式を使用します。

```C
buffer_size = (<expected max number of certificates in chain>) *
             (sizeof(NX_SECURE_X509_CERT) + <max cert size>)
```

署名に SHA-256 を使用する 2048 ビットの RSA キーを持つ一般的な証明書の範囲は、1000 バイトから 2000 バイトです。 バッファーは、証明書ごとに少なくともそのサイズを保持できるだけの大きさが必要ですが、リモート ホスト証明書によっては、大幅に小さい、または大きいことがあります。 バッファーが小さすぎて受信証明書を保持できない場合、TLS ハンドシェイクはエラーで終了します。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certs_number** 指定されたバッファーから割り当てる証明書の数。
- **certificate_buffer** リモート ホストから受信した証明書を保持するバッファーへのポインター。
- **buffer_size** 証明書バッファーのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッションまたはバッファー ポインター。
- **NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE** （0x12D） 指定されたバッファーが小さすぎました。
- **NX_INVALID_PARAMETERS** （0x4D） バッファーが小さすぎて、必要な数の証明書を保持できませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Buffer space to hold the incoming certificates. */
#define CERTIFICATE_NUMBER    (2)
#define CERTIFICATE_SIZE      (2000)
#define BUFFER_SIZE          (CERTIFICATE_NUMBER * \
                                (sizeof(NX_SECURE_X509_CERT) + CERTIFICATE_SIZE))
UCHAR certificate_buffer[BUFFER_SIZE];

/* Enable X.509 Client verification and allocate certificate space in our TLS
   Server session.  */
status =  nx_secure_tls_session_x509_client_verify_configure(&tls_session,
                                                    CERTIFICATE_NUMBER,
                                                    certificate_buffer,
                                                    BUFFER_SIZE);


/* If status is NX_SUCCESS the buffer was successfully allocated.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_buffer_allocate

## <a name="nx_secure_tls_session_client_verify_disable"></a>nx_secure_tls_session_client_verify_disable

NetX Secure TLS セッション用のクライアント証明書認証を無効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_client_verify_disable(
                              NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスは、特定の TLS セッションのクライアント証明書の認証を無効にします。 詳細については、「nx_secure_tls_session_client_verify_enable」をご覧ください。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 状態の変更に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_disable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will not
request certificates from the remote TLS client.  */
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_client_verify_enable"></a>nx_secure_tls_session_client_verify_enable

NetX Secure TLS セッション用のクライアント証明書認証を有効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_client_verify_enable(
                                NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスは、特定の TLS セッションのクライアント証明書の認証を有効にします。 TLS サーバー インスタンスのクライアント証明書の認証を有効にすることで、初期 TLS ハンドシェイク中、TLS サーバーによって、任意のリモート TLS クライアントから証明書が要求されます。 リモート TLS クライアントから受信した証明書には、CertificateVerify メッセージが伴います。TLS サーバーは、このメッセージを使用して、クライアントが証明書を所有していること （その証明書に関連付けられている秘密キーにアクセスできること） を確認します。

指定された証明書が検証され、X.509 証明書チェーンを介して TLS サーバーの信頼された証明書ストア内の証明書にトレースできる場合、リモート TLS クライアントは認証され、ハンドシェイクが続行されます。 証明書または CertificateVerify メッセージの処理中にエラーが発生した場合、TLS ハンドシェイクはエラーで終了します。

> [!NOTE]
> *TLS サーバーの信頼されたストアには、nx_secure_tls_trusted_certificate_add によって追加された証明書が少なくとも 1 つ必要です。これがない場合、常に認証に失敗します。*

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 状態の変更に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Add a trusted certificate so the TLS Server has something to verify against. */
status = nx_secure_tls_trusted_certificate_add(&tls_session,
                                               &trusted_certificate);

/* Disable client certificate authentication for this TLS session.   */
status = nx_secure_tls_session_client_verify_enable(&tls_session);

/* Any new TLS Server sessions using the tls_session control block will now
request and verify certificates from the remote TLS client.  */
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_client_verify_enable
- nx_secure_tls_session_start
- nx_secure_tls_session_create
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_tls_session_create"></a>nx_secure_tls_session_create

セキュリティで保護された通信用の NetX Secure TLS セッションを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_create(NX_SECURE_TLS_SESSION *session_ptr
                                   NX_SECURE_TLS_CRYPTO *cipher_table,
                                   VOID *encryption_metadata_area,
                                   ULONG encryption_metadata_size);
```

### <a name="description"></a>説明

このサービスは、ネットワーク接続を介してセキュリティで保護された TLS 通信を確立する際に使用する、NX_SECURE_TLS_SESSION 構造体のインスタンスを初期化します。

メソッドは、TLS に使用される使用可能な暗号化メソッドが設定された NX_SECURE_TLS_CRYPTO オブジェクトを取ります。 *encryption_metadata_area* は、TLS が使用するために割り当てられた 「メタデータ」 用のバッファーを指します。NX_SECURE_TLS_CRYPTO テーブル内の暗号化メソッドは、このメタデータを計算に使用します。 テーブルのサイズは、nx_secure_tls_metadata_size_calculate サービスを使用して決定できます。 詳細については、第 3 章の「NetX Secure TLS」の暗号」をご覧ください。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **cipher_table** TLS 暗号化メソッドへのポインター。
- **metadata** 暗号メタデータ用のスペースへのポインター。
- **encryption_metadata_size** メタデータ バッファーのサイズ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。
- **NX_INVALID_PARAMETERS** （0x4D） メタデータ バッファーが、指定されたメソッドに対して小さすぎました。
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** （0x106） 有効なバージョンの TLS に必要な暗号メソッドが暗号テーブルに指定されていませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Reference the platform-specific TLS cryptographic method table. */
extern const NX_SECURE_TLS_CRYPTO nx_crypto_tls_ciphers;

/* Declare a buffer for the cryptographic metadata. The size should be calculated
   using nx_secure_tls_metadata_size_calculate. */
UCHAR crypto_metadata[4500];

/* Initialize TLS session.  */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* If status is NX_SUCCESS the TLS Session was successfully initialized.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_metadata_size_calculate
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_delete
- 第 3 章の「NetX Secure TLS の暗号」

## <a name="nx_secure_tls_session_delete"></a>nx_secure_tls_session_delete

NetX Secure TLS セッションを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_delete(NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスは、NX_SECURE_TLS_SESSION 構造体インスタンスによって表される TLS セッションを削除し、そのセッション インスタンスが所有するすべてのシステム リソースを解放します。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete TLS session.  */
status =  nx_secure_tls_session_delete(&tls_session);


/* If status is NX_SUCCESS the TLS Session was successfully deleted.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_end
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_end"></a>nx_secure_tls_session_end

アクティブな NetX Secure TLS セッションを終了します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_end(NX_SECURE_TLS_SESSION *session_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、TLS CloseNotify メッセージをリモート ホストに送信することで、NX_SECURE_TLS_SESSION 構造体インスタンスによって表される TLS セッションを終了します。 その後、サービスは、リモート ホストが独自の CloseNotify メッセージで応答するのを待ちます。

リモート ホストによって CloseNotify メッセージが送信されない場合、TLS はこれをエラーと考え、セキュリティ違反の可能性があると見なします。このため、セキュリティで保護された接続にとって、戻り値を確認することは重要です。 **wait_option** パラメーターを使用すると、呼び出し元スレッドに制御を返すまでの、サービスの応答待機時間を制御できます。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **wait_option** サービスがリモート ホストからの応答を待機する時間を指定します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_SECURE_TLS_NO_CLOSE_RESPONSE** （0x113） リモート ホストから応答を受信せずにタイムアウトになりました。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） CloseNotify メッセージを送信するパケットを割り当てることができませんでした。
- **NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） CloseNotify メッセージを TCP ソケット経由で送信できませんでした。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* End TLS session.  */
status =  nx_secure_tls_session_end(&tls_session, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the TLS Session was successfully ended.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_packet_buffer_set"></a>nx_secure_tls_session_packet_buffer_set

NetX Secure TLS セッション用のパケット再構築バッファーを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_packet_buffer_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *buffer_ptr,
                                    ULONG buffer_size);
```

### <a name="description"></a>説明

このサービスは、パケット再構築バッファーを TLS セッションに関連付けます。 受信 TLS レコードを解読および解析するには、各レコード内のデータを、基になる TCP パケットからアセンブルする必要があります。 TLS レコードのサイズは最大 16 KB であるため （通常はこれよりもかなり小さくなりますが）、1 つの TCP パケットに収まらない可能性があります。

受信メッセージのサイズが TLS レコードの上限である 16 KB 未満であることがわかっている場合は、バッファー サイズを小さくできますが、不明な受信データを処理するには、バッファーをできるだけ大きくする必要があります。 指定されたバッファーより受信レコードが大きい場合、TLS セッションはエラーで終了します。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **buffer_ptr** パケットの再構築に使用する TLS 用バッファーへのポインター。
- **buffer_size** 指定されたバッファーのサイズ （バイト単位）。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_INVALID_PARAMETERS** （0x4D） 無効なバッファーまたは TLS セッション ポインター。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Buffer for TLS packet reassembly. */
UCHAR tls_packet_buffer[16384];
/* Assign buffer to TLS session.  */
status =  nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                  sizeof(tls_packet_buffer));


/* If status is NX_SUCCESS the buffer was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_protocol_version_override"></a>nx_secure_tls_session_protocol_version_override

NetX Secure TLS セッション用の既定の TLS プロトコル バージョンをオーバーライドします

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_protocol_version_override(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              USHORT protocol_version);
```

### <a name="description"></a>説明

このサービスは、特定のセッションで使用される既定 （最新） の TLS プロトコル バージョンをオーバーライドします。 これにより、NetX Secure TLS が、コンパイル時に新しい TLS バージョンを無効にせずに、特定の TLS セッションに対して古いバージョンの TLS を使用することができます。 これは、アプリケーションが、最新バージョンの TLS をサポートしていない古いホストとの通信が必要になる可能性があるときに、役に立つ場合があります。

> [!IMPORTANT]
> *バージョン 5.11SP3 の時点で、NetX Secure TLS は RFC 7507 をサポートしており （以下の注をご覧ください）、この API を使用して古いバージョンにオーバーライドすると、ClientHello 内でフォールバック SCSV が送信されます。サーバーが新しいバージョンの TLS をサポートしていて、フォールバック SCSV が ClientHello に含まれていると、そのサーバーは 「不適切なフォールバック」アラートで TLS ハンドシェイクを中止します。SCSV は、バージョンのオーバーライドが、有効になっているものより古いバージョンの TLS の場合にのみ送信されます （たとえば、バージョンを TLS 1.2 にオーバーライドしても、SCSV は送信されません）。*

protocol_version パラメーターの有効な値は、マクロ NX_SECURE_TLS_VERSION_TLS_1_0、NX_SECURE_TLS_VERSION_TLS_1_1、および NX_SECURE_TLS_VERSION_TLS_1_2 です。

マクロ NX_SECURE_TLS_DISABLE_TLS_1_1 と NX_SECURE_TLS_ENABLE_TLS_1_0 は、アプリケーションにコンパイルされる TLS のバージョンの制御に使用できます。 TLS バージョン1.2 は常に有効です。

指定されたバージョンをリモート ホストがサポートしていない場合、接続は失敗します。NetX Secure TLS によってネゴシエートされるのは、指定されたオーバーライド バージョンのみです。

> [!IMPORTANT]
> RFC 7507: TLS フォールバック SCSV。 この RFC は、プロトコル ダウングレード ネゴシエーションを不適切に処理し、有効な ClientHello メッセージを拒否したサーバーに起因するセキュリティ上の問題を軽減するために導入されました。 このような古いサーバーとの互換性を維持するために、一部の TLS クライアント アプリケーションは、失敗したハンドシェイクの再試行を、古い TLS バージョンを使用して開始します （たとえば、TLS 1.2 で失敗した場合は TLS 1.1 を使ってみます）。 ただし、この回避策による新しい問題が発生しました。サーバーが新しい TLS バージョンをサポートしているのに、攻撃者がネットワークまたはパケット エラーを意図的に引き起こしてクライアントを強制的にダウングレードし、サーバー接続を失敗させるのです。 以前のバージョンにダウングレードすることで、攻撃者はそのバージョンの弱点を悪用する可能性があります （特に、SSLv3<sup>21</sup> は POODLE 攻撃に対して脆弱です）。 このような状況を防ぐために、RFC 7507 は、疑似暗号スイート <sup>22</sup>、「フォールバック SCSV」 を導入しました。このフォールバック SCSV は、TLS クライアントが自身がサポートする最新バージョンではない TLS バージョンを使用している場合に、TLS サーバーに通知するために、ClientHello を使用して送信されます。 この方法で、新しいバージョンをサポートするサーバーが、フォールバック SCSV を含む ClientHello を拒否し、ダウングレード攻撃が成功するのを防ぐことができます。

21. NetX Secure は、POODLE などの既知の深刻な弱点が存在するため SSLv3 を実装していません。

22. 疑似暗号スイート、つまり SCSV （シグナリング暗号スイート値） は予約済み暗号スイート番号で、以前の TLS バージョンでは使用できなかった機能に関する有効な TLS 実装にシグナルを送るために使用されます。 フォールバック SCSV と TLS_EMPTY_RENEGOTIATION_INFO_SCSV （RFC 5746） は例です。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **protocol_version** 使用する特定の TLS バージョンの TLS バージョン マクロ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 状態の変更に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** （0x110） 既知だがサポートされていない TLS バージョン。
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 無効なプロトコル バージョン。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the protocol version to be used to TLSv1.1. */
status = nx_secure_tls_session_protocol_version_override(&tls_session,
                                              NX_SECURE_TLS_VERSION_TLS_1_1);

/* This TLS Session will use TLSv1.1 for the handshake and TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_start
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_receive"></a>nx_secure_tls_session_receive

NetX Secure TLS セッションからデータを受信します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_receive(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET **packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、指定されたアクティブな TLS セッションからデータを受信し、そのデータの解読を処理してから、NX_PACKET パラメーター内で呼び出し元に提供します。 指定されたセッション内でデータがキューに入れられていない場合、呼び出しは、指定された待機オプションに基づいて中断します。

> [!IMPORTANT]
> *NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします。*

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **packet_ptr** 割り当てられた TLS パケット ポインターへのポインター。
- **wait_option** サービスが戻る前にリモート ホストからのパケットを待機する長さを指定します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_NO_PACKET** （0x01） 受信したデータはありません。
- **NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信したメッセージの認証ハッシュの確認に失敗しました。
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信したメッセージのヘッダーに不明なプロトコル バージョンが含まれていました。
- **NX_SECURE_TLS_ALERT_RECEIVED** （0x114） リモート ホストから TLS アラートを受信しました。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Receive a packet from an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is received, blocking otherwise.
*/
status =  nx_secure_tls_session_receive(&tls_session, &packet_ptr,
NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the received packet is pointed to by  "packet_ptr". */
```

### <a name="see-also"></a>参照

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_renegotiate_callback_set"></a>nx_secure_tls_session_renegotiate_callback_set

セッションの再ネゴシエーションの開始時に呼び出されるコールバックを割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_ session_renegotiate_callback_set (
                  NX_SECURE_TLS_SESSION *tls_session,
                  ULONG (*func_ptr)(struct NX_SECURE_TLS_SESSION_struct
                  *session));
```

### <a name="description"></a>説明

このサービスは、TLS セッションにコールバックを割り当てます。これは、再ネゴシエーション ハンドシェイクの最初のメッセージをリモート ホストから受信するたびに呼び出されます。

このコールバック関数の目的は、再ネゴシエーション ハンドシェイクが開始していることをアプリケーションに通知することです。アプリケーションは、コールバックから 0 以外の値を返すことによって TLS セッションを終了できます。これにより TLS は TLS セッションをエラーで終了します。 アプリケーションが再ネゴシエーションを続行する場合、コールバックは NX_SUCCESS を返す必要があります。

> [!NOTE]
> *TLS 再ネゴシエーションのセマンティクスにより、コールバックは、リモートサーバーから HelloRequest を受信したときに必ず NetX Secure TLS クライアントに対して呼び出されますが、クライアントが再ネゴシエーションを開始したときは呼び出されません。NetX Secure TLS Server 上では、コールバックは、再ネゴシエーション用の ClientHello （アクティブな TLS セッションのコンテキスト内で受信したすべての ClientHello） を受信すると必ず呼び出されます。つまり、TLS サーバーは、応答するリモート ホストに対して HelloRequest を送信するため、コールバックは、リモート ホストまたはローカル アプリケーションのどちらが再ネゴシエーションを開始したかにかかわらず呼び出されます。*

NetX Secure TLS は、RFC 5746 の Secure Renegotiation Indication 拡張機能を実装しており、再ネゴシエーションのハンドシェイクが中間者攻撃の対象にならないようにしています。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **func_ptr** コールバック関数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） コールバックの割り当てに成功。
- **NX_PTR_ERROR** （0x07） コールバック関数または TLS セッションに対して無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Simple callback notifying the user that a renegotiation is starting. */
ULONG tls_renegotiation_callback(NX_SECURE_TLS_SESSION *session)
{
    printf("Renegotiation initiated by remote host\n");

    return(NX_SUCCESS);
}

/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Set callback for renegotiation notification. */
status = nx_secure_tls_session_renegotiate_callback_set(&tls_session,
                                                tls_renegotiation_callback);
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiate

## <a name="nx_secure_tls_session_renegotiate"></a>nx_secure_tls_session_renegotiate

リモート ホストでセッション再ネゴシエーション ハンドシェイクを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_ session_renegotiate (
                  NX_SECURE_TLS_SESSION *tls_session,
                  UINT wait_option);
```

### <a name="description"></a>説明

このサービスは、接続されたリモート TLS ホストとのセッション 「*再ネゴシエーション*」 ハンドシェイクを開始します。 再ネゴシエーションは、前に確立された TLS セッションのコンテキスト内での 2 番目の TLS ハンドシェイクで構成されます。 新しいハンドシェイク メッセージはそれぞれ、新しいセッション キーが生成され、ChangeCipherSpec メッセージが交換されるまで、TLS セッションを使用して暗号化され、その時点で新しいキーを使用して、すべてのメッセージが暗号化されます。

一度 TLS セッションが確立されたら、いつでも再ネゴシエーションを開始できます。 TLS ハンドシェイク中または TLS セッションが確立される前に再ネゴシエーションが試行された場合、処理は実行されません。

> [!NOTE]
> *このサービスの起動時は、TLS ハンドシェイク全体が実行されるため、完了までの時間と返される状態は、現在の TLS 設定やセッション パラメーターによって異なります。*

NetX Secure TLS は、RFC 5746 の Secure Renegotiation Indication 拡張機能を実装しており、再ネゴシエーションのハンドシェイクが中間者攻撃の対象にならないようにしています。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **wait_option** サービスが戻る前にリモート ホストからのパケットを待機する長さを指定します。 これは TLS 内のすべての NetX サービスに渡されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 再ネゴシエーションに成功。
- **NX_NO_PACKET** （0x01） 受信したデータはありません。
- **NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信したメッセージの認証ハッシュの確認に失敗しました。
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信したメッセージのヘッダーに不明なプロトコル バージョンが含まれていました。
- **NX_SECURE_TLS_ALERT_RECEIVED** （0x114） リモート ホストから TLS アラートを受信しました。
- **NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE** （0x134） ローカルまたはリモート TLS セッションが非アクティブになっているため、再ネゴシエーションができません。
- **NX_SECURE_TLS_RENEGOTIATION_FAILURE** （0x13A） リモート ホストが SCSV または Secure Renegotiation Indication 拡張機能を提供しなかったため、再ネゴシエーションを実行できません。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 基になるパケットの割り当てに失敗しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Establish a TLS session with a remote host (TLS Client) */
status =  nx_secure_tls_session_create(&tls_session,
                                       &nx_crypto_tls_ciphers,
                                       crypto_metadata,
                                       sizeof(crypto_metadata));


/* Setup a client socket connection.  */
status = nx_tcp_client_socket_connect(&tcp_socket, server_ipv4_address,
REMOTE_SERVER_PORT, NX_WAIT_FOREVER);

/* Start the TLS session. */
status = nx_secure_tls_session_start(&tls_session, &tcp_socket, NX_WAIT_FOREVER);

/* Send some data in the first TLS session. (Check “status” for errors…)*/
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Hello there!\r\n", 14, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);

/* Now renegotiate the session. */
status  = nx_secure_tls_session_renegotiate(&tls_session, NX_WAIT_FOREVER);

/* If status == NX_SUCCESS, new TLS session keys have been generated. */

/* Send some data in the new TLS session. This will be encrypted using the new
   keys. */
status = nx_secure_tls_packet_allocate(&tls_session, &pool_0, &send_packet,
                                       NX_WAIT_FOREVER);
status = nx_packet_data_append(send_packet, "Another message…\r\n", 18, &pool_0,
                               NX_WAIT_FOREVER);
status = nx_secure_tls_session_send(&tls_session, send_packet,
                                    NX_IP_PERIODIC_RATE);
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_start
- nx_secure_tls_session_receive
- nx_secure_tls_session_send
- nx_secure_tls_session_renegotiation_callback_set

## <a name="nx_secure_tls_session_reset"></a>nx_secure_tls_session_reset

NetX Secure TLS セッションのクリアし、リセットします

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_reset (NX_SECURE_TLS_SESSION *session_ptr);
```

### <a name="description"></a>説明

このサービスは、TLS セッションをクリアして、セッションが作成されたばかりのように状態をリセットし、既存の TLS セッション オブジェクトを新しいセッションに再利用できるようにします。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_INVALID_PARAMETERS** （0x4D） 無効な TLS セッション ポインター。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Reset a TLS session.  */
status =  nx_secure_tls_session_reset(&tls_session);


/* If status is NX_SUCCESS the session was successfully reset and may be reused.*/
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_send
- nx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_send"></a>nx_secure_tls_session_send

NetX Secure TLS セッションを介してデータを送信します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_send(NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_PACKET *packet_ptr,
                                    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、指定されたアクティブな TLS セッションを使用して、指定された NX_PACKET でデータを送信し、そのデータの暗号化を処理してから、リモート ホストに送信します。 受信側の最後に公開されたウィンドウのサイズがこの要求よりも小さい場合、サービスは、指定された待機オプションに基づいて、必要に応じて中断します。

> [!IMPORTANT]
> *エラーが返されない限り、アプリケーションは、この呼び出しの後にパケットを解放することはできません。送信後、ネットワーク ドライバーがパケットを解放するため、これを行うと予期しない結果が発生します。*

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **packet_ptr** 送信するデータを含む TLS パケットへのポインター。
- **wait_option** 要求が受信側のウィンドウ サイズより大きい場合に、サービスがどのように動作するかを定義します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_NO_PACKET** （0x01） 受信したデータはありません。
- **NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。
- **NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） 基になる TCP ソケットの送信に失敗しました。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。
- **NX_SECURE_TLS_SESSION_UNINITIALIZED** （0x101） 指定された TLS セッションは初期化されませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send a packet using an active TLS session previously created and started with
nx_secure_tls_session_start. Wait until a packet is sent, blocking otherwise.   */
status =  nx_secure_tls_session_send(&tls_session, &packet_ptr, NX_WAIT_FOREVER);


/* If status is NX_SUCCESS the packet has been sent. */
```

### <a name="see-also"></a>参照

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_session_end
- nx_secure_tls_session_create

## <a name="nx_secure_tls_session_server_callback_set"></a>nx_secure_tls_session_server_callback_set

TLS サーバー ハンドシェイクの開始時に呼び出す TLS 用のコールバックを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_ session_server_callback_set (
                 NX_SECURE_TLS_SESSION *tls_session,
                 ULONG (*func_ptr)(NX_SECURE_TLS_SESSION *tls_session,
                                   NX_SECURE_TLS_HELLO_EXTENSION
                                   *extensions, UINT num_extensions));
```

### <a name="description"></a>説明

このサービスは、TLS セッションに関数ポインターを割り当てます。これは、TLS サーバー ハンドシェイクが ClientHello メッセージを受信したときに TLS によって呼び出されます。 コールバック関数を使用すると、アプリケーションが、入力または意思決定を必要とする受信した ClientHello メッセージから、任意の TLS 拡張機能を処理できます。

コールバックは、呼び出し元の TLS セッション制御ブロックと NX_SECURE_TLS_HELLO_EXTENSION オブジェクトの配列を使用して実行されます。 拡張オブジェクトの配列は、特定の拡張機能を検索して解析するヘルパー関数に渡されるように意図されています。 hello メッセージで提供されている TLS 拡張を解析するヘルパー関数の例については、「*nx_secure_tls_session_sni_extension_parse*」をご覧ください。

サーバー コールバックを使用して、TLS サーバー用の *nx_secure_tls_active_certificate_set* を使ってアクティブな ID 証明書を選択することもできます。 これは、通常、Server Name Indication （SNI） 拡張機能に応答して発生します。これにより、TLS クライアントが、接続しようとしているサーバーを示すことができます。 詳細については、「*nx_secure_tls_session_sni_extension_parse*」および「*nx_secure_tls_active_certificate_set*」のリファレンスをご覧ください。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **func_ptr** TLS サーバー コールバック関数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 関数ポインターの割り当てに成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Application-supplied function to map server DNS name to a specific certificate
   ID. The certificate ID is supplied by the application when the certificate is
   added with nx_secure_tls_server_certificate_add. */
UINT application_find_id_by_dns_name(NX_SECURE_X509_DNS_NAME *dns_name)
{
    if(strncmp(dns_name->nx_secure_x509_dns_name, “server_name”,
               dns_name->nx_secure_x509_dns_name_length) == 0)
    {
        /* DNS name matches one we know, return it’s ID. */
        return(0x12);
    }

    /* Unknown DNS name, return 0 to indicate no matching ID found. */
    return(0);
}

/* Callback routine used to process ClientHello extensions and perform other
   runtime actions at the beginning of a TLS handshake (such as selecting an
   identify certificate to provide to the client). */
ULONG tls_server_callback(NX_SECURE_TLS_SESSION *session,
                          NX_SECURE_TLS_HELLO_EXTENSION *extensions, UINT
                          num_extensions)
{
UINT status;
NX_SECURE_X509_DNS_NAME dns_name;
UINT cert_id;
NX_SECURE_X509_CERT *certificate;


    /* Find and parse a Server Name Indication (SNI) extension. */
    status = nx_secure_tls_session_sni_extension_parse(session, extensions,
                                                       num_extensions, &dns_name);

    if(status != NX_SUCCESS && status != NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
        /* Parsed an invalid extension, return the error. */
        return(status);
    }

    if(status == NX_SECURE_TLS_EXTENSION_NOT_FOUND)
    {
            /* SNI extension not found, just return success to use the default
               certificate. */
            return(NX_SUCCESS);
    }

    /* Find the application-supplied numeric identifier for the specified DNS
       name provided by the remote client. */
    cert_id = application_find_id_by_dns_name(&dns_name);

    /* If cert_id is 0, just use the default identity certificate added with
       nx_secure_tls_local_certificate_add. */
    if(cert_id != 0)
    {
        /* Application found a matching name, find the certificate in our
           store. */
        status = nx_secure_tls_server_certificate_find(tls_session, &certificate,
                                                       cert_id);

        if(status != NX_SUCCESS)
        {
            /* Didn’t find a valid certificate with the supplied ID. Return an
               error so TLS can shut down the handshake. */
            return(NX_SECURE_TLS_CERTIFICATE_NOT_FOUND);
        }

        /* Set the active identity certificate – the certificate should have been
           added to the local store at application start with
           nx_secure_tls_local_certificate_add. */
        nx_secure_tls_active_certificate_set(session, certificate);
    }

    return(NX_SUCCESS);
}

/* TLS setup routine. */
UINT tls_setup(NX_SECURE_TLS_SESSION *tls_session)
{
        /* Add callback to TLS session.  */
        status =  nx_secure_tls_session_server_callback_set(tls_session,
                                                            server_callback);

        /* If status is NX_SUCCESS the callback was added and will be invoked
           immediately after a ClientHello message is received. */

        return(status);
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_active_certificate_set
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_server_certificate_add
- nx_secure_tls_server_certificate_find

## <a name="nx_secure_tls_session_sni_extension_parse"></a>nx_secure_tls_session_sni_extension_parse

TLS クライアントから受信した Server Name Indication （SNI） 拡張機能を解析します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_sni_extension_parse(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_TLS_HELLO_EXTENSION
                                    *extensions,
                                    UINT num_extensions,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>説明

このサービスは、TLS サーバー セッション コールバック内から呼び出され、nx_secure_tls_session_server_callback_set を使用して TLS セッションに追加されるように意図されています。 コールバックは、リモート TLS クライアントから ClientHello メッセージを受信した後に呼び出され、使用可能な拡張機能の配列 （および配列内の拡張機能の数） が提供されます。 その配列とその長さをこのルーチンに直接渡して、SNI 拡張機能が存在するかどうかを判断できます。存在しない場合は、NX_SECURE_TLS_EXTENSION_NOT_FOUND が返されますが、これは単にクライアントが SNI 拡張機能を提供しないことを選択したことを示します （エラーではありません）。

SNI 拡張機能が見つかった場合、TLS クライアントによって提供される X.509 DNS 名が dns_name 構造体で返されます。 現在、SNI 拡張機能が提供しているのは単一の DNS 名エントリのみです。これは、TLS サーバーがリモート クライアントに送信する ID 証明書を決定するために使用されることがあります。**

NX_SECURE_X509_DNS_NAME 構造体のフィールド *nx_secure_x509_dns_name* 内には、単に DNS が UCHAR 文字列として、また *nx_secure_x509_dns_name_length* 内には名前文字列の長さが含まれています。 マクロ NX_SECURE_X509_DNS_NAME_MAX は、nx_secure_x509_dns_name バッファーのサイズを制御します。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **extensions** （セッション コールバックからの） TLS Hello 拡張機能の配列へのポインター。
- **num_extensions** （セッション コールバックからの） 配列内の拡張機能の数。
- **dns_name** SNI 拡張機能内で指定された DNS 名を返します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 拡張機能の解析に成功。
- **NX_PTR_ERROR** （0x07） 無効な拡張機能の配列または TLS セッション ポインター。
- **NX_SECURE_TLS_EXTENSION_NOT_FOUND** （0x136） SNI 拡張機能が見つかりません。
- **NX_SECURE_TLS_SNI_EXTENSION_INVALID** （0x137） SNI 拡張形式が無効でした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

### <a name="see-also"></a>参照

- nx_secure_tls_session_server_callback_set
- nx_secure_tls_session_client_callback_set
- nx_secure_tls_server_callback_set
- nx_secure_tls_active_certificate_set

## <a name="nx_secure_tls_session_sni_extension_set"></a>nx_secure_tls_session_sni_extension_set

リモートサーバーに送信する Server Name Indication （SNI） 拡張機能の DNS 名を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_sni_extension_set(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    NX_SECURE_X509_DNS_NAME *dns_name);
```

### <a name="description"></a>説明

このサービスにより、TLS クライアント アプリケーションが、Server Name Indication （SNI） TLS 拡張機能を使用して、リモート TLS サーバーに優先サーバー DNS 名を提供できます。 SNI 拡張機能を使用すると、サーバーは、クライアントによって指定されたサーバーの設定に基づいて、適切な ID 証明書とパラメーターを選択できます。 SNI 拡張機能は現在、送信される単一の DNS 名のみをサポートしているため、単一の名前パラメーターをサポートしています。 dns_name パラメーターは、*nx_secure_x509_dns_name_initialize* を使用して初期化する必要があり、クライアントの優先サーバーが追加されます。 拡張機能の名前を設定解除するには、「dns_name」 パラメーターの値に NX_NULL に指定して呼び出すだけです。

NX_SECURE_X509_DNS_NAME 構造体のフィールド *nx_secure_x509_dns_name* 内には、単に DNS が UCHAR 文字列として含まれます。また *nx_secure_x509_dns_name_length* 内には名前文字列の長さが含まれます。 マクロ NX_SECURE_X509_DNS_NAME_MAX は、nx_secure_x509_dns_name バッファーのサイズを制御します。

> [!NOTE]
> *このルーチンは、nx_secure_tls_session_start が呼び出される前に呼び出す必要があります。そうしないと、ClientHello に SNI 拡張機能が追加されません。*

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **dns_name** アプリケーションによって指定された DNS 名。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） DNS サーバー名の追加に成功。
- **NX_PTR_ERROR** （0x07） 無効な DNS 名または TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
#define TLS_SNI_SERVER_NAME “www.example.com”

NX_SECURE_X509_DNS_NAME dns_name;
NX_SECURE_TLS_SESSION client_tls_session;

/* Application where TLS session is started. */
void main()
{
    /* Create a TLS session for our socket. Ciphers and metadata defined
       elsewhere. See nx_secure_tls_session_create reference for more
       information. */
    status =  nx_secure_tls_session_create(&client_tls_session,
                                           &nx_crypto_tls_ciphers,
                                           server_crypto_metadata,
                                           sizeof(server_crypto_metadata));


    /* Initialize the DNS server name we want to send in the SNI extension. */
    nx_secure_x509_dns_name_initialize(&dns_name, TLS_SNI_SERVER_NAME,
                                    strlen(TLS_SNI_SERVER_NAME));

    /* The SNI server name needs to be set prior to starting the TLS session. */
    nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);

   /* Start TLS session as normal. */
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_start
- nx_secure_x509_dns_name_initialize

## <a name="nx_secure_tls_session_start"></a>nx_secure_tls_session_start

NetX Secure TLS セッションを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_session_start(NX_SECURE_TLS_SESSION *session_ptr,
                                  NX_TCP_SOCKET *tcp_socket_ptr,
                                  ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、指定された TLS セッション制御ブロック、および接続されている TCP ソケットを使用して、TLS セッションを開始します。 nx_tcp_client_socket_connect または nx_tcp_server_socket_accept のいずれかに対する呼び出しが成功した後、TCP 接続は既に完了している必要があります。

このサービスは、TCP ソケットからの TLS セッション （クライアントまたはサーバー） の種類を決定します。

待機オプションは、TLS ハンドシェイクの進行中にサービスがどのように動作するかを定義します。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **tcp_socket_ptr** 接続されている TCP ソケットへのポインター。
- **wait_option** TLS ハンドシェイクの進行中にサービスがどのように動作するかを定義します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_NOT_CONNECTED** （0x38） 基になる TCP ソケットの接続が解除されています。
- **NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE** （0x102） 受信した TLS メッセージの種類が正しくありません。
- **NX_SECURE_TLS_UNSUPPORTED_CIPHER** （0x106） リモート ホストによって提供された暗号はサポートされていません。
- **NX_SECURE_TLS_HANDSHAKE_FAILURE** （0x107） TLS ハンドシェイク中のメッセージの処理に失敗しました。
- **NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE** （0x108） 受信メッセージがハッシュ MAC チェックに失敗しました。
- **NX_SECURE_TLS_TCP_SEND_FAILED** （0x109） 基になる TCP ソケットの送信に失敗しました。
- **NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH** （0x10A） 受信メッセージに無効な長さのフィールドがありました。
- **NX_SECURE_TLS_BAD_CIPHERSPEC** （0x10B） 受信 ChangeCipherSpec メッセージが正しくありませんでした。
- **NX_SECURE_TLS_INVALID_SERVER_CERT** （0x10C） 受信 TLS 証明書を、リモート TLS サーバーの識別に使用できません。
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** （0x10D） リモート ホストによって提供された公開キー暗号はサポートされていません。
- **NX_SECURE_TLS_NO_SUPPORTED_CIPHERS** （0x10E） リモート ホストは、NetX Secure TLS スタックによってサポートされている暗号スイートがないことを示しています。
- **NX_SECURE_TLS_UNKNOWN_TLS_VERSION** （0x10F） 受信した TLS メッセージのヘッダーに不明な TLS バージョンがありました。
- **NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION** （0x110） 受信した TLS メッセージのヘッダーに既知だがサポートされていない TLS バージョンがありました。
- **NX_SECURE_TLS_ALLOCATE_PACKET_FAILED** （0x111） 内部 TLS パケットの割り当てに失敗しました。
- **NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） リモート ホストが無効な証明書を提供しました。
- **NX_SECURE_TLS_ALERT_RECEIVED** （0x114） リモート ホストが、エラーを通知して TLS セッションを終了するアラートを送信しました。
- **NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE** （0x13B） 暗号スイート テーブル内のエントリに NULL 関数ポインターがありました。
- **NX_SECURE_TLS_INAPPROPRIATE_FALLBACK** （0x146） リモート TLS ClientHello にフォールバック SCSV が含まれており、バージョン フォールバックを試行しました。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_TCP_SOCKET tcp_socket;
NX_SECURE_TLS_SESSION tls_session;
NX_SECURE_X509_CERT certificate;

/* Initialize the TLS session structure. */
nx_secure_tls_session_create(&tls_session,
                              &nx_crypto_tls_ciphers,
                              crypto_metadata,
                              sizeof(crypto_metadata));

/* Setup the TLS packet reassembly buffer. */
status = nx_secure_tls_session_packet_buffer_set(&tls_session, tls_packet_buffer,
                                                 sizeof(tls_packet_buffer));

/* Initialize a certificate for the TLS server. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data, 500,
NX_NULL, 0, private_key, 64);

/* If status is NX_SUCCESS, certificate is initialized. */

/* Add the certificate a local certificate to identify this TLS server. */
status = nx_secure_tls_add_local_certificate(&tls_session, &certificate);

/* If status is NX_SUCCESS, certificate was added successfully. */

/* Create and start a TCP socket as a server. */
/* NOTE: This assumes an IP instance called “ip_0” has already been created. */

/* Create a TCP server socket on the previously created IP instance, with normal
   delivery, IP fragmentation enabled, default time to live, a 8192-byte receive
   window, no urgent callback routine, and the "client_disconnect" routine to
   handle disconnection initiated from the other end of the connection.  */
status =  nx_tcp_socket_create(&ip_0, &tcp_socket, "TLS Server Socket", NX_IP_NORMAL,
                               NX_FRAGMENT_OKAY, NX_IP_TIME_TO_LIVE, 8192, NX_NULL,
                               NX_NULL);

/* If status is NX_SUCCESS, the TCP socket was created successfully. */

/* Start up a TCP server socket by listening on port 443 with a listen queue of
   size 5. */
status =  nx_tcp_server_socket_listen(&ip_0, 443, &tcp_socket, 5, NX_NULL);

/* Application main loop. */
while(1)
{
        /* Accept incoming requests on the TCP socket. */
        status =  nx_tcp_server_socket_accept(&tcp_socket, NX_WAIT_FOREVER);

        /* At this point, the TCP socket should be established (but not the TLS
        session yet). */

        /* Start the TLS session on our active TCP socket. */
        status = nx_secure_tls_session_start(&tls_session, &tcp_socket,
                                             NX_WAIT_FOREVER);

        /* At this point, if status is NX_SUCCESS, the TLS session has been
           established.  Application may now send/receive data through this
           channel. */

        /* Send and receive data using the TLS session. */
        /* Allocate TLS packets using nx_secure_tls_packet_allocate, write data with
           nx_packet_data_append, read data with nx_packet_data_extract_offset. */

        /* Send TLS data. */
        nx_secure_tls_session_send(&tls_session, &send_packet, NX_WAIT_FOREVER);

        nx_secure_tls_session_receive(&tls_session, &receive_packet_ptr,
        NX_WAIT_FOREVER);


        /* Once all application data is sent/received, end the TLS session. */
        status = nx_secure_tls_session_end(&tls_session);

        /* If status is NX_SUCCESS, the TLS session has been closed properly. */

        /* Now disconnect the TCP server socket from the client.  */
        nx_tcp_socket_disconnect(&tcp_socket, 200);

        /* Unaccept the TCP server socket.  Note that unaccept is called even if
           disconnect or accept fails.  */
        nx_tcp_server_socket_unaccept(&tcp_socket);

        /* Setup server socket for listening with this socket again.  */
        nx_tcp_server_socket_relisten(&ip_0, 443, &tcp_socket);
}

/* When the server application is shut down, clean up the TLS session. */
nx_secure_tls_session_delete(&tls_session);

/* Finally, clean up the TCP socket as well. */
nx_tcp_socket_delete(&tcp_socket);
```

### <a name="see-also"></a>参照

- nx_tcp_socket_receive
- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_send
- nx_secure_tls_session_delete
- nx_secure_tls_session_receive
- nx_secure_tls_packet_allocate
- nx_secure_tls_session_end
- nx_secure_tls_session_create
- nx_tcp_socket_accept
- nx_tcp_socket_listen
- nx_tcp_socket_disconnect
- nx_tcp_socket_unaccept
- nx_tcp_socket_relisten
- nx_tcp_socket_delete
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset

## <a name="nx_secure_tls_session_time_function_set"></a>nx_secure_tls_session_time_function_set

NetX Secure TLS セッションにタイムスタンプ関数を割り当てます

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_time_function_set(
                              NX_SECURE_TLS_SESSION *session_ptr,
                              ULONG (*time_func_ptr)(void));
```

### <a name="description"></a>説明

この関数は、TLS が現在の時刻を取得する必要があるときに呼び出す関数ポインターを設定します。これは、さまざまな TLS ハンドシェイク メッセージ内で、また、証明書を検証するときに使用されます。

この関数は、TLS RFC 5246 内の ClientHello の要件に従って、UNIX 32 ビット形式で現在の GMT （UTC 1970 年 1 月 1 日午前 0 時からの秒数、うるう秒は無視） を返すことが想定されています。

タイムスタンプ関数が割り当てられていない場合は、TLS ハンドシェイク内のタイムスタンプに対して値 0 が使用され、証明書の有効期限の確認は機能しません。

### <a name="parameters"></a>パラメーター

- **session_ptr** TLS セッション インスタンスへのポインター。
- **time_func_ptr** UNIX 32 ビット形式で現在の時刻 （GMT） を返す関数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） TLS セッションの初期化に成功。
- **NX_INVALID_PARAMETERS** （0x4D） 無効な TLS セッション ポインター。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* This function returns a 32-bit UNIX-style representation of the current GMT
   time. */
ULONG get_gmt_time(void)
{
ULONG time_value;

   /* Platform-specific time calculation goes here… */

   return(time_value);
}

/* Reset a TLS session.  */
status =  nx_secure_tls_timestamp_function_set(&tls_session, get_gmt_time);


/* If status is NX_SUCCESS the function was successfully added.*/
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_session_start
- nx_secure_tls_session_delete
- nx_secure_tls_session_sendnx_secure_tls_session_receive
- nx_secure_tls_session_create

## <a name="nx_secure_tls_trusted_certificate_add"></a>nx_secure_tls_trusted_certificate_add

信頼された証明書を NetX Secure TLS セッションに追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_trusted_certificate_add(NX_SECURE_TLS_SESSION
                            *session_ptr, NX_SECURE_X509_CERT *certificate_ptr);
```

### <a name="description"></a>説明

このサービスは、初期化された NX_SECURE_X509_CERT 構造体インスタンスを、TLS セッションに追加します。 TLS スタックはこの証明書を使用して、TLS ハンドシェイク中にリモート ホストによって提供される証明書を検証します。

TLS クライアント モードの場合は、信頼された証明書が必要です。

TLS サーバー モードの場合は、クライアント証明書認証が有効になっているときにのみ、信頼された証明書が必要です。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **certificate_ptr** 初期化された TLS 証明書インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の追加に成功。
- **NX_INVALID_PARAMETERS** （0x4D） 無効な証明書を追加しようとしました。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Initialize certificate structure. */
status = nx_secure_x509_certificate_initialize(&certificate, certificate_data,
                                               certificate_buffer,
                                               sizeof(certificate_buffer), 500,
                                               private_key, 64);

/* Add certificate to TLS session.  */
status =  nx_secure_tls_trusted_certificate_add(&tls_session, &certificate);


/* If status is NX_SUCCESS the certificate was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_remove

## <a name="nx_secure_tls_trusted_certificate_remove"></a>nx_secure_tls_trusted_certificate_remove

信頼された証明書を NetX Secure TLS セッションから削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_tls_trusted_certificate_remove(
                                    NX_SECURE_TLS_SESSION *session_ptr,
                                    UCHAR *common_name,
                                    UINT common_name_length);
```

### <a name="description"></a>説明

このサービスは、証明書の共通名フィールドをキーとして、信頼された証明書を TLS セッションから削除します。

### <a name="parameters"></a>パラメーター

- **session_ptr** 前に作成した TLS セッション インスタンスへのポインター。
- **common_name** 削除する証明書の共通名の値。
- **common_name_length** 共通名の文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の追加に成功。
- **NX_PTR_ERROR** （0x07） 無効な TLS セッション ポインター。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） 証明書が見つかりませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Remove certificate from TLS session.  */
status =  nx_secure_tls_trusted_certificate_remove(&tls_session,
                                                “www.example.com”, 15);


/* If status is NX_SUCCESS the certificate was successfully removed.  */
```

### <a name="see-also"></a>参照

- nx_secure_x509_certificate_initialize
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- nx_secure_tls_trusted_certificate_add

## <a name="nx_secure_x509_certificate_initialize"></a>nx_secure_x509_certificate_initialize

NetX Secure TLS 用の X.509 証明書を初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_certificate_initialize(
                  NX_SECURE_X509_CERT *certificate_ptr,
                  const UCHAR *certificate_data,
                  USHORT certificate_data_length,
                  UCHAR *raw_data_buffer,
                  USHORT buffer_size,
                  const UCHAR *private_key_data,
                  USHORT private_key_data_length,
                  UINT private_key_type);
```

### <a name="description"></a>説明

このサービスは、TLS セッションで使用するために、バイナリエンコードされた X.509 デジタル証明書から NX_SECURE_X509_CERT 構造体を初期化します。

証明書データは、DER でエンコードされたバイナリ形式の有効な X.509 デジタル証明書である **必要があります**。 データは、そのデータへの UCHAR ポインターが提供されていれば、どのようなソース （ファイル システム、コンパイル済みの定数バッファーなど） のものでも構いません。

*raw_data_buffer* パラメーターとそのサイズは、解析前に証明書データがコピーされる専用バッファーを指定する省略可能なパラメーターです。 raw_data_buffer が NX_NULL として渡された場合、NX_SECURE_X509_CERT 構造体は、certificate_data 配列を直接指します （この場合、buffer_size は無視されます）。 raw_data_buffer が NX_NULL として渡された場合は、certificate_data ポインターが指すデータを変更 ***しないでください***。そうしないと証明書の処理が失敗する可能性があります。

秘密キー パラメーターはローカル ID 証明書のためのものです。サーバーは秘密キーを使用して、クライアントから受信するキー データ （サーバーの公開キーを使用して暗号化されたもの） を解読し、クライアントは、秘密キーを使用して、サーバーがクライアント証明書を要求したときに、サーバーに対して自身の ID を証明するために使用します。 この API を使用して秘密キーを追加すると、関連付けられている証明書が、TLS アプリケーションの ID 証明書として自動的にマークされます。 他の目的 （信頼されたストアなど） のために証明書を初期化する場合は、*private_key_data* パラメーターを NULL として、*private_key_data_length* を 0 として、また *private_key_type* を NX_SECURE_X509_KEY_TYPE_NONE として渡す必要があります。

*private_key_type* パラメーターは、秘密キーの形式を示します。 たとえば、秘密キーが DER でエンコードされた PKCS#1 形式の RSA 秘密キーである場合は、private_key_type を NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER として渡す必要があります。これは NetX Secure の既知の種類で、すぐに解析され、後で使用するために保存されます。

private_key_type は、特定のキー形式やその他のニーズを持つプラットフォームやアプリケーションに対応するために、ユーザー定義のキーの種類<sup>23</sup> もサポートしています。 たとえば、NetX Secure ソフトウェアによって認識されない特定の形式が、ハードウェアベースの暗号化エンジンによって使用されている場合があります。また、秘密キーは、トラステッド プラットフォーム モジュール （TPM） や PKCS#11 暗号化ハードウェアのように、暗号化トークンによって暗号化または表される場合があります。 ユーザー定義のキーの種類を使用すると、キー データは適切な暗号化ルーチンにそのまま渡されます。たとえば、RSA 秘密キーは、解析や処理を行わずに、暗号スイート テーブル内の TLS に提供された RSA 暗号化ルーチンに直接渡されます。 また、ユーザー定義のキーの種類も暗号化ルーチンに渡されます （RSA の場合、これは 「op」 パラメーターです）。

ユーザー定義キーの範囲は、0x0001 0000-0xFFFF FFFF から、32 ビット符号なし整数の上半分を対象としています。 0x0001 0000 未満の値は、NetX Secure use 用に予約されています。

ユーザー定義のキーの種類は、秘密キーの生データを処理するためのカスタム暗号化ルーチンを必要とする高度な機能です。 この機能が必要な場合は、Express Logic の担当者にお問い合わせください。

### <a name="parameters"></a>パラメーター

- **certificate_ptr** 初期化されていない X.509 証明書インスタンスへのポインター。
- **certificate_data** DER でエンコードされた X.509 バイナリ データへのポインター。
- **raw_data_buffer** オプションの専用証明書データ バッファーへのポインター。
- **buffer_size** オプションの専用証明書データ バッファーのサイズ。
- **certificate_data_length** 証明書のバイナリ データの長さ （バイト単位）。
- **private_key_data** オプションの秘密キー データへのポインター。
- **private_key_data_length** 秘密キー データの長さ。
- **private_key_type** キーの種類の識別子。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書の追加に成功。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。
- **NX_SECURE_TLS_INVALID_CERTIFICATE** （0x112） 証明書データに DER でエンコードされた X.509 証明書が含まれていませんでした。
- **NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER** （0x10D） 証明書に、NetX Secure によってサポートされている公開キー暗号がありませんでした。
- **NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE** （0x186） 秘密キーまたは証明書に、有効な ASN.1 シーケンスが含まれていませんでした。
- **NX_SECURE_PKCS1_INVALID_PRIVATE_KEY** （0x18A） 指定された秘密キーは、有効な PKCS#1 RSA キーではありませんでした。
- **NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE** （0x19D） 指定された秘密キーの種類は、ユーザー定義ではなく、既知の種類と一致しませんでした。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Initialize certificate structure. The certificate structure will point directly
   into the certificate_data array since we are passing the raw_data_buffer as
   NX_NULL. This certificate has a private key so it will be used to identify this
   device. */
status =  nx_secure_x509_certificate_initialize(&certificate, certificate_data,
500, NX_NULL, 0, private_key, 64, NX_SECURE_X509_KEY_TYPE_RSA_PKCS1_DER);


/* If status is NX_SUCCESS the certificate was successfully initialized.  */
```

### <a name="see-also"></a>参照

- nx_secure_local_certificate_add
- nx_secure_tls_session_create
- nx_secure_tls_remote_certificate_allocate
- 第 3 章の「X.509 証明書を NetX Secure にインポートする」

## <a name="nx_secure_x509_common_name_dns_check"></a>nx_secure_x509_common_name_dns_check

DNS 名を X.509 証明書と照合して確認します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_common_name_dns_check(
                        NX_SECURE_X509_CERT *certificate,
                        const UCHAR *dns_tld, UINT dns_tld_length);
```

### <a name="description"></a>説明

このサービスは、リモート ホストの DNS 検証の目的で、証明書の共通名を、呼び出し元によって提供されたトップドメイン名 （TLD） と照合して確認します。 このユーティリティ関数は、アプリケーションによって提供された証明書検証コールバック ルーチン内から呼び出されるように意図されています。 TLD 名は、リモート ホストへのアクセスに使用された URL の先頭部分 （最初のスラッシュの前の 「. 」 で区切られた文字列） です。 共通名にワイルドカード （ *.example.com など） が含まれる場合、そのワイルドカードは、同じサフィックスを持つものと一致します。ワイルドカード照合では、最初のワイルドカード （「* 」） のみが考慮されることに注意してください （右から左に読み取り）。たとえば、abc.*.exampl.com は、末尾が 「.example.com」 の *すべて*」 の名前と一致します。

指定された文字列と共通名が一致しない場合は、「subjectAltName」 拡張機能が解析され （証明書に存在する場合）、さらに DNSName エントリも比較されます。 一致するエントリがない場合は、エラーが返されます。

予想される証明書内の共通名 （および subjectAltName エントリ） の形式を理解することが重要です。 たとえば、証明書によっては、生 IP アドレスまたはワイルド カードが使用されている場合があります。 DNS TLD 文字列は、受信した証明書内の予期される値と一致するように書式設定されている必要があります。

### <a name="parameters"></a>パラメーター

- **certificate_ptr** X.509 証明書インスタンスへのポインター。
- **dns_tld** 比較対象となる最上位レベルのドメイン名。
- **dns_tld_length** TLD 文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 共通名または subjectAltName との比較に成功。
- **NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH** （0x195） 一致する名前が見つかりませんでした。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
UCHAR *tld = “www.example.com”;

    /* Check our DNS TLD against the certificate provided by the
       remote TLS host. */
    status = nx_secure_x509_common_name_dns_check(certificate, tld, strlen(tld));

        if(status != NX_SUCCESS)
        {
            /* TLD did not match any names in the certificate. */
            return(status);
        }

        /* DNS validation and any other checks were successful. */
        return(NX_SUCCESS);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_crl_revocation_check

## <a name="nx_secure_x509_crl_revocation_check"></a>nx_secure_x509_crl_revocation_check

X.509 証明書を指定された証明書失効リスト （CRL） と照合して確認します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_crl_revocation_check(const UCHAR *crl_data,
                              UINT crl_length,
                              NX_SECURE_X509_CERTIFICATE_STORE *store,
                              NX_SECURE_X509_CERT *certificate);
```

### <a name="description"></a>説明

このサービスは、DER でエンコードされた証明書失効リストを取得し、そのリスト内で特定の証明書を検索します。 CRL の発行者は、指定された証明書ストアに対して検証されます。CRL の発行者は、確認対象の証明書の発行者と同じであることが検証され、該当する証明書のシリアル番号を使用して、失効証明書リストが検索されます。 発行者が一致し、署名がチェックアウトされ、証明書がリストに存在 **しない** 場合、呼び出しは成功します。 それ以外の場合は、エラーが返されます。

### <a name="parameters"></a>パラメーター

- **crl_data** DER でエンコードされた CRL へのポインター。
- **crl_length** CRL データの長さ （バイト単位）。
- **store** X.509 証明書ストアへのポインター。
- **certificate_ptr** X.509 証明書インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 証明書が失効していないことの検証に成功。
- **NX_SECURE_TLS_CERTIFICATE_NOT_FOUND** （0x119） CRL の発行者が見つかりませんでした。
- **NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND** （0x11B） 証明書の発行者が見つかりませんでした。
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） CRL ASN.1 に無効な長さのフィールドが含まれています。
- **NX_SECURE_X509_UNEXPECTED_ASN1_TAG （0x189）** CRL に無効な ASN.1 が含まれています。
- **NX_SECURE_X509_CHAIN_VERIFY_FAILURE** （0x18C） 証明書チェーンの検証に失敗しました。
- **NX_SECURE_X509_CRL_ISSUER_MISMATCH** （0x197） CRL と証明書の発行者が一致しませんでした。
- **NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED** （0x198） CRL の署名が無効でした。
- **NX_SECURE_X509_CRL_CERTIFICATE_REVOKED** （0x199） 確認対象の証明書は、CRL 内に見つかったため失効します。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* CRL obtained for the expected certificate issuer through some means (downloaded
   from server manually, obtained from CRL endpoint, etc…) */
const UCHAR *crl_data;
UINT crl_length = 300;

/* Callback routine used to perform additional checks on a certificate. */
ULONG certificate_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT
*certificate)
{
ULONG status;
NX_SECURE_X509_CERTIFICATE_STORE *store;

    /* Obtain a certificate store to check against. In the certificate callback,
       it usually makes the most sense to use the store associated with the TLS
       session. */
    store = &session -> nx_secure_tls_credentials.nx_secure_tls_certificate_store;

    /* Check our certificate against the CRL and TLS certificate store. */
    status = nx_secure_x509_crl_revocation_check(crl, crl_length, store,
                                                 certificate);

        if(status != NX_SUCCESS)
        {
            if(status == NX_SECURE_X509_CRL_CERTIFICATE_REVOKED)
            {
                /* Certificate was revoked. */
               return(status);
            }
            else
            {
               /* CRL was invalid or some other issue. In this case the certificate
                  may still be valid since the CRL itself was a problem. At this
                  point it is up to the application to decide whether to continue
                  with the TLS handshake. For this example, assume certificate is
                  valid (faulty CRL is a possible Denial-of-Service attack).*/
               status = NX_SUCCESS;
        }

    /* Other certificate checking can go here. */

    /* Return status of certificate checks. */
    return(status);
}

…

/* Add callback to TLS session in TLS setup routine.  */
status =  nx_secure_tls_session_certificate_callback_set(&tls_session,
                                                         certificate_callback);
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_common_name_dns_check

## <a name="nx_secure_x509_dns_name_initialize"></a>nx_secure_x509_dns_name_initialize

X.509 DNS 名の構造体を初期化します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_dns_name_initialize(
                        NX_SECURE_X509_DNS_NAME *dns_name,
                        const UCHAR *name_string, UINT length);
```

### <a name="description"></a>説明

このサービスは、特定の名前形式を必要とする特定の API サービスで使用するために、X.509 DNS 名を初期化します。 たとえば、*nx_secure_tls_sni_extension_parse* サービスは、TLS ハンドシェイク中にリモート ホストが Server Name Indication 拡張機能内で提供した名前と一致させるために、NX_SECURE_X509_DNS_NAME オブジェクトを期待します。 DNS 名は、長さを持つシンプルな文字列です。DNS 名の許容最大長 （および NX_SECURE_X509_DNS_NAME 内の内部バッファーのサイズ） は、マクロ NX_SECURE_X509_DNS_NAME_MAX によって制御されます （既定値は 100 バイト）。

### <a name="parameters"></a>パラメーター

- **dns_name** 初期化する DNS 名の構造体。
- **name_string** DNS 名の文字列データ。
- **length** 名前の文字列の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 初期化に成功。
- **NX_SECURE_X509_NAME_STRING_TOO_LONG** （0x19E） 指定された名前の文字列が NX_SECURE_X509_DNS_NAME_MAX を超えました。
- **NX_PTR_ERROR** （0x07） 無効なポインターを使用しようとしました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
NX_SECURE_X509_DNS_NAME dns_name;

/* Initialize DNS name. */
status = nx_secure_x509_dns_name_initialize(&dns_name, “www.example.com”,
                                            strlen(“www.example.com”);

/* Use initialized DNS name to send the Server Name Indication extension to the
   remote TLS server. */
status = nx_secure_tls_session_sni_extension_set(&tls_session, &dns_name);
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_create
- nx_secure_tls_session_sni_extension_parse
- nx_secure_tls_session_sni_extension_set

## <a name="nx_secure_x509_extended_key_usage_extension_parse"></a>nx_secure_x509_extended_key_usage_extension_parse

X.509 証明書内で X.509 拡張キー使用拡張機能を検索して解析します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_extended_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        UINT key_usage);
```

### <a name="description"></a>説明

このサービスは、証明書の検証コールバック内から呼び出されるように意図されています （「*nx_secure_tls_session_certificate_callback_set*」をご覧ください）。 このメソッドは、X.509 証明書内で特定の拡張キー使用 OID を検索し、OID が存在するかどうかを返します。 key_usage パラメーターは OID の整数マッピングで、NetX Secure X.509 と TLS によって内部的に使用され、可変長 OID 文字列がパラメーターとして渡されないようにします。

以下の表に、拡張キー使用拡張機能の関連する OID を示します。 受信した TLS サーバー証明書内で拡張キー使用を確認する一般的な TLS クライアント実装は、OID NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH が存在するかどうかをチェックします。拡張機能が存在しても、OID が存在しない場合、証明書は、ホストを TLS サーバーとして特定するには無効と見なされ、証明書検証コールバックはエラーを返します。 拡張機能自体がない場合は、TLS ハンドシェイクを続行するかどうかにかかわらず、アプリケーションによって処理されます。

証明書の検証コールバックでは、エラー リターン コード NX_SECURE_X509_KEY_USAGE_ERROR は、アプリケーションの用途のために予約されています。 キーの使用の確認中にエラーが発生した場合は、この値がコールバックから返され、エラーの原因を示すことがあります。

| NetX Secure 識別子                                | OID 値         | 説明                                      |
| --------------------------------------------------------- | --------------------- | ---------------------------------------------------- |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH   | 1.3.6.1.5.5.7.3.1 | 証明書を使用して TLS サーバーの識別できます |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CLIENT_AUTH   | 1.3.6.1.5.5.7.3.2 | 証明書を使用して TLS クライアントを識別できます |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_CODE_SIGNING  | 1.3.6.1.5.5.7.3.3 | 証明書を使用してコードに署名できます             |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_EMAIL_PROTECT | 1.3.6.1.5.5.7.3.4 | 証明書を使用してメールに署名できます           |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_TIME_STAMPING | 1.3.6.1.5.5.7.3.8 | 証明書を使用してタイムスタンプに署名できます       |
| NX_SECURE_TLS_X509_TYPE_PKIX_KP_OCSP_SIGNING  | 1.3.6.1.5.5.7.3.9 | 証明書を使用して OCSP 応答に署名できます   |

X.509 拡張キー使用拡張機能 の OID とマッピング

### <a name="parameters"></a>パラメーター

- **certificate** 検証している証明書へのポインター。
- **key_usage** 上記の表からの OID 整数のマッピング。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 指定されたキー使用 OID が見つかりました。
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** （0x181） ASN.1 マルチバイト タグが見つかりました （サポートされていない証明書）。
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） 無効な ASN.1 フィールドが見つかりました （無効な証明書）。
- **NX_SECURE_X509_INVALID_TAG_CLASS** （0x190） 無効な ASN.1 タグ クラスが見つかりました （無効な証明書）。
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** （0x192） 無効な拡張機能が見つかりました （無効な証明書）。
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** （0x19B） 指定された証明書内に拡張キー使用拡張機能が見つかりませんでした。
- **NX_PTR_ERROR** （0x07） 無効な証明書ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session, NX_SECURE_X509_CERT* certificate)
{
UINT status;

    /* Extended key usage - look for specific OIDs. */
    status = nx_secure_x509_extended_key_usage_extension_parse(certificate,
                        NX_SECURE_TLS_X509_TYPE_PKIX_KP_SERVER_AUTH);

    if(status != NX_SUCCESS)
    {
        if(NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND)
        {
            printf("Extended key usage extension not found or specified key usage OID not
                    provided in extension.\n");
            /* The certificate was valid but the specified OID was not found. The
               application can decide whether to continue or abort the TLS handshake. */
            return(NX_SECURE_X509_KEY_USAGE_ERROR);
        }
        else
        {
            /* The extension or certificate was invalid. */
            return(status);
        }
    }

    /* The specified OID was found, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find

## <a name="nx_secure_x509_extension_find"></a>nx_secure_x509_extension_find

X.509 証明書内で X.509 拡張機能を検索して返します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_extension_find(
                        NX_SECURE_X509_CERT *certificate,
                        NX_SECURE_X509_EXTENSION *extension,
                        USHORT extension_id);
```

### <a name="description"></a>説明

このサービスは、証明書の検証コールバック内から呼び出されるように意図されています （「*nx_secure_tls_session_certificate_callback_set*」をご覧ください）。これは、高度な X.509 サービスです。

関数は、OID に基づいて X.509 証明書内で特定の拡張機能を検索し、OID が存在するかどうかを、関連する拡張機能の生データへの参照を含む構造体と共に返します。 extension_id パラメーターは OID の整数マッピングで、NetX Secure X.509 と TLS によって内部的に使用され、可変長 OID 文字列がパラメーターとして渡されないようにします。

特定の拡張機能 （*nx_secure_x509_key_usage_extension_parse* など） 用に提供されるヘルパー関数は、拡張機能データを取得するために、内部的に nx_secure_x509_extension_find を呼び出します。

既知の X.509 拡張機能に関連する OID については、以下の表で説明します。

NX_SECURE_X509_EXTENSION 構造体には、X.509 証明書へのポインターが含まれています。これを使用すると、*nx_secure_x509_key_usage_extension_parse* などのヘルパー関数が、DER でエンコードされた拡張機能の生 ASN.1 データをすばやくデコードできます。

特定の拡張機能については、RFC 5280 （X.509 仕様） または適切なヘルパー関数のリファレンス （使用可能な場合） をご覧ください。

現在のバージョンの NetX Secure X.509 では、X.509 拡張機能が制限付きでサポートされています。 今後、さらにヘルパー関数が追加される予定です。

> [!IMPORTANT]
> *このサービスは、X.509 拡張機能と DER でエンコードされた ASN.1 に精通しているユーザー向けの高度な機能で、NetX Secure X.509 が現在ヘルパー関数を提供していない拡張機能に、これらのユーザーがアクセスできるようにするために用意されています。このようなヘルパー関数のない拡張機能については、DER でエンコードされた生の ASN.1 をご自身で解析する必要があります。*

| NetX Secure 識別子                              | OID 値 | 説明                                                                    | ヘルパー関数 |
| ------------------------------------------------------- | ------------- | ---------------------------------------------------------------------------------- | -------------------- |
| NX_SECURE_TLS_X509_TYPE_DIRECTORY_ATTRIBUTES  | 2.5.29.9  | ディレクトリ属性 - 証明書のサブジェクトに関する基本情報の属性  | いいえ               |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_KEY_ID       | 2.5.29.14 | 特定の公開キーを識別するために使用されます                                         | いいえ               |
| NX_SECURE_TLS_X509_TYPE_KEY_USAGE             | 2.5.29.15 | 証明書の公開キーの有効な使用方法に関する情報を提供します              | はい              |
| NX_SECURE_TLS_X509_TYPE_SUBJECT_ALT_NAME     | 2.5.29.17 | 証明書を識別するための代替 DNS 名を提供します                     | はい<sup>24</sup>        |
| NX_SECURE_TLS_X509_TYPE_ISSUER_ALT_NAME      | 2.5.29.18 | 証明書の発行者を識別するための代替 DNS 名を提供します            | いいえ               |
| NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS     | 2.5.29.19 | 基本証明書の使用に関する制約情報を提供します                        | いいえ               |
| NX_SECURE_TLS_X509_TYPE_NAME_CONSTRAINTS      | 2.5.29.30 | 証明書名を特定のドメインに制限するために使用されます                        | いいえ               |
| NX_SECURE_TLS_X509_TYPE_CRL_DISTRIBUTION      | 2.5.29.31 | CRL 配布の URI を提供します                                             | いいえ               |
| NX_SECURE_TLS_X509_TYPE_CERTIFICATE_POLICIES  | 2.5.29.32 | 大規模な PKI システムの証明書ポリシーのリスト                             | いいえ               |
| NX_SECURE_TLS_X509_TYPE_CERT_POLICY_MAPPINGS | 2.5.29.33 | CA 証明書ポリシーのリスト                                                | いいえ               |
| NX_SECURE_TLS_X509_TYPE_AUTHORITY_KEY_ID     | 2.5.29.35 | 証明書の署名に関連付けられている特定の公開キーを識別するために使用されます | いいえ               |
| NX_SECURE_TLS_X509_TYPE_POLICY_CONSTRAINTS    | 2.5.29.36 | CA ポリシー制約                                                          | いいえ               |
| NX_SECURE_TLS_X509_TYPE_EXTENDED_KEY_USAGE   | 2.5.29.37 | 追加 OID ベースのキー使用情報                                     | はい              |
| NX_SECURE_TLS_X509_TYPE_FRESHEST_CRL          | 2.5.29.46 | Delta CRL を取得するための情報を提供します                                  | いいえ               |
| NX_SECURE_TLS_X509_TYPE_INHIBIT_ANYPOLICY     | 2.5.29.54 | AnyPolicy を使用できないことを示す CA 証明書フィールド                  | いいえ               |

X.509 拡張機能の OID とマッピング

24. SubjectAltName 拡張機能は、サービス nx_secure_x509_common_name_dns_check 内で DNS 名チェックの一部として解析されます。

### <a name="parameters"></a>パラメーター

- **certificate** 検証している証明書へのポインター。
- **extension** 拡張機能データ ポインターと長さを含む構造体を返します。
- **extension_id** 上記の表からの OID 整数のマッピング。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） 指定された拡張機能 OID が見つかり、データが返されました。
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** （0x181） ASN.1 マルチバイト タグが見つかりました （サポートされていない証明書）。
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） 無効な ASN.1 フィールドが見つかりました （無効な証明書）。
- **NX_SECURE_X509_INVALID_TAG_CLASS** （0x190） 無効な ASN.1 タグ クラスが見つかりました （無効な証明書）。
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** （0x192） 無効な拡張機能が見つかりました
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** （0x19B） 指定された証明書内に拡張機能 OID が見つかりませんでした。
- **NX_PTR_ERROR** （0x07） 無効な証明書または拡張ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Function to parse a Basic Constraints X.509 extension. */
UINT _basic_constraints_extension_parse(NX_SECURE_X509_CERT *certificate)
{
const UCHAR             *current_buffer;
ULONG                    length;
UINT                     status;
NX_SECURE_X509_EXTENSION extension_data;

    /* Find the Basic Constraints extension in the certificate. */
    status = _nx_secure_x509_extension_find(certificate, &extension_data,
                              NX_SECURE_TLS_X509_TYPE_BASIC_CONSTRAINTS);

    /* See if extension present - it might be OK if not present! */
    if (status != NX_SUCCESS)
    {
        return(status);
    }

    /* The extension_data structure now points to the raw extension ASN.1
      (DER-encoded). */
    current_buffer = extension_data.nx_secure_x509_extension_data;
    length = extension_data.nx_secure_x509_extension_data_length;

   /* Extension ASN.1 parsing… */

   return(NX_SUCCESS);
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extended_key_usage_extension_parse

## <a name="nx_secure_x509_key_usage_extension_parse"></a>nx_secure_x509_key_usage_extension_parse

X.509 証明書内で X.509 キー使用法拡張機能を検索して解析します

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_secure_x509_key_usage_extension_parse(
                        NX_SECURE_X509_CERT *certificate,
                        USHORT *bitfield);
```

### <a name="description"></a>説明

このサービスは、証明書の検証コールバック内から呼び出されるように意図されています （「*nx_secure_tls_session_certificate_callback_set*」をご覧ください）。 これは、キー使用拡張機能を検索し、見つかった場合は、「ビットフィールド」 パラメーター内でキー使用ビットフィールドを返します。

X.509 仕様 （RFC 5280） で定義されているビットを以下の表に示します。 ビットごとの AND と適切なビットマスク （および 0 以外のチェック） により、各ビットの値が提供されます。

ビットフィールドの DER エンコードにより余分なゼロが削除されるため、証明書の生データ内でのビットの実際の位置は、デコードされたビットフィールドの位置と異なる可能性があります。 指定されたビットマスクは、*nx_secure_x509_key_usage_extension_parse* によって返されるデコードされたビットフィールド上でのみ使用されるように意図されており、DER でエンコードされた証明書の生データとは異なります。

証明書の検証コールバックでは、エラー リターン コード NX_SECURE_X509_KEY_USAGE_ERROR は、アプリケーションの用途のために予約されています。 キーの使用の確認中にエラーが発生した場合は、この値がコールバックから返され、エラーの原因を示すことがあります。

| NetX Secure 識別子                            | ビット位置 | 説明                                                                                                                                                  |
| ----------------------------------------------------- | ---------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE  | 0            | 証明書をデジタル署名に使用できます                                                                                                               |
| NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION    | 1            | 証明書を使用して、証明書および CRL 以外のデジタル署名を検証できます                                                              |
| NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT   | 2            | 証明書を使用して、対称キーを暗号化できます （キー トランスポート）                                                                                            |
| NX_SECURE_X509_KEY_USAGE_DATA_ENCIPHERMENT  | 3            | 証明書を使用して、ユーザーの生データを直接暗号化できます （一般的ではありません）                                                                                         |
| NX_SECURE_X509_KEY_USAGE_KEY_AGREEMENT      | 4            | 証明書をキーの承諾に使用できます （Diffie-Hellman と同様）                                                                                           |
| NX_SECURE_X509_KEY_USAGE_KEY_CERT_SIGN     | 5            | 証明書を使用して、他の証明書に署名して検証できます （証明書は CA または ICA 証明書です）。                                                  |
| NX_SECURE_X509_KEY_USAGE_CRL_SIGN           | 6            | 証明書の公開キーが、CRL 上の署名の検証に使用されます                                                                                                  |
| NX_SECURE_X509_KEY_USAGE_ENCIPHER_ONLY      | 7            | キーの承諾ビット （ビット 4） に使用されます。設定されている場合、キーの承諾中、暗号化にのみ証明書キーを使用できます。 キーの承諾ビットが設定されていない場合は、未定義です。 |
| NX_SECURE_X509_KEY_USAGE_DECIPHER_ONLY      | 8            | キーの承諾ビット （ビット 4） に使用されます。設定されている場合、キーの承諾中、解読にのみ証明書キーを使用できます。 キーの承諾ビットが設定されていない場合は、未定義です。 |

X.509 キー使用拡張機能のビットマスクと値

### <a name="parameters"></a>パラメーター

- **certificate** 検証している証明書へのポインター。
- **bitfield** 拡張機能からビットフィールド全体を返します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** （0x00） キー使用拡張機能が見つかり、ビットフィールドが返されました。
- **NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED** （0x181） ASN.1 マルチバイト タグが見つかりました （サポートされていない証明書）。
- **NX_SECURE_X509_ASN1_LENGTH_TOO_LONG** （0x182） 無効な ASN.1 フィールドが見つかりました （無効な証明書）。
- **NX_SECURE_X509_INVALID_TAG_CLASS** （0x190） 無効な ASN.1 タグ クラスが見つかりました （無効な証明書）。
- **NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE** （0x192） 無効な拡張機能が見つかりました （無効な証明書）。
- **NX_SECURE_X509_EXTENSION_NOT_FOUND** （0x19B） 指定された証明書内にキー使用拡張機能が見つかりませんでした。
- **NX_PTR_ERROR** （0x07） 無効な証明書またはビットフィールド ポインター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
ULONG certificate_verification_callback(NX_SECURE_TLS_SESSION *session,
  NX_SECURE_X509_CERT* certificate)
{
UINT status;
USHORT key_usage_bitfield;

    /* Key usage – extract key usage bitfield. */
    status = nx_secure_x509_key_usage_extension_parse(certificate, &key_usage_bitfield);

   /* Check certificate for a few specific key usage bits. */
   if((key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_DIGITAL_SIGNATURE) == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_NON_REPUDIATION)   == 0 ||
      (key_usage_bitfield & NX_SECURE_X509_KEY_USAGE_KEY_ENCIPHERMENT)  == 0)
    {
        printf("Expected key usage bitfield bits not set!\n");
        return(NX_SECURE_X509_KEY_USAGE_ERROR);
    }

    /* The specified bits were set, return success! */
    return(NX_SUCCESS);
}
```

### <a name="see-also"></a>参照

- nx_secure_tls_session_certificate_callback_set
- nx_secure_x509_extended_key_usage_extension_parse
- nx_secure_x509_crl_revocation_check
- nx_secure_x509_common_name_dns_check
- nx_secure_x509_extension_find
