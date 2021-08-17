---
title: 第 4 章 - Azure RTOS NetX Duo サービスの説明
description: この章は、すべての Azure RTOS NetX Duo サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: d28ca64a6a655bb3f1ad10c563450a0e65b645a1e1a2a464c4137f9a999815bc
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116785024"
---
# <a name="chapter-4---description-of-azure-rtos-netx-duo-services"></a>第 4 章 - Azure RTOS NetX Duo サービスの説明

この章は、すべての Azure RTOS NetX Duo サービスの説明をアルファベット順にまとめたものです。 サービス名は、類似するすべてのサービスがグループ化されるように命名されています。 たとえば、すべての ARP サービスは、この章の最初にあります。 

NetX Duo には、IPv6 ベースのプロトコルと操作をサポートするために導入された新しいサービスが数多くあります。 Net Duo の IPv6 対応サービスには、IPv4 および IPv6 のデュアル スタック操作用に設計されていることを示すプレフィックス ***nxd*** が付いています。

NetX の既存のサービスは、NetX Duo で完全にサポートされています。 NetX アプリケーションは、最小限の移植作業で NetX Duo に移行できます。

> [!NOTE]
> *高パフォーマンスの NetX Duo API を最大限に活用できないレガシ アプリケーション コードでは BSD-Compatible SOCKET API を使用できます。BSD-Compatible Socket API の詳細については、付録 D を参照してください*。

各説明の「戻り値」セクションにある **太字** の値は、API エラー チェックを無効にするために使用される NX_DISABLE_ERROR_CHECKING オプションの影響を受けませんが、太字でない値は完全に無効になります。 「許可元」セクションには、各 NetX Duo サービスを呼び出すことのできる呼び出し元が説明されています。

## <a name="nx_arp_dynamic_entries_invalidate"></a>nx_arp_dynamic_entries_invalidate   
ARP キャッシュ内のすべての動的エントリを無効にします

### <a name="prototype"></a>プロトタイプ     

```c
UINT nx_arp_dynamic_entries_invalidate(NX_IP *ip_ptr);
```

### <a name="description"></a>説明   
このサービスを使用すると、現在 ARP キャッシュにあるすべての動的 ARP エントリが無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ARP キャッシュの無効化に成功しました。
- **NX_NOT_ENABLED** (0x14) ARP が有効になっていません。
- **NX_PTR_ERROR** (0x07) IP アドレスが無効です。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドではありません。

### <a name="allowed-from"></a>許可元   
Threads

### <a name="preemption-possible"></a>プリエンプション可能    
いいえ

### <a name="example"></a>例

```c
/* Invalidate all dynamic entries in the ARP cache. */
status = nx_arp_dynamic_entries_invalidate(&ip_0);

/* If status is NX_SUCCESS the dynamic ARP entries were
   successfully invalidated. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_dynamic_entry_set"></a>nx_arp_dynamic_entry_set  
動的 ARP エントリを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_dynamic_entry_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);  
```

### <a name="description"></a>説明    
このサービスを使用すると、ARP キャッシュから動的エントリが割り当てられ、指定した IP が物理アドレス マッピングに設定されます。 物理アドレスがゼロに指定されている場合は、その物理アドレスを解決するために、実際の ARP 要求がネットワークに送信されます。 別の注意すべき点として、ARP エージングがアクティブである場合や、ARP キャッシュが使い果たされていて、これが最も長く使用されていない ARP エントリである場合は、このエントリは削除されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** マップする IP アドレス。
- **physical_msw** 物理アドレスの上位 16 ビット (47-32)。
- **physical_lsw** 物理アドレスの下位 32 ビット (31-0)。

### <a name="return-values"></a>戻り値    

- **NX_SUCCESS** (0x00) ARP の動的エントリの設定に成功しました。
- **NX_NO_MORE_ENTRIES** (0x17) ARP キャッシュで使用できる ARP エントリがこれ以上ありません。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP インスタンス ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元    
Threads

### <a name="preemption-possible"></a>プリエンプション可能    
いいえ

### <a name="example"></a>例

```c
/* Setup a dynamic ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_dynamic_entry_set(&ip_0, IP_ADDRESS(1,2,3,4),
                                  0x1022, 0x1234);

/* If status is NX_SUCCESS, there is now a dynamic mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   10:22:00:00:12:34. */
```
### <a name="see-also"></a>参照 

- nx_arp_dynamic_entries_invalidate
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_enable"></a>nx_arp_enable  
アドレス解決プロトコル (ARP) を有効にします

### <a name="prototype"></a>プロトタイプ    

```c
UINT nx_arp_enable(
    NX_IP *ip_ptr, 
    VOID *arp_cache_memory,
    ULONG arp_cache_size);
```

### <a name="description"></a>説明

このサービスでは、特定の IP インスタンスの NetX Duo の ARP コンポーネントを初期化します。 ARP の初期化には、ARP メッセージの送受信に必要な ARP キャッシュやさまざまな ARP 処理ルーチンの設定が含まれます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **arp_cache_memory** ARP キャッシュを配置するメモリ領域を指すポインター。
- **arp_cache_size** 各 ARP エントリは 52 バイトであるため、ARP の合計数は 52 で割ることのできる数になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ARP の有効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP またはキャッシュ メモリ ポインターが無効です。
- **NX_SIZE_ERROR** (0x09) ユーザーが指定した ARP キャッシュ メモリが小さすぎます。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_ALREADY_ENABLED** (0x15) このコンポーネントは既に有効になっています。

### <a name="allowed-from"></a>許可元   
初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能  
いいえ

### <a name="example"></a>例

```c
/* Enable ARP and supply 1024 bytes of ARP cache memory for
   previously created IP Instance ip_0. */
status = nx_arp_enable(&ip_0, (void *) pointer, 1024);

/* If status is NX_SUCCESS, ARP was successfully enabled for this IP
instance.*/
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_entry_delete"></a>nx_arp_entry_delete   
ARP エントリを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_entry_delete(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>説明

このサービスでは、指定された IP アドレスの ARP エントリを、その IP 内部の ARP テーブルから削除します。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 指定された IP アドレスを持つ ARP エントリは削除される必要があります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ARP の有効化に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) 指定された IP アドレスを持つエントリが見つかりません。
- **NX_PTR_ERROR** (0x07) IP またはキャッシュ メモリ ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定された IP アドレスが無効です。

### <a name="allowed-from"></a>許可元  
初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能  
いいえ

### <a name="example"></a>例

```c
/* Delete the ARP entry with the IP address 1.2.3.4. */
status = nx_arp_entry_delete(&ip_0, IP_ADDRESS(1, 2, 3, 4));

/* If status is NX_SUCCESS, ARP entry with the specified IP address
   is deleted.*/
```

### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_gratuitous_send"></a>nx_arp_gratuitous_send   
無償 ARP 要求を送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_gratuitous_send(
    NX_IP *ip_ptr,
    VOID (*response_handler)(NX_IP *ip_ptr, NX_PACKET *packet_ptr));
```                               
### <a name="description"></a>説明

このサービスを使用すると、インターフェイスの IP アドレスが有効である限り、すべての物理インターフェイスを経由して、無償 ARP 要求が送信されます。 その後、ARP 応答を受信した場合は、提供された応答ハンドラーが呼び出されて、無償 ARP への応答が処理されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **response_handler** 応答処理関数を指すポインター。 NX_NULL が指定されている場合、応答は無視されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 無償 ARP の送信に成功しました。
- **NX_NO_PACKET** (0x01) 使用可能なパケットがありません。
- **NX_NOT_ENABLED** (0x14) ARP が有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) 現在の IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```
/* Send gratuitous ARP without any response handler. */
status = nx_arp_gratuitous_send(&ip_0, NX_NULL);

/* If status is NX_SUCCESS the gratuitous ARP was successfully
   sent. */
```

### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_hardware_address_find"></a>nx_arp_hardware_address_find
IP アドレスに関連付けられている物理ハードウェア アドレスを特定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_hardware_address_find(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP アドレスに関連付けられている ARP キャッシュ内の物理ハードウェア アドレスの検索が試みられます。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 検索する IP アドレス。
- **physical_msw** 物理アドレスの上位 16 ビット (47-32) を返すための変数を指すポインター。
- **physical_lsw** 物理アドレスの下位 32 ビット (31-0) を返すための変数を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ARP ハードウェア アドレスの検索に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) マッピングが ARP キャッシュに見つかりませんでした。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP またはメモリ ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Search for the hardware address associated with the IP address of
   1.2.3.4 in the ARP cache of the previously created IP
   Instance 0. */
status = nx_arp_hardware_address_find(&ip_0, IP_ADDRESS(1,2,3,4),
                                      &physical_msw,
                                      &physical_lsw);

/* If status is NX_SUCCESS, the variables physical_msw and
   physical_lsw contain the hardware address.*/
```   
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_info_get"></a>nx_arp_info_get
ARP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_info_get(
    NX_IP *ip_ptr,
    ULONG *arp_requests_sent,
    ULONG *arp_requests_received,
    ULONG *arp_responses_sent,
    ULONG *arp_responses_received,
    ULONG *arp_dynamic_entries,
    ULONG *arp_static_entries,
    ULONG *arp_aged_entries,
    ULONG *arp_invalid_messages);
```

### <a name="description"></a>説明

このサービスでは、関連付けられている IP インスタンスの ARP アクティビティに関する情報を取得します。

> [!NOTE]
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **arp_requests_sent** この IP インスタンスから送信された ARP 要求の合計の宛先を指すポインター。
- **arp_requests_received** ネットワークから受信した ARP 要求の合計の宛先を指すポインター。
- **arp_responses_sent** この IP インスタンスから送信された ARP 要求の合計の宛先を指すポインター。
- **arp_responses_received** ネットワークから受信した ARP 応答の合計の宛先を指すポインター。
- **arp_dynamic_entries** 現在の動的 ARP エントリ数の宛先を指すポインター。
- **arp_static_entries** 現在の静的 ARP エントリ数の宛先を指すポインター。
- **arp_aged_entries** 期限切れで無効になった ARP エントリの合計数の宛先を指すポインター。
- **arp_invalid_messages** 受信した無効な ARP メッセージの合計の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ARP 情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Pickup ARP information for ip_0. */
status = nx_arp_info_get(&ip_0, &arp_requests_sent,
                         &arp_requests_received,
                         &arp_responses_sent,
                         &arp_responses_received,
                         &arp_dynamic_entries,
                         &arp_static_entries,
                         &arp_aged_entries,
                         &arp_invalid_messages);

/* If status is NX_SUCCESS, the ARP information has been stored in
   the supplied variables. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_ip_address_find"></a>nx_arp_ip_address_find
物理アドレスに関連付けられている IP アドレスを特定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_ip_address_find(
    NX_IP *ip_ptr, 
    ULONG *ip_address,
    ULONG physical_msw, 
    ULONG physical_lsw);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した物理アドレスに関連付けられている ARP キャッシュ内の IP アドレスの検索が試みられます。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** マップされた IP アドレスが見つかった場合は、それを返すためのポインター。
- **physical_msw** 検索対象の物理アドレスの上位 16 ビット (47-32)。
- **physical_lsw** 検索対象の物理アドレスの下位 32 ビット (31-0)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ARP IP アドレスの検索に成功しました 
- **NX_ENTRY_NOT_FOUND** (0x16) マッピングが ARP キャッシュに見つかりませんでした。
- **NX_PTR_ERROR** (0x07) IP またはメモリ ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_INVALID_PARAMETERS** (0x4D) physical_msw と physical_lsw がどちらも 0 です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Search for the IP address associated with the hardware address of
   0x0:0x01234 in the ARP cache of the previously created IP
   Instance ip_0. */
status = nx_arp_ip_address_find(&ip_0, &ip_address, 0x0, 0x1234);

/* If status is NX_SUCCESS, the variables ip_address contains the
   associated IP address. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entries_delete"></a>nx_arp_static_entries_delete
すべての静的 ARP エントリを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_static_entries_delete(NX_IP *ip_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、ARP キャッシュ内のすべての静的エントリが削除されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 静的エントリが削除されました。
- **NX_PTR_ERROR** (0x07) ip_ptr ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Delete all the static ARP entries for IP Instance 0, assuming
   "ip_0" is the NX_IP structure for IP Instance 0. */
status = nx_arp_static_entries_delete(&ip_0);

/* If status is NX_SUCCESS all static ARP entries in the ARP cache
   have been deleted. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_create"></a>nx_arp_static_entry_create
ARP キャッシュにハードウェア マッピングへの静的 IP を作成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_static_entry_create(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンスの ARP キャッシュに静的 IP から物理アドレスへのマッピングが作成されます。 静的 ARP エントリは、ARP の定期的な更新の対象にはなりません。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** マップする IP アドレス。
- **physical_msw** マップする物理アドレスの上位 16 ビット (47-32)。
- **physical_lsw** マップする物理アドレスの下位 32 ビット (31-0)。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 静的 ARP エントリの作成に成功しました。
- **NX_NO_MORE_ENTRIES** (0x17) ARP キャッシュで使用できる ARP エントリがこれ以上ありません。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_INVALID_PARAMETERS** (0x4D) physical_msw と physical_lsw がどちらも 0 です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Create a static ARP entry on the previously created IP
   Instance 0. */
status = nx_arp_static_entry_create(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, there is now a static mapping between
   the IP address of 1.2.3.4 and the physical hardware address of
   0x00:0x1234. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_arp_static_entry_delete"></a>nx_arp_static_entry_delete 
ARP キャッシュのハードウェア マッピングへの静的 IP を削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_arp_static_entry_delete(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG physical_msw,
    ULONG physical_lsw);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンスの ARP キャッシュに以前に作成された静的 IP から物理アドレスへのマッピングが検索されて削除されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 静的にマップされた IP アドレス。
- **physical_msw** 静的にマップされた物理アドレスの上位 16 ビット (47 - **32)。
- **physical_lsw** 静的にマップされた物理アドレスの下位 32 ビット (31 - **0)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 静的 ARP エントリの削除に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) 静的 ARP エントリが ARP キャッシュに見つかりませんでした。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_INVALID_PARAMETERS** (0x4D) physical_msw と physical_lsw がどちらも 0 です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Delete a static ARP entry on the previously created IP
   instance ip_0. */
status = nx_arp_static_entry_delete(&ip_0, IP_ADDRESS(1,2,3,4),
                                    0x0, 0x1234);

/* If status is NX_SUCCESS, the previously created static ARP entry
   was successfully deleted. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nx_icmp_enable"></a>nx_icmp_enable
インターネット制御メッセージ プロトコル (ICMP) を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンスの ICMP コンポーネントが有効になります。 この ICMP コンポーネントは、インターネット エラー メッセージと ping の要求および応答を処理する役割を果たします。 

> [!IMPORTANT]  
> *このサービスでは、IPv4 サービス用の ICMP のみが有効になります。ICMPv4 と ICMPv6 の両方を有効にするには、アプリケーションで **nxd_icmp_enable** サービスを使用する必要があります*。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ICMP の有効化に成功しました。
- **NX_ALREADY_ENABLED** (0x15) ICMP は既に有効になっています。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable ICMP on the previously created IP Instance ip_0. */
status = nx_icmp_enable(&ip_0);

/* If status is NX_SUCCESS, ICMP is enabled. */
```
### <a name="see-also"></a>参照

- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_info_get"></a>nx_icmp_info_get
ICMP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_icmp_info_get(
    NX_IP *ip_ptr,
    ULONG *pings_sent,
    ULONG *ping_timeouts,
    ULONG *ping_threads_suspended,
    ULONG *ping_responses_received,
    ULONG *icmp_checksum_errors,
    ULONG *icmp_unhandled_messages);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの ICMP アクティビティに関する情報を取得します。

> [!NOTE]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **pings_sent** 送信された ping の合計数の宛先を指すポインター。
- **ping_timeouts** ping タイムアウトの合計数の宛先を指すポインター。
- **ping_threads_suspended** ping 要求で中断されているスレッドの合計数の宛先へのポインター。
- **ping_responses_received** 受信した ping 応答の合計数の宛先へのポインター。
- **icmp_checksum_errors** ICMP チェックサム エラーの合計数の宛先へのポインター。
- **icmp_unhandled_messages** 処理されていない ICMP メッセージの合計数の宛先へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ICMP 情報の取得に成功しました。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve ICMP information from previously created IP
   instance ip_0. */
status = nx_icmp_info_get(&ip_0, &pings_sent, &ping_timeouts,
                          &ping_threads_suspended,
                          &ping_responses_received,
                          &icmp_checksum_errors,
                          &icmp_unhandled_messages);
/* If status is NX_SUCCESS, ICMP information was retrieved. */
```
### <a name="see-also"></a>参照

