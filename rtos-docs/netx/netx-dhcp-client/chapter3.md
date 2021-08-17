---
title: 第 3 章 - Azure RTOS NetX DHCP クライアント サービスの説明
description: この章では、すべての Azure RTOS NetX DHCP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50902d37f823302910b1b219658dcbf1a41406f480c14795ffceea6e733a0848
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799542"
---
# <a name="chapter-3---description-of-azure-rtos-netx-dhcp-client-services"></a>第 3 章 - Azure RTOS NetX DHCP クライアント サービスの説明

この章では、すべての Azure RTOS NetX DHCP サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にする際に使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nx_dhcp_create**: "*DHCP インスタンスを作成する*"

- **nx_dhcp_clear_broadcast_flag**: クライアント メッセージのブロードキャスト フラグをクリアする

- **nx_dhcp_delete**: "*DHCP インスタンスを削除する*"

- **nx_dhcp_decline**: "*サーバーに拒否メッセージを送信する*"

- **nx_dhcp_force_renew**: "*強制更新メッセージを送信する*"

- **nx_dhcp_packet_pool_set**: "*DHCP クライアントのパケット プールを設定する*"

- **nx_dhcp_release**: "*リリース メッセージをサーバーに送信する*"

- **nx_dhcp_reinitialize**: "*DHCP クライアントのネットワーク パラメーターをクリアする*"

- **nx_dhcp_request_client_ip**: "*特定の IP アドレスを指定する*"

- **nx_dhcp_send_request**: "*DHCP メッセージをサーバーに送信する*"

- **nx_dhcp_server_address_get**: "*DHCP クライアントの DHCP サーバー アドレスを取得する*"

- **nx_dhcp_set_interface_index**: "*クライアントのネットワーク インターフェイスを指定する*"

- **nx_dhcp_start**: "*DHCP 処理を開始する*"

- **nx_dhcp_state_change_notify**: "*DHCP の状態の変更をアプリケーションに通知する*"

- **nx_dhcp_stop**: "*DHCP の処理を停止する*"

- **nx_dhcp_user_option_retrieve**: "*DHCP のオプションを取得する*"

- **nx_dhcp_user_option_convert**: "*4 バイトを ULONG に変換する*"

インターフェイス固有の DHCP クライアント サービス:

- **nx_dhcp_interface_clear_broadcast_flag**: "*指定されたインターフェイスでクライアント メッセージのブロードキャスト フラグをクリアする*"

- **nx_dhcp_interface_enable**: "*指定されたインターフェイスで DHCP を実行するためのインターフェイスを有効にする*"

- **nx_dhcp_interface_disable**: "*指定されたインターフェイスで DHCP を実行するためのインターフェイスを無効にする*"

- **nx_dhcp_interface_decline**: "*指定されたインターフェイスでサーバーに Decline メッセージを送信する*"

- **nx_dhcp_interface_force_renew**: "*指定されたインターフェイスで強制更新メッセージを送信する*"

- **nx_dhcp_interface_reinitialize**: "*指定されたインターフェイスで DHCP クライアントのネットワーク パラメーターをクリアする*"

- **nx_dhcp_interface_release**: "*指定されたインターフェイスでサーバーにリリース メッセージを送信する*"

- **nx_dhcp_interface_request_client_ip**: "*指定されたインターフェイスに特定の IP アドレスを指定する*"

- **nx_dhcp_interface_send_request**: "*指定されたインターフェイスでサーバーに DHCP メッセージを送信する*"

- **nx_dhcp_interface_server_address_get**: "*指定されたインターフェイスで DHCP サーバー IP アドレスを取得する*"

- **nx_dhcp_interface_start**: "*指定されたインターフェイスで DHCP クライアントの処理を開始する*"

- **nx_dhcp_interface_stop**: "*指定されたインターフェイスで DHCP クライアントの処理を停止する*"

- **nx_dhcp_interface_state_change_notify**: "*指定されたインターフェイスで DHCP の状態が変更されたときのコールバック関数を設定する*"

- **nx_dhcp_interface_user_option_retrieve**: "*指定されたインターフェイスで指定された DHCP オプションを取得する*"

NX_DHCP_CLIENT_RESORE_STATE が定義されている場合の DHCP クライアント サービス:

- **nx_dhcp_resume**: "*以前に確立された DHCP クライアントの状態を再開する*"

- **nx_dhcp_suspend**: "*DHCP クライアントの状態の処理を中断する*"

- **nx_dhcp_client_get_record**: "*DHCP クライアントの状態のレコードを作成する*"

- **nx_dhcp_client_restore_record**: "*以前に保存されたレコードを DHCP クライアントに復元する*"

- **nx_dhcp_client_update_time_remaining**: "*DHCP の現在の状態の残り時間を更新する*"

NX_DHCP_CLIENT_RESORE_STATE が定義されている場合のインターフェイス固有の DHCP クライアント サービス:

- **nx_dhcp_client_interface_get_record**: "*指定されたインターフェイスで DHCP クライアントの状態のレコードを作成する*"

- **nx_dhcp_client_interface_restore_record**: "*以前に保存されたレコードを、指定されたインターフェイスの DHCP クライアントに復元する*"

- **nx_dhcp_client_interface_update_time_remaining**: "*指定されたインターフェイスの DHCP の現在の状態の残り時間を更新する*"

## <a name="nx_dhcp_create"></a>nx_dhcp_create

