---
title: 第 4 章 - mDNS サービスの説明
description: この章では、すべての NetX mDNS サービスについて説明します
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6e37698ac6023b4cff6cb4fc05330a73b678ef3d2a813a706c9b821381e123db
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797570"
---
# <a name="chapter-4---description-of-mdns-services"></a>第 4 章 - mDNS サービスの説明

この章では、すべての NetX mDNS サービスについて説明します (以下の一覧を参照)。

> [!NOTE]
> 以下の API の説明の「戻り値」セクションで、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字でない値は完全に無効になります。

## <a name="nx_mdns_create"></a>nx_mdns_create

mDNS インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_create(NX_MDNS *mdns_ptr, NX_IP *ip_ptr,
    NX_PACKET_POOL *packet_pool,
    UINT priority, VOID *stack_ptr,
    UINT stack_size, UCHAR *host_name,
    VOID *local_service_cache,
    UINT local_service_cache_size,
    VOID *peer_service_cache,
    UINT peer_service_cache_size,
    VOID (*probing_notify)(NX_MDNS *mdns_ptr,
        UCHAR *name, UINT probing_state));
```

### <a name="description"></a>説明

このサービスは、特定の IP インスタンスとその関連リソース上に mDNS インスタンスを作成します。 受信した mDNS メッセージを処理し、クエリに応答して、定期的にクエリ メッセージを送信するためのスレッドも作成されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **ip_ptr**: 関連付けられている IP インスタンスを指すポインター。
- **packet_pool**: 有効なパケット プールを指すポインター。
- **priority**: mDNS スレッドの優先度。
- **stack_ptr**: mDNS スレッドのスタック領域を指すポインター
- **stack_size**: スタック領域のサイズ。
- **host_name**: このノードに割り当てられたホスト名。
- **local_service_cache**: ローカルに登録されているサービス用の記憶領域。
- **local_service_cache_size**: ローカル サービス キャッシュのサイズ。
- **peer_service_cache**: 受信したサービス情報用の記憶領域
- **peer_service_cache_size**: ピア サービス キャッシュのサイズ
- **probing_notify**: プローブ操作の最後に呼び出される省略可能なコールバック関数。 ホスト名 (ローカル インターフェイスで mDNS を有効にする場合) またはサービス名 (サービスの登録後) が一意であるかどうかをアプリケーションに通知します。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): mDNS インスタンスが正常に作成されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
UCHAR stack_ptr[2048];
UCHAR local_cache_ptr[2048];
UCHAR peer_cache_ptr[8192];

/* Create a mDNS instance. */
status = nx_mdns_create(&my_mdns, &ip_0, &pool_0,
    3, stack_ptr, 2048,
    “NETX-MDNS-HOST”,
    local_cache_ptr, 2048,
    peer_cache_ptr, 8192,
    probing_notify);

/* If status is NX_SUCCESS, mDNS instance was created. */
```

## <a name="nx_mdns_delete"></a>nx_mdns_delete

mDNS インスタンスを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_delete(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>説明

このサービスは、mDNS インスタンスを削除し、そのリソースを解放します。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): mDNS インスタンスが正常に削除されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete a previously created mDNS instance. */

status = nx_mdns_delete(&my_mdns);

/* If status is NX_SUCCESS, the mDNS instance has been deleted. */
```

## <a name="nx_mdns_enable"></a>nx_mdns_enable

mDNS サービスを開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_enable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>説明

この API は、特定の物理インターフェイスで mDNS サービスを有効にします。 サービスが有効になると、mDNS モジュールは、まず、ネットワーク上のそのすべての一意のサービス名をプローブしてから、インターフェイスで受信したクエリに応答します。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS インスタンス制御ブロックを指すポインター。
- **interface_index**: サービスを有効にするインターフェイスへのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービスが正常に有効になりました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Enable mDNS service on specific interface. */

status = nx_mdns_enable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was enabled. */
```

