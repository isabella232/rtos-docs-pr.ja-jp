---
title: 第 4 章 - Azure RTOS NetX Duo DHCPv6 クライアント サービス
description: この章では、すべての Azure RTOS NetX Duo DHCPv6 クライアント サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6caf943f990f8fe5cbd2cd6139a1253fcaf47dc207141963e31a9e31864ef839
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791739"
---
# <a name="chapter-4---azure-rtos-netx-duo-dhcpv6-client-services"></a>第 4 章 - Azure RTOS NetX Duo DHCPv6 クライアント サービス

この章では、すべての Azure RTOS NetX Duo DHCPv6 クライアント サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

- **nx_dhcpv6_client_create:** "*DHCPv6 クライアント インスタンスを作成する*" 

- **nx_dhcpv6_client_delete:** "*DHCPv6 クライアント インスタンスを削除する*" 

- **nx_dhcpv6_create_client_duid:** "*DHCPv6 クライアント DUID を作成する*" 

- **nx_dhcpv6_add_client_ia:** "*DHCPv6 クライアントの ID アドレス (IA) を追加する*" 

- **nx_dhcpv6_create_client_ia:** ("*従来の DHCPv6 クライアントの ID アドレス (IA) を追加する*") 

- **nx_dhcpv6_create_client_iana:** "*DHCPv6 クライアントの非一時アドレス用 ID 関連付け (IANA) を作成する*" 

- **nx_dhcpv6_get_client_duid_time_id:** "*DHCPv6 クライアント DUID から時刻 ID を取得する*" 

- **nx_dhcpv6_client_set_interface:** "*DHCPv6 サーバーと通信するためのクライアント ネットワーク インターフェイスを設定する*" 

- **nx_dhcpv6_get_IP_address:** "*DHCPv6 クライアントに割り当てられたグローバル IPv6 アドレスを取得する*" 

- **nx_dhcpv6_get_lease_time_data:** "*クライアントのグローバル IPv6 アドレスの T1、T2、有効な有効期間、優先有効期間を取得する*"

- **nx_dhcpv6_get_valid_ip_address_lease_time:** "*DHCPv6 クライアントの IPv6 アドレスの T1、T2、有効な有効期間、優先有効期間をアドレス インデックスで取得する*" 

- **nx_dhcpv6_get_iana_lease_time:** "*DHCPv6 クライアントにリースされている ID 関連付け (IANA) の T1 と T2 を取得する*" 

- **nx_dhcpv6_get_other_option_data:** "*指定されたオプション データ (ドメイン名やタイム ゾーン サーバーなど) を取得する*" 

- **nx_dhcpv6_get_DNS_server_address:** "*DHCPv6 クライアントの DNS サーバー リストの指定されたインデックスにある DNS サーバー アドレスを取得する*" 

- **nx_dhcpv6_get_time_accrued:** "*グローバル IPv6 アドレス リースが DHCPv6 クライアントにバインドされている期間を取得する*" 

- **nx_dhcpv6_get_time_server_address:** "*DHCPv6 クライアントのタイム サーバー リストの指定されたインデックスにあるタイム サーバー アドレスを取得する*"

- **nx_dhcpv6_get_valid_ip_address_count:** "*DHCPv6 クライアントに割り当てられた IPv6 アドレスの数を取得する*" 

- **nx_dhcpv6_reinitialize:** "*DHCPv6 クライアント ステート マシンを再起動し、DHCPv6 プロトコルを再実行するために、DHCPv6 を再初期化する*" 

- **nx_dhcpv6_request_confirm:** "*CONFIRM 要求をサーバーに送信する*" 

- **nx_dhcpv6_request_inform_request:** "*INFORM REQUEST メッセージをサーバーに送信する*" 

- **nx_dhcpv6_request_release:** "*RELEASE 要求をサーバーに送信する*" 

- **nx_dhcpv6_request_option_DNS_server:** "*サーバーへの要求メッセージのクライアント オプション要求データに DNS サーバー オプションを追加する*" 

- **nx_dhcpv6_request_option_FQDN:** "*サーバーへの要求メッセージのクライアント オプション要求データに FQDN オプションを追加する*" 

- **nx_dhcpv6_request_option_domain_name:** "*サーバーへの要求メッセージのクライアント オプション要求データにドメイン名オプションを追加する*" 

- **nx_dhcpv6_request_option_time_server:** "*サーバーへの要求メッセージのクライアント オプション要求データにタイム サーバー オプションを追加する*" 

- **nx_dhcpv6_request_option_timezone:** "*サーバーへの要求メッセージのクライアント オプション要求データにタイム ゾーン オプションを追加する*" 

- **nx_dhcpv6_request_solicit:** "*クライアント ネットワーク上の任意のサーバーに DHCPv6 SOLICIT 要求を送信する (ブロードキャスト)* " 

- **nx_dhcpv6_request_solicit_rapid:** *Rapid Commit オプションを設定して、クライアント ネットワーク上の任意のサーバーに DHCPv6 SOLICIT 要求を送信する (ブロードキャスト)* 

- **nx_dhcpv6_resume:** "*DHCPv6 クライアントの処理を再開する*" 

