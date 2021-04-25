---
title: 第 3 章 - USBX ホスト スタックの機能コンポーネント
description: この章では、ハイ パフォーマンスの USBX 埋め込み USB ホスト スタックについて、機能の観点から説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 17b8d884dd2c71d60e91f5fcec40c360060f4fe8
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104813184"
---
# <a name="chapter-3---functional-components-of-usbx-host-stack"></a>第 3 章 - USBX ホスト スタックの機能コンポーネント

この章では、ハイ パフォーマンスの USBX 埋め込み USB ホスト スタックについて、機能の観点から説明します。

## <a name="execution-overview"></a>実行の概要

USBX は、以下の複数のコンポーネントで構成されています。

- 初期化
- アプリケーション インターフェイスの呼び出し
- ルート ハブ
- ハブ クラス
- ホスト クラス
- USB ホスト スタック
- ホスト コントローラー

次の図は、USBX ホスト スタックを示しています。

![USBX ホスト スタック](./media/usbx-host-stack/usbx-host-stack.png)

### <a name="initialization"></a>初期化

USBX をアクティブにするには、関数 ***ux_system_initialize*** を呼び出す必要があります。 この関数により、USBX のメモリ リソースが初期化されます。

USBX ホスト機能をアクティブにするには、関数 ***ux_host_stack_initialize*** を呼び出す必要があります。 この関数により、ThreadX ホスト スタックによって使用されるすべてのリソース (ThreadX スレッド、ミューテックス、セマフォなど) が初期化されます。

少なくとも 1 つの USB ホスト コントローラーと 1 つ以上の USB クラスをアクティブにするには、アプリケーションの初期化が必要です。 スタックにクラスが登録され、ホスト コントローラー初期化関数が呼び出されると、バスがアクティブになり、デバイスの検出を開始できます。 接続されているデバイスがホスト コントローラーのルート ハブによって検出されると、USB トポロジを担当する USB 列挙スレッドがウェイク アップし、デバイスの列挙に進みます。

ルート ハブと下流ハブの性質上、ホスト コントローラー初期化関数から制御が戻ったときに、接続されているすべての USB デバイスがまだ完全に構成されていない可能性があります。 特にルート ハブと USB デバイスの間に 1 つ以上のハブがある場合、すべての USB デバイスを列挙するのに数秒かかることがあります。

### <a name="application-interface-calls"></a>アプリケーション インターフェイスの呼び出し

USBX には、2 つのレベルの API があります。

- USB ホスト スタック API
- USB ホスト クラス API

通常、USBX アプリケーションでは、どの USB ホスト スタック API 関数も呼び出す必要はありません。 ほとんどのアプリケーションは、USB クラス API 関数にのみアクセスします。

### <a name="usb-host-stack-apis"></a>USB ホスト スタック API

ホスト スタック API 関数は、USBX コンポーネント (ホスト クラスとホスト コントローラー) の登録、デバイスの構成、および使用可能なデバイス エンドポイントの転送要求を担当します。

### <a name="usb-host-class-api"></a>USB ホスト クラス API

クラス API は、USB クラスごとに非常に特化しています。 USB クラス用の一般的な API 関数の多くは、デバイスのオープン/クローズ、デバイスとの読み書きなどのサービスを提供します。

### <a name="root-hub"></a>ルート ハブ

ホスト コントローラーの各インスタンスには、1 つ以上の USB ルート ハブがあります。 ルート ハブの数は、コントローラーの性質によって決まります。または、コントローラーから特定のレジスタを読み取ることによっても取得できます。

### <a name="hub-class"></a>ハブ クラス

ハブ クラスは、USB ハブの駆動を担当します。 USB ハブは、スタンドアロン ハブとするか、またはキーボードやモニターなどの複合デバイスの一部とすることもできます。 ハブは、セルフパワー型またはバスパワー型とすることができます。 バスパワー型のハブには最大 4 つの下流ポートを搭載でき、使用電力が 100mA 未満であるセルフパワー型またはバスパワー型のデバイスのみを接続できます。 ハブはカスケード化できます。 最大 5 つのハブを相互に接続できます。

### <a name="usb-host-stack"></a>USB ホスト スタック

USB ホスト スタックは、USBX の中核を成しています。 主に 3 つの機能を持ちます。

- USB のトポロジを管理する。
- 1 つ以上のクラスに USB デバイスをバインドする。
- デバイス記述子問い合わせと USB 転送を実行するための API をクラスに提供する。

### <a name="topology-manager"></a>トポロジ マネージャー

新しいデバイスが接続されたとき、またはデバイスの接続が解除されたときに、USB スタック トポロジ スレッドがウェイク アップします。 ルート ハブまたは通常のハブのいずれも、デバイスの接続を受け入れることができます。 USB にデバイスが接続されると、トポロジ マネージャーはデバイス記述子を取得します。 この記述子には、そのデバイスで使用可能な構成の数が含まれています。 ほとんどのデバイスは 1 つの構成のみを持ちます。 一部のデバイスは、接続先のポートで利用可能な電力に応じて、異なる動作が可能です。 この場合、デバイスには利用可能な電力に応じて選択できる複数の構成があります。 トポロジ マネージャーによってデバイスが構成されると、その構成記述子で指定されている電力を消費できるようになります。

