---
title: 第 3 章 - Azure RTOS NetX DHCP サーバー サービスの説明
description: この章では、Azure RTOS NetX DHCP サーバーのすべてのサービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 702499184b12484fa5862ba83ff3fadb8fccea31089b6bf8b71daf267e8c84a3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799525"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-server-services"></a>第 3 章 - Azure RTOS NetX DHCP サーバー サービスの説明

この章では、NetX DHCP サーバーのすべてのサービスについて説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nx_dhcp_server_create**: "*DHCP サーバー インスタンスを作成する*"
- **nx_dhcp_set_interface_network_parameters**: "*指定されたインターフェイス用の重要なネットワーク パラメーターの DHCP サーバー オプションを設定する*"
- **nx_dhcp_create_server_ip_address_list**: "*DHCP クライアント インターフェイスに割り当てる使用可能な IP アドレスのプールを作成する*"
- **nx_dhcp_clear_client_record**: "*サーバー データベース内のクライアント レコードを削除する*"
- **nx_dhcp_server_delete**: "*DHCP サーバー インスタンスを削除する*"
- **nx_dhcp_server_start**: "*DHCP サーバーの処理を開始または再開する*"
- **nx_dhcp_server_stop**: "*DHCP サーバーの処理を停止する*"

## <a name="nx_dhcp_server_create"></a>nx_dhcp_server_create