- **nx_dhcpv6_start:** "*DHCPv6 クライアント スレッド タスクを開始する (これは DHCPv6 ステート マシンの起動と同じではなく、SOLICIT 要求は送信されないことに注意してください)* " 

- **nx_dhcpv6_stop:** "*DHCPv6 クライアント スレッド タスクを停止する*" 

- **nx_dhcpv6_suspend:** "*DHCPv6 クライアント スレッド タスクを中断する*" 

- **nx_dhcpv6_set_time_accrued:** "*クライアント レコードにクライアントのグローバル IPv6 アドレス リースの経過時間を設定する*"

## <a name="nx_dhcpv6_client_create"></a>nx_dhcpv6_client_create

DHCPv6 クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_dhcpv6_client_create(NX_DHCPV6 *dhcpv6_ptr, 
                        NX_IP *ip_ptr, CHAR *name_ptr, 
                        NX_PACKET_POOL *packet_pool_ptr, 
                        VOID *stack_ptr, ULONG stack_size,
                        VOID (*dhcpv6_state_change_notify)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                  UINT old_state, UINT new_state), 
                        VOID (*dhcpv6_server_error_handler)
                                 (struct NX_DHCPV6_STRUCT *dhcpv6_ptr, 
                                 UINT op_code, UINT status_code, 
                                 UINT message_type));
```

### <a name="description"></a>説明

このサービスでは、コールバック関数を含む DHCPv6 クライアント インスタンスを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 制御ブロックへのポインター  

- **ip_ptr**: クライアント IP インスタンスへのポインター  

- **name_ptr**: DHCPv6 インスタンスの名前へのポインター

- **packet_pool_ptr**: クライアントのパケット プールへのポインター

- **stack_ptr**: クライアントのスタック メモリへのポインター

- **stack_ptr**: クライアントのスタック メモリのサイズ

- **dhcpv6_state_change_notify**: クライアントがサーバーに対して新しい DHCPv6 要求を開始したときに呼び出されるコールバック関数へのポインター

- **dhcpv6_server_error_handler**: クライアントがサーバーからエラー状態を受信したときに呼び出されるコールバック関数へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に作成されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Create a DHCPv6 client instance without specifying link local or preferred
   global IP address.  */
status =  nx_dhcpv6_client_create(&dhcp_0, &ip_0, "DHCPv6 Client", &pool_0,
                                  NULL, NULL, pointer, 2048,        
                                  dhcpv6_state_change_notify, 
                                  dhcpv6_server_error_handler);

/* If status is NX_SUCCESS a DHCPv6 client instance was successfully
   created.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_client_delete

## <a name="nx_dhcpv6_client_delete"></a>nx_dhcpv6_client_delete

DHCPv6 クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_client_delete(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された DHCPv6 クライアント インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCPv6 が正常に削除されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete a DHCPv6 client instance.  */
status =  nx_dhcpv6_client_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCPv6 client instance was successfully
   deleted.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_client_create

## <a name="nx_dhcpv6_client_set_interface"></a>nx_dhcpv6_client_set_interface

クライアントの DHCPv6 用ネットワーク インターフェイスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT    nx_dhcpv6_client_set_interface(NX_DHCPV6 *dhcpv6_ptr, 
                                       UINT *interface_index);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 サーバーと通信するためのクライアントのネットワーク インターフェイスを、指定された入力インターフェイス インデックスに設定します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **interface_index**: ネットワーク インターフェイスを示すインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_INVALID_INTERFACE: (0x4C) インターフェイス インデックス入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the client interface for DHCPv6 communication with the Server to 
   the secondary interface (1). */

UINT index = 1;
status = nx_dhcpv6_client_set_interface(&dhcp_0, index);

/* If status is NX_SUCCESS, the Client successfully set 
   the DHCPv6 network interface.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_client_create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_client_set_destination_address"></a>nx_dhcpv6_client_set_destination_address

DHCPv6 メッセージの送信先となる宛先アドレスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_client_set_destination_address(NX_DHCPV6 *dhcpv6_ptr,
                                              NXD_ADDRESS *destination_address);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 メッセージの送信先となる宛先アドレスを設定します。 既定値は ALL_DHCP_Relay_Agents_and_Servers(FF02::1:2) です。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **destination_address**: 宛先アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました

- NX_PTR_ERROR: (0x07) ポインター入力が無効です

- NX_DHCPV6_PARAM_ERROR: (0xE93) Parament エラー

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the destination address where DHCPv6 message should be sent to. */

NXD_ADDRESS dest_address; /* Set the destination address.  */

status = nx_dhcpv6_client_set_destination_address(&dhcp_0, &dest_address);

/* If status is NX_SUCCESS, the Client successfully set the destination address. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_client_create
- nx_dhcpv6_start

## <a name="nx_dhcpv6_create_client_duid"></a>nx_dhcpv6_create_client_duid

クライアント DUID オブジェクトを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_create_client_duid(NX_DHCPV6 *dhcpv6_ptr,
                                  UINT duid_type, UINT hardware_type,
                                  ULONG time);
```

### <a name="description"></a>説明

