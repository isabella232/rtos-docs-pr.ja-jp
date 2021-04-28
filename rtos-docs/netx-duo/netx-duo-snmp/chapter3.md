---
title: チャプター 3 - Azure RTOS NetX Duo SNMP エージェントのサービスの説明
description: このチャプターでは、NetX Duo SNMP エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cf4c4cb0edb7deb7bd0f257f48949b5c7355426b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810583"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-snmp-agent-services"></a>チャプター 3 - Azure RTOS NetX Duo SNMP エージェントのサービスの説明

このチャプターでは、Azure RTOS NetX Duo SNMP エージェントのすべてのサービス (以下に記載) をアルファベット順に説明します。

次の API の説明の「戻り値」セクションで、**太字** の値は、API のエラー チェックを有効にするための **NX_DISABLE_ERROR_CHECKING** を有効にしてもその影響を受けないことを表します。太字でない値は完全に無効になります。

- [nx_snmp_agent_auth_trap_key_use](#nx_snmp_agent_auth_trap_key_use)
   - *トラップ メッセージの認証キーを指定します (SNMP v3 のみ)*
- [nx_snmp_agent_authenticate_key_use](#nx_snmp_agent_authenticate_key_use)
   - *応答メッセージの認証キーを指定します (SNMP v3 のみ)*
- [nx_snmp_agent_community_get](#nx_snmp_agent_community_get)
   - *コミュニティ名を取得します*
- [nx_snmp_agent_context_engine_set](#nx_snmp_agent_context_engine_set)
   - *コンテキスト エンジンを設定します (SNMP v3 のみ)*
- [nx_snmp_agent_context_name_set](#nx_snmp_agent_context_name_set)
   - *コンテキスト名を設定します (SNMP v3 のみ)*
- [nx_snmp_agent_create](#nx_snmp_agent_create)
   - *SNMP エージェントを作成します*
- [nx_snmp_agent_current_version_get](#nx_snmp_agent_current_version_get)
   - *受信パケットの SNMP のバージョンを取得します*
- [nx_snmp_agent_request_get_type_test](#nx_snmp_agent_request_get_type_test)
   - *最後に受け取った SNMP 要求が GET と SET どちらのタイプであるかを示します*
- [nx_snmp_agent_private_string_test](#nx_snmp_agent_private_string_test)
   - *文字列がエージェントのプライベート文字列に一致するかどうかを判断します*
- [nx_snmp_agent_public_string_test](#nx_snmp_agent_public_string_test)
   - *文字列がエージェントのパブリック文字列に一致するかどうかを判断します*
- [nx_snmp_agent_set_interface](#nx_snmp_agent_set_interface)
   - *SNMP メッセージのネットワーク インターフェイスを設定します*
- [nx_snmp_agent_private_string_set](#nx_snmp_agent_private_string_set)
   - *SNMP エージェントのプライベート コミュニティ文字列を設定します*
- [nx_snmp_agent_public_string_set](#nx_snmp_agent_public_string_set)
   - *SNMP エージェントのパブリック コミュニティ文字列を設定します*
- [nx_snmp_agent_version_set](#nx_snmp_agent_version_set)
   - *すべての SNMP バージョンに対して SNMP エージェントの状態を設定します*
- [nx_snmp_agent_delete](#nx_snmp_agent_delete)
   - *SNMP エージェントを削除します*
- [nx_snmp_agent_md5_key_create](#nx_snmp_agent_md5_key_create)
   - *MD5 キーを作成します (SNMP v3 のみ)*
- [nx_snmp_agent_md5_key_create_extended](#nx_snmp_agent_md5_key_create_extended)
   - *MD5 キーを作成します (SNMP v3 のみ)*
- [nx_snmp_agent_priv_trap_key_use](#nx_snmp_agent_priv_trap_key_use)
   - *トラップ メッセージの暗号化キーを指定します (SNMP v3 のみ)*
- [nx_snmp_agent_privacy_key_use](#nx_snmp_agent_privacy_key_use)
   - *応答メッセージの暗号化キーを指定します (SNMP v3 のみ)*
- [nx_snmp_agent_sha_key_create](#nx_snmp_agent_sha_key_create)
   - *SHA キーを作成します (SNMP v3 のみ)*
- [nx_snmp_agent_sha_key_create_extended](#nx_snmp_agent_sha_key_create_extended)
   - *SHA キーを作成します (SNMP v3 のみ)*
- [nx_snmp_agent_start](#nx_snmp_agent_start)
   - *SNMP エージェントを起動します*
- [nx_snmp_agent_stop](#nx_snmp_agent_stop)
   - *SNMP エージェントを停止します*
- [nx_snmp_agent_trap_send](#nx_snmp_agent_trap_send)
   - *SNMPv1 トラップを送信します (IPv4 のみ)*
- [nx_snmp_agent_trapv2_send](#nx_snmp_agent_trapv2_send)
   - *SNMPv2 トラップを送信します (IPv4 のみ)*
- [nx_snmp_agent_trapv2_oid_send](#nx_snmp_agent_trapv2_oid_send)
   - *OID を指定して SNMPv2 トラップを送信します (IPv4 のみ)*
- [nx_snmp_agent_trapv3_send](#nx_snmp_agent_trapv3_send)
   - *SNMPv3 トラップを送信します (IPv4 のみ)*
- [nx_snmp_agent_trapv3_oid_send](#nx_snmp_agent_trapv3_oid_send)
   - *OID を指定して SNMPv2 トラップを送信します (IPv4 のみ)*
- [nxd_snmp_agent_trap_send](#nxd_snmp_agent_trap_send)
   - *SNMPv1 トラップを送信します (IPv4 と IPv6)*
- [nxd_snmp_agent_trapv2_send](#nxd_snmp_agent_trapv2_send)
   - *SNMPv2 トラップを送信します (IPv4 と IPv6)*
- [nxd_snmp_agent_trapv2_oid_send](#nxd_snmp_agent_trapv2_oid_send)
   - *OID を指定して SNMPv2 トラップを送信します (IPv4 と IPv6)*
- [nxd_snmp_agent_trapv3_send](#nxd_snmp_agent_trapv3_send)
   - *SNMPv3 トラップを送信します (IPv4 と IPv6)*
- [nxd_snmp_agent_trapv3_oid_send](#nxd_snmp_agent_trapv3_oid_send)
   - *OID を指定して SNMP v2 トラップを送信します (IPv4 と IPv6)*
- [nx_snmp_agent_v3_context_boots_set](#nx_snmp_agent_v3_context_boots_set)
   - *再起動回数を設定します*
- [nx_snmp_object_compare](#nx_snmp_object_compare)
   - *2 つのオブジェクトを比較します*
- [nx_snmp_object_compare_extended](#nx_snmp_object_compare_extended)
   - *2 つのオブジェクトを比較します*
- [nx_snmp_object_copy](#nx_snmp_object_copy)
   - *オブジェクトをコピーする*
- [nx_snmp_object_copy_extended](#nx_snmp_object_copy_extended)
   - *オブジェクトをコピーする*
- [nx_snmp_object_counter_get](#nx_snmp_object_counter_get)
   - *カウンター オブジェクトを取得します*
- [nx_snmp_object_counter_set](#nx_snmp_object_counter_set)
   - *カウンター オブジェクトを設定します*
- [nx_snmp_object_counter64_get](#nx_snmp_object_counter64_get)
   - *64 ビットのカウンター オブジェクトを取得します*
- [nx_snmp_object_counter64_set](#nx_snmp_object_counter64_set)
   - *64ビットのカウンター オブジェクトを設定します*
- [nx_snmp_object_end_of_mib](#nx_snmp_object_end_of_mib)
   - *end-of-mib (MIB の末尾) の値を設定します*
- [nx_snmp_object_gauge_get](#nx_snmp_object_gauge_get)
   - *ゲージ オブジェクトを取得します*
- [nx_snmp_object_gauge_set](#nx_snmp_object_gauge_set)
   - *ゲージ オブジェクトを設定します*
- [nx_snmp_object_id_get](#nx_snmp_object_id_get)
   - *オブジェクト ID を取得します*
- [nx_snmp_object_id_set](#nx_snmp_object_id_set)
   - *オブジェクト ID を設定します*
- [nx_snmp_object_integer_get](#nx_snmp_object_integer_get)
   - *整数オブジェクトを取得します*
- [nx_snmp_object_integer_set](#nx_snmp_object_integer_set)
   - *整数オブジェクトを設定します*
- [nx_snmp_object_ip_address_get](#nx_snmp_object_ip_address_get)
   - *IP アドレス オブジェクトを取得します (IPv4 のみ)*
- [nx_snmp_object_ip_address_set](#nx_snmp_object_ip_address_set)
   - *IP アドレス オブジェクトを設定します (IPv4 のみ)*
- [nx_snmp_object_ipv6_address_get](#nx_snmp_object_ipv6_address_get)
   - *IP アドレス オブジェクトを取得します (IPv6 のみ)*
- [nx_snmp_object_ipv6_address_set](#nx_snmp_object_ipv6_address_set)
   - *IP アドレス オブジェクトを設定します (IPv6 のみ)*
- [nx_snmp_object_no_instance](#nx_snmp_object_no_instance)
   - *インスタンス不在の値を設定します*
- [nx_snmp_object_not_found](#nx_snmp_object_not_found)
   - *不検出の値を設定します*
- [nx_snmp_object_octet_string_get](#nx_snmp_object_octet_string_get)
   - *オクテット文字列オブジェクトを取得します*
- [nx_snmp_object_octet_string_set](#nx_snmp_object_octet_string_set)
   - *オクテット文字列オブジェクトを設定します*
- [nx_snmp_object_string_get](#nx_snmp_object_string_get)
   - *ASCII 文字列オブジェクトを取得します*
- [nx_snmp_object_string_set](#nx_snmp_object_string_set)
   - *ASCII 文字列オブジェクトを設定します*
- [nx_snmp_object_timetics_get](#nx_snmp_object_timetics_get)
   - *timetics オブジェクトを取得します*
- [nx_snmp_object_timetics_set](#nx_snmp_object_timetics_set)
   - *timetics オブジェクトを設定します*

## <a name="nx_snmp_agent_auth_trap_key_use"></a>nx_snmp_agent_auth_trap_key_use
トラップ メッセージの認証キーを指定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>説明

このサービスでは、トラップ メッセージの SNMPv3 セキュリティ ヘッダーに認証パラメーターを設定する際に使用するキーを指定します。 キーに NX_NULL の値を指定すると認証を無効にします。

> [!NOTE]
> キーを前もって作成しておく必要があります。 nx_snmp_agent_md5_key_create または nx_snmp_agent_sha_key_create を参考にしてください。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **key** 作成済みの MD5 キーまたは SHA キーへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 認証キーの設定に成功。
- **NX_NOT_ENABLED** (0x14) SNMP セキュリティが無効になっています 
- **NX_PTR_ERROR** (0x07) SNMP エージェントへのポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Use previously created “my_key” for SNMPv3 trap message authentication.  */
status =  nx_snmp_agent_auth_trap_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for authentication parameters in trap messages.  */
```

## <a name="nx_snmp_agent_authenticate_key_use"></a>nx_snmp_agent_authenticate_key_use
応答メッセージの認証キーを指定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr, 
                                        NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>説明

このサービスでは、それ以降のすべての要求で SNMPv3 セキュリティ パラメーターの認証パラメーターに使用するキーを指定します。 キーに NX_NULL の値を指定すると認証を無効にします。

> [!NOTE]
> キーを前もって作成しておく必要があります。 nx_snmp_agent_md5_key_create または nx_snmp_agent_sha_key_create を参考にしてください。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **key** 作成済みの MD5 キーまたは SHA キーへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP キーの設定に成功。
- **NX_NOT_ENABLED** (0x14) SNMP セキュリティが無効になっています
- **NX_PTR_ERROR** (0x07) SNMP エージェントへのポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Use previously created “my_key” for SNMPv3 authentication.  */
status =  nx_snmp_agent_authenticate_key_use(&my_agent, &my_key);


/* If status is NX_SUCCESS the SNMP Agent will use “my_key” for
   for setting the authentication parameters of SNMPv3 requests.  */
```

## <a name="nx_snmp_agent_community_get"></a>nx_snmp_agent_community_get
コミュニティ名を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_community_get(NX_SNMP_AGENT *agent_ptr, 
                                 UCHAR **community_string_ptr);
```

### <a name="description"></a>説明

このサービスでは、SNMP エージェントで最後に受信した SNMP 要求からコミュニティ名を取得します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **community_string_ptr** SNMP エージェントのコミュニティ文字列への文字列ポインターへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP のコミュニティ名の取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
UCHAR *string_ptr;

/* Pickup the community string pointer for my_agent.  */
status =  nx_snmp_agent_community_get(&my_agent, &string_ptr);


/* If status is NX_SUCCESS the pointer “string_ptr” points to the
   last community name supplied to the SNMP agent.  */
```

## <a name="nx_snmp_agent_request_get_type_test"></a>nx_snmp_agent_request_get_type_test
最後に受け取った SNMP 要求が GET と SET どちらのタイプであるかを示します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

### <a name="description"></a>説明

このサービスでは、SNMP マネージャーから最後に受け取った要求が GET タイプ (GET、GETNEXT、または GETBULK) と SET タイプのどちらであるかを示します。 このサービスは、要求が GET タイプである場合は SNMPv1 または SNMPv2 アプリケーションで受信したコミュニティ文字列を SNMP エージェントのパブリック文字列と比較し、要求が SET タイプである場合は SNMP エージェントのプライベート文字列と比較するユーザー名コールバックと合わせて使用することを意図しています。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **is_get_type** 要求のタイプへのポインター:  
GET タイプの場合は NX_TRUE  
SET タイプの場合は NX_FALSE

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) タイプを返すことに成功
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
UINT is_get_type;

/* Determine if the current SNMP request is a GET or SET type.  */
status =  nx_snmp_agent_request_get_type_test(&my_agent, &is_get_type);


/* If status is NX_SUCCESS, is_get_type will indicate the request type.  */
```

## <a name="nx_snmp_agent_context_engine_set"></a>nx_snmp_agent_context_engine_set
コンテキスト エンジンを設定します (SNMP v3 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_context_engine_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *context_engine, 
                                      UINT context_engine_size);
```
### <a name="description"></a>説明

このサービスでは、SNMP エージェントのコンテキスト エンジンを設定します。 SNMPv3 の処理にのみ適用されます。 コンテキスト エンジン ID はキーの作成に使用するため、アプリケーションで認証と暗号化を使用している場合は、セキュリティ キーを作成する前にこのサービスを呼び出す必要があります。 その他の場合、NetX Duo SNMP では、*nxd_snmp.c* の冒頭に既定のコンテキスト エンジン ID を用意しています:

```c
UCHAR _nx_snmp_default_context_engine[NX_SNMP_MAX_CONTEXT_STRING] =  
                {0x80, 0x00, 0x03, 0x10, 0x01, 0xc0, 0xa8, 0x64, 0xaf};

```

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **context_engine** コンテキスト エンジンの文字列へのポインター。
- **context_engine_size** コンテキスト エンジンの文字列のサイズ。 コンテキスト エンジンの最大バイト数は、NX_SNMP_MAX_CONTEXT_STRING で指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP コンテキスト エンジンの設定に成功。
- **NX_NOT_ENABLED** (0x14) SNMPv3 が有効になっていません
- **NX_SNMP_ERROR** (0x100) コンテキスト エンジンのサイズのエラー。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
UCHAR my_engine[] = {0x80, 0x00, 0x01, 0x02, 0x03, 0x04, 0x05, 0x06, 0x07};

/* Set the context engine for my_agent.  */
status =  nx_snmp_agent_context_engine_set(&my_agent, my_engine, 9);


/* If status is NX_SUCCESS the context engine has been set.  */
```
## <a name="nx_snmp_agent_context_name_set"></a>nx_snmp_agent_context_name_set
コンテキスト名を設定します (SNMP v3 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_context_name_set(NX_SNMP_AGENT *agent_ptr, 
                                    UCHAR *context_name, 
                                    UINT context_name_size);
```

### <a name="description"></a>説明

このサービスでは、SNMP エージェントのコンテキスト名を設定します。 SNMPv3 の処理にのみ適用されます。 これを呼び出さない場合、NetX Duo SNMP エージェントのコンテキスト名は空白のままになります。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **context_name** コンテキスト名の文字列へのポインター。
- **context_name_size** コンテキスト名の文字列のサイズ。 コンテキスト名の最大バイト数は NX_SNMP_MAX_CONTEXT_STRING で指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP コンテキスト名の設定に成功。
- **NX_SNMP_ERROR** (0x100) コンテキスト名のサイズのエラー。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the context name for my_agent.  */
status =  nx_snmp_agent_context_name_set(&my_agent, “my_context_name”, 15);


/* If status is NX_SUCCESS the context name has been set.  */
```

## <a name="nx_snmp_agent_create"></a>nx_snmp_agent_create
SNMP エージェントを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_create(NX_SNMP_AGENT *agent_ptr, 
      CHAR *snmp_agent_name, NX_IP *ip_ptr, VOID *stack_ptr, 
      ULONG stack_size, NX_PACKET_POOL *pool_ptr,
      UINT (*snmp_agent_username_process)(struct NX_SNMP_AGENT_STRUCT 
                                    *agent_ptr, UCHAR *username),
      UINT (*snmp_agent_get_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_getnext_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data),
      UINT (*snmp_agent_set_process)(struct NX_SNMP_AGENT_STRUCT 
                  *agent_ptr, UCHAR *object_requested, 
                  NX_SNMP_OBJECT_DATA *object_data));
```
### <a name="description"></a>説明

このサービスでは、指定した IP インスタンスに SNMP エージェントを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **snmp_agent_name** SNMP エージェント名の文字列へのポインター。
- **ip_ptr** IP インスタンスへのポインター。
- **stack_ptr** SNMP エージェントのスレッド スタックへのポインターへのポインター。
- **stack_size** byte 単位のスタック サイズ。
- **pool_ptr** この SNMP エージェントの既定のパケット プールへのポインター。
- **snmp_agent_username_process** アプリケーションのユーザー名処理ルーチンへの関数ポインター。
- **snmp_agent_get_process** アプリケーションの GET 要求処理ルーチンへの関数ポインター。
- **snmp_agent_getnext_process** アプリケーションの GETNEXT 要求処理ルーチンへの関数ポインター。
- **snmp_agent_set_process** アプリケーションの SET 要求処理ルーチンへの関数ポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP エージェントの作成に成功。
- **NX_SNMP_ERROR** (0x100) SNMP エージェント作成エラー。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
NX_SNMP_AGENT my_agent;

/* Create the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_create(&my_agent, "My SNMP Agent", &ip_0, stack_start_ptr,
                4096, &pool_0, my_username_processing, my_get_processing, 
                my_getnext_processing, my_set_processing);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been created.  */
```

## <a name="nx_snmp_agent_current_version_get"></a>nx_snmp_agent_current_version_get
SNMP パケットのバージョンを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_current_version_get(NX_SNMP_AGENT *agent_ptr, 
                                       UINT *version);
```

### <a name="description"></a>説明

このサービスでは、最後に受信した SNMP パケットを解析して SNMP のバージョンを取得します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **version** 受信した SNMP パケットを解析して得た SNMP のバージョンへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP のバージョンの取得に成功
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT          snmp_version;
NX_SNMP_AGENT my_agent;

/* Get the version of the last received SNMP packet. */
status =  nx_snmp_agent_current_version_get (&my_agent, &snmp_version);


/* If status is NX_SUCCESS, snmp_version contains 
   the received packet SNMP version.  */
```

## <a name="nx_snmp_agent_private_string_test"></a>nx_snmp_agent_private_string_test
プライベート文字列がエージェントのプライベート文字列と一致することを確認します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr, 
                                       UCHAR *community_string,          
                                       UINT *is_private);
```

### <a name="description"></a>説明

このサービスでは、NULL で終わる入力コミュニティ文字列を SNMP エージェントのプライベート文字列と比較して、一致するかどうかを示します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **community_string** 比較する文字列へのポインター
- **is_private** 比較結果へのポインター  
NX_TRUE - 文字列が一致します  
NX_FALSE - 文字列が一致しません

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 比較に成功
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT        is_private;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;

/* Determine if the community string matches the agent private string */
status =  nx_snmp_agent_private_string_test(&my_agent, community_string_ptr,  
                                            &is_private);


/* If status is NX_SUCCESS, is_private will indicate if there is a match. 
   If is_private is NX_TRUE, they match.  */
```

## <a name="nx_snmp_agent_public_string_test"></a>nx_snmp_agent_public_string_test
受信したパブリック文字列がエージェントのパブリック文字列と一致することを確認します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string,          
                                      UINT *is_public);
```
### <a name="description"></a>説明

このサービスでは、NULL で終わる入力コミュニティ文字列を SNMP エージェントのパブリック文字列と比較し、一致するかどうかを示します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **community_string** 比較する文字列へのポインター
- **is_public** 比較結果へのポインター  
NX_TRUE - 文字列が一致します  
NX_FALSE - 文字列が一致しません

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 比較に成功
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT        is_public;
UCHAR       *community_string_ptr;
NX_SNMP_AGENT   my_agent;


/* Determine if the community string matches the agent public string */
status =  nx_snmp_agent_public_string_test(&my_agent, community_string_ptr,  
                                           &is_public);


/* If status is NX_SUCCESS, is_public will indicate if there is a match. 
   If is_public is true they match.  */
```

## <a name="nx_snmp_agent_version_set"></a>nx_snmp_agent_version_set
SNMP の各バージョンに対する SNMP エージェントの状態を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_version_set(NX_SNMP_AGENT *agent_ptr, 
                               UINT enabled_v1, UINT enable_v2, 
                               UINT enable_v3);
```

### <a name="description"></a>説明

このサービスでは、 SNMP の各バージョン (V1、V2、V3) に対する SNMP エージェントの状態 (有効/無効) を設定します。 これらのランタイム設定よりも、ユーザーが構成できるオプション、NX_SNMP_DISABLE_V1、NX_SNMP_DISABLE_V2、 NX_SNMP_DISABLE_V3 の効果が優先されます。 既定では、SNMP エージェントは 3 つのバージョンすべてに対して有効になっています。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **enabled_v1** SNMP V1 に対する有効/無効を設定します。
- **enabled_v2** SNMP V2 に対する有効/無効を設定します。
- **enabled_v3** SNMP V3 に対する有効/無効を設定します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP バージョンに対する設定に成功
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
UINT          v1_on = NX_TRUE;
UINT          v2_on = NX_TRUE;
UINT          v3_on = NX_FALSE;

NX_SNMP_AGENT my_agent;

/* Enable/Disable each SNMP protocol (version) for the SNMP Agent) */
status =  nx_snmp_agent_version_set(&my_agent, v1_on, v2_on, v3_on);


/* If status is NX_SUCCESS, my_agent is enabled only for V1 and V2 assuming 
   NX_SNMP_DISABLE_V1 and NX_SNMP_DISABLE_V2 are not defined. */
```

## <a name="nx_snmp_agent_private_string_set"></a>nx_snmp_agent_private_string_set
SNMP エージェントのプライベート文字列を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_private_string_set(NX_SNMP_AGENT *agent_ptr, 
                                      UCHAR *community_string);
```

### <a name="description"></a>説明

このサービスは、NULL で終わる入力文字列を使用して、SNMP エージェントのプライベート コミュニティ文字列を設定します。 既定値は NULL です (プライベート文字列が設定されていない状態)。そのため、受信した SNMP パケットが “プライベート” コミュニティ文字列を含む場合、SNMP エージェントで読み取り/書き込みはできません。 入力文字列は、ユーザーが構成できる NX_SNMP_MAX_USER_NAME-1 のサイズ以下である必要があります (NULL 終端のスペースを確保するため)。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **community_string** 割り当てるプライベート文字列へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) プライベート文字列の設定に成功
- **NX_SNMP_ERROR_TOOBIG** (0x01) 文字列のサイズが大きすぎます 
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s private community string */
status =  nx_snmp_agent_private_string_set(&my_agent, “private”));


/* If status is NX_SUCCESS, the SNMP agent private string is set.  */
```

## <a name="nx_snmp_agent_public_string_set"></a>nx_snmp_agent_public_string_set
SNMP エージェントのパブリック文字列を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_public_string_set(NX_SNMP_AGENT *agent_ptr, 
                                     UCHAR *community_string);
```

### <a name="description"></a>説明

このサービスでは、NULL で終わる入力文字列を使用して、SNMP エージェントのパブリック コミュニティ文字列を設定します。 コミュニティ文字列は、ユーザーが構成できる NX_SNMP_MAX_USER_NAME-1 のサイズ以下である必要があります (NULL 終端のスペースを確保するため)。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **community_string** 割り当てるパブリック文字列へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パブリック文字列の設定に成功
- **NX_SNMP_ERROR_TOOBIG** (0x01) 文字列のサイズが大きすぎます
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_AGENT my_agent;

/* Set the SNMP agent’s public string. */
nx_snmp_agent_public_string_set(&my_agent, “my_public”));


/* If status is NX_SUCCESS, the SNMP agent public string is set.  */
```

## <a name="nx_snmp_agent_delete"></a>nx_snmp_agent_delete
SNMP エージェントを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_snmp_agent_delete(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>説明

このサービスでは、作成済みの SNMP エージェントを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP エージェントの削除に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Delete the SNMP Agent “my_agent.”  */
status =  nx_snmp_agent_delete(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been deleted.  */
```

## <a name="nx_snmp_agent_set_interface"></a>nx_snmp_agent_set_interface
SNMP エージェントのネットワーク インターフェイスを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_set_interface(NX_SNMP_AGENT *agent_ptr,  
                                 UINT if_index);
```

### <a name="description"></a>説明

このサービスでは、インターフェイス インデックスの指定に基づいて、SNMP エージェントの SNMP ネットワーク インターフェイスを設定します。 複数のネットワーク インターフェイスをサポートしているバージョン 5.6 以降の NetX Duo を SNMP ホスト アプリケーションで使用する場合のみ、このサービスは役に立ちます。 ホストで指定しない場合、プライマリ インターフェイスの既定値は 0 です。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **If_index** SNMP インターフェイスを指定するインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP インターフェイスの設定に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the SNMP Agent “my_agent” to the secondary interface.  */
if_index = 1;
status =  nx_snmp_agent_set_interface(&my_agent, if_index);


/* If status is NX_SUCCESS the SNMP agent interface is set.  */
```

## <a name="nx_snmp_agent_md5_key_create"></a>nx_snmp_agent_md5_key_create
MD5 キーを作成します (SNMP v3 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY 
                                       *destination_key);
```
### <a name="description"></a>説明

このサービスでは、認証と暗号化に使用できる MD5 キーを作成します。

このサービスは推奨されなくなりました。 開発者は *nx_snmp_agent_md5_key_create_extended()* に移行することを推奨します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **password** パスワードの文字列へのポインター。
- **destination_key** SNMP のキーのデータ構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) キーの作成に成功。
- **NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS an MD5 key has been created.  */
```

## <a name="nx_snmp_agent_md5_key_create_extended"></a>nx_snmp_agent_md5_key_create_extended
MD5 キーを作成します (SNMP v3 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_md5_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY 
                                           *destination_key);
```
### <a name="description"></a>説明

このサービスでは、認証と暗号化に使用できる MD5 キーを作成します。

これは *nx_snmp_agent_md5_key_create()* の後継サービスです。 このバージョンでは、呼び出し元でパスワードの長さを指定する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **password** パスワードの文字列へのポインター。
- **password_length** パスワードの文字列の長さ。
- **destination_key** SNMP のキーのデータ構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) キーの作成に成功。
- **NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。
- **NX_SNMP_FAILED** (0x102) SNMP が失敗しました。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the MD5 key for “my_agent.”   */
status =  nx_snmp_agent_md5_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_priv_trap_key_use"></a>nx_snmp_agent_priv_trap_key_use
トラップ メッセージの暗号化キーを指定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr, 
                                     NX_SNMP_SECURITY_KEY *key);
```

### <a name="description"></a>説明

このサービスでは、作成済みのプライバシー キーを使用して SNMPv3 トラップ メッセージの暗号化と復号を行うよう指定します。

> [!NOTE]
> *認証キーを前もって作成しておく必要があります。SNMP v3 のプライバシー (暗号化) には認証が必要です。詳細は nx_snmp_agent_auth_trap_key_use をご覧ください。*

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **key** 作成済みのキーへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パライバシー キーの設定に成功。
- **NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent” trap messages.   */
status =  nx_snmp_agent_priv_trap_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_privacy_key_use"></a>nx_snmp_agent_privacy_key_use
応答メッセージの暗号化キーを指定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr, 
                                   NX_SNMP_SECURITY_KEY *key);
```
### <a name="description"></a>説明

このサービスでは、作成済みのキーを使用して SNMPv3 の応答メッセージの暗号化と復号を行うよう指定します。

> [!NOTE]
> *認証キーを前もって指定しておく必要があります。SNMPv3 の暗号化では認証キーの作成も必要です。詳細は nx_snmp_agent_authentiation_key_use をご覧ください。*

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **key** 作成済みのキーへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パライバシー キーの設定に成功。
- **NX_NOT_ENABLED** (0x14) セキュリティが有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Use the “my_privacy_key” for the SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_privacy_key_use(&my_agent, &my_privacy_key);


/* If status is NX_SUCCESS the privacy key is registered with the SNMP agent.  */
```

## <a name="nx_snmp_agent_sha_key_create"></a>nx_snmp_agent_sha_key_create
SHA キーを作成します (SNMP v3 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr, 
                                  UCHAR *password, 
                                  NX_SNMP_SECURITY_KEY  
                                  *destination_key);
```
### <a name="description"></a>説明

このサービスでは、認証と暗号化に使用できる SHA キーを作成します。

このサービスは推奨されなくなりました。 開発者は *nx_snmp_agent_sha_key_create_extended()* に移行することを推奨します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **password** パスワードの文字列へのポインター。
- **destination_key** SNMP のキーのデータ構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) キーの作成に成功。
- **NX_SNMP_ERROR** (0x100) キー作成エラー。
- **NX_PTR_ERROR** (0x07) SNMP エージェントまたはキーへのポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create(&my_agent, “authpw”, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_sha_key_create_extended"></a>nx_snmp_agent_sha_key_create_extended
SHA キーを作成します (SNMP v3 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_sha_key_create_extended(NX_SNMP_AGENT *agent_ptr, 
                                           UCHAR *password, 
                                           UINT password_length,
                                           NX_SNMP_SECURITY_KEY  
                                           *destination_key);
```
### <a name="description"></a>説明

このサービスでは、認証と暗号化に使用できる SHA キーを作成します。

これは *nx_snmp_agent_sha_key_create()* の後継サービスです。 このバージョンでは、呼び出し元でパスワードの長さを指定する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **password** パスワードの文字列へのポインター。
- **password_length** パスワードの文字列の長さ。
- **destination_key** SNMP のキーのデータ構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) キーの作成に成功。
- **NX_SNMP_ERROR** (0x100) キー作成エラー。
- **NX_SNMP_FAILED** (0x102) キー作成に失敗。
- **NX_PTR_ERROR** (0x07) SNMP エージェントまたはキーへのポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
NX_SNMP_SECURITY_KEY my_key;

/* Create the SHA key for “my_agent.”   */
status =  nx_snmp_agent_sha_key_create_extended(&my_agent, “authpw”, 6, &my_key);


/* If status is NX_SUCCESS the key for the password “authpw” has been created.  */
```

## <a name="nx_snmp_agent_start"></a>nx_snmp_agent_start
SNMP エージェントを起動します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_start(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>説明

このサービスでは、UDP ソケットを 161 番の SNMP ポートにバインドし、SNMP エージェントのスレッドのタスクを開始します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP エージェントの起動に成功。
- **NX_SNMP_ERROR** (0x100) SNMP エージェントの起動エラー。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Start the previously created SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_start(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been started.  */
```
## <a name="nx_snmp_agent_stop"></a>nx_snmp_agent_stop
SNMP エージェントを停止します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_stop(NX_SNMP_AGENT *agent_ptr);
```
### <a name="description"></a>説明

このサービスでは、SNMP エージェントのスレッドのタスクを停止し、UDP ソケットを SNMP ポートからバインド解除します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP エージェントの停止に成功。
- **NX_PTR_ERROR** (0x07) SNMP エージェントへのポインターが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Stop the previously created and started SNMP Agent “my_agent.”   */
status =  nx_snmp_agent_stop(&my_agent);


/* If status is NX_SUCCESS the SNMP Agent “my_agent” has been stopped.  */
```
## <a name="nx_snmp_agent_trap_send"></a>nx_snmp_agent_trap_send
SNMPv1 トラップを送信します *(IPv4 のみ)*

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
                             ULONG ip_address, UCHAR *enterprise, 
                             UINT trap_type, UINT trap_code, 
                             ULONG elapsed_time, 
                             NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定した IPv4 アドレスの SNMP マネージャーに SNMP トラップを送信します。 NetX Duo で SNMP トラップを送信する際は *nxd_snmp_agent_trap_send* サービスを使用することを推奨します。 *nx_snmp_agent_trap_send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IPv4 アドレス。
- **enterprise** エンタープライズ オブジェクト ID の文字列 (sysObectID)。
- **trap_type** 要求されたトラップの種類。次の種類があります:  
   - NX_SNMP_TRAP_COLDSTART (0)  
   - NX_SNMP_TRAP_WARMSTART (1)  
   - NX_SNMP_TRAP_LINKDOWN (2)  
   - NX_SNMP_TRAP_LINKUP (3)  
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)  
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  

- **trap_code** 特定のトラップコード。
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_NOT_ENABLED** (0x14) SNMPv1 が有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nx_snmp_agent_trap_send(&my_agent,dest_ip_address,
                                   "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, 
                                  tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trap_send"></a>nxd_snmp_agent_trap_send
SNMPv1 トラップを送信します *(IPv4 と IPv6)*

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_snmp_agent_trap_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *enterprise, UINT trap_type, 
            UINT trap_code, ULONG elapsed_time, 
            NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IP アドレスの SNMP マネージャーに SNMP トラップを送信します。 NetX で SNMP トラップを送信するためのこれに相当するサービスは *nxd_snmp_agent_trap_send* です。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IPv4 または IPv6 アドレス。
- **enterprise** エンタープライズ オブジェクト ID の文字列 (sysObectID)。
- **trap_type** 要求されたトラップの種類。次の種類があります:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

- **trap_code** 特定のトラップコード。
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_NOT_ENABLED** (0x14) SNMPv1 が有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build list of objects to supply in the trap.  */
trap_list[0].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.2.2.1.1.0";
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_INTEGER;
trap_list[0].nx_snmp_object_data.nx_snmp_object_data_msw =   counter;
trap_list[1].nx_snmp_object_string_ptr =  "1.3.6.1.2.1.1.3.0";
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_type =  NX_SNMP_TIME_TICS;
trap_list[1].nx_snmp_object_data.nx_snmp_object_data_msw =   tx_time_get();
trap_list[2].nx_snmp_object_string_ptr =  NX_NULL; /* Terminate list!  */

/* Send trap to SNMP manager at 193.2.2.61.  */
status =  nxd_snmp_agent_trap_send(&my_agent,&dest_ip_address,
                 "1.3.6.7.7.7", NX_SNMP_TRAP_LINKUP, counter++, tx_time_get(), 
               trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_send"></a>nx_snmp_agent_trapv2_send
SNMPv2 トラップを送信します (IPv4 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
            NXD_ADDRESS *ip_address, UCHAR *community, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IPv4 アドレスの SNMP マネージャーに SNMPv2 トラップを送信します。 NetX Duo で SNMP トラップを送信する際は *nxd_snmp_agent_trapv2_send* サービスを使用することを推奨します。 *nx_snmp_agent_trapv2_send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IPv4 アドレス。
- **community** コミュニティ名 (ユーザー名)。
- **trap_type**  
   要求されたトラップの種類。 標準のイベントは次のとおりです:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   独自データを使用する場合:  
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF。*nxd_snmp.h* で指定されます)
   
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_NOT_ENABLED** (0x14) SNMPv2 が有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG  dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_send(&my_agent,dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv2_oid_send"></a>nx_snmp_agent_trapv2_oid_send
OID を直接指定して SNMPv2 トラップを送信します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *community,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IP アドレス (IPv4 のみ) の SNMP マネージャーに SNMPv2 トラップを送信し、呼び出し元で OID を直接指定できます。 NetX Duo で OID を指定して SNMP トラップを送信する際は、*nxd_snmp_agent_trapv2_oid_send* サービスを使用することを推奨します。 *nx_snmp_agent_trapv2_oid_ send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IP アドレス。
- **community** コミュニティ名 (ユーザー名)。
- **oid** OID を保持するバッファーへのポインター。
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。
- **NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。
- **NX_OPTION_ERROR** (0x0a) 無効なパラメーター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv2_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_send"></a>nxd_snmp_agent_trapv2_send
SNMPv2 トラップを送信します (IPv4 と IPv6)

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_snmp_agent_trapv2_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *community, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IP アドレスの SNMP マネージャーに SNMP V2 トラップを送信します。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IP アドレス (IPv4 または IPv6)
- **community** コミュニティ名 (ユーザー名)。
- **trap_type**  
   要求されたトラップの種類。 標準のイベントは次のとおりです:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   独自データを使用する場合:

   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF。*nxd_snmp.h* で指定されます)

- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_NOT_ENABLED** (0x14) SNMPv2 が有効になっていません。
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) サポートされていない IP バージョン
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send a standard event trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_send(&my_agent,&dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv2_oid_send"></a>nxd_snmp_agent_trapv2_oid_send
OID を直接指定して SNMPv2 トラップを送信します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_snmp_agent_trapv2_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *community,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                    *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定された IP アドレス (IPv4 または IPv6) の SNMP マネージャーに SNMP v2 トラップを送信し、呼び出し元で OID を直接指定できます。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IP アドレス (IPv4 または IPv6)。
- **community** コミュニティ名 (ユーザー名)。
- **oid** OID を保持するバッファーへのポインター。
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。
- **NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。
- **NX_OPTION_ERROR** (0x0a) 無効なパラメーター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS         address;


/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

address.nxd_ip_version = NX_IP_VERSION_V4;
address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61)

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv2_oid_send(&my_agent, &address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_trapv3_send"></a>nx_snmp_agent_trapv3_send
SNMPv3 トラップを送信します (IPv4 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
            ULONG ip_address, UCHAR *username, UINT trap_type, 
            ULONG elapsed_time, NX_SNMP_TRAP_OBJECT *object_list_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定した IPv4 アドレスの SNMP マネージャーに SNMPv3 トラップを送信します。 NetX Duo で SNMP トラップを送信する際は *nxd_snmp_agent_trapv3_send* サービスを使用することを推奨します。 *nx_snmp_agent_trapv3_send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IPv4 アドレス。
- **username** コミュニティ名 (ユーザー名)。
- **trap_type**  
   要求されたトラップの種類。 標準のイベントは次のとおりです:  
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)

   独自データを使用する場合:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) *nxd_snmp.h* で指定されます)

- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_NOT_ENABLED** (0x14) SNMPv3 が有効になっていません。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
ULONG dest_ip_address = IP_ADDRESS(1,2,3,4);

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_send(&my_agent, dest_ip_address, "public",
               NX_SNMP_TRAP_COLDSTART, tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nx_snmp_agent_trapv3_oid_send"></a>nx_snmp_agent_trapv3_oid_send
OID を直接指定して SNMPv3 トラップを送信します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                   ULONG ip_address, UCHAR *username,        
                                   UCHAR *oid, ULONG elapsed_time,   
                                   NX_SNMP_TRAP_OBJECT 
                                   *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IP アドレス (IPv4 のみ) の SNMP マネージャーに SNMPv3 トラップを送信し、呼び出し元で OID を直接指定できます。 NetX Duo で OID を指定して SNMP トラップを送信する際は、*nxd_snmp_agent_trapv3_oid_send* サービスを使用することを推奨します。 *nx_snmp_agent_trapv3_oid_ send* が NetX Duo に含まれているのは、既存の NetX SNMP エージェント アプリケーションをサポートするためです。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IP アドレス。
- **username** コミュニティ名 (ユーザー名)。
- **oid** OID を保持するバッファーへのポインター。
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。
- **NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。
- **NX_OPTION_ERROR** (0x0a) 無効なパラメーター。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nx_snmp_agent_trapv3_oid_send(&my_agent, IP_ADDRESS(193,2,2,61), 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nxd_snmp_agent_trapv3_send"></a>nxd_snmp_agent_trapv3_send
SNMPv3 トラップを送信します (IPv4 と IPv6)

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_snmp_agent_trapv3_send(NX_SNMP_AGENT *agent_ptr, 
                                NXD_ADDRESS *ip_address, 
                                UCHAR *username, UINT trap_type, 
                                ULONG elapsed_time, 
                                NX_SNMP_TRAP_OBJECT *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IP アドレスの SNMP マネージャーに SNMP トラップを送信します。 このトラップは基本的に SNMP v2 トラップと同じですが、SNMP v3 ではトラップ メッセージの形式を PDU に入れる点が異なります。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IP アドレス (IPv4 または IPv6)
- **username** コミュニティ名 (ユーザー名)。
- **trap_type**  
   要求されたトラップの種類。 標準のイベントは次のとおりです:
   - NX_SNMP_TRAP_COLDSTART (0)
   - NX_SNMP_TRAP_WARMSTART (1)
   - NX_SNMP_TRAP_LINKDOWN (2)
   - NX_SNMP_TRAP_LINKUP (3)
   - NX_SNMP_TRAP_AUTHENTICATE_FAILURE (4)
   - NX_SNMP_TRAP_EGPNEIGHBORLOSS (5)  
   独自データを使用する場合:
   - NX_SNMP_TRAP_CUSTOM (0xFFFFFFFF) (*nxd_snmp.h* で指定されます)

- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_NOT_ENABLED** (0x14) SNMPv3 が有効になっていません。
- **NX_SNMP_INVALID_IP_PROTOCOL_ERROR** (0x104) サポートされていない IP バージョン
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NX_SNMP_TRAP_OBJECT trap_list[5];
NXD_ADDRESS dest_ip_address;

    dest_ip_address.nxd_ip_version = NX_IP_VERSION_V6 ;
    dest_ip_address.nxd_ip_address.v6[0] = 0x20010db8;
    dest_ip_address.nxd_ip_address.v6[1] = 0xf101;
    dest_ip_address.nxd_ip_address.v6[2] = 0x00000000;
    dest_ip_address.nxd_ip_address.v6[3] = 0x00000101;

/* Build an empty object list, since it is not needed for the 
   NX_SNMP_TRAP_COLDSTART trap.  */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_send(&my_agent, &dest_ip_address, "public",
                                    NX_SNMP_TRAP_COLDSTART, tx_time_get(),  
                                    trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```

## <a name="nxd_snmp_agent_trapv3_oid_send"></a>nxd_snmp_agent_trapv3_oid_send
OID を直接指定して SNMPv3 トラップを送信します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nxd_snmp_agent_trapv3_oid_send(NX_SNMP_AGENT *agent_ptr, 
                                    NXD_ADDRESS *ip_address, 
                                    UCHAR *username,        
                                    UCHAR *oid, ULONG elapsed_time,   
                                    NX_SNMP_TRAP_OBJECT 
                                            *object_list_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定した IP アドレス (IPv4 または IPv6) の SNMP マネージャーに SNMPv3 トラップを送信し、呼び出し元で OID を直接指定できます。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター。
- **ip_address** SNMP マネージャーの IP アドレスへのポインター。
- **username** ユーザー名 (コミュニティ名)。
- **oid** OID を保持するバッファーへのポインター。
- **elapsed_time** システムの稼働時間 (sysUpTime)。
- **object_list_ptr** SNMP トラップに組み込むオブジェクトおよびそれに関連する値の配列。 リストは NX_NULL で終わります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) SNMP トラップの送信に成功。
- **NX_SNMP_ERROR** (0x100) SNMP トラップ送信エラー。
- **NX_PTR_ERROR** (0x16) SNMP エージェントまたはパラメーターへのポインターが無効。
- **NX_IP_ADDRESS_ERROR** (0x21) 宛先の IP アドレスが無効。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
NXD_ADDRESS         ip_address;
NX_SNMP_TRAP_OBJECT trap_list[5];

/* Build an empty object list */
trap_list[0].nx_snmp_object_string_ptr =  NX_NULL;

ip_address.nxd_ip_version = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4 = IP_ADDRESS(193,2,2,61);

/* Send trap to SNMP manager at 193.2.2.61.  */
Status =  nxd_snmp_agent_trapv3_oid_send(&my_agent, &ip_address, 
                                       "public", (UCHAR *)"0.9.9.9.9.9.9.9.9.9",  
                                       tx_time_get(), trap_list);

/* If status is NX_SUCCESS the SNMP trap has been sent.  */
```
## <a name="nx_snmp_agent_v3_context_boots_set"></a>nx_snmp_agent_v3_context_boots_set
再起動の回数を設定します (SNMPv3 が有効になっている場合)

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_agent_v3_context_boots_set(NX_SNMP_AGENT *agent_ptr, 
                                        UINT boots);
```

### <a name="description"></a>説明

このサービスでは、SNMP エージェントで記録する再起動の回数を設定します。 起動回数は SNMPv3 プロトコルでのみ使用されるため、このサービスは、SNMP エージェントで SNMPv3 が有効になっている場合のみ使用できます。

### <a name="input-parameters"></a>入力パラメーター

- **agent_ptr** SNMP エージェント制御ブロックへのポインター
- **boots** SNMP エージェントの起動回数として設定する値

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 起動回数の設定に成功
- **NX_SNMP_ERROR** (0x100) 起動回数設定エラー
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
UINT my_boots = 4;

if (my_agent.nx_snmp_agent_v3_enabled == NX_TRUE)
{
   status = nx_snmp_agent_v3_context_boots_set(&my_agent, my_boots);
}


/* If status is NX_SUCCESS the SNMP boot count is set.  */
```

## <a name="nx_snmp_object_compare"></a>nx_snmp_object_compare
2 つのオブジェクトを比較します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_object_compare(UCHAR *object, UCHAR *reference_object);
```

### <a name="description"></a>説明

このサービスでは、指定されたオブジェクト ID と参照オブジェクト ID を比較します。 どちらのオブジェクト ID も、SMI の表記形式の ASCII 文字列です。たとえば、どちらのオブジェクトも ASCII 文字列 “1.3.6” で始まる必要があります。

このサービスは推奨されなくなりました。 開発者は *nx_snmp_object_compare_extended()* に移行することを推奨します。

### <a name="input-parameters"></a>入力パラメーター

- **object** オブジェクト ID へのポインター。
- **reference_object** 参照オブジェクト ID へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オブジェクトが参照オブジェクトに一致。
- **NX_SNMP_NEXT_ENTRY** (0x101) オブジェクトが参照オブジェクトより小さいです。
- **NX_SNMP_ERROR** (0x100) オブジェクトが参照オブジェクトより大きいです。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare(requested_object, "1.3.6.1.2.1.1.1.0");

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_compare_extended"></a>nx_snmp_object_compare_extended
2 つのオブジェクトを比較します 

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_snmp_object_compare_extended(UCHAR *request_object, 
                                     UINT requested_object_length,
                                     UCHAR *reference_object
                                     UINT reference_object_length);
```
### <a name="description"></a>説明

このサービスでは、指定されたオブジェクト ID と参照オブジェクトID を比較します。 どちらのオブジェクト ID も、SMI の表記形式の ASCII 文字列です。たとえば、どちらのオブジェクトも ASCII 文字列 “1.3.6” で始まる必要があります。

これは *nx_snmp_object_compare()* の後継サービスです。 このバージョンでは、呼び出し元で長さを指定する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **request_object** 要求オブジェクト ID へのポインター。
- **request_object_length** 要求オブジェクトID の長さ。
- **reference_object** 参照オブジェクト ID へのポインター。
- **reference_object_length** 参照オブジェクト ID の長さ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オブジェクトが参照オブジェクトに一致。
- **NX_SNMP_NEXT_ENTRY** (0x101) オブジェクトが参照オブジェクトより小さいです。
- **NX_SNMP_ERROR** (0x100) オブジェクトが参照オブジェクトより大きいです。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Compare “requested_object” with the sysDescr object ID of 
   "1.3.6.1.2.1.1.1.0".  */
Status =  nx_snmp_object_compare_extended(requested_object, 17,
                                          "1.3.6.1.2.1.1.1.0", 17);

/* If status is NX_SUCCESS, requested_object is the sysDescr object. 
   Otherwise, if status is NX_SNMP_NEXT_ENTRY, the requested object is
   less than the sysDescr. If status is NX_SNMP_ERROR, the object is 
   greater than sysDescr. */
```

## <a name="nx_snmp_object_copy"></a>nx_snmp_object_copy
オブジェクトをコピーする 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_copy(UCHAR *source_object_name, 
                          UCHAR *destination_object_name);
```
### <a name="description"></a>説明

このサービスでは、SMI の表記形式の ASCII 文字列を使用するソース オブジェクトを、目的のオブジェクトにコピーします。

このサービスは推奨されなくなりました。 開発者は *nx_snmp_object_copy_extended()* に移行することを推奨します。

### <a name="input-parameters"></a>入力パラメーター

- **source_object_name** ソース オブジェクト ID へのポインター。
- **destination_object_name** コピー先のオブジェクト ID へのポインター。

### <a name="return-values"></a>戻り値

- **size** コピー先の名前にコピーするバイト数。 エラーが発生した場合は 0 を返します。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, my_new_object);

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_copy_extended"></a>nx_snmp_object_copy_extended
オブジェクトをコピーする 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_copy_extended(UCHAR *source_object_name, 
                             UINT source_object_name_length,
                             UCHAR *destination_object_name_buffer,
                             UINT destination_object_name_buffer_size);
```

### <a name="description"></a>説明

このサービスでは、SMI の表記形式の ASCII 文字列を使用するソース オブジェクトを、目的のオブジェクトにコピーします。

これは *nx_snmp_object_copy()* の後継サービスです。 このバージョンでは、呼び出し元で長さを指定する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **source_object_name** ソース オブジェクト ID へのポインター。
- **source_object_name_length** ソース オブジェクト ID の長さ。
- **destination_object_name_buffer** コピー先のオブジェクトのバッファーへのポインター。
- **destination_object_name_buffer_size** コピー先のオブジェクトのバッファーのサイズ。

### <a name="return-values"></a>戻り値

- **size** コピー先の名前にコピーするバイト数。 エラーが発生した場合は 0 を返します。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
UCHAR   my_object = "1.3.6.1.2.1.1.1.0";
UCHAR   my_new_object[32];


/* Copy “my_object” to “my_new_object”.  */
size =  nx_snmp_object_copy(my_object, 17, my_new_object, sizeof(my_new_object));

/* Size contains the number of bytes copied. */
```

## <a name="nx_snmp_object_counter_get"></a>nx_snmp_object_counter_get
カウンター オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_counter_get(VOID *source_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスのカウンター オブジェクトを取得し、それを NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** カウンターのソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) カウンター オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object.  */
status =  nx_snmp_object_counter_get(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter_set"></a>nx_snmp_object_counter_set
カウンター オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_counter_set(VOID *destination_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスのカウンターを、NetX オブジェクト データ構造体にあるカウンターの値に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** カウンターの設定先へのポインター。
- **object_data** カウンターのソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) カウンター オブジェクトの設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the ifInOctets (1.3.6.1.2.1.2.2.1.10.0) MIB-2 object with
   the counter object value contained in my_object.  */
status =  nx_snmp_object_counter_set(&ifInOctets, my_object);

/* If status is NX_SUCCESS, the ifInOctets object has been 
   set. */
```

## <a name="nx_snmp_object_counter64_get"></a>nx_snmp_object_counter64_get
64 ビットのカウンター オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_counter64_get(VOID *source_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスにある 64 ビットのカウンター オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** カウンターのソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) カウンター オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of my_64_bit_counter and place it into my_object
   for return.  */
status =  nx_snmp_object_counter64_get(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   retrieved and is ready to be returned. */
```

## <a name="nx_snmp_object_counter64_set"></a>nx_snmp_object_counter64_set
64 ビット カウンター オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_counter64_set(VOID *destination_ptr, 
                                   NX_SNMP_OBJECT_DATA *object_data);
```
### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスの 64 ビット カウンターを、NetX オブジェクト データ構造体にあるカウンターの値に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** カウンターの設定先へのポインター。
- **object_data** カウンターのソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) カウンター オブジェクトの設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of my_64_bit_counter with the value in my_object.  */
status =  nx_snmp_object_counter64_set(&my_64_bit_counter, my_object);

/* If status is NX_SUCCESS, the my_64_bit_counter object has been 
   set. */
```

## <a name="nx_snmp_object_end_of_mib"></a>nx_snmp_object_end_of_mib
end-of-mib (MIB の末尾) の値を設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_end_of_mib(VOID *not_used_ptr, 
                              NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、MIB の末尾を示すオブジェクトを作成します。通常 GET または GETNEXT アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **not_used_ptr** 使用しないポインター - NX_NULL にする必要があります。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) end-of-mib オブジェクトの構築に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Place an end-of-mib value in my_object.  */
status =  nx_snmp_object_end_of_mib(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now an end-of-mib object. */
```

## <a name="nx_snmp_object_gauge_get"></a>nx_snmp_object_gauge_get
ゲージ オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_gauge_get(VOID *source_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスのゲージ オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** ゲージのソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ゲージ オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of ifSpeed (1.3.6.1.2.1.2.2.1.5.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_gauge_get(&ifSpeed, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ifSpeed gauge value. */
```

## <a name="nx_snmp_object_gauge_set"></a>nx_snmp_object_gauge_set
ゲージ オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_gauge_set(VOID *destination_ptr,
                                     NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスのゲージを、NetX オブジェクト データ構造体にあるゲージの値に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** ゲージの設定先へのポインター。
- **object_data** ゲージのソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ゲージ オブジェクトの設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of “my_gauge” from the gauge value in my_object.  */
status =  nx_snmp_object_gauge_set(&my_gauge, my_object);

/* If status is NX_SUCCESS, the my_gauge now contains the new gauge value. */
```

## <a name="nx_snmp_object_id_get"></a>nx_snmp_object_id_get
オブジェクト ID を取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_id_get(VOID *source_ptr, 
                            NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスのオブジェクト ID (SMI の表記形式の ASCII 文字列) を取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** オブジェクト ID のソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オブジェクト ID の取得に成功。
- **NX_SNMP_ERROR** (0x100) オブジェクトの長さが無効
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of sysObjectID(1.3.6.1.2.1.1.2.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_id_get(&sysObjectID, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysObjectID value. */
```

## <a name="nx_snmp_object_id_set"></a>nx_snmp_object_id_set
オブジェクト ID を設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_id_set(VOID *destination_ptr, 
                             NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスのオブジェクト ID (SMI の表記形式の ASCII 文字列) を、NetX オブジェクト データ構造体にあるオブジェクト ID に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** オブジェクト ID の設定先へのポインター。
- **object_data** オブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オブジェクト ID の設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the string “my_object_id” with the object ID value contained 
   in my_object.  */
status =  nx_snmp_object_id_set(my_object_id, my_object);

/* If status is NX_SUCCESS, the my_object_id now contains the object ID value. */
```

## <a name="nx_snmp_object_integer_get"></a>nx_snmp_object_integer_get
整数オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_integer_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスの整数オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** 整数のソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 整数オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of sysServices (1.3.6.1.2.1.1.7.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_integer_get(&sysServices, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysServices value. */
```

## <a name="nx_snmp_object_integer_set"></a>nx_snmp_object_integer_set
整数オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_integer_set(VOID *destination_ptr,
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスの整数を、NetX オブジェクト データ構造体にある整数値に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** 整数の設定先へのポインター。
- **object_data** 整数のソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 整数オブジェクトの設定に成功しました。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of ifAdminStatus from the integer value in my_object.  */
status =  nx_snmp_object_integer_set(&ifAdminStatus, my_object);

/* If status is NX_SUCCESS, ifAdnminStatus now contains the new integer value. */
```

## <a name="nx_snmp_object_ip_address_get"></a>nx_snmp_object_ip_address_get
IP アドレス オブジェクトを取得します (IPv4 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_ip_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスの IP アドレス オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** IPv4 アドレスのソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレス オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ip_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ipv6_address_get"></a>nx_snmp_object_ipv6_address_get
IP アドレス オブジェクトを取得します (IPv6 のみ)

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_ipv6_address_get(VOID *source_ptr,
                                          NX_SNMP_OBJECT_DATA 
                                      *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスの IPv6 アドレス オブジェクトを取得し、NetX オブジェクト データ構造体に配置します。
このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** IPv6 アドレスのソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレス オブジェクトの取得に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) 入力した SNMP オブジェクト コードが無効
- **NX_NOT_ENABLED** (0x14) IPv6 が有効になっていません
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of ipAdEntAddr (1.3.6.1.2.1.4.20.1.1.0) and place it in my_object
   for return.  */
status =  nx_snmp_object_ipv6_address_get(&ipAdEntAddr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the ipAdEntAddr value. */
```

## <a name="nx_snmp_object_ip_address_set"></a>nx_snmp_object_ip_address_set
IPv4 アドレス オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_ip_address_set(VOID *destination_ptr, 
                                    NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定した IPv4 アドレスを、NetX オブジェクト データ構造体にある IP アドレスに設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** 設定先の IP アドレスへのポインター。
- **object_data** IP アドレス オブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレス オブジェクトの設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ip_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_ipv6_address_set"></a>nx_snmp_object_ipv6_address_set
IPv6 アドレス オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_ipv6_address_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA  
                                      *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定した IPv6 アドレスを、NetX オブジェクト データ構造体にある IP アドレスに設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** 設定先の IP アドレスへのポインター。
- **object_data** IP アドレス オブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IPv6 アドレスの設定に成功しました。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_NOT_ENABLED** (0x14) IPv6 が有効になっていません
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of atNetworkAddress to the IP address in my_object.  */
status =  nx_snmp_object_ipv6_address_set(&atNetworkAddress, my_object);

/* If status is NX_SUCCESS, atNetWorkAddress now contains the new IP address. */
```

## <a name="nx_snmp_object_no_instance"></a>nx_snmp_object_no_instance
インスタンス不在オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_no_instance(VOID *not_used_ptr, 
                                 NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、指定したオブジェクトのインスタンスが存在しなかったことを示すオブジェクトを作成します。通常 GET または GETNEXT アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **not_used_ptr** 使用しないポインター - NX_NULL にする必要があります。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) インスタンス不在オブジェクトの構築に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Place no-instance value in my_object.  */
status =  nx_snmp_object_no_instance(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a no-instance object. */
```

## <a name="nx_snmp_object_not_found"></a>nx_snmp_object_not_found
不検出オブジェクトを作成します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_not_found(VOID *not_used_ptr, 
                               NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、オブジェクトが見つからなかったことを示すオブジェクトを作成します。通常 GET または GETNEXT アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **not_used_ptr** 使用しないポインター - NX_NULL にする必要があります。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 不検出オブジェクトの構築に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Place not-found value in my_object.  */
status =  nx_snmp_object_not_found(NX_NULL, my_object);

/* If status is NX_SUCCESS, the my_object is now a not-found object. */
```

## <a name="nx_snmp_object_octet_string_get"></a>nx_snmp_object_octet_string_get
オクテット文字列オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_octet_string_get(VOID *source_ptr,
                                            NX_SNMP_OBJECT_DATA *object_data, 
                                      UINT length);
```
### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスのオクテット文字列を取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** オクテット文字列のソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。
- **length** オクテット文字列のバイト数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オクテット文字列オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of the 6-byte ifPhysAddress (1.3.6.1.2.1.2.2.1.6.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_octet_string_get(ifPhysAddress, my_object, 6);

/* If status is NX_SUCCESS, the my_object now contains the ifPhysAddress value. */
```

## <a name="nx_snmp_object_octet_string_set"></a>nx_snmp_object_octet_string_set
オクテット文字列オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_octet_string_set(VOID *destination_ptr, 
                                      NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスのオクテット文字列を、NetX オブジェクト データ構造体にあるオクテット文字列に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** オクテット文字列の設定先へのポインター。
- **object_data** オクテット文字列のソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オクテット文字列オブジェクトの設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   octet string in my_object.  */
status =  nx_snmp_object_octet_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new octet string. */
```

## <a name="nx_snmp_object_string_get"></a>nx_snmp_object_string_get
ASCII 文字列オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_string_get(VOID *source_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスの ASCII 文字列を取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** ASCII 文字列のソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ASCII 文字列オブジェクトの取得に成功。
- **NX_SNMP_ERROR** (0x100) 文字列が大きすぎます  
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of the sysDescr (1.3.6.1.2.1.1.1.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_string_get(sysDescr, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysDescr string. */
```

## <a name="nx_snmp_object_string_set"></a>nx_snmp_object_string_set
ASCII 文字列オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_string_set(VOID *destination_ptr, 
                                NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスの ASCII 文字列を、NetX オブジェクト データ構造体にある ASCII 文字列に設定します。 このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** ASCII 文字列の設定先へのポインター。
- **object_data** ASCII 文字列のソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ASCII 文字列オブジェクトの設定に成功。
- **NX_SNMP_ERROR** (0x100) 文字列が大きすぎます。
- **NX_SNMP_ERROR_BADVALUE** (0x03) 文字列中の文字が無効
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of sysContact (1.3.6.1.2.1.1.4.0) from the 
   ASCII string in my_object.  */
status =  nx_snmp_object_string_set(sysContact, my_object);

/* If status is NX_SUCCESS, sysContact now contains the new ASCII string. */
```

## <a name="nx_snmp_object_timetics_get"></a>nx_snmp_object_timetics_get
timetics オブジェクトを取得します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_timetics_get(VOID *source_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、ソースへのポインターで指定したアドレスの timetics を取得し、NetX オブジェクト データ構造体に配置します。 このルーチンは通常 GET または GETNEXT アプリケーション コールバックルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **source_ptr** timetics のソースへのポインター。
- **object_data** 配置先のオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) timetics オブジェクトの取得に成功。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Get the value of the sysUpTime (1.3.6.1.2.1.1.3.0) and place 
   it in my_object for return.  */
status =  nx_snmp_object_timetics_get(sysUpTime, my_object);

/* If status is NX_SUCCESS, the my_object now contains the sysUpTime value. */
```

## <a name="nx_snmp_object_timetics_set"></a>nx_snmp_object_timetics_set
timetics オブジェクトを設定します 

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_snmp_object_timetics_set(VOID *destination_ptr, 
                                  NX_SNMP_OBJECT_DATA *object_data);
```

### <a name="description"></a>説明

このサービスでは、設定先へのポインターで指定したアドレスの timetics 変数を、NetX オブジェクト データ構造体にある timetics に設定します。
このルーチンは通常 SET アプリケーション コールバック ルーチンから呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **destination_ptr** timetics の設定先へのポインター。
- **object_data** timetics のソースのオブジェクト構造体へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) timetics オブジェクトの設定に成功。
- **NX_SNMP_ERROR_WRONGTYPE** (0x07) オブジェクトの型が無効。
- **NX_PTR_ERROR** (0x07) 入力したポインターが無効

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the value of “my_time” from the timetics value in my_object.  */
status =  nx_snmp_object_timetics_set(&my_time, my_object);

/* If status is NX_SUCCESS, my_time now contains the new timetics. */
```