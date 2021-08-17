---
title: 付録 A - Azure RTOS NetX Secure のリターン コードとエラー コード
description: NetX Secure のリターン コードとエラー コード
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3957075f2b2e83f70bbd5f267cac41f003eb7d93722a3b2247b2a33226b4dfc5
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791756"
---
# <a name="appendix-a---azure-rtos-netx-secure-returnerror-codes"></a>付録 A - Azure RTOS NetX Secure のリターン コードとエラー コード

## <a name="netx-secure-tls-return-codes"></a>NetX Secure TLS のリターン コード

以下の表 1 は、Azure RTOS NetX Secure TLS サービスによって返される可能性があるエラー コードを示しています。 サービスによって TCP/IP エラー コードが返される可能性があることに注意してください。TLS 値は 0x101 から始まります。一方、TCP/IP 値は 0x100 未満です。 X.509 戻り値は 0x181 から始まります。 TCP/IP の戻り値については、NetX TCP/IP のドキュメントをご覧ください。X.509 値については、以下をご覧ください。

| エラー名                                             | 値  | 説明                                                                                                                                                    |
| ---------------------------------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| NX_SECURE_TLS_SUCCESS                              | 0x00  | 関数が正常に返されました （NX_SUCCESS と同じ）。                                                                                                         |
| NX_SECURE_TLS_SESSION_UNINITIALIZED               | 0x101  | 初期化されていないソケットを伴って TLS メイン ループが呼び出されました。                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE          | 0x102  | TLS レコード レイヤーが認識できないメッセージ型を受け取りました。                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                       | 0x103  | 内部エラー - 状態が認識されません。                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                      | 0x104  | 内部エラー - 受信パケットに TLS データが含まれていませんでした。                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                 | 0x105  | 選択した暗号スイートはサポートされていません - サーバーの内部エラーです。クライアントの場合は、リモート ホストが無効な暗号スイート （エラーまたは攻撃） を送信したことを意味します。            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                  | 0x106  | 暗号化または解読の実行中、選択されている暗号は無効になっているか、使用できません。                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                   | 0x107  | ハンドシェイク中、メッセージ処理で問題が発生しました。                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE           | 0x108  | 受信レコードに、生成されたものと一致しない MAC がありました。                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                    | 0x109  | 何らかの理由により、レコードの発信 TCP 送信に失敗しました。                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH            | 0x10A  | 受信メッセージの長さが正しくありませんでした （通常は、証明書メッセージのように、ヘッダー内の 1 以外の長さ）                               |
| NX_SECURE_TLS_BAD_CIPHERSPEC                      | 0x10B  | 受信 ChangeCipherSpec メッセージが正しくありませんでした。                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                | 0x10C  | 受信サーバー証明書が正しく解析されませんでした。                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER          | 0x10D  | サーバーが提供した証明書によって、サポートされていない公開キー操作が指定されました。                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS               | 0x10E  | サポートされている暗号スイートがない ClientHello を受信しました。                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                | 0x10F  | 受信レコードに、認識されない TLS バージョンがありました。                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION            | 0x110  | 受信レコードに有効な TLS バージョンがありましたが、サポートされていないものです。                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED             | 0x111 | TLS メッセージに対する内部パケットの割り当てに失敗しました。                                                                                                        |
| NX_SECURE_TLS_INVALID_CERTIFICATE                 | 0x112  | X509 証明書が正しく解析されませんでした。                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                  | 0x113 | TLS セッションの終了中、リモート ホストから CloseNotify を受信しませんでした。                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                      | 0x114 | リモート ホストが、エラーを示して接続を終了するアラートを送信しました。                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE              | 0x115  | 受信した Finish メッセージ ハッシュが、ローカルで生成されたハッシュと一致しません - ハンドシェイクの破損。                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM         | 0x116 | 検証中の証明書に、サポートされていない署名アルゴリズムがありました。                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED       | 0x117  | 証明書の署名検証チェックに失敗しました - 証明書データが署名と一致しませんでした。                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD              | 0x118  | サポートされていない圧縮方法が使用された Hello メッセージを受信しました。                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND               | 0x119  | 証明書リストの操作で、一致する証明書が見つかりませんでした。                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT           | 0x11A  | リモート ホストが自己署名証明書を送信しましたが、NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES が定義されていません。                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND       | 0x11B  | リモート証明書を受信しましたが、ローカルの信頼されたストアに発行者がありません。                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE               | 0x11C  | DTLS メッセージを間違った順序で受信しました - 破棄されたデータグラムが原因である可能性があります。                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                 | 0x11D  | 認識されないリモート ホストからパケットを受信しました。                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                        | 0x11E  | 受信した DTLS メッセージは DTLS セッションと一致しましたが、そのエポックが間違っています。メッセージは無視する必要があります。                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED             | 0x11F  | 既に示されているシーケンス番号を持つ DTLS メッセージを受信しました。無視してください。                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                   | 0x120  | DTLS 用に初期化されていない DTLS API 内で TLS セッションが使用されました。                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                    | 0x121  | TLS ではなく DTLS 用に初期化された TLS API 内で TLS セッションが使用されました。                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH               | 0x122  | 呼び出し元が、DTLS セッションと一致しなかった IP アドレスまたはポートを使用して、そのセッションを介してデータを送信しようとしました。                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS              | 0x123  | 新しい接続がキャッシュから DTLS セッションを取得しようとしましたが、空きがありませんでした。                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                  | 0x124  | 呼び出し元は DTLS セッションを検索しましたが、指定された IP アドレスとポートはキャッシュ内のどのエントリとも一致しませんでした。                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                  | 0x125  | 呼び出し元が TLS セッションに PSK を追加しようとしましたが、指定されたセッション内に領域がありませんでした。                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                     | 0x126  | リモート ホストによって、ローカル ストア内のいずれにも一致しない PSK ID ヒントが提供されました。                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED               | 0x127  | TLS セッションが、セッション完了を示す CloseNotify アラートをリモートホストから受信しました。                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS               | 0x128  | 接続の処理に使用できる TLS セッションが、TLS オブジェクト内にありません。                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED            | 0x129  | 証明書領域が、受信リモート証明書に対して割り当てられていませんでした。                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED                | 0x12A  | 着信メッセージ内の暗号化パディングが正しくありませんでした。                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE         | 0x12B  | CertificateVerifyRequest の処理中、サポートされている証明書の種類がリモート サーバーによって提供されませんでした。                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG          | 0x12C  | CertificateVerifyRequest の処理中、サポートされている署名アルゴリズムがリモート サーバーによって提供されませんでした。                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE             | 0x12D  | 証明書に対して割り当てられた証明書のバッファー領域が不足しています。                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED            | 0x12E  | 受信 TLS レコード内のプロトコル バージョンが、確立されたセッションのバージョンと一致しませんでした。                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR              | 0x12F  | HelloRequest メッセージを受信しましたが、再ネゴシエーションが行われていません。                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                  | 0x130  | TLS セッションまたはハンドシェイク中、無効にされた機能が見つかりました。                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE          | 0x131  | リモート クライアントからの CertificateVerify メッセージが、クライアント証明書を確認できませんでした。                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED  | 0x132  | リモート ホストが、空の証明書メッセージを送信しました。                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR       | 0x133  | Secure Renegotation Indication 拡張機能の処理中または送信中にエラーが発生しました。                                                                      |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE      | 0x134  | セッションの再ネゴシエーションが、アクティブでない TLS セッションで試行されました。                                                                                 |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL            | 0x135  | TLS が受信したレコードが、割り当てられたパケット バッファーに対して大きすぎました。 レコードを処理できませんでした。                                                    |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                 | 0x136  | TLS ハンドシェイク中、指定された拡張機能を、リモート ホストから受信できませんでした。                                                                          |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID               | 0x137  | TLS が無効な Server Name Indication 拡張機能を受信しました。                                                                                                      |
| NX_SECURE_TLS_CERT_ID_INVALID                     | 0x138  | アプリケーションがサーバー証明書を追加しようとしましたが、証明書 ID の値が無効です （0 の可能性があります）。                                                                 |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                   | 0x139  | アプリケーションがサーバー証明書を追加しようとしましたが、証明書 ID がローカル ストアに既に存在します。                                                        |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE                | 0x13A  | リモート ホストが、Secure Renegotiation Indication 拡張機能または SCSV 擬似暗号スイートを提供しなかったため、セキュリティで保護された再ネゴシエーションを実行できません。      |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE              | 0x13B  | 暗号化操作を実行しようとしているときに、暗号スイート テーブル （またはその関数ポインターの 1 つ） 内のエントリの 1 つが不適切に NULL に設定されました。 |
| NX_SECURE_TLS_EMPTY_EC_GROUP                      | 0x13C  | ECC 暗号スイートは設定されていますが、サポートされている EC グループがありません。                                                                                                             |
| NX_SECURE_TLS_EMPTY_EC_POINT_FORMAT              | 0x13D  | ECC 暗号スイートは設定されていますが、サポートされている EC ポイント形式がありません。                                                                                                      |
| NX_SECURE_TLS_BAD_SERVERHELLO_KEYSHARE            | 0x13E  | リモート サーバーからの TLS 1.3 KeyShare 拡張機能内で、予期しなかったものが、そのサーバーによって提供されました。                                                         |
| NX_SECURE_TLS_INSUFFICIENT_METADATA_SPACE         | 0x13F  | アプリケーションによって提供された TLS 暗号化ルーチン用の 「メタデータ」 が小さすぎました。                                                                             |
| NX_SECURE_TLS_POST_HANDSHAKE_RECEIVED             | 0x140  | エラーではなく、アプリケーション データを受信するまで処理を続行することを示しています。                                                                    |
| NX_SECURE_TLS_BAD_CLIENTHELLO_KEYSHARE            | 0x141  | リモート クライアントからの TLS 1.3 KeyShare 拡張機能内で、予期しなかったものが、そのクライアントによって提供されました。                                                         |
| NX_SECURE_TLS_1_3_UNKNOWN_CIPHERSUITE            | 0x142  | TLS 1.3 を使用しているときに不明な暗号スイートを受信しました。                                                                                                              |
| NX_SECURE_TLS_INVALID_SESSION_TICKET              | 0x143  | パラメーターが不適切または無効な NewSessionTicket メッセージを受信しました。                                                                                      |
| NX_SECURE_TLS_MISSING_EXTENSION                    | 0x144  | メッセージ内に特定の拡張子が見つかりません。                                                                                                                  |
| NX_SECURE_TLS_CERTIFICATE_REQUIRED                 | 0x145  | サーバーが、空の証明書を受け取りました。                                                                                                                         |
| NX_SECURE_TLS_UNEXPECTED_CLIENTHELLO               | 0x146  | TLS 1.3 Server は、再ネゴシエーション用に ClientHello を受信します。                                                                                                         |
| NX_SECURE_TLS_INAPPROPRIATE_FALLBACK               | 0x147  | リモート クライアントが、不適切な TLS バージョン ダウングレードを試行しました。                                                                                               |
| NX_SECURE_TLS_BAD_CLIENTHELLO_PSK_EXTENSION      | 0x148  | リモート クライアントからの TLS 1.3 PSK 拡張機能内で、予期しなかったものが、そのクライアントによって提供されました。                                                              |
| NX_SECURE_TLS_PSK_BINDER_MISMATCH                 | 0x149  | リモート クライアントからの TLS 1.3 PSK 拡張機能内で、無効な PSK バインダー値がそのクライアントによって提供されました。                                                                  |
| NX_SECURE_TLS_CRYPTO_KEYS_TOO_LARGE              | 0x14A  | TLS セッション キーを生成しようとしましたが、キー バッファーが小さすぎました - NX_SECURE_TLS_KEY_MATERIAL_SIZE を増やしてください。                                     |
| NX_SECURE_TLS_UNSUPPORTED_ECC_CURVE               | 0x14B  | リモート ホストが証明書を提供したか、サポートされていない ECC 曲線の暗号スイートを選択しました。                                                         |
| NX_SECURE_TLS_UNSUPPORTED_ECC_FORMAT              | 0x14C  | サポートされていない曲線の種類または ECC 形式が見つかりました。                                                                                                 |
| NX_SECURE_TLS_UNSUPPORTED_SIGNATURE_ALGORITHM     | 0x14D  | サポートされていない署名アルゴリズムが見つかりました （キー交換またはその他の証明書以外の状況で使用）。                                                |
| NX_SECURE_TLS_SIGNATURE_VERIFICATION_ERROR        | 0x14E  | 署名検証チェックに失敗しました （キー交換またはその他の証明書以外の状況で使用）。                                                                    |
| NX_SECURE_TLS_UNEXPECTED_MESSAGE                   | 0x14F  | TLS がリモート ホストから予期しないメッセージを受信しました。                                                                                                      |
| NX_SECURE_TLS_AEAD_DECRYPT_FAIL                   | 0x150  | 受信レコードは、AEAD 暗号による整合性チェックに合格しませんでした。                                                                                            |
| NX_SECURE_TLS_RECORD_OVERFLOW                      | 0x151  | 受信した TLSCiphertext レコードの長さが長すぎました。                                                                                                   |
| NX_SECURE_TLS_HANDSHAKE_FRAGMENT_RECEIVED         | 0x152  | 断片化されたハンドシェイク メッセージを受信しました - より高いレベルのステート マシンで適切なアクションを実行してください。                                                     |

