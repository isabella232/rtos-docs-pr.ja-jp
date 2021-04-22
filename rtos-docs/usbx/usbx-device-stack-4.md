---
title: 第 4 章 - USBX デバイス サービスの説明
description: USBX デバイス サービスについて説明します。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: d4aea7470ba2d9075296164b9d1fb61db4f88523
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812953"
---
# <a name="description-of-usbx-device-services"></a><span data-ttu-id="d3bed-103">USBX デバイス サービスの説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-103">Description of USBX Device Services</span></span>

### <a name="ux_device_stack_alternate_setting_get"></a><span data-ttu-id="d3bed-104">ux_device_stack_alternate_setting_get</span><span class="sxs-lookup"><span data-stu-id="d3bed-104">ux_device_stack_alternate_setting_get</span></span>

<span data-ttu-id="d3bed-105">インターフェイス値の現在の代替設定を取得します</span><span class="sxs-lookup"><span data-stu-id="d3bed-105">Get current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-106">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-106">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_get(ULONG interface_value);
```

### <a name="description"></a><span data-ttu-id="d3bed-107">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-107">Description</span></span>

<span data-ttu-id="d3bed-108">この関数は、特定のインターフェイス値の現在の代替設定を取得するために、USB ホストによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-108">This function is used by the USB host to obtain the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="d3bed-109">**GET_INTERFACE** 要求を受信すると、コントローラー ドライバーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-109">It is called by the controller driver when a **GET_INTERFACE** request is received.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-110">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-110">Input Parameter</span></span>

- <span data-ttu-id="d3bed-111">**Interface_value**: 現在の代替設定に対してクエリを行う対象のインターフェイスの値</span><span class="sxs-lookup"><span data-stu-id="d3bed-111">**Interface_value** Interface value for which the current alternate setting is queried</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-112">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-112">Return Values</span></span>

- <span data-ttu-id="d3bed-113">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-113">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="d3bed-114">**UX_ERROR**: (0xFF) インターフェイス値が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-114">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-115">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-115">Example</span></span>

```c
ULONG interface_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_alternate_setting_set"></a><span data-ttu-id="d3bed-116">ux_device_stack_alternate_setting_set</span><span class="sxs-lookup"><span data-stu-id="d3bed-116">ux_device_stack_alternate_setting_set</span></span>

<span data-ttu-id="d3bed-117">インターフェイス値の現在の代替設定を設定します</span><span class="sxs-lookup"><span data-stu-id="d3bed-117">Set current alternate setting for an interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-118">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-118">Prototype</span></span>

```c
UINT ux_device_stack_alternate_setting_set(
    ULONG interface_value, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="d3bed-119">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-119">Description</span></span>

<span data-ttu-id="d3bed-120">この関数は、特定のインターフェイス値の現在の代替設定を設定するために、USB ホストによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-120">This function is used by the USB host to set the current alternate setting for a specific interface value.</span></span> <span data-ttu-id="d3bed-121">**SET_INTERFACE** 要求を受信すると、コントローラー ドライバーによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-121">It is called by the controller driver when a **SET_INTERFACE** request is received.</span></span> <span data-ttu-id="d3bed-122">**SET_INTERFACE** が完了すると、代替設定の値がクラスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-122">When the **SET_INTERFACE** is completed, the values of the alternate settings are applied to the class.</span></span>

<span data-ttu-id="d3bed-123">デバイス スタックは、このインターフェイスを所有するクラスに **UX_SLAVE_CLASS_COMMAND_CHANGE** を発行して、代替設定の変更を反映します。</span><span class="sxs-lookup"><span data-stu-id="d3bed-123">The device stack will issue a **UX_SLAVE_CLASS_COMMAND_CHANGE** to the class that owns this interface to reflect the change of alternate setting.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-124">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-124">Parameters</span></span>

- <span data-ttu-id="d3bed-125">**Interface_value** 現在の代替設定を設定する対象のインターフェイスの値。</span><span class="sxs-lookup"><span data-stu-id="d3bed-125">**interface_value**: Interface value for which the current alternate setting is set.</span></span>
- <span data-ttu-id="d3bed-126">**alternate_setting_value**: 新しい代替設定値。</span><span class="sxs-lookup"><span data-stu-id="d3bed-126">**alternate_setting_value**: The new alternate setting value.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-127">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-127">Return Values</span></span>

- <span data-ttu-id="d3bed-128">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-128">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="d3bed-129">**UX_INTERFACE_HANDLE_UNKNOWN**: (0x52) インターフェイスがアタッチされていません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-129">**UX_INTERFACE_HANDLE_UNKNOWN** (0x52) No interface attached.</span></span>
- <span data-ttu-id="d3bed-130">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) デバイスが構成されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-130">**UX_FUNCTION_NOT_SUPPORTED** (0x54) Device is not configured.</span></span>
- <span data-ttu-id="d3bed-131">**UX_ERROR**: (0xFF) インターフェイス値が正しくありません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-131">**UX_ERROR** (0xFF) Wrong interface value.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-132">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-132">Example</span></span>

```c
ULONG interface_value;

ULONG alternate_setting_value;