- nx_icmp_enable
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_icmp_ping"></a>nx_icmp_ping  
指定された IP アドレスに ping 要求を送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_icmp_ping(
    NX_IP *ip_ptr,
    ULONG ip_address,
    CHAR *data, ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP アドレスに ping 要求が送信され、ping 応答メッセージを指定した時間だけ待機します。 応答が受信されない場合は、エラーが返されます。 それ以外の場合は、response_ptr によってポイントされている変数で応答メッセージ全体が返されます。 

IPv6 宛先に ping 要求を送信するには、アプリケーションで ***nxd_icmp_ping** _ または _ *_nxd_icmp_source_ping_** サービスを使用する必要があります。

> [!WARNING]  
> *NX_SUCCESS が返された場合、不要になった受信パケットを解放する責任はアプリケーションにあります*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** ping する IP アドレス (ホストのバイト順)。
- **data** ping メッセージのデータ領域へのポインター。
- **data_size** ping データ内のバイト数。
- **response_ptr** ping 応答メッセージを返すパケット ポインターへのポインター。
- **wait_option** ping 応答を待機する ThreadX のタイマー ティック数を定義します。 この待機オプションは次のように定義されます。

| 待機オプション            | 値                           |
| -----------------------|---------------------------------|
| NX_NO_WAIT             | (0x00000000)                    |
| タイムアウト値 (ティック数) | (0x00000001 から 0xFFFFFFFE) |
| NX_WAIT_FOREVER        | 0xFFFFFFFF                      |

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ping に成功しました。 応答メッセージ ポインターは、response_ptr によってポイントされる変数に配置されました。
- **NX_NO_PACKET** (0x01) ping 要求パケットを割り当てることができません。
- **NX_OVERFLOW** (0x03) 指定されたデータ領域が、この IP インスタンスの既定のパケット サイズを超えています。
- **NX_NO_RESPONSE** (0x29) 要求された IP が応答しませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP または応答ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Issue a ping to IP address 1.2.3.5 from the previously created IP
   Instance ip_0. */
status = nx_icmp_ping(&ip_0, IP_ADDRESS(1,2,3,5), "abcd", 4,
                      &response_ptr, 10);

/* If status is NX_SUCCESS, a ping response was received from IP
   address 1.2.3.5 and the response packet is contained in the
   packet pointed to by response_ptr. It should have the same "abcd"
   four bytes of data. */
```
### <a name="see-also"></a>参照

- nx_icmp_enable
- nx_icmp_info_get
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nx_igmp_enable"></a>nx_igmp_enable
インターネット グループ管理プロトコル (IGMP) を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンスの IGMP コンポーネントが有効になります。 IGMP コンポーネントは、IP マルチキャスト グループ管理操作のサポートを提供する役割を果たします。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IGMP の有効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_ALREADY_ENABLED** (0x15) このコンポーネントは既に有効になっています。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable IGMP on the previously created IP Instance ip_0. */
status = nx_igmp_enable(&ip_0);

/* If status is NX_SUCCESS, IGMP is enabled. */
```
### <a name="see-also"></a>参照

- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_info_get"></a>nx_igmp_info_get
IGMP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_info_get(
    NX_IP *ip_ptr,
    ULONG *igmp_reports_sent,
    ULONG *igmp_queries_received,
    ULONG *igmp_checksum_errors,
    ULONG *current_groups_joined);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの IGMP アクティビティに関する情報を取得します。

> [!IMPORTANT]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **igmp_reports_sent** 送信された ICMP レポートの合計数の宛先を指すポインター。
- **igmp_queries_received** マルチキャスト ルーターによって受信されたクエリの合計数の宛先を指すポインター。
- **igmp_checksum_errors** 受信パケットの IGMP チェックサム エラーの合計数の宛先を指すポインター。
- **current_groups_joined** この IP インスタンスを介して参加している現在のグループ数の宛先を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IGMP 情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve IGMP information from previously created IP Instance ip_0. */
status = nx_igmp_info_get(&ip_0, &igmp_reports_sent,
                          &igmp_queries_received,
                          &igmp_checksum_errors,
                          &current_groups_joined);

/* If status is NX_SUCCESS, IGMP information was retrieved. */
```

### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_disable"></a>nx_igmp_loopback_disable
IGMP ループバックを無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_loopback_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、以降に参加したすべてのマルチキャスト グループの IGMP ループバックが無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IGMP ループバックの無効化に成功しました。
- **NX_NOT_ENABLED** (0x14) IGMP が有効になっていません。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Disable IGMP loopback for all subsequent multicast groups
   joined. */
status = nx_igmp_loopback_disable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is disabled. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_loopback_enable"></a>nx_igmp_loopback_enable
IGMP ループバックを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_loopback_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、以降に参加したすべてのマルチキャスト グループの IGMP ループバックが有効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IGMP ループバックの無効化に成功しました。
- **NX_NOT_ENABLED** (0x14) IGMP が有効になっていません。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable IGMP loopback for all subsequent multicast
   groups joined. */
status = nx_igmp_loopback_enable(&ip_0);

/* If status is NX_SUCCESS IGMP loopback is enabled. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_join"></a>nx_igmp_multicast_interface_join
指定されたマルチキャスト グループに IP インスタンスをインターフェイス経由で参加させます

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したネットワーク インターフェイス経由で、指定したマルチキャスト グループに IP インスタンスを参加できます。 内部カウンターは、同じグループに参加した回数を追跡するために保持されます。 マルチキャスト グループに参加した後、この IGMP コンポーネントによって、このグループ アドレスを持つ IP パケットを指定されたネットワーク インターフェイス経由で受信することが許可されます。また、この IP がこのマルチキャスト グループのメンバーであることがルーターに報告されます。 IGMP メンバーシップの参加、報告、脱退のメッセージも、指定されたネットワーク インターフェイス経由で送信されます。 IGMP グループ メンバーシップ レポートを送信せずに IPv4 マルチキャスト グループに参加するには、アプリケーションでサービス ***nx_ipv4_multicast_interface_join*** を使用する必要があります。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **group_address** 参加するクラス D IP マルチキャスト グループ アドレス (ホストのバイト順)。
- **interface_index** NetX Duo インスタンスに接続されているインターフェイスのインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。
- **NX_NO_MORE_ENTRIES** (0x17) これ以上、マルチキャスト グループに参加できません。最大値を超えています。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定されたマルチキャスト グループ アドレスは、有効なクラス D アドレスではありません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IP マルチキャスト サポートが有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Previously created IP Instance joins the multicast group
   244.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_join
                                 (&ip IP_ADDRESS(244,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```   
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_interface_leave"></a>nx_igmp_multicast_interface_leave
指定したマルチキャスト グループをインターフェイス経由で脱退します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイス経由で、指定されたマルチキャスト グループを脱退します。 同じグループのメンバーになった回数を追跡するため、内部カウンターが保持されます。 マルチキャスト グループを脱退すると、IGMP コンポーネントは適切なメンバーシップ レポートを送信し、このノードのメンバーが存在しない場合はそのグループを脱退する可能性があります。 IGMP グループ メンバーシップ レポートを送信せずに IPv4 マルチキャスト グループを脱退するには、アプリケーションでサービス ***nx_ipv4_multicast_interface_leave*** を使用する必要があります。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **group_address** 脱退するクラス D IP マルチキャスト グループ アドレス。 この IP アドレスは、ホストのバイト順になっています。
- **interface_index** NetX Duo インスタンスに接続されているインターフェイスのインデックス。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) 指定したマルチキャスト グループ アドレスがローカル マルチキャスト テーブルに見つかりません。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定されたマルチキャスト グループ アドレスは、有効なクラス D アドレスではありません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IP マルチキャスト サポートが有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Leave the multicast group 244.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_igmp_multicast_interface_leave
                                (&ip IP_ADDRESS(244,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_join"></a>nx_igmp_multicast_join
指定されたマルチキャスト グループに IP インスタンスを参加させます

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_multicast_join(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したマルチキャスト グループに IP インスタンスを参加できます。 内部カウンターは、同じグループに参加した回数を追跡するために保持されます。 これが、ホストがグループに参加しようとしていることを示すネットワーク上に送信される最初の参加要求である場合、このドライバーは IGMP レポートを送信するように命令されます。 参加後に、この IGMP コンポーネントは、このグループ アドレスを使用した IP パケットの受信を許可し、その IP がこのマルチキャスト グループのメンバーであることをルーターに報告します。 IGMP グループ メンバーシップ レポートを送信せずに IPv4 マルチキャスト グループに参加するには、アプリケーションでサービス ***nx_ipv4_multicast_interface_join*** を使用する必要があります。

> [!NOTE]  
> *非プライマリ デバイスのマルチキャスト グループに参加するには、サービス **nx_igmp_multicast_interface_join** を使用します。*

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **group_address** 参加するクラス D IP マルチキャスト グループ アドレス。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。
- **NX_NO_MORE_ENTRIES** (0x17) これ以上、マルチキャスト グループに参加できません。最大値を超えています。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。
- **NX_IP_ADDRESS_ERROR** (0x21) IP グループ アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Previously created IP Instance ip_0 joins the multicast group
   224.0.0.200. */
status = nx_igmp_multicast_join(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully
   joined the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_igmp_multicast_leave"></a>nx_igmp_multicast_leave
指定したマルチキャスト グループから IP インスタンスを脱退させます

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_igmp_multicast_leave(
    NX_IP *ip_ptr, 
    ULONG group_address);
```
### <a name="description"></a>説明

このサービスでは、脱退要求の数が参加要求の数と一致する場合、その指定されたマルチキャスト グループから IP インスタンスを脱退させます。 それ以外の場合は、内部の参加カウントが単にデクリメントされます。 IGMP グループ メンバーシップ レポートを送信せずに IPv4 マルチキャスト グループを脱退するには、アプリケーションでサービス ***nx_ipv4_multicast_interface_leave*** を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **group_address** 脱退するマルチキャスト グループ。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) 前の参加要求が見つかりませんでした。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。
- **NX_IP_ADDRESS_ERROR** (0x21) IP グループ アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Cause IP instance to leave the multicast group 224.0.0.200. */
status = nx_igmp_multicast_leave(&ip_0, IP_ADDRESS(224,0,0,200);

/* If status is NX_SUCCESS, this IP instance has successfully left
   the multicast group 224.0.0.200. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ip_address_change_notifiy"></a>nx_ip_address_change_notifiy
IP アドレスが変化した場合、アプリケーションに通知します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_address_change_notify(
    NX_IP *ip_ptr,
    VOID(*change_notify)(NX_IP *, VOID *),
    VOID *additional_info);
```
### <a name="description"></a>説明

このサービスでは、IPv4 アドレスが変更されるたびに呼び出されるアプリケーション通知関数を登録します。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **change_notify** IP 変更通知関数を指すポインター。 このパラメーターが NX_NULL の場合、IP アドレスの変更通知は無効になります。
- **additional_info** IP アドレスが変更されたときに通知関数にも提供されるオプションの追加情報を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP アドレスの変更通知に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Register the function "my_ip_changed" to be called whenever the
   IP address is changed. */
status = nx_ip_address_change_notify(&ip_0, my_ip_changed,
                                      NX_NULL);

/* If status is NX_SUCCESS, the "my_ip_changed" function will be
   called whenever the IP address changes. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_get"></a>nx_ip_address_get
IPv4 アドレスとネットワーク マスクを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_address_get(
    NX_IP *ip_ptr,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>説明

このサービスでは、プライマリ ネットワーク インターフェイスの IPv4 アドレスとそのサブネット マスクを取得します。

> [!IMPORTANT]   
> *セカンダリ デバイスの情報を取得するには、サービス **nx_ip_interface_address_get** を使用します*。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** IP アドレスの宛先を指すポインター。
- **network_mask** ネットワーク マスクの宛先を指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) IP アドレスの取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP または戻り変数ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the IP address and network mask from the previously created
   IP Instance ip_0. */
status = nx_ip_address_get(&ip_0, &ip_address, &network_mask);

/* If status is NX_SUCCESS, the variables ip_address and
   network_mask contain the IP and network mask respectively. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_address_set"></a>nx_ip_address_set
IPv4 アドレスとネットワーク マスクを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_address_set(
    NX_IP *ip_ptr,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>説明

このサービスでは、プライマリ ネットワーク インターフェイスの IPv4 アドレスとネットワーク マスクを設定します。

> [!IMPORTANT]  
> *セカンダリ デバイスの IP アドレスとネットワーク マスクを設定するには、サービス **nx_ip_interface_address_set** を使用します*。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 新しい IP アドレス。
- **network_mask** 新しいネットワーク マスク。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレスの設定に成功しました。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Set the IP address and network mask to 1.2.3.4 and 0xFFFFFF00 for
   the previously created IP Instance ip_0. */
status = nx_ip_address_set(&ip_0, IP_ADDRESS(1,2,3,4),
                           0xFFFFFF00UL);

/* If status is NX_SUCCESS, the IP instance now has an IP address of
   1.2.3.4 and a network mask of 0xFFFFFF00. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_auxiliary_packet_pool_set"></a>nx_ip_auxiliary_packet_pool_set
補助パケット プールを構成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_auxiliary_packet_pool_set(
    NX_IP *ip_ptr,
    NX_PACKET_POOL *aux_pool);
```
### <a name="description"></a>説明

このサービスでは、IP インスタンスに補助パケット プールを構成します。 メモリに制約のあるシステムの場合、ユーザーは、メモリの効率を向上させるため、パケット サイズが MTU である既定のパケット プールを作成したり、それよりも小さいパケット サイズの補助パケット プールを IP スレッド用に作成して、小さいパケットを送信するために使用したりすることができます。 IPv6 と IPsec の両方が有効になっている場合、補助プールの推奨パケット サイズは 256 バイトです。

既定では、IP インスタンスは、補助パケット プールを受け入れません。 この機能を有効にするには、NetX Duo ライブラリをコンパイルするときに *NX_DUAL_PACKET_POOL_ENABLE* を定義する必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **aux_pool** その IP インスタンス用に構成する補助パケット プール。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) IP アドレスの設定に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) デュアル パケット プール機能がライブラリにコンパイルされていません。
- **NX_PTR_ERROR** (0x07) IP ポインターまたはプール ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能  

いいえ

### <a name="example"></a>例

```c
#define SMALL_PAYLOAD_SIZE 256
NX_PACKET small_pool;

nx_packet_pool_create(&small_pool, "small pool", SMALL_PAYLOAD_SIZE,
                       small_pool_memory_ptr, small_pool_size);

/* Add the small packet pool to the IP instance. */
status = nx_ip_auxiliary_packet_pool_set(&ip_0, &small_pool);

/* If status is NX_SUCCESS, the IP instance now is able to use the
   small pool for transmitting small datagram. */
```
### <a name="see-also"></a>参照

- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_ip_create"></a>nx_ip_create
IP インスタンスを作成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_create(
    NX_IP *ip_ptr, 
    CHAR *name, ULONG ip_address,
    ULONG network_mask, 
    NX_PACKET_POOL *default_pool,
    VOID (*ip_network_driver)(NX_IP_DRIVER *),
    VOID *memory_ptr, 
    ULONG memory_size,
    UINT priority);
```
### <a name="description"></a>説明

このサービスを使用すると、ユーザーが指定した IP アドレスとネットワーク ドライバーを持つ IP インスタンスが作成されます。 また、このアプリケーションは、その IP インスタンスが内部パケット割り当てに使用するために、以前に作成したパケット プールを指定する必要があります。 この IP のスレッドが実行されるまで、指定されたアプリケーション ネットワーク ドライバーは呼び出されないことにご注意ください。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 新しい IP インスタンスを作成するための制御ブロックを指すポインター。
- **name** この新しい IP インスタンスの名前。
- **ip_address** この新しい IP インスタンスの IP アドレス。
- **network_mask** サブネット化またはスーパーネット化で使用する IP アドレスのネットワーク部分を表すマスク。
- **default_pool** 以前に作成された NetX Duo パケット プールの制御ブロックへのポインター。
- **ip_network_driver** IP パケットを送受信するために使用される、ユーザーが指定したネットワーク ドライバー。
- **memory_ptr** IP ヘルパー スレッドのスタック領域のメモリ領域を指すポインター。
- **memory_size** IP ヘルパー スレッドのスタックのメモリ領域内のバイト数。
- **priority** IP ヘルパー スレッドの優先順位。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP インスタンスの作成に成功しました。
- **NX_NOT_IMPLEMENTED** (0x4A) NetX Duo ライブラリが正しく構成されていません。
- **NX_PTR_ERROR** (0x07) IP、ネットワーク ドライバー関数ポインター、パケット プール、またはメモリ ポインターが無効です。
- **NX_SIZE_ERROR** (0x09) 指定されたスタック サイズが小さすぎます。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定された IP アドレスが無効です。
- **NX_OPTION_ERROR** (0x21) 指定された IP スレッドの優先順位が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Create an IP instance with an IP address of 1.2.3.4 and a network
   mask of 0xFFFFFF00UL. The "ethernet_driver" specifies the entry
   point of the application specific network driver and the
   "stack_memory_ptr" specifies the start of a 1024 byte memory
   area that is used for this IP instance’s helper thread. */
status = nx_ip_create(&ip_0, "NetX IP Instance ip_0",
                      IP_ADDRESS(1, 2, 3, 4),
                      0xFFFFFF00UL, &pool_0, ethernet_driver,
                      stack_memory_ptr, 1024, 1);

/* If status is NX_SUCCESS, the IP instance has been created. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_delete"></a>nx_ip_delete
以前に作成した IP インスタンスを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_delete(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成した IP インスタンスが削除され、その IP インスタンスによって所有されていたすべてのシステム リソースが解放されます。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレスの削除に成功しました。
- **NX_SOCKETS_BOUND** (0x28) この IP インスタンスには依然として UDP ソケットまたは TCP ソケットがバインドされています。 IP インスタンスを削除する前に、すべてのソケットをバインド解除し、削除する必要があります。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
/* Delete a previously created IP instance. */
status = nx_ip_delete(&ip_0);

/* If status is NX_SUCCESS, the IP instance has been deleted. */
```

### <a name="see-also"></a>参照 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_direct_command"></a>nx_ip_driver_direct_command
ネットワーク ドライバーにコマンドを発行します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_driver_direct_command
    (NX_IP *ip_ptr,
    UINT command,
    ULONG *return_value_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、***nx_ip_create*** の呼び出し時に指定したアプリケーションのプライマリ ネットワーク インターフェイス ドライバーに対する直接インターフェイスが提供されます。 アプリケーション固有のコマンドは、その数値が NX_LINK_USER_COMMAND 以上である場合に使用できます。

> [!IMPORTANT]  
> *セカンダリ デバイスに対してコマンドを発行するには、サービス **nx_ip_driver_interface_direct_command** を使用します*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **command** 数値コマンド コード。 標準コマンドは次のように定義されています。
    - NX_LINK_GET_STATUS (10)
    - NX_LINK_GET_SPEED (11)
    - NX_LINK_GET_DUPLEX_TYPE (12)
    - NX_LINK_GET_ERROR_COUNT (13)
    - NX_LINK_GET_RX_COUNT (14)
    - NX_LINK_GET_TX_COUNT (15)
    - NX_LINK_GET_ALLOC_ERRORS (16)
    - NX_LINK_USER_COMMAND (50)
- **return_value_ptr** 呼び出し元の戻り変数を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ネットワーク ドライバーのダイレクト コマンドに成功しました。
- **NX_UNHANDLED_COMMAND** (0x44) ネットワーク ドライバー コマンドが処理または実装されていません。
- **NX_PTR_ERROR** (0x07) IP または戻り値ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイス インデックスが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */
status = nx_ip_driver_direct_command(&ip_0, NX_LINK_GET_STATUS,
                                     &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_driver_interface_direct_command"></a>nx_ip_driver_interface_direct_command
ネットワーク ドライバーにコマンドを発行します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_driver_interface_direct_command(
    NX_IP *ip_ptr,
    UINT command,
    UINT interface_index,
    ULONG *return_value_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、IP インスタンス内のアプリケーションのネットワーク デバイス ドライバーに対する直接コマンドが提供されます。 アプリケーション固有のコマンドは、その数値が *NX_LINK_USER_COMMAND* 以上である場合に使用できます。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **command** 数値コマンド コード。 標準コマンドは次のように定義されています。
    - NX_LINK_GET_STATUS (10)
    - NX_LINK_GET_SPEED (11)
    - NX_LINK_GET_DUPLEX_TYPE (12)
    - NX_LINK_GET_ERROR_COUNT (13)
    - NX_LINK_GET_RX_COUNT (14)
    - NX_LINK_GET_TX_COUNT (15)
    - NX_LINK_GET_ALLOC_ERRORS (16)
    - NX_LINK_USER_COMMAND (50)
- **interface_index** コマンドの送信先となるネットワーク インターフェイスのインデックス。
- **return_value_ptr** 呼び出し元の戻り変数を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ネットワーク ドライバーのダイレクト コマンドに成功しました。
- **NX_UNHANDLED_COMMAND** (0x44) ネットワーク ドライバー コマンドが処理または実装されていません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイス インデックスが無効です
- **NX_PTR_ERROR** (0x07) IP または戻り値ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Make a direct call to the application-specific network driver
   for the previously created IP instance. For this example, the
   network driver is interrogated for the link status. */

/* Set the interface index to the primary device. */
UINT interface_index = 0;

status = nx_ip_driver_interface_direct_command(&ip_0,
                                               NX_LINK_GET_STATUS,
                                               interface_index,
                                               &link_status);

/* If status is NX_SUCCESS, the link_status variable contains a
   NX_TRUE or NX_FALSE value representing the status of the
   physical link. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_disable"></a>nx_ip_forwarding_disable  
IP パケット転送を無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_forwarding_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、NetX Duo IP コンポーネント内の IP パケットの転送を無効にします。 IP タスクを作成すると、このサービスは自動的に無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) IP 転送の無効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能  

いいえ

### <a name="example"></a>例

```c
/* Disable IP forwarding on this IP instance. */
status = nx_ip_forwarding_disable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been disabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>参照  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_forwarding_enable"></a>nx_ip_forwarding_enable
IP パケット転送を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_forwarding_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、NetX Duo IP コンポーネント内の IP パケットの転送を有効にします。 IP タスクを作成すると、このサービスは自動的に無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP 転送の有効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable IP forwarding on this IP instance. */
status = nx_ip_forwarding_enable(&ip_0);

/* If status is NX_SUCCESS, IP forwarding has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>参照 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_disable"></a>nx_ip_fragment_disable
IP パケットのフラグメント化を無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_fragment_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、IPv4 および IPv6 パケットのフラグメント化と再アセンブル機能を無効にします。 再アセンブルされるのを待機しているパケットは、このサービスによって解放されます。 IP タスクを作成すると、このサービスは自動的に無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP フラグメントの無効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IP のフラグメント化はこの IP インスタンスで有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Disable IP fragmenting on this IP instance. */
status = nx_ip_fragment_disable(&ip_0);

/* If status is NX_SUCCESS, disables IP fragmenting on the
   previously created IP instance. */
```

### <a name="see-also"></a>参照  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_fragment_enable"></a>nx_ip_fragment_enable
IP パケットのフラグメント化を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_fragment_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、IPv4 および IPv6 パケットのフラグメント化と再アセンブル機能を有効にします。 IP タスクを作成すると、このサービスは自動的に無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP フラグメントの有効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IP のフラグメント化機能が NetX Duo にコンパイルされていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable IP fragmenting on this IP instance. */
status = nx_ip_fragment_enable(&ip_0);

/* If status is NX_SUCCESS, IP fragmenting has been enabled on the
   previously created IP instance. */
```
### <a name="see-also"></a>参照  

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_gateway_address_clear"></a>nx_ip_gateway_address_clear
IPv4 ゲートウェイ アドレスをクリアします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_gateway_address_clear(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、インスタンスで構成された IPv4 ゲートウェイ アドレスをクリアします。 IPv6 既定ルーターを IP インスタンスからクリアするには、アプリケーションで ***nxd_ipv6_default_router_delete*** サービスを使用する必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP ゲートウェイ アドレスが正常にクリアされました。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Clear the gateway address of IP instance. */
status = nx_ip_gateway_address_clear(&ip_0);

/* If status == NX_SUCCESS, the gateway address was successfully
   cleared from the IP instance. */
```
### <a name="see-also"></a>参照

-nx_ip_gateway_address_get -nx_ip_gateway_address_set -nx_ip_info_get -nx_ip_static_route_add -nx_ip_static_route_delete -nxd_ipv6_default_router_add -nxd_ipv6_default_router_delete -nxd_ipv6_default_router_entry_get -nxd_ipv6_default_router_get -nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_get"></a>nx_ip_gateway_address_get
IPv4 ゲートウェイ アドレスを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_gateway_address_get(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>説明

このサービスでは、IP インスタンスで構成された IPv4 ゲートウェイ アドレスを取得します。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **ip_address** ゲートウェイ アドレスが格納されているメモリへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 取得に成功しました。 
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターまたは IP アドレスのポインターが無効です。
- **NX_NOT_FOUND** (0x4E) ゲートウェイ アドレスが見つかりません。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
ULONG ip_address;

/* Get the gateway address of IP instance. */
status = nx_ip_gateway_address_get(&ip_0, &ip_address);

/* If status == NX_SUCCESS, the gateway address was successfully
   got. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_gateway_address_set"></a>nx_ip_gateway_address_set
ゲートウェイ IP アドレスを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_gateway_address_set(
    NX_IP *ip_ptr, 
    ULONG ip_address);
```
### <a name="description"></a>説明

このサービスでは、IPv4 ゲートウェイの IP アドレスを設定します。 ネットワーク外に向かうすべてのトラフィックは、送信のためにこのゲートウェイにルーティングされます。 このゲートウェイは、いずれかのネットワーク インターフェイスを介して直接アクセスできる必要があります。 IPv6 ゲートウェイ アドレスを構成するには、サービス ***nxd_ipv6_default_router_add*** を使用します。 

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** ゲートウェイの IP アドレス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ゲートウェイ IP アドレスの設定に成功しました。
- **NX_PTR_ERROR** (0x07) IP インスタンス ポインターが無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Setup the Gateway address for previously created IP
   Instance ip_0. */
status = nx_ip_gateway_address_set(&ip_0, IP_ADDRESS(1,2,3,99);

/* If status is NX_SUCCESS, all out-of-network send requests are
   routed to 1.2.3.99. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_info_get"></a>nx_ip_info_get
IP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_info_get(
    NX_IP *ip_ptr,
    ULONG *ip_total_packets_sent,
    ULONG *ip_total_bytes_sent,
    ULONG *ip_total_packets_received,
    ULONG *ip_total_bytes_received,
    ULONG *ip_invalid_packets,
    ULONG *ip_receive_packets_dropped,
    ULONG *ip_receive_checksum_errors,
    ULONG *ip_send_packets_dropped,
    ULONG *ip_total_fragments_sent,
    ULONG *ip_total_fragments_received);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの IP アクティビティに関する情報を取得します。

> [!NOTE]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_total_packets_sent** 送信された IP パケットの合計数の宛先を指すポインター。
- **ip_total_bytes_sent** 送信された合計バイト数の宛先を指すポインター。
- **ip_total_packets_received** IP 受信パケットの合計数の宛先を指すポインター。
- **ip_total_bytes_received** 受信した IP バイトの合計数の宛先を指すポインター。
- **ip_invalid_packets** 無効な IP パケットの合計数の宛先を指すポインター。
- **ip_receive_packets_dropped** 破棄された受信パケットの合計数の宛先を指すポインター。
- **ip_receive_checksum_errors** 受信パケットのチェックサム エラーの合計数の宛先を指すポインター。
- **ip_send_packets_dropped** 破棄された送信パケットの合計数の宛先を指すポインター。
- **ip_total_fragments_sent** 送信されたフラグメントの合計数の宛先を指すポインター。
- **ip_total_fragments_received** 受信したフラグメントの合計数の宛先を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP 情報の取得に成功しました。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve IP information from previously created IP
   Instance 0. */
status = nx_ip_info_get(&ip_0,
                        &ip_total_packets_sent,
                        &ip_total_bytes_sent,
                        &ip_total_packets_received,
                        &ip_total_bytes_received,
                        &ip_invalid_packets,
                        &ip_receive_packets_dropped,
                        &ip_receive_checksum_errors,
                        &ip_send_packets_dropped,
                        &ip_total_fragments_sent,
                        &ip_total_fragments_received);

/* If status is NX_SUCCESS, IP information was retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_interface_address_get"></a>nx_ip_interface_address_get
インターフェイスの IP アドレスを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_address_get (
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *ip_address,
    ULONG *network_mask);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイスの IPv4 アドレスを取得します。 IPv6 アドレスを取得するには、アプリケーションでサービス ***nxd_ipv6_address_get*** を使用する必要があります。

> [!CAUTION]  
> *指定されたデバイスがプライマリ デバイスでない場合は、そのデバイスを先に IP インスタンスに接続しておく必要があります*。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_index** インターフェイス インデックス。IP インスタンスに接続されているネットワーク インターフェイスのインデックスと同じ値です。
- **ip_address** デバイス インターフェイスの IP アドレスの宛先を指すポインター。
- **network_mask** デバイス インターフェイスのネットワーク マスクの宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレスの取得に成功しました。
- **NX_INVALID_INTERFACE** (0x4C) 指定されたネットワーク インターフェイスが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define INTERFACE_INDEX 1

/* Get device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_get(ip_ptr,INTERFACE_INDEX,
                                     &ip_address,
                                     &network_mask);

/* If status is NX_SUCCESS the interface address was successfully
   retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_mapping_configure"></a>nx_ip_interface_address_mapping_configure
アドレス マッピングが必要かどうかを構成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_address_mapping_configure(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT mapping_needed);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイスに IP アドレスから MAC アドレスへのマッピングが必要かどうかを構成します。 このサービスは、通常、インターフェイス デバイス ドライバーから呼び出され、基になるインターフェイスに IP アドレスから第 2 層 (MAC) アドレスへのマッピングが必要かどうかを IP スタックに通知します。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **mapping_needed** NX_TRUE -- アドレス マッピングが必要 NX_FALSE -- アドレス マッピングは不要。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 構成に成功しました。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
UCHAR mapping_needed = NX_TRUE;

/* Configure address mapping needed specified interface. */
status = nx_ip_interface_address_mapping_configure(&ip_0,
                                             PRIMARY_INTERFACE,
                                             mapping_needed);

/* If status == NX_SUCCESS, the address mapping needed was
   successfully configured. */
```

### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_address_set"></a>nx_ip_interface_address_set
インターフェイスの IP アドレスとネットワーク マスクを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG ip_address,
    ULONG network_mask);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インターフェイスの IPv4 アドレスとネットワーク マスクを設定します。 IPv6 インターフェイス アドレスを構成するには、アプリケーションでサービス ***nxd_ipv6_address_set*** を使用する必要があります。 
 
> [!WARNING]  
> *指定されたインターフェイスは、先に IP インスタンスに接続されている必要があります*。 

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_index** NetX Duo インスタンスに接続されているインターフェイスのインデックス。
- **ip_address** 新しいネットワーク インターフェイスの IP アドレス。
- **network_mask** 新しいインターフェイスのネットワーク マスク。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP アドレスの設定に成功しました。
- **NX_INVALID_INTERFACE** (0x4C) 指定されたネットワーク インターフェイスが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define INTERFACE_INDEX 1

/* Set device IP address and network mask for the specified
   interface index 1 in IP instance list of interfaces). */
status = nx_ip_interface_address_set(ip_ptr, INTERFACE_INDEX,
                                     ip_address,
                                     network_mask);

/* If status is NX_SUCCESS the interface IP address and mask was
   successfully set. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_attach"></a>nx_ip_interface_attach
ネットワーク インターフェイスを IP インスタンスに接続します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_attach(
    NX_IP *ip_ptr, 
    CHAR *interface_name,
    ULONG ip_address,
    ULONG network_mask,
    VOID(*ip_link_driver)(struct NX_IP_DRIVER_STRUCT *));
```
### <a name="description"></a>説明

このサービスを使用すると、物理ネットワーク インターフェイスを IP インターフェイスに追加できます。 この IP インスタンスはプライマリ インターフェイスを使用して作成されるので、追加の各インターフェイスはプライマリ インターフェイスのセカンダリになります。 この IP インスタンスに接続されているネットワーク インターフェイスの総数 (プライマリ インターフェイスを含む) は、**NX_MAX_PHYSICAL_INTERFACES** を超えることはできません。

IP スレッドがまだ実行されていない場合は、すべての物理インターフェイスを初期化する IP スレッド スタートアップ プロセスの一部として、セカンダリ インターフェイスが初期化されます。

IP スレッドがまだ実行中でない場合は、このセカンダリ インターフェイスが ***nx_ip_interface_attach*** サービスの一部として初期化されます。

> [!WARNING]  
> *ip_ptr は、有効な NetX Duo IP 構造体をポイントする必要があります。**NX_MAX_PHYSICAL_INTERFACES** は、その IP インスタンスのネットワーク インターフェイスの数に対して構成する必要があります。既定値は 1 です*。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_name** インターフェイス名の文字列を指すポインター。
- **ip_address** デバイスの IP アドレス (ホストのバイト順)。
- **network_mask** デバイスのネットワーク マスク (ホストのバイト順)。
- **ip_link_driver** そのインターフェイスのイーサネット ドライバー。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 静的ルーティング テーブルにエントリが追加されました。
- **NX_NO_MORE_ENTRIES** (0x17) インターフェイスの最大数。 NX_MAX_PHYSICAL_INTERFACES を超えています。 IPv6 が有効になっている場合、このエラーは、IPv6 マルチキャスト操作を処理するのに十分なリソースがドライバーにないことを示しているおそれもあります。
- **NX_DUPLICATED_ENTRY** (0x52) 指定された IP アドレスは、この IP インスタンスで既に使用されています。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレス入力が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Attach secondary device for device IP address 192.168.1.68 with
   the specified Ethernet driver. */
status = nx_ip_interface_attach(ip_ptr, “secondary_port”,
                                IP_ADDRESS(192,168,1,68),
                                0xFFFFFF00UL,
                                nx_etherDriver);

/* If status is NX_SUCCESS the interface was successfully added to
   the IP instance interface table. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_get"></a>nx_ip_interface_capability_get
インターフェイスのハードウェア機能を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_capability_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *interface_capability_flag);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイスから機能フラグを取得します。 このサービスを使用するには、オプション ***NX_ENABLE_INTERFACE_CAPABILITY*** を有効にして NetX Duo ライブラリを構築する必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **interface_capability_flag** 機能フラグのメモリ領域へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) インターフェイスの機能情報が正常に取得されました。
- **NX_NOT_SUPPORTED** (0x4B) インターフェイス機能の機能は、このビルドではサポートされていません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効であるか、機能フラグのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
ULONG       capability_flag;

/* Get the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_get(&ip_0,
                                        PRIMARY_INTERFACE,
                                        &capability_flag);

/* If status == NX_SUCCESS, the capability flag from the primary
   interface was successfully retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_capability_set"></a>nx_ip_interface_capability_set
ハードウェア機能フラグを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_capability_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG interface_capability_flag);
```                           
### <a name="description"></a>説明

このサービスは、指定されたネットワーク インターフェイスの機能フラグを構成するために、ネットワーク デバイス ドライバーによって使用されます。 このサービスを使用するには、オプション ***NX_ENABLE_INTERFACE_CAPABILITY*** を定義して NetX Duo ライブラリをコンパイルする必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **interface_capability_flag** 出力の機能フラグ。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) インターフェイスのハードウェア機能フラグが正常に設定されました。
- **NX_NOT_SUPPORTED** (0x4B) インターフェイス機能の機能は、このビルドではサポートされていません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。 
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。 
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
ULONG capability_flag = \
                 NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM |\
                 NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM;
UINT device_index = 0;

/* Set the hardware capability flag of specified interface. */
status = nx_ip_interface_capability_set(&ip_0,
                                        PRIMARY_INTERFACE,
                                        capability_flag);

/* If status == NX_SUCCESS, the hardware capability flag was
   successfully set. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_detach"></a>nx_ip_interface_detach
指定されたインターフェイスを IP インスタンスからデタッチします。

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_address_set(
    NX_IP *ip_ptr, 
    UINT index);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インターフェイスを IP インスタンスからデタッチします。 インターフェイスがデタッチされると、接続されていたすべての TCP ソケットが閉じられ、このインターフェイスの ND キャッシュと ARP エントリがそれぞれのテーブルから削除されます。 このインターフェイスの IGMP メンバーシップは削除されます。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **index** 削除されるインターフェイスのインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 物理インターフェイスが正常に削除されました。
- **NX_INVALID_INTERFACE** (0x4C) 指定されたネットワーク インターフェイスが無効です。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define INTERFACE_INDEX 1

/* Detach interface 1. */
status = nx_ip_interface_detach(&IP_0, INTERFACE_INDEX);

/* If status is NX_SUCCESS the interface is successfully detached
   from the IP instance. */
```

### <a name="see-also"></a>参照  

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_info_get"></a>nx_ip_interface_info_get
ネットワーク インターフェイス パラメーターを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_info_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    CHAR **interface_name,
    ULONG *ip_address,
    ULONG *network_mask,
    ULONG *mtu_size,
    ULONG *physical_address_msw,
    ULONG *physical_address_lsw);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したネットワーク インターフェイスのネットワーク パラメーターに関する情報が取得されます。 すべてのデータは、ホストのバイト順に取得されます。 

> [!WARNING]  
> *ip_ptr は、有効な NetX Duo IP 構造体をポイントする必要があります。指定されたインターフェイスがプライマリ インターフェイスでない場合は、事前に IP インスタンスに接続しておく必要があります*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_index** ネットワーク インターフェイスを指定するインデックス。
- **interface_name** ネットワーク インターフェイスの名前を保持するバッファーを指すポインター。
- **ip_address** インターフェイスの IP アドレスの宛先を指すポインター。
- **network_mask** ネットワーク マスクの宛先を指すポインター。
- **mtu_size** このインターフェイスの最大転送単位の宛先を指すポインター。
- **physical_address_msw** デバイスの MAC アドレスの上位 16 ビットの宛先を指すポインター。
- **physical_address_lsw** デバイスの MAC アドレスの下位 32 ビットの宛先を指すポインター。

### <a name="return-values"></a>戻り値   

- **NX_SUCCESS** (0x00) インターフェイス情報が取得されました。
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です。
- **NX_INVALID_INTERFACE** (0x4C) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve interface parameters for the specified interface (index
   1 in IP instance list of interfaces). */
#define INTERFACE_INDEX 1
status = nx_ip_interface_info_get(ip_ptr, INTERFACE_INDEX,
                                  &name_ptr, &ip_address,
                                  &network_mask,
                                  &mtu_size,
                                  &physical_address_msw,
                                  &physical_address_lsw);

/* If status is NX_SUCCESS the interface information is
   successfully retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_mtu_set"></a>nx_ip_interface_mtu_set
ネットワーク インターフェイスの MTU 値を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_mtu_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG mtu_size);
```
### <a name="description"></a>説明

このサービスは、指定されたネットワーク インターフェイスの IP MTU 値を構成するために、デバイス ドライバーによって使用されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **mtu_size** IP MTU サイズ。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) MTU 値が正常に設定されました。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
ULONG       mtu_size = 1500;

/* Set the MTU size of specified interface. */
status = nx_ip_interface_mtu_set(&ip_0,
                                 PRIMARY_INTERFACE, mtu_size);

/* If status == NX_SUCCESS, the MTU size was successfully set. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_get"></a>nx_ip_interface_physical_address_get
ネットワーク デバイスの物理アドレスを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_physical_address_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG *physical_msw,
    ULONG *physical_lsw);
```
### <a name="description"></a>説明

このサービスでは、IP インスタンスからネットワーク インターフェイスの物理アドレスを取得します。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **physical_msw** デバイスの MAC アドレスの上位 16 ビットの宛先へのポインター。
- **physical_lsw** デバイスの MAC アドレスの下位 32 ビットの宛先へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 取得に成功しました。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターまたは物理アドレスのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
ULONG   physical_msw;
ULONG   physical_lsw;

/* Get the physical address of specified interface. */
status = nx_ip_interface_physical_address_get(&ip_0,
                                              PRIMARY_INTERFACE,
                                              &physical_msw,
                                              &physical_lsw);

/* If status == NX_SUCCESS, the physical address was successfully
   retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_physical_address_set"></a>nx_ip_interface_physical_address_set
指定されたネットワーク インターフェイスの物理アドレスを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_physical_address_set(
    NX_IP *ip_ptr,
    UINT interface_index,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT update_driver);
```
### <a name="description"></a>説明

このサービスは、指定されたネットワーク インターフェイスの MAC アドレスの物理アドレスを構成するために、アプリケーションまたはデバイス ドライバーによって使用されます。 新しい MAC アドレスは、インターフェイス構造体の制御ブロックに適用されます。 ***update_driver*** フラグが設定されている場合は、そのデバイス ドライバーでイーサネット コントローラーにプログラムされた MAC アドレスを更新できるように、ドライバー レベルのコマンドが発行されます。

一般的な状況では、このサービスは初期化フェーズ中にインターフェイス デバイス ドライバーから呼び出され、IP スタックにその MAC アドレスを通知します。 この場合は、***update_driver*** フラグを設定しないでください。

このルーチンは、実行時にインターフェイスの MAC アドレスを再構成するために、ユーザー アプリケーションから呼び出すこともできます。 このユース ケースでは、新しい MAC アドレスをデバイス ドライバーに適用できるようにするために、***update_driver*** フラグを設定する必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **physical_msw** デバイスの MAC アドレスの上位 16 ビットの宛先へのポインター。
- **physical_lsw** デバイスの MAC アドレスの下位 32 ビットの宛先へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 設定に成功しました。
- **NX_UNHANDLED_COMMAND** (0x4B) コマンドがドライバーによって認識されません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
ULONG       physical_msw = 0x00CF;
ULONG       physical_lsw = 0x01020304;

/* Set the physical address of specified device. */
status = nx_ip_interface_physical_address_set(&ip_0,
                                              PRIMARY_INTERFACE,
                                              physical_msw,
                                              physical_lsw,
                                              NX_TRUE);

/* If status == NX_SUCCESS, the physical address was successfully
   set. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_status_check
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_interface_status_check"></a>nx_ip_interface_status_check
IP インスタンスの状態を確認します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_interface_status_check(
    NX_IP *ip_ptr,
    UINT interface_index
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成された IP インスタンスのネットワーク インターフェイスの指定した状態を確認し、必要に応じて待機します。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_index** インターフェイスのインデックス番号。needed_status 要求された IP 状態。ビットマップ形式で次のように定義されます。
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **actual_status** 設定された実際のビットの宛先へのポインター。 wait_option 要求されたステータス ビットが使用できない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
  - **NX_NO_WAIT** (0x00000000)
  - **timeout value** (0x00000001 から 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IP 状態の確認に成功しました。
- **NX_NOT_SUCCESSFUL** (0x43) 状態要求が、指定されたタイムアウト時間内に満たされませんでした。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効であるか、無効になったか、または実際の状態ポインターが無効です。
- **NX_OPTION_ERROR** (0x0a) 必要な状態オプションが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_INTERFACE** (0x4C) Interface_index が範囲外です。 または、インターフェイスが正しくありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_interface_status_check(&ip_0, 1, NX_IP_LINK_ENABLED,
                                      &actual_status, 10);

/* If status is NX_SUCCESS, the secondary link for the specified IP
   instance is up. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_link_status_change_notify_set

## <a name="nx_ip_link_status_change_notify_set"></a>nx_ip_link_status_change_notify_set
リンク状態の変更通知コールバック関数を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_link_status_change_notify_set(
    NX_IP *ip_ptr,
    VOID(*link_status_change_notify)(NX_IP *ip_ptr, UINT interface_index, UINT link_up));
```
### <a name="description"></a>説明

このサービスを使用すると、リンク状態の変更通知コールバック関数を構成できます。 ユーザーが指定した *link_status_change_notify* ルーチンは、プライマリかセカンダリのいずれかのインターフェイスの状態が変更されたとき (IP アドレスの変更など) に呼び出されます。*link_status_change_notify* が null 値の場合、リンク状態の変更通知コールバック関数は無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロック ポインター
- **link_status_change_notify** 物理インターフェイスの変更時に呼び出されるユーザー指定のコールバック関数。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 設定に成功しました
- **NX_PTR_ERROR** (0x07) IP 制御ブロック ポインターまたは新しい物理アドレス ポインターが無効です
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Configure a callback function to be used when the physical
   interface status is changed. */
status = nx_ip_link_status_change_notify_set(&ip_0,
                                             my_change_cb);

/* If status == NX_SUCCESS, the link status change notify function
   is set. */
```
### <a name="see-also"></a>参照

- nx_ip_interface_address_get
- nx_ip_interface_address_mapping_configure
- nx_ip_interface_address_set
- nx_ip_interface_attach
- nx_ip_interface_capability_get
- nx_ip_interface_capability_set
- nx_ip_interface_detach
- nx_ip_interface_info_get
- nx_ip_interface_mtu_set
- nx_ip_interface_physical_address_get
- nx_ip_interface_physical_address_set
- nx_ip_interface_status_check

## <a name="nx_ip_max_payload_size_find"></a>nx_ip_max_payload_size_find
最大パケット データ ペイロードを計算します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_max_payload_size_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *dest_address,
    UINT if_index,
    UINT src_port,
    UINT dest_port,
    ULONG protocol,
    ULONG *start_offset_ptr,
    ULONG *payload_length_ptr);
```
### <a name="description"></a>説明

このサービスでは、IP のフラグメント化なしで宛先に到達できるアプリケーション ペイロードの最大サイズを調べます。たとえば、ペイロードが次と同じかそれを下回る場合です: ローカル インターフェイスの MTU サイズ。 (または IPv6 パス MTU 検出で取得したパス MTU 値)。 IP ヘッダーと上位のアプリケーション ヘッダーのサイズ (TCP または UDP) は、合計ペイロードから差し引かれます。 NetX Duo IPsec セキュリティ ポリシーがこのエンドポイントに適用される場合、IPsec ヘッダー (ESP/AH) および関連するオーバーヘッド (初期ベクターなど) も、MTU から差し引かれます。 このサービスは、IPv4 と IPv6 の両方のパケットに適用されます。

パラメーター *if_index* は、パケットの送信に使用するインターフェイスを指定します。 マルチホーム システムの場合、宛先がブロードキャスト (IPv4 のみ)、マルチキャスト、または IPv6 リンク ローカル アドレスである場合、呼び出し元で *if_index* パラメーターを指定する必要があります。

このサービスは、次の 2 つの値を呼び出し元に返します。

1) start_offset_ptr: これは、TCP/UDP/IP/IPsec ヘッダーの後の場所です。
2) payload_length_ptr: MTU を超えずにアプリケーションで転送できるデータ量です。

これに相当する NetX サービスはありません。

### <a name="restrictions"></a>制限 

IP インスタンスを先に作成しておく必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスへのポインター。
- **dest_address** パケットの宛先アドレスへのポインター。
- **if_index** 使用するインターフェイスのインデックスを示します。
- **src_port** 発信元のポート番号。
- **dest_port** 宛先のポート番号。
- **protocol** 使用する上位層プロトコル。
- **start_offset_ptr** 最大パケット ペイロードのデータの先頭へのポインター。
- **payload_length_ptr** ヘッダーを除くペイロード サイズへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ペイロードが正常に計算されました。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが無効であるか、インターフェイスが正しくありません。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効であるか、宛先アドレスが無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定されたアドレスが無効です。 
- **NX_NOT_SUPPORTED** (0x4B) プロトコルが無効です (UDP または TCP ではありません)。
- **NX_CALLER_ERROR** (0x11) サービスが、システムの初期化またはスレッド コンテキストから呼び出されていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* The following example determines the maximum payload for UDP
   packet to remote host. */
#define PRIMARY_INTERFACE 0
status = nx_ip_max_payload_size_find(&ip_0,
                                     &dest_ipv6_address,
                                     PRIMARY_INTERFACE,
                                     source_port,
                                     dest_port, NX_PROTOCOL_UDP,
                                     &start_offset,
                                     &payload_length);

/* A return value of NX_SUCCESS indicates the packet payload
   payload_length starting at the offset start_offset is
   successfully computed. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ip_raw_packet_disable"></a>nx_ip_raw_packet_disable
生パケットの送受信を無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_packet_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、この IP インスタンスの生 IP パケットの送信と受信が無効になります。 生パケットのサービスが以前に有効になっていて、生パケットが受信キューに存在する場合、受信済みの生パケットはすべてこのサービスによって解放されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) IP 生パケットの無効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Disable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_disable(&ip_0);
/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been disabled for the previously created IP instance. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_enable"></a>nx_ip_raw_packet_enable
生パケットの処理を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_packet_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスは、この IP インスタンスの生 IP パケットの送信と受信を有効にします。 着信 TCP、UDP、ICMP、IGMP パケットは引き続き NetX Duo によって処理されます。 上位層プロトコルの種類が不明なパケットは、生パケット受信ルーチンによって処理されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) IP 生パケットの有効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable raw packet sending/receiving for this IP instance. */
status = nx_ip_raw_packet_enable(&ip_0);

/* If status is NX_SUCCESS, raw IP packet sending/receiving has
   been enabled for the previously created IP instance. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_filter_set"></a>nx_ip_raw_packet_filter_set
生 IP パケット フィルターを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_packet_filter_set(
    NX_IP *ip_ptr,
    UINT (*raw_packet_filter)(NX_IP *, ULONG, NX_PACKET *));
```
### <a name="description"></a>説明

このサービスは、IP 生パケット フィルターを構成します。 ユーザー アプリケーションによって実装される生パケット フィルター関数を使用すると、ユーザーが指定した条件に基づいて、アプリケーションで生パケットを受信できます。 NetX Duo BSD ラッパー レイヤーでは、この生パケット フィルター機能を使用して、BSD 層の raw ソケットを処理することにご注意ください。 このサービスを使用するには、オプション ***NX_ENABLE_IP_RAW_PACKET_FILTER*** を定義して NetX Duo ライブラリを構築する必要があります。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** IP 制御ブロックのポインター。
- **raw_packet_filter** 生パケット フィルターの関数ポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 生パケット フィルター ルーチンが正常に設定されました。
- **NX_NOT_SUPPORT** (0x4B) 生パケット サポートは使用できません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
UINT raw_packet_filter(NX_IP *ip_ptr, ULONG protocol,
                       NX_PACKET *packet_ptr)
{

/* Simply filter protocol. */
if(protocol == NX_IP_RAW)
   return NX_SUCCESS;
else
   return NX_NOT_SUCCESSFUL;
}

void raw_packet_thread_entry(ULONG id)
{

/* Set the raw packet filter of IP instance. */
status = nx_ip_raw_packet_filter_set(&ip_0,
                                     raw_packet_filter);

/* If status == NX_SUCCESS, the raw packet filter of IP instance
   was successfully set. */
}
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_receive"></a>nx_ip_raw_packet_receive
生 IP パケットを受信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_packet_receive(
    NX_IP *ip_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンスから生 IP パケットを受信できます。 生パケット受信キューに IP パケットがある場合、最初の (最も古い) パケットが呼び出し元に返されます。 それ以外の場合、使用可能なパケットがない場合は、待機オプションの指定に従って呼び出し元が中断される場合があります。

> [!CAUTION]   
> *NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **packet_ptr** 受信した生 IP パケットを格納するポインターへのポインター。
- **wait_option** パケットが使用できない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
   - **NX_NO_WAIT** (0x00000000)
   - **NX_WAIT_FOREVER** (0xFFFFFFFF)
   - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP 生パケットの受信に成功しました。
- **NX_NO_PACKET** (0x01) 使用可能なパケットがありませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_PTR_ERROR** (0x07) IP またはパケットの戻りポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Receive a raw IP packet for this IP instance, wait for a maximum
   of 4 timer ticks. */
status = nx_ip_raw_packet_receive(&ip_0, &packet_ptr, 4);

/* If status is NX_SUCCESS, the raw IP packet pointer is in the
   variable packet_ptr. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_send"></a>nx_ip_raw_packet_send
生 IP パケットを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_packet_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    ULONG type_of_service);
```
### <a name="description"></a>説明

このサービスでは、宛先 IP アドレスに生の IPv4 パケットを送信します。 このルーチンはすぐに戻るため、IP パケットが実際に送信されたかどうかはわからないことにご注意ください。 送信が完了したときに、ネットワーク ドライバーがパケットを解放する役割を果たします。

マルチホーム システムの場合、NetX Duo はこの宛先 IP アドレスを使用して適切なネットワーク インターフェイスを検索し、発信元アドレスとしてこのインターフェイスの IP アドレスを使用します。 宛先 IP アドレスがブロードキャストまたはマルチキャストの場合は、最初の有効なインターフェイスが使用されます。 この場合、アプリケーションでは ***nx_ip_raw_packet_source_send*** が使用されます。

生の IPv6 パケットを送信するには、アプリケーションでサービス ***nxd_ip_raw_packet_send** _ または _ *_nxd_ip_raw_packet_source_send_* を使用する必要があります。*

> [!WARNING]  
> *エラーが返されない限り、この呼び出しの後にアプリケーションでパケットを解放することはできません。これを行うと、送信後にネットワーク ドライバーでパケットが解放されるため、予期しない結果が発生します*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **packet_ptr** 送信する生 IP パケットを指すポインター。
- **destination_ip** 宛先 IP アドレス。特定のホスト IP アドレス、ネットワーク ブロードキャスト、内部ループバック、またはマルチキャスト アドレスを指定できます。
- **type_of_service** 送信のためのサービスの種類を定義します。有効な値は次のとおりです。
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IP 生パケットの送信開始に成功しました。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_NOT_ENABLED** (0x14) 生 IP 機能が有効になっていません。
- **NX_OPTION_ERROR** (0x0A) サービスの種類が無効です。
- **NX_UNDERFLOW** (0x02) パケットの先頭に IP ヘッダーを付加するのに十分な空き領域がありません。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_PTR_ERROR** (0x07) IP またはパケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Send a raw IP packet to IP address 1.2.3.5. */
status = nx_ip_raw_packet_send(&ip_0, packet_ptr,
                               IP_ADDRESS(1,2,3,5),
                               NX_IP_NORMAL);

/* If status is NX_SUCCESS, the raw IP packet pointed to by
   packet_ptr has been sent. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_packet_source_send"></a>nx_ip_raw_packet_source_send
指定されたネットワーク インターフェイスを経由して生 IP パケットを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    ULONG destination_ip,
    UINT address_index,
    ULONG type_of_service);
```
### <a name="description"></a>説明

このサービスでは、指定されたローカル IPv4 アドレスを発信元アドレスとして使用し、関連付けられているネットワーク インターフェイスを経由して、宛先 IP アドレスに生 IP パケットを送信します。 このルーチンはすぐに戻るため、IP パケットが実際に送信されたかどうかはわからないことにご注意ください。 このネットワーク ドライバーは、送信が完了したときにパケットを開放する役割を果たします。 このサービスは、パケットが実際に送信されたかどうかを知る方法がないという点で、他のサービスとは異なります。 パケットはインターネット上で失われているおそれがあります。

> [!CAUTION]  
> *生 IP 処理を有効にする必要があることにご注意ください*。

> [!WARNING]  
> *このサービスは、指定された物理インターフェイスから生の IPv4 パケットを送信することをアプリケーションに許可する点を除けば、**nx_ip_raw_packet_send** と似ています*。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** 以前に作成された IP タスクを指すポインター。
- **packet_ptr** 送信するパケットを指すポインター。
- **destination_ip** パケットを送信する IP アドレス。
- **address_index** パケットを送信するインターフェイスのアドレスのインデックス。
- **type_of_service** パケットのサービスの種類。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) パケットが正常に転送されました。
- **NX_IP_ADDRESS_ERROR** (0x21) 使用可能な適切な送信インターフェイスがありません。
- **NX_NOT_ENABLED** (0x14) 生 IP パケット処理が有効になっていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です。
- **NX_OPTION_ERROR** (0x0A) 指定されたサービスの種類が無効です。
- **NX_OVERFLOW** (0x03) パケットのプリペンド ポインターが無効です。
- **NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。
- **NX_INVALID_INTERFACE** (0x4C) 指定されたインターフェイス インデックスが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define ADDRESS_IDNEX 1

/* Send packet out on interface 1 with normal type of service. */
status = nx_ip_raw_packet_source_send(ip_ptr, packet_ptr,
                                      destination_ip,
                                      ADDRESS_INDEX,
                                      NX_IP_NORMAL);

/* If status is NX_SUCCESS the packet was successfully
   transmitted. */
```

### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_raw_receive_queue_max_set"></a>nx_ip_raw_receive_queue_max_set
生の受信キューの最大サイズを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_raw_receive_queue_max_set(
    NX_IP *ip_ptr, 
    ULONG queue_max);
```
### <a name="description"></a>説明

このサービスは、IP 生パケット受信キューの最大深度を構成します。 この IP 生パケット受信キューは IPv4 パケットと IPv6 パケットの両方で共有されることにご注意ください。 生パケット受信キューがユーザーが構成した最大深度に達すると、新しく受信した生パケットは削除されます。 既定の IP 生パケット受信キューの深度は 20 です。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **queue_max** キュー サイズの新しい値。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) 生受信キューの最大深度が正常に設定されました。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
ULONG queue_max = 10;

/* Set the maximum size of the IP raw packet receive queue. */
status = nx_ip_raw_receive_queue_max_set (&ip_0,
                                          queue_max);

/* If status == NX_SUCCESS, the maximum size of the IP raw packet
   receive queue was successfully set. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nxd_ip_raw_packet_send
- nxd_ip_raw_packet_source_send

## <a name="nx_ip_static_route_add"></a>nx_ip_static_route_add
ルーティング テーブルに静的ルートを追加します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_static_route_add(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask,
    ULONG next_hop);
```
### <a name="description"></a>説明

このサービスを使用すると、静的ルーティング テーブルにエントリが追加されます。 *next_hop* アドレスは、いずれかのローカル ネットワーク デバイスから直接アクセスできる必要があることにご注意ください。

> [!CAUTION]  
> *次の点にご注意ください。このサービスを使用するために、ip_ptr は有効な NetX Duo IP 構造体をポイントする必要があり、NetX Duo ライブラリは NX_ENABLE_IP_STATIC_ROUTING を定義して構築される必要があります。既定で NetX Duo は、NX_ENABLE_IP_STATIC_ROUTING が定義されていない状態で構築されます*。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **network_address** ターゲット ネットワーク アドレス (ホストのバイト順) 
- **net_mask** ターゲット ネットワーク マスク (ホストのバイト順)
- **next_hop** ターゲット ネットワークのネクスト ホップ アドレス (ホストのバイト順)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 静的ルーティング テーブルにエントリが追加されました。
- **NX_OVERFLOW** (0x03) 静的ルーティング テーブルがいっぱいです。
- **NX_NOT_SUPPORTED** (0x4B) この機能はコンパイルされていません。
- **NX_IP_ADDRESS_ERROR** (0x21) ネクスト ホップにローカル インターフェイス経由で直接アクセスできません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) ip_ptr ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Specify the next hop for 192.168.1.68 through the gateway
   192.168.1.1. */
status = nx_ip_static_route_add(ip_ptr, IP_ADDRESS(192,168,1,0),
                                0xFFFFFF00UL,
                                IP_ADDRESS(192,168,1,1));

/* If status is NX_SUCCESS the route was successfully added to the
   static routing table. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_static_route_delete"></a>nx_ip_static_route_delete
静的ルートをルーティング テーブルから削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_static_route_delete(
    NX_IP *ip_ptr,
    ULONG network_address,
    ULONG net_mask);
```
### <a name="description"></a>説明

このサービスでは、静的ルーティング テーブルからエントリを削除します。

> [!WARNING]  
> *次の点にご注意ください。このサービスを使用するために、ip_ptr は有効な NetX Duo IP 構造体をポイントする必要があり、NetX Duo ライブラリは NX_ENABLE_IP_STATIC_ROUTING を定義して構築される必要があります。既定で NetX Duo は、NX_ENABLE_IP_STATIC_ROUTING が定義されていない状態で構築されます*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **network_address** ターゲット ネットワーク アドレス (ホストのバイト順)。
- **net_mask** ターゲット ネットワーク マスク (ホストのバイト順)。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 静的ルーティング テーブルからの削除に成功しました。
- **NX_NOT_SUCCESSFUL** (0x43) エントリがルーティング テーブルに見つかりません。
- **NX_NOT_SUPPORTED** (0x4B) この機能はコンパイルされていません。
- **NX_PTR_ERROR** (0x07) ip_ptr ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Remove the static route for 192.168.1.68 from the routing
   table.*/
status = nx_ip_static_route_delete(ip_ptr,
                                   IP_ADDRESS(192,168,1,0),
                                   0xFFFFFF00UL,);

/* If status is NX_SUCCESS the route was successfully removed from
   the static routing table. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nx_ip_status_check"></a>nx_ip_status_check
IP インスタンスの状態を確認します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ip_status_check(
    NX_IP *ip_ptr,
    ULONG needed_status,
    ULONG *actual_status,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成された IP インスタンスのプライマリ ネットワーク インターフェイスの指定した状態の確認が行われ、必要に応じて待機します。 セカンダリ インターフェイスの状態を取得するには、アプリケーションでサービス ***nx_ip_interface_status_check*** を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **needed_status** 要求された IP 状態。ビットマップ形式で次のように定義されます。
  - **NX_IP_INITIALIZE_DONE** (0x0001)
  - **NX_IP_ADDRESS_RESOLVED** (0x0002)
  - **NX_IP_LINK_ENABLED** (0x0004)
  - **NX_IP_ARP_ENABLED** (0x0008)
  - **NX_IP_UDP_ENABLED** (0x0010)
  - **NX_IP_TCP_ENABLED** (0x0020)
  - **NX_IP_IGMP_ENABLED** (0x0040)
  - **NX_IP_RARP_COMPLETE** (0x0080)
  - **NX_IP_INTERFACE_LINK_ENABLED** (0x0100)
- **actual_status** 設定された実際のビットの宛先へのポインター。
- **wait_option** 要求されたステータス ビットが使用できない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
  - **NX_NO_WAIT** (0x00000000)
  - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)
  - **NX_WAIT_FOREVER** 0xFFFFFFFF

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) IP 状態の確認に成功しました。
- **NX_NOT_SUCCESSFUL** (0x43) 状態要求が、指定されたタイムアウト時間内に満たされませんでした。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効であるか、無効になったか、または実際の状態ポインターが無効です。
- **NX_OPTION_ERROR** (0x0a) 必要な状態オプションが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Wait 10 ticks for the link up status on the previously created IP
   instance. */
status = nx_ip_status_check(&ip_0, NX_IP_LINK_ENABLED,
                            &actual_status, 10);

/* If status is NX_SUCCESS, the link for the specified IP instance
   is up. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_ipv4_multicast_interface_join"></a>nx_ipv4_multicast_interface_join
指定されたマルチキャスト グループに IP インスタンスをインターフェイス経由で参加させます

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ipv4_multicast_interface_join(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイス経由で、指定されたマルチキャスト グループに IP インスタンスを参加させます。 IP インスタンスがマルチキャスト グループに参加すると、この IP 受信ロジックは指定されたマルチキャスト グループから上位層へのデータ パケット転送を開始します。 このサービスは、IGMP レポートを送信せずにマルチキャスト グループに参加することにご注意ください。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **group_address** 参加するクラス D IP マルチキャスト グループ アドレス (ホストのバイト順)。
- **interface_index** NetX Duo インスタンスに接続されているインターフェイスのインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。
- **NX_NO_MORE_ENTRIES** (0x17) これ以上、マルチキャスト グループに参加できません。最大値を超えています。
- **NX_PTR_ERROR** (0x07) IP インスタンスへのポインターが無効であるか、IP インスタンスが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_EANABLED** (0x14) この IP インスタンスでは IGMP が有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定されたマルチキャスト グループ アドレスは、有効なクラス D アドレスではありません。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Previously created IP Instance joins the multicast group
   224.0.0.200, via the interface at index 1 in the IP interface
   list. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_join
                                 (&ip IP_ADDRESS(224,0,0,200),
                                  INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully joined
   the multicast group. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_ipv4_multicast_interface_leave"></a>nx_ipv4_multicast_interface_leave
指定したマルチキャスト グループをインターフェイス経由で脱退します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_ipv4_multicast_interface_leave(
    NX_IP *ip_ptr,
    ULONG group_address,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイス経由で、指定されたマルチキャスト グループを脱退します。 グループを脱退した後、このサービスでは、生成される IGMP メッセージをトリガーしません。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **group_address** 脱退するクラス D IP マルチキャスト グループ アドレス。 この IP アドレスは、ホストのバイト順になっています。
- **interface_index** NetX Duo インスタンスに接続されているインターフェイスのインデックス。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) マルチキャスト グループの参加に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) 指定したマルチキャスト グループ アドレスがローカル マルチキャスト テーブルに見つかりません。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックスが無効なネットワーク インターフェイスをポイントしています。
- **NX_IP_ADDRESS_ERROR** (0x21) 指定されたマルチキャスト グループ アドレスは、有効なクラス D アドレスではありません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) IP インスタンスへのポインターが無効であるか、IP インスタンスが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Leave the multicast group 224.0.0.200. */
#define INTERFACE_INDEX 1
status = nx_ipv4_multicast_interface_leave
                                (&ip, IP_ADDRESS(224,0,0,200),
                                 INTERFACE_INDEX);

/* If status is NX_SUCCESS, the IP instance has successfully leaves
   the multicast group 244.0.0.200. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nxd_ipv6_multicast_interface_join
- nxd_ipv6_multicast_interface_leave

## <a name="nx_packet_allocate"></a>nx_packet_allocate
指定されたプールからパケットを割り当てます

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_allocate(
    NX_PACKET_POOL *pool_ptr,
    NX_PACKET **packet_ptr,
    ULONG packet_type,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したプールからパケットが割り当てられ、指定したパケットの種類に従ってパケット内のプリペンド ポインターが調整されます。 使用可能なパケットがない場合は、指定された待機オプションに従ってサービスが中断されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたパケット プールへのポインター。
- **packet_ptr** 割り当てられたパケット ポインターのポインターへのポインター。
- **packet_type** 要求されたパケットの種類を定義します。 サポートされているパケットの種類の一覧については、第 3 章の 63 ページにある「パケット プール」を参照してください。
- **wait_option** パケット プールに使用可能なパケットがない場合の待機時間をティック数で定義します。 この待機オプションは次のように定義します。
  - **NX_NO_WAIT** (0x00000000)
  - **NX_WAIT_FOREVER** (0xFFFFFFFF)
  - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケットの割り当てに成功しました。
- **NX_NO_PACKET** (0x01) 使用可能なパケットがありません。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_INVALID_PARAMETERS** (0x4D) パケット サイズはプロトコルをサポートできません。
- **NX_OPTION_ERROR** (0x0A) パケットの種類が無効です。
- **NX_PTR_ERROR** (0x07) プールまたはパケットの戻りポインターが無効です。
- **NX_CALLER_ERROR** (0x11) スレッド以外からの待機オプションが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR (アプリケーション ネットワーク ドライバー)。 ISR またはタイマー コンテキストで使用する場合、待機オプションは *NX_NO_WAIT* である必要があります。

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Allocate a new UDP packet from the previously created packet pool
   and suspend for a maximum of 5 timer ticks if the pool is
   empty. */
status = nx_packet_allocate(&pool_0, &packet_ptr,
                            NX_UDP_PACKET, 5);

/* If status is NX_SUCCESS, the newly allocated packet pointer is
   found in the variable packet_ptr. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_copy"></a>nx_packet_copy
パケットをコピーします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_copy(
    NX_PACKET *packet_ptr,
    NX_PACKET **new_packet_ptr,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したパケットの情報が、指定したパケット プールから割り当てられている 1 つ以上の新しいパケットにコピーされます。 成功した場合、新しいパケットを指すポインターが、**new_packet_ptr** よってポイントされている宛先に返されます。

### <a name="parameters"></a>パラメーター

- **packet_ptr** 発信元パケットを指すポインター。
- **new_packet_ptr** パケットの新しいコピーを指すポインターを返すべき宛先を指すポインター。
- **pool_ptr** そのコピーのために 1 つ以上のパケットを割り当てるのに使用される、以前に作成されたパケット プールを指すポインター。
- **wait_option** 使用可能なパケットがない場合にサービスが待機する方法を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) パケットのコピーに成功しました。
- **NX_NO_PACKET** (0x01) コピーに使用できるパケットがありません。
- **NX_INVALID_PACKET** (0x12) 発信元パケットが空であるか、コピーに失敗しました。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_INVALID_PARAMETERS** (0x4D) パケット サイズはプロトコルをサポートできません。
- **NX_PTR_ERROR** (0x07) プール、パケット、または宛先のポインターが無効です。
- **NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) 待機オプションが初期化または ISR で指定されました。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NX_PACKET *new_copy_ptr;

/* Copy packet pointed to by "old_packet_ptr" using packets from
   previously created packet pool_0. */
status = nx_packet_copy(old_packet, &new_copy_ptr, &pool_0, 20);

/* If status is NX_SUCCESS, new_copy_ptr points to the packet copy. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_append"></a>nx_packet_data_append
パケットの末尾にデータを追加します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_data_append(
    NX_PACKET *packet_ptr,
    VOID *data_start, ULONG data_size,
    NX_PACKET_POOL *pool_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したパケットの末尾にデータが追加されます。 指定されたデータ領域がパケットにコピーされます。 使用可能なメモリが不足していて、チェーン化されたパケット機能が有効になっている場合、要求を満たすために 1 つ以上のパケットが割り当てられます。 チェーン化されたパケット機能が有効になっていない場合は、*NX_SIZE_ERROR* が返されます。

### <a name="parameters"></a>パラメーター

- **packet_ptr** パケット ポインター。
- **data_start** パケットに追加するユーザーのデータ領域の先頭を指すポインター。
- **data_size** ユーザーのデータ領域のサイズ。
- **pool_ptr** 現在のパケットに十分な空き領域がない場合に、別のパケットの割り当て元となるパケット プールを指すポインター。
- **wait_option** 使用可能なパケットがない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットの追加に成功しました。
- **NX_NO_PACKET** (0x01) 使用可能なパケットがありません。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_INVALID_PARAMETERS** (0x4D) パケット サイズはプロトコルをサポートできません。
- **NX_UNDERFLOW** (0x02) プリペンド ポインターがペイロードの先頭未満です。
- **NX_OVERFLOW** (0x03) 追加ポインターがペイロードの末尾を超えています。
- **NX_PTR_ERROR** (0x07) プール、パケット、またはデータ ポインターが無効です。
- **NX_SIZE_ERROR** (0x09) データ サイズが無効です。
- **NX_CALLER_ERROR** (0x11) スレッド以外からの待機オプションが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR (アプリケーション ネットワーク ドライバー)

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Append "abcd" to the specified packet. */
status = nx_packet_data_append(packet_ptr, "abcd", 4, &pool_0, 5);

/* If status is NX_SUCCESS, the additional four bytes "abcd" have
   been appended to the packet. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release


## <a name="nx_packet_data_extract_offset"></a>nx_packet_data_extract_offset
オフセット経由でパケットからデータを抽出します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_data_extract_offset(
    NX_PACKET *packet_ptr,
    ULONG offset,
    VOID *buffer_start,
    ULONG buffer_length,
    ULONG *bytes_copied);
```
### <a name="description"></a>説明

このサービスでは、NetX Duo パケット (またはパケット チェーン) のデータを、パケット先頭追加ポインターからのオフセットで指定した起点から、バイト単位で指定したサイズだけ、指定されたバッファーにコピーします。 実際にコピーされたバイト数が *bytes_copied* に返されます。 このサービスでは、パケットからデータは削除されません。また、プリペンド ポインターやその他の内部状態情報も調整されません。

### <a name="parameters"></a>パラメーター

- **packet_ptr** 抽出するパケットを指すポインター
- **offset** 現在のプリペンド ポインターからのオフセット。
- **buffer_start** 保存バッファーの先頭を指すポインター
- **buffer_length** コピーするバイト数
- **bytes_copied** 実際にコピーされたバイト数

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットのコピーに成功しました
- **NX_PACKET_OFFSET_ERROR** (0x53) 無効なオフセット値が指定されました
- **NX_PTR_ERROR** (0x07) パケット ポインターまたはバッファー ポインターが無効です

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

```c
/* Extract 10 bytes from the start of the received packet buffer
   into the specified memory area. */
status = nx_packet_data_extract_offset(my_packet, 0, &data[0], 10,
                                       &bytes_copied) ;
/* If status is NX_SUCCESS, 10 bytes were successfully copied into
   the data buffer. */
```
### <a name="see-also"></a>関連項目

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_data_retrieve"></a>nx_packet_data_retrieve
パケットからデータを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_data_retrieve(
    NX_PACKET *packet_ptr,
    VOID *buffer_start,
    ULONG *bytes_copied);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したパケットから指定したバッファーにデータがコピーされます。 コピーされた実際のバイト数は、**bytes_copied** から指されている宛先に返されます。

このサービスでは、パケットの内部状態は変更されないことにご注意ください。 取得されるデータは、パケットで引き続き使用できます。 

> [!CAUTION]  
> *コピー先のバッファーは、パケットの内容を保持するのに十分な大きさである必要があります。十分でない場合、メモリが破損し、予期しない結果が発生します*。

### <a name="parameters"></a>パラメーター

- **packet_ptr** 発信元パケットを指すポインター。
- **buffer_start** バッファー領域の先頭を指すポインター。
- **bytes_copied** コピーされたバイト数の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケット データの取得に成功しました。
- **NX_INVALID_PACKET** (0x12) パケットが無効です。
- **NX_PTR_ERROR** (0x07) パケット、バッファーの先頭、またはコピーされたバイト数のポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
UCHAR                 buffer[512];
ULONG                 bytes_copied;

/* Retrieve data from packet pointed to by "packet_ptr". */
status = nx_packet_data_retrieve(packet_ptr, buffer, &bytes_copied);

/* If status is NX_SUCCESS, buffer contains the contents of the
   packet, the size of which is contained in "bytes_copied." */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_length_get"></a>nx_packet_length_get
パケット データの長さを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_length_get(
    NX_PACKET *packet_ptr, 
    ULONG *length);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したパケット内のデータの長さが取得されます。

### <a name="parameters"></a>パラメーター

- **packet_ptr** パケットを指すポインター。
- **length** パケットの長さの宛先。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) パケットの長さの取得に成功しました。
- **NX_PTR_ERROR** (0x07) パケット ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the length of the data in "my_packet." */
status = nx_packet_length_get(my_packet, &my_length);

/* If status is NX_SUCCESS, data length is in "my_length". */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_create"></a>nx_packet_pool_create
指定されたメモリ領域にパケット プールを作成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_pool_create(
    NX_PACKET_POOL *pool_ptr,
    CHAR *name,
    ULONG payload_size,
    VOID *memory_ptr,
    ULONG memory_size);
```
### <a name="description"></a>説明

このサービスを使用すると、ユーザーが指定したメモリ領域に、指定したパケット サイズのパケット プールが作成されます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** パケット プール制御ブロックを指すポインター。
- **name** パケット プールのアプリケーションの名前を指すポインター。
- **payload_size** プール内の各パケットのバイト数。 この値は、40 バイト以上である必要があり、4 で割り切れなければなりません。
- **memory_ptr** パケット プールを配置するメモリ領域を指すポインター。 このポインターは、ULONG 境界上に配置する必要があります。
- **memory_size** プールのメモリ領域のサイズ。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケット プールの作成に成功しました。
- **NX_PTR_ERROR** (0x07) プールまたはメモリ ポインターが無効です。
- **NX_SIZE_ERROR** (0x09) ブロックまたはメモリのサイズが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Create a packet pool of 32000 bytes starting at physical
   address 0x10000000. */
status = nx_packet_pool_create(&pool_0, "Default Pool", 128,
                               (void *) 0x10000000, 32000);

/* If status is NX_SUCCESS, the packet pool has been successfully
   created. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_delete"></a>nx_packet_pool_delete
以前に作成されたパケット プールを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT  nx_packet_pool_delete(NX_PACKET_POOL *pool_ptr);
```
### <a name="description"></a>説明

このサービスでは、以前に作成されたパケット プールを削除します。 NetX Duo により、そのパケット プール内のパケットで現在中断状態にあるスレッドがないかが確認され、中断がクリアされます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** パケット プール制御ブロック ポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケット プールの削除に成功しました。
- **NX_PTR_ERROR** (0x07) プール ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
/* Delete a previously created packet pool. */
status = nx_packet_pool_delete(&pool_0);

/* If status is NX_SUCCESS, the packet pool has been successfully
   deleted. */
```

### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_info_get"></a>nx_packet_pool_info_get
パケット プールに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_pool_info_get(
    NX_PACKET_POOL *pool_ptr,
    ULONG *total_packets,
    ULONG *free_packets,
    ULONG *empty_pool_requests,
    ULONG *empty_pool_suspensions,
    ULONG *invalid_packet_releases);
```
### <a name="description"></a>説明

このサービスでは、指定されたパケット プールに関する情報を取得します。

> [!IMPORTANT]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **pool_ptr** 以前に作成されたパケット プールを指すポインター。
- **total_packets** プール内のパケットの合計数の宛先を指すポインター。
- **free_packets** 現在解放されているパケットの合計数の宛先を指すポインター。
- **empty_pool_requests** プールが空だった場合の割り当て要求の合計数の宛先を指すポインター。
- **empty_pool_suspensions** 空のプールによる中断の合計数の宛先を指すポインター。
- **invalid_packet_releases** 無効なパケット リリースの合計数の宛先を指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケット プール情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve packet pool information. */
status = nx_packet_pool_info_get(&pool_0,
                                 &total_packets,
                                 &free_packets,
                                 &empty_pool_requests,
                                 &empty_pool_suspensions,
                                 &invalid_packet_releases);

/* If status is NX_SUCCESS, packet pool information was
   retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_low_watermark_set
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_pool_low_watermark_set"></a>nx_packet_pool_low_watermark_set
パケット プールの低レベルのウォーターマークを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_pool_low_watermark_set(
    NX_PACKET_POOL *pool_ptr,
    ULONG low_watermark);
```
### <a name="description"></a>説明

このサービスでは、指定されたパケット プールの低レベルのウォーターマークを構成します。 低レベルのウォーターマーク値を設定すると、TCP または UDP は、パケット プール内の使用可能なパケット数がそのパケット プールの低レベル ウォーターマーク未満の場合、受信したパケットをキューで待機しません。これにより、パケット プールのパケットが不足するのを防ぐことができます。 このサービスは、オプション ***NX_ENABLE_LOW_WATERMARK*** を定義して NetX Duo ライブラリが構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター

- **pool_ptr** パケット プール制御ブロックへのポインター。
- **low_watermark** 構成する低レベルのウォーターマーク値

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 低レベルのウォーターマーク値が正常に設定されました。
- **NX_NOT_SUPPORTED** (0x4B) 低レベルのウォーターマーク機能は NetX Duo に組み込まれていません。
- **NX_PTR_ERROR** (0x07) プール ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Set pool_0 low watermark value to 2. */
status = nx_packet_pool_create(&pool_0, 2);

/* If status is NX_SUCCESS, the low watermark value is set for
   pool_0.*/
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_release
- nx_packet_transmit_release

## <a name="nx_packet_release"></a>nx_packet_release
以前に割り当てられたパケットを解放します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、パケットが解放されます。これには、指定したパケットにチェーンされている追加のパケットも含まれます。 パケット割り当てで別のスレッドがブロックされている場合は、それにこのパケットが与えられて、それが再開されます。

> [!NOTE]  
> *パケットが複数回解放されると予期しない結果が発生するため、アプリケーションでそれが生じないようにする必要があります*。

### <a name="parameters"></a>パラメーター

- **packet_ptr** パケット ポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケットの解放に成功しました。
- **NX_PTR_ERROR** (0x07) パケット ポインターが無効です。
- **NX_UNDERFLOW** (0x02) プリペンド ポインターがペイロードの先頭未満です。
- **NX_OVERFLOW** (0x03) 追加ポインターがペイロードの末尾を超えています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR (アプリケーション ネットワーク ドライバー)

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
/* Release a previously allocated packet. */
status = nx_packet_release(packet_ptr);

/* If status is NX_SUCCESS, the packet has been returned to the
   packet pool it was allocated from. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_transmit_release

## <a name="nx_packet_transmit_release"></a>nx_packet_transmit_release
送信済みパケットを解放します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_packet_transmit_release(NX_PACKET *packet_ptr);
```
### <a name="description"></a>説明

TCP 以外のパケットの場合、このサービスによって送信済みパケットが解放されます。これには、指定されたパケットにチェーンされている追加のパケットも含まれます。 パケット割り当てで別のスレッドがブロックされている場合は、そのスレッドにこのパケットが与えられて、再開されます。 送信済みの TCP パケットの場合、パケットは送信中としてマークされますが、パケットの受信が確認されるまでは解放されません。 通常、このサービスは、パケットが送信された後にアプリケーションのネットワーク ドライバーから呼び出されます。

> [!WARNING] 
> *ネットワーク ドライバーでは、このサービスを呼び出す前に、物理メディア ヘッダーを削除し、パケットの長さを調整する必要があります*。

### <a name="parameters"></a>パラメーター

- **packet_ptr** パケット ポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 送信パケットの解放に成功しました。
- **NX_PTR_ERROR** (0x07) パケット ポインターが無効です。
- **NX_UNDERFLOW** (0x02) プリペンド ポインターがペイロードの先頭未満です。
- **NX_OVERFLOW** (0x03) 追加ポインターがペイロードの末尾を超えています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、アプリケーション ネットワーク ドライバー (ISR を含む)

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
/* Release a previously allocated packet that was just transmitted
   from the application network driver. */
status = nx_packet_transmit_release(packet_ptr);

/* If status is NX_SUCCESS, the transmitted packet has been
   returned to the packet pool it was allocated from. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_packet_allocate
- nx_packet_copy
- nx_packet_data_append
- nx_packet_data_extract_offset
- nx_packet_data_retrieve
- nx_packet_length_get
- nx_packet_pool_create
- nx_packet_pool_delete
- nx_packet_pool_info_get
- nx_packet_pool_low_watermark_set
- nx_packet_release

## <a name="nx_rarp_disable"></a>nx_rarp_disable
逆アドレス解決プロトコル (RARP) を無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_rarp_disable(NX_IP *ip_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、特定の IP インスタンスの NetX Duo の RARP コンポーネントが無効になります。 マルチホーム システムの場合、このサービスを使用するとすべてのインターフェイスで RARP が無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) RARP の無効化に成功しました。
- **NX_NOT_ENABLED** (0x14) RARP が有効になっていませんでした。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Disable RARP on the previously created IP instance. */
status = nx_rarp_disable(&ip_0);

/* If status is NX_SUCCESS, RARP is disabled. */
```
### <a name="see-also"></a>参照

- nx_rarp_enable
- nx_rarp_info_get

## <a name="nx_rarp_enable"></a>nx_rarp_enable
逆アドレス解決プロトコル (RARP) を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_rarp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、特定の IP インスタンスの NetX Duo の RARP コンポーネントが有効になります。 RARP コンポーネントでは、接続されているすべてのネットワーク インターフェイスから IP アドレスがゼロであるものを検索します。 IP アドレスがゼロであることは、そのインターフェイスに IP アドレスがまだ割り当てられていないことを示します。 RARP は、そのインターフェイスで RARP プロセスを有効にすることにより、IP アドレスの解決を試みます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) RARP の有効化に成功しました。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスは既に有効です。
- **NX_ALREADY_ENABLED** (0x15) RARP は既に有効になっています。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable RARP on the previously created IP instance. */
status = nx_rarp_enable(&ip_0);

/* If status is NX_SUCCESS, RARP is enabled and is attempting to
   resolve this IP instance’s address by querying the network. */
```
### <a name="see-also"></a>参照

- nx_rarp_disable
- nx_rarp_info_get

## <a name="nx_rarp_info_get"></a>nx_rarp_info_get
RARP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_rarp_info_get(
    NX_IP *ip_ptr,
    ULONG *rarp_requests_sent,
    ULONG *rarp_responses_received,
    ULONG *rarp_invalid_messages);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの RARP アクティビティに関する情報を取得します。

> [!IMPORTANT]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **rarp_requests_sent** 送信された RARP 要求の合計数の宛先を指すポインター。
- **rarp_responses_received** 受信した RARP 応答の合計数の宛先を指すポインター。
- **rarp_invalid_messages** 無効なメッセージの合計数の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) RARP 情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve RARP information from previously created IP
   Instance 0. */
status = nx_rarp_info_get(&ip_0,
                          &rarp_requests_sent,
                          &rarp_responses_received,
                          &rarp_invalid_messages);

/* If status is NX_SUCCESS, RARP information was retrieved. */
```
### <a name="see-also"></a>参照

- nx_rarp_disable
- nx_rarp_enable

## <a name="nx_system_initialize"></a>nx_system_initialize
NetX Duo システムを初期化します

### <a name="prototype"></a>プロトタイプ  

```c
VOID nx_system_initialize(VOID);
```
### <a name="description"></a>説明

このサービスを使用すると、NetX Duo の基本的なシステム リソースが使用に備えて初期化されます。 これはアプリケーションにより、初期化中、他のどの NetX Duo 呼び出しが実行されるよりも前に呼び出されなければなりません。

### <a name="parameters"></a>パラメーター

なし

### <a name="return-values"></a>戻り値

なし

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

システム管理

### <a name="example"></a>例

```c
/* Initialize NetX Duo for operation. */
nx_system_initialize();

/* At this point, NetX Duo is ready for IP creation and all
   subsequent network operations. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nx_tcp_client_socket_bind"></a>nx_tcp_client_socket_bind
TCP ポートにクライアントの TCP ソケットをバインドします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_client_socket_bind(
    NX_TCP_SOCKET *socket_ptr,
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成された TCP クライアント ソケットが、指定した TCP ポートにバインドされます。 有効な TCP ソケットの範囲は 0 から 0xFFFF です。 指定された TCP ポートが使用できない場合は、指定された待機オプションに従ってサービスが中断されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット インスタンスへのポインター。
- **port** バインドするポート番号 (1 から 0xFFFF)。 ポート番号が NX_ANY_PORT (0x0000) の場合、IP インスタンスによって次の空きポートが検索されて、バインドに使用されます。
- **wait_option** ポートが既に別のソケットにバインドされている場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
- **NX_NO_WAIT** (0x00000000)
- **NX_WAIT_FOREVER** (0xFFFFFFFF)
- **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソケットのバインドに成功しました。
- **NX_ALREADY_BOUND** (0x22) このソケットは既に別の TCP ポートにバインドされています。
- **NX_PORT_UNAVAILABLE** (0x23) ポートは既に別のソケットにバインドされています。
- **NX_NO_FREE_PORTS** (0x45) 空きポートがありません。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_INVALID_PORT** (0x46) ポートが無効です。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Bind a previously created client socket to port 12 and wait for 7
   timer ticks for the bind to complete. */
status = nx_tcp_client_socket_bind(&client_socket, 12, 7);

/* If status is NX_SUCCESS, the previously created client_socket is
   bound to port 12 on the associated IP instance. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_connect"></a>nx_tcp_client_socket_connect
クライアントの TCP ソケットを接続します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスでは、以前に作成され、バインドされた TCP クライアント ソケットを、指定されたサーバーのポートに接続します。 有効な TCP サーバー ポートの範囲は 0 から 0xFFFF です。 接続がすぐに完了しない場合、指定された待機オプションに従ってサービスが中断されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。
- **server_ip** サーバーの IP アドレス。
- **server_port** 接続先のサーバー ポート番号** (1 から 0xFFFF)。
- **wait_option** 接続を確立している最中のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットの接続に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがバインドされていません。
- **NX_NOT_CLOSED** (0x35) ソケットが CLOSED 状態ではありません。
- **NX_IN_PROGRESS** (0x37) 待機が指定されていないため、接続の試行を実行中です。
- **NX_INVALID_INTERFACE** (0x4C) 指定されたインターフェイスが無効です。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_IP_ADDRESS_ERROR** (0x21) サーバー IP アドレスが無効です。
- **NX_INVALID_PORT** (0x46) ポートが無効です。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Initiate a TCP connection from a previously created and bound
   client socket. The connection requested in this example is to
   port 12 on the server with the IP address of 1.2.3.5. This
   service will wait 300 timer ticks for the connection to take
   place before giving up. */
status = nx_tcp_client_socket_connect(&client_socket,
                                      IP_ADDRESS(1,2,3,5),
                                      12, 300);

/* If status is NX_SUCCESS, the previously created and bound
   client_socket is connected to port 12 on IP 1.2.3.5. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_port_get"></a>nx_tcp_client_socket_port_get
クライアントの TCP ソケットにバインドされているポート番号を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_client_socket_port_get(
    NX_TCP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>説明

このサービスでは、ソケットに関連付けられているポート番号を取得します。これは、ソケットのバインド時に NX_ANY_PORT が指定された場合に NetX Duo によって割り当てられたポートを見つけるのに便利です。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。
- **port_ptr** 戻りポート番号の宛先を指すポインター。 有効なポート番号は、1 から 0xFFFF です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソケットのバインドに成功しました。
- **NX_NOT_BOUND** (0x24) このソケットはポートにバインドされていません。
- **NX_PTR_ERROR** (0x07) ソケット ポインターまたはポートの戻りポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the port number of previously created and bound client
   socket. */
status = nx_tcp_client_socket_port_get(&client_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_client_socket_unbind"></a>nx_tcp_client_socket_unbind
TCP クライアント ソケットを TCP ポートからバインド解除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_client_socket_unbind(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、TCP クライアント ソケットと TCP ポートとの間のバインドが解放されます。 他のスレッドが同じポート番号に別のソケットをバインドするために待機している場合は、中断されている最初のスレッドがこのポートにバインドされます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットのバインド解除に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。
- **NX_NOT_CLOSED** (0x35) ソケットが切断されていません。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
/* Unbind a previously created and bound client TCP socket. */
status = nx_tcp_client_socket_unbind(&client_socket);

/* If status is NX_SUCCESS, the client socket is no longer
   bound. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_enable"></a>nx_tcp_enable
NetX Duo の TCP コンポーネントを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、NetX Duo の伝送制御プロトコル (TCP) コンポーネントを有効にします。 有効にすると、アプリケーションで TCP 接続を確立できるようになります。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TCP の有効化に成功しました。
- **NX_ALREADY_ENABLED** (0x15) TCP は既に有効になっています。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable TCP on a previously created IP instance ip_0. */
status = nx_tcp_enable(&ip_0);

/* If status is NX_SUCCESS, TCP is enabled on the IP instance. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_free_port_find"></a>nx_tcp_free_port_find
使用可能な次の TCP ポートを検索します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_free_port_find(
    NX_IP *ip_ptr,
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、アプリケーションで指定されているポートを起点として、空いている TCP ポート (バインドされていない) の検索が試みられます。 この検索ロジックは、検索が最大ポート値 0xFFFF に到達すると、ラップアラウンドします。 検索が成功すると、*free_port_ptr* によってポイントされている変数に空きポートが返されます。

> [!WARNING]  
> *このサービスが別のスレッドから呼び出されて、同じポートが返される場合があります。このような競合状態を回避するには、アプリケーションでこのサービスと実際のクライアント ソケット バインドをミューテックスの保護下に置くことが必要になる場合があります*。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **port** 検索を開始するポート番号 (1 から 0xFFFF)。
- **free_port_ptr** 宛先の空きポートの戻り値を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 空きポートの検索に成功しました。
- **NX_NO_FREE_PORTS** (0x45) 空きポートが見つかりませんでした。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_INVALID_PORT** (0x46) 指定されたポート番号が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Locate a free TCP port, starting at port 12, on a previously
   created IP instance. */
status = nx_tcp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS, "free_port" contains the next free port
   on the IP instance. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_info_get"></a>nx_tcp_info_get
TCP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_info_get(
    NX_IP *ip_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_invalid_packets,
    ULONG *tcp_receive_packets_dropped,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_connections,
    ULONG *tcp_disconnections,
    ULONG *tcp_connections_dropped,
    ULONG *tcp_retransmit_packets);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの TCP アクティビティに関する情報を取得します。

> [!IMPORTANT]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **tcp_packets_sent** 送信された TCP パケットの合計数の宛先を指すポインター。
- **tcp_bytes_sent** 送信された TCP バイトの合計数の宛先を指すポインター。
- **tcp_packets_received** 受信した TCP パケットの合計数の宛先を指すポインター。
- **tcp_bytes_received** 受信した TCP バイトの合計数の宛先を指すポインター。
- **tcp_invalid_packets** 無効な TCP パケットの合計数の宛先を指すポインター。
- **tcp_receive_packets_dropped** 破棄された TCP 受信パケットの合計数の宛先を指すポインター。
- **tcp_checksum_errors** チェックサム エラーが発生している TCP パケットの合計数の宛先を指すポインター。
- **tcp_connections** TCP 接続の合計数の宛先を指すポインター。
- **tcp_disconnections** TCP 切断の合計数の宛先を指すポインター。
- **tcp_connections_dropped** 破棄された TCP 接続の合計数の宛先を指すポインター。
- **tcp_retransmit_packets** 再送信された TCP パケットの合計数の宛先を指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) TCP 情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve TCP information from previously created IP Instance
   ip_0. */
status = nx_tcp_info_get(&ip_0,
                         &tcp_packets_sent,
                         &tcp_bytes_sent,
                         &tcp_packets_received,
                         &tcp_bytes_received,
                         &tcp_invalid_packets,
                         &tcp_receive_packets_dropped,
                         &tcp_checksum_errors,
                         &tcp_connections,
                         &tcp_disconnections
                         &tcp_connections_dropped,
                         &tcp_retransmit_packets);

/* If status is NX_SUCCESS, TCP information was retrieved. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_accept"></a>nx_tcp_server_socket_accept
TCP 接続を受け入れます

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_server_socket_accept(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスでは、以前にリッスン用に設定されたポートに対する、TCP クライアント ソケット接続要求を受け入れます (または受け入れる準備を行います)。 このサービスは、アプリケーションがリッスンまたは再リッスン サービスを呼び出した直後、またはクライアント接続が実際に存在する場合は、リッスン コールバック ルーチンが呼び出された後に呼び出されることがあります。 接続をすぐに確立できない場合、サービスは指定された待機オプションに従って中断されます。

> [!WARNING]  
> *サーバー ポートへのサーバー ソケットのバインドを削除するためにその接続が必要ではなくなった後、アプリケーションで **nx_tcp_server_socket_unaccept** を呼び出す必要があります*。

> [!IMPORTANT]  
> *アプリケーション コールバック ルーチンは、IP のヘルパー スレッド内から呼び出されます*。

### <a name="parameters"></a>パラメーター

- **socket_ptr** TCP サーバー ソケット制御ブロックを指すポインター。
- **wait_option** 接続を確立している最中のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) TCP サーバー ソケットの受け入れに成功しました (パッシブ接続)。
- **NX_NOT_LISTEN_STATE** (0x36) 指定されたサーバー ソケットはリッスン状態ではありません。
- **NX_IN_PROGRESS** (0x37) 待機が指定されていないため、接続の試行を実行中です。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_PTR_ERROR** (0x07) ソケット ポインター エラー。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
    /* Simply set the semaphore to wake up the server thread. */
    tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
    /* The client has initiated a disconnect on this socket. This
       example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
    /* Assuming that:
       "port_12_semaphore" has already been created with an
        initial count of 0 "my_ip" has already been created and the
        link is enabled "my_pool" packet pool has already been
        created
    */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket,
                         "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending
       "Hello_and_Goodbye" to each client and then disconnecting.*/
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection
        request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
        if (status == NX_SUCCESS)
        {

            /* Allocate a packet for the "Hello_and_Goodbye"
               message */
            nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                         NX_WAIT_FOREVER);

            /* Place "Hello_and_Goodbye" in the packet. */
            nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                  sizeof("Hello_and_Goodbye"),
                                  &my_pool, NX_WAIT_FOREVER);

            /* Send "Hello_and_Goodbye" to client. */
            nx_tcp_socket_send(&server_socket, my_packet, 200);

            /* Check for an error. */
            if (status)
            {
               /* Error, release the packet. */
               nx_packet_release(my_packet);
            }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_listen"></a>nx_tcp_server_socket_listen
TCP ポートでのクライアント接続のリッスンを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_server_socket_listen(
    NX_IP *ip_ptr, UINT port,
    NX_TCP_SOCKET *socket_ptr,
    UINT listen_queue_size,
    VOID (*listen_callback)(NX_TCP_SOCKET *socket_ptr, UINT port));
```
### <a name="description"></a>説明

このサービスを使用すると、指定した TCP ポートでクライアント接続要求をリッスンできるようになります。 クライアント接続要求を受信すると、指定されたサーバー ソケットが指定されたポートにバインドされ、指定されたリッスン コールバック関数が呼び出されます。

リッスン コールバック ルーチンの処理は、アプリケーションによって決まります。 アプリケーションによっては、後から受け入れ操作を実行するアプリケーション スレッドをウェイクアップするロジックが含まれている場合があります。 アプリケーションによるこのソケットの受け入れ処理でスレッドが既に中断されている場合、リッスン コールバック ルーチンは必要ではない可能性があります。

同じポート上の追加のクライアント接続をそのアプリケーションで処理する場合は、次の接続のために使用可能なソケット (CLOSED 状態のソケット) を使用して ***nx_tcp_server_socket_relisten*** を呼び出す必要があります。 再リッスン サービスが呼び出されるまで、追加のクライアント接続はキューに入れられます。 キューの最大深度を超えた場合は、新しい接続要求をキューできるようにするため、最も古い接続要求が破棄されます。 キューの最大深度は、このサービスによって指定されます。

> [!IMPORTANT]  
> *アプリケーション コールバック ルーチンは、内部の IP ヘルパー スレッドから呼び出されます*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **port** リッスンするポート番号 (1 から 0xFFFF)。
- **socket_ptr** 接続に使用するソケットを指すポインター。
- **listen_queue_size** キューに入れることができるクライアント接続要求の数。
- **listen_callback** 接続を受信したときに呼び出すアプリケーション関数。 NULL 値が指定されている場合、リッスン コールバック機能は無効になります。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) TCP ポートのリッスンの有効化に成功しました。
- **NX_MAX_LISTEN** (0x33) 使用できるリッスン要求構造体がこれ以上ありません。 **_nx_api.h_** の定数 NX_MAX_LISTEN_REQUESTS により、許可されるアクティブなリッスン要求の数が定義されます。
- **NX_NOT_CLOSED** (0x35) 指定されたサーバー ソケットが CLOSED 状態ではありません。
- **NX_ALREADY_BOUND** (0x22) 指定されたサーバー ソケットは既にポートにバインドされています。
- **NX_DUPLICATE_LISTEN** (0x34) このポートに対するアクティブなリッスン要求が既に存在します。
- **NX_INVALID_PORT** (0x46) 指定されたポートが無効です。
- **NX_PTR_ERROR** (0x07) IP またはソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{
   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket.
   This example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{
NX_PACKET *my_packet;
UINT status, i;
   /* Assuming that:
      "port_12_semaphore" has already been created with an
      initial count of 0 "my_ip" has already been created
      and the link is enabled "my_pool" packet pool has already
      been created.
   */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                        Socket",
                        NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                        NX_IP_TIME_TO_LIVE, 100,
                        NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to
      each client and then disconnecting. */
   for (i = 0; i < 5; i++)
   {

        /* Get the semaphore that indicates a client connection
           request is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection
           to complete. */
        status = nx_tcp_server_socket_accept(&server_socket, 200);

        /* Check for a successful connection. */
           if (status == NX_SUCCESS)
        {

              /* Allocate a packet for the "Hello_and_Goodbye"
                 message. */
              nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                 NX_WAIT_FOREVER);

              /* Place "Hello_and_Goodbye" in the packet. */
              nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                    sizeof("Hello_and_Goodbye"),
                                    &my_pool,
                                    NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {
                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

            /* Now disconnect the server socket from the client. */
            nx_tcp_socket_disconnect(&server_socket, 200);
         }
         /* Unaccept the server socket. Note that unaccept is called
            even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
         again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);
     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```

### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_relisten"></a>nx_tcp_server_socket_relisten
TCP ポートでクライアント接続を再リッスンします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_server_socket_relisten(
    NX_IP *ip_ptr, 
    UINT port,
    NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスは、以前にリッスン用に設定されたポートで接続を受信した後に呼び出されます。 このサービスの主な目的は、次のクライアント接続に新しいサーバー ソケットを提供することです。 キューに入れられている接続要求がある場合、このサービス呼び出し中にその接続が直ちに処理されます。

> [!IMPORTANT]  
> *元のリッスン要求によって指定されたのと同じコールバック ルーチンが、この新しいサーバー ソケットのための接続が存在する場合にも呼び出されます*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **port** 再リッスンするポート番号 (1 から 0xFFFF)。
- **socket_ptr** 次のクライアント接続に使用するソケット。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) TCP ポートの再リッスンに成功しました。
- **NX_NOT_CLOSED** (0x35) 指定されたサーバー ソケットが CLOSED 状態ではありません。
- **NX_ALREADY_BOUND** (0x22) 指定されたサーバー ソケットは既にポートにバインドされています。
- **NX_INVALID_RELISTEN** (0x47) このポートには有効なソケット ポインターが既に存在するか、指定されたポートでリッスン要求がアクティブになっていません。
- **NX_CONNECTION_PENDING** (0x48) キューに入れられた接続要求が既に存在しており、この呼び出し中にその要求が処理されたこと以外は、NX_SUCCESS と同じです。
- **NX_INVALID_PORT** (0x46) 指定されたポートが無効です。
- **NX_PTR_ERROR** (0x07) IP またはリッスン コールバック ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NX_PACKET_POOL my_pool;
NX_IP my_ip;
NX_TCP_SOCKET server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread.*/
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This
      example doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial
     count of 0.
    "my_ip" has already been created and the link is enabled.
    "my_pool" packet pool has already been created. */

   /* Create the server socket. */
   nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                                 NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                                 NX_IP_TIME_TO_LIVE, 100,
                                 NX_NULL, port_12_disconnect_request);

   /* Setup server listening on port 12. */
   nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                               port_12_connect_request);

   /* Loop to process 5 server connections, sending
      "Hello_and_Goodbye" to each client then disconnecting. */
   for (i = 0; i < 5; i++)
   {

       /* Get the semaphore that indicates a client connection
          request is present. */
       tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

       /* Wait for 200 ticks for the client socket connection to
          complete. */
       status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {

             /* Allocate a packet for the "Hello_and_Goodbye"
                message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"),
                                   &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
         }

         /* Unaccept the server socket. Note that unaccept is
            called even if disconnect or accept fails. */
         nx_tcp_server_socket_unaccept(&server_socket);

         /* Setup server socket for listening with this socket
            again. */
         nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }

     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unaccept"></a>nx_tcp_server_socket_unaccept
リッスン ポートとのソケットの関連付けを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_server_socket_unaccept(NX_TCP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、このサーバー ソケットと指定したサーバー ポートとの間の関連付けが削除されます。 アプリケーションは、切断の後か、着信の応答に失敗した後、このサービスを呼び出す必要があります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前にセットアップされたサーバーのソケット インスタンスを指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) サーバー ソケットの受け入れ解除に成功しました。
- **NX_NOT_LISTEN_STATE** (0x36) サーバー ソケットが不適切な状態のため、切断されていない可能性があります。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NX_PACKET_POOL        my_pool;
NX_IP                 my_ip;
NX_TCP_SOCKET         server_socket;
void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

   /* Simply set the semaphore to wake up the server thread. */
   tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{
   /* The client has initiated a disconnect on this socket. This example
   doesn't use this callback. */
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET  *my_packet;
UINT       status, i;

   /* Assuming that:
     "port_12_semaphore" has already been created with an initial count
      of 0 "my_ip" has already been created and the link is enabled
     "my_pool" packet pool has already been created
   */

    /* Create the server socket. */
    nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server
                         Socket",NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                         NX_IP_TIME_TO_LIVE, 100,NX_NULL,
                         port_12_disconnect_request);

    /* Setup server listening on port 12. */
    nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                port_12_connect_request);

    /* Loop to process 5 server connections, sending "Hello_and_Goodbye"
       to
       each client and then disconnecting. */
    for (i = 0; i < 5; i++)
    {

        /* Get the semaphore that indicates a client connection request
           is present. */
        tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

        /* Wait for 200 ticks for the client socket connection to
           complete.*/
        status = nx_tcp_server_socket_accept(&server_socket, 200);

       /* Check for a successful connection. */
          if (status == NX_SUCCESS)
       {
             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet,
                      "Hello_and_Goodbye",sizeof("Hello_and_Goodbye"),
                      &my_pool, NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
       }

       /* Unaccept the server socket. Note that unaccept is called even
          if disconnect or accept fails. */
       nx_tcp_server_socket_unaccept(&server_socket);

      /* Setup server socket for listening with this socket again. */
      nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
    }

    /* We are now done so unlisten on server port 12. */
    nx_tcp_server_socket_unlisten(&my_ip, 12);

    /* Delete the server socket. */
    nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_server_socket_unlisten"></a>nx_tcp_server_socket_unlisten
