---
title: 第 4 章 - NAT サービスの説明
description: この章では、すべての NetX Duo NAT API サービスをアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 07/14/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: dbe2cb25607162b62b048251927bdc7671c5884d2a3b45b6b24bae539e08d24a
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797297"
---
# <a name="chapter-4---description-of-nat-services"></a>第 4 章 - NAT サービスの説明

この章では、すべての NetX Duo NAT API サービス (以下に記載) をアルファベット順に説明します。

> [!NOTE]
> 以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

## <a name="nx_nat_create"></a>nx_nat_create

NAT サーバーを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_create(NX_NAT_DEVICE *nat_ptr, NX_IP *ip_ptr,
    UINT global_interface_index,
    VOID *dynamic_cache_memory,
    UINT dynamic_cache_size);
```

### <a name="description"></a>説明

このサービスは、NAT サーバーのインスタンスを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: 作成する NAT インスタンスへのポインター
- **ip_ptr**: IP インスタンスへのポインター
- **global_interface_index**: グローバル ネットワーク インターフェイスへのインデックス
- **dynamic_cache_memory**: NAT テーブルへのポインター メモリ領域
- **dynamic_cache_size**: NAT テーブルのメモリ領域のサイズ

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) NAT サーバーが正常に作成されました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
- NX_NAT_PARAM_ERROR: (0xD01) 非ポインター入力が無効です
- NX_NAT_CACHE_ERROR: (0xD02) キャッシュ ポインター入力が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
#define NX_NAT_ENTRY_CACHE_SIZE 20480

static UCHAR nat_cache[NX_NAT_ENTRY_CACHE_SIZE];
UINT global_interface_index = 0;

/* Create a NAT Server and cache with a global interface index. */
status = nx_nat_create(nat_ptr, ip_ptr, global_interface_index,
    nat_cache, NX_NAT_ENTRY_CACHE_SIZE);

/* If status = NX_SUCCESS, the NAT instance was successfully
    created. */
```

## <a name="nx_nat_delete"></a>nx_nat_delete

NAT サーバーを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_delete(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>説明

このサービスは、以前に作成された NAT サーバーを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: 削除する NAT インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) NAT が正常に削除されました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Delete the NAT instance. */
status = nx_nat_delete (nat_ptr);

/* If the NAT instance was successfully deleted, status = NX_SUCCESS. */
```

## <a name="nx_nat_enable"></a>nx_nat_enable

NAT の IP インスタンスを有効にする

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_enable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>説明

このサービスは、NAT の IP インスタンスを有効にします (たとえば、受信したパケットを NAT サーバーに転送します)。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: NAT インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) NAT が正常に有効になりました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Enable the NAT server. */
status = nx_nat_enable (nat_ptr);

/* If status = NX_SUCCESS, the IP instance was successfully enabled for NAT. */
```

## <a name="nx_nat_disable"></a>nx_nat_disable

NAT の IP インスタンスを無効にする

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_disable(NX_NAT_DEVICE *nat_ptr);
```

### <a name="description"></a>説明

このサービスは、IP インスタンスで NAT を無効にします。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: NAT インスタンスへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) NAT が正常に無効になりました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Disable the NAT server. */
status = nx_nat_disable (nat_ptr);

/* If status = NX_SUCCESS the NAT operation successfully disable. */
```

## <a name="nx_nat_cache_notify_set"></a>nx_nat_cache_notify_set

キャッシュ完全通知コールバック関数を設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_cache_notify_set(NX_NAT_DEVICE *nat_ptr,
    VOID (*cache_full_notify_cb)
    (NX_NAT_DEVICE *nat_ptr)));
```

### <a name="description"></a>説明

このサービスは、ユーザー定義のキャッシュ完全通知関数を指す入力関数ポインター cache_full_notify_cb に、キャッシュ完全コールバックを登録します。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: NAT インスタンスへのポインター
- **cache_full_notify_cb**: キャッシュ完全通知関数へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) キャッシュ完全通知関数が正常に設定されました
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
- NX_NAT_PARAM_ERROR: (0xD01) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Set the cache full notify callback function to the NAT instance. */
status = nx_nat_cache_notify_set(nat_ptr, cache_full_notify_cb);

/* If status = NX_SUCCESS the callback function was successfully set. */
```

## <a name="nx_nat_inbound_entry_create"></a>nx_nat_inbound_entry_create

NAT 変換テーブルに受信エントリを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_inbound_entry_create(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *entry_ptr
    ULONG local_ip_address,
    USHORT external_port,
    USHORT local_port, UCHAR protocol);
```

### <a name="description"></a>説明

このサービスは、受信エントリを静的 (有効期限のない永続的なエントリ) として作成し、NAT 変換テーブルに追加します。 通常、これらのエントリは、外部ネットワーク上のホストから接続が開始されるローカル ホスト サーバー用に作成されます。 NAT サーバーは、外部ポートが変換テーブルでまだ使用されていないか、同じプロトコルの既存の NetX Duo ソケットによってバインドされていないことを確認します。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: NAT インスタンスへのポインター
- **entry_ptr**: 変換エントリへのポインター
- **local_ip_address**: ローカル ホストの IP アドレス
- **external_port**: 外部ネットワーク上の宛先ポート
- **local_port**: 送信元 (ローカル ホスト) ポート
- **protocol**: パケット プロトコル (TCP など)

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) エントリが正常に作成されました
- **NX_NAT_PORT_UNAVAILABLE**: (0xD0D) 外部ポートが無効です
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
- NX_NAT_PARAM_ERROR: (0xD01) 非ポインター入力が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Create an entry for an inbound TCP packet. */
status = nx_nat_inbound_entry_create(nat_ptr, entry_ptr,
    IP_ADDRESS(192,168,2,2), 5001, 5001,
    NX_PROTOCOL_TCP);

/* If status = NX_SUCCESS the entry was successfully created. */
```

## <a name="nx_nat_inbound_entry_delete"></a>nx_nat_inbound_entry_delete

NAT 変換テーブルの受信エントリを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_nat_inbound_entry_delete(NX_NAT_DEVICE *nat_ptr,
    NX_NAT_TRANSLATION_ENTRY *delete_entry_ptr)
```

### <a name="description"></a>説明

このサービスは、指定された受信エントリを変換テーブルから削除します。

### <a name="input-parameters"></a>入力パラメーター

- **nat_ptr**: NAT インスタンスへのポインター
- **delete_entry_ptr**: NAT 変換エントリへのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) エントリが正常に削除されました
- **NX_NAT_ENTRY_NOT_FOUND**: (0xD04) エントリが見つかりません
- NX_PTR_ERROR: (0x07) 入力ポインター パラメーターが無効です
- NX_NAT_ENTRY_TYPE_ERROR: (0xD0C) 変換の種類が無効です

### <a name="allowed-from"></a>許可元

アプリケーション コード

### <a name="example"></a>例

```C
/* Delete the specified static entry from the translation table. */
status = nx_nat_inbound_entry_delete(nat_ptr, delete_entry_ptr);

/* If status = NX_SUCCESS the entry was successfully deleted. */
```
