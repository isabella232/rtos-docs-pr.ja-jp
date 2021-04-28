---
title: 第 1 章 - Azure RTOS NetX Duo MQTT の概要
description: NetX Duo MQTT クライアント パッケージを使用するには、NetX Duo (バージョン 5.10 以降) がインストールされ、適切に構成されていることと、IP インスタンスが作成されていることが必要です。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 2e13b997f987e2fd82569bcb1904218908313d70
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810727"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-mqtt"></a>第 1 章 - Azure RTOS NetX Duo MQTT の概要

## <a name="netx-duo-mqtt-requirements"></a>NetX Duo MQTT の要件

Azure RTOS NetX Duo MQTT クライアント パッケージを使用するには、NetX Duo (バージョン 5.10 以降) がインストールされて適切に構成されていて、IP インスタンスが作成されている必要があります。 システムで TCP モジュールが有効になっている必要があります。 さらに、TLS セキュリティが必要な場合は、ブローカーが必要とするセキュリティ パラメーターに従って NetX Secure TLS モジュールを構成する必要があります。

## <a name="netx-duo-mqtt-specification"></a>NetX Duo MQTT の仕様

NetX Duo MQTT クライアントの実装は、OASIS MQTT バージョン 3.1.1 (2014 年 10 月 29 日) に準拠しています。<sup></sup> この仕様は次の場所にあります。