TCP ポートでのクライアント接続のリッスンを無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_server_socket_unlisten(
    NX_IP *ip_ptr, 
    UINT port);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した TCP ポートでのクライアント接続要求のリッスンが無効になります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **port** リッスンを無効にするポートの数 (0 から 0xFFFF)。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) TCP のリッスンの無効化に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) 指定されたポートに対してリッスンが有効になっていませんでした。
- **NX_INVALID_PORT** (0x46) 指定されたポートが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NX_PACKET_POOL       my_pool;
NX_IP                my_ip;
NX_TCP_SOCKET        server_socket;

void port_12_connect_request(NX_TCP_SOCKET *socket_ptr, UINT port)
{

     /* Simply set the semaphore to wake up the server thread. */
     tx_semaphore_put(&port_12_semaphore);
}

void port_12_disconnect_request(NX_TCP_SOCKET *socket_ptr)
{

     /* The client has initiated a disconnect on this socket. This example
        doesn't use this callback.*/
}

void port_12_server_thread_entry(ULONG id)
{

NX_PACKET *my_packet;
UINT status, i;

     /* Assuming that:
       "port_12_semaphore" has already been created with an initial count
        of 0 "my_ip" has already been created and the link is enabled
       "my_pool" packet pool has already been created
     */

     /* Create the server socket. */
     nx_tcp_socket_create(&my_ip, &server_socket, "Port 12 Server Socket",
                          NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                          NX_IP_TIME_TO_LIVE, 100,
                          NX_NULL, port_12_disconnect_request);

     /* Setup server listening on port 12. */
     nx_tcp_server_socket_listen(&my_ip, 12, &server_socket, 5,
                                 port_12_connect_request);

     /* Loop to process 5 server connections, sending "Hello_and_Goodbye" to
        each client and then disconnecting. */
     for (i = 0; i < 5; i++)
     {

         /* Get the semaphore that indicates a client connection request is
            present. */
         tx_semaphore_get(&port_12_semaphore, TX_WAIT_FOREVER);

         /* Wait for 200 ticks for the client socket connection to complete.*/
         status = nx_tcp_server_socket_accept(&server_socket, 200);

         /* Check for a successful connection. */
         if (status == NX_SUCCESS)
         {

             /* Allocate a packet for the "Hello_and_Goodbye" message. */
             nx_packet_allocate(&my_pool, &my_packet, NX_TCP_PACKET,
                                NX_WAIT_FOREVER);

             /* Place "Hello_and_Goodbye" in the packet. */
             nx_packet_data_append(my_packet, "Hello_and_Goodbye",
                                   sizeof("Hello_and_Goodbye"), &my_pool,
                                   NX_WAIT_FOREVER);

             /* Send "Hello_and_Goodbye" to client. */
             nx_tcp_socket_send(&server_socket, my_packet, 200);

             /* Check for an error. */
             if (status)
             {

                /* Error, release the packet. */
                nx_packet_release(my_packet);
             }

             /* Now disconnect the server socket from the client. */
             nx_tcp_socket_disconnect(&server_socket, 200);
          }

          /* Unaccept the server socket. Note that unaccept is called even if
             disconnect or accept fails. */
          nx_tcp_server_socket_unaccept(&server_socket);

          /* Setup server socket for listening with this socket again. */
          nx_tcp_server_socket_relisten(&my_ip, 12, &server_socket);
     }
  
     /* We are now done so unlisten on server port 12. */
     nx_tcp_server_socket_unlisten(&my_ip, 12);

     /* Delete the server socket. */
     nx_tcp_socket_delete(&server_socket);
}
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_bytes_available"></a>nx_tcp_socket_bytes_available
取得可能なバイト数を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_bytes_available(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した TCP ソケットで取得可能なバイト数が取得されます。 TCP ソケットが既に接続されている必要があることに注意してください。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成され、接続されている TCP ソケットを指すポインター。
- **bytes_available** 使用可能なバイトの宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サービスが正常に実行されます。 読み取り可能なバイト数が呼び出し元に返されます。
- **NX_NOT_CONNECTED** (0x38) ソケットが接続状態ではありません。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the bytes available for retrieval on the specified socket. */
status = nx_tcp_socket_bytes_available(&my_socket,&bytes_available);

/* Is status = NX_SUCCESS, the available bytes is returned in
   bytes_available. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_create"></a>nx_tcp_socket_create
TCP クライアントまたはサーバー ソケットを作成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_create(
    NX_IP *ip_ptr, 
    NX_TCP_SOCKET *socket_ptr,
    CHAR *name, 
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG window_size,
    VOID (*urgent_data_callback)(NX_TCP_SOCKET *socket_ptr),
    VOID (*disconnect_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの TCP クライアントまたはサーバー ソケットを作成します。

> [!NOTE]  
> *アプリケーション コールバック ルーチンは、この IP インスタンスに関連付けられているスレッドから呼び出されます*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **socket_ptr** 新しい TCP ソケット制御ブロックを指すポインター。
- **name** この TCP ソケットのアプリケーション名。
- **type_of_service** 送信のためのサービスの種類を定義します。有効な値は次のとおりです。
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragment** IP のフラグメント化を許可するかどうかを指定します。 NX_FRAGMENT_OKAY** (0x0) が指定されている場合は、IP のフラグメント化が許可されます。 NX_DONT_FRAGMENT (0x4000) が指定されている場合は、IP のフラグメント化が無効になります。
- **time_to_live** このパケットが破棄されるまでに通過できるルーターの数を定義する 8 ビットの値を指定します。 既定値は NX_IP_TIME_TO_LIVE によって指定されます。
- **window_size** このソケットの受信キューで許可される最大バイト数を定義します
- **urgent_data_callback** 受信ストリームで緊急データが検出されるたびに呼び出されるアプリケーション関数。 この値が NX_NULL 場合は、緊急データが無視されます。
- **disconnect_callback** 接続の反対側のソケットによって切断が発行されるたびに呼び出されるアプリケーション関数。 この値が NX_NULL の場合は、切断コールバック関数が無効になります。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) TCP クライアント ソケットの作成に成功しました。
- **NX_OPTION_ERROR** (0x0A) サービスの種類、フラグメント、ウィンドウ サイズ、または有効期限オプションが無効です。
- **NX_PTR_ERROR** (0x07) IP またはソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Create a TCP client socket on the previously created IP instance,
   with normal delivery, IP fragmentation enabled, 0x80 time to
   live, a 200-byte receive window, no urgent callback routine, and
   the "client_disconnect" routine to handle disconnection initiated
   from the other end of the connection. */
status = nx_tcp_socket_create(&ip_0, &client_socket,
                             "Client Socket",
                             NX_IP_NORMAL, NX_FRAGMENT_OKAY,
                             0x80, 200, NX_NULL
                             client_disconnect);

/* If status is NX_SUCCESS, the client socket is created and ready
   to be bound. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_delete"></a>nx_tcp_socket_delete
TCP ソケットを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_delete(NX_TCP_SOCKET *socket_ptr);
```

### <a name="description"></a>説明

このサービスを使用すると、以前作成した TCP ソケットが削除されます。 そのソケットがまだバインドされているか接続されている場合、サービスはエラー コードを返します。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソケットの削除に成功しました。
- **NX_NOT_CREATED** (0x27) ソケットが作成されていませんでした。
- **NX_STILL_BOUND** (0x42) ソケットはまだバインドされています。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Delete a previously created TCP client socket. */
status = nx_tcp_socket_delete(&client_socket);

/* If status is NX_SUCCESS, the client socket is deleted. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect"></a>nx_tcp_socket_disconnect
クライアントとサーバーのソケット接続を切断します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_disconnect(
    NX_TCP_SOCKET *socket_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、確立されたクライアントまたはサーバーのソケット接続が切断されます。 サーバー ソケットを切断した場合、その後に受け入れ解除要求が発行される必要がありますが、切断されているクライアント ソケットは別の接続要求を受け入れられる状態のままになります。 切断プロセスをすぐに完了できない場合、指定された待機オプションに従ってサービスが中断されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。
- **wait_option** 切断を実行中のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットの切断に成功しました。
- **NX_NOT_CONNECTED** (0x38) 指定されたソケットは接続されていません。
- **NX_IN_PROGRESS** (0x37) 切断を実行中です。待機は指定されていませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい 

### <a name="example"></a>例 

```c
/* Disconnect from a previously established connection and wait a
   maximum of 400 timer ticks. */
status = nx_tcp_socket_disconnect(&client_socket, 400);

/* If status is NX_SUCCESS, the previously connected socket (either
   as a result of the client socket connect or the server accept) is
   disconnected. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_disconnect_complete_notify"></a>nx_tcp_socket_disconnect_complete_notify
TCP 切断完了通知コールバック関数をインストールします
 
### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_disconnect_complete_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_disconnect_complete_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明

このサービスを使用すると、ソケットの切断操作の完了後に呼び出されるコールバック関数が登録されます。 TCP ソケット切断完了コールバック関数は、オプション ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** を定義して NetX Duo が構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。
- **tcp_disconnect_complete_notify** インストールされるコールバック関数。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) コールバック関数が正常に登録されました。
- **NX_NOT_SUPPORTED** (0x4B) 拡張通知機能が NetX Duo ライブラリに組み込まれていません。NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Install the disconnect complete notify callback function. */
status = nx_tcp_socket_disconnect_complete_notify(&client_socket,
                                                  callback);
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_setnx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_establish_notify"></a>nx_tcp_socket_establish_notify
TCP 確立通知コールバック関数を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_establish_notify(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_establish_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明

このサービスを使用すると、TCP ソケットが接続を確立した後に呼び出されるコールバック関数が登録されます。 TCP ソケット確立コールバック関数は、オプション ***NX_ENABLE_EXTENDED_NOTIFY_SUPPORT*** を定義して NetX Duo が構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。
- **tcp_establish_notify** TCP 接続が確立された後に呼び出されるコールバック関数。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 通知関数が正常に設定されました。
- **NX_NOT_SUPPORTED** (0x4B) 拡張通知機能が NetX Duo ライブラリに組み込まれていません。 
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) TCP は、このアプリケーションで有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Set the function pointer "callback" as the notify function NetX
   Duo will call when the connection is in the established state. */
status = nx_tcp_socket_establish_notify(&client_socket, callback);
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_info_get"></a>nx_tcp_socket_info_get
TCP ソケット アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *tcp_packets_sent,
    ULONG *tcp_bytes_sent,
    ULONG *tcp_packets_received,
    ULONG *tcp_bytes_received,
    ULONG *tcp_retransmit_packets,
    ULONG *tcp_packets_queued,
    ULONG *tcp_checksum_errors,
    ULONG *tcp_socket_state,
    ULONG *tcp_transmit_queue_depth,
    ULONG *tcp_transmit_window,
    ULONG *tcp_receive_window);
