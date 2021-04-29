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
# <a name="chapter-3---functional-components-of-usbx-device-stack"></a><span data-ttu-id="b5528-103">第 3 章 - USBX デバイス スタックの機能コンポーネント</span><span class="sxs-lookup"><span data-stu-id="b5528-103">Chapter 3 - Functional Components of USBX Device Stack</span></span>

<span data-ttu-id="b5528-104">この章では、ハイ パフォーマンスの USBX 埋め込み USB デバイス スタックについて、機能の観点から説明します。</span><span class="sxs-lookup"><span data-stu-id="b5528-104">This chapter contains a description of the high performance USBX embedded USB device stack from a functional perspective.</span></span>

## <a name="execution-overview"></a><span data-ttu-id="b5528-105">実行の概要</span><span class="sxs-lookup"><span data-stu-id="b5528-105">Execution Overview</span></span>

<span data-ttu-id="b5528-106">デバイスの USBX は、いくつかのコンポーネントで構成されます。</span><span class="sxs-lookup"><span data-stu-id="b5528-106">USBX for the device is composed of several components.</span></span>

- <span data-ttu-id="b5528-107">初期化</span><span class="sxs-lookup"><span data-stu-id="b5528-107">Initialization</span></span>
- <span data-ttu-id="b5528-108">アプリケーション インターフェイスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="b5528-108">Application interface calls</span></span>
- <span data-ttu-id="b5528-109">デバイス クラス</span><span class="sxs-lookup"><span data-stu-id="b5528-109">Device Classes</span></span>
- <span data-ttu-id="b5528-110">USB デバイス スタック</span><span class="sxs-lookup"><span data-stu-id="b5528-110">USB Device Stack</span></span>
- <span data-ttu-id="b5528-111">デバイス コントローラー</span><span class="sxs-lookup"><span data-stu-id="b5528-111">Device controller</span></span>
- <span data-ttu-id="b5528-112">VBUS マネージャー</span><span class="sxs-lookup"><span data-stu-id="b5528-112">VBUS manager</span></span>

<span data-ttu-id="b5528-113">次の図は、USBX デバイス スタックを示したものです。</span><span class="sxs-lookup"><span data-stu-id="b5528-113">The following diagram illustrates the USBX Device stack.</span></span>

![USBX デバイス スタック](media/usbx-device-stack/usbx-device-stack.png)

### <a name="initialization"></a><span data-ttu-id="b5528-115">初期化</span><span class="sxs-lookup"><span data-stu-id="b5528-115">Initialization</span></span>

<span data-ttu-id="b5528-116">USBX をアクティブにするには、関数 ***ux_system_initialize*** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-116">In order to activate USBX, the function ***ux_system_initialize*** must be called.</span></span> <span data-ttu-id="b5528-117">この関数により、USBX のメモリ リソースが初期化されます。</span><span class="sxs-lookup"><span data-stu-id="b5528-117">This function initializes the memory resources of USBX.</span></span>

<span data-ttu-id="b5528-118">USBX デバイス機能をアクティブにするには、関数 ***ux_device_stack_initialize*** を呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-118">In order to activate USBX device facilities, the function ***ux_device_stack_initialize*** must be called.</span></span> <span data-ttu-id="b5528-119">この関数により、USBX デバイス スタックによって使用されるすべてのリソース (ThreadX スレッド、ミューテックス、セマフォなど) が初期化されます。</span><span class="sxs-lookup"><span data-stu-id="b5528-119">This function will in turn initialize all the resources used by the USBX device stack such as ThreadX threads, mutexes, and semaphores.</span></span>

<span data-ttu-id="b5528-120">USB デバイス コントローラーと 1 つ以上の USB クラスをアクティブにするには、アプリケーションの初期化が必要です。</span><span class="sxs-lookup"><span data-stu-id="b5528-120">It is up to the application initialization to activate the USB device controller and one or more USB classes.</span></span> <span data-ttu-id="b5528-121">USB ホスト側とは対照的に、デバイス側では、USB コントローラー ドライバーを常に 1 つしか実行できません。</span><span class="sxs-lookup"><span data-stu-id="b5528-121">Contrary to the USB host side, the device side can have only one USB controller driver running at any time.</span></span> <span data-ttu-id="b5528-122">スタックにクラスが登録され、デバイス コントローラー初期化関数が呼び出されると、バスがアクティブになり、スタックがバス リセットとホスト列挙のコマンドに応答します。</span><span class="sxs-lookup"><span data-stu-id="b5528-122">When the classes have been registered to the stack and the device controller(s) initialization function has been called, the bus is active and the stack will reply to bus reset and host enumeration commands.</span></span>

