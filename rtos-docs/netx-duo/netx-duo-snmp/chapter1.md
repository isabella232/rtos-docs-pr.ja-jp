---
title: チャプター 1 - Azure RTOS NetX Duo SNMP の概要
description: NetX Duo SNMP は SNMP エージェントにより実装されています。 エージェントによって SNMP マネージャーのコマンドに応答し、イベント トラップを送信します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810598"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a>チャプター 1 - Azure RTOS NetX Duo SNMP の概要

Simple Network Management Protocol (SNMP) は、インターネット上のデバイスを管理するために設計されたプロトコルです。 SNMP は、コネクションレスのユーザー データグラム プロトコル (UDP) サービスを使用して管理機能を実行するプロトコルです。 Azure RTOS NetX Duo SNMP は SNMP エージェントにより実装されています。 エージェントによって SNMP マネージャーのコマンドに応答し、イベント トラップを送信します。 

NetX Duo SNMP は、SNMP マネージャーとの通信で IPv4 と IPv6 の両方をサポートしています。 NetX SNMP アプリケーションは、NetX Duo SNMP でコンパイルして実行するべきです。 ただし、開発者の方には、既存の SNMP アプリケーションを、対応する “duo” サービスを使用できるように移植することを推奨します。 たとえば、SNMP トラップ メッセージを送信するときは、次の “duo” サービスで、対応する NetX サービスを置き換えます:

*nxd_snmp_object_trap_send*

*nxd_snmp_object_trapv2_send*

*nxd_snmp_object_trapv3_send*

詳細は、このユーザー ガイドの「**SNMP エージェントのサービスの説明**」をご覧ください。

## <a name="netx-duo-snmp-agent-requirements"></a>NetX Duo SNMP エージェントの要件

NetX Duo SNMP パッケージを使用するには、IP インスタンスを作成しておく必要があります。 さらに、その IP インスタンスで UDP を有効にする必要があります。

NetX Duo SNMP エージェントには、いくつかの追加要件があります。 まず、SNMP マネージャーのすべての要求を処理するために、ポート 161 へのアクセスが必要です。 また、トラップ メッセージをマネージャーに送信するために、ポート 162 へのアクセスが必要です。

IPv6 で NetX Duo SNMP エージェントを使用して IPv6 オブジェクトを取得するには、NetX Duo で IPv6 を有効にする必要があります。 IPv6 サービスで IP インスタンスを有効にする方法の詳細は『***Netx Duo ユーザー ガイド***』をご覧ください。

## <a name="netx-duo-snmp-constraints"></a>NetX Duo SNMP の制約

NetX Duo SNMP プロトコルでは、SNMP version 1、2、3 を実装しています。 SNMPv3 の実装では、MD5 認証、SHA 認証、DES 暗号化をサポートしています。 このバージョンの NetX Duo SNMP エージェントには次の制約があります:

1. NetX IP インスタンス 1 つにつき SNMP エージェントは 1 つだけです
2. RMON をサポートしていません
3. SNMPv3 の Inform メッセージをサポートしていません
4. OPAQUE と NSAP のデータ型をサポートしていません
5. IPv6 アドレスをオクテット文字列で指定し、形式のチェックはアプリケーションに任されています。

## <a name="snmp-object-names"></a>SNMP オブジェクトの名前

SNMP プロトコルはインターネット上のデバイスを管理するように設計されています。 この目的のために、SNMP で管理するデバイスにはそれぞれ、RFC 1155 で定義されている管理情報構造 (SMI) で定義するオブジェクトのセットが存在します。 管理情報構造は、次のような階層ツリー型の構造です:

![管理情報構造の図。](media/image3.png)

ツリーの各ノードはオブジェクトです。 ツリーの “dod” オブジェクトは 1.3.6 の標識によって、“internet” オブジェクトは 1.3.6.1 の標識によって識別されます。 SNMP オブジェクトの名前はすべて 1.3.6 で始まります。