```
### <a name="description"></a>説明

このサービスでは、指定された TCP ソケット インスタンスの TCP ソケット アクティビティに関する情報を取得します。

> [!NOTE]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。
- **tcp_packets_sent** ソケットで送信された TCP パケットの合計数の宛先を指すポインター。
- **tcp_bytes_sent** ソケットで送信された TCP バイトの合計数の宛先を指すポインター。
- **tcp_packets_received** ソケットで受信した TCP パケットの合計数の宛先を指すポインター。
- **tcp_bytes_received** ソケットで受信した TCP バイトの合計数の宛先を指すポインター。
- **tcp_retransmit_packets** TCP パケット再送信の合計数の宛先を指すポインター。
- **tcp_packets_queued** ソケットでキューに入れられた TCP パケットの合計数の宛先を指すポインター。
- **tcp_checksum_errors** ソケットでチェックサム エラーが発生している TCP パケットの合計数の宛先を指すポインター。
- **tcp_socket_state** ソケットの現在の状態の宛先を指すポインター。
- **tcp_transmit_queue_depth** ACK を待機してキューに入れられたままになっている送信パケットの合計数の宛先を指すポインター。
- **tcp_transmit_window** 現在の送信ウィンドウ サイズの宛先を指すポインター。
- **tcp_receive_window** 現在の受信ウィンドウ サイズの宛先を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) TCP ソケット情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。 
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve TCP socket information from previously created
   socket_0.*/
status = nx_tcp_socket_info_get(&socket_0,
                                &tcp_packets_sent,
                                &tcp_bytes_sent,
                                &tcp_packets_received,
                                &tcp_bytes_received,
                                &tcp_retransmit_packets,
                                &tcp_packets_queued,
                                &tcp_checksum_errors,
                                &tcp_socket_state,
                                &tcp_transmit_queue_depth,
                                &tcp_transmit_window,
                                &tcp_receive_window);

/* If status is NX_SUCCESS, TCP socket information was retrieved. */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_mss_get"></a>nx_tcp_socket_mss_get
ソケットの MSS を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_mss_get(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG *mss);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したソケットのローカルの最大セグメント サイズ (MSS) が取得されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成されたソケットを指すポインター。
- **mss** MSS を返す宛先。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) MSS の取得に成功しました。
- **NX_PTR_ERROR** (0x07) ソケットまたは MSS 宛先ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the MSS for the socket "my_socket". */
status = nx_tcp_socket_mss_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket's current MSS value. */
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_peer_get"></a>nx_tcp_socket_mss_peer_get
ピア TCP ソケットの MSS を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_mss_peer_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *mss);
```
### <a name="description"></a>説明