## <a name="nx_mdns_disable"></a>nx_mdns_disable

mDNS サービスを無効にします

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_disable(NX_MDNS *mdns_ptr, UINT interface_index);
```

### <a name="description"></a>説明

この API は、特定の物理インターフェイスで mDNS サービスを無効にします。 サービスが無効になると、mDNS は、インターフェイスに接続されているネットワークに対してすべてのローカル サービスの "goodbye" メッセージを送信するため、隣接ノードに通知されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **interface_index**: サービスを無効にするインターフェイスへのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービスが正常に無効になりました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Disable mDNS service on specific interface. */

status = nx_mdns_disable(&my_mdns, 0);

/* If status is NX_SUCCESS, mDNS service was disabled. */
```

## <a name="nx_mdns_cache_notify_set"></a>nx_mdns_cache_notify_set

mDNS のキャッシュ満杯通知関数をインストールします

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_mdns_cache_notify_set(NX_MDNS *mdns_ptr,
    VOID (*cache_full_notify_cb)(NX_MDNS *mdns_ptr,
        UINT state, UINT cache_type));
```

### <a name="description"></a>説明

このサービスは、ローカル サービス キャッシュまたはピア サービス キャッシュのいずれかがいっぱいになったときに呼び出される、ユーザー指定のコールバック関数をインストールします。 サービス キャッシュがいっぱいになると、mDNS リソース レコードをそれ以上追加できなくなります。 さまざまな文字列長のサービスが追加されたり削除されたりすると、内部断片化の結果としてサービス キャッシュがいっぱいになる可能性があることに注意してください。 アプリケーションは、ピア サービス キャッシュのキャッシュがいっぱいという通知を受信すると、サービス "*nx_mdns_service_cache_clear*" を使用して、ピア サービス キャッシュ内のすべてのエントリを消去できます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): mDNS のキャッシュ通知コールバック関数が正常にインストールされました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set mDNS cache notify callback. */

status = nx_mdns_cache_notify_set(&my_mdns, cache_full_nofiy_cb);

/* If status is NX_SUCCESS, mDNS cache notify callback was set. */
```

## <a name="nx_mdns_cache_notify_clear"></a>nx_mdns_cache_notify_clear

mDNS のサービス キャッシュ満杯通知関数をクリアします

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_cache_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>説明

このサービスは、ユーザー指定のサービス キャッシュ通知コールバック関数をクリアします。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): mDNS のサービス キャッシュ通知コールバック関数が正常にクリアされました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Clear mDNS cache notify callback. */

status = nx_mdns_cache_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, mDNS cache notify callback clear. */
```

## <a name="nx_mdns_domain_name_set"></a>nx_mdns_domain_name_set

ドメイン名を設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_domain_name_set(NX_MDNS *mdns_ptr, CHAR *domain_name);
```

### <a name="description"></a>説明

このサービスは、既定のローカル ドメイン名を設定します。 mDNS インスタンスが作成されると、既定のローカル ドメイン名が ".local" に設定されます。 この API を使用すると、アプリケーションは既定のローカル ドメイン名を上書きできます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **domain_name**: 使用するドメイン名。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): ローカル ドメインが正常に構成されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the domain name. */

status = nx_mdns_domain_name_set(&my_mdns, “home”);

/* If status is NX_SUCCESS, the “home” domain name was set. */
```

## <a name="nx_mdns_service_announcement_timing_set"></a>nx_mdns_service_announcement_timing_set

サービス アナウンス メッセージのタイミング パラメーターを設定します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_announcement_timing_set(NX_MDNS *mdns_ptr,
    UINT t, UINT p, UINT k, UINT retrans_interval,
    UINT period_interval, UINT max_time);
```

### <a name="description"></a>説明

