---
title: 第 3 章 - Azure RTOS NetX Duo AutoIP サービスの説明
description: この章では、すべての Azure RTOS NetX Duo AutoIP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82a186505104983dbe6964f92e89c8e775d545eedb6495e27f21542d7660bf42
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791195"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-autoip-services"></a>第 3 章 - Azure RTOS NetX Duo AutoIP サービスの説明

この章では、すべての Azure RTOS NetX Duo AutoIP サービス (以下に記載) をアルファベット順に説明します。

次の API の説明の「戻り値」セクションでは、**太字** の値が API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nx_auto_ip_create**: *AutoIP インスタンスを作成する*
- **nx_auto_ip_delete**: *AutoIP インスタンスを削除する*
- **nx_auto_ip_get_address**: *現在の AutoIP アドレスを取得する*
- **nx_auto_ip_set_interface**: *AutoIP アドレスが必要な IP インターフェイスを設定する*
- **nx_auto_ip_start**: *AutoIP 処理を開始する*
- **nx_auto_ip_stop**: *AutoIP 処理を停止する*

## <a name="nx_auto_ip_create"></a>nx_auto_ip_create

AutoIP インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_auto_ip_create(NX_AUTO_IP *auto_ip_ptr, CHAR *name,
                    NX_IP *ip_ptr, VOID *stack_ptr, ULONG stack_size,
                    UINT priority);
```

### <a name="description"></a>説明

このサービスでは、指定された IP インスタンス上に AutoIP インスタンスを作成します。

### <a name="input-parameters"></a>入力パラメーター

- **auto_ip_ptr**: AutoIP 制御ブロックへのポインター。
- **name**: AutoIP インスタンスの名前。
- **ip_ptr**: IP インスタンスへのポインター。
- **stack_ptr**: AutoIP スレッド スタック領域へのポインター。
- **stack_size**: AutoIP スレッド スタック領域のサイズ。
- **priority**: AutoIP スレッドの優先度。

> [!NOTE]
> DHCP が使用される場合は、DHCP スレッドの優先度を IP インスタンス スレッドと AutoIP スレッドより高くする必要があります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) AutoIP の作成に成功しました。
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP の作成のエラー。
- NX_PTR_ERROR: (0x16) AutoIP、ip_ptr、またはスタック ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create the AutoIP instance "auto_ip_0" on "ip_0". */
status = nx_auto_ip_create(&auto_ip_0, "AutoIP 0", &ip_0, pointer, 4096, 1);

/* If status is NX_SUCCESS an AutoIP instance was successfully created. */
```

### <a name="see-also"></a>参照

nx_auto_ip_delete、nx_auto_ip_set_interface、nx_auto_ip_get_address、nx_auto_ip_start、nx_auto_ip_stop

## <a name="nx_auto_ip_delete"></a>nx_auto_ip_delete

AutoIP インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_auto_ip_delete(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>説明

このサービスでは、指定された IP インスタンス上の以前に作成された AutoIP インスタンスを削除します。

### <a name="input-parameters"></a>入力パラメーター

- **auto_ip_ptr**: AutoIP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) AutoIP の削除に成功しました。
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP の削除のエラー。
- NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_delete(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully deleted. */
```

### <a name="see-also"></a>参照

nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_get_address、nx_auto_ip_start、nx_auto_ip_stop

## <a name="nx_auto_ip_get_address"></a>nx_auto_ip_get_address

現在の AutoIP アドレスを取得する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_auto_ip_get_address(NX_AUTO_IP *auto_ip_ptr,
                            ULONG *local_ip_address);
```

### <a name="description"></a>説明

このサービスでは、現在設定されている AutoIP アドレスを取得します。 存在しない場合は、0.0.0.0 の IP アドレスが返されます。

### <a name="input-parameters"></a>入力パラメーター

- **auto_ip_ptr**: AutoIP 制御ブロックへのポインター。
- **local_ip_address**: 戻り IP アドレスの宛先。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) AutoIP アドレスの取得に成功しました。
- **NX_AUTO_IP_NO_LOCAL**: (0xA01) 有効な AutoIP アドレスがありません。
- NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、タイマー、スレッド、ISR