### <a name="application-interface-calls"></a><span data-ttu-id="b5528-123">アプリケーション インターフェイスの呼び出し</span><span class="sxs-lookup"><span data-stu-id="b5528-123">Application Interface Calls</span></span>

<span data-ttu-id="b5528-124">USBX には、2 つのレベルの API があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-124">There are two levels of APIs in USBX.</span></span>

- <span data-ttu-id="b5528-125">USB デバイス スタック API</span><span class="sxs-lookup"><span data-stu-id="b5528-125">USB Device Stack APIs</span></span>
- <span data-ttu-id="b5528-126">USB デバイス クラス API</span><span class="sxs-lookup"><span data-stu-id="b5528-126">USB Device Class APIs</span></span>

<span data-ttu-id="b5528-127">通常、USBX アプリケーションでは、どの USB デバイス スタック API も呼び出す必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b5528-127">Normally, a USBX application should not have to call any of the USB device stack APIs.</span></span> <span data-ttu-id="b5528-128">ほとんどのアプリケーションは、USB クラス API にのみアクセスします。</span><span class="sxs-lookup"><span data-stu-id="b5528-128">Most applications will only access the USB Class APIs.</span></span>

### <a name="usb-device-stack-apis"></a><span data-ttu-id="b5528-129">USB デバイス スタック API</span><span class="sxs-lookup"><span data-stu-id="b5528-129">USB Device Stack APIs</span></span>

<span data-ttu-id="b5528-130">デバイス スタック API では、USBX デバイス コンポーネント (クラスやデバイス フレームワークなど) の登録が行われます。</span><span class="sxs-lookup"><span data-stu-id="b5528-130">The device stack APIs are responsible for the registration of USBX device components such as classes and the device framework.</span></span>

### <a name="usb-device-class-apis"></a><span data-ttu-id="b5528-131">USB デバイス クラス API</span><span class="sxs-lookup"><span data-stu-id="b5528-131">USB Device Class APIs</span></span>

<span data-ttu-id="b5528-132">クラス API は、USB クラスごとに非常に特化しています。</span><span class="sxs-lookup"><span data-stu-id="b5528-132">The Class APIs are very specific to each USB class.</span></span> <span data-ttu-id="b5528-133">USB クラス用の一般的な API の多くは、デバイスのオープン/クローズ、デバイスとの読み書きなどのサービスを提供します。</span><span class="sxs-lookup"><span data-stu-id="b5528-133">Most of the common APIs for USB classes provided services such as opening/closing a device and reading from and writing to a device.</span></span> <span data-ttu-id="b5528-134">これらの API は、ホスト側と本質的に似ています。</span><span class="sxs-lookup"><span data-stu-id="b5528-134">The APIs are similar in nature to the host side.</span></span>

## <a name="device-framework"></a><span data-ttu-id="b5528-135">デバイス フレームワーク</span><span class="sxs-lookup"><span data-stu-id="b5528-135">Device Framework</span></span>

<span data-ttu-id="b5528-136">USB デバイス側では、デバイス フレームワークの定義が行われます。</span><span class="sxs-lookup"><span data-stu-id="b5528-136">The USB device side is responsible for the definition of the device framework.</span></span> <span data-ttu-id="b5528-137">デバイス フレームワークは、次のセクションで説明するように、3 つのカテゴリに分類されます。</span><span class="sxs-lookup"><span data-stu-id="b5528-137">The device framework is divided into three categories, as described in the following sections.</span></span>

### <a name="definition-of-the-components-of-the-device-framework"></a><span data-ttu-id="b5528-138">デバイス フレームワークのコンポーネントの定義</span><span class="sxs-lookup"><span data-stu-id="b5528-138">Definition of the Components of the Device Framework</span></span>

<span data-ttu-id="b5528-139">デバイス フレームワークの各コンポーネントの定義は、デバイスの性質と、デバイスによって使用されるリソースに関連しています。</span><span class="sxs-lookup"><span data-stu-id="b5528-139">The definition of each component of the device framework is related to the nature of the device and the resources utilized by the device.</span></span> <span data-ttu-id="b5528-140">主なカテゴリは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="b5528-140">Following are the main categories.</span></span>

- <span data-ttu-id="b5528-141">デバイス記述子</span><span class="sxs-lookup"><span data-stu-id="b5528-141">Device Descriptor</span></span>
- <span data-ttu-id="b5528-142">構成記述子</span><span class="sxs-lookup"><span data-stu-id="b5528-142">Configuration Descriptor</span></span>
- <span data-ttu-id="b5528-143">インターフェイス記述子</span><span class="sxs-lookup"><span data-stu-id="b5528-143">Interface Descriptor</span></span>
- <span data-ttu-id="b5528-144">エンドポイント記述子</span><span class="sxs-lookup"><span data-stu-id="b5528-144">Endpoint Descriptor</span></span>

