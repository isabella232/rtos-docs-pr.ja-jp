---
title: 付録 A - Azure RTOS NetX Secure DTLS のリターン/エラー コード
description: Azure RTOS NetX Secure DTLS サービスによって返される可能性があるエラー コードの一覧を示します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: reference
ms.service: rtos
ms.openlocfilehash: f14f27167a95a1b9d3ebbdf0d903be7b043ccb28
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810514"
---
# <a name="appendix-a-azure-rtos-netx-secure-dtls-returnerror-codes"></a>付録 A: Azure RTOS NetX Secure DTLS のリターン/エラー コード

## <a name="netx-secure-tlsdtls-return-codes"></a>NetX Secure TLS/DTLS のリターン コード

以下の表 1 は、Azure RTOS NetX Secure DTLS サービスによって返される可能性があるエラー コードの一覧を示しています。 また、サービスから UDP または IP のエラー コードが返される可能性があることに注意してください。TLS 値は 0x101 から始まり、TCP/IP/UDP 値は 0x100 未満です。 X.509 の戻り値は 0x181 から始まります。 IP と UDP の戻り値に関する情報ついては、NetX TCP/IP/UDP のドキュメントを参照してください。X.509 値については、以下を参照してください。

| **エラー名**                                        | **Value** | **説明**                                                                                                                                               |
| ----------------------------------------------------- | --------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_TLS_SUCCESS                              | 0x00      | 関数が正常に戻りました。 (NX_SUCCESS と同じです)。                                                                                                        |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101     | TLS メイン ループが、初期化されていないソケットで呼び出されました。                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102     | TLS レコード層で認識できないメッセージの種類を受け取りました。                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103     | 内部エラー - 状態が認識されません。                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104     | 内部エラー - 受信パケットに TLS データが含まれていませんでした。                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105     | 選択した暗号スイートはサポートされていません - サーバーの内部エラー。クライアントの場合は、リモート ホストから不正な暗号スイート (エラーまたは攻撃) が送信されたことを意味します。            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106     | 暗号化または解暗号化の解除の実行で、選択した暗号が無効であるか、使用できません。                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107     | ハンドシェイク中にメッセージ処理で何らかの問題が発生しました。                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108     | 受信レコードの MAC が、サービスで生成されたものと一致しませんでした。                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109     | 何らかの理由により、レコードの発信 TCP の送信に失敗しました。                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH           | 0x10A     | 受信メッセージの長さが正しくありませんでした (通常はヘッダー内の長さと異なる長さ (証明書メッセージなど))                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B     | 受信した ChangeCipherSpec メッセージが正しくありませんでした。                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C     | 受信したサーバー証明書が正しく解析されませんでした。                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D     | サーバーによって提供された証明書に、サポートされていない公開キー操作が指定されていました。                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E     | サポートされている暗号スイートがない ClientHello を受信しました。                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F     | 受信したレコードに、認識されない TLS バージョンがありました。                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110     | 受信したレコードに有効な TLS バージョンがありましたが、サポートされていないものです。                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111     | TLS メッセージに対する内部パケットの割り当てに失敗しました。                                                                                                       |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112     | X509 証明書が正しく解析されませんでした。                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113     | TLS セッションの終了中に、リモート ホストから CloseNotify を受信しませんでした。                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114     | リモート ホストから、エラーを示して接続を終了するアラートが送信されました。                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115     | 受信した Finish メッセージのハッシュが、ローカルで生成されたハッシュと一致しません - ハンドシェイクの破損。                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM        | 0x116     | 検証中の証明書に、サポートされていない署名アルゴリズムがありました。                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED      | 0x117     | 証明書の署名検証チェックに失敗しました - 証明書データが署名と一致しませんでした。                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD             | 0x118     | サポートされていない圧縮方法が使用された Hello メッセージを受信しました。                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND              | 0x119     | 証明書リストの操作で、一致する証明書が見つかりませんでした。                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT          | 0x11A     | リモート ホストによって自己署名証明書が送信されましたが、NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES が定義されていません。                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND      | 0x11B     | リモート証明書を受信しましたが、発行者がローカルの信頼されたストアにありません。                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE              | 0x11C     | DTLS メッセージを間違った順序で受信しました - 破棄されたデータグラムが原因である可能性があります。                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                | 0x11D     | 認識されていないリモート ホストからパケットを受信しました。                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                       | 0x11E     | DTLS メッセージを受信し、DTLS セッションと一致しましたが、そのエポックが間違っており、無視する必要があります。                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED            | 0x11F     | 既に示されているシーケンス番号を持つ DTLS メッセージを受信しました。これは無視されます。                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                  | 0x120     | DTLS API で DTLS 用に初期化されていない TLS セッションが使用されました。                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                   | 0x121     | TLS API で TLS ではなく DTLS 用に初期化された TLS セッションが使用されました。                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH              | 0x122     | 呼び出し元で、DTLS セッションと一致しなかった IP アドレスまたはポートを使用して、そのセッションを介してデータを送信しようとしました。                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS             | 0x123     | 新しい接続でキャッシュから DTLS セッションを取得しようとしましたが、空きがありませんでした。                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                 | 0x124     | 呼び出し元で DTLS セッションを検索しましたが、指定された IP アドレスとポートはキャッシュ内のどのエントリとも一致しませんでした。                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                 | 0x125     | 呼び出し元で TLS セッションに PSK を追加しようとしましたが、指定されたセッション内にはこれ以上領域がありませんでした。                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                    | 0x126     | リモート ホストによって、ローカル ストア内のいずれにも一致しない PSK ID ヒントが提供されました。                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED              | 0x127     | TLS セッションで、セッションが完了したことを示す CloseNotify アラートをリモート ホストから受信しました。                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS              | 0x128     | 接続を処理するために使用できる TLS セッションが、TLS オブジェクト内にありません。                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED           | 0x129     | 証明書領域が、受信リモート証明書に対して割り当てられていませんでした。                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED               | 0x12A     | 受信メッセージ内の暗号化パディングが正しくありませんでした。                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE        | 0x12B     | CertificateVerifyRequest の処理中に、サポートされている証明書の種類がリモート サーバーによって提供されませんでした。                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG         | 0x12C     | CertificateVerifyRequest の処理中に、サポートされている署名アルゴリズムがリモート サーバーによって提供されませんでした。                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE            | 0x12D     | 証明書に対して割り当てられた証明書バッファー領域が不足しています。                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED           | 0x12E     | 受信 TLS レコード内のプロトコル バージョンが、確立されたセッションのバージョンと一致しませんでした。                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR             | 0x12F     | HelloRequest メッセージを受信しましたが、再ネゴシエーションが行われていません。                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                 | 0x130     | TLS セッションで、またはハンドシェイク中に、無効にされた機能が見つかりました。                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE         | 0x131     | リモート クライアントからの CertificateVerify メッセージで、クライアント証明書を確認できませんでした。                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED | 0x132     | リモート ホストによって、空の証明書メッセージが送信されました。                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR      | 0x133     | Secure Renegotiation Indication 拡張機能の処理または送信でエラーが発生しました。                                                                     |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE     | 0x134     | セッションの再ネゴシエーションが、アクティブでない TLS セッションで試行されました。                                                                                |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL           | 0x135     | TLS で受信したレコードが、割り当てられたパケット バッファーに対して大きすぎます。 レコードを処理できませんでした。                                                   |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                | 0x136     | TLS ハンドシェイク中に、指定された拡張機能をリモート ホストから受信しませんでした。                                                                         |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID              | 0x137     | TLS で無効な Server Name Indication 拡張機能を受信しました。                                                                                                     |
| NX_SECURE_TLS_CERT_ID_INVALID                    | 0x138     | アプリケーションで無効な証明書 ID 値 (0 の可能性があります) のサーバー証明書を追加しようとしました。                                                                |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                  | 0x139     | アプリケーションでローカル ストアに既に存在する証明書 ID のサーバー証明書を追加しようとしました。                                                       |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE               | 0x13A     | リモート ホストによって Secure Renegotiation Indication 拡張機能または SCSV 擬似暗号スイートが提供されなかったため、セキュリティで保護された再ネゴシエーションを実行できません。     |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE             | 0x13B     | 暗号化操作を実行しようとしているときに、暗号スイート テーブル内のエントリの 1 つ (またはその関数ポインターの 1 つ) に不適切に null 値が設定されていました。 |