## <a name="usb-class-binding"></a>USB クラスのバインド

デバイスが構成されたら、トポロジ マネージャーによって、クラス マネージャーがデバイスのインターフェイス記述子を確認してデバイスの検出を続行できるようになります。 デバイスには、1 つ以上のインターフェイス記述子を持たせることができます。

インターフェイスは、デバイス内の機能を表します。 たとえば USB スピーカーには、オーディオ ストリーミング用、オーディオ コントロール用、各種スピーカー ボタン管理用の 3 つのインターフェイスがあります。

クラス マネージャーには、デバイス インターフェイスを 1 つ以上のクラスに結合するためのメカニズムが 2 種類あります。 すなわち、インターフェイス記述子で見つかった PID/VID (製品 ID とベンダー ID) の組み合わせを使用する方法と、クラス/サブクラス/プロトコルの組み合わせを使用する方法です。

PID/VID の組み合わせは、汎用クラスでは駆動できないインターフェイスに対して有効です。 クラス/サブクラス/プロトコルの組み合わせは、プリンターやハブ、ストレージ、オーディオ、HID などの、USB-IF 認定クラスに属しているインターフェイスによって使用されます。

クラス マネージャーには、USBX の初期化によって登録されたクラスの一覧が含まれています。 クラス マネージャーは、いずれかのクラスがそのデバイスのインターフェイスの管理を引き受けるまで、各クラスを 1 つずつ呼び出し続けます。 1 つのクラスは、1 つのインターフェイスのみを管理できます。 USB オーディオ スピーカーの例では、各インターフェイスに対してクラス マネージャーがすべてのクラスを呼び出します。

クラスがインターフェイスを引き受けると、そのクラスの新しいインスタンスが作成されます。 次にクラス マネージャーは、そのインターフェイスの既定の代替設定を検索します。 デバイスでは、インターフェイスごとに 1 つ以上の代替設定を持つことができます。 クラスで変更が決定されるまでは、代替設定 0 が既定で使用されます。

既定の代替設定では、クラス マネージャーによって代替設定に含まれるすべてのエンドポイントがマウントされます。 各エンドポイントのマウントが成功すると、クラス マネージャーはインターフェイスの初期化を完成させるクラスに戻り、そのジョブを完了させます。

### <a name="usbx-apis"></a>USBX API

USB スタックから、一定の数の API がエクスポートされます。これは、USB クラスがデバイス上で問い合わせおよび特定のエンドポイントでの USB 転送を実行するためのものです。 これらの API 関数の詳細については、こちらのリファレンス マニュアルを参照してください。

### <a name="host-controller"></a>ホスト コントローラー

ホスト コントローラー ドライバーは、特定の種類の USB コントローラーを駆動する役割を担います。 USB ホスト コントローラーは、複数のコントローラーを内蔵できます。 たとえば、ある Intel PC チップセットには、2 つの UHCI コントローラーが内蔵されています。 一部の USB 2.0 コントローラーには、EHCI コントローラーのインスタンス 1 つに加えて、OHCI コントローラーのインスタンスが複数内蔵されています。

ホスト コントローラーは、同じコントローラーの複数のインスタンスのみを管理します。 ほとんどの USB 2.0 ホスト コントローラーを駆動するためには、USBX の初期化時に OCHI コントローラーと EHCI コントローラーの両方を初期化する必要があります。

ホスト コントローラーは、次の管理を担当します。

- ルート ハブ
- 電源管理
- エンドポイント
- 転送

### <a name="root-hub"></a>ルート ハブ

ルート ハブの管理は、各コントローラー ポートの電源を入れ、デバイスが挿入されているかどうかを判定する役割を担います。 この機能は、コントローラーの下流ポートに問い合わせを行うために USBX 汎用ルート ハブによって使用されます。

### <a name="power-management"></a>電源管理

電源管理の処理では、中断/再開信号を扱います。ギャング モードにしてコントローラーのすべての下流ポートに同時に影響を与えるようにするか、または (コントローラー側で対応している場合は) 各ポートに対して個別に行います。

### <a name="endpoints"></a>エンドポイント

エンドポイント管理では、コントローラーに対する物理エンドポイントの作成または破棄を行うことができます。 物理エンドポイントとはメモリ エンティティであり、マスタ DMA をサポートしているコントローラーによって解析される場合と、コントローラーに書き込まれている場合があります。 物理エンドポイントには、コントローラーによって実行されるトランザクション情報が含まれています。

### <a name="transfers"></a>転送

転送管理では、作成された各エンドポイントでトランザクションを実行するクラスが提供されます。 各論理エンドポイントには、USB 転送要求用のTRANSFER REQUEST と呼ばれるコンポーネントが含まれています。 TRANSFER REQUEST は、トランザクションを記述するためにスタックによって使用されます。 その後、この TRANSFER REQUEST はスタックとコントローラーに渡され、コントローラーの機能に応じていくつかのサブ トランザクションに分割することができます。

## <a name="usb-device-framework"></a>USB デバイスのフレームワーク

USB デバイスは、記述子のツリーによって表されます。 記述子には、6 つの主要な種類があります。

- デバイス記述子
- 構成記述子
- インターフェイス記述子
- エンドポイント記述子
- 文字列記述子
- 機能記述子