<span data-ttu-id="b5528-145">USBX では、高速と最速の両方のデバイス コンポーネント定義がサポートされています (低速は最速と同じ方法で処理されます)。</span><span class="sxs-lookup"><span data-stu-id="b5528-145">USBX supports device component definition for both high and full speed (low speed being treated the same way as full speed).</span></span> <span data-ttu-id="b5528-146">これにより、高速ホストに接続しているときと最速ホストに接続しているときとで、デバイスの動作を変えられるようになっています。</span><span class="sxs-lookup"><span data-stu-id="b5528-146">This allows the device to operate differently when connected to a high speed or full speed host.</span></span> <span data-ttu-id="b5528-147">一般的な違いは、各エンドポイントのサイズと、デバイスの消費電力です。</span><span class="sxs-lookup"><span data-stu-id="b5528-147">The typical differences are the size of each endpoint and the power consumed by the device.</span></span>

<span data-ttu-id="b5528-148">デバイス コンポーネントの定義では、USB 仕様に従ったバイト文字列の形式がとられます。</span><span class="sxs-lookup"><span data-stu-id="b5528-148">The definition of the device component takes the form of a byte string that follows the USB specification.</span></span> <span data-ttu-id="b5528-149">定義は連続式で、メモリ内でのフレームワークの表現順序は、列挙時にホストに返されるものと同じになります。</span><span class="sxs-lookup"><span data-stu-id="b5528-149">The definition is contiguous and the order in which the framework is represented in memory will be the same as the one returned to the host during enumeration.</span></span>

<span data-ttu-id="b5528-150">次に示すのは、高速 USB フラッシュ ディスクのデバイス フレームワークの例です。</span><span class="sxs-lookup"><span data-stu-id="b5528-150">Following is an example of a device framework for a high speed USB Flash Disk.</span></span>

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

### <a name="definition-of-the-strings-of-the-device-framework"></a><span data-ttu-id="b5528-151">デバイス フレームワークの文字列の定義</span><span class="sxs-lookup"><span data-stu-id="b5528-151">Definition of the Strings of the Device Framework</span></span>

<span data-ttu-id="b5528-152">デバイスでは、文字列は省略可能です。</span><span class="sxs-lookup"><span data-stu-id="b5528-152">Strings are optional in a device.</span></span> <span data-ttu-id="b5528-153">文字列の目的は、デバイスの製造元、製品名、およびリビジョン番号を、USB ホストが Unicode 文字列を通じて認識できるようにすることです。</span><span class="sxs-lookup"><span data-stu-id="b5528-153">Their purpose is to let the USB host know about the manufacturer of the device, the product name, and the revision number through Unicode strings.</span></span>

<span data-ttu-id="b5528-154">メインの文字列は、デバイス記述子に埋め込まれたインデックスです。</span><span class="sxs-lookup"><span data-stu-id="b5528-154">The main strings are indexes embedded in the device descriptors.</span></span> <span data-ttu-id="b5528-155">追加の文字列インデックスを、個々のインターフェイスに埋め込むこともできます。</span><span class="sxs-lookup"><span data-stu-id="b5528-155">Additional strings indexes can be embedded into individual interfaces.</span></span>

<span data-ttu-id="b5528-156">上記のデバイス フレームワークで、3 つの文字列インデックスがデバイス記述子に埋め込まれていると仮定した場合、文字列フレームワークの定義は次のコード例のようになります。</span><span class="sxs-lookup"><span data-stu-id="b5528-156">Assuming the device framework above has three string indexes embedded into the device descriptor, the string framework definition could look like this example code.</span></span>

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

<span data-ttu-id="b5528-157">インデックスは速度非依存であるため、速度ごとに異なる文字列を使用する必要がある場合は、異なるインデックスを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-157">If different strings have to be used for each speed, different indexes must be used as the indexes are speed agnostic.</span></span>

<span data-ttu-id="b5528-158">文字列のエンコードは UNICODE ベースです。</span><span class="sxs-lookup"><span data-stu-id="b5528-158">The encoding of the string is UNICODE-based.</span></span> <span data-ttu-id="b5528-159">UNICODE エンコード標準の詳細については、次のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5528-159">For more information on the UNICODE encoding standard refer to the following publication:</span></span>

<span data-ttu-id="b5528-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2 (Unicode 標準 - 世界的文字エンコード、第 1 版、第 1 巻および第 2 巻)、Unicode コンソーシアム、Addison-Wesley 出版社 (マサチューセッツ州レディング)。*</span><span class="sxs-lookup"><span data-stu-id="b5528-160">*The Unicode Standard, Worldwide Character Encoding, Version 1., Volumes 1 and 2, The Unicode Consortium, Addison-Wesley Publishing Company, Reading MA.*</span></span>