このサービスを使用すると、ピア ソケットによってアドバタイズされた最大セグメント サイズ (MSS) が取得されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成され、接続されているソケットを指すポインター。
- **mss** MSS を返す宛先。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ピア MSS の取得に成功しました。
- **NX_PTR_ERROR** (0x07) ソケットまたは MSS 宛先ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the MSS of the connected peer to the socket "my_socket". */
status = nx_tcp_socket_mss_peer_get(&my_socket, &mss_value);

/* If status is NX_SUCCESS, the "mss_value" variable contains the
   socket peer’s advertised MSS value. */
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_mss_set"></a>nx_tcp_socket_mss_set
ソケットの MSS を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_mss_set(
    NX_TCP_SOCKET *socket_ptr, 
    ULONG mss);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したソケットの最大セグメント サイズ (MSS) が設定されます。 MSS 値は、ネットワーク インターフェイスの IP MTU の範囲内で指定して、IP ヘッダーと TCP ヘッダーのための余地を残す必要があることにご注意ください。

このサービスは、TCP ソケットで接続プロセスが開始される前に使用する必要があります。 TCP 接続が確立された後にこのサービスを使用した場合、新しい値は接続に影響しません。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成されたソケットを指すポインター。
- **mss** 設定する MSS の値。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) MSS の設定に成功しました。
- **NX_SIZE_ERROR** (0x09) 指定された MSS 値が大きすぎます。
- **NX_NOT_CONNECTED** (0x38) TCP 接続が確立されていません 
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_CALLER_ERROR** (0x11) 呼び出し元がスレッドでも初期化でもありません。

### <a name="allowed-from"></a>許可元

初期化とスレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Set the MSS of the socket "my_socket" to 1000 bytes. */
status = nx_tcp_socket_mss_set(&my_socket, 1000);

/* If status is NX_SUCCESS, the MSS of "my_socket" is 1000 bytes. */
```

### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_peer_info_get"></a>nx_tcp_socket_peer_info_get
ピア TCP ソケットに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_peer_info_get(
    NX_TCP_SOCKET *socket_ptr,
    ULONG *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>説明

このサービスでは、IPv4 ネットワーク経由で接続されている TCP ソケットのピア IP アドレスとポート情報を取得します。 これに相当し、IPv6 ネットワークもサポートするサービスは ***nxd_tcp_socket_peer_info_get*** です。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケットを指すポインター。
- **peer_ip_address** ピア IP アドレスの宛先を指すポインター (ホストのバイト順)。
- **peer_port** ピア ポート番号の宛先を指すポインター (ホストのバイト順)。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) サービスが正常に実行されます。 ピア IP アドレスとポート番号が呼び出し元に返されます。
- **NX_NOT_CONNECTED** (0x38) ソケットが接続状態ではありません。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Obtain peer IP address and port on the specified TCP socket. */
status = nx_tcp_socket_peer_info_get(&my_socket, &peer_ip_address,
                                     &peer_port);

/* If status = NX_SUCCESS, the data was successfully obtained. */
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_queue_depth_notify_set"></a>nx_tcp_socket_queue_depth_notify_set
TCP 送信キュー通知関数を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_queue_depth_notify_set(
              NX_TCP_SOCKET *socket_ptr,
              VOID(*tcp_socket_queue_depth_notify)(NX_TCP_SOCKET *));
```
### <a name="description"></a>説明

このサービスでは、アプリケーションによって指定された送信キューの深度更新通知関数が設定されます。指定されたソケットで送信キューからパケットが解放されて、キューの深度の制限超過が収まったと判別されるたびに、これが呼び出されます。 キューの深度が原因でアプリケーションが送信時にブロックされる場合、このコールバック関数は、送信を再開してよいことをアプリケーションに通知する役割を果たします。 このサービスは、オプション ***NX_ENABLE_TCP_QUEUE_DEPTH_UPDATE_NOTIFY*** を定義して NetX Duo ライブラリが構築されている場合にのみ使用できます。

### <a name="parameters"></a>パラメーター 

- **socket_ptr** ソケット構造体へのポインター。 
- **tcp_socket_queue_depth_notify** インストールする通知関数。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 通知関数が正常にインストールされました。
- **NX_NOT_SUPPORTED** (0x4B) TCP ソケットのキュー深度通知機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) ソケット制御ブロックまたは通知関数へのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
VOID tcp_socket_queue_depth_notify(NX_TCP_SOCKET *socket_ptr)
{
   /* Notify the application to resume sending. */

}
/* Install the TCP transmit queue notify function .*/
status = nxd_tcp_socket_queue_depth_notify_set(&tcp_socket,
                                  tcp_socket_queue_depth_notify);

/* If status == NX_SUCCESS, the callback function is successfully
   installed. */