DHCP サーバー インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_server_create(NX_DHCP_SERVER *dhcp_ptr, NX_IP *ip_ptr,
                        VOID *stack_ptr, ULONG stack_size,
                        CHAR *input_address_list, CHAR *name_ptr,
                        NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>説明

このサービスにより、以前に作成された IP インスタンスを使用して DHCP サーバー インスタンスが作成されます。

> [!IMPORTANT]
> アプリケーションでは、IP 作成サービス用に作成されたパケット プールに、UDP、IP、およびイーサネット ヘッダーを含まない最小 548 バイトのペイロードがあることを確認する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP サーバー制御ブロックへのポインター。  
- **ip_ptr**: DHCP サーバーの IP インスタンスへのポインター。
- **stack_ptr**: DHCP サーバー スタックの場所を指すポインター。
- **stack_size**: DHCP サーバー スタックのサイズ
- **input_address_list**: サーバーの IP アドレスのリストへのポインター
- **name_ptr**: DHCP サーバー名へのポインター
- **packet_pool_ptr**: DHCP サーバーのパケット プールへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。
- **NX_DHCP_INADEQUATE_PACKET_POOL_PAYLOAD**: (0xA9) パケット ペイロードが小さすぎるというエラー
- **NX_DHCP_NO_SERVER_OPTION_LIST**: (0x96) サーバー オプション リストが空です
- NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```c
/* Create a DHCP Server instance. */
status = nx_dhcp_server_create(&dhcp_server, &server_ip, pointer,
                    DEMO_SERVER_STACK_SIZE, SERVER_IP_ADDRESS_LIST,
                    "DHCP server", &server_pool);

/* If status is NX_SUCCESS a DHCP Server instance was successfully created. */
```

## <a name="nx_dhcp_create_server_ip_address_list"></a>nx_dhcp_create_server_ip_address_list

IP アドレス プールを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_create_server_ip_address_list(NX_DHCP_SERVER *dhcp_ptr,
                            UINT iface_index, ULONG start_ip_address,
                            ULONG end_ip_address, UINT *addresses_added);
```

### <a name="description"></a>説明

このサービスにより、指定された DHCP サーバーによって割り当てられる、使用可能な IP アドレスのネットワーク インターフェイス固有のプールが作成されます。 開始および終了 IP アドレスは、指定されたネットワーク インターフェイスと一致している必要があります。 IP アドレス リストのサイズが十分でない場合 (ユーザーが構成可能な *NX_DHCP_IP_ADDRESS_MAX_LIST_SIZE* パラメーターで設定されています)、実際に追加される IP アドレスの数は、アドレスの総数よりも少なくなる可能性があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP サーバー制御ブロックへのポインター。  
- **iface_index**: ネットワーク インターフェイスに対応するインデックス
- **start_ip_address**: 使用可能な最初の IP アドレス
- **end_ip_address**: 使用可能な最後の IP アドレス
- **addresses_added**: リストに追加された IP アドレスの数

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) インデックスがアドレスと一致しません
- **NX_DHCP_INVALID_IP_ADDRESS_LIST**: (0x99) アドレス入力が無効です
- NX_DHCP_INVALID_IP_ADDRESS: (0x9B) 非論理的な開始/終了アドレス
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```c
/* Create a pool of available IP addresses to assign. */
status = nx_dhcp_create_server_ip_list (&dhcp_server, iface_index,
                START_IP_ADDRESS_LIST, END_IP_ADDRESS_LIST, &addresses_added);

/* If status is NX_SUCCESS aIP address list was successfully created. 
addresses_added indicates how many IP addresses were actually added to the list. */
```

## <a name="nx_dhcp_clear_client_record"></a>nx_dhcp_clear_client_record

サーバー データベースからクライアント レコードを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_clear_client_record (NX_DHCP_SERVER *dhcp_ptr,
                                NX_DHCP_CLIENT *dhcp_client_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、サーバー データベースからクライアント レコードがクリアされます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP サーバー制御ブロックへのポインター。  
- **dhcp_client_ptr**: 削除する DHCP クライアントへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元がスレッドではありません

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```c
/* Remove Client record from the server database. */
status = nx_dhcp_clear_client_record (&dhcp_server, &dhcp_client_ptr);

/* If status is NX_SUCCESS the specified Client was removed from the database. */
```

## <a name="nx_dhcp_set_interface_network_parameters"></a>nx_dhcp_set_interface_network_parameters

DHCP オプションのネットワーク パラメーターを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_set_interface_network_parameters(NX_DHCP_SERVER *dhcp_ptr,
                                    UINT iface_index, ULONG subnet_mask,
                                    ULONG default_gateway_address,
                                    ULONG dns_server_address);
```

### <a name="description"></a>説明

このサービスを使用すると、指定したインターフェイスのネットワーク クリティカルなパラメーターに既定値が設定されます。 DHCP サーバーによって、これらのオプションが DHCP クライアントへの OFFER および ACK 応答に含められます。 DHCP サーバーが実行されているホストによってインターフェイス パラメーターが設定された場合、パラメーターの既定値は次のようになります: ルーターは DHCP サーバー自体のプライマリ インターフェイス ゲートウェイに設定され、DNS サーバー アドレスは DHCP サーバー自体で、サブネット マスクは DHCP サーバー インターフェイスで構成されているものと同じです。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP サーバー制御ブロックへのポインター。  
- **iface_index**: ネットワーク インターフェイスに対応するインデックス
- **subnet_mask**: クライアント ネットワークのサブネット マスク
- **default_gateway_address**: クライアントのルーター IP アドレス
- **dns_server_address**: クライアントのネットワーク用の DNS サーバー

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCP サーバーが正常に作成されました。
- **NX_DHCP_SERVER_BAD_INTERFACE_INDEX**: (0xA1) インデックスがアドレスと一致しません
- **NX_DHCP_INVALID_NETWORK_PARAMETERS**: (0xA3) ネットワーク パラメーターが無効です
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。

### <a name="allowed-from"></a>許可元

Application

### <a name="example"></a>例

```c
/* Set network parameters for a specific interface. */
status = nx_dhcp_set_interface_network_parameters(&dhcp_server, iface_index,
                                    NX_DHCP_SUBNET_MASK, IP_ADDRESS(10,0,0,1),
                                    IP_ADDRESS(10,0,0,1));

/* If status is NX_SUCCESS network parameters were successfully set. */
```

## <a name="nx_dhcp_server_delete"></a>nx_dhcp_server_delete

DHCP サーバー インスタンスを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_server_delete(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、以前に作成した DHCP サーバー インスタンスが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCP サーバーが正常に削除されました。
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。
- NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete a DHCP Server instance. */
status = nx_dhcp_server_delete(&dhcp_server);  
  
/* If status is NX_SUCCESS the DHCP Server instance was successfully deleted. */
```

## <a name="nx_dhcp_server_start"></a>nx_dhcp_server_start

DHCP サーバーの処理を開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_server_start(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、DHCP サーバーの処理が開始されます。これには、サーバー UDP ソケットの作成、DHCP ポートのバインド、クライアント DHCP 要求の受信の待機が含まれます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) サーバーが正常に起動しました。  
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP は既に開始されています。
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。
- NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Start the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_start(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully started. */
```

### <a name="see-also"></a>参照

nx_dhcp_create、nx_dhcp_delete、nx_dhcp_release、nx_dhcp_state_change_notify、nx_dhcp_stop、nx_dhcp_user_option_retrieve、nx_dhcp_user_option_convert

## <a name="nx_dhcp_server_stop"></a>nx_dhcp_server_stop

DHCP サーバーの処理を停止します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_dhcp_server_stop(NX_DHCP_SERVER *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、DHCP クライアント要求の受信など、DHCP サーバーの処理が停止されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr**: DHCP サーバー インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DHCP が正常に停止されました。
- **NX_DHCP_ALREADY_STARTED**: (0x93) DHCP は既に開始されています。
- NX_PTR_ERROR: (0x16) ポインター入力が無効です。
- NX_CALLER_ERROR: (0x11) サービスの呼び出し元が無効です。
- NX_DHCP_PARAMETER_ERROR: (0x92) ポインターではない無効な入力。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Stop the DHCP Server processing for this IP instance. */
status = nx_dhcp_server_stop(&dhcp_server);  

/* If status is NX_SUCCESS the DHCP Server was successfully stopped. */
```