| エラー名                                             | 値  | 説明                                                                                                                                                    |
| ---------------------------------------------------------- | ---------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| NX_SECURE_TLS_SUCCESS                               | 0x00   | 関数が正常に返されました （NX_SUCCESS と同じ）。                                                                                                         |
| NX_SECURE_TLS_SESSION_UNINITIALIZED                | 0x101  | 初期化されていないソケットを伴って TLS メイン ループが呼び出されました。                                                                                                               |
| NX_SECURE_TLS_UNRECOGNIZED_MESSAGE_TYPE           | 0x102  | TLS レコード レイヤーが認識できないメッセージ型を受け取りました。                                                                                                       |
| NX_SECURE_TLS_INVALID_STATE                        | 0x103  | 内部エラー - 状態が認識されません。                                                                                                                        |
| NX_SECURE_TLS_INVALID_PACKET                       | 0x104  | 内部エラー - 受信パケットに TLS データが含まれていませんでした。                                                                                                    |
| NX_SECURE_TLS_UNKNOWN_CIPHERSUITE                  | 0x105  | 選択した暗号スイートはサポートされていません - サーバーの内部エラーです。クライアントの場合は、リモート ホストが無効な暗号スイート （エラーまたは攻撃） を送信したことを意味します。            |
| NX_SECURE_TLS_UNSUPPORTED_CIPHER                   | 0x106  | 暗号化または解読の実行中、選択されている暗号は無効になっているか、使用できません。                                                                           |
| NX_SECURE_TLS_HANDSHAKE_FAILURE                    | 0x107  | ハンドシェイク中、メッセージ処理で問題が発生しました。                                                                                              |
| NX_SECURE_TLS_HASH_MAC_VERIFY_FAILURE            | 0x108  | 受信レコードに、生成されたものと一致しない MAC がありました。                                                                                         |
| NX_SECURE_TLS_TCP_SEND_FAILED                     | 0x109  | 何らかの理由により、レコードの発信 TCP 送信に失敗しました。                                                                                                     |
| NX_SECURE_TLS_INCORRECT_MESSAGE_LENGTH            | 0x10A  | 受信メッセージの長さが正しくありませんでした （通常は、証明書メッセージのように、ヘッダー内の 1 以外の長さ）                                |
| NX_SECURE_TLS_BAD_CIPHERSPEC                       | 0x10B  | 受信 ChangeCipherSpec メッセージが正しくありませんでした。                                                                                                           |
| NX_SECURE_TLS_INVALID_SERVER_CERT                 | 0x10C  | 受信サーバー証明書が正しく解析されませんでした。                                                                                                       |
| NX_SECURE_TLS_UNSUPPORTED_PUBLIC_CIPHER           | 0x10D  | サーバーが提供した証明書によって、サポートされていない公開キー操作が指定されました。                                                                        |
| NX_SECURE_TLS_NO_SUPPORTED_CIPHERS                | 0x10E  | サポートされている暗号スイートがない ClientHello を受信しました。                                                                                                        |
| NX_SECURE_TLS_UNKNOWN_TLS_VERSION                 | 0x10F  | 受信レコードに、認識されない TLS バージョンがありました。                                                                                                   |
| NX_SECURE_TLS_UNSUPPORTED_TLS_VERSION             | 0x110  | 受信レコードに有効な TLS バージョンがありましたが、サポートされていないものです。                                                                                     |
| NX_SECURE_TLS_ALLOCATE_PACKET_FAILED              | 0x111  | TLS メッセージに対する内部パケットの割り当てに失敗しました。                                                                                                        |
| NX_SECURE_TLS_INVALID_CERTIFICATE                  | 0x112  | X509 証明書が正しく解析されませんでした。                                                                                                                  |
| NX_SECURE_TLS_NO_CLOSE_RESPONSE                   | 0x113  | TLS セッションの終了中、リモート ホストから CloseNotify を受信しませんでした。                                                                               |
| NX_SECURE_TLS_ALERT_RECEIVED                       | 0x114  | リモート ホストが、エラーを示して接続を終了するアラートを送信しました。                                                                                |
| NX_SECURE_TLS_FINISHED_HASH_FAILURE               | 0x115  | 受信した Finish メッセージ ハッシュが、ローカルで生成されたハッシュと一致しません - ハンドシェイクの破損。                                                              |
| NX_SECURE_TLS_UNKNOWN_CERT_SIG_ALGORITHM         | 0x116  | 検証中の証明書に、サポートされていない署名アルゴリズムがありました。                                                                                     |
| NX_SECURE_TLS_CERTIFICATE_SIG_CHECK_FAILED       | 0x117  | 証明書の署名検証チェックに失敗しました - 証明書データが署名と一致しませんでした。                                                                 |
| NX_SECURE_TLS_BAD_COMPRESSION_METHOD              | 0x118  | サポートされていない圧縮方法が使用された Hello メッセージを受信しました。                                                                                              |
| NX_SECURE_TLS_CERTIFICATE_NOT_FOUND               | 0x119  | 証明書リストの操作で、一致する証明書が見つかりませんでした。                                                                                     |
| NX_SECURE_TLS_INVALID_SELF_SIGNED_CERT           | 0x11A  | リモート ホストが自己署名証明書を送信しましたが、NX_SECURE_ALLOW_SELF_SIGNED_CERTIFICATES が定義されていません。                                              |
| NX_SECURE_TLS_ISSUER_CERTIFICATE_NOT_FOUND       | 0x11B  | リモート証明書を受信しましたが、ローカルの信頼されたストアに発行者がありません。                                                                              |
| NX_SECURE_TLS_OUT_OF_ORDER_MESSAGE               | 0x11C  | DTLS メッセージを間違った順序で受信しました - 破棄されたデータグラムが原因である可能性があります。                                                                    |
| NX_SECURE_TLS_INVALID_REMOTE_HOST                 | 0x11D  | 認識されないリモート ホストからパケットを受信しました。                                                                                            |
| NX_SECURE_TLS_INVALID_EPOCH                        | 0x11E  | 受信した DTLS メッセージは DTLS セッションと一致しましたが、そのエポックが間違っています。メッセージは無視する必要があります。                                                   |
| NX_SECURE_TLS_REPEAT_MESSAGE_RECEIVED             | 0x11F  | 既に示されているシーケンス番号を持つ DTLS メッセージを受信しました。無視してください。                                                                           |
| NX_SECURE_TLS_NEED_DTLS_SESSION                   | 0x120  | DTLS 用に初期化されていない DTLS API 内で TLS セッションが使用されました。                                                                                       |
| NX_SECURE_TLS_NEED_TLS_SESSION                    | 0x121  | TLS ではなく DTLS 用に初期化された TLS API 内で TLS セッションが使用されました。                                                                                |
| NX_SECURE_TLS_SEND_ADDRESS_MISMATCH               | 0x122  | 呼び出し元が、DTLS セッションと一致しなかった IP アドレスまたはポートを使用して、そのセッションを介してデータを送信しようとしました。                                                  |
| NX_SECURE_TLS_NO_FREE_DTLS_SESSIONS              | 0x123  | 新しい接続がキャッシュから DTLS セッションを取得しようとしましたが、空きがありませんでした。                                                                        |
| NX_SECURE_DTLS_SESSION_NOT_FOUND                  | 0x124  | 呼び出し元は DTLS セッションを検索しましたが、指定された IP アドレスとポートはキャッシュ内のどのエントリとも一致しませんでした。                                             |
| NX_SECURE_TLS_NO_MORE_PSK_SPACE                  | 0x125  | 呼び出し元が TLS セッションに PSK を追加しようとしましたが、指定されたセッション内に領域がありませんでした。                                                          |
| NX_SECURE_TLS_NO_MATCHING_PSK                     | 0x126  | リモート ホストによって、ローカル ストア内のいずれにも一致しない PSK ID ヒントが提供されました。                                                                         |
| NX_SECURE_TLS_CLOSE_NOTIFY_RECEIVED               | 0x127  | TLS セッションが、セッション完了を示す CloseNotify アラートをリモートホストから受信しました。                                                           |
| NX_SECURE_TLS_NO_AVAILABLE_SESSIONS               | 0x128  | 接続の処理に使用できる TLS セッションが、TLS オブジェクト内にありません。                                                                                         |
| NX_SECURE_TLS_NO_CERT_SPACE_ALLOCATED            | 0x129  | 証明書領域が、受信リモート証明書に対して割り当てられていませんでした。                                                                                          |
| NX_SECURE_TLS_PADDING_CHECK_FAILED                | 0x12A  | 着信メッセージ内の暗号化パディングが正しくありませんでした。                                                                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_TYPE         | 0x12B  | CertificateVerifyRequest の処理中、サポートされている証明書の種類がリモート サーバーによって提供されませんでした。                                                    |
| NX_SECURE_TLS_UNSUPPORTED_CERT_SIGN_ALG          | 0x12C  | CertificateVerifyRequest の処理中、サポートされている署名アルゴリズムがリモート サーバーによって提供されませんでした。                                                 |
| NX_SECURE_TLS_INSUFFICIENT_CERT_SPACE             | 0x12D  | 証明書に対して割り当てられた証明書のバッファー領域が不足しています。                                                                                              |
| NX_SECURE_TLS_PROTOCOL_VERSION_CHANGED            | 0x12E  | 受信 TLS レコード内のプロトコル バージョンが、確立されたセッションのバージョンと一致しませんでした。                                                          |
| NX_SECURE_TLS_NO_RENEGOTIATION_ERROR              | 0x12F  | HelloRequest メッセージを受信しましたが、再ネゴシエーションが行われていません。                                                                                           |
| NX_SECURE_TLS_UNSUPPORTED_FEATURE                  | 0x130  | TLS セッションまたはハンドシェイク中、無効にされた機能が見つかりました。                                                                                |
| NX_SECURE_TLS_CERTIFICATE_VERIFY_FAILURE          | 0x131  | リモート クライアントからの CertificateVerify メッセージが、クライアント証明書を確認できませんでした。                                                                     |
| NX_SECURE_TLS_EMPTY_REMOTE_CERTIFICATE_RECEIVED  | 0x132  | リモート ホストが、空の証明書メッセージを送信しました。                                                                                                            |
| NX_SECURE_TLS_RENEGOTIATION_EXTENSION_ERROR       | 0x133  | Secure Renegotation Indication 拡張機能の処理中または送信中にエラーが発生しました。                                                                      |
| NX_SECURE_TLS_RENEGOTIATION_SESSION_INACTIVE      | 0x134  | セッションの再ネゴシエーションが、アクティブでない TLS セッションで試行されました。                                                                                 |
| NX_SECURE_TLS_PACKET_BUFFER_TOO_SMALL            | 0x135  | TLS が受信したレコードが、割り当てられたパケット バッファーに対して大きすぎました。 レコードを処理できませんでした。                                                    |
| NX_SECURE_TLS_EXTENSION_NOT_FOUND                 | 0x136  | TLS ハンドシェイク中、指定された拡張機能を、リモート ホストから受信できませんでした。                                                                          |
| NX_SECURE_TLS_SNI_EXTENSION_INVALID               | 0x137  | TLS が無効な Server Name Indication 拡張機能を受信しました。                                                                                                      |
| NX_SECURE_TLS_CERT_ID_INVALID                     | 0x138  | アプリケーションがサーバー証明書を追加しようとしましたが、証明書 ID の値が無効です （0 の可能性があります）。                                                                 |
| NX_SECURE_TLS_CERT_ID_DUPLICATE                   | 0x139  | アプリケーションがサーバー証明書を追加しようとしましたが、証明書 ID がローカル ストアに既に存在します。                                                        |
| NX_SECURE_TLS_RENEGOTIATION_FAILURE                | 0x13A  | リモート ホストが、Secure Renegotiation Indication 拡張機能または SCSV 擬似暗号スイートを提供しなかったため、セキュリティで保護された再ネゴシエーションを実行できません。      |
| NX_SECURE_TLS_MISSING_CRYPTO_ROUTINE              | 0x13B  | 暗号化操作を実行しようとしているときに、暗号スイート テーブル （またはその関数ポインターの 1 つ） 内のエントリの 1 つが不適切に NULL に設定されました。 |
| NX_SECURE_TLS_EMPTY_EC_GROUP                      | 0x13C  | ECC 暗号スイートは設定されていますが、サポートされている EC グループがありません。                                                                                                             |
| NX_SECURE_TLS_EMPTY_EC_POINT_FORMAT              | 0x13D  | ECC 暗号スイートは設定されていますが、サポートされている EC ポイント形式がありません。                                                                                                      |
| NX_SECURE_TLS_BAD_SERVERHELLO_KEYSHARE            | 0x13E  | リモート サーバーからの TLS 1.3 KeyShare 拡張機能内で、予期しなかったものが、そのサーバーによって提供されました。                                                         |
| NX_SECURE_TLS_INSUFFICIENT_METADATA_SPACE         | 0x13F  | アプリケーションによって提供された TLS 暗号化ルーチン用の 「メタデータ」 が小さすぎました。                                                                             |
| NX_SECURE_TLS_POST_HANDSHAKE_RECEIVED             | 0x140  | エラーではなく、アプリケーション データを受信するまで処理を続行することを示しています。                                                                    |
| NX_SECURE_TLS_BAD_CLIENTHELLO_KEYSHARE            | 0x141  | リモート クライアントからの TLS 1.3 KeyShare 拡張機能内で、予期しなかったものが、そのクライアントによって提供されました。                                                         |
| NX_SECURE_TLS_1_3_UNKNOWN_CIPHERSUITE            | 0x142  | TLS 1.3 を使用しているときに不明な暗号スイートを受信しました。                                                                                                              |
| NX_SECURE_TLS_INVALID_SESSION_TICKET              | 0x143  | パラメーターが不適切または無効な NewSessionTicket メッセージを受信しました。                                                                                      |
| NX_SECURE_TLS_MISSING_EXTENSION                    | 0x144  | メッセージ内に特定の拡張子が見つかりません。                                                                                                                  |
| NX_SECURE_TLS_CERTIFICATE_REQUIRED                 | 0x145  | サーバーが、空の証明書を受け取りました。                                                                                                                         |
| NX_SECURE_TLS_UNEXPECTED_CLIENTHELLO               | 0x146  | TLS 1.3 Server は、再ネゴシエーション用に ClientHello を受信します。                                                                                                         |
| NX_SECURE_TLS_INAPPROPRIATE_FALLBACK               | 0x147  | リモート クライアントが、不適切な TLS バージョン ダウングレードを試行しました。                                                                                               |
| NX_SECURE_TLS_BAD_CLIENTHELLO_PSK_EXTENSION      | 0x148  | リモート クライアントからの TLS 1.3 PSK 拡張機能内で、予期しなかったものが、そのクライアントによって提供されました。                                                              |
| NX_SECURE_TLS_PSK_BINDER_MISMATCH                 | 0x149  | リモート クライアントからの TLS 1.3 PSK 拡張機能内で、無効な PSK バインダー値がそのクライアントによって提供されました。                                                                  |
| NX_SECURE_TLS_CRYPTO_KEYS_TOO_LARGE              | 0x14A  | TLS セッション キーを生成しようとしましたが、キー バッファーが小さすぎました - NX_SECURE_TLS_KEY_MATERIAL_SIZE を増やしてください。                                     |
| NX_SECURE_TLS_UNSUPPORTED_ECC_CURVE               | 0x14B  | リモート ホストが証明書を提供したか、サポートされていない ECC 曲線の暗号スイートを選択しました。                                                         |
| NX_SECURE_TLS_UNSUPPORTED_ECC_FORMAT              | 0x14C  | サポートされていない曲線の種類または ECC 形式が見つかりました。                                                                                                 |
| NX_SECURE_TLS_UNSUPPORTED_SIGNATURE_ALGORITHM     | 0x14D  | サポートされていない署名アルゴリズムが見つかりました （キー交換またはその他の証明書以外の状況で使用）。                                                |
| NX_SECURE_TLS_SIGNATURE_VERIFICATION_ERROR        | 0x14E  | 署名検証チェックに失敗しました （キー交換またはその他の証明書以外の状況で使用）。                                                                    |
| NX_SECURE_TLS_UNEXPECTED_MESSAGE                   | 0x14F  | TLS がリモート ホストから予期しないメッセージを受信しました。                                                                                                      |
| NX_SECURE_TLS_AEAD_DECRYPT_FAIL                   | 0x150  | 受信レコードは、AEAD 暗号による整合性チェックに合格しませんでした。                                                                                            |
| NX_SECURE_TLS_RECORD_OVERFLOW                      | 0x151  | 受信した TLSCiphertext レコードの長さが長すぎました。                                                                                                   |
| NX_SECURE_TLS_HANDSHAKE_FRAGMENT_RECEIVED         | 0x152  | 断片化されたハンドシェイク メッセージを受信しました - より高いレベルのステート マシンで適切なアクションを実行してください。                                                     |