```

### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_receive"></a>nx_tcp_socket_receive
TCP ソケットからデータを受信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_receive(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスでは、指定されたソケットから TCP データを受信します。 指定されたソケットでキューに入れられたデータが存在しない場合は、指定された待機オプションに基づいて呼び出し元が中断されます。

> [!CAUTION]  
> *NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします*。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケット インスタンスを指すポインター。
- **packet_ptr** TCP パケット ポインターへのポインター。
- **wait_option** このソケットで現在キューに入れられたデータが存在しない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ソケットのデータの受信に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがまだバインドされていません。
- **NX_NO_PACKET** (0x01) 受信したデータはありません。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_NOT_CONNECTED** (0x38) ソケットの接続が解除されています。
- **NX_PTR_ERROR** (0x07) ソケットまたはパケットの戻りポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Receive a packet from the previously created and connected TCP
   client socket. If no packet is available, wait for 200 timer
   ticks before giving up. */
status = nx_tcp_socket_receive(&client_socket, &packet_ptr, 200);

/* If status is NX_SUCCESS, the received packet is pointed to by
   "packet_ptr". */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_receive_notify"></a>nx_tcp_socket_receive_notify
受信したパケットをアプリケーションに通知します

### <a name="prototype"></a>プロトタイプ   

```c
UINT nx_tcp_socket_receive_notify(
    NX_TCP_SOCKET *socket_ptr, 
    VOID (*tcp_receive_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明 

このサービスを使用すると、アプリケーションによって指定されたコールバック関数を使用して、受信通知関数ポインターを構成できます。 このコールバック関数は、ソケットで 1 つ以上のパケットを受信するたびに呼び出されます。 NX_NULL ポインターが指定されている場合、通知関数は無効になります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** TCP ソケットを指すポインター。
- **tcp_receive_notify** ソケットで 1 つ以上のパケットを受信したときに呼び出されるアプリケーション コールバック関数ポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットの受信の通知に成功しました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Setup a receive packet callback function for the "client_socket"
   socket. */
status = nx_tcp_socket_receive_notify(&client_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever one or more packets are received for
   "client_socket". */
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_send"></a>nx_tcp_socket_send
TCP ソケットを介してデータを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_send(
    NX_TCP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に接続された TCP ソケットを介して TCP データが送信されます。 受信側の最後に公開されたウィンドウのサイズがこの要求よりも小さい場合、サービスは、指定された待機オプションに基づいて、必要に応じて中断します。 このサービスにより、MSS を超えるパケット データが IP 層に送信されないことが保証されます。 

> [!WARNING]  
> *エラーが返されない限り、この呼び出しの後にアプリケーションでパケットを解放することはできません。これを行うと、送信後にネットワーク ドライバーでもパケットの解放が試みられるため、予期しない結果が発生します*。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に接続された TCP ソケット インスタンスを指すポインター。
- **packet_ptr** TCP データ パケット ポインター。
- **wait_option** 要求が受信側のウィンドウ サイズより大きい場合に、サービスがどのように動作するかを定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソケットの送信に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりませんでした。
- **NX_NOT_CONNECTED** (0x38) ソケットの接続が解除されています。
- **NX_WINDOW_OVERFLOW** (0x39) 要求が、受信側の公開されたウィンドウ サイズ (バイト単位) を超えています。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_INVALID_PACKET** (0x12) パケットが割り当てられていません。
- **NX_TX_QUEUE_DEPTH** (0x49) 最大転送キューの深さに達しました。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Send a packet out on the previously created and connected TCP
   socket. If the receive window on the other side of the connection
   is less than the packet size, wait 200 timer ticks before giving
   up. */
status = nx_tcp_socket_send(&client_socket, packet_ptr, 200);

/* If status is NX_SUCCESS, the packet has been sent! */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_state_wait"></a>nx_tcp_socket_state_wait
TCP ソケットが特定の状態になるのを待機します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_state_wait(
    NX_TCP_SOCKET *socket_ptr,
    UINT desired_state,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスは、ソケットが目的の状態になるまで待機します。 ソケットが目的の状態でない場合、指定された待機オプションに従ってサービスが中断されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に接続された TCP ソケット インスタンスを指すポインター。
- **desired_state** 目的の TCP 状態。 有効な TCP ソケットの状態は、次のように定義されます。
    - **NX_TCP_CLOSED** (0x01)
    - **NX_TCP_LISTEN_STATE** (0x02)
    - **NX_TCP_SYN_SENT** (0x03)
    - **NX_TCP_SYN_RECEIVED** (0x04)
    - **NX_TCP_ESTABLISHED** (0x05)
    - **NX_TCP_CLOSE_WAIT** (0x06)
    - **NX_TCP_FIN_WAIT_1** (0x07)
    - **NX_TCP_FIN_WAIT_2** (0x08)
    - **NX_TCP_CLOSING** (0x09)
    - **NX_TCP_TIMED_WAIT** (0x0A)
    - **NX_TCP_LAST_ACK** (0x0B)
- **wait_option** 要求された状態が存在しない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFF)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 状態の待機に成功しました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_NOT_SUCCESSFUL** (0x43) 指定された待機時間内に状態が存在しませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_OPTION_ERROR** (0x0A) 目的のソケットの状態が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Wait 300 timer ticks for the previously created socket to enter
   the established state in the TCP state machine. */
status = nx_tcp_socket_state_wait(&client_socket,
                                  NX_TCP_ESTABLISHED, 300);

/* If status is NX_SUCCESS, the socket is now in the established
   state! */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nxd_tcp_client_socket_connect
- nxd_tcp_socket_peer_info_get

## <a name="nx_tcp_socket_timed_wait_callback"></a>nx_tcp_socket_timed_wait_callback
時間指定された待機状態のコールバックをインストールします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_timed_wait_callback(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_timed_wait_callback)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明

このサービスを使用すると、TCP ソケットが時間指定された待機状態になったときに呼び出されるコールバック関数が登録されます。 このサービスを使用するには、オプション ***NX_ENABLE_EXTENDED_NOTIFY*** を定義して NetX Duo ライブラリを構築する必要があります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に接続されたクライアントまたはサーバー ソケット インスタンスを指すポインター。
- **tcp_timed_wait_callback** 時間指定された待機コールバック関数

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) コールバック関数ソケットが正常に登録されました。
- **NX_NOT_SUPPORTED** (0x4B) この拡張通知機能を有効にせずに NetX Duo ライブラリが構築されています。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Install the timed wait callback function */
nx_tcp_socket_timed_wait_callback(&client_socket, callback);
```

### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_transmit_configure
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_transmit_configure"></a>nx_tcp_socket_transmit_configure
ソケットの送信パラメーターを構成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_transmit_configure(
    NX_TCP_SOCKET *socket_ptr,
    ULONG max_queue_depth,
    ULONG timeout,
    ULONG max_retries,
    ULONG timeout_shift);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した TCP ソケットのさまざまな送信パラメーターを構成できます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** TCP ソケットを指すポインター。
- **max_queue_depth** 送信するためにキューに入れることができるパケットの最大数。
- **timeout** パケットが再度送信される前に ACK が待機する ThreadX タイマー ティック数。
- **max_retries** 許可される最大再試行回数。
- **timeout_shift** 再試行のたびにタイムアウトをシフトする値。 値が 0 の場合は、次の再試行との間のタイムアウトは同じになります。 値が 1 の場合は、再試行の間のタイムアウトは 2 倍になります。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 送信ソケットの構成に成功しました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_OPTION_ERROR** (0x0a) キューの深度オプションが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Configure the "client_socket" for a maximum transmit queue depth of
   12, 100 tick timeouts, a maximum of 20 retries, and a timeout double
   on each successive retry. */
status = nx_tcp_socket_transmit_configure(&client_socket,12,100,20,1);

/* If status is NX_SUCCESS, the socket’s transmit retry has been
   configured. */
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_window_update_notify_set

## <a name="nx_tcp_socket_window_update_notify_set"></a>nx_tcp_socket_window_update_notify_set
アプリケーションにウィンドウ サイズの更新を通知します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_tcp_socket_window_update_notify_set(
    NX_TCP_SOCKET *socket_ptr,
    VOID (*tcp_window_update_notify)(NX_TCP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明

このサービスを使用すると、ソケット ウィンドウ更新コールバック ルーチンがインストールされます。 このルーチンは、指定されたソケットがリモート ホストのウィンドウ サイズが増加したことを示すパケットを受信するたびに自動的に呼び出されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケットを指すポインター。
- **tcp_window_update_notify** ウィンドウ サイズが変更されたときに呼び出されるコールバック ルーチン。 NULL 値を指定すると、ウィンドウの変更更新は無効になります。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) コールバック ルーチンがソケットにインストールされました。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) TCP 機能が有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Set the function pointer to the windows update callback after creating the
   socket. */
status = nx_tcp_socket_window_update_notify_set(&data_socket,
                                                my_windows_update_callback);

/* Define the window callback function in the host application. */
void my_windows_update_callback(&data_socket)
{

/* Process update on increase TCP transmit socket window size. */
   return;
}
```
### <a name="see-also"></a>参照

- nx_tcp_enable
- nx_tcp_socket_create
- nx_tcp_socket_disconnect_complete_notify
- nx_tcp_socket_establish_notify
- nx_tcp_socket_mss_get
- nx_tcp_socket_mss_peer_get
- nx_tcp_socket_mss_set
- nx_tcp_socket_peer_info_get
- nx_tcp_socket_queue_depth_notify_set
- nx_tcp_socket_receive_notify
- nx_tcp_socket_timed_wait_callback
- nx_tcp_socket_transmit_configure

## <a name="nx_udp_enable"></a>nx_udp_enable
NetX Duo の UDP コンポーネントを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、NetX Duo のユーザー データグラム プロトコル (UDP) コンポーネントを有効にします。 有効にすると、アプリケーションで UDP データグラムを送受信できるようになります。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) UDP の有効化に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_ALREADY_ENABLED** (0x15) このコンポーネントは既に有効になっています。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable UDP on the previously created IP instance. */
status = nx_udp_enable(&ip_0);

/* If status is NX_SUCCESS, UDP is now enabled on the specified IP
   instance. */
```
### <a name="see-also"></a>参照

- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_free_port_find"></a>nx_udp_free_port_find
使用可能な次の UDP ポートを検索します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_free_port_find(
    NX_IP *ip_ptr, 
    UINT port,
    UINT *free_port_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、アプリケーションで指定されているポート番号を起点として、空いている UDP ポート (バインドされていない) の検索が行われます。 この検索ロジックは、検索が最大ポート値 0xFFFF に到達すると、ラップアラウンドします。 検索が成功すると、free_port_ptr によってポイントされている変数に空きポートが返されます。

> [!WARNING]  
> *このサービスが別のスレッドから呼び出されて、同じポートが返される場合があります。このような競合状態を回避するには、アプリケーションでこのサービスと実際のソケット バインドをミューテックスの保護下に置くことが必要になる場合があります*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **port** 検索を開始するポート番号 (1 から 0xFFFF)。
- **free_port_ptr** 宛先の空きポートの戻り変数を指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 空きポートの検索に成功しました。
- **NX_NO_FREE_PORTS** (0x45) 空きポートが見つかりませんでした。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。
- **NX_INVALID_PORT** (0x46) 指定されたポート番号が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Locate a free UDP port, starting at port 12, on a previously
   created IP instance. */
status = nx_udp_free_port_find(&ip_0, 12, &free_port);

/* If status is NX_SUCCESS pointer, "free_port" identifies the next
   free UDP port on the IP instance. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_info_get"></a>nx_udp_info_get
UDP アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_info_get(
    NX_IP *ip_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_invalid_packets,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの UDP アクティビティに関する情報を取得します。

> [!IMPORTANT]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **udp_packets_sent** 送信された UDP パケットの合計数の宛先を指すポインター。
- **udp_bytes_sent** 送信された UDP バイトの合計数の宛先を指すポインター。
- **udp_packets_received** 受信した UDP パケットの合計数の宛先を指すポインター。
- **udp_bytes_received** 受信した UDP バイトの合計数の宛先を指すポインター。
- **udp_invalid_packets** 無効な UDP パケットの合計数の宛先を指すポインター。
- **udp_receive_packets_dropped** 破棄された UDP 受信パケットの合計数の宛先を指すポインター。
- **udp_checksum_errors** チェックサム エラーが発生している UDP パケットの合計数の宛先を指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) UDP 情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve UDP information from previously created IP Instance
   ip_0. */
status = nx_udp_info_get(&ip_0, &udp_packets_sent,
                         &udp_bytes_sent,
                         &udp_packets_received,
                         &udp_bytes_received,
                         &udp_invalid_packets,
                         &udp_receive_packets_dropped,
                         &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP information was retrieved. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_packet_info_extract"></a>nx_udp_packet_info_extract
UDP パケットからネットワーク パラメーターを抽出します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>説明

このサービスでは、受信インターフェイスで受信したパケットから IPv4 アドレス、ピア ポート番号、プロトコルの種類 (このサービスでは常に UDP の種類が返されます) などのネットワーク パラメーターを抽出します。 IPv4 または IPv6 ネットワークから受信したパケットに関する情報を取得するには、アプリケーションでサービス ***nxd_udp_packet_info_extract*** を使用する必要があります。

### <a name="parameters"></a>パラメーター

- **packet_ptr** パケットを指すポインター。
- **ip_address** 送信元 IP アドレスを指すポインター。
- **protocol** プロトコル (UDP) を指すポインター。
- **port** 送信者のポート番号を指すポインター。
- **interface_index** 受信インターフェイス インデックスを指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) パケット インターフェイス データが正常に抽出されました。
- **NX_INVALID_PACKET** (0x12) パケットに IPv4 フレームが含まれていません。
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Extract network data from UDP packet interface.*/
status = nx_udp_packet_info_extract(packet_ptr, &ip_address,
                                     &protocol, &port,
                                     &interface_index);

/* If status is NX_SUCCESS packet data was successfully
   retrieved. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bind"></a>nx_udp_socket_bind
UDP ソケットを UDP ポートにバインドします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_bind(
    NX_UDP_SOCKET *socket_ptr, 
    UINT port,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、以前作成した UDP ソケットが、指定した UDP ポートにバインドされます。 有効な UDP ソケットの範囲は 0 から 0xFFFF です。 要求されたポート番号が別のソケットにバインドされている場合、このサービスは、そのポート番号からソケットがバインド解除されるまで、指定された時間待機します。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスへのポインター。
- **port** バインド先のポート番号** (1 から 0xFFFF)。 ポート番号が NX_ANY_PORT** (0x0000) の場合、IP インスタンスによって次の空きポートが検索されて、バインドに使用されます。
- **wait_option** ポートが既に別のソケットにバインドされている場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ソケットのバインドに成功しました。
- **NX_ALREADY_BOUND** (0x22) このソケットは既に別のポートにバインドされています。
- **NX_PORT_UNAVAILABLE** (0x23) ポートは既に別のソケットにバインドされています。
- **NX_NO_FREE_PORTS** (0x45) 空きポートがありません。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_INVALID_PORT** (0x46) 指定されたポートが無効です。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Bind the previously created UDP socket to port 12 on the
   previously created IP instance. If the port is already bound,
   wait for 300 timer ticks before giving up. */
status = nx_udp_socket_bind(&udp_socket, 12, 300);

/* If status is NX_SUCCESS, the UDP socket is now bound to
   port 12.*/
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_bytes_available"></a>nx_udp_socket_bytes_available
取得可能なバイト数を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_bytes_available(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *bytes_available);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した UDP ソケットでの受信に使用可能なバイト数が取得されます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケットを指すポインター。
- **bytes_available** 使用可能なバイトの宛先を指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 使用可能なバイト数の取得に成功しました。
- **NX_NOT_SUCCESSFUL** (0x43) ソケットがポートにバインドされていません。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **NX_NOT_ENABLED** (0x14) UDP 機能が有効になっていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the bytes available for retrieval from the UDP socket. */
status = nx_udp_socket_bytes_available(&my_socket,
                                       &bytes_available);

/* If status == NX_SUCCESS, the number of bytes was successfully
   retrieved.*/
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_disable"></a>nx_udp_socket_checksum_disable
UDP ソケットのチェックサムを無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_checksum_disable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した UDP ソケットでパケットを送受信するためのチェックサム ロジックが無効になります。 チェックサム ロジックが無効になっている場合、このソケットを介して送信されるすべてのパケットの UDP ヘッダーのチェックサム フィールドに値 0 が読み込まれます。 UDP ヘッダーのゼロ値のチェックサム値は、このパケットのチェックサムが計算されていないことを受信者に示す働きをします。

UDP パケットの受信と送信で、それぞれ **NX_DISABLE_UDP_RX_CHECKSUM** および **NX_DISABLE_UDP_TX_CHECKSUM** が定義されている場合は、この影響はないことにもご注意ください。

このサービスは、IPv6 ネットワーク上のパケットには影響しません。これは、IPv6 では UDP チェックサムが必須であるためです。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットのチェックサムの無効化に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがバインドされていません。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Disable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_disable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will not have a checksum
   calculated. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_checksum_enable"></a>nx_udp_socket_checksum_enable
UDP ソケットのチェックサムを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_checksum_enable(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した UDP ソケットでパケットを送受信するためのチェックサム ロジックが有効になります。 このチェックサムでは、UDP データ領域全体と擬似 IP ヘッダーが対象になります。

また、UDP パケットの受信と送信で、それぞれ **NX_DISABLE_UDP_RX_CHECKSUM** および **NX_DISABLE_UDP_TX_CHECKSUM** が定義されている場合は、この影響はないことにもご注意ください。

このサービスは、IPv6 ネットワーク上のパケットには影響しません。 UDP チェックサムは IPv6 では必須です。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ソケットのチェックサムの有効化に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがバインドされていません。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable the UDP checksum logic for packets sent on this socket. */
status = nx_udp_socket_checksum_enable(&udp_socket);

/* If status is NX_SUCCESS, outgoing packets will have a checksum
   calculated. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_create"></a>nx_udp_socket_create
UDP ソケットを作成します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_create(
    NX_IP *ip_ptr,
    NX_UDP_SOCKET *socket_ptr, 
    CHAR *name,
    ULONG type_of_service, 
    ULONG fragment,
    UINT time_to_live, 
    ULONG queue_maximum);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP インスタンスの UDP ソケットが作成されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **socket_ptr** 新しい UDP ソケット制御ブロックを指すポインター。
- **name** この UDP ソケットのアプリケーション名。
- **type_of_service** 送信のためのサービスの種類を定義します。有効な値は次のとおりです。
    - **NX_IP_NORMAL** (0x00000000)
    - **NX_IP_MIN_DELAY** (0x00100000)
    - **NX_IP_MAX_DATA** (0x00080000)
    - **NX_IP_MAX_RELIABLE** (0x00040000)
    - **NX_IP_MIN_COST** (0x00020000)
- **fragment** IP のフラグメント化を許可するかどうかを指定します。 NX_FRAGMENT_OKAY (0x0) が指定されている場合は、IP のフラグメント化が許可されます。 NX_DONT_FRAGMENT (0x4000) が指定されている場合は、IP のフラグメント化が無効になります。
- **time_to_live** このパケットが破棄されるまでに通過できるルーターの数を定義する 8 ビットの値を指定します。 既定値は NX_IP_TIME_TO_LIVE によって指定されます。
- **queue_maximum** このソケットのキューに入れることができる UDP データグラムの最大数を定義します。 キューの上限に達すると、新しいパケットを受信するたびに、最も古い UDP パケットが解放されます。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) UDP ソケットの作成に成功しました。
- **NX_OPTION_ERROR** (0x0A) サービスの種類、フラグメント、または有効期限オプションが無効です。
- **NX_PTR_ERROR** (0x07) IP またはソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Create a UDP socket with a maximum receive queue of 30 packets.*/
status = nx_udp_socket_create(&ip_0, &udp_socket, "Sample UDP Socket",
                              NX_IP_NORMAL, NX_FRAGMENT_OKAY, 0x80,
                              30);

/* If status is NX_SUCCESS, the new UDP socket has been created and
   is ready for binding. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_delete"></a>nx_udp_socket_delete
UDP ソケットを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_delete(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、以前に作成された UDP ソケットが削除されます。 ソケットがポートにバインドされている場合は、最初にソケットをバインド解除する必要があります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットの削除に成功しました。
- **NX_STILL_BOUND** (0x42) ソケットはまだバインドされています。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Delete a previously created UDP socket. */
status = nx_udp_socket_delete(&udp_socket);

/* If status is NX_SUCCESS, the previously created UDP socket has
   been deleted. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_info_get"></a>nx_udp_socket_info_get
UDP ソケット アクティビティに関する情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_info_get(
    NX_UDP_SOCKET *socket_ptr,
    ULONG *udp_packets_sent,
    ULONG *udp_bytes_sent,
    ULONG *udp_packets_received,
    ULONG *udp_bytes_received,
    ULONG *udp_packets_queued,
    ULONG *udp_receive_packets_dropped,
    ULONG *udp_checksum_errors);
```
### <a name="description"></a>説明

このサービスでは、指定された UDP ソケット インスタンスの UDP ソケット アクティビティに関する情報を取得します。

> [!IMPORTANT]  
> *宛先ポインターが NX_NULL の場合、その特定の情報は呼び出し元に返されません*。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスへのポインター。
- **udp_packets_sent** ソケットで送信された UDP パケットの合計数の宛先へのポインター。
- **udp_bytes_sent** ソケットで送信された UDP バイトの合計数の宛先を指すポインター。
- **udp_packets_received** ソケットで受信した UDP パケットの合計数の宛先を指すポインター。
- **udp_bytes_received** ソケットで受信した UDP バイトの合計数の宛先を指すポインター。
- **udp_packets_queued** ソケットでキューに入れられた UDP パケットの合計数の宛先を指すポインター。
- **udp_receive_packets_dropped** キューのサイズを超えたため、ソケットに対して破棄された UDP 受信パケットの合計数の宛先を指すポインター。
- **tcp_checksum_errors** ソケットでチェックサム エラーが発生している UDP パケットの合計数の宛先を指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) UDP ソケット情報の取得に成功しました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Retrieve UDP socket information from socket 0.*/
status = nx_udp_socket_info_get(&socket_0,
                                &udp_packets_sent,
                                &udp_bytes_sent,
                                &udp_packets_received,
                                &udp_bytes_received,
                                &udp_queued_packets,
                                &udp_receive_packets_dropped,
                                &udp_checksum_errors);

/* If status is NX_SUCCESS, UDP socket information was retrieved.*/
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_port_get"></a>nx_udp_socket_port_get
UDP ソケットにバインドされているポート番号を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_port_get(
    NX_UDP_SOCKET *socket_ptr,
    UINT *port_ptr);
```
### <a name="description"></a>説明

このサービスでは、ソケットに関連付けられているポート番号を取得します。これは、ソケットのバインド時に NX_ANY_PORT が指定された場合に NetX Duo によって割り当てられたポートを見つけるのに便利です。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。
- **port_ptr** 戻りポート番号の宛先を指すポインター。 有効なポート番号は (1 から 0xFFFF) です。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットのバインドに成功しました。
- **NX_NOT_BOUND** (0x24) このソケットはポートにバインドされていません。
- **NX_PTR_ERROR** (0x07) ソケット ポインターまたはポートの戻りポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Get the port number of created and bound UDP socket. */
status = nx_udp_socket_port_get(&udp_socket, &port);

/* If status is NX_SUCCESS, the port variable contains the port this
   socket is bound to. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive"></a>nx_udp_socket_receive
UDP ソケットからデータグラムを受信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_receive(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET **packet_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスを使用すると、指定したソケットから UDP データグラムを受信できます。 指定されたソケットでキューに入れられたデータグラムが存在しない場合は、指定された待機オプションに基づいて呼び出し元が中断されます。

> [!CAUTION]  
> *NX_SUCCESS が返された場合は、そのアプリケーションが、不要になった受信パケットを解放する役割を果たします*。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。
- **packet_ptr** UDP データグラム パケット ポインターを指すポインター。
- **wait_option** このソケットで現在キューに入れられたデータグラムが存在しない場合のサービスの動作を定義します。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) ソケットの受信に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。
- **NX_NO_PACKET** (0x01) 受信する UDP データグラムがありませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_PTR_ERROR** (0x07) ソケットまたはパケットの戻りポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Receive a packet from a previously created and bound UDP socket.
   If no packets are currently available, wait for 500 timer ticks
   before giving up. */
status = nx_udp_socket_receive(&udp_socket, &packet_ptr, 500);

/* If status is NX_SUCCESS, the received UDP packet is pointed to by
   packet_ptr. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_receive_notify"></a>nx_udp_socket_receive_notify
受信した各パケットをアプリケーションに通知します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_receive_notify(
    NX_UDP_SOCKET *socket_ptr,
    VOID (*udp_receive_notify)(NX_UDP_SOCKET *socket_ptr));
```
### <a name="description"></a>説明 

このサービスでは、受信通知関数ポインターを、アプリケーションによって指定されたコールバック関数に設定します。 そのようにすると、そのソケットでパケットが受信されるたびに、このコールバック関数が呼び出されます。 NX_NULL ポインターが指定されている場合、この受信通知関数は無効になります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** UDP ソケットを指すポインター。
- **udp_receive_notify** ソケットでパケットを受信したときに呼び出されるアプリケーション コールバック関数ポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケット受信通知関数が正常に設定されました。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、およびISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Setup a receive packet callback function for the "udp_socket"
   socket. */
status = nx_udp_socket_receive_notify(&udp_socket,
                                      my_receive_notify);

/* If status is NX_SUCCESS, NetX Duo will call the function named
   "my_receive_notify" whenever a packet is received for
   "udp_socket". */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_send"></a>nx_udp_socket_send
UDP データグラムを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address, 
    UINT port);
```
### <a name="description"></a>説明

このサービスでは、以前に作成され、バインドされた IPv4 ネットワーク用の UDP ソケットを介して UDP データグラムを送信します。 NetX Duo では、宛先 IP アドレスに基づいて、適切なローカル IP アドレスを発信元アドレスとして検索します。 特定のインターフェイスおよび発信元 IP アドレスを指定するには、アプリケーションで **nxd_udp_socket_source_send** サービスを使用する必要があります。

このサービスは、UDP データグラムが正常に送信されたかどうかに関係なく、直ちに返されることにご注意ください。 NetX Duo (IPv4/IPv6) でこれに相当するサービスは、***nxd_udp_socket_send*** です。

このソケットは、ローカル ポートにバインドされている必要があります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター
- **packet_ptr** UDP データグラム パケットのポインター。
- **ip_address** 宛先 IPv4 アドレス。
- **port** 1 から 0xFFFF の範囲の有効な宛先ポート番号 (ホストのバイト順)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) UDP ソケットの送信に成功しました
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていません
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_IP_ADDRESS_ERROR** (0x21) サーバー IP アドレスが無効です
- **NX_UNDERFLOW** (0x02) パケット内の UDP ヘッダーに十分な領域がありません
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) UDP が有効になっていません
- **NX_INVALID_PORT** (0x46) ポート番号が有効な範囲内ではありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
ULONG server_address;

/* Set the UDP Client IP address. */
server_address = IP_ADDRESS(1,2,3,5);

/* Send a packet to the UDP server at server_address on port 12. */
status = nx_udp_socket_send(&client_socket, packet_ptr,
                            server_address, 12);

/* If status == NX_SUCCESS, the application successfully transmitted
   the packet out the UDP socket to its peer. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_source_send"></a>nx_udp_socket_source_send
UDP ソケット経由でデータグラムを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    ULONG ip_address,
    UINT port,
    UINT address_index);
```
### <a name="description"></a>説明

このサービスを使用すると、指定した IP アドレスを発信元アドレスとするネットワーク インターフェイスを経由して、以前に作成され、バインドされた UDP ソケットを介して UDP データグラムが送信されます。 このサービスは、UDP データグラムが正常に送信されたかどうかに関係なく、直ちに返されることにご注意ください。 ***nxd_udp_socket_source_send*** は、IPv4 および IPv6 の両方のネットワークで機能します。

### <a name="parameters"></a>パラメーター 

- **socket_ptr** パケットを送信するソケット。
- **packet_ptr** 送信するパケットを指すポインター。
- **ip_address** パケットを送信する宛先 IP アドレス。
- **port** 宛先ポート。
- **address_index** パケットを送信するインターフェイスに関連付けられているアドレスのインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットが正常に送信されました。
- **NX_NOT_BOUND** (0x24) ソケットがポートにバインドされていません。
- **NX_IP_ADDRESS_ERROR** (0x21) IP アドレスが無効です。
- **NX_NOT_ENABLED** (0x14) UDP 処理が有効になっていません。
- **NX_PTR_ERROR** (0x07) ポインターが無効です。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_UNDERFLOW** (0x02) パケットのプリペンド ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_INTERFACE** (0x4C) アドレス インデックスが無効です。
- **NX_INVALID_PORT** (0x46) ポート番号がポート番号の最大値を超えています。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define ADDRESS_INDEX 1

/* Send packet out on port 80 to the specified destination IP on the
   interface at index 1 in the IP task interface list. */
status = nx_udp_socket_source_send(socket_ptr, packet_ptr,
                                   destination_ip, 80,
                                   ADDRESS_INDEX);

/* If status is NX_SUCCESS packet was successfully transmitted. */
```

### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_socket_unbind"></a>nx_udp_socket_unbind
UDP ポートから UDP ソケットをバインド解除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_socket_unbind(NX_UDP_SOCKET *socket_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、UDP ソケットと UDP ポート間のバインドが解除されます。 受信キューに格納されている受信パケットは、バインド解除操作の一部として解放されます。

他のスレッドが非バインド ポートに別のソケットをバインドするために待機している場合は、中断されている最初のスレッドが新しい非バインド ポートにバインドされます。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ソケットのバインド解除に成功しました。
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていませんでした。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) このコンポーネントは有効になっていません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

はい

### <a name="example"></a>例

```c
/* Unbind the previously bound UDP socket. */
status = nx_udp_socket_unbind(&udp_socket);

/* If status is NX_SUCCESS, the previously bound socket is now
   unbound. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nx_udp_source_extract"></a>nx_udp_source_extract
UDP データグラムから IP と送信ポートを抽出します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nx_udp_source_extract(
    NX_PACKET *packet_ptr,
    ULONG *ip_address, 
    UINT *port);
```
### <a name="description"></a>説明

このサービスでは、指定された UDP データグラムの IP および UDP ヘッダーから送信者の IP とポート番号を抽出します。 サービス ***nxd_udp_source_extract*** では、IPv4 と IPv6 のどちらか一方のネットワークからのパケットが処理されることにご注意ください。

### <a name="parameters"></a>パラメーター

- **packet_ptr** UDP データグラム パケット ポインター。
- **ip_address** 戻り IP アドレス変数への有効なポインターです。
- **port** 戻りポート変数への有効なポインターです。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 送信元 IP またはポートの抽出が成功しました。
- **NX_INVALID_PACKET** (0x12) 指定されたパケットが無効です。
- **NX_PTR_ERROR** (0x07) パケット、IP、またはポートの宛先が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド、タイマー、ISR

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Extract the IP and port information from the sender of the UPD packet. */
status = nx_udp_source_extract(packet_ptr, &sender_ip_address, &sender_port);

/* If status is NX_SUCCESS, the sender IP and port information has been stored
   in sender_ip_address and sender_port respectively.*/
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_icmp_enable"></a>nxd_icmp_enable
ICMPv4 および ICMPv6 サービスを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_icmp_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスを使用すると、ICMPv4 および ICMPv6 サービスの両方が有効になります。これは、IP インスタンスの作成後にのみ呼び出すことができます。 このサービスを有効にするのは、IPv6 を有効にする前と後のどちらでもかまいません (「*nxd_ipv6_enable*」を参照)。 ICMPv4 サービスには、エコー要求と応答が含まれます。 ICMPv6 サービスには、エコー要求と応答、近隣探索、重複アドレス検出、ルーター検出、ステートレス アドレス自動構成が含まれます。 NetX において IPv4 でこれに相当するのは、*nx_icmp_enable* です。

> [!NOTE] 
> *ICMPv6 を有効にする前から IPv6 アドレスが手動で構成されている場合、手動で構成されたその IPv6 は重複アドレス検出プロセスの対象になりません*。

*nx_icmp_enable* を使用すると、IPv4 操作に対してのみ ICMP サービスが開始します。 ICMPv6 サービスを使用するアプリケーションでは、*nx_icmp_enable* ではなく *nxd_icmp_enable* を使用する必要があります。