このサービスでは、入力パラメーターを使用してクライアント DUID を作成します。 時刻入力が指定されておらず、DUID の種類が "リンク層と時刻" を示している場合、この関数によって、一意性を確保するためのランダム化係数を含む時刻が指定されます。 DUID の種類としてベンダー割り当て (エンタープライズ) はサポートされていません。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **duid_type**: DUID の種類 (ハードウェア、エンタープライズなど)

- **hardware_type**: ネットワーク ハードウェア (IEEE 802 など)

- **time**: 一意識別子の作成に使用する値

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアント DUID が正常に作成されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です

- NX_DHCPV6_UNSUPPORTED_DUID_TYPE: (0xE98) DUID の種類が不明であるか、サポートされていません 

- NX_DHCPV6_UNSUPPORTED_DUID_HW_TYPE: (0xE99) DUID のハードウェアの種類が不明であるか、サポートされていません

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Create the Client DUID from the supplied input.
   The time field is left NULL so the DHCPv6 client will provide one.  */
status = nx_dhcpv6_create_client_duid(&dhcp_0, NX_DHCPV6_DUID_TYPE_LINK_TIME,
                                      NX_DHCPV6_HW_TYPE_IEEE_802, 0)

/* If status is NX_SUCCESS the client DUID was successfully created.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_create_client_ia
- nx_dhcpv6_create_client_iana
- nx_dhcpv6_create_server_duid

## <a name="nx_dhcpv6_create_client_ia"></a>nx_dhcpv6_create_client_ia

ID 関連付けをクライアントに追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_create_client_ia(NX_DHCPV6 *dhcpv6_ptr,
                                NXD_ADDRESS *ipv6_address,
                                ULONG preferred_lifetime,
                                ULONG valid_lifetime);
```

### <a name="description"></a>説明

このサービスは、*nx_dhcpv6_add_client_ia* サービスと同じです。 指定されたパラメーターをクライアント レコードに入力することによって、クライアントの ID 関連付けを追加します。 優先有効期間と有効な有効期間の最大値を要求するには、これらのパラメーターを無限大に設定します。 DHCPv6 クライアントに複数の IA を追加するには、NX_DHCPV6_MAX_IA_ADDRESS を既定値の 1 より大きい値に設定します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **ipv6_address**: NetX Duo IP アドレス ブロックへのポインター

- **preferred_lifetime**: IP アドレスが非推奨になるまでの時間

- **valid_lifetime**: IP アドレスの有効期限が切れるまでの時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントの IA が正常に追加されました

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**: (0xEAF) IA アドレスが重複しています 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS**: (0xEAE) IA が、クライアントが保存できる IA の最大数を超えています

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_INVALID_IA_ADDRESS: (0xEA4) IA の IA アドレスが無効です (null など)

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_create_client_ia(&dhcp_0, &ipv6_address, 
NX_DHCPV6_PREFERRED_LIFETIME, NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_add_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_create_client_iana"></a>nx_dhcpv6_create_client_iana

クライアントの ID 関連付け (非一時) を作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_create_client_iana(NX_DHCPV6 *dhcpv6_ptr, 
                                  UINT IA_ident, ULONG T1, ULONG T2);
```

### <a name="description"></a>説明

このサービスでは、指定されたパラメーターからクライアントの非一時 ID 関連付け (IANA) を作成します。 DHCPv6 クライアント要求で T1 および T2 時間を最大 (無限大) に設定するには、これらのパラメーターを NX_DHCPV6_INFINITE_LEASE に設定します。 

> [!NOTE]
> クライアントには IANA は 1 つしかありません。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **IA_ident**: ID 関連付け一意識別子

- **T1**: クライアントが IPv6 アドレスの更新を開始する必要がある時間

- **T2**: クライアントが IPv6 アドレスの再バインドを開始する必要がある時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IANA が正常に作成されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Create the Client IANA from the supplied input.  */
status = nx_dhcpv6_create_client_iana(&dhcp_0, DHCPV6_IA_ID, DHCPV6_T1,   
                                      DHCPV6_T2);

/* If status is NX_SUCCESS the client IANA was successfully created.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_add_client_ia

## <a name="nx_dhcpv6_add_client_ia"></a>nx_dhcpv6_add_client_ia 

ID 関連付けをクライアントに追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_add_client_ia(NX_DHCPV6 *dhcpv6_ptr, 
                             NXD_ADDRESS *ipv6_address, 
                             ULONG preferred_lifetime, 
                             ULONG valid_lifetime);
```

### <a name="description"></a>説明

このサービスでは、指定されたパラメーターをクライアント レコードに入力することによって、クライアントの ID 関連付けを追加します。 優先有効期間と有効な有効期間の最大値を要求するには、これらのパラメーターを無限大に設定します。 DHCPv6 クライアントに複数の IA を追加するには、NX_DHCPV6_MAX_IA_ADDRESS を既定値の 1 より大きい値に設定します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **ipv6_address**: NetX Duo IP アドレス ブロックへのポインター

- **preferred_lifetime**: IP アドレスが非推奨になるまでの時間

- **valid_lifetime**: IP アドレスの有効期限が切れるまでの時間 

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントの IA が正常に追加されました

- **NX_DHCPV6_IA_ADDRESS_ALREADY_EXIST**: (0xEAF) IA アドレスが重複しています 

- **NX_DHCPV6_REACHED_MAX_IA_ADDRESS**: (0xEAE) IA が、クライアントが保存できる IA の最大数を超えています

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_INVALID_IA_ADDRESS: (0xEA4) IA の IA アドレスが無効です (null など)

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です

 
### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Add an Client IA using the supplied input.   */
status = nx_dhcpv6_add_client_ia(&dhcp_0, &ipv6_address, 
                                 NX_DHCPV6_PREFERRED_LIFETIME,
                                 NX_DHCPV6_VALID_LIFETIME);