SNMP マネージャーは、このオブジェクト命名法を使用して、取得または設定するデバイス上のオブジェクトを指定します。 NetX Duo SNMP エージェントはマネージャーのそうした要求を解釈し、要求された操作をアプリケーションで実行する仕組みを提供します。

## <a name="snmp-manager-requests"></a>SNMP マネージャーの要求

SNMP には、デバイスを管理するシンプルな仕組みがあります。 SNMP には、SNMP マネージャーが *ポート 161* を使用して SNMP デバイスに発行する、標準 SNMP コマンドのセットが存在します。 SNMP マネージャーの基本的なコマンドの一部を次に挙げます:

| SNMP コマンド | 意味                                                        |
|--------------|----------------------------------------------------------------|
| GET          | *指定したオブジェクトを取得します*                                       |
| GETNEXT      | *指定したオブジェクト ID の次の論理オブジェクトを取得します*      |
| GETBULK      | *指定したオブジェクト ID より後にある複数の論理オブジェクトを取得します* |
| SET          | *指定したオブジェクトを設定します*                                       |

これらのコマンドは抽象構文記法 1 (ASN.1) 形式でエンコードされ、SNMP マネージャーから送信される UDP パケットのペイロードに存在します。 NetX Duo SNMP エージェント は、要求を処理してから、***nx_snmp_agent_create*** の呼び出しで指定された、対応する処理ルーチンを呼び出します。

## <a name="netx-duo-snmp-agent-traps"></a>NetX Duo SNMP エージェント トラップ

NetX Duo SNMP エージェント によって、SNMP マネージャーに非同期でイベントのアラートを送ることができます。 これは SNMP トラップ コマンドで実行します。 SNMP マネージャーにトラップを送信するために、SNMP の各バージョンには固有の API が用意されています。 既定では、トラップはSNMP マネージャーのポート 162 に送信されます。

NetX Duo SNMP エージェント では、SNMPv3 のトラップ メッセージに個別のセキュリティ キーを使用します。 そのため、SNMP アプリケーションでは、マネージャーの要求への応答に使用するもキーとは別に、キーのセットを作成する必要があります。 トラップのセキュリティにより、SNMP エージェントでは、認証用とプライバシー用で同じパスワードと異なるパスワードのどちらも使用できます。 セキュリティ キー作成の詳しい情報は、次のセクションの「**Netx Duo SNMP 認証および暗号化**」をご覧ください。

標準の SNMP トラップ変数は *nxd_snmp.h* の冒頭に列挙されています:

| 変数                                 | 値  |
|-------------------------------------------|---|
| #NX_SNMP_TRAP_COLDSTART を有効            | 0 |
| #NX_SNMP_TRAP_WARMSTART を有効化            | 1 |
| #NX_SNMP_TRAP_LINKDOWN を有効化             | 2 |
| #NX_SNMP_TRAP_LINKUP を有効化               | 3 |
| #NX_SNMP_TRAP_AUTHENTICATE_FAILURE を有効化 | 4 |
| #NX_SNMP_TRAP_EGPNEIGHBORLOSS を有効化      | 5 |
| #NX_SNMP_TRAP_ENTERPRISESPECIFIC を有効化   | 6 |

これらの変数をトラップ メッセージに含めるには、ここに列挙されている値を、各変数に対応する値として、*nx_snmp_agent_trapv2_send* (SNMPv2) または *nx_snmp_agent_trapv3_send* (SNMPv3) の trap_type 引数に入力します。 下に示すのは、SNMPv2 で SNMP マネージャーにコールド スタートのイベントを通知する例です:

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

独自の変数をトラップ メッセージに含めるには、trap_type 引数を NX_SNMP_TRAP_CUSTOM に設定して、トラップ リストの引数に独自のデータを入力します。 トラップ メッセージにはシステムのアップタイム (1.3.6.1.6.3.1.1.4.1.0) が含まれます。 次に SNMPv2 の例を示します:

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a>NetX Duo SNMP 認証および暗号化