/* The following example illustrates this service. */
status = ux_device_stack_alternate_setting_set(interface_value, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_class_register"></a><span data-ttu-id="d3bed-133">ux_device_stack_class_register</span><span class="sxs-lookup"><span data-stu-id="d3bed-133">ux_device_stack_class_register</span></span>

<span data-ttu-id="d3bed-134">新しい USB デバイス クラスを登録します</span><span class="sxs-lookup"><span data-stu-id="d3bed-134">Register a new USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-135">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-135">Prototype</span></span>

```c
UINT ux_device_stack_class_register(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT *),
    ULONG configuration_number, 
    ULONG interface_number,  
    VOID *parameter);
```

### <a name="description"></a><span data-ttu-id="d3bed-136">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-136">Description</span></span>

<span data-ttu-id="d3bed-137">この関数は、新しい USB デバイス クラスを登録するために、アプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-137">This function is used by the application to register a new USB device class.</span></span> <span data-ttu-id="d3bed-138">この登録によって、クラスのインスタンスではなく、クラス コンテナーが開始されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-138">This registration starts a class container and not an instance of the class.</span></span> <span data-ttu-id="d3bed-139">クラスはアクティブなスレッドを持ち、特定のインターフェイスにアタッチされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-139">A class should have an active thread and be attached to a specific interface.</span></span>

<span data-ttu-id="d3bed-140">パラメーターまたはパラメーター リストを必要とするクラスもあります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-140">Some classes expect a parameter or parameter list.</span></span> <span data-ttu-id="d3bed-141">たとえば、デバイス ストレージ クラスは、エミュレートしようとしているストレージ デバイスのジオメトリを必要とします。</span><span class="sxs-lookup"><span data-stu-id="d3bed-141">For instance, the device storage class would expect the geometry of the storage device it is trying to emulate.</span></span> <span data-ttu-id="d3bed-142">したがって、パラメーター フィールドはクラスの要件に依存しており、値になる場合も、またクラス値が設定された構造体へのポインターになる場合もあります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-142">The parameter field is therefore dependent on the class requirement and can be a value or a pointer to a structure filled with the class values.</span></span>

> [!NOTE]
> <span data-ttu-id="d3bed-143">class_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_MAX_CLASS_NAME_LENGTH** よりも大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-143">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-144">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-144">Parameters</span></span>

- <span data-ttu-id="d3bed-145">**class_name**: クラス名</span><span class="sxs-lookup"><span data-stu-id="d3bed-145">**class_name** Class Name</span></span>
- <span data-ttu-id="d3bed-146">**class_entry_function**: クラスのエントリ関数。</span><span class="sxs-lookup"><span data-stu-id="d3bed-146">**class_entry_function** The entry function of the class.</span></span>
- <span data-ttu-id="d3bed-147">**configuration_number**: このクラスがアタッチされている構成番号。</span><span class="sxs-lookup"><span data-stu-id="d3bed-147">**configuration_number** The configuration number this class is attached to.</span></span>
- <span data-ttu-id="d3bed-148">**interface_number**: このクラスがアタッチされているインターフェイス番号。</span><span class="sxs-lookup"><span data-stu-id="d3bed-148">**interface_number** The interface number this class is attached to.</span></span>
- <span data-ttu-id="d3bed-149">**parameter**: クラス固有のパラメーター リストへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-149">**parameter** A pointer to a class specific parameter list.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-150">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-150">Return Values</span></span>

- <span data-ttu-id="d3bed-151">**UX_SUCCESS**: (0x00) クラスが登録されました</span><span class="sxs-lookup"><span data-stu-id="d3bed-151">**UX_SUCCESS** (0x00) The class was registered</span></span>
- <span data-ttu-id="d3bed-152">**UX_MEMORY_INSUFFICIENT**: (0x12) クラス テーブルにエントリが残っていません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-152">**UX_MEMORY_INSUFFICIENT** (0x12) No entries left in class table.</span></span>
- <span data-ttu-id="d3bed-153">**UX_THREAD_ERROR**: (0x16) クラス スレッドを作成できません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-153">**UX_THREAD_ERROR** (0x16) Cannot create a class thread.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-154">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-154">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */

/* Initialize the device storage class. The class is connected with interface 1 */
status = ux_device_stack_class_register(_ux_system_slave_class_storage_name ux_device_class_storage_entry,
    1, 1, (VOID *)&parameter);
```

### <a name="ux_device_stack_class_unregister"></a><span data-ttu-id="d3bed-155">ux_device_stack_class_unregister</span><span class="sxs-lookup"><span data-stu-id="d3bed-155">ux_device_stack_class_unregister</span></span>

<span data-ttu-id="d3bed-156">USB デバイス クラスを登録解除します</span><span class="sxs-lookup"><span data-stu-id="d3bed-156">Unregister a USB device class</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-157">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-157">Prototype</span></span>

```c
UINT ux_device_stack_class_unregister(
    UCHAR *class_name,
    UINT (*class_entry_function)(struct UX_SLAVE_CLASS_COMMAND_STRUCT*));
```

### <a name="description"></a><span data-ttu-id="d3bed-158">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-158">Description</span></span>

<span data-ttu-id="d3bed-159">この関数は、USB デバイス クラスを登録解除するために、アプリケーションによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-159">This function is used by the application to unregister a USB device class.</span></span>

> [!NOTE]
> <span data-ttu-id="d3bed-160">class_name という C の文字列は NULL で終わる必要があり、その長さ (NULL 終端文字自体を除く) は **UX_MAX_CLASS_NAME_LENGTH** よりも大きくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-160">The C string of class_name must be NULL-terminated and the length of it (without the NULL-terminator itself) must be no larger than **UX_MAX_CLASS_NAME_LENGTH**.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-161">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-161">Parameters</span></span>

- <span data-ttu-id="d3bed-162">**class_name**: クラス名</span><span class="sxs-lookup"><span data-stu-id="d3bed-162">**class_name**: Class Name</span></span>
- <span data-ttu-id="d3bed-163">**class_entry_function**: クラスのエントリ関数。</span><span class="sxs-lookup"><span data-stu-id="d3bed-163">**class_entry_function**: The entry function of the class.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-164">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-164">Return Values</span></span>

- <span data-ttu-id="d3bed-165">**UX_SUCCESS**: (0x00) クラスが登録解除されました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-165">**UX_SUCCESS** (0x00) The class was unregistered.</span></span>
- <span data-ttu-id="d3bed-166">**UX_NO_CLASS_MATCH**: (0x57) クラスが登録されていません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-166">**UX_NO_CLASS_MATCH** (0x57) The class isn't registered.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-167">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-167">Example</span></span>

```c
/* The following example illustrates this service. */

/* Unitialize the device storage class. */
status = ux_device_stack_class_unregister(_ux_system_slave_class_storage_name, ux_device_class_storage_entry);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_get"></a><span data-ttu-id="d3bed-168">ux_device_stack_configuration_get</span><span class="sxs-lookup"><span data-stu-id="d3bed-168">ux_device_stack_configuration_get</span></span>

<span data-ttu-id="d3bed-169">現在の構成を取得します</span><span class="sxs-lookup"><span data-stu-id="d3bed-169">Get the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-170">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-170">Prototype</span></span>

```c
UINT ux_device_stack_configuration_get(VOID);
```

### <a name="description"></a><span data-ttu-id="d3bed-171">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-171">Description</span></span>

<span data-ttu-id="d3bed-172">この関数は、デバイスで実行されている現在の構成を取得するために、ホストによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-172">This function is used by the host to obtain the current configuration running in the device.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-173">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-173">Input Parameter</span></span>

<span data-ttu-id="d3bed-174">なし</span><span class="sxs-lookup"><span data-stu-id="d3bed-174">None</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-175">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-175">Return Value</span></span>

- <span data-ttu-id="d3bed-176">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-176">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-177">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-177">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_get();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_configuration_set"></a><span data-ttu-id="d3bed-178">ux_device_stack_configuration_set</span><span class="sxs-lookup"><span data-stu-id="d3bed-178">ux_device_stack_configuration_set</span></span>

<span data-ttu-id="d3bed-179">現在の構成を設定します</span><span class="sxs-lookup"><span data-stu-id="d3bed-179">Set the current configuration</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-180">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-180">Prototype</span></span>

```c
UINT ux_device_stack_configuration_set(ULONG configuration_value);
```

### <a name="description"></a><span data-ttu-id="d3bed-181">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-181">Description</span></span>

<span data-ttu-id="d3bed-182">この関数は、デバイスで実行されている現在の構成を設定するために、ホストによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-182">This function is used by the host to set the current configuration running in the device.</span></span> <span data-ttu-id="d3bed-183">このコマンドを受信すると、USB デバイス スタックは、この構成に接続されている各インターフェイスの代替設定 0 をアクティブにします。</span><span class="sxs-lookup"><span data-stu-id="d3bed-183">Upon reception of this command, the USB device stack will activate the alternate setting 0 of each interface connected to this configuration.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-184">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-184">Input Parameter</span></span>

- <span data-ttu-id="d3bed-185">**configuration_value**: ホストによって選択された構成値。</span><span class="sxs-lookup"><span data-stu-id="d3bed-185">**configuration_value** The configuration value selected by the host.</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-186">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-186">Return Value</span></span>

- <span data-ttu-id="d3bed-187">**UX_SUCCESS**: (0x00) 構成が正常に設定された。</span><span class="sxs-lookup"><span data-stu-id="d3bed-187">**UX_SUCCESS** (0x00) The configuration was successfully set.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-188">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-188">Example</span></span>

```c
ULONG configuration_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_configuration_set(configuration_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_descriptor_send"></a><span data-ttu-id="d3bed-189">ux_device_stack_descriptor_send</span><span class="sxs-lookup"><span data-stu-id="d3bed-189">ux_device_stack_descriptor_send</span></span>

<span data-ttu-id="d3bed-190">記述子をホストに送信します</span><span class="sxs-lookup"><span data-stu-id="d3bed-190">Send a descriptor to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-191">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-191">Prototype</span></span>

```c
UINT ux_device_stack_descriptor_send(
    ULONG descriptor_type, 
    ULONG request_index, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="d3bed-192">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-192">Description</span></span>

<span data-ttu-id="d3bed-193">この関数は、ホストに記述子を返すためにデバイス側で使用されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-193">This function is used by the device side to return a descriptor to the host.</span></span> <span data-ttu-id="d3bed-194">この記述子は、デバイス記述子、構成記述子、文字列記述子のいずれでもかまいません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-194">This descriptor can be a device descriptor, a configuration descriptor or a string descriptor.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-195">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-195">Parameters</span></span>

- <span data-ttu-id="d3bed-196">**descriptor_type**: 記述子のタイプ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-196">**descriptor_type**: The type of the descriptor.</span></span> <span data-ttu-id="d3bed-197">次のいずれかの値を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-197">Must be one of the following values.</span></span>
  - <span data-ttu-id="d3bed-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="d3bed-198">**UX_DEVICE_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="d3bed-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="d3bed-199">**UX_CONFIGURATION_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="d3bed-200">**UX_STRING_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="d3bed-200">**UX_STRING_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="d3bed-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="d3bed-201">**UX_DEVICE_QUALIFIER_DESCRIPTOR_ITEM**</span></span>
  - <span data-ttu-id="d3bed-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span><span class="sxs-lookup"><span data-stu-id="d3bed-202">**UX_OTHER_SPEED_DESCRIPTOR_ITEM**</span></span>
- <span data-ttu-id="d3bed-203">**request_index**: 記述子のインデックス。</span><span class="sxs-lookup"><span data-stu-id="d3bed-203">**request_index**: The index of the descriptor.</span></span>
- <span data-ttu-id="d3bed-204">**host_length**: ホストが必要とする長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-204">**host_length**: The length required by the host.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-205">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-205">Return Values</span></span>

- <span data-ttu-id="d3bed-206">**UX_SUCCESS**: (0x00) データ転送が完了しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-206">**UX_SUCCESS** (0x00) The data transfer was completed.</span></span>
- <span data-ttu-id="d3bed-207">**UX_ERROR**: (0xFF) 転送が完了しませんでした。</span><span class="sxs-lookup"><span data-stu-id="d3bed-207">**UX_ERROR** (0xFF) The transfer was not completed.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-208">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-208">Example</span></span>

```c
ULONG descriptor_type;
ULONG request_index;
ULONG host_length;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_descriptor_send(descriptor_type, request_index, host_length);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_disconnect"></a><span data-ttu-id="d3bed-209">ux_device_stack_disconnect</span><span class="sxs-lookup"><span data-stu-id="d3bed-209">ux_device_stack_disconnect</span></span>

<span data-ttu-id="d3bed-210">デバイス スタックを切断します</span><span class="sxs-lookup"><span data-stu-id="d3bed-210">Disconnect device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-211">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-211">Prototype</span></span>

```c
UINT ux_device_stack_disconnect(VOID);
```

### <a name="description"></a><span data-ttu-id="d3bed-212">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-212">Description</span></span>

<span data-ttu-id="d3bed-213">VBUS マネージャーは、デバイスの切断時にこの関数を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="d3bed-213">The VBUS manager calls this function when there is a device disconnection.</span></span> <span data-ttu-id="d3bed-214">デバイス スタックによって、このデバイスに登録されているすべてのクラスに通知され、その後すべてのデバイス リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-214">The device stack will inform all classes registered to this device and will thereafter release all the device resources.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-215">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-215">Input Parameter</span></span>

<span data-ttu-id="d3bed-216">なし</span><span class="sxs-lookup"><span data-stu-id="d3bed-216">None</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-217">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-217">Return Value</span></span>

- <span data-ttu-id="d3bed-218">**UX_SUCCESS**: (0x00) デバイスが切断されました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-218">**UX_SUCCESS** (0x00) The device was disconnected.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-219">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-219">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_disconnect();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_endpoint_stall"></a><span data-ttu-id="d3bed-220">ux_device_stack_endpoint_stall</span><span class="sxs-lookup"><span data-stu-id="d3bed-220">ux_device_stack_endpoint_stall</span></span>

<span data-ttu-id="d3bed-221">エンドポイント停止条件を要求します</span><span class="sxs-lookup"><span data-stu-id="d3bed-221">Request endpoint Stall condition</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-222">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-222">Prototype</span></span>

```c
UINT ux_device_stack_endpoint_stall(UX_SLAVE_ENDPOINT*endpoint);
```

### <a name="description"></a><span data-ttu-id="d3bed-223">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-223">Description</span></span>

<span data-ttu-id="d3bed-224">この関数は、エンドポイントがホストに停止条件を返す必要がある場合に、USB デバイス クラスによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-224">This function is called by the USB device class when an endpoint should return a Stall condition to the host.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-225">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-225">Input Parameter</span></span>

- <span data-ttu-id="d3bed-226">**endpoint**: 停止条件が要求されるエンドポイント。</span><span class="sxs-lookup"><span data-stu-id="d3bed-226">**endpoint** The endpoint on which the Stall condition is requested.</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-227">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-227">Return Value</span></span>

- <span data-ttu-id="d3bed-228">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-228">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d3bed-229">**UX_ERROR**: (0xFF) デバイスが無効な状態です。</span><span class="sxs-lookup"><span data-stu-id="d3bed-229">**UX_ERROR** (0xFF) The device is in an invalid state.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-230">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-230">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_endpoint_stall(endpoint);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_host_wakeup"></a><span data-ttu-id="d3bed-231">ux_device_stack_host_wakeup</span><span class="sxs-lookup"><span data-stu-id="d3bed-231">ux_device_stack_host_wakeup</span></span>

<span data-ttu-id="d3bed-232">ホストをウェイク アップします</span><span class="sxs-lookup"><span data-stu-id="d3bed-232">Wake up the host</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-233">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-233">Prototype</span></span>

```c
UINT ux_device_stack_host_wakeup(VOID);
```

### <a name="description"></a><span data-ttu-id="d3bed-234">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-234">Description</span></span>

<span data-ttu-id="d3bed-235">この関数は、デバイスがホストをウェイク アップするときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-235">This function is called when the device wants to wake up the host.</span></span> <span data-ttu-id="d3bed-236">このコマンドは、デバイスが一時停止モードの場合にのみ有効です。</span><span class="sxs-lookup"><span data-stu-id="d3bed-236">This command is only valid when the device is in suspend mode.</span></span> <span data-ttu-id="d3bed-237">USB ホストをウェイク アップするタイミングの決定は、デバイス アプリケーション次第です。</span><span class="sxs-lookup"><span data-stu-id="d3bed-237">It is up to the device application to decide when it wants to wake up the USB host.</span></span> <span data-ttu-id="d3bed-238">たとえば、USB モデムは、電話回線で RING 信号を検出したときにホストをウェイク アップできます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-238">For instance, a USB modem can wake up a host when it detects a RING signal on the telephone line.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-239">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-239">Input Parameter</span></span>

<span data-ttu-id="d3bed-240">なし</span><span class="sxs-lookup"><span data-stu-id="d3bed-240">None</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-241">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-241">Return values</span></span>

- <span data-ttu-id="d3bed-242">**UX_SUCCESS** (0x00) 呼び出しに成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-242">**UX_SUCCESS** (0x00) The call was successful.</span></span>
- <span data-ttu-id="d3bed-243">**UX_FUNCTION_NOT_SUPPORTED**: (0x54) 呼び出しに失敗しました (デバイスが一時停止モードではなかった可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="d3bed-243">**UX_FUNCTION_NOT_SUPPORTED** (0x54) The call failed (the device was probably not in the suspended mode).</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-244">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-244">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_host_wakeup();

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_initialize"></a><span data-ttu-id="d3bed-245">ux_device_stack_initialize</span><span class="sxs-lookup"><span data-stu-id="d3bed-245">ux_device_stack_initialize</span></span>

<span data-ttu-id="d3bed-246">USB デバイス スタックを初期化します</span><span class="sxs-lookup"><span data-stu-id="d3bed-246">Initialize USB device stack</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-247">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-247">Prototype</span></span>

```c
UINT ux_device_stack_initialize(
    UCHAR *device_framework_high_speed,
    ULONG device_framework_length_high_speed,
    UCHAR *device_framework_full_speed,
    ULONG device_framework_length_full_speed,
    UCHAR *string_framework,
    ULONG string_framework_length,
    UCHAR *language_id_framework,
    ULONG language_id_framework_length),
    UINT (*ux_system_slave_change_function)(ULONG)));