IPv6 ルーター要請と IPv6 ステートレス自動アドレス構成を利用するには、ICMPv6 が有効になっている必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ICMP サービスが正常に有効化されました。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Enable ICMP on the IP instance. */
status = nxd_icmp_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for ICMP services. */
```
### <a name="see-also"></a>参照

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_ping
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_ping"></a>nxd_icmp_ping
ICMPv4 または ICMPv6 エコー要求を実行します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_icmp_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr, 
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスでは、適切な物理インターフェイスを介して ICMP エコー要求パケットを送信し、宛先ホストからのエコー応答を待機します。 ping メッセージを送信するのに適切なインターフェイスは、NetX Duo により、宛先アドレスに基づいて決定されます。 パケット送信に使用する物理インターフェイスと正確な発信元 IP アドレスを指定するには、アプリケーションでサービス ***nxd_icmp_source_ping*** を使用する必要があります。

IP インスタンスが既に作成されていることと、ICMPv4 または ICMPv6 サービスが有効になっていることが必要です (「***nxd_icmp_enable***」を参照)。

> [!WARNING]  
> NX_SUCCESS が返された場合、不要になった受信パケットを解放する責任はアプリケーションにあります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスへのポインター。
- **ip_address** ping の宛先 IP アドレス (ホストのバイト順)。
- **data_ptr** ping パケットのデータ領域へのポインター。
- **data_size** ping データのバイト数。
- **response_ptr** 応答パケット ポインターへのポインター。
- **wait_option** 応答を待機する時間。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **タイムアウト値 (ティック数)** (0x00000001 から 
    - **NX_WAIT_FOREVER** 0xFFFFFFFE)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ping の送受信に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 が有効になっていません。
- **NX_OVERFLOW** (0x03) ping データがパケット ペイロードを超えています。
- **NX_NO_RESPONSE** (0x29) 宛先ホストが応答しませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort によって中止されました。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_PTR_ERROR** (0x07) IP または応答ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IP または ICMP コンポーネントが有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) 入力 IP アドレスが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* The following two examples illustrate how to use this API to send
   ping packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   2001:1234:5678::1 */
   
/* Declare variable address to hold the destination address. */
NXD_ADDRESS ip_address;

char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0x20011234;
ip_address.nxd_ip_address.v6[1]    = 0x56780000;
ip_address.nxd_ip_address.v6[2]    = 0;
ip_address.nxd_ip_address.v6[3]    = 1;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr,
                       NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been
   received from IP address 2001:1234:5678::1 and the response
   packet is contained in the packet pointed to by response_ptr.It
   should have the same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4[0]    = 0x01020304;

status = nxd_icmp_ping(&ip_0, &ip_address, buffer,
                       strlen(buffer),&response_ptr, 10);

/* A return value of NX_SUCCESS indicates a ping reply was received
   from IP address 1.2.3.4 and the response packet is contained in
   the packet pointed to by response_ptr. It should have the same
   “abcd” four bytes of data. */
```
### <a name="see-also"></a>参照

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_source_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmp_source_ping"></a>nxd_icmp_source_ping
ICMPv4 または ICMPv6 エコー要求を実行します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_icmp_source_ping(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *ip_address,
    UINT address_index,
    CHAR *data_ptr, 
    ULONG data_size,
    NX_PACKET **response_ptr,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスでは、IPv4 アドレスまたは IPv6 アドレスの指定されたインデックスを使用して、発信元アドレスが関連付けられているネットワーク インターフェイス経由で ICMP エコー要求パケットを送信し、宛先ホストからのエコー応答を待機します。 このサービスは、IPv4 および IPv6 アドレスの両方で動作します。 パラメーター *address_index* は、使用する発信元 IPv4 または IPv6 アドレスを示します。 IPv4 アドレスの場合、*address_index* は接続されているネットワーク インターフェイスと同じインデックスです。 IPv6 の場合、*address_index* は IPv6 アドレス テーブルのエントリを示します。

IP インスタンスが既に作成されていることと、ICMPv4 および ICMPv6 サービスが有効になっていることが必要です (「*nxd_icmp_enable*」を参照)。

> [!CAUTION] 
> *NX_SUCCESS が返された場合、不要になった受信パケットを解放する責任はアプリケーションにあります*。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスへのポインター。
- **ip_address** ping の宛先 IP アドレス (ホストのバイト順)。
- **address_index** 発信元アドレスとして使用する IP アドレスを示します。
- **data_ptr** ping パケットのデータ領域へのポインター。
- **data_size** ping データのバイト数。
- **response_ptr** 応答パケット ポインターへのポインター。
- **wait_option** 応答を待機する時間。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ping の送受信に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 が有効になっていません。
- **NX_OVERFLOW** (0x03) ping データがパケット ペイロードを超えています。
- **NX_NO_RESPONSE** (0x29) 宛先ホストが応答しませんでした。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort によって中止されました。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_PTR_ERROR** (0x07) IP または応答ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IP または ICMP コンポーネントが有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) 入力 IP アドレスが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* The following two examples illustrate how to use this API to send ping
   packets to IPv6 or IPv4 destinations. */

/* The first example: Send a ping packet to an IPv6 host
   FE80::411:7B23:40dc:f181 */

/* Declare variable address to hold the destination address. */

#define PRIMARY_INTERFACE 0
#define GLOBAL_IPv6_ADDRESS 1

NXD_ADDRESS ip_address;
char *buffer = “abcd”;
UINT prefix_length = 10;

/* Set the IPv6 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]    = 0xFE800000;
ip_address.nxd_ip_address.v6[1]    = 0x00000000;
ip_address.nxd_ip_address.v6[2]    = 0x04117B23;
ip_address.nxd_ip_address.v6[3]    = 0x40DCF181;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              GLOBAL_IPv6_ADDRESS,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply has been received
   from IP address FE80::411:7B23:40dc:f181 and the response packet is
   contained in the packet pointed to by response_ptr. It should have the
   same “abcd” four bytes of data. */

/* The second example: Send a ping packet to an IPv4 host 1.2.3.4 */

/* Program the IPv4 address. */
ip_address.nxd_ip_address_version  = NX_IP_VERSION_V4;
ip_address.nxd_ip_address.v4       = 0x01020304;

status = nxd_icmp_source_ping(&ip_0, &ip_address,
                              PRIMARY_INTERFACE,
                              buffer,
                              strlen(buffer),
                              &response_ptr,
                              NX_WAIT_FOREVER);

/* A return value of NX_SUCCESS indicates a ping reply was received from
   IP address 1.2.3.4 and the response packet is contained in the packet
   pointed to by response_ptr. It should have the same “abcd” four bytes
   of data. */
```

### <a name="see-also"></a>参照

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmpv6_ra_flag_callback_set

## <a name="nxd_icmpv6_ra_flag_callback_set"></a>nxd_icmpv6_ra_flag_callback_set
ICMPv6 RA フラグ変更コールバック関数を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_icmpv6_ra_flag_callback_set(
    NX_IP *ip_ptr, 
    VOID(*ra_callback)(NX_IP*ip_ptr, UINT ra_flag));
```
### <a name="description"></a>説明

このサービスを使用すると、ICMPv6 ルーター アドバタイズ フラグ変更コールバック関数が設定されます。 NetX Duo によってルーター アドバタイズ メッセージが受信されると、ユーザー指定のコールバック関数が呼び出されます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスへのポインター。
- **ra_callback** ユーザー指定のコールバック関数。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) RA フラグ コールバック関数の設定に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 が有効になっていません。
- **NX_PTR_ERROR** (0x07) IP が無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
VOID icmpv6_ra_flag_callback(NX_IP *ip_ptr, UINT ra_flag)
{
   /* RA flag has changed. The updated value is passed in via the
      ra_flag parameter. */
}

/* Configure the user-defined ICMPv6 RA flag change callback
   function. */
status = nxd_icmpv6_ra_flag_callback_set(&ip_0,
                                         icmpv6_ra_flag_callback);

/* A status return of NX_SUCCESS indicates the callback function has
   been successfully configured. */
```
### <a name="see-also"></a>参照

- nx_icmp_enable
- nx_icmp_info_get
- nx_icmp_ping
- nxd_icmp_enable
- nxd_icmp_ping
- nxd_icmp_source_ping

## <a name="nxd_ip_raw_packet_send"></a>nxd_ip_raw_packet_send
生 IP パケットを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ip_raw_packet_send(
    NX_IP *ip_ptr, 
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination
    ULONG protocol, 
    UINT ttl, 
    ULONG tos);
```
### <a name="description"></a>説明

このサービスでは、生の IPv4 または IPv6 パケットを送信します (トランスポート層プロトコル ヘッダーはありません)。 マルチホーム システムで、適切なインターフェイスをシステムによって特定できない場合 (たとえば、宛先 IP アドレスが IPv4 ブロードキャスト、マルチキャスト、または IPv6 マルチキャスト アドレスの場合)、プライマリ デバイスが選択されます。 サービス ***nxd_ip_raw_packet_source_send** _ を使用して、送信インターフェイスを指定できます。 NetX でこれに相当するのは、_ *_nx_ip_raw_packet_send_ です。* *

IP インスタンスを事前に作成し、***nx_ip_raw_packet_enable*** サービスを使用して、生 IP パケットの処理を有効にする必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **packet_ptr** 送信するパケットへのポインター。
- **destination_ip** 宛先アドレスへのポインター。
- **protocol** IP ヘッダーに格納されているパケット プロトコル。
- **ttl** TTL またはホップの制限の値。
- **tos** TOS またはトラフィック クラスとフロー ラベルの値。

### <a name="return-value"></a>戻り値 

- **NX_SUCCESS** (0x00) 生 IP パケットが正常に送信されました。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_NOT_ENABLED** (0x14) 生 IP 処理が有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) IPv4 または IPv6 アドレスが無効です。
- **NX_UNDERFLOW** (0x02) パケットに IPv4 または IPv6 ヘッダーのための十分な空き領域がありません。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターまたはパケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_PARAMETERS** (0x4D) 有効な IPv6 アドレス入力ではありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS dest_address;

/* Set the destination address,in this case an IPv6 address. */
dest_address.nxd_ip_address_version  = NX_IP_VERSION_V6;
dest_address.nxd_ip_address.v6[0]    = 0x20011234;
dest_address.nxd_ip_address.v6[1]    = 0x56780000;
dest_address.nxd_ip_address.v6[2]    = 0;
dest_address.nxd_ip_address.v6[3]    = 1;

UINT ttl, tos;

ttl = 128;

tos = 0;

/* Enable RAW IP handling on the previously created IP instance.*/
status = nx_raw_ip_packet_enable(&ip_0);

/* Allocate a packet pointed to by packet_ptr from the IP packet
   pool. */
/* Then transmit the packet to the destination address. */

status = nxd_ip_raw_packet_send(&ip_0, packet_ptr, dest_address,
                                NX_PROTOCOL_UDP, ttl, tos);

/* A status return of NX_SUCCESS indicates the packet was
   successfully transmitted. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_source_send

## <a name="nxd_ip_raw_packet_source_send"></a>nxd_ip_raw_packet_source_send
指定された発信元アドレスを使用して生パケットを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ip_raw_packet_source_send(
    NX_IP *ip_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *destination_ip,
    UINT address_index,
    ULONG protocol,
    UINT ttl,
    ULONG tos);
```
### <a name="description"></a>説明

このサービスでは、指定された IPv4 または IPv6 アドレスを発信元アドレスとして使用して、生の IPv4 または IPv6 パケットを送信します。 このサービスは、通常、マルチホーム システムで、システムが適切なインターフェイスを特定できない場合 (たとえば、宛先 IP アドレスが IPv4 ブロードキャスト、マルチキャスト、または IPv6 マルチキャスト アドレスの場合) に使用されます。 パラメーター *address_index* を使用すると、この生パケットを送信するときに使用する発信元アドレスをアプリケーションで指定できます。

IP インスタンスを事前に作成し、***nx_ip_raw_packet_enable*** サービスを使用して、生 IP パケットの処理を有効にする必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスのポインター。
- **packet_ptr** 送信するパケットへのポインター。
- **destination_ip** 宛先 IP アドレス。
- **address_index** 発信元アドレスとして使用する IPv4 または IPv6 アドレスのインデックス。
- **protocol** プロトコル フィールドの値。
- **ttl** TTL またはホップの制限の値。
- **tos** TOS またはトラフィック クラスとフロー ラベルの値。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケットが正常に送信されました。
- **NX_UNDERFLOW** (0x02) パケットに IPv4 または IPv6 ヘッダーのための十分な空き領域がありません。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_PTR_ERROR** (0x07) IP 制御ブロック、パケット、または destination_ip へのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) 生処理が有効になっていません。
- **NX_IP_ADDRESS_ERROR** (0x21) アドレス エラー。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが無効です。
- **NX_INVALID_PARAMETERS** (0x4D) 有効な IPv6 アドレス入力ではありません。

### <a name="allowed-from"></a>許可元

スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define SOURCE_ADDRESS_INDEX 2

/* Send a raw packet from specified interface. */
status = nxd_ip_raw_packet_source_send(&ip_0, packet_ptr,
                                       dest_ip,
                                       SOURCE_ADDRESS_INDEX,
                                       NX_IP_RAW,
                                       NX_IP_TIME_TO_LIVE,
                                       NX_IP_NORMAL);

/* If status == NX_SUCCESS, raw packet has been sent out on the
   specified interface. */
```
### <a name="see-also"></a>参照

- nx_ip_raw_packet_disable
- nx_ip_raw_packet_enable
- nx_ip_raw_packet_filter_set
- nx_ip_raw_packet_receive
- nx_ip_raw_packet_send
- nx_ip_raw_packet_source_send
- nx_ip_raw_receive_queue_max_set
- nxd_ip_raw_packet_send

## <a name="nxd_ipv6_address_change_notify"></a>nxd_ipv6_address_change_notify
IPv6 アドレス変更通知を設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_address_change_notify(
    NX_IP *ip_ptr,
    VOID (*ip_address_change_notify)(NX_IP *, UINT, UINT, UINT, ULONG *));
```
### <a name="description"></a>説明

このサービスでは、IPv6 アドレスが変更されるたびに NetX Duo によって呼び出されるアプリケーション コールバック ルーチンを登録します。

このサービスは、オプション ***NX_ENABLE_IPV6_ADDRESS_CHANGE_NOTIFY*** を定義して NetX Duo ライブラリが構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** IP 制御ブロックのポインター。
- **ip_address_change_notify** アプリケーション コールバック関数。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 設定に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 アドレス変更通知機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) IPv6 アドレス変更通知がコンパイルされていません。

### <a name="allowed-from"></a>許可元

スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
VOID ip_address_change_notify(NX_IP *ip_ptr, UINT status,
                              UINT interface_index,
                              UINT address_index,
                              ULONG *ip_address)
{

   /* Do something when ip address changed. */
}

void ip_address_thread_entry(ULONG id)
{

   /* Set the ip address change notify of IP instance. */
   status = nxd_ipv6_address_change_notify (&ip_0, ip_address_change_notify);

/* If status == NX_SUCCESS, the ip address change notify of IP
   instance was successfully set. */
}
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_delete"></a>nxd_ipv6_address_delete
IPv6 アドレスを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_address_delete(
    NX_IP *ip_ptr, 
    UINT address_index);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの IPv6 アドレス テーブル内の指定されたインデックスにある IPv6 アドレスを削除します。 NetX でこれに相当するものはありません。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **address_index** IP インスタンスの IPv6 アドレス テーブルへのインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) アドレスが正常に削除されました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS ip_address;
UINT        address_index;

/* Delete the IPv6 address at the specified address table index. */
address_index = 1;
status = nxd_ipv6_address_delete(&ip_0, address_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully deleted. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_get"></a>nxd_ipv6_address_get
IPv6 アドレスとプレフィックスを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_address_get(
    NX_IP *ip_ptr, 
    UINT address_index, 
    NXD_ADDRESS *ip_address,
    ULONG *prefix_length,
    UINT *interface_index);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスのアドレス テーブル内の指定されたインデックスにある IPv6 アドレスとプレフィックスを取得します。 その IPv6 アドレスが関連付けられている物理インターフェイスのインデックスが *interface_index* ポインターに返されます。 NetX でこれに相当するサービスは、***nx_ip_address_get** _ および _*_nx_ip_interface_address_get_** です。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **address_index** IP インスタンスのアドレス テーブルへのインデックス。
- **ip_address** 設定するアドレスへのポインター。
- **prefix_length** アドレス プレフィックスの長さ (サブネット マスク)。
- **interface_index** インターフェイスのインデックスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IPv6 が正常に有効化されました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_NO_INTERFACE_ADDRESS** (0x50) インターフェイス アドレスがないか、address_index が無効です。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS ip_address;
UINT        address_index;
ULONG       prefix_length;
UINT        interface_index;

/* Get the IPv6 address at the specified address table index. If
   found, the address network interface is returned in the
   interface_index input, as well as the address prefix in the
   prefix_length input. */

address_index = 1;
status = nxd_ipv6_address_get(&ip_0, address_index, &ip_address,
                              &prefix_length, &interface_index);

/* A status return of NX_SUCCESS indicates that the IP instance
   address is successfully retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_address_set"></a>nxd_ipv6_address_set
IPv6 アドレスとプレフィックスを設定します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_address_set(
    NX_IP *ip_ptr, 
    UINT interface_index,
    NXD_ADDRESS *ip_address,
    ULONG prefix_length,
    UINT *address_index);
```
### <a name="description"></a>説明

このサービスでは、指定された IPv6 アドレスとプレフィックスを指定された IP インスタンスに設定します。 *address_index* 引数が null 値でない場合は、アドレスが挿入される IPv6 アドレス テーブルへのインデックスが返されます。 NetX でこれに相当するサービスは、***nx_ip_address_set** _ および _*_nx_ip_interface_address_set_** です。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_index** IPv6 アドレスが関連付けられているインターフェイスのインデックス。
- **ip_address** 設定するアドレスへのポインター。
- **prefix_length** アドレス プレフィックスの長さ (サブネット マスク)。
- **address_index** アドレスが挿入されるアドレス テーブルへのインデックスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) IPv6 が正常に有効化されました。
- **NX_NO_MORE_ENTRIES** (0x15) IP アドレス テーブルがいっぱいです。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_DUPLICATED_ENTRY** (0x52) 指定された IP アドレスは、この IP インスタンスで既に使用されています。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) IPv6 アドレスが無効です。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスが無効なネットワーク インターフェイスをポイントしています。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS ip_address;
UINT        address_index;
UINT        interface_index;

ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                     IP_ADDRESS(1,2,3,4),
                     0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                     pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* Set the IPv6 address (a global address as indicated by the 64 bit
   prefix) using the IPv6 address just created on the primary device
   (index zero). The index into the address table is returned in
   address_index. */
interface_index = 0;
status = nxd_ipv6_address_set(&ip_0, interface_index, &ip_address,
                              64,&address_index);

/* A status return of NX_SUCCESS indicates that the IPv6 address is
   successfully assigned to the primary interface (interface 0). */
```

### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_default_router_add"></a>nxd_ipv6_default_router_add
IPv6 ルーターを既定のルーター テーブルに追加します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_default_router_add(
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address,
    ULONG router_lifetime,
    UINT index_index);
```
### <a name="description"></a>説明

このサービスでは、指定された物理インターフェイスの IPv6 既定ルーターを既定のルーター テーブルに追加します。 これに相当する NetX IPv4 サービスは、***nx_ip_gateway_address_set*** です。

*router_address* によって有効な IPv6 アドレスがポイントされていなければならず、指定された物理インターフェイスからこのルーターに直接アクセスできなければなりません。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **router_address** 既定のルーター アドレスへのポインター (ホストのバイト順)。
- **router_lifetime** 既定のルーターの有効期間 (秒単位)。 次の値を指定できます。
    - **0xFFFF:** タイムアウトなし
    - **0 から 0xFFFE:** タイムアウト値 (秒単位)
- **index_index** ルーターに到達するために使用できるネットワーク インデックス インデックスを示す有効なメモリ位置へのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 既定のルーターが正常に追加されました。
- **NX_NO_MORE_ENTRIES** (0x17) 既定のルーター テーブルで使用できるエントリがこれ以上ありません。
- **NX_IP_ADDRESS_ERROR** (0x21) IPv6 アドレスが無効です。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_INVALID_PARAMETERS** (0x4D) 有効な IPv6 アドレス入力ではありません。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_INTERFACE** (0x4C) ルーターのインターフェイスのインデックスが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example adds a default router for the primary interface at
   fe80::1219:B9FF:FE37:ac to the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;

/* Set the router address version to IPv6 */
router_address.nxd_ip_version   = NX_IP_VERSION_V6;

/* Set the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Set IPv6 default router. */
status = nxd_ipv6_default_router_add(ip_ptr, &router_address,
                                     0xFFFF, PRIMARY_INTERFACE);

/* Unless invalid pointer input is detected by the error checking
   Service, status return is always NX_SUCCESS. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_delete"></a>nxd_ipv6_default_router_delete
既定のルーター テーブルから IPv6 ルーターを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_default_router_delete (
    NX_IP *ip_ptr,
    NXD_ADDRESS *router_address);
```
### <a name="description"></a>説明

このサービスでは、既定のルーター テーブルから IPv6 既定ルーターを削除します。 これに相当する NetX IPv4 サービスは、***nx_ip_gateway_address_clear*** です。

### <a name="restrictions"></a>制限

IP インスタンスが既に作成されていること。 *router_address* によって有効な情報がポイントされている必要があります。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **router_address** IPv6 デフォルト ゲートウェイ アドレスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ルーターが正常に削除されました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_NOT_FOUND** (0x4E) ルーター エントリが見つかりません。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_PARAMETERS** (0x82) 無効な非ポインター入力です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/*This example removes a default router:fe80::1219:B9FF:FE37:ac */

NXD_ADDRESS router_address;

/* Set the router_address version to IPv6 */
router_address.nxd_ip_version = NX_IP_VERSION_V6;

/* Program the IPv6 address, in host byte order. */
router_address.nxd_ip_address[0] = 0xfe800000;
router_address.nxd_ip_address[1] = 0x0;
router_address.nxd_ip_address[2] = 0x1219B9FF;
router_address.nxd_ip_address[3] = 0xFE3700AC;

/* Delete the IPv6 default router. */
nxd_ipv6_default_router_delete(ip_ptr, &router_address);
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clearnx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_getnx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_entry_get"></a>nxd_ipv6_default_router_entry_get
既定のルーター エントリを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_default_router_entry_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT entry_index,
    NXD_ADDRESS *router_addr,
    ULONG *router_lifetime,
    ULONG *prefix_length,
    ULONG *configuration_method);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク デバイスに接続されている既定の IPv6 ルーティング テーブルからルーター エントリを取得します。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **entry_index** エントリのインデックス。
- **router_addr** ルーターの IPv6 アドレス。
- **router_lifetime** ルーターの有効期間へのポインター。
- **prefix_length** プレフィックス長へのポインター。
- **configuration_method** エントリがどのように構成されたかに関する情報へのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 取得に成功しました。
- **NX_NOT_FOUND** (0x4E) ルーターのエントリが見つかりません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
NXD_ADDRESS            router_addr;
ULONG                  router_lifetime;
ULONG                  prefix_length;
ULONG                  configuration_method;

/* Get the router entry of specified interface. */
status = nxd_ipv6_default_router_entry_get (&ip_0,
                                            PRIMARY_INTERFACE,
                                            entry_index,
                                            &router_addr,
                                            &router_lifetime,
                                            &prefix_length,
                                            &configuration_method);

/* If status == NX_SUCCESS, the router entry was successfully
   got. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_get"></a>nxd_ipv6_default_router_get
既定のルーター テーブルから IPv6 ルーターを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_default_router_get(
    NX_IP *ip_ptr, 
    UINT interface_index
    NXD_ADDRESS *router_address,
    ULONG *router_lifetime,
    ULONG *prefix_length);
```
### <a name="description"></a>説明

このサービスでは、既定のルーター テーブルから、指定された物理インターフェイスのについて、IPv6 の既定のルーター アドレス、有効期間、プレフィックス長を取得します。 これに相当する NetX IPv4 サービスは、***nx_ip_gateway_address_get*** です。

*router_address* では有効な NXD_ADDRESS 構造体をポイントする必要があるため、このサービスで既定のルーターの IPv6 アドレスを入力できます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **interface_index** ルーターへのアクセスに使用できるネットワーク インターフェイスのインデックス。
- **router_address** 既定のルーター アドレスの戻り値のストレージ スペースへのポインター (ホストのバイト順)。
- **router_lifetime** ルーターの有効期間へのポインター。
- **prefix_length** ルーター アドレス プレフィックス長へのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 既定のルーターが正常に追加されました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_NOT_FOUND** (0x4E) 既定のルーターが見つかりません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_INTERFACE** (0x4C) ルーターのインターフェイスのインデックスが無効です。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example retrieves a default router for the primary device
   from the default router table. */

#define PRIMARY_INTERFACE 0

NXD_ADDRESS router_address;
ULONG       router_lifetime;
ULONG       prefix_length;

/* Get IPv6 default router. */
status = nxd_ipv6_default_router_get(ip_ptr, PRIMARY_INTERFACE,
                                     &router_address,
                                     &router_lifetime,
                                     &prefix_length);

/* If status returns NX_SUCCESS, the router address and related
   information is returned successfully. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_number_of_entries_get

## <a name="nxd_ipv6_default_router_number_of_entries_get"></a>nxd_ipv6_default_router_number_of_entries_get
既定の IPv6 ルーターの数を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_default_router_number_of_entries_get(
    NX_IP *ip_ptr,
    UINT interface_index,
    UINT *num_entries);
```
### <a name="description"></a>説明

このサービスでは、特定のネットワーク インターフェイス上に構成されている IPv6 既定ルーターの数を取得します。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP 制御ブロックのポインター。
- **interface_index** ネットワーク インターフェイスのインデックス。
- **num_entries** 指定されたネットワーク デバイス上の IPv6 ルーターの数の宛先。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) 取得に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_INVALID_INTERFACE** (0x4C) デバイス インデックス値が正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターまたは num_entries ポインターが無効です。

### <a name="allowed-from"></a>許可元

スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0
UINT                   num_entries;

/* Get the router entries of specified interface. */
status = nxd_ipv6_default_router_number_of_entries_get(&ip_0,
                                                       PRIMARY_INTERFACE,
                                                       &num_entries);

/* If status == NX_SUCCESS, the router entries was successfully
   retrieved. */
```
### <a name="see-also"></a>参照

- nx_ip_gateway_address_clear
- nx_ip_gateway_address_get
- nx_ip_gateway_address_set
- nx_ip_info_get
- nx_ip_static_route_add
- nx_ip_static_route_delete
- nxd_ipv6_default_router_add
- nxd_ipv6_default_router_delete
- nxd_ipv6_default_router_entry_get
- nxd_ipv6_default_router_get

## <a name="nxd_ipv6_disable"></a>nxd_ipv6_disable
IPv6 機能を無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_disable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、指定された IP インスタンスの IPv6 を無効にします。 また、既定のルーター テーブル、ND キャッシュ、IPv6 アドレス テーブルをクリアし、すべてのマルチキャスト グループを脱退し、ルーター要請変数をリセットします。 IPv6 が有効になっていない場合、このサービスによる影響はありません。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) 無効化に成功しました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_NOT_SUPPORT** (0x4B) IPv6 モジュールがコンパイルされていません。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Disable IPv6 feature on this IP instance. */
status = nxd_ipv6_disable(&ip_0);

/* If status == NX_SUCCESS, disables IPv6 feature on IP instance.*/
```
### <a name="see-also"></a>参照 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_enable"></a>nxd_ipv6_enable
IPv6 サービスを有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_enable(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、IPv6 サービスを有効にします。 IPv6 サービスが有効になると、IP インスタンスは全ノードのマルチキャスト グループ (FF02::1) に参加します。 このサービスで、リンク ローカル アドレスやグローバル アドレスが設定されることはありません。 アプリケーションでは、*nxd_ipv6_address_set* を使用してデバイスのネットワーク アドレスを構成する必要があります。 NetX でこれに相当するものはありません。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IPv6 が正常に有効化されました。
- **NX_ALREADY_ENABLED** (0x15) IPv6 は既に有効になっています。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* First create an IP instance with packet pool, source address, and
   driver.*/
status = nx_ip_create(&ip_0, "NetX IP Instance 0",
                      IP_ADDRESS(1,2,3,4),
                      0xFFFFFF00UL, &pool_0,_nx_ram_network_driver,
                      pointer, 2048, 1);

/* Then enable IPv6 on the IP instance. */
status = nxd_ipv6_enable(&ip_0);

/* A status return of NX_SUCCESS indicates that the IP instance is
   enabled for IPv6 services. */
```
### <a name="see-also"></a>参照

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_stateless_address_autoconfig_disable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_multicast_interface_join"></a>nxd_ipv6_multicast_interface_join
IPv6 マルチキャスト グループに参加します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_multicast_interface_join(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```

### <a name="description"></a>説明

このサービスを使用すると、アプリケーションは特定のネットワーク インターフェイス上の特定の IPv6 マルチキャスト アドレスに参加できます。 リンク ドライバーは、そのマルチキャスト アドレスを追加するようにとの通知を受けます。 このサービスは、オプション ***NX_ENABLE_IPV6_MULTICAST*** を定義して NetX Duo ライブラリが構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** IP インスタンスのポインター。
- **group_address** IPv6 マルチキャスト アドレス。
- **interface_index** そのマルチキャスト グループに関連付けられているネットワーク インターフェイスのインデックス。

### <a name="return-values"></a>戻り値  

- **NX_SUCCESS** (0x00) IPv6 マルチキャスト アドレスでの受信が正常に有効化されました。
- **NX_NO_MORE_ENTRIES** (0x17) IPv6 マルチキャスト テーブルにエントリがこれ以上ありません。
- **NX_OVERFLOW** (0x03) このデバイス ドライバーで使用できるグループ アドレスがこれ以上ありません。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能と IPv6 マルチキャスト機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) IPv6 アドレスが無効です。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0