認証には *Basic* と *Digest* の 2 種類があります。 Basic 認証は、多くのプロトコルで使用される、プレーン テキストを用いた単純な *ユーザー名* 認証と同等の認証です。 SNMP の Basic 認証では、渡されたユーザー名が SNMP 操作を実行するために有効であることを確認するだけです。 SNMP バージョン 1 と 2 では、Basic 認証だけを使用できます。

Basic 認証の主な欠点はユーザー名をプレーン テキストで送信することです。 SNMPv3 の Digest 認証では、ユーザー名をプレーン テキストで送信しないことによって、この問題に対処しています。 代わりに、アルゴリズムを使用して、ユーザー名、コンテキスト エンジンなどの情報から 96 ビットの “ダイジェスト” を生成します。 NetX Duo SNMP エージェント は、MD5 と SHA のダイジェスト アルゴリズムを両方サポートしています。

認証を有効にするには、SNMP エージェントで *nx_snmp_agent_context_engine_set* サービスを使用してコンテキスト エンジン ID を設定する必要があります。 コンテキスト エンジン ID は、認証キーの作成に使用します。

SNMPv3 のデータは DES アルゴリズムを使用して暗号化できます。 暗号化するには認証を有効にする必要があります (認証のパラメーターを設定しないとデータを暗号化できません)。

認証キーとプライバシー キーを作成するには次の API を使用します:

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

次に、これらのキーを使用するように SNMP エージェントを構成する必要があります。 キーを SNMP エージェントに登録するには次の API を使用します:

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

トラップ メッセージには個別のキーを作成できます。 トラップ メッセージ用のキーを使用するには次の API を使用します:

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

応答メッセージとトラップ送信の認証または暗号化を無効にするには、キー ポインターの入力を NULL に設定してこれらのサービスを使用します。

## <a name="netx-duo-snmp-community-strings"></a>NetX Duo SNMP コミュニティ文字列

NetX Duo SNMP エージェント は、パブリックとプライベート両方のコミュニティ文字列をサポートしています。 パブリック文字列は *nx_snmp_agent _public_string_set* サービスで設定します。 NetX Duo SNMP エージェント のプライベート文字列は *nx_snmp_agent_private_string_set* サービスを使用して設定します。

## <a name="netx-duo-snmp-username-callback"></a>NetX Duo SNMP ユーザー名コールバック

NetX Duo SNMP エージェント パッケージでは、アプリケーションで、SNMP クライアントの各要求の処理を開始するときに呼び出すユーザー名コールバックを指定できます (***nx_snmp_agent_create*** を呼び出すことで指定します)。

コールバック ルーチンで、NetX Duo SNMP エージェント にユーザー名を渡します。 渡されたユーザー名が有効である場合、または要求への応答にユーザー名の確認が必要ない場合は、ユーザー名コールバックから **NX_SUCCESS** の値が返されます。 それ以外の場合は、ルーチンから **NX_SNMP_ERROR** が返され、指定されたユーザー名が無効であることを示します。

アプリケーションのユーザー名コールバック ルーチンの形式は次のとおりです:

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

入力パラメーターは次のとおり定義されています:

| パラメーター | 意味                                              |
|-----------|------------------------------------------------------|
| *agent_ptr* | 呼び出し元の SNMP エージェントへのポインター                        |
| username  | 必要なユーザー名へのポインターの保存先 |

SNMPv1 および SNMPv2/v2C セッションンでは、アプリケーション使用時に、受信 SNMP 要求のコミュニティ文字列を調べてそれが有効かどうかを判断します。 SNMP アプリケーションには、これを実行するためのサービスがいくつかあります。

SNMP アプリケーションでは、処理中の SNMP マネージャーの要求が GET (GET、GETNEXT、GETBULKなど) と SET どちらのタイプの要求かを、次のサービスによって確認できます:

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

GET タイプの要求である場合、アプリケーションでは、入力されたコミュニティ文字列を SNMP エージェントのパブリック文字列と比較します:

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

SET タイプの要求である場合、アプリケーションでは、入力されたコミュニティ文字列を SNMP エージェントのプライベート文字列と比較します:

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