```

### <a name="description"></a><span data-ttu-id="d3bed-248">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-248">Description</span></span>

<span data-ttu-id="d3bed-249">この関数は、USB デバイス スタックを初期化するために、アプリケーションによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-249">This function is called by the application to initialize the USB device stack.</span></span> <span data-ttu-id="d3bed-250">クラスやコントローラーは初期化されません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-250">It does not initialize any classes or any controllers.</span></span> <span data-ttu-id="d3bed-251">これは、個別の関数呼び出しを使用して行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-251">This should be done with separate function calls.</span></span> <span data-ttu-id="d3bed-252">この呼び出しでは主に、USB 関数のデバイス フレームワークがスタックに提供されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-252">This call mainly provides the stack with the device framework for the USB function.</span></span> <span data-ttu-id="d3bed-253">高速と全速の両方の速度がサポートされるので、速度ごとにデバイス フレームワークを完全に分けることができます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-253">It supports both high and full speeds with the possibility to have completely separate device framework for each speed.</span></span> <span data-ttu-id="d3bed-254">文字列フレームワークと複数言語がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="d3bed-254">String framework and multiple languages are supported.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-255">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-255">Parameters</span></span>

- <span data-ttu-id="d3bed-256">**device_framework_high_speed**: 高速フレームワークへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-256">**device_framework_high_speed**: Pointer to the high speed framework.</span></span>
- <span data-ttu-id="d3bed-257">**device_framework_length_high_speed**: 高速フレームワークの長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-257">**device_framework_length_high_speed**: Length of the high speed framework.</span></span>
- <span data-ttu-id="d3bed-258">**device_framework_full_speed**: 全速フレームワークへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-258">**device_framework_full_speed**: Pointer to the full speed framework.</span></span>
- <span data-ttu-id="d3bed-259">**device_framework_length_full_speed**: 全速フレームワークの長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-259">**device_framework_length_full_speed**: Length of the full speed framework.</span></span>
- <span data-ttu-id="d3bed-260">**string_framework**: 文字列フレームワークへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-260">**string_framework**: Pointer to string framework.</span></span>
- <span data-ttu-id="d3bed-261">**string_framework_length**: 文字列フレームワークの長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-261">**string_framework_length**: Length of string framework.</span></span>
- <span data-ttu-id="d3bed-262">**language_id_framework**: 文字列言語フレームワークへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-262">**language_id_framework**: Pointer to string language framework.</span></span>
- <span data-ttu-id="d3bed-263">**language_id_framework_length**: 文字列言語フレームワークの長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-263">**language_id_framework_length**: Length of the string language framework.</span></span>
- <span data-ttu-id="d3bed-264">**ux_system_slave_change_function**: デバイスの状態が変化するときに呼び出される関数。</span><span class="sxs-lookup"><span data-stu-id="d3bed-264">**ux_system_slave_change_function**: Function to be called when the device state changes.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-265">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-265">Return Values</span></span>

- <span data-ttu-id="d3bed-266">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-266">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d3bed-267">**UX_MEMORY_INSUFFICIENT**: (0x12) スタックを初期化できる十分なメモリがありません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-267">**UX_MEMORY_INSUFFICIENT** (0x12) Not enough memory to initialize the stack.</span></span>
- <span data-ttu-id="d3bed-268">**UX_DESCRIPTOR_CORRUPTED**: (0x42) 記述子が無効です。</span><span class="sxs-lookup"><span data-stu-id="d3bed-268">**UX_DESCRIPTOR_CORRUPTED** (0x42) The descriptor is invalid.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-269">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-269">Example</span></span>

```c
/* Example of a device framework */