このサービスは、サービス アナウンスの送信時に mDNS によって使用されるタイミング パラメーターを再構成します。 公開期間は、ティック数 *t* から始まり、2 の *k* 乗で自在に拡張できます。 公開通知あたりの繰り返し回数は *p*、繰り返される各公開通知の間隔は *interval* のティック数、アナウンス期間の数値は max_time です。 既定では、最初の期間は 1 秒に設定されており、k = 1 (期間は毎回 2 倍になります)、*p = 1* (繰り返しなし)、retrans_interval = 0 (間隔なし)、period_interval = 0xFFFFFFFF (最大期間間隔)、および max_time = 3 (公開通知の数) となっています。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **t**: 最初の期間のティック数。 既定値は 100 ティック (1 秒) です。
- **p**: 繰り返しの数。 既定値は 1 です。
- **k**: テレスコープ係数。 既定値は 1 です。
- **retrans_interval**: 繰り返しされるアナウンス メッセージを送信する前に待機するティック数。 既定値は 0 です。
- **period_interval**: 2 つのアナウンス期間の間のティック数。 既定値は 0xFFFFFFFF です。
- **max_time**: 公開通知に使用するアナウンス期間の数値。 *max_time* のアナウンス期間が過ぎると、アナウンス メッセージはそれ以上送信されません。 既定値は 3 です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): タイミングの値が正常に設定されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the service announcement timing. */

status = nx_mdns_service_announcement_timing_set(&my_mdns, 100,
    1, 1, 0, 0xFFFFFFFF, 3);

/* If status is NX_SUCCESS, the service announcement timing was set. */
```

## <a name="nx_mdns_service_add"></a>nx_mdns_service_add

ローカル サービスを追加します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_add(NX_MDNS *mdns_ptr, CHAR *instance,
    CHAR *service, CHAR *subtype, UINT ttl, USHORT priority,
    USHORT weight, USHORT port, UCHAR *text, UCHAR is_unique,
    UINT interface_index);
```

### <a name="description"></a>説明

この API は、アプリケーションが提供するサービスを登録します。 フラグ *is_unique* が設定されている場合、mDNS は、ネットワーク上でサービスのアナウンスを開始する前に、サービス名をプローブして、それがローカル ネットワーク上で一意であることを確認します。 *instance* は、サービス名のインスタンス部分です。 *service* は、サービス名のサービス部分です。 たとえば、"_http._tcp" はサービスです。 サブタイプを使用してサービスを記述するには、呼び出し元で *subtype* パラメーターを使用する必要があります。 たとえば、目的のサービスが "_printer._sub._http._tcp" の場合、サービス フィールドは "_http._tcp:"、サブタイプ フィールドは "_printer" です。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **instance**: サービスのインスタンス名を指すポインター。
- **service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。
- **subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。
- **priority**: サービスの優先度
- **weight**: サービスの重み
- **port**: サービスが使用する TCP または UDP ポート番号
- **text**: 追加のテキスト情報
- **is_unique**: サービスが共有されているか一意であるかを示すブール型のフラグ。 一意として登録されるサービスの場合、mDNS は、ネットワーク上のサービスをプローブしてから、その提供を開始する必要があります。
- **Interface_index**: サービスが提供される際に使用される物理インターフェイス。 接続型サービスのいずれかを介して提供されるサービスの場合、値 *NX_MDNS_ALL_INTERFACES* が使用されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービスが正常に登録されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Add local service. */

status = nx_mdns_service_add(&my_mdns, “NETX-SERVICE”,
    “_http._tcp”, NX_NULL,
    NX_NULL, 0, 0, 0, 80, NX_TRUE, 0);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was added. */
```

## <a name="nx_mdns_service_delete"></a>nx_mdns_service_delete

以前に登録されたサービスを削除します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_delete(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype);
```

### <a name="description"></a>説明

この API は、以前に登録されたサービスを削除します。 サービスが削除されると、"goodbye" メッセージがローカル ネットワークに送信されるため、隣接ノードに通知されます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **instance**: サービスのインスタンス名を指すポインター。
- **service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。
- **subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービスが正常に削除されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete local service. */

