---
title: 第 3 章 - Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) サービスの説明
description: この章では、すべての Azure RTOS NetX Duo PPP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1174d7fdc470bc91278413d56948789cc210aab9d7389a5ecad5baf4f6ad7a7f
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116798080"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-point-to-point-protocol-ppp-services"></a>第 3 章 - Azure RTOS NetX Duo Point-to-Point プロトコル (PPP) サービスの説明

この章では、すべての Azure RTOS NetX Duo PPP サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

- **nx_ppp_byte_receive**: "*シリアル ISR からバイトを受信する*"
- **nx_ppp_chap_challenge**: "*CHAP チャレンジを生成する*"
- **nx_ppp_chap_enable**: "*CHAP 認証を有効にする*"
- **nx_ppp_create**: "*PPP インスタンスを作成する*"
- **nx_ppp_delete**: "*PPP インスタンスを削除する*"
- **nx_ppp_dns_address_get**: "*DNS サーバーの IP アドレスを取得する*"
- **nx_ppp_dns_address_set**: "*DNS サーバーの IP アドレスを設定する*"
- **nx_ppp_secondary_dns_address_get**: "*セカンダリ DNS サーバーの IP アドレスを取得する*"
- **nx_ppp_secondary_dns_address_set**: "*セカンダリ DNS サーバーの IP アドレスを設定する*"
- **nx_ppp_interface_index_get**: "*IP インターフェイス インデックスを取得する*"
- **nx_ppp_ip_address_assign**: "*IPCP 用の IP アドレスを割り当てる*"
- **nx_ppp_link_down_notify**: "*リンクダウン時にアプリケーションに通知する*"
- **nx_ppp_link_down_notify**: "*リンクアップ時にアプリケーションに通知する*"
- **nx_ppp_nak_authentication_notify**: "*認証 NAK を受信した場合にアプリケーションに通知する*"
- **nx_ppp_pap_enable**: "*PAP 認証を有効にする*"
- **nx_ppp_ping_request**: "*LCP エコー要求を送信する*"
- **nx_ppp_raw_string_send**: "*PPP 以外の文字列を送信する*"
- **nx_ppp_restart**: "*PPP の処理を再開する*"
- **nx_ppp_start**: "*PPP の処理を開始する*"
- **nx_ppp_status_get**: "*PPP の現在の状態を取得する*"
- **nx_ppp_stop**: "*PPP の処理を停止する*"
- **nx_ppp_packet_receive**: "*PPP パケットを受信する*"
- **nx_ppp_packet_send_set**: "*PPP パケット送信関数を設定する*"

## <a name="nx_ppp_byte_receive"></a>nx_ppp_byte_receive

シリアル ISR からバイトを受信します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_byte_receive(NX_PPP *ppp_ptr, UCHAR byte);
```

### <a name="description"></a>説明

このサービスは通常、受信したバイトを PPP に転送するために、アプリケーションのシリアル ドライバーの割り込みサービス ルーチン (ISR) から呼び出されます。 呼び出されると、このルーチンは受信したバイトを循環バイト バッファーに配置し、処理のために適切な PPP スレッドに通知します。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **byte**: シリアル デバイスから受信したバイト。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP バイトを正常に受信しました。
- **NX_PPP_BUFFER_FULL**: (0xB1) PPP シリアル バッファーが既にいっぱいになっています。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド、ISR

### <a name="example"></a>例

```c
/* Notify “my_ppp” of a received byte. */
status =  nx_ppp_byte_receive(&my_ppp, new_byte);

/* If status is NX_SUCCESS the received byte was successfully
   buffered. */
```

## <a name="nx_ppp_chap_challenge"></a>nx_ppp_chap_challenge

CHAP チャレンジを生成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_chap_challenge(NX_PPP *ppp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、PPP 接続が稼働状態になった後に CHAP チャレンジが開始されます。 これにより、アプリケーションは接続の信頼性を定期的に確認できます。 チャレンジが失敗すると、PPP リンクは閉じられます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP チャレンジが正常に開始されました。
- **NX_PPP_FAILURE**: (0xB0) PPP チャレンジが無効です。CHAP は応答でのみ有効になっています。
- **NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_CHAP によって CHAP ロジックが無効になっています。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Initiate a PPP challenge for instance “my_ppp”. */
status =  nx_ppp_chap_challenge(&my_ppp);

/* If status is NX_SUCCESS a CHAP challenge “my_ppp” was successfully 
initiated. */
```