is_public と is_private の戻り値はそれぞれ、入力されたコミュニティ文字列が有効なパブリック コミュニティ文字列、有効なプライベート コミュニティ文字列であるかどうかを示します。

ユーザー名コールバック ルーチンの戻り値は、ユーザー名が有効であるかどうかを示します。 ユーザー名が有効である場合は **NX_SUCCESS** という値が、ユーザー名が無効である場合は **NX_SNMP_ERROR** が返されます。

## <a name="netx-duo-snmp-agent-get-callback"></a>NetX Duo SNMP エージェント GET コールバック

アプリケーションでは、SNMP マネージャーの GET オブジェクト要求を処理するコールバック ルーチンを設定する必要があります。 そのコールバックにより、要求で指定されたオブジェクトの値を取得します。

アプリケーションの GET 要求コールバック ルーチンは次のように定義されます:

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

入力パラメーターは次のとおり定義されています:

| パラメーター        | 意味 |
|------------------|----------------------------------|
| *agent_ptr*        | 呼び出し元の SNMP エージェントへのポインター |
| object_requested | GET 操作の対象のオブジェクト ID を表す ASCII 文字列。 |
| object_data      | コールバックで取得した値を保持するデータ構造体。 これは、次に説明する一連の NetX Duo SNMP API で設定できます。 |

> [!NOTE]
> *コールバック自体には長さの引数がないため、オクテット文字列を使用する場合は、オブジェクトに長さを割り当てて、内部の関数で長さを把握できるようにする必要があります:*

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

GET コールバックではそのデータ型を扱わないため、データ型を確認する必要はありません。 長さは、数値型または NULL 区切りの文字列には影響しません。

次に内部の関数を呼び出します:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

要求されたオブジェクトがコールバック関数で見つからない場合は **NX_SNMP_ERROR_NOSUCHNAME** エラー コードが返されます。 他のエラーが検出された場合は **NX_SNMP_ERROR** が返されます。

## <a name="netx-duo-snmp-agent-getnext-callback"></a>NetX Duo SNMP エージェント の GETNEXT コールバック

アプリケーションでは、SNMP マネージャーによる GETNEXT オブジェクト要求のためのコールバック ルーチンも設定する必要があります。 GETNEXT コールバックは、要求で指定された次のオブジェクトの値を取得します。

アプリケーションの GETNEXT 要求コールバック ルーチンは次のように定義されます:

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

入力パラメーターは次のとおり定義されています:

| パラメーター        | 意味 |
|------------------|-------------------------------------------|
| *agent_ptr*        | 呼び出し元の SNMP エージェントへのポインター |
| object_requested | GETNEXT 操作の対象のオブジェクト ID を表す ASCII 文字列。 |
| object_data      | コールバックで取得した値を保持するデータ構造体。 これは、次に説明する一連の NetX Duo SNMP API で設定できます。 |

コールバック自体には長さの引数がないため、GET コールバックと同様に、オクテット文字列のデータを含むオブジェクトには長さを割り当てて、内部関数で長さを把握できるようにする必要があります:

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

GET コールバックではそのデータ型を扱わないため、データ型を確認する必要はありません。 長さは、数値型または NULL 区切りの文字列には影響しません。

次に内部の関数を呼び出します:

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

要求されたオブジェクトがコールバック関数で見つからない場合は **NX_SNMP_ERROR_NOSUCHNAME** エラー コードが返されます。 他のエラーが検出された場合は **NX_SNMP_ERROR** が返されます。

## <a name="netx-duo-snmp-agent-set-callback"></a>NetX Duo SNMP エージェント SET コールバック

アプリケーションでは、SNMP マネージャーによる SET オブジェクト要求を処理するコールバック ルーチンを設定する必要があります。 SET コールバックは、要求で指定されたオブジェクトの値を設定します。

アプリケーションの SET 要求コールバック ルーチンは次のように定義されます:

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

入力パラメーターは次のとおり定義されています:

| パラメーター        | 意味 |
|------------------|-------- |
| *agent_ptr*      | 呼び出し元の SNMP エージェントへのポインター |
| object_requested | SET 操作の対象のオブジェクト ID を表す ASCII 文字列。 |
| object_data      | 指定されたオブジェクトのための新しい値を保持するデータ構造体。 操作は、次に説明する NetX Duo SNMP API を使用して実行できます。 |

オクテット文字列については、SET コールバックで MIB テーブルの長さのデータを更新するべきです。これは、SNMP エージェントが前もってデータを解析して型と長さを把握しているからです:

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

要求されたオブジェクトがコールバック関数で見つからない場合は **NX_SNMP_ERROR_NOSUCHNAME** エラー コードが返されます。

NetX Duo SNMP ホストでプライベート　コミュニティ文字列が既に作成されていて、SNMP の SET 要求の送信元にそれに一致するプライベート文字列がない場合、**NX_SNMP_ERROR_NOACCESS** エラーが返されることがあります。 他のエラーが検出された場合は **NX_SNMP_ERROR** が返されます。

> [!NOTE]
> *NetX Duo SNMP エージェント の配布パッケージには SNMP MIB データベースが付いて来ますが、それは主にテストおよび開発用です。開発者がプロフェッショナル向けの SNMP アプリケーションを使用するためには、恐らく、独自の MIB データベースが必要になるでしょう。*

## <a name="changing-snmp-version-at-run-time"></a>実行時に SNMP のバージョンを変更する

SNMP エージェント ホストは、実行時に *nx_snmp_agent_set_version* サービスを使用して、3 つの SNMP バージョンのうち好きなものにバージョンを変更できます。 *nx_snmp_agent_create* で SNMP エージェントを作成すると、3 つのバージョンすべてに対して SNMP エージェントは既定で有効になります。 ですが、アプリケーションでそれを一部のバージョンに限定することもできます。

> [!NOTE]
> *構成オプションの NX_SNMP_DISABLE_V1、 NX_SNMP_DISABLE_V2 または NX_SNMP_DISABLE_V3 を有効にしている場合、そのオプションの対象となるバージョンに対して、この関数で SNMP エージェントを有効にすることはできません。*

SNMP エージェントでは *nx_snmp_agent_get_current_version* サービスを使用して、最後に受信した SNMP パケットの SNMP バージョンを取得できます。

## <a name="snmpv3-discovery"></a>SNMPv3 検出

SNMPv3 に対して SNMP エージェントが有効にあっている場合、このエージェントは SNMP マネージャーの検出要求に応答します。 この種の要求のセキュリティ パラメーターのデータでは、認証エンジン ID、ユーザー名、ブート回数、ブート時間の値が NULL になっています。 認証パラメーターは DISCOVERY メッセージには適用されません。 要求の変数バインド リストは空です (リストには 1 つも項目がありません)。 SNMP エージェントは、値が 0 のブート時間とブート回数、項目 1 つを含む変数バインド リスト *usmStatsUnknownEngineIDs* で応答します。これは、エンジン ID が不明 (NULL) の要求を受信した回数を表します。 それに続いて GETNEXT 要求をブラウザー/マネージャーから受け取ると、セキュリティが有効である場合に限り、ブートのデータとセキュリティ パラメーターが用意されます。 その場合、最新の NotInTime データもPDU に入れて送信します。 認証などのセキュリティ パラメーターにより、エージェントの ID をマネージャーに証明します。

SNMPv3 認証の詳しい情報は、RFC 3414 の「User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)」(SNMPv3 のユーザー ベース セキュリティ モデル (USM))をご覧ください。

## <a name="netx-duo-snmp-rfcs"></a>NetX Duo SNMP に関連する RFC

NetX Duo SNMP は、RFC1155、RFC1157、RFC1215、RFC1901、RFC1905、RFC1906、RFC1907、RFC1908、RFC2571、RFC2572、RFC2574、RFC2575、RFC 3414、および関連するその他の RFC に準拠しています。