status = nx_mdns_service_delete(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The service (NetX-SERVICE._http._tcp.local) was deleted. */
```

## <a name="nx_mdns_service_one_shot_query"></a>nx_mdns_service_one_shot_query

ワンショット サービス検出を開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_one_shot_query(NX_MDNS *mdns_ptr,
    UCHAR *instance,
    UCHAR *service,
    UCHAR *subtype,
    NX_MDNS_SERVICE *service_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、ワンショット mDNS クエリを実行します。 指定したサービスがピア サービス キャッシュ内に見つかった場合は、最初のインスタンスが返されます。 ローカル ピア サービス キャッシュ内にサービスが見つからない場合、mDNS モジュールは、クエリ コマンドを発行し、応答を待機します。 このサービスは、最初の回答を受信するか、クエリがタイムアウトするまで、ブロックされます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **instance**: サービスのインスタンス名を指すポインター (該当する場合)。
- **service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。 アプリケーションでは、サービスの種類を指定する必要があります。
- **subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。
- **service_ptr**: クエリ結果を格納する NX_MDNS_SERVICE 構造体を指すユーザー指定のポインター。
- **wait_option**: 応答を待機する時間 (ティック数)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービス情報が正常に取得されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start service one shot query. */

status = nx_mdns_service_one_shot_query(&my_mdns, “NETX-SERVICE”, “_http._tcp”,
    NX_NULL, service_ptr, 500);

/* If status is NX_SUCCESS, The query with
    name: NetX-SERVICE._http._tcp.local,
     type: ANY (SRV and TXT) was sent.
    And the answer was stored in service_ptr if success. */
```

## <a name="nx_mdns_service_continuous_query"></a>nx_mdns_service_continuous_query

連続サービス検出を開始します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_continous_query(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>説明

このサービスは、連続クエリを開始します。 サービスから即座に制御が返されることに注意してください。 連続クエリを発行した後、アプリケーションは、API *nx_mdns_service_lookup* を使用してサービス レコードを取得することができます。 連続クエリを停止するために、アプリケーションは、API *nx_mdns_service_query_stop* を使用することができます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **instance**: サービスのインスタンス名を指すポインター (該当する場合)。
- **service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター (該当する場合)。
- **subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): 連続クエリが正常に開始されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Start service continuous query. */

status = nx_mdns_service_continuous_query(&my_mdns,
    “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was added.
    And the query will be periodically sent. */
```

## <a name="nx_mdns_service_query_stop"></a>nx_mdns_service_query_stop

以前に発行された連続サービス検出を停止します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_query_stop(NX_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service, CHAR *subtype);
```

### <a name="description"></a>説明

この API は、以前に発行された連続サービス検出を終了します。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **instance**: サービスのインスタンス名を指すポインター。
- **service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター。
- **subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): 連続クエリが正常に停止されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop service continuous query. */

status = nx_mdns_service_query_stop(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL);

/* If status is NX_SUCCESS, The continuous query with
    name: NetX-SERVICE._http._tcp.local,
    type: ANY (SRV and TXT) was stopped. */
```

## <a name="nx_mdns_service_lookup"></a>nx_mdns_service_lookup

ローカル ピア サービス キャッシュからサービスを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_lookup(NXD_MDNS *mdns_ptr,
    CHAR *instance, CHAR *service,
    CHAR *subtype, UINT instance_index,
    NXD_MDNS_SERVICE *service_ptr);
```

### <a name="description"></a>説明

このサービスは、インスタンス名 (指定されている場合) とサービスの種類が一致するサービスをローカル ピア サービス キャッシュ内で検索します。 アプリケーションは、記述に一致するキャッシュ内の最初のサービスの *instance_index* を 0 に設定して、サービスの検索を開始する必要があります。 アプリケーションは、キャッシュの末尾を示す *NX_NO_MORE_ENTRIES* がサービスから返されるまで、キャッシュ内で追加のサービスが見つかるたびに *instance_index* 値を引き上げながらこのサービスを使用し続ける必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **instance**: サービスのインスタンス名を指すポインター (該当する場合)。
- **service**: サブタイプ情報を除く、mDNS サービスの種類を指すポインター (該当する場合)。
- **subtype**: mDNS サービスのサブタイプ部分を指すポインター (該当する場合)。
- **Instance_index**: 返されるインスタンスのインデックス番号。
- **service_ptr**: 検索結果を格納する NX_MDNS_SERVICE 構造体を指すユーザー指定のポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービスが正常に取得されました
- **NX_NO_MORE_ENTRIES** (0x17): 指定されたインデックス番号にサービス エントリが見つかりません。 このエラー コードは、検索の終了を示します。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Lookup the service on specific index. */

status = nx_mdns_service_lookup(&my_mdns, “NETX-SERVICE”, “_http._tcp”, NX_NULL,
    0, service_ptr);

/* If status is NX_SUCCESS, The service with
    name: NetX-SERVICE._http._tcp.local, was retrieved. */
```

## <a name="nx_mdns_service_ignore_set"></a>nx_mdns_service_ignore_set

サービス無視セットを構成します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_ignore_set(NX_MDNS *mdns_ptr, ULONG service_mask);
```

### <a name="description"></a>説明

この API は、*service_mask* ビットマスクで指定されたサービスを無視するようマスクを構成します。 ユーザーは、必要に応じて service_mask を使用して、キャッシュしないサービスの種類を選択できます。 サービスの一覧は、*nxd_mdns.c* 内のテーブル *nx_mdns_service_types* で定義されています。 nx_mdns_service_types[] 内の最初のサービスの種類に対応するマスクは 0x00000001、2 番目のサービスの種類のマスクは 0x00000002 のようになります。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **service_mask**: 無視するユーザー定義のサービスの種類。 マスクは、32 ビットの ULONG 型です。 各ビットは、ユーザー定義の *nx_mdns_service_types* 配列内のエントリを表します。 ビットが設定されている場合、*nx_mdns_service_type* 配列で指定された対応するサービスの種類はピア サービス キャッシュに格納されません。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): サービス無視マスクが正常に設定されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the service mask to ignore the specified service. */