DHCP インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_create(NX_DHCP *dhcp_ptr, NX_IP *ip_ptr, CHAR *name_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された IP インスタンスの DHCP インスタンスを作成します。 既定では、DHCP の実行にはプライマリ インターフェイスが有効になります。 DHCP クライアントの NetX 実装では使用されませんが、入力する名前は、RFC 1035 のホスト名の規定に従っている必要があります。 合計長は 255 文字以下にする必要があります。ドットで区切られたラベルは、文字で始まり、文字または数字で終わる必要があります。また、ハイフンを含めることはできますが、その他の英数字以外の文字は使用できません。

アプリケーションで、(*nx_ip_interface_attach* を使用して) IP インスタンスに登録された別の DHCP インターフェイスを実行する場合、*nx_dhcp_set_interface_index* を呼び出すと、そのインターフェイスだけで DHCP を実行でき、*nx_dhcp_interface_enable* を呼び出すと、そのインターフェイスでも DHCP を実行できます。 詳細については、これらのサービスの説明をご覧ください。

> [!NOTE]
> アプリケーションでは、RFC 2131 セクション 2 で指定されている DHCP メッセージの最小サイズ (548 バイトの DHCP メッセージ データに、UDP、IP、物理ネットワーク フレームの各ヘッダーを加えたサイズ) を、DHCP クライアントのパケット プールのペイロードでサポートできることを確認する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  
- **ip_ptr** 以前に作成された IP インスタンスへのポインター。  
- **name_ptr** DHCP インスタンスのホスト名へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に作成されました

- **NX_DHCP_INVALID_NAME** (0xA8) ホスト名が無効です

- **NX_DHCP_INVALID_PAYLOAD** (0x9C) DHCP メッセージに対してペイロードが小さすぎます

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

### <a name="allowed-from"></a>許可元

**スレッド**、初期化

### <a name="example"></a>例

```C
/* Create a DHCP instance. */
status =  nx_dhcp_create(&my_dhcp, &my_ip, "My-DHCP");

/* If status is NX_SUCCESS a DHCP instance was successfully created. */
```

## <a name="nx_dhcp_interface_enable"></a>nx_dhcp_interface_enable

DHCP を実行するための指定されたインターフェイスを有効にする 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_enable(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、DHCP を実行するための指定されたインターフェイスを有効にします。 既定では、DHCP クライアントのプライマリ インターフェイスが有効になります。 この時点で、*nx_dhcp_interface_start* を呼び出すとこのインターフェイスで DHCP を開始でき、*nx_dhcp_start* を呼び出すとすべての有効なインターフェイスで DHCP を開始できます。

アプリケーションでは、*nx_ip_interface_attach* を使用して、まずこのインターフェイスを IP インスタンスに登録する必要があります。

さらに、有効なインターフェイスの一覧にこのインターフェイスを追加する、使用可能な DHCP クライアント インターフェイスの "レコード" が必要です。 既定では、NX_DHCP_CLIENT_MAX_RECORDS は 1 に定義されています。 このオプションを、DHCP クライアントを同時に実行することが予想されるインターフェイスの最大数に設定します。 通常、NX_DHCP_CLIENT_MAX_RECORDS は NX_MAX_PHYSICAL_INTERFACES と等しくなります。ただし、DHCP クライアントを実行することが予想されるインターフェイスの数よりも多くの物理インターフェイスがデバイスにある場合は、NX_DHCP_CLIENT_MAX_RECORDS をその数よりも小さい値に設定することによって、メモリを節約できます。 物理インターフェイスと DHCP クライアント インターフェイスのレコードのマッピングは 1 対 1 ではありません。

このサービスと *nx_dhcp_set_interface_index* の違いは、後者が DHCP を実行するためのインターフェイスを 1 つだけ設定するのに対し、このサービスでは、DHCP が有効になっているクライアント インターフェイスの一覧に指定されたインターフェイスが単純に追加されることです。

DHCP 用のインターフェイスを無効にするには、アプリケーションで *nx_dhcp_interface_disable* サービスを呼び出すことができます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  

- **interface_index** DHCP を有効にするインターフェイスのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に有効にされました

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) DHCP を有効にする別のインターフェイスのレコードがありません

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP が有効になっているインターフェイス

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Enable DHCP on a secondary interface. It is already enabled on the primary 
   interface. NX_DHCP_CLIENT_MAX_RECORDS is set to 2. */

status =  nx_dhcp_interface_enable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface was successfully enabled. */


status = nx_dhcp_start(&my_dhcp);
/* If status is NX_SUCCESS DHCP is running on interface 0 and 1. */
```

## <a name="nx_dhcp_interface_disable"></a>nx_dhcp_interface_disable

DHCP を実行するための指定されたインターフェイスを無効にする 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_disable(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、DHCP を実行するための指定されたインターフェイスを無効にします。 このインターフェイスの DHCP クライアントが再初期化されます。

DHCP クライアントを再起動するには、アプリケーションで *nx_dhcp_interface_enable* を使用してインターフェイスを再度有効にし、*nx_dhcp_interface_start* を呼び出して DHCP を再起動する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  

- **interface_index** DHCP を無効にするインターフェイスのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に作成されました

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Disable DHCP on a secondary interface.
. */

status = nx_dhcp_interface_disable(&my_dhcp, 1);
/* If status is NX_SUCCESS the interface is successfully disabled. */
```

## <a name="nx_dhcp_clear_broadcast_flag"></a>nx_dhcp_clear_broadcast_flag

DHCP ブロードキャスト フラグを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_clear_broadcast_flag(NX_DHCP *dhcp_ptr, UINT clear_flag);
```

### <a name="description"></a>説明

このサービスは、DHCP が有効になっているすべてのインターフェイスの DHCP メッセージ ヘッダーのブロードキャスト フラグを設定またはクリアします。 一部の DHCP メッセージ (DISCOVER など) の場合、クライアントに IP アドレスがないため、ブロードキャスト フラグがブロードキャストに設定されます。

__clear_flag__


- **NX_TRUE** ブロードキャスト フラグがクリアされました (ユニキャスト応答を要求します)

- **NX_FALSE** ブロードキャスト フラグが設定されました (ブロードキャスト応答を要求します)

このサービスは、ブロードキャスト メッセージの転送が拒否されるルーターを経由して DHCP サーバーにアクセスする必要がある DHCP クライアントを対象としています。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター  

- **clear_flag** ブロードキャスト フラグに設定する値

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ブロードキャスト フラグが正常に更新されました

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a  
    unicast response). */
status =  nx_dhcp_clear_broadcast_flag(&my_dhcp, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_interface_clear_broadcast_flag"></a>nx_dhcp_interface_clear_broadcast_flag

指定されたインターフェイスでブロードキャスト フラグを設定またはクリアする

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_clear_broadcast_flag(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            UINT clear_flag);
```

### <a name="description"></a>説明

このサービスを使用すると、DHCP クライアントのホスト アプリケーションでは、DHCP クライアント メッセージのブロードキャスト フラグを、指定されたインターフェイスの DHCP サーバーに設定するか、クリアすることができます。 詳細については、**nx_dhcp_clear_broadcast_flag** を参照してください

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター

- **interface_index** ブロードキャスト フラグを設定するインターフェイスのインデックス  

- **clear_flag** ブロードキャスト フラグに設定する値

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ブロードキャスト フラグが正常に更新されました

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Send DHCP Client messages with the broadcast flag cleared (e.g. request a 
   unicast response) on a previously attached secondary interface. */

iface_index = 1;

status =  nx_dhcp_interface_clear_broadcast_flag(&my_dhcp, iface_index, NX_TRUE);

/* If status is NX_SUCCESS the DHCP Client broadcast flag is updated. */
```

## <a name="nx_dhcp_delete"></a>nx_dhcp_delete

DHCP インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_delete(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された DHCP インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に削除されました。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete a DHCP instance. */
status =  nx_dhcp_delete(&my_dhcp);

/* If status is NX_SUCCESS the DHCP instance was successfully deleted. */
```

## <a name="nx_dhcp_-force_renew"></a>nx_dhcp_force_renew

強制更新メッセージを送信する 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp force_renew(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、ホスト アプリケーションは、DHCP が有効になっているすべてのインターフェイスで強制更新メッセージを送信できます。 DHCP クライアントは、BOUND 状態である必要があります。 この関数によって状態が RENEW に設定され、T1 タイムアウトになる前に DHCP クライアントは更新を試みるようになります。

複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスで強制更新を送信するには、*nx_dhcp_interface_force_renew* を使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 強制更新が正常に送信されました。  

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send a force renew message from the Client. */
status =  nx_dhcp_force_renew(&my_dhcp);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_interface_force_renew"></a>nx_dhcp_interface_force_renew

指定されたインターフェイスで強制更新メッセージを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_force_renew(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>説明

このサービスを使用すると、ホスト アプリケーションは、入力インターフェイスで DHCP が有効になっていれば (「*nx_dhcp_interface_enable*」を参照)、そのインターフェイスで強制更新メッセージを送信できます。 指定されたインターフェイスの DHCP クライアントは、BOUND 状態である必要があります。 この関数によって状態が RENEW に設定され、T1 タイムアウトになる前に DHCP クライアントは更新を試みるようになります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 強制更新が正常に送信されました。  

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send a force renew message to the server on interface 1. */
status =  nx_dhcp_interface_force_renew(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP client state is the RENEWING state and the    
   DHCP Client thread task will begin renewing before T1 is expired. */
```

## <a name="nx_dhcp_packet_pool_set"></a>nx_dhcp_packet_pool_set

DHCP クライアントのパケット プールを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_packet_pool_set(NX_DHCP *dhcp_ptr,
                            NX_PACKET_POOL *packet_pool_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションは、以前に作成されたパケット プールへのポインターをこのサービス呼び出しで渡すことによって、DHCP クライアントのパケット プールを作成できます。 この機能を使用するには、ホスト アプリケーションで NX_DHCP_CLIENT_USER_CREATE_PACKET_POOL を定義する必要があります。 定義した場合、*nx_dhcp_create* サービスによってクライアントのパケット プールが作成されません。 パケット プールを作成するときには、*nx_dhcp.h* で NX_DHCP_PACKET_PAYLOAD として定義されている、DHCP クライアントのパケット プールのペイロードの既定値をアプリケーションで使用することをお勧めします。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  

- **packet_pool_ptr** 以前に作成されたパケット プールへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP クライアントのパケット プールが設定されました

- **NX_NOT_ENABLED** (0x14) サービスが有効になっていません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_DHCP_INVALID_PAYLOAD (0x9C) ペイロードが小さすぎます

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Create the packet pool. */
status =  nx_packet_pool_create(&dhcp_pool, "DHCP Client Packet Pool", 
        NX_DHCP_PACKET_PAYLOAD, pointer, (15 * NX_DHCP_PACKET_PAYLOAD));

/* Create the DHCP Client. */
status =  nx_dhcp_create(&dhcp_0, &ip_0, "janetsdhcp1");

/* Set the DHCP Client packet pool. */
status =  nx_dhcp_packet_pool_set(&my_dhcp, packet_pool_ptr);
/* If status is NX_SUCCESS packet pool was successfully set. */
```

## <a name="nx_dhcp_request_client_ip"></a>nx_dhcp_request_client_ip

DHCP インスタンスの要求された IP アドレスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_request_client_ip(NX_DHCP *dhcp_ptr,
                                ULONG client_ip_address,
                                UINT skip_discover_message);
```

### <a name="description"></a>説明

このサービスは、DHCP クライアント レコードの DHCP が有効になっている最初のインターフェイスで、DHCP クライアントが DHCP サーバーに要求する IP アドレスを設定します。 *skip_discover_message* フラグが設定されている場合、DHCP クライアントは Discover メッセージをスキップし、Request メッセージを送信します。

特定のインターフェイスで DHCP メッセージに特定の IP の要求を設定するには、*nx_dhcp_interface_request_client_ip* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  

- **client_ip_address** DHCP サーバーに要求する IP アドレス

- **skip_discover_message** True の場合、DHCP クライアントでは Request メッセージが送信されます  
False の場合は、Discover メッセージが送信されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求された IP アドレスが設定されました。

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です
 
### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the DHCP Client requested IP address and skip the discover message. */

status =  nx_dhcp_request_client_ip(&my_dhcp, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_interface_request_client_ip"></a>nx_dhcp_interface_request_client_ip

指定されたインターフェイスで DHCP インスタンスの要求された IP アドレスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_request_client_ip(NX_DHCP *dhcp_ptr,
                                        UINT interface_index,
                                        ULONG client_ip_address,
                                        UINT skip_discover_message);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に (「*nx_dhcp_interface_enable*」を参照)、そのインターフェイスで DHCP クライアントが DHCP サーバーに要求する IP アドレスを設定します。 *skip_discover_message* フラグが設定されている場合、DHCP クライアントは Discover メッセージをスキップし、Request メッセージを送信します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。

- **Interface_index** IP アドレスを要求するインターフェイスのインデックス

- **client_ip_address** DHCP サーバーに要求する IP アドレス

- **skip_discover_message** True の場合、DHCP クライアントによって Request メッセージが送信されます。それ以外の場合は、Discover メッセージが送信されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 要求された IP アドレスが設定されました。

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) IP または DHCP ポインターが無効です

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です


### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the DHCP Client requested IP address and skip the discover message on  
   interface 0. */
status =  nx_dhcp_interface_request_client_ip(&my_dhcp, 0, IP(192,168,0,6), NX_TRUE);

/* If status is NX_SUCCESS requested IP address was successfully set. */
```

## <a name="nx_dhcp_reinitialize"></a>nx_dhcp_reinitialize

DHCP クライアントのネットワーク パラメーターをクリアする 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_reinitialize(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスは、ホスト アプリケーションのネットワーク パラメーター (IP アドレス、ネットワーク アドレス、ネットワーク マスク) をクリアし、DHCP が有効になっているすべてのインターフェイスの DHCP クライアントの状態をクリアします。 これは *nx_dhcp_stop* および *nx_dhcp_start* と組み合わせて使用され、DHCP ステート マシンが "再起動" されます。 

nx_dhcp_stop(&my_dhcp);  
nx_dhcp_reinitialize(&my_dhcp);  
nx_dhcp_start(&my_dhcp);


複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスの DHCP クライアントを再初期化するには、*nx_dhcp_interface_reinitialize* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に再初期化されました 

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Reinitialize the previously started DHCP client. */
status =  nx_dhcp_reinitialize(&my_dhcp);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_interface_reinitialize"></a>nx_dhcp_interface_reinitialize

指定されたインターフェイスの DHCP クライアントのネットワーク パラメーターをクリアする 

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_reinitialize(NX_DHCP *dhcp_ptr,
                                    UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に (「*nx_dhcp_interface_enable*」を参照)、そのインターフェイスのネットワーク パラメーター (IP アドレス、ネットワーク アドレス、ネットワーク マスク) をクリアします。 詳細については、「*nx_dhcp_reinitialize*」を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター

- **interface_index** 再初期化するインターフェイスのインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) インターフェイスが正常に再初期化されました

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Reinitialize the previously started DHCP client on interface 1. */
status =  nx_dhcp_interface_reinitialize(&my_dhcp, 1);

/* If status is NX_SUCCESS the host application successfully reinitialized its 
network parameters and DHCP client state. */
```

## <a name="nx_dhcp_release"></a>nx_dhcp_release

リースした IP アドレスを解放する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_release(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスは、DHCP サーバーに RELEASE メッセージを送信することによって、そのサーバーから取得した IP アドレスを解放します。 その後、DHCP クライアントが再初期化されます。 このサービスは、DHCP が有効になっているすべてのインターフェイスに適用されます。

アプリケーションでは、*nx_dhcp_start* を呼び出すことによって DHCP クライアントを再起動できます。

特定のインターフェイスでアドレスを解放して DHCP サーバーに返却するには、*nx_dhcp_interface_release* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に解放されました。  

- **NX_DHCP_NOT_BOUND** (0x94) IP アドレスがリースされていないため、解放できません。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Release the previously leased IP address. */
status =  nx_dhcp_release(&my_dhcp);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_interface_release"></a>nx_dhcp_interface_release

指定されたインターフェイスで IP アドレスを解放する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_release(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP サーバーから取得した IP アドレスを解放し、DHCP クライアントを再初期化します。 *nx_dhcp_start* を呼び出すことによって、DHCP クライアントを再起動できます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に解放されました。

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- **NX_DHCP_NOT_BOUND** (0x94) IP アドレスがリースされていないため、解放できません。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Release the previously leased IP address on interface 1. */
status =  nx_dhcp_interface_release(&my_dhcp, 1);

/* If status is NX_SUCCESS the previous IP lease was successfully released. */
```

## <a name="nx_dhcp_decline"></a>nx_dhcp_decline

DHCP サーバーからの IP アドレスを拒否する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_decline(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスは、DHCP が有効になっているすべてのインターフェイスで、DHCP サーバーからリースされた IP アドレスを拒否します。 NX_DHCP_CLIENT_ SEND_ ARP_PROBE が定義されていて、その IP アドレスが既に使用されていることが DHCP クライアントで検出された場合、DECLINE メッセージが送信されます。 NetX DHCP クライアントでの ARP プローブの構成の詳細については、第 1 章の **ARP プローブ** に関する記述を参照してください。

アプリケーションでは、このサービスを使用して、IP アドレスが他で使用されていることが検出された場合に、その IP アドレスを拒否することができます。

このサービスは、*nx_dhcp_start* を呼び出して再起動できるように、DHCP クライアントを再初期化します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 拒否が正常に送信されました  

- **NX_DHCP_NOT_STARTED** (0x96) DHCP インスタンスが開始されていません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Decline the IP address offered by the DHCP server. */
status =  nx_dhcp_decline(&my_dhcp);

/* If status is NX_SUCCESS the previous IP address decline message was 
   successfully trasnmitted. */
```

## <a name="nx_dhcp_interface_decline"></a>nx_dhcp_interface_decline

指定されたインターフェイスで DHCP サーバーからの IP アドレスを拒否する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_decline(NX_DHCP *dhcp_ptr,
                                UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、サーバーに DECLINE メッセージを送信して、DHCP サーバーによって割り当てられた IP アドレスを拒否します。 また、DHCP クライアントが再初期化されます。 詳細については、「*nx_dhcp_decline*」を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **Interface_index** IP アドレスを拒否するインターフェイスのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP 拒否メッセージが送信されました  

- **NX_DHCP_NOT_BOUND** (0x94) DHCP クライアントがバインドされていません

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例
```C
/* Decline the IP address offered by the DHCP server on interface 2. */
status =  nx_dhcp_interface_decline(&my_dhcp, 2);

/* If status is NX_SUCCESS the previous IP address decline message was
   successfully trasnmitted. */
```

## <a name="nx_dhcp_send_request"></a>nx_dhcp_send_request

サーバーに DHCP メッセージを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_send_request(NX_DHCP *dhcp_ptr, UINT dhcp_message_type);
```

### <a name="description"></a>説明

このサービスは、DHCP クライアント レコードで最初に見つかった、DHCP が有効になっているインターフェイスで、指定された DHCP メッセージを DHCP サーバーに送信します。 RELEASE または DECLINE メッセージを送信するには、アプリケーションで *nx_dhcp[_interface]_release()* または *nx_dhcp_interface_decline()* サービスをそれぞれ使用する必要があります。

種類が INFORM_REQUEST のメッセージを送信する場合を除き、このサービスを使用するには DHCP クライアントを起動する必要があります。

> [!NOTE] 
> このサービスは、ホスト アプリケーションで DHCP クライアント ステート マシンを "駆動" するためのものではありません。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  

- **dhcp_message_type** メッセージ要求 (*nx_dhcp.h* で定義されます)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP メッセージが送信されました  

- **NX_DHCP_NOT_STARTED** (0x96) インターフェイスのインデックスが無効です

- **NX_DHCP_INVALID_MESSAGE** (0x9B) 送信するメッセージの種類が無効です

- NX_PTR_ERROR (0x16) ポインターの入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send the DHCP INFORM REQUEST message to the server. */

status =  nx_dhcp_send_request(&my_dhcp, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_interface_send_request"></a>nx_dhcp_interface_send_request

特定のインターフェイスでサーバーに DHCP メッセージを送信する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_send_request(NX_DHCP *dhcp_ptr,
                                    UINT interface_index,
                                    UINT dhcp_message_type);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP サーバーにメッセージを送信します。 RELEASE または DECLINE メッセージを送信するには、アプリケーションで *nx_dhcp[_interface]_release()* または *nx_dhcp_interface_decline()* サービスをそれぞれ使用する必要があります。

種類が DHCP INFORM REQUEST のメッセージを送信する場合を除き、このサービスを使用するには DHCP クライアントを起動する必要があります。

このサービスは、ホスト アプリケーションで DHCP クライアント ステート マシンを "駆動" するためのものではありません。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。

- **Interface_index** メッセージを送信するインターフェイスのインデックス  

- **dhcp_message_type** メッセージ要求 (*nx_dhcp.h* で定義されます)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP メッセージが送信されました  

- **NX_DHCP_NOT_STARTED** (0x96) インターフェイスのインデックスが無効です

- **NX_DHCP_INVALID_MESSAGE** (0x9B) 送信するメッセージの種類が無効です

- **NX_DHCP_INTERFACE_NOT_ENABLED** (0xA4) インターフェイスで DHCP が有効になっていません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Send the INFORM REQUEST message to the server on the primary interface. */

status =  nx_dhcp_interface_send_request(&my_dhcp, 0, NX_DHCP_TYPE_DHCPINFORM);
/* If status is NX_SUCCESS a DHCP message was successfully sent. */
```

## <a name="nx_dhcp_server_address_get"></a>nx_dhcp_server_address_get

DHCP クライアントの DHCP サーバー IP アドレスを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_server_address_get(NX_DHCP *dhcp_ptr,
                                ULONG server_address);
```

### <a name="description"></a>説明

このサービスは、DHCP クライアント レコードで最初に見つかった、DHCP が有効になっているインターフェイスで、DHCP クライアントの DHCP サーバー IP アドレスを取得します。 DHCP クライアントが DHCP サーバーによって割り当てられた IP アドレスにバインドされた後にのみ、呼び出し元はこのサービスを使用できます。 ホスト アプリケーションでは、*nx_ip_status_check* サービスを使用して IP アドレスが設定されていることを確認できます。または、*nx_dhcp_state_change_notify* を使用して、DHCP クライアントの状態が NX_DHCP_STATE_BOUND であることを照会できます。 状態変更コールバック関数の設定の詳細については、*nx_dhcp_state_change_notify* を参照してください。

DHCP クライアントの複数のインターフェイスが有効になっている場合に、特定のインターフェイスで DHCP サーバーを検索するには、*nx_dhcp_interface_server_address_get* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。

- **server_address** サーバーの IP アドレスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP サーバー アドレスが返されました

- NX_PTR_ERROR (0x16) 入力されたポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_server_address_get(&dhcp_0, &server_address);
    }
```

## <a name="nx_dhcp_interface_server_address_get"></a>nx_dhcp_interface_server_address_get

指定されたインターフェイスで DHCP クライアントの DHCP サーバー IP アドレスを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_server_address_get(NX_DHCP *dhcp_ptr,
                                            UINT interface_index,
                                            ULONG server_address);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP クライアントの DHCP サーバー IP アドレスを取得します。 DHCP クライアントは、BOUND 状態である必要があります。 そのインターフェイスの DHCP クライアントを起動した後に、ホスト アプリケーションでは、*nx_ip_status_check* サービスを使用して、IP アドレスが設定されていることを確認できます。また、DHCP クライアントの状態変更コールバックを使用し、DHCP クライアントの状態が NX_DHCP_STATE_BOUND であることを照会することもできます。 状態変更コールバック関数の設定の詳細については、「*nx_dhcp_state_change_notify*」を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。

- **Interface_index** IP アドレスを取得するインターフェイスのインデックス  

- **server_address** サーバーの IP アドレスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP サーバー アドレスが返されました

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が有効になっているインターフェイスがありません

- **NX_DHCP_NOT_BOUND** (0x94) DHCP クライアントがバインドされていません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Use the state change notify service to determine the Client transition to the 
bound state and get its DHCP server IP address. 
/* void dhcp_state_change(NX_DHCP *dhcp_ptr, UCHAR new_state)
{

ULONG server_address;
UINT  status;

/* Increment state changes counter. */
    state_changes++;

    /* Get the DHCP server IP address on interface 1 */
    if (dhcp_0.nx_dhcp_state == NX_DHCP_STATE_BOUND)
    {
            status = nx_dhcp_interface_server_address_get(&dhcp_0, 1, 
                                                    &server_address);
    }
```

## <a name="nx_dhcp_set_interface_index"></a>nx_dhcp_set_interface_index

DHCP インスタンスのネットワーク インターフェイスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_set_interface_index(NX_DHCP *dhcp_ptr, UINT index);
```

### <a name="description"></a>説明

このサービスは、単一のネットワーク インターフェイス用に構成された DHCP クライアントを実行する場合に、DHCP サーバーに接続するための DHCP インスタンスのネットワーク インターフェイスを設定します。

既定では、DHCP クライアントはプライマリ インターフェイスで実行されます。 セカンダリ サービスで DHCP を実行するには、このサービスを使用して、セカンダリ インターフェイスを DHCP クライアント インターフェイスとして設定します。 アプリケーションでは、*nx_ip_interface_attach* サービスを使用して、指定されたインターフェイスを IP インスタンスに事前に登録する必要があります。

このサービスは、1 つのインターフェイスでのみ DHCP クライアントを実行するアプリケーションを対象としています。 複数のインターフェイスで DHCP を実行する方法の詳細については、*nx_dhcp_interface_enable* を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** DHCP 制御ブロックへのポインター。  

- **index** デバイスのネットワーク インターフェイスのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) インターフェイスが正常に設定されました。

- **NX_INVALID_INTERFACE** (0x4C) ネットワーク インターフェイスが無効です

- **NX_DHCP_INTERFACE_ALREADY_ENABLED** (0xA3) DHCP が有効になっているインターフェイス

- **NX_DHCP_NO_RECORDS_AVAILABLE** (0xA7) 別のインターフェイスのレコードがありません

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the DHCP Client interface to the secondary interface (index 1). */
status =  nx_dhcp_set_interface_index(&my_dhcp, 1);
/* If status is NX_SUCCESS a DHCP interface was successfully set. */
```

## <a name="nx_dhcp_start"></a>nx_dhcp_start

DHCP の処理を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_start(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスは、DHCP が有効になっているすべてのインターフェイスで DHCP の処理を開始します。 既定では、アプリケーションで *nx_dhcp_create* を呼び出すと、DHCP のプライマリ インターフェイスが有効になります。

DHCP クライアント インターフェイスで、IP インスタンスが IP アドレスにバインドされていることを確認するには、*nx_ip_status_check* を使用して、IP アドレスが有効であることを確認します。

DHCP が既に実行されている他のインターフェイスがある場合、それらはこのサービスの影響を受けません。

複数のインターフェイスが有効になっている場合に、特定のインターフェイスで DHCP を開始するには、*nx_dhcp_interface_start* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に開始されました。  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP は既に開始されています。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start the DHCP processing for this IP instance. */
status =  nx_dhcp_start(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_interface_start"></a>nx_dhcp_interface_start

指定されたインターフェイスで DHCP の処理を開始する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_start(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで DHCP の処理を開始します。 インターフェイスで DHCP を有効にする方法の詳細については、「*nx_dhcp_interface_enable*」を参照してください。 既定では、アプリケーションで *nx_dhcp_create* を呼び出すと、DHCP のプライマリ インターフェイスが有効になります。

DHCP クライアントが実行されている他のインターフェイスがない場合、このサービスは DHCP クライアントのスレッドを開始または再開し、DHCP クライアントのタイマーを (再) アクティブ化します。  
  
アプリケーションで *nx_ip_status_check* を使用して、IP アドレスが取得されたかどうかを確認する必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **Interface_index** DHCP クライアントを開始するインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に開始されました。  

- **NX_DHCP_ALREADY_STARTED** (0x93) DHCP インスタンスは既に開始されています。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start the DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_start(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully started. */
```

## <a name="nx_dhcp_state_change_notify"></a>nx_dhcp_state_change_notify

DHCP 状態変更コールバック関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_state_change_notify(
          NX_DHCP *dhcp_ptr, 
          VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                           UCHAR new_state));
```

### <a name="description"></a>説明

このサービスは、DHCP の状態変更をアプリケーションに通知するために、指定されたコールバック関数 dhcp_state_change_notify を登録します。 このコールバック関数では、DHCP クライアントの遷移後の状態が示されます。

さまざまな DHCP の状態に関連付けられている値を以下に示します。

| State                             | 値 |
|-----------------------------------|-------|
| NX\_DHCP\_STATE\_BOOT             | 1     |
| NX\_DHCP\_STATE\_INIT             | 2     |
| NX\_DHCP\_STATE\_SELECTING        | 3     |
| NX\_DHCP\_STATE\_REQUESTING       | 4     |
| NX\_DHCP\_STATE\_BOUND            | 5     |
| NX\_DHCP\_STATE\_RENEWING         | 6     |
| NX\_DHCP\_STATE\_REBINDING        | 7     |
| NX_DHCP_STATE_FORCERENEW          | 8     |
| NX\_DHCP\_STATE\_ADDRESS\_PROBING | 9     |


### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **dhcp_state_change_notify** 状態変更コールバック関数のポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました。  

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Register the “my_state_change” function to be called on any DHCP state change, 
   assuming DHCP has alreadybeen created. */
status =  nx_dhcp_state_change_notify(&my_dhcp, my_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_interface_state_change_notify"></a>nx_dhcp_interface_state_change_notify

指定されたインターフェイスで DHCP 状態変更コールバック関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_state_change_notify(
              NX_DHCP *dhcp_ptr, 
              UINT interface_index,
              VOID (*dhcp_state_change_notify)(NX_DHCP *dhcp_ptr, 
                                               UINT interface_index,
                                               UCHAR new_state));
```

### <a name="description"></a>説明

このサービスは、DHCP の状態変更をアプリケーションに通知するために、指定されたコールバック関数を登録します。 このコールバック関数の入力引数は、インターフェイス インデックスと、そのインターフェイスでの DHCP クライアントの遷移後の状態です。

状態変更関数の詳細については、「*nx_dhcp_state_change_notify*」を参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **dhcp_interface_state_change_notify** アプリケーションのコールバック関数のポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました。  

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、初期化

### <a name="example"></a>例

```C
/* Register the “my_state_change” function to be called on any DHCP state 
   change, assuming DHCP has alreadybeen created. */

void dhcp_interstate_state_change(NX_DHCP *dhcp_ptr, UINT iface_index, 
                                 UCHAR new_state);


status =  nx_dhcp_interstate_state_change_notify(&my_dhcp,  
                                                 dhcp_interstate_state_change);

/* If status is NX_SUCCESS the callback function was successfully
   registered. */
```

## <a name="nx_dhcp_stop"></a>nx_dhcp_stop

DHCP の処理を停止する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_stop(NX_DHCP *dhcp_ptr);
```

### <a name="description"></a>説明

このサービスは、DHCP の処理が開始されているすべてのインターフェイスで DHCP の処理を停止します。 DHCP を処理しているインターフェイスがない場合、このサービスは DHCP クライアントのスレッドを中断し、DHCP クライアントのタイマーを非アクティブにします。

複数のインターフェイスで DHCP が有効になっている場合に、特定のインターフェイスで DHCP を停止するには、*nx_dhcp_interface_stop* サービスを使用します。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に停止されました

- **NX_DHCP_NOT_STARTED** (0x96) DHCP インスタンスが開始されていません。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop the DHCP processing for this IP instance. */
status =  nx_dhcp_stop(&my_dhcp);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_interface_stop"></a>nx_dhcp_interface_stop

指定されたインターフェイスで DHCP の処理を停止する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_stop(NX_DHCP *dhcp_ptr, UINT interface_index);
```

### <a name="description"></a>説明

このサービスは、DHCP が既に開始されている場合に、指定されたインターフェイスで DHCP の処理を停止します。 DHCP が実行されている他のインターフェイスがない場合は、DHCP のスレッドとタイマーが中断されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **Interface_index** DHCP の処理を停止するインターフェイス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) DHCP が正常に停止されました

- **NX_DHCP_NOT_STARTED** (0x96) DHCP が開始されていません。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop DHCP processing for this IP instance on interface 1. */
status =  nx_dhcp_interface_stop(&my_dhcp, 1);

/* If status is NX_SUCCESS the DHCP was successfully stopped. */
```

## <a name="nx_dhcp_user_option_retrieve"></a>nx_dhcp_user_option_retrieve

最後のサーバー応答から DHCP オプションを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_user_option_retrieve(NX_DHCP *dhcp_ptr, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>説明

このサービスは、DHCP クライアント レコードで最初に見つかった、DHCP が有効になっているインターフェイスで、DHCP オプションのバッファーから指定された DHCP オプションを取得します。 成功すると、そのオプションのデータが指定されたバッファーにコピーされます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。  

- **request_option** RFC で指定されている DHCP のオプション。 *nx_dhcp.h* の NX_DHCP_OPTION オプションを参照してください。

- **destination_ptr** 応答文字列のコピー先へのポインター。  

- **destination_size** コピー先のサイズへのポインター。戻り値では、返されたバイト数が保持されているコピー先。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オプションの取得に成功しました。  

- **NX_DHCP_NOT_BOUND** (0x94) DHCP クライアントがバインドされていません。

- **NX_DHCP_NO_INTERFACES_ENABLED** (0xA5) DHCP が有効になっているインターフェイスがありません

- **NX_DHCP_DEST_TO_SMALL** (0x95) コピー先が小さすぎて応答を保持できません。

- **NX_DHCP_PARSE_ERROR** (0x97) DHCP オプションがサーバー応答で見つかりませんでした。

- NX_PTR_ERROR (0x16) 入力されたポインターが無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_user_option_retrieve(&my_dhcp, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_interface_user_option_retrieve"></a>nx_dhcp_interface_user_option_retrieve

指定されたインターフェイスで、最後のサーバー応答から DHCP オプションを取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_dhcp_interface_user_option_retrieve(NX_DHCP *dhcp_ptr,
                  UINT interface_index, 
            UINT request_option, UCHAR *destination_ptr, 
            UINT *destination_size);
```

### <a name="description"></a>説明

このサービスは、指定されたインターフェイスで DHCP が有効になっている場合に、そのインターフェイスで、DHCP オプションのバッファーから指定された DHCP オプションを取得します。 成功すると、そのオプションのデータが指定されたバッファーにコピーされます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **Interface_index** 指定されたオプションを取得するインデックス  

- **request_option** RFC で指定されている DHCP のオプション。 *nx_dhcp.h* の NX_DHCP_OPTION オプションを参照してください。  

- **destination_ptr** 応答文字列のコピー先へのポインター。  

- **destination_size** コピー先のサイズへのポインター。戻り値では、返されたバイト数が保持されているコピー先。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) オプションの取得に成功しました。  

- **NX_DHCP_NOT_BOUND** (0x94) IP アドレスが割り当てられていません

- **NX_DHCP_DEST_TO_SMALL** (0x95) バッファーが小さすぎます

- **NX_DHCP_PARSE_ERROR** (0x97) DHCP オプションがサーバー応答で見つかりませんでした。

- NX_PTR_ERROR (0x16) DHCP ポインターが無効です。

- NX_CALLER_ERROR (0x11) サービスの呼び出し元が無効です。

- NX_INVALID_INTERFACE (0x4C) ネットワーク インターフェイスが無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UCHAR  dns_ip_string[4];
ULONG  size;

/* Obtain the IP address of the DNS server on the prmary interface. */
size =    sizeof(dnx_ip_string);
status =  nx_dhcp_interface_user_option_retrieve(&my_dhcp, 0, NX_DHCP_OPTION_DNS_SVR,
        dns_ip_string, &size);

/* If status is NX_SUCCESS the DNS IP address is in dns_ip_string. */
```

## <a name="nx_dhcp_user_option_convert"></a>nx_dhcp_user_option_convert

4 バイトを ULONG に変換する

### <a name="prototype"></a>プロトタイプ

```C
ULONG nx_dhcp_user_option_convert(UCHAR *option_string_ptr);
```

### <a name="description"></a>説明

このサービスでは、"option_string_ptr" が指している 4 文字が符号なしの long 値に変換されます。 これは、IP アドレスが存在する場合に特に便利です。

### <a name="input-parameters"></a>入力パラメーター

- **option_string_ptr** 以前に取得されたオプションの文字列へのポインター。

### <a name="return-values"></a>戻り値

- **Value** 最初の 4 バイトの値。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UCHAR  dns_ip_string[4];
ULONG  dns_ip;

/* Convert the first four bytes of “dns_ip_string” to an actual IP
address in “dns_ip.”  */
dns_ip=  nx_dhcp_user_option_convert(dns_ip_string);

/* If status is NX_SUCCESS the DNS IP address is in “dns_ip.”  */
```

## <a name="nx_dhcp_user_option_add_callback_set"></a>nx_dhcp_user_option_add_callback_set

ユーザーが指定したオプションを追加するためにコールバック関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
ULONG nx_dhcp_user_option_add_callbcak_set(NX_DHCP *dhcp_ptr, 
    UINT (*dhcp_user_option_add)(NX_DHCP *dhcp_ptr, 
                                 UINT iface_index, 
                                 UINT message_type, 
                                 UCHAR *user_option_ptr, 
                                 UINT *user_option_length));
```

### <a name="description"></a>説明

このサービスは、ユーザーが指定したオプションを追加するために、指定されたコールバック関数を登録します。

このコールバック関数が指定されている場合、アプリケーションでは iface_index と message_type を使用して、ユーザーが指定したオプションをパケットに追加できます。

> [!NOTE]
> ユーザーのルーチンで。 アプリケーションは、ユーザーが指定したオプションを追加するときに、DHCP オプションの形式に従う必要があります。 ユーザー オプションの合計サイズは user_option_length 以下である必要があり、user_option_length を実際のオプションの長さで更新する必要があります。 オプションが正常に追加された場合は NX_TRUE が返され、それ以外の場合は NX_FALSE が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **dhcp_ptr** 以前に作成された DHCP インスタンスへのポインター。

- **dhcp_user_option_add** ユーザー オプション追加関数へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) コールバックが正常に設定されました。

- NX_PTR_ERROR (0x16) ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Register the “my_dhcp_user_option_add” function to be called when add DHCP
options, assuming DHCP has already been created. */

status =  nx_dhcp_user_option_add_callback_set(&my_dhcp, my_dhcp_user_option_add);

/* If status is NX_SUCCESS the callback function was successfully registered. */
```