#define DEVICE_FRAMEWORK_LENGTH_FULL_SPEED 50

UCHAR device_framework_full_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x10, 0x01, 0x00, 0x00, 0x00, 0x08,
    0xec, 0x08, 0x10, 0x00, 0x00, 0x00, 0x00, 0x00,
    0x00, 0x01,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x40, 0x00, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x40, 0x00, 0x00
};

#define DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED 60

UCHAR device_framework_high_speed[] = {
    /* Device descriptor */
    0x12, 0x01, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x0a, 0x07, 0x25, 0x40, 0x01, 0x00, 0x01, 0x02,
    0x03, 0x01,

    /* Device qualifier descriptor */
    0x0a, 0x06, 0x00, 0x02, 0x00, 0x00, 0x00, 0x40,
    0x01, 0x00,

    /* Configuration descriptor */
    0x09, 0x02, 0x20, 0x00, 0x01, 0x01, 0x00, 0xc0,
    0x32,

    /* Interface descriptor */
    0x09, 0x04, 0x00, 0x00, 0x02, 0x08, 0x06, 0x50,
    0x00,

    /* Endpoint descriptor (Bulk Out) */
    0x07, 0x05, 0x01, 0x02, 0x00, 0x02, 0x00,

    /* Endpoint descriptor (Bulk In) */
    0x07, 0x05, 0x82, 0x02, 0x00, 0x02, 0x00
};