USB デバイスは非常に簡単に記述することができ、次のようになります。
![簡単な USB デバイス](./media/usbx-host-stack/usb-device-simple.png)

上の図では、デバイスに含まれる構成は 1 つだけです。 この構成には 1 つのインターフェイスがアタッチされています。これは、このデバイスの機能が 1 つだけで、エンドポイントも 1 つだけであることを示しています。 デバイス記述子にアタッチされている文字列記述子は、デバイスの識別を可視化しています。

ただし、より複雑なデバイスとすることも可能であり、その場合は次のように表示されます。

![複雑な USB デバイス](./media/usbx-host-stack/usb-device-complex.png)

上の図のデバイスでは、デバイス記述子に 2 つの構成記述子がアタッチされています。 このデバイスは、電源モードが 2 つあることを示している場合もあれば、標準クラスと各社独自のクラスのどちらでも駆動できることを示している場合もあります。

最初の構成には 2 つのインターフェイスがアタッチされており、デバイスに 2 つの論理機能があることを示しています。 最初の機能には、3 つのエンドポイント記述子と 1 つの機能記述子があります。 機能記述子は、このインターフェイスに関して汎用記述子には通常含まれていない追加情報を取得するために、インターフェイスの駆動を担当するクラスによって使用される場合があります。

### <a name="device-descriptors"></a>デバイス記述子

各 USB デバイスには、1 つのデバイス記述子があります。 この記述子には、デバイス識別子、サポートされている構成の数、およびデバイスの構成に使用される既定のコントロール エンドポイントの特性が含まれます。

| Offset | フィールド              | Size | 値    | 説明                             |
| ------ | ------------------ | ---- | -------- | --------------------------------------- |
| 0      | BLength            | 1    | 数値   | この記述子のサイズ (byte 単位) |
| 1      | bDescriptorType    | 1    | 一定 | デバイス記述子の型 |
| 2      | bcdUSB             | 2    | BCD●bcd○      | USB 仕様リリース番号 (2 進化 10 進数)<br />例: 2.10 は 0x210 と等しいです。 このフィールドは、デバイスとその記述子が準拠している USB 仕様のリリースを特定します。 |
| 4      | bDeviceClass       | 1    | クラス    | クラス コード (USB-IF により割り当てられる)。<br />このフィールドが 0 にリセットされた場合、構成内の各インターフェイスが自身のクラス情報を指定し、さまざまなインターフェイスが独立して動作します。<br />このフィールドが 1 から 0xFE の範囲の値に設定された場合、デバイスは異なるインターフェイスごとに異なるクラス仕様をサポートすることになり、インターフェイスは独立して動作しない場合があります。 この値は、インターフェイスの集合に使用されるクラス定義を特定します。<br />このフィールドが 0xFF に設定された場合、デバイス クラスはベンダー固有となります。 |
| 5      | bDeviceSubClass    | 1    | サブクラス | サブクラス コード (USB-IF により割り当てられる)。<br />これらのコードは、bDeviceClass フィールドの値によって修飾されます。 bDeviceClass フィールドが 0 にリセットされた場合、このフィールドも 0 にリセットする必要があります。 bDeviceClass フィールドが 0xFF に設定されていない場合、すべての値が USB による割り当て用に予約されます。 |
| 6      | bDeviceProtocol    | 1    | プロトコル | プロトコル コード (USB-IF により割り当てられる)。<br />これらのコードは、bDeviceClass フィールドと bDeviceSubClass フィールドの値によって修飾されます。 インターフェイス ベースではなくデバイス ベースでクラス固有プロトコルをサポートしているデバイスの場合、このコードはデバイスが使用するプロトコルを、デバイス クラスの仕様による定義に従って特定します。 このフィールドが 0 にリセットされた場合、デバイスはクラス固有プロトコルをデバイス ベースで使用しません。<br />ただし、クラス固有プロトコルをインターフェイス ベースで使用することはできます。<br />このフィールドが 0xFF に設定された場合、デバイスはベンダー固有プロトコルをデバイス ベースで使用します。 |
| 7      | bMaxPacketSize0    | 1    | 数値   | エンドポイント 0 の最大パケット サイズ (byte サイズ 8、16、32、または 64 のみ有効) |
| 8      | idVendor           | 2    | id       | ベンダー ID (USB-IF により割り当てられる) |
| 10     | idProduct          | 2    | id       | 製品 ID (製造元により割り当てられる) |
| 12     | bcdDevice          | 2    | BCD●bcd○      | デバイス リリース番号 (2 進化 10 進数) |
| 14     | iManufacturer      | 1    | インデックス    | 製造元を記述する文字列記述子のインデックス |
| 15     | iProduct           | 1    | インデックス    | 製品を記述する文字列記述子のインデックス |
| 16     | iSerialNumbe       | 1    | インデックス    | デバイスのシリアル番号を記述する文字列記述子のインデックス |
| 17     | bNumConfigurations | 1    | 数値   | 可能な構成の数 |

USBX では、USB デバイス記述子を次のように定義します。