/* Join multicast group on this IP instance. */
status = nxd_ipv6_multicast_interface_join(&ip_0,
                                           &group_address,
                                           PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, interface of index on IP instance
   has joined the multicast group. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_getnx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_leave

## <a name="nxd_ipv6_multicast_interface_leave"></a>nxd_ipv6_multicast_interface_leave
IPv6 マルチキャスト グループを脱退します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_multicast_interface_leave(
    NX_IP *ip_ptr,
    NXD_ADDRESS *group_address,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスでは、特定のネットワーク デバイスから特定の IPv6 マルチキャスト アドレスを削除します。 この IPv6 マルチキャスト アドレスの削除は、リンク ドライバーにも通知されます。このサービスは、オプション ***NX_ENABLE_IPV6_MULTICAST*** を定義して NetX Duo ライブラリが構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター  

- **ip_ptr** IP インスタンスのポインター。
- **group_address** IPv6 マルチキャスト アドレス。
- **interface_index** グループに関連付けられているネットワーク インターフェイスのインデックス。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) マルチキャストの脱退に成功しました。
- **NX_ENTRY_NOT_FOUND** (0x16) エントリが見つかりません。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能と IPv6 マルチキャスト機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_IP_ADDRESS_ERROR** (0x21) IPv6 アドレスが無効です。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0

/* Leave multicast address on this IP instance. */
status = nxd_ipv6_multicast_interface_leave(&ip_0,
                                            &group_address,
                                            primary_interface);

/* If status == NX_SUCCESS, interface of index on IP instance
   has left the multicast group. */
```
### <a name="see-also"></a>参照

- nx_igmp_enable
- nx_igmp_info_get
- nx_igmp_loopback_disable
- nx_igmp_loopback_enable
- nx_igmp_multicast_interface_join
- nx_igmp_multicast_join
- nx_igmp_multicast_interface_leave
- nx_igmp_multicast_leave
- nx_ipv4_multicast_interface_join
- nx_ipv4_multicast_interface_leave
- nxd_ipv6_multicast_interface_join

## <a name="nxd_ipv6_stateless_address_autoconfig_disable"></a>nxd_ipv6_stateless_address_autoconfig_disable
ステートレス アドレス自動構成を無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_stateless_address_autoconfig_disable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク デバイスの IPv6 ステートレス アドレス自動構成機能を無効にします。 IPv6 アドレスが構成されている場合、このサービスによる影響はありません。

このサービスは、オプション ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** を定義して NetX Duo ライブラリが構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスのポインター。
- **interface_index** IPv6 ステートレス アドレス自動構成を無効にするネットワーク インターフェイスのインデックス。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ステートレス アドレス自動構成が正常に無効化されました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能と IPv6 ステートレス アドレス自動構成制御機能が NetX Duo ライブラリに組み込まれていません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE 0

/* Disable stateless address auto configuration on this IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_disable(&ip_0,
                                                       PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, disables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>参照 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_enable

## <a name="nxd_ipv6_stateless_address_autoconfig_enable"></a>nxd_ipv6_stateless_address_autoconfig_enable
ステートレス アドレス自動構成を有効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_ipv6_stateless_address_autoconfig_enable(
    NX_IP *ip_ptr,
    UINT interface_index);
```
### <a name="description"></a>説明

このサービスでは、指定されたネットワーク デバイスの IPv6 ステートレス アドレス自動構成機能を有効にします。

このサービスは、オプション ***NX_IPV6_STATELESS_AUTOCONFIG_CONTROL*** を定義して NetX Duo ライブラリが構築されている場合に使用できます。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** IP インスタンスのポインター。
- **interface_index** IPv6 ステートレス アドレス自動構成を有効にするネットワーク インターフェイスのインデックス。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) ステートレス アドレス自動構成が正常に有効化されました。
- **NX_ALREADY_ENABLED** (0x15) 既に有効になっています。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能と IPv6 ステートレス アドレス自動構成制御機能が NetX Duo ライブラリに組み込まれていません。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが正しくありません。
- **NX_PTR_ERROR** (0x07) IP 制御ブロックのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
#define PRIMARY_INTERFACE

/* Enable stateless address auto configuration on this
   IP instance. */
status = nxd_ipv6_stateless_address_autoconfig_enable(&ip_0,
                                                      PRIMARY_INTERFACE);

/* If status == NX_SUCCESS, enables stateless address auto
   configuration on IP instance. */
```
### <a name="see-also"></a>参照 

- nx_ip_auxiliary_packet_pool_set
- nx_ip_address_change_notify
- nx_ip_address_get
- nx_ip_address_set
- nx_ip_create
- nx_ip_delete
- nx_ip_driver_direct_command
- nx_ip_driver_interface_direct_command
- nx_ip_forwarding_disable
- nx_ip_forwarding_enable
- nx_ip_fragment_disable
- nx_ip_fragment_enable
- nx_ip_info_get
- nx_ip_max_payload_size_find
- nx_ip_status_check
- nx_system_initialize
- nxd_ipv6_address_change_notify
- nxd_ipv6_address_delete
- nxd_ipv6_address_get
- nxd_ipv6_address_set
- nxd_ipv6_disable
- nxd_ipv6_enable
- nxd_ipv6_stateless_address_autoconfig_disable

## <a name="nxd_nd_cache_entry_delete"></a>nxd_nd_cache_entry_delete
近隣キャッシュ内の IPv6 アドレス エントリを削除します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_nd_cache_entry_delete(
    NX_IP *ip_ptr, 
    ULONG *ip_address);
```
### <a name="description"></a>説明

このサービスでは、指定された IP アドレスの IPv6 近隣探索キャッシュ エントリを削除します。 これに相当する NetX IPv4 関数は、***nx_arp_static_entry_delete*** です。

### <a name="parameters"></a>パラメーター

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 削除する IPv6 アドレスへのポインター (ホストのバイト順)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) アドレスが正常に削除されました。
- **NX_ENTRY_NOT_FOUND** (0x16) IPv6 近隣キャッシュにアドレスが見つかりません。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example deletes an entry from the neighbor cache table. */

NXD_ADDRESS ip_address;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Delete an entry in the neighbor cache table with the specified IPv6
   address and hardware address. */
status = nxd_nd_cache_entry_delete(&ip_0,
                                   &ip_address.nxd_ip_address.v6[0]);

/* If status == NX_SUCCESS, the entry was deleted from the neighbor cache
   table. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_entry_set"></a>nxd_nd_cache_entry_set
近隣キャッシュに IPv6 アドレスと MAC とのマッピングを追加します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_nd_cache_entry_set(
    NX_IP *ip_ptr, 
    NXD_ADDRESS *dest_ip,
    UINT interface_index, 
    char *mac);
```

### <a name="description"></a>説明

このサービスでは、指定されたネットワーク インターフェイスのインデックス (interface_index) 上のハードウェア MAC アドレスにマップされている、指定された IP アドレス *ip_address* に関するエントリを近隣探索キャッシュに追加します。 これに相当する NetX IPv4 サービスは、***nx_arp_static_entry_create*** です。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **dest_ip** IPv6 アドレス インスタンスへのポインター。
- **interface_index** 宛先 IPv6 アドレスに到達できる物理ネットワーク インターフェイスを指定するインデックス。 
- **mac** ハードウェア アドレスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) エントリが正常に追加されました。
- **NX_NOT_SUCCESSFUL** (0x43) キャッシュが無効であるか、使用できる近隣キャッシュ エントリがありません。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックス値が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example adds an entry on the primary network interface to
   the neighbor cache table. */

#define PRIMARY_INTEFACE 0

NXD_ADDRESS ip_address;
UCHAR hw_address[6] = {0x0, 0xcf,0x01,0x02, 0x03, 0x04};
CHAR  *mac;

mac = (CHAR *)&hw_address[0];

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Create an entry in the neighbor cache table with the specified
   IPv6 address and hardware address. */
status = nxd_nd_cache_entry_set(&ip_0,
                                &ip_address.nxd_ip_address.v6[0],
                                PRIMARY_INTERFACE, mac);

/* If status == NX_SUCCESS, the entry was added to the neighbor
   cache table. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_hardware_address_find"></a>nxd_nd_cache_hardware_address_find
IPv6 アドレスのハードウェア アドレスを検索します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_nd_cache_hardware_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG *physical_msw,
    ULONG *physical_lsw
    UINT *interface_index);
```
### <a name="description"></a>説明

このサービスでは、IPv6 近隣探索キャッシュで、指定された IPv6 アドレスに関連付けられている物理ハードウェア アドレスの検索が試みられます。 このネイバーに到達できるネットワーク インターフェイスのインデックスも、パラメーター *interface_index* で返されます。 これに相当する NetX IPv4 サービスは、***nx_arp_hardware_address_find*** です。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 検索する IP アドレスへのポインター (ホストのバイト順)。
- **physical_msw** その物理アドレスの上位 16 ビット (47-32) へのポインター (ホストのバイト順)。 
- **physical_lsw** その物理アドレスの下位 32 ビット (31-0) へのポインター (ホストのバイト順)。
- **interface_index** その IPv6 アドレスに到達できるネットワーク デバイスを指定するインターフェイスのインデックスを示す有効なメモリ位置へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) アドレスが正常に検出されました。
- **NX_ENTRY_NOT_FOUND** (0x16) マッピングが近隣キャッシュにありません。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_INVALID_PARAMETERS** (0x4D) 指定された IP アドレスはバージョン 6 ではありません。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example inputs an IP address on the primary network in order
   to obtain the hardware address it is mapped to in the neighbor
   cache able. */

NXD_ADDRESS  ip_address;
ULONG physical_msw, physical_lsw;
UINT  interface_index;

ip_address.nxd_ip_address_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0]   = 0x20011234;
ip_address.nxd_ip_address.v6[1]   = 0x56780000;
ip_address.nxd_ip_address.v6[2]   = 0;
ip_address.nxd_ip_address.v6[3]   = 1;

/* Obtain the hardware address mapped to the supplied global IPv6
   address. */
status = nxd_nd_cache_hardware_address_find(&ip_0, &ip_address,
                                            &physical_msw,
                                            &physical_lsw
                                            &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the hardware address returned in
   variables physical_msw and physical_lsw, the index of the network
   interface through which the neighbor can be reached is stored in
   interface_index. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_invalidate
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_invalidate"></a>nxd_nd_cache_invalidate
近隣探索キャッシュを無効にします

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_nd_cache_invalidate(NX_IP *ip_ptr);
```
### <a name="description"></a>説明

このサービスでは、IPv6 近隣探索キャッシュ全体を無効にします。 このサービスは、ICMPv6 が有効化される前または後に呼び出すことができます。 このサービスは IPv4 接続には適用されないため、NetX でこれに相当するサービスはありません。

### <a name="parameters"></a>パラメーター

- **ip_ptr** IP インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) キャッシュが正常に無効化されました。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP インスタンスが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example invalidates the host neighbor cache table. */

/* Invalidate the cache table bound to the IP instance. */
status = nxd_nd_cache_invalidate (&ip_0);

/* If status == NX_SUCCESS, all entries in the neighbor cache table
   are invalidated. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_ip_address_find

## <a name="nxd_nd_cache_ip_address_find"></a>nxd_nd_cache_ip_address_find
物理アドレスに相当する IPv6 アドレスを取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_nd_cache_ip_address_find(
    NX_IP *ip_ptr,
    NXD_ADDRESS *ip_address,
    ULONG physical_msw,
    ULONG physical_lsw,
    UINT *interface_index);
```
### <a name="description"></a>説明

このサービスでは、IPv6 近隣探索キャッシュで、指定された物理アドレスに関連付けられている IPv6 アドレスの検索が試みられます。 このネイバーに到達できるネットワーク インターフェイスのインデックスも返されます。 これに相当する NetX IPv4 サービスは、***nx_arp_ip_address_find*** です。

### <a name="parameters"></a>パラメーター 

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。
- **ip_address** 有効な NXD_ADDRESS 構造体へのポインター。
- **physical_msw** 検索する物理アドレスの上位 16 ビット (47-32) (ホストのバイト順)。
- **physical_lsw** 検索する物理アドレスの下位 32 ビット (31-0) (ホストのバイト順)。
- **interface_index** この IPv6 アドレスに到達できるネットワーク デバイス インデックスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) アドレスが正常に検出されました。
- **NX_ENTRY_NOT_FOUND** (0x16) 近隣キャッシュに物理アドレスが見つかりません。
- **NX_NOT_SUPPORTED** (0x4B) IPv6 機能が NetX Duo ライブラリに組み込まれていません。
- **NX_PTR_ERROR** (0x07) IP インスタンスまたはストレージ スペースが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。 
- **NX_INVALID_PARAMETERS** (0x4D) MAC アドレスがゼロです。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* This example inputs a hardware address to search on for the
   matching IPv6 global address in the neighbor cache table. */

NXD_ADDRESS ip_address;
ULONG physical_msw = 0xcf;
ULONG physical_lsw = 0x01020304;
UINT  interface_index;

/* Obtain the IPv6 address mapped to the supplied hardware
   Address on the primary device. */
status = nxd_nd_cache_ip_address_find(&ip_0, &ip_address,
                                      physical_msw, physical_lsw,
                                      &interface_index);

/* If status == NX_SUCCESS, a matching entry was found in the
   neighbor cache table and the global IPv6 address returned in
   variable ip_address. */
```
### <a name="see-also"></a>参照

- nx_arp_dynamic_entries_invalidate
- nx_arp_dynamic_entry_set
- nx_arp_enable
- nx_arp_entry_delete
- nx_arp_gratuitous_send
- nx_arp_hardware_address_find
- nx_arp_info_get
- nx_arp_ip_address_find
- nx_arp_static_entries_delete
- nx_arp_static_entry_create
- nx_arp_static_entry_delete
- nxd_nd_cache_entry_delete
- nxd_nd_cache_entry_set
- nxd_nd_cache_hardware_address_find
- nxd_nd_cache_invalidate

## <a name="nxd_tcp_client_socket_connect"></a>nxd_tcp_client_socket_connect
TCP 接続を確立します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_tcp_client_socket_connect(
    NX_TCP_SOCKET *socket_ptr
    NXD_ADDRESSS *server_ip,
    UINT server_port,
    ULONG wait_option);
```
### <a name="description"></a>説明

このサービスでは、以前に作成した TCP クライアント ソケットを使用して、指定されたサーバーのポートへの TCP 接続を確立します。 このサービスは、IPv4 と IPv6 のどちらのネットワーク上でも動作します。 有効な TCP サーバー ポートの範囲は 0 から 0xFFFF です。 NetX Duo では、このサーバーの IP アドレスに基づいて適切な物理インターフェイスを決定します。 NetX IPv4 でこれに相当するのは、***nx_tcp_client_socket_connect*** です。

ソケットはローカル ポートにバインドされている必要があります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された TCP ソケットへのポインター。
- **server_ip** IPv4 または IPv6 宛先アドレスへのポインター (ホストのバイト順)。
- **server_port** (1 から 0xFFFF) に接続するサーバー ポート番号 (ホストのバイト順)。
- **wait_option** 接続の確立中の待機オプション。 この待機オプションは次のように定義されます。
    - **NX_NO_WAIT** (0x00000000)
    - **NX_WAIT_FOREVER** (0xFFFFFFFF)
    - **タイムアウト値 (ティック数)** (0x00000001 から 0xFFFFFFFE)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソケットの接続に成功しました。
- **NX_WAIT_ABORTED** (0x1A) 要求された中断が tx_thread_wait_abort への呼び出しによって中止されました。
- **NX_IP_ADDRESS_ERROR** (0x21) サーバーの IPv4 アドレスまたは IPv6 アドレスが無効です。
- **NX_NOT_BOUND** (0x24) ソケットがバインドされていません。
- **NX_NOT_CLOSED** (0x35) ソケットが CLOSED 状態ではありません。
- **NX_IN_PROGRESS** (0x37) 待機が指定されていないため、接続の試行を実行中です。
- **NX_INVALID_INTERFACE** (0x4C) インターフェイスのインデックスが無効です。
- **NX_NO_INTERFACE_ADDRESS** (0x50) ネットワーク インターフェイスに有効な IPv6 アドレスがありません。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_INVALID_PORT** (0x46) ポートが無効です。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_CONNECTED** (0x38) 接続に失敗しました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS peer_ip_address;
ULONG       peer_port;

/* Set Peer IPv6 address */
peer_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
peer_ip_address.nxd_ip_address.v6[0] = 0x20010000;
peer_ip_address.nxd_ip_address.v6[1] = 0;
peer_ip_address.nxd_ip_address.v6[2] = 0;
peer_ip_address.nxd_ip_address.v6[3] = 0x101;

/* Set peer port number */
peer_port = 2563;

/* Connect to the peer */
status = nxd_tcp_client_socket_connect(socket_ptr,
                                       &peer_ip_address,
                                       peer_port, NX_WAIT_FOREVER);
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_socket_peer_info_get

## <a name="nxd_tcp_socket_peer_info_get"></a>nxd_tcp_socket_peer_info_get
ピア TCP ソケットの IP アドレスとポート番号を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_tcp_socket_peer_info_get
    (NX_TCP_SOCKET *socket_ptr,
    NXD_ADDRESS *peer_ip_address,
    ULONG *peer_port);
```
### <a name="description"></a>説明

このサービスでは、IPv4 または IPv6 ネットワーク経由で接続されている TCP ソケットのピア IP アドレスとポート情報を取得します。 これに相当する NetX IPv4 サービスは、***nx_tcp_socket_peer_info_get*** です。

*socket_ptr* では既に接続状態にある TCP ソケットをポイントする必要があることにご注意ください。

### <a name="parameters"></a>パラメーター

- **socket_ptr** ピア ホストに接続されている TCP ソケットへのポインター。
- **peer_ip_address** IPv4 または IPv6 ピア アドレスへのポインター。 返される IP アドレスは、ホストのバイト順になっています。
- **peer_port** ピア ポート番号へのポインター。 返されるポート番号は、ホストのバイト順になっています。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソケット情報が正常に取得されました。
- **NX_NOT_CONNECTED** (0x38) ソケットがピアに接続されていません。
- **NX_NOT_ENABLED** (0x14) TCP が有効になっていません。
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS  peer_ip_address;
ULONG        peer_port;

/* Get TCP socket information. */
status = nxd_tcp_socket_peer_info_get(socket_ptr, &peer_ip_address,
                                      &peer_port);

/* If status == NX_SUCCESS, the service returns valid peer info: */
if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V4)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v4 */

if(peer_ip_address.nxd_ip_version == NX_IP_VERSION_V6)
    /* Peer IP address is stored in
       peer_ip_address.nxd_ip_address.v6 */
```
### <a name="see-also"></a>参照

- nx_tcp_client_socket_bind
- nx_tcp_client_socket_connect
- nx_tcp_client_socket_port_get
- nx_tcp_client_socket_unbind
- nx_tcp_enable
- nx_tcp_free_port_find
- nx_tcp_info_get
- nx_tcp_server_socket_accept
- nx_tcp_server_socket_listen
- nx_tcp_server_socket_relisten
- nx_tcp_server_socket_unaccept
- nx_tcp_server_socket_unlisten
- nx_tcp_socket_bytes_available
- nx_tcp_socket_create
- nx_tcp_socket_delete
- nx_tcp_socket_disconnect
- nx_tcp_socket_info_get
- nx_tcp_socket_receive
- nx_tcp_socket_receive_queue_max_set
- nx_tcp_socket_send
- nx_tcp_socket_state_wait
- nxd_tcp_client_socket_connect

## <a name="nxd_udp_packet_info_extract"></a>nxd_udp_packet_info_extract
UDP パケットからネットワーク パラメーターを抽出します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_udp_packet_info_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT *protocol,
    UINT *port,
    UINT *interface_index);
```
### <a name="description"></a>説明

このサービスでは、IPv4 または IPv6 UDP ネットワーク上で受信したパケットからネットワーク パラメーターを抽出します。 NetX でこれに相当するサービスは、***nx_udp_packet_info_extract*** です。

### <a name="parameters"></a>パラメーター

- **packet_ptr** パケットを指すポインター。
- **ip_address** 送信元 IP アドレスへのポインター。
- **protocol** 返されるプロトコルへのポインター。
- **port** 送信元のポート番号へのポインター。
- **interface_index** パケットの取得元となるネットワーク インターフェイスのインデックスへのポインター。

### <a name="return-values"></a>戻り値 

- **NX_SUCCESS** (0x00) パケット インターフェイス データが正常に抽出されました。
- **NX_INVALID_PACKET** (0x12) パケットが IPv4 でも IPv6 でもありません。
- **NX_PTR_ERROR** (0x07) ポインター入力が無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
/* Extract network data from UDP packet interface.*/
status = nxd_udp_packet_info_extract(packet_ptr, &ip_address,
                                    &protocol, &port,
                                    &interface_index);

/* If status is NX_SUCCESS packet data was successfully retrieved.*/
```
### <a name="see-also"></a>参照 

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_send"></a>nxd_udp_socket_send
UDP データグラムを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_udp_socket_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port);
```
### <a name="description"></a>説明

このサービスでは、以前に作成され、バインドされた IPv4 または IPv6 ネットワーク用の UDP ソケットを介して UDP データグラムを送信します。 NetX Duo では、宛先 IP アドレスに基づいて、適切なローカル IP アドレスを発信元アドレスとして検索します。 特定のインターフェイスと発信元 IP アドレスを指定するには、アプリケーションで ***nxd_udp_socket_source_send*** サービスを使用する必要があります。

このサービスは、UDP データグラムが正常に送信されたかどうかに関係なく、直ちに返されることにご注意ください。 NetX (IPv4) でこれに相当するサービスは、***nx_udp_socket_send*** です。

このソケットは、ローカル ポートにバインドされている必要があります。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター
- **packet_ptr** UDP データグラム パケットのポインター。
- **ip_address** 宛先の IPv4 または IPv6 アドレスへのポインター。
- **port** 1 から 0xFFFF の範囲の有効な宛先ポート番号 (ホストのバイト順)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) UDP ソケットの送信に成功しました。
- **NX_IP_ADDRESS_ERROR** (0x21) サーバーの IPv4 アドレスまたは IPv6 アドレスが無効です。
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていません。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_UNDERFLOW** (0x02) パケットに UDP ヘッダーのための十分な空き領域がありません。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。
- **NX_PTR_ERROR** (0x07) ソケットのポインター、アドレスのポインター、またはパケットのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) UDP が有効になっていません
- **NX_INVALID_PORT** (0x46) ポート番号が有効な範囲内ではありません

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS ip_address, server_address;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the
   IPv6 address just created on the primary device (index 0). We
   don’t need the index into the address table, so the last argument
   is set to null. */

interface_index = 0;
status = nxd_ipv6_address_set(&client_ip, interface_index,
                              &ip_address, 64, NX_NULL);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_send(&client_socket, packet_ptr,
                             &server_address, 12);

/* If status == NX_SUCCESS, the UDP host successfully transmitted
   the packet out the UDP socket to the server. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_source_send
- nxd_udp_source_extract

## <a name="nxd_udp_socket_source_send"></a>nxd_udp_socket_source_send
UDP データグラムを送信します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_udp_socket_source_send(
    NX_UDP_SOCKET *socket_ptr,
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address,
    UINT port, 
    UINT address_index);
```
### <a name="description"></a>説明

このサービスでは、以前に作成され、バインドされた IPv4 または IPv6 ネットワーク用の UDP ソケットを介して UDP データグラムを送信します。 パラメーター *address_index* に、発信パケットに使用する発信元 IP アドレスを指定します。 この関数は、UDP データグラムが正常に送信されたかどうかに関係なく、直ちに返されることにご注意ください。

このソケットは、ローカル ポートにバインドされている必要があります。

NetX (IPv4) でこれに相当するサービスは、***nx_udp_socket_source_send*** です。

### <a name="parameters"></a>パラメーター

- **socket_ptr** 以前に作成された UDP ソケット インスタンスを指すポインター
- **packet_ptr** UDP データグラム パケットのポインター。
- **ip_address** 宛先 IPv4 または IPv6 アドレス ポート (有効な宛先ポート番号の範囲は 1 から 0xFFFF) へのポインター (ホストのバイト順)。
- **address_index** パケットに使用する発信元アドレスを指定するインデックス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) UDP ソケットの送信に成功しました。
- **NX_IP_ADDRESS_ERROR** (0x21) サーバーの IPv4 アドレスまたは IPv6 アドレスが無効です。
- **NX_NOT_BOUND** (0x24) ソケットがどのポートにもバインドされていません。
- **NX_NO_INTERFACE_ADDRESS** (0x50) 適切な送信インターフェイスが見つかりません。
- **NX_NOT_FOUND** (0x4E) 適切なインターフェイスが見つかりません。
- **NX_PTR_ERROR** (0x07) ソケットのポインター、アドレス、またはパケットのポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。
- **NX_NOT_ENABLED** (0x14) UDP が有効になっていません。
- **NX_INVALID_PORT** (0x46) ポート番号が有効な範囲内にありません。
- **NX_INVALID_INTERFACE** (0x4C) 指定されたネットワーク インターフェイスが有効です。
- **NX_UNDERFLOW** (0x02) パケットに UDP ヘッダーのための十分な空き領域がありません。
- **NX_OVERFLOW** (0x03) パケットの追加ポインターが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS ip_address, server_address;
UINT address_index;

/* Set the UDP Client IPv6 address. */
ip_address.nxd_ip_version = NX_IP_VERSION_V6;
ip_address.nxd_ip_address.v6[0] = 0x20010000;
ip_address.nxd_ip_address.v6[1] = 0;
ip_address.nxd_ip_address.v6[2] = 0;
ip_address.nxd_ip_address.v6[3] = 1;

/* Set the UDP server IPv6 address to send to. */
server_address.nxd_ip_version = NX_IP_VERSION_V6;
server_address.nxd_ip_address.v6[0] = 0x20010000;
server_address.nxd_ip_address.v6[1] = 0;
server_address.nxd_ip_address.v6[2] = 0;
server_address.nxd_ip_address.v6[3] = 2;

/* Set the global address (indicated by the 64 bit prefix) using the IPv6
   address just created on the primary device (index 0). The address index
   is needed for nxd_udp_socket_source_send. */

status = nxd_ipv6_address_set(&client_ip, 0,
                              &ip_address, 64, &address_index);

/* Create the UDP socket client_socket with the ip_address and
   allocate a packet pointed to by packet_ptr (not shown). */

/* Send a packet to the UDP server at server_address on port 12. */
status = nxd_udp_socket_source_send(&client_socket, packet_ptr,
                                    &server_address, 12, address_index);

/* If status == NX_SUCCESS, the UDP host successfully transmitted the
   packet out the UDP socket to the server. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_source_extract

## <a name="nxd_udp_source_extract"></a>nxd_udp_source_extract
UDP パケットの発信元情報を取得します

### <a name="prototype"></a>プロトタイプ  

```c
UINT nxd_udp_source_extract(
    NX_PACKET *packet_ptr,
    NXD_ADDRESS *ip_address, 
    UINT *port);
```
### <a name="description"></a>説明

このサービスでは、ホストの UDP ソケット経由で受信した UDP パケットから、発信元 IP アドレスとポート番号を抽出します。 NetX (IPv4) でこれに相当するのは、***nx_udp_source_extract*** です。

### <a name="parameters"></a>パラメーター

- **packet_ptr** 受信した UDP パケットへのポインター。
- **ip_address** パケットの発信元 IP アドレスを格納する NXD_ADDRESS 構造体へのポインター
- **port** UDP ソケットのポート番号へのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) ソースの抽出に成功しました。
- **NX_INVALID_PACKET** (0x12) パケットが正しくありません。
- **NX_PTR_ERROR** (0x07) ソケット ポインターが無効です。
- **NX_CALLER_ERROR** (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="preemption-possible"></a>プリエンプション可能

いいえ

### <a name="example"></a>例

```c
NXD_ADDRESS ip_address;
UINT         port;

/* Create the UDP socket client_socket and
   allocate the packet pointed to by packet_ptr (not shown). */

/* Extract the IP address and port of the packet received on the UDP
   socket specified in the packet interface. */
status = nxd_udp_source_extract(&packet_ptr, &ip_address, &port);

/* If status == NX_SUCCESS, the source IP address and port of the
   packet received on the UDP socket was successfully extracted. */
```
### <a name="see-also"></a>参照

- nx_udp_enable
- nx_udp_free_port_find
- nx_udp_info_get
- nx_udp_packet_info_extract
- nx_udp_socket_bind
- nx_udp_socket_bytes_available
- nx_udp_socket_checksum_disable
- nx_udp_socket_checksum_enable
- nx_udp_socket_create
- nx_udp_socket_delete
- nx_udp_socket_info_get
- nx_udp_socket_port_get
- nx_udp_socket_receive
- nx_udp_socket_receive_notify
- nx_udp_socket_send
- nx_udp_socket_source_send
- nx_udp_socket_unbind
- nx_udp_source_extract
- nxd_udp_packet_info_extract
- nxd_udp_socket_send
- nxd_udp_socket_source_send