**表 1 - NetX Secure TLS エラーのリターン コード**

## <a name="netx-secure-x509-return-codes"></a>NetX Secure X.509 のリターン コード

以下の表 2 は、NetX Secure X.509 サービスによって返される可能性があるエラー コードを示しています。 他のエラー コードがサービスによって返される可能性があることにも注意してください。 X.509 戻り値は 0x181 から、TLS 値は 0x101 から始まります。また、TCP/IP 値は 0x100 未満です。 TCP/IP の戻り値については、NetX TCP/IP のドキュメントをご覧ください。TLS の戻り値については、上記をご覧ください。

| エラー名                                   | 値 | 説明                                                                                                        |
| ------------------------------------------------ | --------- | ---------------------------------------------------------------------------------------------------------------------- |
| NX_SECURE_X509_SUCCESS                        | 0x00      | 正常なリターン状態 （NX_SUCCESS と同じです）。                                                                        |
| NX_SECURE_X509_MULTIBYTE_TAG_UNSUPPORTED    | 0x181     | マルチバイト ASN.1 タグが見つかりました - 現在サポートされていません。                                                       |
| NX_SECURE_X509_ASN1_LENGTH_TOO_LONG        | 0x182     | 処理できる長さを超える長さの値が見つかりました。                                                                  |
| NX_SECURE_X509_FOUND_NON_ZERO_PADDING      | 0x183     | 埋め込み値 0 が必要ですが、異なるものを取得しました。                                                               |
| NX_SECURE_X509_MISSING_PUBLIC_KEY           | 0x184     | X509 には公開キーが必要ですが、見つかりませんでした。                                                                        |
| NX_SECURE_X509_INVALID_PUBLIC_KEY           | 0x185     | 公開キーが見つかりましたが、無効であるか、形式が正しくありません。                                                      |
| NX_SECURE_X509_INVALID_CERTIFICATE_SEQUENCE | 0x186     | 最上位レベルの ASN.1 ブロックはシーケンスではありません - 無効な X509 証明書。                                                |
| NX_SECURE_X509_MISSING_SIGNATURE_ALGORITHM  | 0x187     | 署名アルゴリズム識別子が必要ですが、見つかりませんでした。                                                           |
| NX_SECURE_X509_INVALID_CERTIFICATE_DATA     | 0x188     | 証明書 ID データの形式が無効です。                                                                     |
| NX_SECURE_X509_UNEXPECTED_ASN1_TAG          | 0x189     | X509 形式に特定の ASN.1 タグが必要でしたが、別のものを取得しました。                                      |
| NX_SECURE_PKCS1_INVALID_PRIVATE_KEY         | 0x18A     | PKCS#1 秘密キー ファイルが渡されましたが、形式が正しくありませんでした。                                            |
| NX_SECURE_X509_CHAIN_TOO_SHORT              | 0x18B     | X509 証明書チェーンが短すぎて、チェーン構築中にチェーン全体を保持できませんでした。                                |
| NX_SECURE_X509_CHAIN_VERIFY_FAILURE         | 0x18C     | X509 証明書チェーンを検証できませんでした （キャッチオール エラー）。                                                 |
| NX_SECURE_X509_PKCS7_PARSING_FAILED         | 0x18D     | X.509 PKCS#7 でエンコードされた署名の解析に失敗しました。                                                                     |
| NX_SECURE_X509_CERTIFICATE_NOT_FOUND        | 0x18E     | 証明書を検索しているときに、一致するエントリが見つかりませんでした。                                                              |
| NX_SECURE_X509_INVALID_VERSION               | 0x18F     | 指定されたバージョンと互換性のないフィールドが証明書に含まれていました。                                           |
| NX_SECURE_X509_INVALID_TAG_CLASS            | 0x190     | 無効なタグ クラス値を持つ ASN.1 タグが証明書に含まれていました。                                                   |
| NX_SECURE_X509_INVALID_EXTENSIONS            | 0x191     | 拡張機能 TLV が証明書に含まれていましたが、シーケンスは含まれていませんでした。                                          |
| NX_SECURE_X509_INVALID_EXTENSION_SEQUENCE   | 0x192     | 無効な X.509 である拡張シーケンスが証明書に含まれていました。                                                   |
| NX_SECURE_X509_CERTIFICATE_EXPIRED           | 0x193     | 現在の時刻よりも前の 「期間の終了時刻」 フィールドが証明書にありました。                                             |
| NX_SECURE_X509_CERTIFICATE_NOT_YET_VALID   | 0x194     | 現在の時刻よりも後の 「期間の開始時刻」 フィールドが証明書にありました。                                         |
| NX_SECURE_X509_CERTIFICATE_DNS_MISMATCH     | 0x195     | 証明書共通名またはサブジェクト代替名が、指定された DNS TLD と一致しませんでした。                                           |
| NX_SECURE_X509_INVALID_DATE_FORMAT          | 0x196     | 認識される形式ではない日付フィールドが証明書に含まれていました。                                               |
| NX_SECURE_X509_CRL_ISSUER_MISMATCH          | 0x197     | 指定された CRL と証明書は、同じ証明機関によって発行されたものではありません。                                      |
| NX_SECURE_X509_CRL_SIGNATURE_CHECK_FAILED  | 0x198     | 発行者に対する CRL 署名チェックに失敗しました。                                                                       |
| NX_SECURE_X509_CRL_CERTIFICATE_REVOKED      | 0x199     | 証明書は有効な CRL 内で見つかったため、失効しました。                                                 |
| NX_SECURE_X509_WRONG_SIGNATURE_METHOD       | 0x19A     | 署名を検証しようとしているときに、署名メソッドが、予期されたメソッドと一致しませんでした。                          |
| NX_SECURE_X509_EXTENSION_NOT_FOUND          | 0x19B     | 拡張機能を探しているときに、ID が一致する拡張機能が見つかりませんでした。                                                |
| NX_SECURE_X509_ALT_NAME_NOT_FOUND          | 0x19C     | subjectAltName 拡張機能内で名前が検索されましたが、見つかりませんでした。                                               |
| NX_SECURE_X509_INVALID_PRIVATE_KEY_TYPE    | 0x19D     | 指定された秘密キーの種類が不明または無効でした。                                                                         |
| NX_SECURE_X509_NAME_STRING_TOO_LONG        | 0x19E     | 渡された名前文字列が、内部バッファー （DNS 名など） に対して長すぎました。                                        |
| NX_SECURE_X509_EXT_KEY_USAGE_NOT_FOUND    | 0x19F     | 拡張キー使用拡張機能を検索しているときに、指定されたキー使用 OID が見つかりませんでした。                               |
| NX_SECURE_X509_KEY_USAGE_ERROR              | 0x1A0     | 証明書の検証チェック中、キーの使用に失敗した場合に、アプリケーション コールバックによって返されます。 |

**表 2 - NetX Secure X.509 エラーのリターン コード**