```c
typedef struct UX_DEVICE_DESCRIPTOR_STRUCT
{
    UINT      bLength;
    UINT      bDescriptorType;
    USHORT    bcdUSB;
    UINT      bDeviceClass;
    UINT      bDeviceSubClass;
    UINT      bDeviceProtocol;
    UINT      bMaxPacketSize0;
    USHORT    idVendor;
    USHORT    idProduct;
    USHORT    bcdDevice;
    UINT      iManufacturer;
    UINT      iProduct;
    UINT      iSerialNumber;
    UINT      bNumConfigurations;
} UX_DEVICE_DESCRIPTOR;
```

USB デバイス記述子は、次に示すデバイス コンテナーの一部となっています。

```c
typedef struct UX_DEVICE_STRUCT
{
    ULONG ux_device_handle;
    ULONG ux_device_type;
    ULONG ux_device_state;
    ULONG ux_device_address;
    ULONG ux_device_speed;
    ULONG ux_device_port_location;
    ULONG ux_device_max_power;
    ULONG ux_device_power_source;
    UINT ux_device_current_configuration;

    TX_SEMAPHORE ux_device_protection_semaphore;
    struct UX_DEVICE_STRUCT *ux_device_parent; 
    struct UX_HOST_CLASS_STRUCT *ux_device_class; 
    VOID *ux_device_class_instance;
    struct UX_HCD_STRUCT *ux_device_hcd;
    struct UX_CONFIGURATION_STRUCT *ux_device_first_configuration; 
    struct UX_DEVICE_STRUCT *ux_device_next_device;
    struct UX_DEVICE_DESCRIPTOR_STRUCT ux_device_descriptor;
    struct UX_ENDPOINT_STRUCT ux_device_control_endpoint;
    struct UX_HUB_TT_STRUCT ux_device_hub_tt[UX_MAX_TT];
} UX_DEVICE;
```

- **ux_device_handle**: デバイスのハンドル。 これは通常、デバイスのこの構造体のインスタンスのアドレスです。
- **ux_device_type**: 古い値。 未使用。
- **ux_device_state**: デバイスの状態。次のいずれかの値を指定できます。
    - **UX_DEVICE_RESET**                0
    - **UX_DEVICE_ATTACHED**             1
    - **UX_DEVICE_ADDRESSED**            2
    - **UX_DEVICE_CONFIGURED**           3
    - **UX_DEVICE_SUSPENDED**            4
    - **UX_DEVICE_RESUMED**              5
    - **UX_DEVICE_SELF_POWERED_STATE**   6
    - **UX_DEVICE_SELF_POWERED_STATE**   7
    - **UX_DEVICE_REMOTE_WAKEUP**        8
    - **UX_DEVICE_BUS_RESET_COMPLETED**  9
    - **UX_DEVICE_REMOVED**              10
    - **UX_DEVICE_FORCE_DISCONNECT**     11
- **ux_device_address**: **SET_ADDRESS** コマンドが受け付けられた後のデバイスのアドレス (1 から 127)。
- **ux_device_speed**: デバイスの速度。
    - **UX_LOW_SPEED_DEVICE**      0
    - **UX_FULL_SPEED_DEVICE**     1
    - **UX_HIGH_SPEED_DEVICE**     2
- **ux_device_port_location**: 親デバイス (ルート ハブまたはハブ) のポートのインデックス。
- **ux_device_max_power**: 選択された構成においてデバイスが取り込むことのできる最大電力 (単位 mA)。
- **ux_device_power_source**: 次の 2 つの値のうちのいずれかを指定できます。
    - **UX_DEVICE_BUS_POWERED**     1
    - **UX_DEVICE_SELF_POWERED**    2
- **ux_device_current_configuration**: このデバイスで現在使用されている構成のインデックス。
- **ux_device_parent**: このデバイスの親のデバイス コンテナー ポインター。 ポインターが null 値の場合、親はコントローラーのルート ハブです。
- **ux_device_class**: このデバイスを所有するクラス型へのポインター。
- **ux_device_class_instance**: このデバイスを所有するクラスのインスタンスへのポインター。
- **ux_device_hcd**: このデバイスがアタッチされる USB ホスト コントローラー インスタンス。
- **ux_device_first_configuration**: このデバイスの最初の構成コンテナーへのポインター。
- **ux_device_next_device**: USBX によって検出される任意のバス上にあるデバイスの一覧内の、次のデバイスへのポインター。
- **ux_device_descriptor**: USB デバイス記述子。
- **ux_device_control_endpoint**: このデバイスで使用される既定のコントロール エンドポイントの記述子。
- **ux_device_hub_tt**: デバイスのハブ TT の配列

### <a name="configuration-descriptors"></a>構成記述子

構成記述子には、特定のデバイス構成に関する情報を記述します。 USB デバイスには、1 つ以上の構成記述子を含めることができます。 デバイス記述子の **bNumConfigurations** フィールドには、構成記述子の数が示されます。 記述子には **bConfigurationValue** フィールドが含まれており、その値が Set Configuration 要求へのパラメーターとして使用された場合、デバイスは記述された構成を取るようになります。

記述子には、構成によって提供されるインターフェイスの数を記述します。 各インターフェイスはデバイス内の論理機能を表し、それぞれ独立して動作することが可能です。 たとえば USB オーディオ スピーカーの場合、オーディオ ストリーミング用インターフェイス、オーディオ コントロール用インターフェイス、スピーカー ボタン管理用の HID インターフェイスの計 3 つのインターフェイスを設けることができます。

