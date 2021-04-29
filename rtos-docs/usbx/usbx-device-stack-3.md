---
title: 第 3 章 - USBX デバイス スタックの機能コンポーネント
description: この章では、ハイ パフォーマンスの USBX 埋め込み USB デバイス スタックについて、機能の観点から説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: a20fed71cbee8c50519be4a971eb191e0cc93915
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812242"
---
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a>第 3 章 - USBX デバイス スタックの機能コンポーネント

この章では、ハイ パフォーマンスの USBX 埋め込み USB デバイス スタックについて、機能の観点から説明します。

## <a name="execution-overview"></a>実行の概要

デバイスの USBX は、いくつかのコンポーネントで構成されます。

- 初期化
- アプリケーション インターフェイスの呼び出し
- デバイス クラス
- USB デバイス スタック
- デバイス コントローラー
- VBUS マネージャー

次の図は、USBX デバイス スタックを示したものです。

![USBX デバイス スタック](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a>初期化

USBX をアクティブにするには、関数 ***ux_system_initialize*** を呼び出す必要があります。 この関数により、USBX のメモリ リソースが初期化されます。

USBX デバイス機能をアクティブにするには、関数 ***ux_device_stack_initialize*** を呼び出す必要があります。 この関数により、USBX デバイス スタックによって使用されるすべてのリソース (ThreadX スレッド、ミューテックス、セマフォなど) が初期化されます。

USB デバイス コントローラーと 1 つ以上の USB クラスをアクティブにするには、アプリケーションの初期化が必要です。 USB ホスト側とは対照的に、デバイス側では、USB コントローラー ドライバーを常に 1 つしか実行できません。 スタックにクラスが登録され、デバイス コントローラー初期化関数が呼び出されると、バスがアクティブになり、スタックがバス リセットとホスト列挙のコマンドに応答します。

### <a name="application-interface-calls"></a>アプリケーション インターフェイスの呼び出し

USBX には、2 つのレベルの API があります。

- USB デバイス スタック API
- USB デバイス クラス API

通常、USBX アプリケーションでは、どの USB デバイス スタック API も呼び出す必要はありません。 ほとんどのアプリケーションは、USB クラス API にのみアクセスします。

### <a name="usb-device-stack-apis"></a>USB デバイス スタック API

デバイス スタック API では、USBX デバイス コンポーネント (クラスやデバイス フレームワークなど) の登録が行われます。

### <a name="usb-device-class-apis"></a>USB デバイス クラス API

クラス API は、USB クラスごとに非常に特化しています。 USB クラス用の一般的な API の多くは、デバイスのオープン/クローズ、デバイスとの読み書きなどのサービスを提供します。 これらの API は、ホスト側と本質的に似ています。

## <a name="device-framework"></a>デバイス フレームワーク

USB デバイス側では、デバイス フレームワークの定義が行われます。 デバイス フレームワークは、次のセクションで説明するように、3 つのカテゴリに分類されます。

### <a name="definition-of-the-components-of-the-device-framework"></a>デバイス フレームワークのコンポーネントの定義

デバイス フレームワークの各コンポーネントの定義は、デバイスの性質と、デバイスによって使用されるリソースに関連しています。 主なカテゴリは次のとおりです。

- デバイス記述子
- 構成記述子
- インターフェイス記述子
- エンドポイント記述子

USBX では、高速と最速の両方のデバイス コンポーネント定義がサポートされています (低速は最速と同じ方法で処理されます)。 これにより、高速ホストに接続しているときと最速ホストに接続しているときとで、デバイスの動作を変えられるようになっています。 一般的な違いは、各エンドポイントのサイズと、デバイスの消費電力です。

デバイス コンポーネントの定義では、USB 仕様に従ったバイト文字列の形式がとられます。 定義は連続式で、メモリ内でのフレームワークの表現順序は、列挙時にホストに返されるものと同じになります。

次に示すのは、高速 USB フラッシュ ディスクのデバイス フレームワークの例です。

```c
#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60
UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02, 0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40, 0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0, 0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50, 0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};
```

### <a name="definition-of-the-strings-of-the-device-framework"></a>デバイス フレームワークの文字列の定義

デバイスでは、文字列は省略可能です。 文字列の目的は、デバイスの製造元、製品名、およびリビジョン番号を、USB ホストが Unicode 文字列を通じて認識できるようにすることです。

メインの文字列は、デバイス記述子に埋め込まれたインデックスです。 追加の文字列インデックスを、個々のインターフェイスに埋め込むこともできます。

上記のデバイス フレームワークで、3 つの文字列インデックスがデバイス記述子に埋め込まれていると仮定した場合、文字列フレームワークの定義は次のコード例のようになります。

```c
/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string
*/

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72, 0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};
```

インデックスは速度非依存であるため、速度ごとに異なる文字列を使用する必要がある場合は、異なるインデックスを使用する必要があります。

文字列のエンコードは UNICODE ベースです。 UNICODE エンコード標準の詳細については、次のドキュメントを参照してください。

*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2 (Unicode 標準 - 世界的文字エンコード、第 1 版、第 1 巻および第 2 巻)、Unicode コンソーシアム、Addison-Wesley 出版社 (マサチューセッツ州レディング)。*

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a>各文字列に対してデバイスでサポートされる言語の定義

USBX では、英語が既定値ですが、複数の言語をサポートすることができます。 文字列記述子の各言語の定義では、次に示すように、言語定義の配列の形式がとられます。

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

追加の言語をサポートするには、言語コードの 2 バイト定義を、既定の英語コードの後に追加します。 言語コードは、Microsoft のドキュメントで定義されています。

*Developing International Software for Windows 95 and Windows NT (Windows 95 および Windows NT 向けのインターナショナル ソフトウェアの開発)、Nadine Kano、Microsoft Press (ワシントン州レドモンド)*

## <a name="vbus-manager"></a>VBUS マネージャー

ほとんどの USB デバイス設計では、VBUS は USB デバイス コアの一部ではなく、回線信号を監視する外部 GPIO に接続されています。

そのため、VBUS はデバイス コントローラー ドライバーとは別に管理する必要があります。

デバイス コントローラーに VBUS IO のアドレスを提供する操作は、アプリケーションで行います。 VBUS は、デバイス コントローラーを初期化する前に初期化する必要があります。

VBUS の監視に関するプラットフォームの仕様によっては、VBUS IO が初期化された後に、コントローラー ドライバーで VBUS のシグナルを処理できるようにすることもできます。それができない場合は、VBUS を処理するためのコードをアプリケーションで提供する必要があります。

アプリケーション自身で VBUS を処理するのが望ましい場合、その唯一の要件は、デバイスが抽出されたことをアプリケーションが検出したときに、関数 ***ux_device_stack_disconnect*** を呼び出すことです。 BUS RESET アサート/デアサート シグナルが検出されたときにはコントローラーがウェイクアップするため、デバイスがいつ挿入されたかをコントローラーに通知する必要はありません。