status = nx_mdns_service_ignore_set(&my_mdns, 0x00000003);

/* If status is NX_SUCCESS, The service with
    type “_device-info” and “_http” will be ignored. */
```

## <a name="nx_mdns_service_notify_set"></a>nx_mdns_service_notify_set

サービス変更通知コールバック関数を構成します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_notify_set(NX_MDNS *mdns_ptr, ULONG service_mask,
    VOID (*service_change_notify)(NX_MDNS *mdns_ptr,
    NX_MDNS_SERVICE *service_ptr, UINT state));
```

### <a name="description"></a>説明

この API は、サービス変更通知コールバック関数を構成します。 このコールバック関数は、ネットワーク上の他のノードによって提供されるサービスが追加または変更されたとき、あるいは使用できなくなったときに呼び出されます。 ユーザーは、必要に応じて service_mask を使用して、監視するサービスの種類を選択できます。 監視対象のサービスのリストは、*nxd_mdns.c* 内のテーブル *nx_mdns_service_types* にハードコーディングされています。

nx_mdns_service_types[] 内の最初のサービスの種類に対応するマスクは 0x00000001、2 番目のサービスの種類のマスクは 0x00000002 のようになります。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **service_mask**: 監視するユーザー定義のサービスの種類。 マスクは、32 ビットの ULONG 型です。 各ビットは、*nx_mdns_service_types* 配列内のエントリを表します。
- **service_change_notify**: 指定されたサービスが変更されたときに呼び出されるコールバック関数。 詳細なサービス情報は、*service_ptr* が指すメモリに返されます。 コールバック通知関数から制御が返された後はメモリ内のコンテンツが無効であることに注意してください。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): コールバック関数が正常にインストールされました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Set the service mask to notify the specified service. */