ホストが構成記述子に対して GET_DESCRIPTOR 要求を発行すると、関連するすべてのインターフェイス記述子およびエンドポイント記述子が返されます。

| Offset | フィールド               | Size | 値    | 説明                       |
| ------ | ------------------- | ---- | -------- | --------------------------------- |
| 0      | bLength             | 1    | 数値   | この記述子のサイズ (byte 単位) |
| 1      | bDescriptorType     | 1    | 一定 | CONFIGURATION                     |
| 2      | wTotalLength        | 2    | 数値   | この構成に対して返されるデータの合計長さ。 この構成に対して返されるすべての記述子 (構成、インターフェイス、エンドポイント、クラスまたはベンダー固有) を合計した長さが含まれます。 |
| 4      | bNumInterfaces      | 1    | 数値   | この構成でサポートされるインターフェイスの数。 |
| 5      | bConfigurationValue | 1    | 数値   | この構成を選択するために Set<br/>Configuration の引数として使用する値。 |
| 6      | iConfiguration      | 1    | インデックス    | この構成を記述する文字列記述子のインデックス。 |
| 7      | bMAttributes        | 1    | Bitmap   | 構成特性 D7 バス パワー<br />D6 セルフ パワー<br />D5 リモート ウェイクアップ<br />D4..0 予約済み (0 にリセット)<br />バス パワーおよびローカル電源を使用するデバイス構成では、D7 と D6 の両方を設定します。 実行時の実際の電源は、Get Status デバイス要求を使用して決定することもできます。<br />デバイス構成がリモート ウェイクアップをサポートしている場合は、D5 を 1 に設定します。 |
| 8      | MaxPower            | 1    | mA       | デバイスが完全に動作しているときの、この特定の構成における USB デバイスのバス パワーからの最大消費電力。<br />2 mA 単位で表現します (例: 50 = 100 mA)。<br />注: デバイス構成は、構成がバスパワーとセルフパワーのどちらであるかを報告します。<br />デバイスの状態は、デバイスが現在セルフパワーで動作しているかどうかを報告します。 デバイスの外部電源との接続が切断された場合、デバイスの状態が更新され、セルフパワーではなくなったことが示されます。 |

USBX では、USB 構成記述子を次のように定義します。

```c
typedef struct UX_CONFIGURATION_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT wTotalLength;
    UINT bNumInterfaces;
    UINT bConfigurationValue;
    UINT iConfiguration;
    UINT bmAttributes;
    UINT MaxPower;
} UX_CONFIGURATION_DESCRIPTOR;
```

USB 構成記述子は、次に示す構成コンテナーの一部となっています。

```c
typedef struct UX_CONFIGURATION_STRUCT
{
    ULONG ux_configuration_handle;
    ULONG ux_configuration_state;
    struct UX_CONFIGURATION_DESCRIPTOR_STRUCT ux_configuration_descriptor;
    struct UX_INTERFACE_STRUCT *ux_configuration_first_interface;
    struct UX_CONFIGURATION_STRUCT *ux_configuration_next_configuration;
    struct UX_DEVICE_STRUCT *ux_configuration_device;
} UX_CONFIGURATION;
```

- **ux_configuration_handle**: 構成のハンドル。 これは通常、構成のこの構造体のインスタンスのアドレスです。
- **ux_configuration_state**: 構成の状態。
- **ux_configuration_descriptor**: USB デバイス記述子。
- **ux_configuration_first_interface**: この構成の最初のインターフェイスへのポインター。
- **ux_configuration_next_configuration**: 同じデバイスの次の構成へのポインター。
- **ux_configuration_device**: この構成のデバイス所有者へのポインター。

### <a name="interface-descriptors"></a>インターフェイス記述子

インターフェイス記述子には、構成内の特定のインターフェイスを記述します。 インターフェイスとは、USB デバイス内の論理機能です。 構成には、1 つ以上のインターフェイスが用意されています。各インターフェイスには、構成内のエンドポイントの一意のセットを記述する 0 個以上のエンドポイント記述子が含まれます。 複数のインターフェイスをサポートしている構成の場合、特定のインターフェイスのエンドポイント記述子は、指定された構成の **GET_DESCRIPTOR** 要求によって返されるデータに含まれるインターフェイス記述子に従います。

インターフェイス記述子は、常に構成記述子の一部として返されます。 GET_DESCRIPTOR 要求によってインターフェイス記述子に直接アクセスすることはできません。

インターフェイスには、デバイスが構成された後にエンドポイントやその特性を変化させることを可能にする代替設定を含めることができます。 インターフェイスの既定の設定では、常に代替設定は 0 です。 クラスによって現在の代替設定を変更して、インターフェイスの動作および関連するエンドポイントの特性を変更することができます。 代替設定の選択や既定の設定への復帰には、SET_INTERFACE 要求を使用します。

代替設定を使用すると、他のインターフェイスを動作させたままで、デバイスの構成の一部を変更することができます。 1 つ以上のインターフェイスに対する代替設定を持つ構成の場合、それぞれの設定には、個別のインターフェイス記述子と、その関連するエンドポイントが含まれます。