- [http://mqtt.org/](http://mqtt.org/)

## <a name="netx-duo-mqtt-basic-operation"></a>NetX Duo MQTT の基本的な動作

MQTT (メッセージ キュー テレメトリ転送) は、パブリッシャー/サブスクライバー モデルに基づいています。 クライアントは、ブローカーを介して他のクライアントに情報を公開できます。 クライアントは、トピックに関心がある場合、そのトピックをブローカーを通じてサブスクライブできます。 ブローカーの役割は、公開されたメッセージを、トピックをサブスクライブしているクライアントに配信することです。 このパブリッシャー/サブスクライバー モデルでは、複数のクライアントが同じトピックのデータを公開できます。 クライアントは、同じトピックをサブスクライブしている場合、自身が公開するメッセージを受信することになります。

クライアントは、ユース ケースに応じて、メッセージの公開時に 3 つの QoS レベルのいずれかを選択できます。

- **QoS 0**: メッセージは最大で 1 回配信されます。 QoS 0 で送信されるメッセージは失われる可能性があります。
- **QoS 1**: メッセージは少なくとも 1 回配信されます。 QoS 1 で送信されるメッセージは、複数回配信される可能性があります。
- **QoS 2**: メッセージは 1 回だけ配信されます。 QoS 2 で送信されるメッセージは、重複することなく配信されることが保証されます。

> [!NOTE]
> この MQTT クライアントの実装では、QoS レベル 2 のメッセージはサポートされません。

QoS 1 と QoS 2 では配信されることが保証されるため、ブローカーは、各クライアントに送信された QoS 1 と QoS 2 のメッセージの状態を追跡します。 これは、QoS1 または QoS 2 のメッセージを想定しているクライアントにとって特に重要です。 クライアントは、(たとえば、クライアントが再起動したときや通信リンクが一時的に失われたときに) ブローカーから切断される可能性があります。 ブローカーは、クライアントがブローカーに再接続されたらメッセージを配信できるように QoS 1 と QoS 2 のメッセージを格納する必要があります。 ただし、クライアントは、再接続後にブローカーから古いメッセージを受信しないことを選択できます。 クライアントは、そのために、*clean_session* フラグを ***NX_TRUE** _ に設定して接続を開始します。 この場合、ブローカーは、MQTT CONNECT メッセージの受信時に、未配信または未確認の QoS 1 または QoS 2 メッセージを含む、このクライアントに関連付けられたすべてのセッション情報を破棄する必要があります。 _clean_session* フラグが ***NX_FALSE**_ に設定されている場合、サーバーは QoS 1 および QoS 2 メッセージを再送信する必要があります。 また、_clean_session* が ***NX_TRUE*** に設定されている場合、MQTT クライアントは、未確認メッセージを再送信します。 この受信確認は TCP 層の ACK とは異なりますが、同様に発生します。 MQTT クライアントは、受信確認をブローカーに送信します。

アプリケーションは、***nxd_mqtt_client_create()** _ を呼び出して MQTT クライアント インスタンスを作成します。 クライアントが作成されると、アプリケーションは _*_nxd_mqtt_client_connect()_*_ を呼び出すことによってブローカーに接続できます。 ブローカーに接続した後、クライアントは、_*_nxd_mqtt_client_subscribe()_*_ を呼び出してトピックをサブスクライブすることも、_*_nxd_mqtt_client_publish()_ ** を呼び出してトピックを公開することもできます。

受信した MQTT メッセージは、MQTT クライアント インスタンスの受信キューに格納されます。 アプリケーションは、***nxd_mqtt_client_message_get()*** を呼び出すことによって、これらのメッセージを取得します。 受信キューにメッセージがある場合、キューの最初のメッセージ (たとえば、最も古いメッセージ) が呼び出し元に返されます。 メッセージのトピック文字列も返されます。

> [!NOTE]
> MQTT クライアントの受信キューが空の場合、***nxd_mqtt_client_message_get()** _ 関数はブロックされません。 この関数は、リターン コード _*_NXD_MQTT_NO_MESSAGE_** と共に即座に返されます。 アプリケーションでは、この戻り値を、エラーではなく、受信キューが空であることを示すものとして処理されます。

アプリケーションでは、受信メッセージ用の受信キューのポーリングを回避するために、***nxd_mqtt_client_recieve_notify_set()*** を呼び出すことによって、コールバック関数を MQTT クライアントに登録できます。 コールバック関数は次のように宣言されます。

```c
VOID (*receive_notify_callback)(NXD_MQTT_CLIENT *client_ptr, 
    UINT message_count);
```

MQTT クライアントは、ブローカーからメッセージを受信すると、コールバック関数を呼び出します (関数が設定されている場合)。 このコールバック関数は、クライアント制御ブロックを指すポインターとメッセージ カウント値を渡します。 メッセージ カウント値は、受信キュー内の MQTT メッセージの数を示します。 このコールバック関数は MQTT クライアント スレッドのコンテキストで実行されることに注意してください。 そのため、コールバック関数では、MQTT クライアント スレッドをブロックする可能性のあるプロシージャは実行しないでください。 コールバック関数により、***nxd_mqtt_client_message_get()*** を呼び出してメッセージを取得するアプリケーション スレッドがトリガーされます。

MQTT クライアント サービスを切断して終了するには、アプリケーションでサービスの ***nxd_mqtt_client_disconnect()** _ と _*_nxd_mqtt_client_delete()_*_ を使用する必要があります。 _*_nxd_mqtt_client_disconnect()_*_ を呼び出した場合は、ブローカーへの TCP 接続が切断されるだけです。 既に受信されて受信キューに格納されているメッセージは解放されます。 ただし、送信キューにある QoS レベル 1 のメッセージは解放されません。 QoS レベル 1 のメッセージは、接続時に再送信されます (_*_clean_session_*_ フラグが _ *_NX_FALSE_** に設定されていると想定)。

ブローカーは、クライアントから切断することもできます。 クライアントとブローカーの間の TCP 接続が終了すると、切断通知機能でアプリケーションに通知できます。 この通知メカニズムを使用するには、アプリケーションで ***nxd_mqtt_client_disconnect_notify_set*** を呼び出して、切断通知機能をインストールします。 TCP 切断が確認され、MQTT セッションが作成されていると、通知機能が呼び出されます。

***nxd_mqtt_client_delete()*** を呼び出すと、送信キューと受信キュー内のすべてのメッセージ ブロックが解放されます。 未確認の QoS レベル 1 のメッセージも削除されます。

## <a name="secure-mqtt-connection"></a>セキュリティで保護された MQTT 接続

MQTT クライアントは、NetX Secure TLS モジュールを使用して、ブローカーへのセキュリティで保護された接続を確立します。 TLS セキュリティを使用する MQTT の既定のポート番号は 8883 で、***NXD_MQTT_TLS_PORT*** で定義されています。

ブローカーへのセキュリティで保護された MQTT 接続を作成するには、TCP 接続が確立されてから MQTT CONNECT メッセージをブローカーに送信するまでに、TLS セッションをネゴシエートする必要があります。 TLS セッションの設定を行うには、***nxd_mqtt_client_secure_connect()*** を呼び出し、ユーザー定義の TLS 設定コールバック関数を渡します。 MQTT 接続フェーズでは、TCP 接続が確立されると、クライアントが TLS 設定コールバック関数を呼び出して、適切な TLS ハンドシェイク プロセスを開始します。 TLS セッションが確立された後、クライアントは、セキュリティで保護されたチャネルを介して MQTT CONNECT メッセージを続行します。

ユーザー定義のコールバック関数は、5 つの入力値を受け取り、次のように宣言されます。

```c
UINT tls_Setup_callback(NXD_MQTT_CLIENT *client_ptr,
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certificate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_cerfiticate);
```

入力パラメーターの説明を以下に示します。

- **client_ptr**: MQTT クライアント制御ブロックを指すポインター。
- **session_ptr**: TLS セッション制御ブロックを指すポインター。
- **certificate_ptr**: 証明書制御ブロックを指すポインター。 この証明書は、ブローカーに送信される前に設定関数によって構成されます。
- **trusted_certificate_ptr**: 信頼できる証明書を指すポインター。 TLS 設定関数は、サーバーを認証するために信頼できる証明書を構成します。

この TLS 設定関数において、アプリケーションの役割は、TLS セッションを作成し、適切な証明書を使用してそのセッションを構成することです。 次の擬似コードは、一般的な TLS セッションの開始手順を示しています。 TLS API シリーズの使用の詳細については、『NetX Secure TLS ユーザー ガイド』を参照してください。

TLS 設定コールバックの例を以下に示します。

```c
UINT tls_setup_callback(NXD_MQTT_CLIENT *client_pt
    NX_SECURE_TLS_SESSION *session_ptr,
    NX_SECURE_TLS_CERTIFICATE *certrifcate_ptr,
    NX_SECURE_TLS_CERTIFICATE *trusted_certificate_ptr)
{
    /* Initialize TLS module */
    nx_secure_tls_initialize();

    /* Create a TLS session */
    nx_secure_tls_session_create(session_ptr, …);

    /* Need to allocate space for the certificate coming in from the broker. */
    memset(certificate_ptr), 0, sizeof(NX_SECURE_TLS_CERTIFICATE));

    nx_secure_tls_remote_certificate_allocate(session_ptr, certificate_ptr);

    /* Add a CA Certificate to our trusted store for verifying incomingserver certificates. */
    nx_secure_tls_certificate_initialize(
        trusted_certificate_ptr,
        ca_cert_der,
        ca_cert_der_len, NULL, 0);
    nx_secure_tls_trusted_certificate_add(session_ptr,
        trusted_certificate));
}
```

## <a name="known-limitations-of-the-netx-duo-mqtt-client"></a>NetX Duo MQTT クライアントの既知の制限事項

- NetX Duo MQTT では、QoS レベル 2 のメッセージの送受信がサポートされていません。
- NetX Duo MQTT では、連鎖パケットがサポートされていません。