status = nx_mdns_service_notify_set(&my_mdns, 0x00000002, service_change_notify);

/* If status is NX_SUCCESS, the callback will be called
    if received the service with type “_http”. */
```

## <a name="nx_mdns_service_notify_clear"></a>nx_mdns_service_notify_clear

サービス変更通知コールバック関数をクリアします

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_service_notify_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>説明

この API は、サービス変更通知コールバック関数をクリアします。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): コールバック関数が正常にクリアされました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Clear the service notify. */

status = nx_mdns_service_notify_clear(&my_mdns);

/* If status is NX_SUCCESS, the service notify function clear. */
```

## <a name="nx_mdns_host_address_get"></a>nx_mdns_host_address_get

ホスト アドレスを取得します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_host_address_get(NX_MDNS *mdns_ptr,
    UCHAR *host_name, ULONG *ipv4_address,
    ULONG *ipv6_address, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスは、ホスト IPv4 および IPv6 アドレスに対する mDNS クエリを実行します。 指定されたホスト名のアドレスがピア サービス キャッシュ内に見つかった場合は、そのアドレスが返されます。 アドレスがピア サービス キャッシュ内に見つからない場合、mDNS モジュールは、A および AAAA 型のクエリを発行し、応答を待機します。 この API は、回答が受信されるかクエリがタイムアウトするまでブロックされます。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。
- **host_name**: ホスト名を指すポインター。
- **ipv4_address**: IPv4 アドレスの記憶領域用に 4 バイトでアラインされたアドレスを指すポインター。 ユーザーは、IPv4 アドレス用に 4 バイトの領域を割り当てる必要があります。 アプリケーションが IPv4 アドレスを取得する必要がない場合は、NX_NULL アドレスをこの API に渡すことができます。
- **ipv6_address**: IPv6 アドレスの記憶領域用に 4 バイトでアラインされたアドレスを指すポインター。 ユーザーは、IPv6 アドレス用に 16 バイトの領域を割り当てる必要があります。 アプリケーションが IPv6 アドレスを取得する必要がない場合は、NX_NULL アドレスをこの API に渡すことができます。
- **wait_option**: 応答を待機する時間 (ティック数)。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): ホスト アドレスが正常に取得されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
ULONG ipv4_address;
ULONG ipv6_address[4];

/* Get the IP address of specified host. */
status = nx_mdns_host_address_get(&my_mdns, “MDNS-Host”, &ipv4_address, ipv6_address, 500);

/* If status is NX_SUCCESS, the IP address of specified host was retrieved. */
```

## <a name="nx_mdns_local_cache_clear"></a>nx_mdns_local_cache_clear

すべてのローカル サービスを消去します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_local_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>説明

このサービスは、Goodbye メッセージを送信した後、ローカル サービス キャッシュ内のすべてのエントリをクリアします。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): キャッシュ内のすべてのエントリが正常に消去されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Clear the local cache, delete all local service. */

status = nx_mdns_local_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of local cache were deleted. */
```

## <a name="nx_mdns_peer_cache_clear"></a>nx_mdns_peer_cache_clear

検出されたすべてのサービスを消去します

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_mdns_peer_cache_clear(NX_MDNS *mdns_ptr);
```

### <a name="description"></a>説明

このサービスは、ピア サービス キャッシュ内のすべてのエントリをクリアします。

### <a name="input-parameters"></a>入力パラメーター

- **mdns_ptr**: mDNS 制御ブロックを指すポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00): キャッシュ内のすべてのエントリが正常に消去されました。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Clear the peer cache, delete all peer service. */

status = nx_mdns_peer_cache_clear(&my_mdns);

/* If status is NX_SUCCESS, all services and resource records of peer cache were deleted. */
```