**表 1 - NetX Secure TLS エラーのリターン コード**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X.509 のリターン コード

以下の表 2 は、NetX Secure X.509 サービスによって返される可能性があるエラー コードの一覧を示しています。 また、他のエラー コードがサービスによって返される可能性があることに注意してください。 X.509 の戻り値は 0x181 から、TLS 値は 0x101 から始まります。また、TCP/IP 値は 0x100 未満です。 TCP/IP の戻り値に関する情報については、NetX TCP/IP のドキュメントを参照してください。TLS の戻り値については、上記を参照してください。

| **エラー名**                                   | **Value** | **説明**                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | 正常なリターン状態。 (NX_SUCCESS と同じです)                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | マルチバイトの ASN.1 タグが見つかりました - 現在サポートされていません。                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | 処理できる長さを超える長さの値が見つかりました。                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | パディング値 0 が予期されていました - 異なる値が取得されました。                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X509 には公開キーが予期されていましたが、見つかりませんでした。                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | 公開キーが見つかりましたが、無効であるか、形式が正しくありません。                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | 最上位レベルの ASN.1 ブロックがシーケンスではありません - 無効な X509 証明書。                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | 署名アルゴリズム識別子が予期されていましたが、見つかりませんでした。                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | 証明書 ID データの形式が無効です。                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | X509 形式に固有の ASN.1 タグが予期されていましたが、別のタグが取得されました。                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | PKCS#1 秘密キー ファイルが渡されましたが、形式が正しくありませんでした。                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | X509 証明書チェーンが短すぎて、チェーン構築中にチェーン全体を保持できませんでした。                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | X509 証明書チェーンを検証できませんでした (キャッチオール エラー)。                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | X.509 PKCS#7 でエンコードされた署名の解析に失敗しました。                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | 証明書の検索で、一致するエントリが見つかりませんでした。                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | 指定されたバージョンと互換性のないフィールドが証明書に含まれていました。                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | 無効なタグ クラス値を持つ ASN.1 タグが証明書に含まれていました。                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | 拡張機能 TLV が証明書に含まれていましたが、シーケンスは含まれていませんでした。                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | 無効な X.509 である拡張シーケンスが証明書に含まれていました。                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | 現在の時刻よりも前の "有効期間の終了時刻" フィールドが証明書にありました。                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | 現在の時刻よりも後の "有効期間の開始時刻" フィールドが証明書にありました。                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | 証明書の共通名またはサブジェクト代替名が、指定された DNS TLD と一致しませんでした。                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | 認識されている形式ではない日付フィールドが証明書に含まれていました。                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | 提示された CRL と証明書は、同じ証明機関によって発行されたものではありません。                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | 発行者に対する CRL 署名チェックに失敗しました。                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | 証明書は有効な CRL 内で見つかったため、失効しました。                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | 署名の検証で、署名メソッドが予期されたメソッドと一致しませんでした。                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | 拡張機能の検索で、ID が一致する拡張機能が見つかりませんでした。                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | subjectAltName 拡張機能内で名前が検索されましたが、見つかりませんでした。                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | 指定された秘密キーの種類が不明または無効でした。                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | 渡された名前文字列が、内部バッファーに対して長すぎました (DNS 名など)。                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | 拡張キー使用拡張機能の検索で、指定されたキー使用 OID が見つかりませんでした。                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | 証明書の検証チェック中、キーの使用に失敗した場合に、アプリケーション コールバックによって返されます。 |

**表 2 - NetX Secure X.509 エラーのリターン コード**