/* String Device Framework:
    Byte 0 and 1: Word containing the language ID: 0x0904 for US
    Byte 2 : Byte containing the index of the descriptor
    Byte 3 : Byte containing the length of the descriptor string */

#define STRING_FRAMEWORK_LENGTH 38 UCHAR string_framework[] = {
    /* Manufacturer string descriptor: Index 1 */
    0x09, 0x04, 0x01, 0x0c,
    0x45, 0x78, 0x70, 0x72,0x65, 0x73, 0x20, 0x4c,
    0x6f, 0x67, 0x69, 0x63,

    /* Product string descriptor: Index 2 */
    0x09, 0x04, 0x02, 0x0c,
    0x4D, 0x4C, 0x36, 0x39, 0x36, 0x35, 0x30, 0x30,
    0x20, 0x53, 0x44, 0x4B,

    /* Serial Number string descriptor: Index 3 */
    0x09, 0x04, 0x03, 0x04,
    0x30, 0x30, 0x30, 0x31
};

/* Multiple languages are supported on the device, to add a language besides English, 
  the Unicode language code must be appended to the language_id_framework array 
  and the length adjusted accordingly. */

#define LANGUAGE_ID_FRAMEWORK_LENGTH 2

UCHAR language_id_framework[] = {
    /* English. */
    0x09, 0x04
};
```

<span data-ttu-id="d3bed-270">アプリケーションは、コントローラーの状態が変化するときにコールバックを要求できます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-270">The application can request a call back when the controller changes its state.</span></span> <span data-ttu-id="d3bed-271">コントローラーの主な状態は次の 2 つです。</span><span class="sxs-lookup"><span data-stu-id="d3bed-271">The two main states for the controller are:</span></span>

- <span data-ttu-id="d3bed-272">**UX_DEVICE_SUSPENDED**</span><span class="sxs-lookup"><span data-stu-id="d3bed-272">**UX_DEVICE_SUSPENDED**</span></span>
- <span data-ttu-id="d3bed-273">**UX_DEVICE_RESUMED**</span><span class="sxs-lookup"><span data-stu-id="d3bed-273">**UX_DEVICE_RESUMED**</span></span>

<span data-ttu-id="d3bed-274">アプリケーションが一時停止/再開信号を必要としない場合は、UX_NULL 関数を送信します。</span><span class="sxs-lookup"><span data-stu-id="d3bed-274">If the application does not need Suspend/Resume signals, it would supply a UX_NULL function.</span></span>

```c
UINT status;