## <a name="nx_ppp_chap_enable"></a>nx_ppp_chap_enable

CHAP 認証を有効にします

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_chap_enable(NX_PPP *ppp_ptr, 
                        UINT (*get_challenge_values)(CHAR *rand_value,CHAR *id,CHAR *name),
                        UINT (*get_responder_values)(CHAR *system,CHAR *name,CHAR *secret),
                        UINT (*get_verification_values)(CHAR *system,CHAR *name,CHAR *secret)); 
```

### <a name="description"></a>説明

このサービスを使用すると、指定した PPP インスタンスのチャレンジ ハンドシェイク認証プロトコル (CHAP) が有効になります。

関数ポインター "***get_challenge_values** _" と "_ *_get_verification_values_**" が指定されている場合、この PPP インスタンスに CHAP が必要になります。 それ以外の場合、CHAP はピアのチャレンジ要求にのみ応答します。

必要なコールバック関数で参照されるデータ項目がいくつかあります。 *secret*、*name*、*system* の各データ項目は、最大サイズが NX_PPP_NAME_SIZE-1 の NULL 終端文字列である必要があります。 *rand_value* データ項目は、最大サイズが NX_PPP_VALUE_SIZE-1 の NULL 終端文字列である必要があります。 *id* データ項目は、単純な符号なし文字型です。

>[!NOTE]
> この関数は、*nx_ppp_create* の後、nx_ip_create または *nx_ip_interface_attach* の前に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **get_challenge_values**: チャレンジに使用される値を取得するアプリケーション関数へのポインター。 *rand_value*、*id*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。
- **get_responder_values**: チャレンジへの応答に使用される値を取得するアプリケーション関数へのポインター。 *system*、*name*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。
- **get_verification_values**: チャレンジ応答の検証に使用される値を取得するアプリケーション関数へのポインター。 *system*、*name*、*secret* の各値は、指定されたコピー先にコピーする必要があることに注意してください。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP CHAP が正常に有効になりました。
- **NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_CHAP によって CHAP ロジックが無効になっています。
- NX_PTR_ERROR: (0x07) PPP ポインターまたはコールバック関数ポインターが無効です。 *get_challenge_values* が指定されている場合は、*get_verification_values* 関数も指定する必要があることに注意してください。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
CHAR    name_string[] = "username";
CHAR    rand_value_string[] = "123456";
CHAR    system_string[] = "system";
CHAR    secret_string[] = "secret";

/* Enable CHAP in both directions (CHAP challenger and CHAP responder) for 
“my_ppp”. */
status =  nx_ppp_chap_enable(&my_ppp,   get_challenge_values, 
                              get_responder_values,
                              get_verification_values);


/* If status is NX_SUCCESS, “my_ppp” has CHAP enabled. */
/* Define the CHAP enable routines.  */
UINT  get_challenge_values(CHAR *rand_value, CHAR *id, CHAR *name)
{
   UINT    i;
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   *id =  '1';  /* One byte  */
   for (i = 0; i< (NX_PPP_VALUE_SIZE-1); i++)
   {
      rand_value[i] =  rand_value_string[i];
   }
   rand_value[i] =  0;
   
   return(NX_SUCCESS);  
}


UINT  get_responder_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;

   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

UINT  get_verification_values(CHAR *system, CHAR *name, CHAR *secret)
{
   UINT    i;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      name[i] = name_string[i];
   }
   name[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      system[i] =  system_string[i];
   }
   system[i] =  0;
   
   for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
   {
      secret[i] =  secret_string[i];
   }
   secret[i] =  0;
   
   return(NX_SUCCESS);  
}

```
## <a name="nx_ppp_create"></a>nx_ppp_create

PPP インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_create(NX_PPP *ppp_ptr, CHAR *name, NX_IP *ip_ptr, 
                    VOID *stack_memory_ptr, ULONG stack_size, 
                    UINT thread_priority, NX_PACKET_POOL *pool_ptr,
                    void (*ppp_invalid_packet_handler)(NX_PACKET *packet_ptr),
                    void (*ppp_byte_send)(UCHAR byte));