/* If status is NX_SUCCESS the client IA was successfully added.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_create_client_duid
- nx_dhcpv6_create_server_duid
- nx_dhcpv6_create_client_iana

## <a name="nx_dhcpv6_get_client_duid_time_id"></a>nx_dhcpv6_get_client_duid_time_id

クライアント DUID から時刻 ID を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_client_duid_time_id(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_id);
```

### <a name="description"></a>説明

このサービスでは、クライアント DUID から時刻 ID フィールドを取得します。 DHCPv6 クライアント インスタンスのクライアント DUID を入力するために、アプリケーションで最初に *nx_dhcpv6_create_client_duid* を呼び出す必要がある場合、このフィールドには null 値が設定されます。 これは、アプリケーションがこのデータを保存し、再起動のたびに時刻フィールドを含む同じクライアント DUID をサーバーに提示することを目的としています。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **time_id**: クライアント DUID の時刻フィールドへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IP リース データが正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve the time ID from the Client DUID.  */
status = nx_dhcpv6_get_client_duid_time_id(&dhcp_0, &time_ID);

/* If status is NX_SUCCESS the time ID was retrieved. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_time_lease_data
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_ip_address"></a>nx_dhcpv6_get_IP_address

クライアントのグローバル IPv6 アドレスを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address);
```

### <a name="description"></a>説明

このサービスでは、クライアントのグローバル IPv6 アドレスを取得します。 クライアントに有効なアドレスがない場合は、エラー状態が返されます。 クライアントに複数のグローバル IPv6 アドレスがある場合は、プライマリ IPv6 アドレスが返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **ip_address**: IPv6 アドレスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IPv6 アドレスが正常に割り当てられました

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID**: (0xEAD) IPv6 アドレスが無効です

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UINT address_status;
UINT address_index;

/* Retrieve the client’s assigned IP address.  */
status = nx_dhcpv6_get_IP_address(&dhcp_0, &ipv6_address);

/* If status is NX_SUCCESS the client IP address was assigned.
   Now register it with NetX Duo on the primary interface (index zero). 
   The address index is returned in the address_index field*/
status = nxd_ipv6_address_set(&ip_0, 0, &ipv6_address, 64, &address_index);
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_lease_time_data"></a>nx_dhcpv6_get_lease_time_data

クライアントの IA アドレスのリース時間データを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_lease_time_data(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                   ULONG *T2, ULONG *preferred_lifetime, 
                                   ULONG *valid_lifetime);
```

### <a name="description"></a>説明

このサービスでは、クライアントのグローバル IA アドレスの時間データを取得します。 クライアントの IA アドレスの状態が無効の場合、時間データは 0 に設定され、正常完了状態が返されます。 クライアントに複数のグローバル IPv6 アドレスがある場合は、プライマリ IA アドレス データが返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **T1**: IA アドレス更新時間へのポインター

- **T2**: IA アドレス再バインド時間へのポインター

- **preferred_lifetime**: IA アドレスが非推奨になる時間へのポインター

- **valid_lifetime**: IA アドレスの有効期限が切れる時間へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IA リース データが正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve the client’s assigned IA lease data.  */
status = nx_dhcpv6_get_lease_time_data(&dhcp_0, &T1, &T2, &preferred_lifetime, 
                                       &valid_lifetime);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_iana_lease_time

## <a name="nx_dhcpv6_get_iana-lease_time"></a>nx_dhcpv6_get_iana_lease_time

クライアントの IANA のリース時間データを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_iana_lease_time(NX_DHCPV6 *dhcpv6_ptr, ULONG *T1, 
                                    ULONG *T2);
```

### <a name="description"></a>説明

このサービスでは、クライアントのグローバル IA-NA のリース時間データ (T1 と T2) を取得します。 クライアントの IA-NA アドレスの状態が無効の場合、時間データは 0 に設定され、正常完了状態が返されます。 クライアントに複数のグローバル IPv6 アドレスがある場合は、プライマリ IA アドレス データが返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **T1**: リースの更新を開始する時間へのポインター

- **T2**: リースの再バインドを開始する時間へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IANA リース データが正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve the client’s assigned IANA lease data.  */
status = nx_dhcpv6_get_iana_lease_time(&dhcp_0, &T1, &T2);