デバイス構成に 2 つの代替設定を持つ 1 つのインターフェイスが含まれている場合、構成に対して GET_DESCRIPTOR 要求を行うと構成記述子が返され、次に **bInterfaceNumber** フィールドと **bAlternateSetting** フィールドが 0 に設定されたインターフェイス記述子が返され、次いでその設定のエンドポイント記述子が返されます。その後で、もう 1 つのインターフェイス記述子とそれに関連するエンドポイント記述子が返されます。 2 番目のインターフェイス記述子では、**bInterfaceNumber** フィールドは 0 に設定されていますが、**bAlternateSetting** フィールドは 1 に設定されています。これは、この代替設定が最初のインターフェイスに属していることを示しています。

関連するエンドポイントを持たないインターフェイスもあります。この場合、そのインターフェイスに対しては既定のコントロール エンドポイントのみが有効です。

代替設定は、主にインターフェイスに関連する周期的なエンドポイントに対する要求帯域幅を変更するために使用されます。 たとえば、USB スピーカーのストリーミング インターフェイスの場合、最初の代替設定で、アイソクロナス エンドポイントでの帯域幅の要求を 0 とする必要があります。 その他の代替設定では、オーディオ ストリーミング周波数に応じて異なる帯域幅要件を選択できます。

インターフェイスの USB 記述子は次のとおりです。

| Offset | フィールド              | Size | 値     | 記述子                              |
| ------ | ------------------ | ---- | --------- | --------------------------------------- |
| 0      | bLength            | 1    | 数値    | この記述子のサイズ (byte 単位)       |
| 1      | bDescriptorType    | 1    | 一定  | インターフェイス記述子の型               |
| 2      | bInterfaceNumber   | 1    | 数値    | インターフェイスの番号。 この構成でサポートされているコンカレント インターフェイスの配列内のインデックスを特定する、0 から始まる値。 |
| 3      | bAltenateSetting   | 1    | 数値    | 前のフィールドで特定されたインターフェイスに対する代替設定を選択するために使用される値。 |
| 4      | bNumEndpoints      | 1    | 数値    | このインターフェイスで使用されているエンドポイントの数 (エンドポイント 0 を除く)。 この値が 0 の場合、このインターフェイスはエンドポイント 0 のみを使用します。 |
| 5      | bInterfaceClass    | 1    | クラス     | クラス コード (USB により割り当てられる)<br />このフィールドが 0 にリセットされた場合、インターフェイスはどの USB 指定デバイス クラスにも属しません。<br />このフィールドが 0xFF に設定された場合、インターフェイス クラスはベンダー固有となります。<br />その他の値はすべて、USB による割り当て用に予約されています。 |
| 6      | bInterfaceSubClass | 1    | サブクラス  | サブクラス コード (USB により割り当てられる)。<br />これらのコードは、bInterfaceClass フィールドの値によって修飾されます。 bInterfaceClass フィールドが 0 にリセットされた場合、このフィールドも 0 にリセットする必要があります。 bInterfaceClass フィールドが 0xFF に設定されていない場合、すべての値が USB による割り当て用に予約されます。 |
| 7      | bInterfaceProtocol | 1    | プロトコル  | プロトコル コード (USB により割り当てられる)。 これらのコードは、bInterfaceClass フィールドと bInterfaceSubClass フィールドの値によって修飾されます。 インターフェイスがクラス固有の要求をサポートしている場合、このコードはデバイスが使用するプロトコルを、デバイス クラスの仕様による定義に従って特定します。<br />このフィールドが 0 にリセットされた場合、デバイスはこのインターフェイスにクラス固有プロトコルを使用しません。 このフィールドが 0xFF に設定された場合、デバイスはこのインターフェイスにベンダー固有プロトコルを使用します。 |
| 8      | iInterface         | 1    | インデックス     | このインターフェイスを記述する文字列記述子のインデックス。 |

USBX では、USB インターフェイス記述子を次のように定義します。

```c
typedef struct UX_INTERFACE_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bInterfaceNumber;
    UINT bAlternateSetting;
    UINT bNumEndpoints;
    UINT bInterfaceClass
    UINT bInterfaceSubClass;
    UINT bInterfaceProtocol;
    UINT iInterface;
} UX_INTERFACE_DESCRIPTOR;
```

USB インターフェイス記述子は、次に示すインターフェイス コンテナーの一部となっています。

```c
typedef struct UX_INTERFACE_STRUCT
{
    ULONG ux_interface_handle;
    ULONG ux_interface_state;
    ULONG ux_interface_current_alternate_setting;
    struct UX_INTERFACE_DESCRIPTOR_STRUCT ux_interface_descriptor;
    struct UX_HOST_CLASS_STRUCT    *ux_interface_class;
    VOID    *ux_interface_class_instance;
    struct UX_ENDPOINT_STRUCT    *ux_interface_first_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_interface_next_interface;
    struct UX_CONFIGURATION_STRUCT    *ux_interface_configuration;
} UX_INTERFACE;
```