### <a name="definition-of-the-languages-supported-by-the-device-for-each-string"></a><span data-ttu-id="b5528-161">各文字列に対してデバイスでサポートされる言語の定義</span><span class="sxs-lookup"><span data-stu-id="b5528-161">Definition of the Languages Supported by the Device for each String</span></span>

<span data-ttu-id="b5528-162">USBX では、英語が既定値ですが、複数の言語をサポートすることができます。</span><span class="sxs-lookup"><span data-stu-id="b5528-162">USBX has the ability to support multiple languages although English is the default.</span></span> <span data-ttu-id="b5528-163">文字列記述子の各言語の定義では、次に示すように、言語定義の配列の形式がとられます。</span><span class="sxs-lookup"><span data-stu-id="b5528-163">The definition of each language for the string descriptors is in the form of an array of languages definition defined as follows.</span></span>

```c
#define LANGUAGE_ID_FRAMEWORK_LENGTH 2
UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="b5528-164">追加の言語をサポートするには、言語コードの 2 バイト定義を、既定の英語コードの後に追加します。</span><span class="sxs-lookup"><span data-stu-id="b5528-164">To support additional languages, simply add the language code double-byte definition after the default English code.</span></span> <span data-ttu-id="b5528-165">言語コードは、Microsoft のドキュメントで定義されています。</span><span class="sxs-lookup"><span data-stu-id="b5528-165">The language code has been defined by Microsoft in the document.</span></span>

<span data-ttu-id="b5528-166">*Developing International Software for Windows 95 and Windows NT (Windows 95 および Windows NT 向けのインターナショナル ソフトウェアの開発)、Nadine Kano、Microsoft Press (ワシントン州レドモンド)*</span><span class="sxs-lookup"><span data-stu-id="b5528-166">*Developing International Software for Windows 95 and Windows NT, Nadine Kano, Microsoft Press, Redmond WA*</span></span>

## <a name="vbus-manager"></a><span data-ttu-id="b5528-167">VBUS マネージャー</span><span class="sxs-lookup"><span data-stu-id="b5528-167">VBUS Manager</span></span>

<span data-ttu-id="b5528-168">ほとんどの USB デバイス設計では、VBUS は USB デバイス コアの一部ではなく、回線信号を監視する外部 GPIO に接続されています。</span><span class="sxs-lookup"><span data-stu-id="b5528-168">In most USB device designs, VBUS is not part of the USB Device core but rather connected to an external GPIO, which monitors the line signal.</span></span>

<span data-ttu-id="b5528-169">そのため、VBUS はデバイス コントローラー ドライバーとは別に管理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-169">As a result, VBUS has to be managed separately from the device controller driver.</span></span>

<span data-ttu-id="b5528-170">デバイス コントローラーに VBUS IO のアドレスを提供する操作は、アプリケーションで行います。</span><span class="sxs-lookup"><span data-stu-id="b5528-170">It is up to the application to provide the device controller with the address of the VBUS IO.</span></span> <span data-ttu-id="b5528-171">VBUS は、デバイス コントローラーを初期化する前に初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-171">VBUS must be initialized prior to the device controller initialization.</span></span>

<span data-ttu-id="b5528-172">VBUS の監視に関するプラットフォームの仕様によっては、VBUS IO が初期化された後に、コントローラー ドライバーで VBUS のシグナルを処理できるようにすることもできます。それができない場合は、VBUS を処理するためのコードをアプリケーションで提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="b5528-172">Depending on the platform specification for monitoring VBUS, it is possible to let the controller driver handle VBUS signals after the VBUS IO is initialized or if this is not possible, the application has to provide the code for handling VBUS.</span></span>

<span data-ttu-id="b5528-173">アプリケーション自身で VBUS を処理するのが望ましい場合、その唯一の要件は、デバイスが抽出されたことをアプリケーションが検出したときに、関数 ***ux_device_stack_disconnect*** を呼び出すことです。</span><span class="sxs-lookup"><span data-stu-id="b5528-173">If the application wishes to handle VBUS by itself, its only requirement is to call the function ***ux_device_stack_disconnect*** when it detects that a device has been extracted.</span></span> <span data-ttu-id="b5528-174">BUS RESET アサート/デアサート シグナルが検出されたときにはコントローラーがウェイクアップするため、デバイスがいつ挿入されたかをコントローラーに通知する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="b5528-174">It is not necessary to inform the controller when a device is inserted because the controller will wake up when the BUS RESET assert/deassert signal is detected.</span></span>