/* If status is NX_SUCCESS the client IA address lease data was retrieved.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_client_duid_time_id
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_valid_ip_address_count"></a>nx_dhcpv6_get_valid_ip_address_count

クライアントの有効な IA アドレスの数を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count);
```

### <a name="description"></a>説明

このサービスでは、クライアントの有効な IPv6 アドレスの数を取得します。 有効な IPv6 アドレスがクライアントにバインドされ (割り当てられ)、IP インスタンスに登録されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **address_count**: 返されるアドレス数へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IANA リース データが正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UINT address_count; 

/* Retrieve the count of valid IA-NA addresses.  */
status = nx_dhcpv6_get_valid_ip_address_count(&dhcp_0, &address_count);

/* If status is NX_SUCCESS the client IA address count was retrieved.  */
```

## <a name="nx_dhcpv6_get_valid_ip_address_lease_time"></a>nx_dhcpv6_get_valid_ip_address_lease_time

クライアントの IA データをアドレス インデックスで取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                               UINT address_index,
                                               NXD_ADDRESS *ip_address,
                                               ULONG *preferred_lifetime,
                                               ULONG *valid_lifetime);
```

### <a name="description"></a>説明

このサービスでは、クライアントの IA アドレスとリース データをアドレス インデックスで取得します。 無効なインデックスが指定された場合、またはそのインデックスにある IPv6 アドレスが無効な場合は、NX_DHCPV6_IA_ADDRESS_NOT_VALID エラー状態が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **address_index**: DHCPv6 IA テーブルへのインデックス

- **ip_address**: 取得する IPv6 アドレスへのポインター

- **preferred_lifetime**: IA アドレスが非推奨になる時間へのポインター

- **valid_lifetime**: IA アドレスの有効期限が切れる時間へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) IANA データが正常に取得されました

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID**: (0xEAD) インデックスが無効であるか、指定されたインデックスにある IPv6 アドレスが無効です 

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UINT address_index = 1; 
NXD_ADDRESS *ip_address;

/* Retrieve the IPv6 address, and valid and preferred lifetime for the IA record
   Saved at index 1 in the DHCPv6 table.  */
status = nx_dhcpv6_get_valid_ip_address_lease_time(&dhcp_0, address_index, 
                                                   &ip_address, 
                                                   &preferred_lifetime,  
                                                   &valid_lifetime);

/* If status is NX_SUCCESS the client IA address and lease data were retrieved.  */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_iana_lease_time
- nx_dhcpv6_get_lease_time_data

## <a name="nx_dhcpv6_get_dns_server_address"></a>nx_dhcpv6_get_DNS_server_address

DNS サーバー アドレスを取得する 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_DNS_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index,
                                      NXD_ADDRESS *server_address);
```

### <a name="description"></a>説明

このサービスでは、クライアント リストの指定されたインデックスにある DNS サーバー IPv6 アドレス データを取得します。 リストのそのインデックスにサーバー アドレスがない場合は、エラーが返されます。 インデックスは、ユーザーが構成可能な NX_DHCPV6_NUM_DNS_SERVERS オプションで指定された DNS サーバー リストのサイズを超えることはできません。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **index**: DNS サーバー リストへのインデックス

- **server_address**: サーバー アドレス バッファーへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) アドレスが正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve the DNS server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


        status = nx_dhcpv6_get_DNS_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the DNS server IP address successfully retrieved. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_other_option_data"></a>nx_dhcpv6_get_other_option_data

DHCPv6 オプション データを取得する 

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_dhcpv6_get_other_option_data(NX_DHCPV6 *dhcpv6_ptr, 
                                      UINT option_code, UCHAR *buffer);
```

### <a name="description"></a>説明

このサービスでは、指定されたオプション コードの DHCPv6 オプション データを DHCPv6 メッセージから取得します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **option_code**: 取得するデータのオプション コード

- **buffer**: データのコピー先のバッファーへのポインター 

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) オプション データが正常に取得されました

- **NX_DHCPV6_UNKNOWN_OPTION**: (0xEAB) オプション コードが不明であるか、サポートされていません

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_DHCPV6_PARAM_ERROR: (0xE93) 非ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve the option data specified by the input option code. */
status = nx_dhcpv6_get_other_option_data(&dhcp_0, option_code, buffer);

/* If status is NX_SUCCESS the option data was retrieved. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_get_time_accrued"></a>nx_dhcpv6_get_time_accrued

クライアントの IP アドレス リースの経過時間を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_get_time_accrued(NX_DHCPV6 *dhcpv6_ptr, ULONG *time_accrued);
```

### <a name="description"></a>説明

このサービスでは、クライアントの IPv6 アドレス リースの経過時間を取得します。 この関数は、クライアントに割り当てられたすべての IPv6 アドレスをチェックして最初の有効なアドレスを探します。 有効なアドレスが見つからない場合、経過時間の値として 0 が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **time_accrued**: IP リースの経過時間へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 経過時間が正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve time accrued time on the Client address lease. */
status = nx_dhcpv6_get_time_accrued(&dhcp_0, &time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address 
   lease was retrieved. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_set_time_accrued

## <a name="nx_dhcpv6_get_time_server_address"></a>nx_dhcpv6_get_time_server_address

タイム サーバー アドレスを取得する 

### <a name="prototype"></a>プロトタイプ

```C
UINT  nx_dhcpv6_get_time_server_address(NX_DHCPV6 *dhcpv6_ptr, UINT index, 
                                        NXD_ADDRESS *server_address);
```

### <a name="description"></a>説明

このサービスでは、クライアント リストの指定されたインデックスにあるタイム サーバーの IPv6 アドレス データを取得します。 リストのそのインデックスにサーバー アドレスがない場合は、エラーが返されます。 インデックスは、ユーザーが構成可能な NX_DHCPV6_NUM_TIME_SERVERS オプションで指定されたタイム サーバー リストのサイズを超えることはできません。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **index**: タイム サーバー リストへのインデックス

- **server_address**: サーバー アドレス バッファーへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) アドレスが正常に取得されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Retrieve the Time server at the specified index in the list. */