- **ux_interface_handle**: インターフェイスのハンドル。 これは通常、インターフェイスのこの構造体のインスタンスのアドレスです。
- **ux_interface_state**: インターフェイスの状態。
- **ux_interface_descriptor**: USB インターフェイス記述子。
- **ux_interface_class**: このインターフェイスを所有するクラス型へのポインター。
- **ux_interface_class_instance**: このインターフェイスを所有するクラスのインスタンスへのポインター。
- **ux_interface_first_endpoint**: このインターフェイスで登録される最初のエンドポイントへのポインター。
- **ux_interface_next_interface**: 構成に関連する次のインターフェイスへのポインター。
- **ux_interface_configuration**: このインターフェイスの構成所有者へのポインター。

### <a name="endpoint-descriptors"></a>エンドポイント記述子

インターフェイスに関連する各エンドポイントには、それぞれ自身のエンドポイント記述子があります。 この記述子には、各エンドポイントの帯域幅要件、エンドポイントに関連する最大ペイロード、周期性、および方向を決定するためにホスト スタックが必要とする情報を記述します。 エンドポイント記述子は常に、構成に対する GET_DESCRIPTOR コマンドによって返されます。

デバイス記述子に関連する既定のコントロール エンドポイントは、インターフェイスに関連するエンドポイントの一部としてはカウントされないため、この記述子では返されません。

ホスト ソフトウェアがインターフェイスの代替設定の変更を要求すると、関連するすべてのエンドポイントとその USB リソースが新しい代替設定に従って変更されます。

既定のコントロール エンドポイントを除き、エンドポイントをインターフェイス間で共有することはできません。

| Offset | フィールド            | Size | 値    | 説明                       |
| ------ | ---------------- | ---- | -------- | --------------------------------- |
| 0      | bLength          | 1    | 数値   | この記述子のサイズ (byte 単位) |
| 1      | bDescriptorType  | 1    | 一定 | エンドポイント記述子の型。 |
| 2      | bEndpointAddress | 1    | エンドポイント | この記述子によって記述される USB デバイス上のエンドポイントのアドレス。 アドレスは次のようにエンコードされます。<br />ビット 3...0: エンドポイント番号<br />ビット 6...4: 予約済み、0 にリセット<br />ビット 7: 方向、コントロール エンドポイントの場合は無視<br />0 = OUT エンドポイント<br />1 = IN エンドポイント |
| 3      | bmAttributes     | 1    | Bitmap   | このフィールドには、**bConfigurationValue** フィールドを使用してエンドポイントを構成する場合のエンドポイントの属性を記述します。 ビット 1..0: 転送の種類<br />00 = コントロール<br />01 = アイソクロナス<br />10 = バルク<br />11 = 割り込み<br />アイソクロナス エンドポイントでない場合は、ビット 5..2 は予約されており、0 に設定する必要があります。 アイソクロナスの場合は、次のように定義されます。<br />ビット 3..2: 同期の種類<br />00 = 同期なし<br />01 = 非同期<br />10 = 適応<br />11 = 同期<br />ビット 5..4: 使用法の種類<br />00 = データ エンドポイント<br />01 = フィードバック エンドポイント<br />10 = 暗黙のフィードバック データ エンドポイント<br />11 = 予約済み |
| 4      | wMaxPacketSize   | 2    | 数値   | この構成を選択した場合に、このエンドポイントで送受信できる最大パケット サイズ。<br />アイソクロナス エンドポイントの場合、この値を使用して、(マイクロ) フレームあたりのデータ ペイロードに必要となるバス時間をスケジュールに予約します。 パイプで実際に継続的に使用される帯域幅は、予約した帯域幅よりも少ない場合があります。 デバイスは必要に応じて、通常の非 USB 定義のメカニズムを介して実際に使用された帯域幅を報告します。<br />すべてのエンドポイントについて、ビット 10..0 は最大パケット サイズ (バイト単位) を指定します。<br />高速アイソクロナスおよび割り込みエンドポイントの場合:<br />ビット 12..11 では、マイクロ フレームあたりの追加トランザクションの機会の数を指定します。00 = なし (マイクロ フレームあたり 1 トランザクション)<br />01 = 1 つ追加 (マイクロ フレームあたり 2)<br />10 = 2 つ追加 (マイクロ フレームあたり 3)<br />11 = 予約済み<br />ビット 15..13 は予約されており、0 に設定する必要があります。 |
| 6      | bInterval        | 1     | 数値   | データ転送用にエンドポイントをポーリングする間隔の値。<br />デバイスの動作速度に応じて、フレームまたはマイクロ フレームで表現されます (1 ミリ秒または 125 マイクロ秒単位のいずれか)。<br />全速/高速アイソクロナス エンドポイントの場合、この値は 1 から 16 の範囲内である必要があります。 **bInterval** は、2bInterval - 1 乗の指数の値として使用されます。たとえば、**bInterval** を 4 とすると、周期は 8 (24-1) となります。<br />全速/低速割り込みエンドポイントの場合、このフィールドの値は 1 から 255 の範囲とすることができます。<br />高速割り込みエンドポイントの場合、**bInterval** は、2bInterval - 1 乗の指数の値として使用されます。たとえば、**bInterval** を 4 とすると、周期は 8 (24-1) となります。 この値は、1 から 16 の範囲内とする必要があります。<br />高速バルク/コントロール OUT エンドポイントの場合、**bInterval** ではエンドポイントの最大 NAK 率を指定します。 値 0 は、エンドポイントで NAK が絶対に発生しないことを示します。 その他の値では、**bInterval** マイクロ フレームごとに最大 1 回の NAK であることを示します。<br />この値は、0 から 255 の範囲内である必要があります。 |