/* The code below is required for installing the device portion of USBX. 
    There is no call back for device status change in this example. */
status = ux_device_stack_initialize(&device_framework_high_speed,
    DEVICE_FRAMEWORK_LENGTH_HIGH_SPEED, &device_framework_full_speed,
    DEVICE_FRAMEWORK_LENGTH_FULL_SPEED, &string_framework,
    STRING_FRAMEWORK_LENGTH, &language_id_framework,
    LANGUAGE_ID_FRAMEWORK_LENGTH, UX_NULL);

/* If status equals UX_SUCCESS, initialization was successful. */
```

### <a name="ux_device_stack_interface_delete"></a><span data-ttu-id="d3bed-275">ux_device_stack_interface_delete</span><span class="sxs-lookup"><span data-stu-id="d3bed-275">ux_device_stack_interface_delete</span></span>

<span data-ttu-id="d3bed-276">ネットワーク インターフェイスを削除する</span><span class="sxs-lookup"><span data-stu-id="d3bed-276">Delete a stack interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-277">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-277">Prototype</span></span>

```c
UINT ux_device_stack_interface_delete(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="d3bed-278">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-278">Description</span></span>

<span data-ttu-id="d3bed-279">この関数は、インターフェイスの削除が必要なときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-279">This function is called when an interface should be removed.</span></span> <span data-ttu-id="d3bed-280">インターフェイスが削除されるのは、デバイスが抽出されるとき、バスがリセットされた後、または新しい代替設定があるときです。</span><span class="sxs-lookup"><span data-stu-id="d3bed-280">An interface is either removed when a device is extracted, or following a bus reset, or when there is a new alternate setting.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-281">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-281">Input Parameter</span></span>

- <span data-ttu-id="d3bed-282">**interface**: 削除するインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-282">**interface**: Pointer to the interface to remove.</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-283">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-283">Return Value</span></span>

- <span data-ttu-id="d3bed-284">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-284">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-285">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-285">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_delete(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_get"></a><span data-ttu-id="d3bed-286">ux_device_stack_interface_get</span><span class="sxs-lookup"><span data-stu-id="d3bed-286">ux_device_stack_interface_get</span></span>

<span data-ttu-id="d3bed-287">現在のインターフェイス値を取得します</span><span class="sxs-lookup"><span data-stu-id="d3bed-287">Get the current interface value</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-288">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-288">Prototype</span></span>

```c
UINT ux_device_stack_interface_get(UINT interface_value);
```

### <a name="description"></a><span data-ttu-id="d3bed-289">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-289">Description</span></span>

<span data-ttu-id="d3bed-290">この関数は、ホストが現在のインターフェイスに対してクエリを行うときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-290">This function is called when the host queries the current interface.</span></span> <span data-ttu-id="d3bed-291">デバイスは現在のインターフェイス値を返します。</span><span class="sxs-lookup"><span data-stu-id="d3bed-291">The device returns the current interface value.</span></span>

> [!NOTE]
> <span data-ttu-id="d3bed-292">この関数の使用は非推奨とされます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-292">This function is deprecated.</span></span> <span data-ttu-id="d3bed-293">レガシ ソフトウェアには使用できますが、新しいソフトウェアでは、代わりに ***ux_device_stack_alternate_setting_get*** 関数を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-293">It is available for legacy software, but new software should use the ***ux_device_stack_alternate_setting_get*** function instead.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-294">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-294">Input Parameter</span></span>

- <span data-ttu-id="d3bed-295">**interface_value**: 返されるインターフェイスの値。</span><span class="sxs-lookup"><span data-stu-id="d3bed-295">**interface_value** Interface value to return.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-296">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-296">Return Values</span></span>

- <span data-ttu-id="d3bed-297">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-297">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d3bed-298">**UX_ERROR**: (0xFF) インターフェイスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-298">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-299">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-299">Example</span></span>

```c
ULONG interface_value;

UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_get(interface_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_set"></a><span data-ttu-id="d3bed-300">ux_device_stack_interface_set</span><span class="sxs-lookup"><span data-stu-id="d3bed-300">ux_device_stack_interface_set</span></span>

<span data-ttu-id="d3bed-301">インターフェイスの代替設定を変更します</span><span class="sxs-lookup"><span data-stu-id="d3bed-301">Change the alternate setting of the interface</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-302">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-302">Prototype</span></span>

```c
UINT ux_device_stack_interface_set(
    UCHAR *device_framework,
    ULONG device_framework_length, 
    ULONG alternate_setting_value);
```

### <a name="description"></a><span data-ttu-id="d3bed-303">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-303">Description</span></span>

<span data-ttu-id="d3bed-304">この関数は、ホストがインターフェイスの代替設定の変更を要求するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-304">This function is called when the host requests a change of the alternate setting for the interface.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-305">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-305">Parameters</span></span>

- <span data-ttu-id="d3bed-306">**device_framework**: このインターフェイスのデバイス フレームワークのアドレス。</span><span class="sxs-lookup"><span data-stu-id="d3bed-306">**device_framework**: Address of the device framework for this interface.</span></span>
- <span data-ttu-id="d3bed-307">**device_framework_length**: デバイス フレームワークの長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-307">**device_framework_length**: Length of the device framework.</span></span>
- <span data-ttu-id="d3bed-308">**alternate_setting_value**: このインターフェイスによって使用される代替設定値。</span><span class="sxs-lookup"><span data-stu-id="d3bed-308">**alternate_setting_value**: Alternate setting value to be used by this interface.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-309">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-309">Return Values</span></span>

- <span data-ttu-id="d3bed-310">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-310">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d3bed-311">**UX_ERROR**: (0xFF) インターフェイスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-311">**UX_ERROR** (0xFF) No interface exists.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-312">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-312">Example</span></span>

```c
UCHAR * device_framework
ULONG device_framework_length;
ULONG alternate_setting_value;
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_set(device_framework,
    device_framework_length, alternate_setting_value);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_interface_start"></a><span data-ttu-id="d3bed-313">ux_device_stack_interface_start</span><span class="sxs-lookup"><span data-stu-id="d3bed-313">ux_device_stack_interface_start</span></span>

<span data-ttu-id="d3bed-314">インターフェイス インスタンスを所有するクラスの検索を開始します</span><span class="sxs-lookup"><span data-stu-id="d3bed-314">Start search for a class to own an interface instance</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-315">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-315">Prototype</span></span>

```c
UINT ux_device_stack_interface_start(UX_SLAVE_INTERFACE*interface);
```

### <a name="description"></a><span data-ttu-id="d3bed-316">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-316">Description</span></span>

<span data-ttu-id="d3bed-317">この関数は、ホストによってインターフェイスが選択され、デバイス スタックがこのインターフェイス インスタンスを所有するデバイス クラスを検索する必要があるときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-317">This function is called when an interface has been selected by the host and the device stack needs to search for a device class to own this interface instance.</span></span>

### <a name="input-parameter"></a><span data-ttu-id="d3bed-318">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-318">Input Parameter</span></span>

- <span data-ttu-id="d3bed-319">**interface**: 作成されたインターフェイスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-319">**interface**: Pointer to the interface created.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-320">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-320">Return Values</span></span>

- <span data-ttu-id="d3bed-321">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-321">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d3bed-322">**UX_NO_CLASS_MATCH**: (0x57) このインターフェイスにはクラスが存在しません。</span><span class="sxs-lookup"><span data-stu-id="d3bed-322">**UX_NO_CLASS_MATCH** (0x57) No class exists for this interface.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-323">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-323">Example</span></span>

```c
UINT status;

/* The following example illustrates this service. */
status = ux_device_stack_interface_start(interface);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_transfer_request"></a><span data-ttu-id="d3bed-324">ux_device_stack_transfer_request</span><span class="sxs-lookup"><span data-stu-id="d3bed-324">ux_device_stack_transfer_request</span></span>

<span data-ttu-id="d3bed-325">ホストにデータ転送を要求します</span><span class="sxs-lookup"><span data-stu-id="d3bed-325">Request to transfer data to the host</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-326">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-326">Prototype</span></span>

```c
UINT ux_device_stack_transfer_request(
    UX_SLAVE_TRANSFER *transfer_request,
    ULONG slave_length, 
    ULONG host_length);
```

### <a name="description"></a><span data-ttu-id="d3bed-327">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-327">Description</span></span>

<span data-ttu-id="d3bed-328">この関数は、クラスまたはスタックがデータをホストに転送するときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-328">This function is called when a class or the stack wants to transfer data to the host.</span></span> <span data-ttu-id="d3bed-329">ホストは常にデバイスをポーリングしますが、デバイスでは事前にデータを準備することができます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-329">The host always polls the device but the device can prepare data in advance.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-330">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-330">Parameters</span></span>

- <span data-ttu-id="d3bed-331">**transfer_request**: 転送要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-331">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="d3bed-332">**slave_length**: デバイスが返す必要がある長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-332">**slave_length**: Length the device wants to return.</span></span>
- <span data-ttu-id="d3bed-333">**host_length**: ホストが要求した長さ。</span><span class="sxs-lookup"><span data-stu-id="d3bed-333">**host_length**: Length the host has requested.</span></span>

### <a name="return-values"></a><span data-ttu-id="d3bed-334">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-334">Return Values</span></span>

- <span data-ttu-id="d3bed-335">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-335">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
- <span data-ttu-id="d3bed-336">**UX_TRANSFER_NOT_READY**: (0x25) デバイスが無効な状態です (**ATTACHED**、**CONFIGURED**、**ADDRESSED** のいずれかである必要があります)。</span><span class="sxs-lookup"><span data-stu-id="d3bed-336">**UX_TRANSFER_NOT_READY** (0x25) The device is in an invalid state; it must be **ATTACHED**, **CONFIGURED**, or **ADDRESSED**.</span></span>
- <span data-ttu-id="d3bed-337">**UX_ERROR**: (0xFF) 転送エラー。</span><span class="sxs-lookup"><span data-stu-id="d3bed-337">**UX_ERROR** (0xFF) Transport error.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-338">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-338">Example</span></span>

```c
UINT status;

/* The following example illustrates how to transfer more data than an application requests. */
while(total_length) {
    /* How much can we send in this transfer? */
    if (total_length > UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE)
        transfer_length = UX_SLAVE_CLASS_STORAGE_BUFFER_SIZE;
    else
        transfer_length = total_length;

   /* Copy the Storage Buffer into the transfer request memory. */
   ux_utility_memory_copy(transfer_request ->  ux_slave_transfer_request_data_pointer,
       media_memory, transfer_length);

   /* Send the data payload back to the caller. */
   status = ux_device_transfer_request(transfer_request,
       transfer_length, transfer_length);

   /* If status equals UX_SUCCESS, the operation was successful. */

   /* Update the buffer address.  */
    media_memory += transfer_length;

   /* Update the length to remain. */
    total_length -= transfer_length;
}
```

### <a name="ux_device_stack_transfer_abort"></a><span data-ttu-id="d3bed-339">ux_device_stack_transfer_abort</span><span class="sxs-lookup"><span data-stu-id="d3bed-339">ux_device_stack_transfer_abort</span></span>

<span data-ttu-id="d3bed-340">譲渡要求のキャンセル</span><span class="sxs-lookup"><span data-stu-id="d3bed-340">Cancel a transfer request</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-341">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-341">Prototype</span></span>

```c
UINT ux_device_stack_transfer_abort(
    UX_SLAVE_TRANSFER *transfer_request, 
    ULONG completion_code);
```

### <a name="description"></a><span data-ttu-id="d3bed-342">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-342">Description</span></span>

<span data-ttu-id="d3bed-343">この関数は、アプリケーションが転送要求をキャンセルする必要がある場合、またはスタックがエンドポイントに関連する転送要求を中止する必要がある場合に呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-343">This function is called when an application needs to cancel a transfer request or when the stack needs to abort a transfer request associated with an endpoint.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-344">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-344">Parameters</span></span>

- <span data-ttu-id="d3bed-345">**transfer_request**: 転送要求へのポインター。</span><span class="sxs-lookup"><span data-stu-id="d3bed-345">**transfer_request**: Pointer to the transfer request.</span></span>
- <span data-ttu-id="d3bed-346">**completion_code**: この転送要求の完了を待機しているクラスに返されるエラー コード。</span><span class="sxs-lookup"><span data-stu-id="d3bed-346">**completion_code**: Error code to be returned to the class waiting for this transfer request to complete.</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-347">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-347">Return Value</span></span>

- <span data-ttu-id="d3bed-348">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-348">**UX_SUCCESS** (0x00) This operation was successful.</span></span>

### <a name="example"></a><span data-ttu-id="d3bed-349">例</span><span class="sxs-lookup"><span data-stu-id="d3bed-349">Example</span></span>

```c
UINT status;

/* The following example illustrates how to abort a transfer when a
    bus reset has been detected on the bus. */
status = ux_device_stack_transfer_abort(transfer_request, UX_TRANSFER_BUS_RESET);

/* If status equals UX_SUCCESS, the operation was successful. */
```

### <a name="ux_device_stack_uninitialize"></a><span data-ttu-id="d3bed-350">ux_device_stack_uninitialize</span><span class="sxs-lookup"><span data-stu-id="d3bed-350">ux_device_stack_uninitialize</span></span>

<span data-ttu-id="d3bed-351">スタックを初期化解除します</span><span class="sxs-lookup"><span data-stu-id="d3bed-351">Unitialize stack</span></span>

### <a name="prototype"></a><span data-ttu-id="d3bed-352">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="d3bed-352">Prototype</span></span>

```c
UINT ux_device_stack_uninitialize();
```

### <a name="description"></a><span data-ttu-id="d3bed-353">説明</span><span class="sxs-lookup"><span data-stu-id="d3bed-353">Description</span></span>

<span data-ttu-id="d3bed-354">この関数は、アプリケーションが USBX デバイス スタックを初期化解除する必要がある場合に呼び出されます。すべてのデバイス スタック リソースが解放されます。</span><span class="sxs-lookup"><span data-stu-id="d3bed-354">This function is called when an application needs to unitialize the USBX device stack – all device stack resources are freed.</span></span> <span data-ttu-id="d3bed-355">これは、ux_device_stack_class_unregister を使用してすべてのクラスを登録解除した後で呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="d3bed-355">This should be called after all classes have been unregistered via ux_device_stack_class_unregister.</span></span>

### <a name="parameters"></a><span data-ttu-id="d3bed-356">パラメーター</span><span class="sxs-lookup"><span data-stu-id="d3bed-356">Parameters</span></span>

<span data-ttu-id="d3bed-357">なし</span><span class="sxs-lookup"><span data-stu-id="d3bed-357">None</span></span>

### <a name="return-value"></a><span data-ttu-id="d3bed-358">戻り値</span><span class="sxs-lookup"><span data-stu-id="d3bed-358">Return Value</span></span>

<span data-ttu-id="d3bed-359">**UX_SUCCESS**: (0x00) この操作は成功しました。</span><span class="sxs-lookup"><span data-stu-id="d3bed-359">**UX_SUCCESS** (0x00) This operation was successful.</span></span>