UINT index = 0;
NXD_ADDRESS server_address;


      status = nx_dhcpv6_get_time_server_address(&dhcp_0, index, &server_address);

/* If status == NX_SUCCESS, the Time server IP address successfully retrieved. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued
- nx_dhcpv6_get_DNS_server_address

## <a name="nx_dhcpv6_reinitialize"></a>nx_dhcpv6_reinitialize

IP テーブルからクライアント IP アドレスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_reinitialize(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 ステート マシンを再起動し、DHCPv6 プロトコルを再実行するために、クライアントを再初期化します。 クライアントが DHPCv6 ステート マシンをまだ起動していない場合、または IPv6 アドレスが割り当てられていない場合、これは不要です。 DHCPv6 クライアントに保存されているアドレスと、IP インスタンスに登録されているアドレスは、どちらもクリアされます。

> [!NOTE]
> アプリケーションでは、*nx_dhcpv6_start サービス* を使用して DHCPv6 クライアントを起動し、*nx_dhcpv6_request_solicit* を呼び出して IPv6 アドレス割り当ての要求を開始する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) アドレスが正常に削除されました

- **NX_DHCPV6_ALREADY_STARTED**: (0xE91) DHCPv6 クライアントは既に実行されています

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Clear the assigned IP address(es) from the Client and the IP instance */
status = nx_dhcpv6_reinitialize(&dhcp_0);