USBX では、USB エンドポイント記述子を次のように定義します。

```c
typedef struct UX_ENDPOINT_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    UINT bEndpointAddress;
    UINT bmAttributes;
    USHORT wMaxPacketSize;
    UINT bInterval;
} UX_ENDPOINT_DESCRIPTOR;
```

USB エンドポイント記述子は、次に示すエンドポイント コンテナーの一部となっています。

```c
typedef struct UX_ENDPOINT_STRUCT {
    ULONG    ux_endpoint_handle;
    ULONG    ux_endpoint_state;
    VOID    *ux_endpoint_ed;
    struct UX_ENDPOINT_DESCRIPTOR_STRUCT    ux_endpoint_descriptor;
    struct UX_ENDPOINT_STRUCT    *ux_endpoint_next_endpoint;
    struct UX_INTERFACE_STRUCT    *ux_endpoint_interface;
    struct UX_DEVICE_STRUCT    *ux_endpoint_device;
    struct UX_TRANSFER REQUEST_STRUCT    ux_endpoint_transfer request;
} UX_ENDPOINT;

```

- **ux_endpoint_handle**: エンドポイントのハンドル。 これは通常、エンドポイントのこの構造体のインスタンスのアドレスです。
- **ux_endpoint_state**: エンドポイントの状態。
- **ux_endpoint_ed**: ホスト コントローラー レイヤーでの物理エンドポイントへのポインター。
- **ux_endpoint_descriptor**: USB エンドポイント記述子。
- **ux_endpoint_next_endpoint**: 同じインターフェイスに属する次のエンドポイントへのポインター。
- **ux_endpoint_interface**: このエンドポイント インターフェイスを所有するインターフェイスへのポインター。
- **ux_endpoint_device**: 親デバイス コンテナーへのポインター。
- **ux_endpoint_transfer request**: デバイスとの間でデータを送受信するために使用される USB 転送要求。

### <a name="string-descriptors"></a>文字列記述子

文字列記述子は省略可能です。 デバイスで文字列記述子がサポートされていない場合は、デバイス記述子、構成記述子、およびインターフェイス記述子内に含まれる文字列記述子への参照を、すべて 0 にリセットする必要があります。

文字列記述子では UNICODE エンコードが使用されるため、複数の文字セットをサポートできます。 USB デバイス内の文字列は、複数の言語をサポートすることが可能です。 文字列記述子を要求する際に要求元は、USB-IF によって定義されている言語 ID を使用して目的の言語を指定します。 現在定義されている USB LANGID の一覧については、『USBX 付録 ??』を参照してください。
すべての言語に対して文字列インデックスを 0 にすると、デバイスでサポートされている 2 バイトの LANGID コードの配列を含む文字列記述子が返されます。 UNICODE 文字列は 0 で終端しない点に注意してください。 代わりに、記述子の先頭バイトに格納されている配列のサイズから 2 を減算することで、文字列配列のサイズを計算します。

USB 文字列記述子 0 は、次のようにエンコードされます。

| Offset | フィールド           | Size | 値    | 説明                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | N+2      | この記述子のサイズ (byte 単位) |
| 1      | bDescriptorType | 1    | 一定 | 文字列記述子の型           |
| 2      | wLANGID[0]      | 2    | 数値   | LANGID コード 0                    |
| ...    | ...]            | ...  | ...      | ...                              |
| N      | wLANGID[n]      | 2    | 数値   | LANGID コード n                    |

他の USB 文字列記述子は、次のようにエンコードされます。

| Offset | フィールド           | Size | 値    | 説明                      |
| ------ | --------------- | ---- | -------- | -------------------------------- |
| 0      | bLength         | 1    | 数値   | この記述子のサイズ (byte 単位) |
| 1      | bDescriptorType | 1    | 一定 | 文字列記述子の型           |
| 2      | bString         | n    | 数値   | UNICODE でエンコードされた文字列           |

USBX では、非 0 長の USB 文字列記述子を次のように定義します。

```c
typedef struct UX_STRING_DESCRIPTOR_STRUCT
{
    UINT bLength;
    UINT bDescriptorType;
    USHORT bString[1];
} UX_STRING_DESCRIPTOR;
```

### <a name="functional-descriptors"></a>機能記述子

機能記述子は、クラス固有記述子とも呼ばれます。 通常は、汎用記述子と同じ基本構造を使用し、追加情報がクラスで使用できるようになります。 たとえば USB オーディオ スピーカーの場合、クラス固有記述子を使用すると、オーディオ クラスはサポートされるオーディオ周波数の種類を代替設定ごとに取得できます。

### <a name="usbx-device-descriptor-framework-in-memory"></a>メモリ内の USBX デバイス記述子フレームワーク

USBX では、ほとんどのデバイス記述子、すなわち文字列と機能記述子を除くすべての記述子がメモリ内に保持されます。 次の図は、これらの記述子がどのように格納され、関連するかを示しています。

![メモリ内の USBX デバイス記述子フレームワーク](./media/usbx-host-stack/usbx-device-descriptor-framework.png)