### <a name="example"></a>例

```c
ULONG local_address;

/* Get the AutoIP address resolved by the instance "auto_ip_0." */
status = nx_auto_ip_get_address(&auto_ip_0, &local_address);

/* If status is NX_SUCCESS the local IP address is in "local_address." */
```

### <a name="see-also"></a>参照

nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_start、nx_auto_ip_stop

## <a name="nx_auto_ip_set_interface"></a>nx_auto_ip_set_interface

AutoIP のネットワーク インターフェイスを設定する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_auto_ip_set_interface(NX_AUTO_IP *auto_ip_ptr,
                            UINT interface_index);
```

### <a name="description"></a>説明

このサービスでは、AutoIP でネットワーク IP アドレスをプローブするネットワーク インターフェイスのインデックスを設定します。 既定値は 0 (プライマリ ネットワーク インターフェイス) です。 マルチホーム デバイスにのみ適用されます。

### <a name="input-parameters"></a>入力パラメーター

- **auto_ip_ptr**: AutoIP 制御ブロックへのポインター。
- **interface_index**: IP アドレスをプローブするインターフェイス。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) AutoIP インターフェイスの設定に成功しました。
- **NX_AUTO_IP_BAD_INTERFACE_INDEX**: (0xA02) ネットワーク インターフェイスが無効です NX_PTR_ERROR (0x16) AutoIP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、タイマー、スレッド、ISR

### <a name="example"></a>例

```c
ULONG interface_index;

/* Set the network interface on which AutoIP probes for host address. */
status = nx_auto_ip_set_interface(&auto_ip_0, interface_index);

/* If status is NX_SUCCESS the network interface is valid and set in the AutoIP control block *auto_ip_0*. */
```

### <a name="see-also"></a>参照

nx_auto_ip_create、nx_auto_ip_get_address、nx_auto_ip_delete、nx_auto_ip_start、nx_auto_ip_stop

## <a name="nx_auto_ip_start"></a>nx_auto_ip_start

AutoIP 処理を開始する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_auto_ip_start(NX_AUTO_IP *auto_ip_ptr,
                    ULONG starting_local_address);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された AutoIP インスタンス上で AutoIP プロトコルを開始します。

### <a name="input-parameters"></a>入力パラメーター

- **auto_ip_ptr**: AutoIP 制御ブロックへのポインター。
- **starting_local_address**: 省略可能な AutoIP の開始アドレス。 IP_ADDRESS(0,0,0,0) の値は、ランダムな AutoIP アドレスを派生させる必要があることを指定します。 それ以外の場合は、有効な AutoIP アドレスが指定されていると、NetX AutoIP ではそのアドレスを割り当てようとします。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) AutoIP の開始に成功しました。
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP の開始のエラー。
- NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Start the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_start(&auto_ip_0, IP_ADDRESS(0,0,0,0));

/* If status is NX_SUCCESS an AutoIP instance was successfully started. */
```

### <a name="see-also"></a>参照

nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_get_address、nx_auto_ip_stop

## <a name="nx_auto_ip_stop"></a>nx_auto_ip_stop

AutoIP 処理を停止する

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_auto_ip_stop(NX_AUTO_IP *auto_ip_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成されて開始された AutoIP インスタンス上の AutoIP プロトコルを停止します。 このサービスは通常、IP アドレスが DHCP 経由または手動で AutoIP 以外のアドレスに変更されているときに使用されます。

### <a name="input-parameters"></a>入力パラメーター

- **auto_ip_ptr**: AutoIP 制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) AutoIP の停止に成功しました。
- **NX_AUTO_IP_ERROR**: (0xA00) AutoIP の停止のエラー。
- NX_PTR_ERROR: (0x16) AutoIP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Stop the AutoIP instance "auto_ip_0." */
status = nx_auto_ip_stop(&auto_ip_0);

/* If status is NX_SUCCESS an AutoIP instance was successfully stopped. */
```

### <a name="see-also"></a>参照

nx_auto_ip_create、nx_auto_ip_set_interface、nx_auto_ip_delete、nx_auto_ip_get_address、nx_auto_ip_start