/* If status is NX_SUCCESS the Client IP address was successfully removed. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_stop
- nx_dhcpv6_start

## <a name="nx_dhcpv6_request_confirm"></a>nx_dhcpv6_request_confirm

クライアントの CONFIRM 状態を処理する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_confirm(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスは、CONFIRM 要求を送信します。 サーバーから応答を受信すると、DHCPv6 クライアントは受信したデータでリース パラメーターを更新します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) CONFIRM メッセージが正常に送信され、処理されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send a CONFIRM message to the Server. */
status = nx_dhcpv6_request_confirm(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the CONFIRM message. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release
- nx_dhcpv6_request_solicit


## <a name="nx_dhcpv6_request_inform_request"></a>nx_dhcpv6_request_inform_request

クライアントの INFORM REQUEST 状態を処理する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_inform_request(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、INFORM REQUEST メッセージを送信します。 応答を受信すると、応答が処理され、それが有効であり、サーバーが要求に応じたことが確認されます。 その後、クライアント インスタンスは、必要に応じてサーバー情報で更新されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) INFORM REQUEST メッセージが正常に作成され、処理されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send an INFORM REQUEST message to the server. */
status = nx_dhcpv6_request_inform_request(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the INFORM REQUEST 
   message and processed the reply. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_confirm

## <a name="nx_dhcpv6_request_option_dns_server"></a>nx_dhcpv6_request_option_DNS_server

DHCPv6 オプション要求に DNS サーバーを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_option_DNS_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 オプション要求に、DNS サーバー情報を要求するためのオプションを追加します。 サーバーの応答に DNS サーバー データが含まれている場合、クライアントは DNS サーバーを保存する余地があれば保存します。 クライアントが保存できる DNS サーバーの数は、構成可能な NX_DHCPV6_NUM_DNS_SERVERS オプションによって決まります。既定値は 2 です。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS サーバー オプションが含まれています

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the DNS server option in Client requests. */
nx_dhcpv6_request_option_DNS_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_fqdn"></a>nx_dhcpv6_request_option_FQDN

オプション要求リストに完全修飾ドメイン名オプションを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_option_FQDN(NX_DHCPV6 *dhcpv6_ptr, UCHAR *domain_name, 
UINT op);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 オプション要求に、クライアントの完全修飾ドメイン名を追加するためのオプションを追加します。 FQDN オプションには、3 つのオプションがあります。

- NX_DHCPV6_CLIENT_DESIRES_UPDATE_AAAA_RR 0: クライアントで使用される FQDN とアドレスについて、FQDN から IPv6 アドレスへのマッピングを更新します。

- NX_DHCPV6_CLIENT_DESIRES_SERVER_DO_DNS_UPDATE 1: クライアントでサーバーに対して使用される FQDN とアドレスについて、FQDN から IPv6 アドレスへのマッピングを更新します。

- NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE 2: クライアントに代わって DNS 更新を実行しないようサーバーに要求します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **domain_name**: ドメイン名を保持する文字列

- **op**: 適用する FQDN オプションの種類 (上記の一覧を参照)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FQDN オプションが含まれています

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the FQDN option in Client DHCPv6 request. */
nx_dhcpv6_request_option_FQDN(&dhcp_0, “DHCPv6_Client”, 
                              NX_DHCPV6_CLIENT_DESIRES_NO_SERVER_DNS_UPDATE);
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_domain_name"></a>nx_dhcpv6_request_option_domain_name

DHCPv6 オプション要求にドメイン名オプションを追加する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_option_domain_name(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、クライアント要求メッセージのオプション要求にドメイン名オプションを追加します。 サーバーの応答にドメイン名データが含まれている場合、ドメイン名のサイズがドメイン名を保持するためのバッファー サイズ内であれば、クライアントはドメイン名情報を保存します。 このバッファー サイズは構成可能なオプション (NX_DHCPV6_DOMAIN_NAME_BUFFER_SIZE) であり、既定値は 30 バイトです。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) ドメイン名オプションが設定されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the domain name option in Client requests. */
nx_dhcpv6_request_option_domain_name(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_time_server
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_time_server"></a>nx_dhcpv6_request_option_time_server

オプション要求としてタイム サーバー データを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_option_time_server(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、クライアント要求メッセージのオプション要求に、タイム サーバー情報のオプションを追加します。 サーバーの応答にタイム サーバー データが含まれている場合、クライアントはタイム サーバーを保存する余地があれば保存します。 クライアントが保存できるタイム サーバーの数は、構成可能な NX_DHCPV6_NUM_TIME _SERVERS オプションによって決まります。既定値は 1 です。

NX_DHCPV6_NUM_TIME _SERVERS の既定値は 1 です。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) タイム サーバー オプションが追加されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the time server option in Client request messages. */
nx_dhcpv6_request_option_time_server(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_timezone

## <a name="nx_dhcpv6_request_option_timezone"></a>nx_dhcpv6_request_option_timezone

オプション要求としてタイム ゾーン データを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_option_timezone(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、クライアント オプション要求に、タイム ゾーン情報を要求するためのオプションを追加します。 サーバーの応答にタイム ゾーン データが含まれている場合、タイム ゾーンのサイズがタイム ゾーンを保持するためのバッファー サイズ内であれば、クライアントはタイム ゾーン情報を保存します。 このバッファー サイズは構成可能なオプション (NX_DHCPV6_TIME_ZONE_BUFFER_SIZE) であり、既定値は 10 バイトです。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) タイム ゾーン オプションが追加されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set time zone option in Client request messages. */
nx_dhcpv6_request_option_timezone(&dhcp_0, NX_TRUE);
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_option_DNS_server
- nx_dhcpv6_request_option_domain_name
- nx_dhcpv6_request_option_time_server

## <a name="nx_dhcpv6_request_release"></a>nx_dhcpv6_request_release

DHCPv6 RELEASE メッセージを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_release(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、クライアント ネットワーク上で RELEASE メッセージを送信します。 メッセージが正常に送信されると、成功状態が返されます。 正常完了は、クライアントが応答を受信したことや、IPv6 アドレスが既に付与されていることを意味するわけではありません。 DHCPv6 クライアント スレッド タスクは、DHCPv6 サーバーからの応答を待機します。 応答を受信すると、それが有効であることを確認し、データをクライアント レコードに保存します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) RELEASE メッセージが正常に送信されました

- **NX_DHCPV6_NOT_STARTED**: (0xE92) DHCPv6 クライアント タスクが開始されていません

- **NX_DHCPV6_IA_ADDRESS_NOT_VALID**: (0xEAD) クライアントにアドレスがバインドされていません

- **NX_INVALID_INTERFACE**: (0x4C) IP アドレス テーブルに見つかりません

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send an RELEASE message to the Server. */
status = nx_dhcpv6_request_release(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the RELEASE message. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_solicit

## <a name="nx_dhcpv6_request_solicit"></a>nx_dhcpv6_request_solicit

SOLICIT メッセージを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_solicit(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、ネットワーク上で SOLICIT メッセージを送信します。 メッセージが正常に送信されると、成功状態が返されます。 正常完了は、クライアントが応答を受信したことや、IPv6 アドレスが既に付与されていることを意味するわけではありません。 DHCPv6 クライアント スレッド タスクは、DHCPv6 サーバーからの応答 (ADVERTISE メッセージ) を待機します。 応答を受信すると、それが有効であることを確認し、データをクライアント レコードに保存して、クライアントを REQUEST 状態に昇格させます。

> [!NOTE] 
> Rapid Commit オプションを設定した場合、DHCPv6 クライアントは、サーバーの有効な ADVERTISE メッセージを受信すると、BOUND 状態に直接移行します。 詳細については、*nx_dhcpv6_request_solicit_rapid* のサービスの説明を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) SOLICIT メッセージが正常に送信されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

## <a name="nx_dhcpv6_request_solicit_rapid"></a>nx_dhcpv6_request_solicit_rapid

Rapid Commit オプションを使用して SOLICIT メッセージを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_request_solicit_rapid(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、Rapid Commit オプションを設定して、ネットワーク上で SOLICIT メッセージを送信します。 メッセージが正常に送信されると、成功状態が返されます。 正常完了は、クライアントが応答を受信したことや、IPv6 アドレスが既に付与されていることを意味するわけではありません。 DHCPv6 クライアント スレッド タスクは、DHCPv6 サーバーからの応答 (ADVERTISE メッセージ) を待機します。 応答を受信すると、それが有効であることを確認し、データをクライアント レコードに保存して、クライアントを BOUND 状態に昇格させます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) SOLICIT メッセージが正常に送信されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send an SOLICIT message to the server. */
status = nx_dhcpv6_request_solicit_rapid(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully sent the SOLICIT message. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_request_solicit
- nx_dhcpv6_request_confirm
- nx_dhcpv6_request_inform_request
- nx_dhcpv6_request_release

## <a name="nx_dhcpv6_resume"></a>nx_dhcpv6_resume

DHCPv6 クライアント タスクを再開する 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_resume(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 クライアント スレッド タスクを再開します。 DHCPv6 クライアントの現在の状態 (Bound、Solicit など) が処理されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に再開されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Resume the DHCPv6 Client task. */
status = nx_dhcpv6_resume(&dhcp_0);

/* If status is NX_SUCCESS the Client thread task successfully resumed. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_start
- nx_dhcpv6_stop
- nx_dhcpv6_suspend

## <a name="nx_dhcpv6_set_-time_accrued"></a>nx_dhcpv6_set_time_accrued

クライアントの IP アドレス リースの経過時間を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_set_time_accrued(NX_DHCPV6 *dhcpv6_ptr,
                                ULONG time_accrued);
```

### <a name="description"></a>説明

このサービスでは、クライアントのグローバル IP アドレスがサーバーによって割り当てられてからの経過時間を設定します。 これは、割り当てられた IPv6 アドレスにクライアントが現在バインドされている場合にのみ使用する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

- **time_accrued**: IP リースの経過時間

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 経過時間が正常に設定されました

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set time accrued since client’s assigned IP address was assigned. */
status = nx_dhcpv6_set_time_accrued(&dhcp_0, time_accrued);

/* If status is NX_SUCCESS the time accrued on the client IP address lease was 
   successfully set. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_get_IP_address
- nx_dhcpv6_get_other_option_data
- nx_dhcpv6_get_lease_time_data
- nx_dhcpv6_get_time_accrued

## <a name="nx_dhcpv6_start"></a>nx_dhcpv6_start

DHCPv6 クライアント タスクを開始する 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_start(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 クライアント タスクを開始し、DHCPv6 プロトコルを実行するためにクライアントを準備します。 クライアント インスタンスに十分な情報 (クライアント DUID など) があることを確認し、DHCPv6 メッセージを送受信するための UDP ソケットを作成してバインドします。また、セッション時間と現在の IPv6 リースの有効期限を追跡するためのタイマーをアクティブにします。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に起動されました

- **NX_DHCPV6_MISSING_REQUIRED_OPTIONS**: (0xEA9) クライアントに必要なオプションがありません

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully started. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_stop
- nx_dhcpv6_reinitialize

## <a name="nx_dhcpv6_stop"></a>nx_dhcpv6_stop

DHCPv6 クライアント タスクを停止する 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_stop(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 クライアント タスクを停止し、再送信回数と最大再送信間隔をクリアします。また、セッションとリースの有効期限のタイマーを非アクティブ化し、DHCPv6 クライアント ソケット ポートのバインドを解除します。 クライアントを再起動するには、DHCPv6 サーバーとの別のセッションを開始する前に、まずクライアントを停止し、必要に応じて再初期化する必要があります。 詳細については、簡単な例のセクションを参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に停止されました

- **NX_DHCPV6_NOT_STARTED**: (0xE92) クライアント スレッドが開始されていません

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop the DHCPv6 Client task. */
status = nx_dhcpv6_start(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully stopped. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_resume
- nx_dhcpv6_suspend
- nx_dhcpv6_reinitialize
- nx_dhcpv6_start

## <a name="nx_dhcpv6_suspend"></a>nx_dhcpv6_suspend

DHCPv6 クライアント タスクを中断する 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcpv6_suspend(NX_DHCPV6 *dhcpv6_ptr);
```

### <a name="description"></a>説明

このサービスでは、DHCPv6 クライアント タスクと処理中のすべての要求を中断します。 タイマーが非アクティブ化され、クライアントの状態が非実行に設定されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcpv6_ptr**: DHCPv6 クライアント インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) クライアントが正常に一時停止されました

- **NX_DHCPV6_NOT_STARTED**: (0XE92) クライアントが実行されていないため、一時停止できません

- NX_PTR_ERROR: (0x16) ポインター入力が無効です

- NX_CALLER_ERROR: (0x11) スレッドから呼び出す必要があります

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Suspend the DHCPv6 Client task. */
status = nx_dhcpv6_suspend(&dhcp_0);

/* If status is NX_SUCCESS the Client successfully suspended. */
```

### <a name="see-also"></a>参照

- nx_dhcpv6_resume
- nx_dhcpv6_start
- nx_dhcpv6_reinitialize
- nx_dhcpv6_stop