```

### <a name="description"></a>説明

このサービスでは、指定された NetX IP インスタンスの PPP インスタンスを作成します。 NetX IP インスタンスを作成する前に、この関数を呼び出す必要があります。

>[!NOTE]
> 一般に、PPP スレッドの優先順位よりも高い優先順位で NetX IP スレッドを作成することをお勧めします。 IP スレッドの優先順位の指定の詳細については、*nx_ip_create* サービスを参照してください。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **name**: この PPP インスタンスの名前。
- **ip_ptr**: まだ作成されていない IP インスタンスの制御ブロックへのポインター。
- **stack_memory_ptr**: PPP スレッドのスタック領域の先頭へのポインター。
- **stack_size**: スレッドのスタックのサイズ (バイト単位)。
- **pool_ptr**: 既定のパケット プールへのポインター。
- **thread_priority**: 内部 PPP スレッドの優先順位 (1 - 31)。
- **ppp_invalid_packet_handler**: PPP 以外のすべてのパケットに対するアプリケーションのハンドラーへの関数ポインター。 通常、このルーチンは初期化の間に NetX PPP によって呼び出されます。 ここで、アプリケーションはモデムのコマンドに応答できます。Windows XP の場合、NetX PPP アプリケーションでは、Windows XP によって送信された最初の "CLIENT" に "CLIENT SERVER" で応答することで PPP を開始できます。
- **ppp_byte_send**: アプリケーションのシリアル バイト出力ルーチンへの関数ポインター。


### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP が正常に作成されました。
- NX_PTR_ERROR: (0x07) PPP、IP、またはバイト出力関数ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create “my_ppp” for IP instance “my_ip”. */
status =  nx_ppp_create(&my_ppp, “my PPP”, &my_ip, stack_start, 1024, 2, 
                        &my_pool, my_invalid_packet_handler, my_out_byte);

/* If status is NX_SUCCESS the PPP instance was successfully
   created. */
```

## <a name="nx_ppp_delete"></a>nx_ppp_delete

PPP インスタンスを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_delete(NX_PPP *ppp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、以前に作成された PPP インスタンスが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP が正常に削除されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete PPP instance “my_ppp”. */
status =  nx_ppp_delete(&my_ppp);

/* If status is NX_SUCCESS the “my_ppp” was successfully deleted. */
```

## <a name="nx_ppp_dns_address_get"></a>nx_ppp_dns_address_get

DNS サーバーの IP アドレスを取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>説明

このサービスでは、IPCP ハンドシェイクでピアから提供された DNS IP アドレスを取得します。 ピアから IP アドレスが提供されていない場合は、IP アドレスとして 0 が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **dns_address_ptr**: DNS サーバー アドレスの宛先。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS アドレスが正常に取得されました。
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="example"></a>例

```c

ULONG  my_dns_address;

/* Get DNS Server address supplied by peer. */
status =  nx_ppp_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the DNS IP address – 
   if the peer supplied one. */
```

## <a name="nx_ppp_secondary_dns_address_get"></a>nx_ppp_secondary_dns_address_get

セカンダリ DNS サーバーの IP アドレスを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_secondary_dns_address_get(NX_PPP *ppp_ptr, ULONG *dns_address_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、IPCP ハンドシェイクでピアによって提供されたセカンダリ DNS IP アドレスが取得されます。 ピアから IP アドレスが提供されていない場合は、IP アドレスとして 0 が返されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **dns_address_ptr**: セカンダリ DNS サーバーのアドレスの格納先

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS アドレスが正常に取得されました。
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="example"></a>例

```c
ULONG  my_dns_address;

/* Get secondary DNS Server address supplied by peer. */
status =  nx_ppp_secondary_dns_address_get(&my_ppp, &my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” contains the secondary DNS Server address – if the peer supplied one. */
```

## <a name="nx_ppp_dns_address_set"></a>nx_ppp_dns_address_set

プライマリ DNS サーバーの IP アドレスを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>説明

このサービスを使用すると、DNS サーバーの IP アドレスが設定されます。 ピアが IPCP 状態で DNS サーバー オプション要求を送信すると、このホストが情報を提供します。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **dns_address**: DNS サーバー アドレス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS アドレスが正常に設定されました。
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c

ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the DNS Server address provided if the peer requests one. */

```

## <a name="nx_ppp_secondary_dns_address_set"></a>nx_ppp_secondary_dns_address_set

セカンダリ DNS サーバーの IP アドレスを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_secondary_dns_address_set(NX_PPP *ppp_ptr, ULONG dns_address);
```

### <a name="description"></a>説明

このサービスを使用すると、セカンダリ DNS サーバーの IP アドレスが設定されます。 ピアが IPCP 状態でセカンダリ DNS サーバー オプション要求を送信すると、このホストが情報を提供します。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **dns_address**: セカンダリ DNS サーバー アドレス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) DNS アドレスが正常に設定されました。 
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP はピアとのネゴシエーションを完了していません。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
ULONG  my_dns_address = IP_ADDRESS(1,2,3,1);

/* Set DNS Server address. */
status =  nx_ppp_secondary_dns_address_set(&my_ppp, my_dns_address);

/* If status is NX_SUCCESS the “my_dns_address” will be the secondary DNS Server address provided if the peer requests one. */

```
## <a name="nx_ppp_interface_index_get"></a>nx_ppp_interface_index_get

IP インターフェイスのインデックスを取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_interface_index_get(NX_PPP *ppp_ptr, UINT *index_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、この PPP インスタンスに関連付けられている IP インターフェイスのインデックスが取得されます。 これは、PPP インスタンスが IP インスタンスのプライマリ インターフェイスではない場合にのみ役立ちます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **index_ptr**: インターフェイスのインデックスの格納先

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP インデックスが正常に取得されました。
- **NX_IN_PROGRESS**: (0x37) PPP は初期化を完了していません。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
ULONG  my_index;

/* Get the interface index for this PPP instance. */
status =  nx_ppp_interface_index_get(&my_ppp, &my_index);

/* If status is NX_SUCCESS the “my_index” contains the IP interface index for
   this PPP instance. */

```
## <a name="nx_ppp_ip_address_assign"></a>nx_ppp_ip_address_assign

IPCP 用の IP アドレスを割り当てます

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_ip_address_assign(NX_PPP *ppp_ptr, ULONG local_ip_address, 
            ULONG peer_ip_address);
```

### <a name="description"></a>説明

このサービスでは、インターネット プロトコル制御プロトコル (IPCP) で使用するローカルおよびピアの IP アドレスを設定します。 これは、自身ともう一方のピアの有効な IP アドレスを備えた PPP インスタンスに対して呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **local_ip_address**: ローカル IP アドレス。
- **peer_ip_address**: ピアの IP アドレス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP アドレスが正常に割り当てられました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set IP addresses for “my_ppp”. */
status =  nx_ppp_ip_address_assign(&my_ppp, IP_ADDRESS(256,2,2,187), 
IP_ADDRESS(256,2,2,188));


/* If status is NX_SUCCESS the “my_ppp” has the IP addresses. */
```

## <a name="nx_ppp_link_down_notify"></a>nx_ppp_link_down_notify

リンク ダウン時にアプリケーションに通知します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_link_down_notify(NX_PPP *ppp_ptr, 
                             VOID (*link_down_callback)(NX_PPP *ppp_ptr));
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションのリンク ダウン通知コールバックが、指定した PPP インスタンスに登録されます。 NULL 以外の場合、リンクがダウンするたびに、アプリケーションのリンクダウン コールバック関数が呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **link_down_callback**: アプリケーションのリンク ダウン通知関数へのポインター。 NULL の場合、リンクダウン通知は無効になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) リンクダウン通知コールバックが正常に登録されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="example"></a>例

```c
/* Register “my_link_down_callback” to be called whenever the PPP
   link goes down. */
status =  nx_ppp_link_down_notify(&my_ppp, my_link_down_callback);


/* If status is NX_SUCCESS the function “my_link_down_callback” has been
   registered with this PPP instance. */

VOID my_link_down_callback(NX_PPP *ppp_ptr)
{

/* On link down, simply restart PPP.  */
    nx_ppp_restart(ppp_ptr);
} 
```
## <a name="nx_ppp_link_up_notify"></a>nx_ppp_link_up_notify

リンク アップ時にアプリケーションに通知します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ppp_link_up_notify(NX_PPP *ppp_ptr, 
                           VOID (*link_up_callback)(NX_PPP *ppp_ptr));
```
### <a name="description"></a>説明

このサービスを使用すると、アプリケーションのリンク アップ通知コールバックが、指定した PPP インスタンスに登録されます。 NULL 以外の場合、リンクがアップするたびに、アプリケーションのリンクアップ コールバック関数が呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **link_down_callback**: アプリケーションのリンク アップ通知関数へのポインター。 NULL の場合、リンクアップ通知は無効になります。**

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) リンクアップ通知コールバックが正常に登録されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="example"></a>例

```c
/* Register “my_link_up_callback” to be called whenever the PPP
   link comes up. */
status =  nx_ppp_link_up_notify(&my_ppp, my_link_up_callback);


/* If status is NX_SUCCESS the function “my_link_up_callback” has been
   registered with this PPP instance. */

VOID my_link_up_callback(NX_PPP *ppp_ptr)
{
    /* On link up, the application my want to start sending/receiving
       UPD/TCP data.  */
}
```

## <a name="nx_ppp_nak_authentication_notify"></a>nx_ppp_nak_authentication_notify

認証 NAK を受信した場合にアプリケーションに通知します

### <a name="prototype"></a>プロトタイプ

```c
UINT    nx_ppp_nak_authentication_notify(NX_PPP *ppp_ptr, 
                                         void (*nak_authentication_notify)(void));
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションの認証 NAK 通知コールバックが、指定した PPP インスタンスに登録されます。 NULL 以外の場合、PPP インスタンスが認証時に NAK を受信するたびに、このコールバック関数が呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **nak_authentication_notify**: PPP インスタンスが認証 NAK を受信したときに呼び出される関数へのポインター。 NULL の場合、通知は無効になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) 通知コールバックが正常に登録されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="example"></a>例

```c
/* Register “my_nak_auth_callback” to be called whenever the PPP
   receives a NAK during authentication. */
status =  nx_ppp_nak_authentication_notify(&my_ppp, my_nak_auth_callback);

/* If status is NX_SUCCESS the function “my_nak_auth_callback” has been
   registered with this PPP instance. */

VOID my_nak_auth_callback(NX_PPP *ppp_ptr)
{
   /* Handle the situation of receiving an authentication NAK */
}

```

## <a name="nx_ppp_pap_enable"></a>nx_ppp_pap_enable

PAP 認証を有効にします

### <a name="prototype"></a>プロトタイプ

```c

UINT  nx_ppp_pap_enable(NX_PPP *ppp_ptr, 
                        UINT (*generate_login)(CHAR *name, CHAR *password),
                        UINT (*verify_login)(CHAR *name, CHAR *password));
```

### <a name="description"></a>説明

このサービスを使用すると、指定した PPP インスタンスでパスワード認証プロトコル (PAP) が有効になります。 "***verify_login***" 関数ポインターが指定されている場合は、この PPP インスタンスに PAP が必要になります。 それ以外の場合、PAP は、LCP ネゴシエーション中に指定された、ピアの PAP 要件にのみ応答します。

必要なコールバック関数で参照されるデータ項目がいくつかあります。 *name* データ項目は、最大サイズが NX_PPP_NAME_SIZE-1 の NULL 終端文字列である必要があります。 *password* データ項目も、最大サイズが NX_PPP_PASSWORD_SIZE-1 の NULL 終端文字列である必要があります。

>[!NOTE]
> この関数は、*nx_ppp_create* の後、*nx_ip_create* または *nx_ip_interface_attach* の前に呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **generate_login**: ピアによる認証用の *name* と *password* を生成するアプリケーション関数へのポインター。 *name* と *password* の値は、指定されたコピー先にコピーする必要があることに注意してください。
- **verify_login**: ピアから提供された *name* と *password* を検証するアプリケーション関数へのポインター。 このルーチンでは、提供された *name* および *password* を比較する必要があります。 このルーチンから NX_SUCCESS が返された場合、名前とパスワードは正しいので、PPP は次の手順に進むことができます。 それ以外の場合、このルーチンは NX_PPP_ERROR を返します。PPP は別の名前とパスワードを待機するだけです。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP PAP が正常に有効になりました。
- **NX_NOT_IMPLEMENTED**: (0x80) NX_PPP_DISABLE_PAP によって PAP ロジックが無効になっています。
- NX_PTR_ERROR: (0x07) PPP ポインターまたはアプリケーション関数ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
CHAR    name_string[] = "username";
CHAR    password_string[] =  "password";

/* Enable PAP for PPP instance “my_ppp”. */
status =  nx_ppp_pap_enable(&my_ppp, my_generate_login, my_verify_login);

/* If status is NX_SUCCESS the “my_ppp” now has PAP enabled. */

/* Define callback routines for PAP enable.  */

UINT  generate_login(CHAR *name, CHAR *password)
{

UINT    i;

for (i = 0; i< (NX_PPP_NAME_SIZE-1); i++)
name[i] = name_string[i];
name[i] =  0;

for (i = 0; i< (NX_PPP_PASSWORD_SIZE-1); i++)
password[i] = password_string[i];
password_string[i] =  0;

return(NX_SUCCESS);  
}

UINT  verify_login(CHAR *name, CHAR *password)
{

/* Assume name and password are correct. Normally, 
a comparison would be made here!  */
printf("Name: %s, Password: %s\n", name, password);

return(NX_SUCCESS);  
}
```

## <a name="nx_ppp_ping_request"></a>nx_ppp_ping_request

LCP ping 要求を送信します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_ping_request(NX_PPP *ppp_ptr, CHAR *data, 
                          UINT data_size, ULONG wait_opion);
```

### <a name="description"></a>説明

このサービスでは LCP 要求を送信し、PPP デバイスがエコー応答を待機していることを示すフラグを設定します。 待機オプションは、主に *nx_packet_allocate* 呼び出し用です。 要求が送信されるとすぐに、サービスに制御が戻ります。 応答を待機することはありません。 

対応するエコー応答を受信すると、PPP スレッド タスクによってフラグがクリアされます。 PPP デバイスは、PPP ネゴシエーションの LCP 部分を完了している必要があります。

このサービスは、リンクの状態を確認するためのハードウェアのポーリングを簡単に行うことができない可能性がある PPP 設定で役立ちます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **data**: エコー要求で送信するデータへのポインター。
- **data_size**: 送信するデータのサイズ。wait_option: LCP エコー メッセージの送信を待機する時間。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) エコー要求が正常に送信されました。
- **NX_PPP_NOT_ESTABLISHED**: (0xB5) PPP 接続が確立されていません。
- NX_PTR_ERROR: (0x07) PPP ポインターまたはアプリケーション関数ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

アプリケーション スレッド

### <a name="example"></a>例

```c

CHAR    buffer[] = "username";
UINT    buffer_length =  sizeof("username ") - 1;

/* Send an LCP ping request”. */
status =  nx_ppp_ping_request(&my_ppp, &buffer[0], buffer_length, 200);

/* If status is NX_SUCCESS the LCP echo request was successfully sent. Now wait to 
   receive a response. */

while(my_ppp.nx_ppp_lcp_echo_reply_id > 0)
{
    tx_thread_sleep(100);
}

/* Got a valid reply! */
```

## <a name="nx_ppp_raw_string_send"></a>nx_ppp_raw_string_send

生の ASCII 文字列を送信します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_raw_sting_send(NX_PPP *ppp_ptr, CHAR *string_ptr);
```

### <a name="description"></a>説明

このサービスでは、PPP 以外の ASCII 文字列を PPP インターフェイスから直接送信します。 通常、モデム制御情報を含む PPP 以外のパケットを PPP が受信した後に使用されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **string_ptr**: 送信する文字列へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP 生文字列が正常に送信されました。
- NX_PTR_ERROR: (0x07) PPP ポインターまたは文字列ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c

/* Send “CLIENTSERVER” to “CLIENT” sent by Windows 98 before PPP is
initiated.  */
status =  nx_ppp_raw_string_send(&my_ppp, “CLIENTSERVER”);

/* If status is NX_SUCCESS the raw string was successfully Sent via PPP. */
```
## <a name="nx_ppp_restart"></a>nx_ppp_restart

PPP の処理を再開します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_restart(NX_PPP *ppp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、PPP の処理が再開されます。 通常、リンクを再確立する必要がある場合に、リンクダウン コールバックから呼び出されるか、通信が失われたことを示す PPP 以外のモデム メッセージによって呼び出されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP の再開が正常に開始されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Restart the PPP instance “my_ppp”.  */
status =  nx_ppp_restart(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been restarted. */
```

## <a name="nx_ppp_start"></a>nx_ppp_start

PPP の処理を開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_start(NX_PPP *ppp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、PPP の処理が開始されます。 通常は、nx_ppp_stop() が呼び出された後に呼び出されます。

>[!NOTE]
> PPP では、リンクが有効になると、PPP の処理が自動的に開始されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP が正常に開始されました。 
- **NX_PPP_ALREADY_STARTED**: (0xb9) PPP は既に開始されています。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Start the PPP instance “my_ppp”.  */
status =  nx_ppp_start(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been started. */
```

## <a name="nx_ppp_status_get"></a>nx_ppp_status_get

PPP の現在の状態を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_status_get(NX_PPP *ppp_ptr, UINT *status_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した PPP インスタンスの現在の状態が取得されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **status_ptr**: PPP の状態の格納先。可能性のある状態値は次のとおりです。
    - **NX_PPP_STATUS_ESTABLISHED**
    - **NX_PPP_STATUS_LCP_IN_PROGRESS**
    - **NX_PPP_STATUS_LCP_FAILED**
    - **NX_PPP_STATUS_PAP_IN_PROGRESS**
    - **NX_PPP_STATUS_PAP_FAILED**
    - **NX_PPP_STATUS_CHAP_IN_PROGRESS**
    - **NX_PPP_STATUS_CHAP_FAILED**
    - **NX_PPP_STATUS_IPCP_IN_PROGRESS**
    - **NX_PPP_STATUS_IPCP_FAILED**

>[!NOTE]
> 状態は、API から NX_SUCCESS が返された場合にのみ有効です。 さらに、*_FAILED 状態値のいずれかが返された場合、PPP の処理は、アプリケーションによってもう一度再開されるまで実質的に停止されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="example"></a>例

```c
UINT ppp_status;
UINT status;


/* Get the current status of PPP instance “my_ppp”.  */
status =  nx_ppp_status_get(&my_ppp, &ppp_status);

/* If status is NX_SUCCESS the current internal PPP status is contained in
   “ppp_status”. */
```
## <a name="nx_ppp_stop"></a>nx_ppp_stop

PPP の処理を開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_stop(NX_PPP *ppp_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、PPP の処理が停止されます。 ユーザーは、必要に応じて nx_ppp_start() を呼び出して、PPP の処理を開始することもできます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP が正常に開始されました。 
- **NX_PPP_ALREADY_STOPPED**: (0xb8) PPP は既に停止しています。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。
- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Stop the PPP instance “my_ppp”.  */
status =  nx_ppp_stop(&my_ppp);

/* If status is NX_SUCCESS the PPP instance has been stopped. */
```
## <a name="nx_ppp_packet_receive"></a>nx_ppp_packet_receive

PPP パケットを受信します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_packet_receive(NX_PPP *ppp_ptr, NX_PACKET *packet_ptr);

```

### <a name="description"></a>説明

このサービスを使用すると、PPP パケットが受信されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **packet_ptr**: PPP パケットへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Receive the PPP packet of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_receive(&my_ppp, packet_ptr);

/* If status is NX_SUCCESS the PPP packet has received. */


```
## <a name="nx_ppp_packet_send_set"></a>nx_ppp_packet_send_set

PPP パケット送信関数を設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT  nx_ppp_packet_send_set(NX_PPP *ppp_ptr, 
                             VOID (*nx_ppp_packet_send)(NX_PACKET *packet_ptr));

```

### <a name="description"></a>説明

このサービスを使用すると、PPP パケット送信関数が設定されます。

### <a name="input-parameters"></a>入力パラメーター

- **ppp_ptr**: PPP 制御ブロックへのポインター。
- **nx_ppp_packet_send**: PPP パケットを送信するルーチン。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) PPP 状態要求が正常に実行されました。
- NX_PTR_ERROR: (0x07) PPP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Set the PPP packet send function of PPP instance “my_ppp”.  */
status =  nx_ppp_packet_send_set(&my_ppp, nx_ppp_packet_send);

/* If status is NX_SUCCESS the PPP packet send function has set. */


```