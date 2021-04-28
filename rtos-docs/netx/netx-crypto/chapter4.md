---
title: 第 4 章 - Azure RTOS NetX Crypto API の説明
description: Azure RTOS NetX Crypto API の説明
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 04e732bc1fd6012636aab3a57391829f529724cf
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811627"
---
# <a name="chapter-4---azure-rtos-netx-crypto-api-description"></a><span data-ttu-id="5005a-103">第 4 章 - Azure RTOS NetX Crypto API の説明</span><span class="sxs-lookup"><span data-stu-id="5005a-103">Chapter 4 - Azure RTOS NetX Crypto API description</span></span>

## <a name="nx_crypto_initialize"></a><span data-ttu-id="5005a-104">nx_crypto_initialize</span><span class="sxs-lookup"><span data-stu-id="5005a-104">nx_crypto_initialize</span></span>

<span data-ttu-id="5005a-105">NetX Secure ライブラリを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-105">Initializes the NetX Secure Library</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-106">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-106">Prototype</span></span>

```c
UINT nx_crypto_initialize(VOID);
```

### <a name="description"></a><span data-ttu-id="5005a-107">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-107">Description</span></span>

<span data-ttu-id="5005a-108">この関数では、Azure RTOS NetX Crypto ライブラリ モジュールを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-108">This function initializes the Azure RTOS NetX Crypto library module.</span></span> <span data-ttu-id="5005a-109">アプリケーションは、他のいずれかの暗号化関数を使用する前に、この関数を呼び出して初期化を実行し、ライブラリの整合性を検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-109">Before using any of the other cryptographic functions, the application must call this function to perform initialization and to validate the integrity of the library.</span></span> <span data-ttu-id="5005a-110">他の NetX Crypto サービスを使用する前にこの関数を呼び出さないと、エラーが返されることになります。</span><span class="sxs-lookup"><span data-stu-id="5005a-110">Failure to call this function before using other NetX Crypto services will result in errors being returned.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-111">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-111">Parameters</span></span>

- <span data-ttu-id="5005a-112">**なし**</span><span class="sxs-lookup"><span data-stu-id="5005a-112">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-113">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-113">Return Values</span></span>

- <span data-ttu-id="5005a-114">**NX_CRYPTO_SUCCESS** (0x00) NetX Crypto ライブラリが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-114">**NX_CRYPTO_SUCCESS** (0x00) Successful initialized NetX Crypto library.</span></span> <span data-ttu-id="5005a-115">これでライブラリ関数の準備が整い、使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-115">The library functions are now ready, and can be used.</span></span>
- <span data-ttu-id="5005a-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリを初期化できなかったか、整合性チェックに失敗しました。</span><span class="sxs-lookup"><span data-stu-id="5005a-116">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library fails to initialize, or fails the integrity check.</span></span> <span data-ttu-id="5005a-117">アプリケーションでこのライブラリを使用することはできません。</span><span class="sxs-lookup"><span data-stu-id="5005a-117">Application cannot use this library.</span></span>

### <a name="example"></a><span data-ttu-id="5005a-118">例</span><span class="sxs-lookup"><span data-stu-id="5005a-118">Example</span></span>

<span data-ttu-id="5005a-119">TODO</span><span class="sxs-lookup"><span data-stu-id="5005a-119">TODO</span></span>

## <a name="nx_crypto_module_state_get"></a><span data-ttu-id="5005a-120">nx_crypto_module_state_get</span><span class="sxs-lookup"><span data-stu-id="5005a-120">nx_crypto_module_state_get</span></span>

<span data-ttu-id="5005a-121">FIPS 対応モジュールの現在の状態を取得します。</span><span class="sxs-lookup"><span data-stu-id="5005a-121">Retrieve the current status of the FIPS-enabled module</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-122">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-122">Prototype</span></span>

```c
UINT nx_crypto_module_state_get(VOID);
```

### <a name="description"></a><span data-ttu-id="5005a-123">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-123">Description</span></span>

<span data-ttu-id="5005a-124">このサービスは、FIPS ビルド ライブラリでのみ使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-124">This service is only available in the FIPS build library.</span></span> <span data-ttu-id="5005a-125">NetX Crypto ライブラリの現在の状態を返します。</span><span class="sxs-lookup"><span data-stu-id="5005a-125">It returns the state of the current state of the NetX Crypto library.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-126">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-126">Parameters</span></span>

- <span data-ttu-id="5005a-127">**なし**</span><span class="sxs-lookup"><span data-stu-id="5005a-127">**None**</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-128">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-128">Return Values</span></span>

- <span data-ttu-id="5005a-129">**状態フラグ:**</span><span class="sxs-lookup"><span data-stu-id="5005a-129">**Status Flag:**</span></span>
  - <span data-ttu-id="5005a-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span><span class="sxs-lookup"><span data-stu-id="5005a-130">NX_CRYPTO_LIBRARY_STATE_UNINITIALIZED 0x00000001</span></span>
  - <span data-ttu-id="5005a-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span><span class="sxs-lookup"><span data-stu-id="5005a-131">NX_CRYPTO_LIBRARY_STATE_POST_IN_PROGRESS 0x00000002</span></span>
  - <span data-ttu-id="5005a-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span><span class="sxs-lookup"><span data-stu-id="5005a-132">NX_CRYPTO_LIBRARY_STATE_INTEGRITY_TEST_FAILED 0x00000004</span></span>
  - <span data-ttu-id="5005a-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span><span class="sxs-lookup"><span data-stu-id="5005a-133">NX_CRYPTO_LIBRARY_STATE_FUNCTIONAL_TEST_FAILED 0x00000008</span></span>
  - <span data-ttu-id="5005a-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span><span class="sxs-lookup"><span data-stu-id="5005a-134">NX_CRYPTO_LIBRARY_STATE_OPERATIONAL 0x80000000</span></span>
- <span data-ttu-id="5005a-135">**その他のすべての値は無効です。**</span><span class="sxs-lookup"><span data-stu-id="5005a-135">**All other values are invalid.**</span></span>

### <a name="example"></a><span data-ttu-id="5005a-136">例</span><span class="sxs-lookup"><span data-stu-id="5005a-136">Example</span></span>

<span data-ttu-id="5005a-137">TODO</span><span class="sxs-lookup"><span data-stu-id="5005a-137">TODO</span></span>

## <a name="_nx_crypto_method_aes_init"></a><span data-ttu-id="5005a-138">_nx_crypto_method_aes_init</span><span class="sxs-lookup"><span data-stu-id="5005a-138">_nx_crypto_method_aes_init</span></span>

<span data-ttu-id="5005a-139">AES 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-139">Initializes the AES crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-140">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-140">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-141">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-141">Description</span></span>

<span data-ttu-id="5005a-142">この関数では、指定されたキー文字列を使用して、AES 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-142">This function initializes the AES control block with the given key string.</span></span> <span data-ttu-id="5005a-143">いったん AES 制御ブロックが初期化されると、後続の AES 操作では、同じキーとキー サイズが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-143">Once the AES control block is initialized, subsequent AES operation will be using the same key and key size.</span></span>

<span data-ttu-id="5005a-144">アプリケーションは複数の AES 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-144">Application may create multiple AES control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-145">キーは制御ブロックに割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5005a-145">A key is assigned to a control block.</span></span> <span data-ttu-id="5005a-146">後続の暗号化や暗号化解除の操作では、同じ AES 制御ブロックを参照することができ、AES 制御ブロックを再初期化する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-146">Subsequent encryption or decryption operation can reference to the same AES control block without the need to re-initialize the AES control block.</span></span> <span data-ttu-id="5005a-147">セッションのキーが変更された場合、アプリケーションでは、更新されたキーを使用して AES 制御ブロックを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-147">If the key for the session is changed, application needs to re-initialize AES control block with the updated key.</span></span>

<span data-ttu-id="5005a-148">_ *Nx_crypto_method_aes_init()* を呼び出すと、以前に構成されたキーとキー サイズが、新しいキーに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-148">Calling _ *nx_crypto_method_aes_init()* automatically updates a previously configured key and key size to the new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-149">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-149">Parameters</span></span>

- <span data-ttu-id="5005a-150">**method** 有効な AES 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-150">**method** Pointer to a valid AES crypto method control block.</span></span> <span data-ttu-id="5005a-151">以下の定義済み AES 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-151">The following pre-defined AES crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-152">*crypto_method_aes_cbc_128*</span><span class="sxs-lookup"><span data-stu-id="5005a-152">*crypto_method_aes_cbc_128*</span></span>
  - <span data-ttu-id="5005a-153">*crypto_method_aes_cbc_192*</span><span class="sxs-lookup"><span data-stu-id="5005a-153">*crypto_method_aes_cbc_192*</span></span>
  - <span data-ttu-id="5005a-154">*crypto_method_aes_cbc_256*</span><span class="sxs-lookup"><span data-stu-id="5005a-154">*crypto_method_aes_cbc_256*</span></span>
  - <span data-ttu-id="5005a-155">*crypto_method_aes_ctr_128*</span><span class="sxs-lookup"><span data-stu-id="5005a-155">*crypto_method_aes_ctr_128*</span></span>
  - <span data-ttu-id="5005a-156">*crypto_method_aes_ctr_192*</span><span class="sxs-lookup"><span data-stu-id="5005a-156">*crypto_method_aes_ctr_192*</span></span>
  - <span data-ttu-id="5005a-157">*crypto_method_aes_ctr_256*</span><span class="sxs-lookup"><span data-stu-id="5005a-157">*crypto_method_aes_ctr_256*</span></span>
  - <span data-ttu-id="5005a-158">*crypto_method_aes_xcbc_128*</span><span class="sxs-lookup"><span data-stu-id="5005a-158">*crypto_method_aes_xcbc_128*</span></span>
  - <span data-ttu-id="5005a-159">*crypto_method_aes_ccm_8_128*</span><span class="sxs-lookup"><span data-stu-id="5005a-159">*crypto_method_aes_ccm_8_128*</span></span>
- <span data-ttu-id="5005a-160">**key** AES キーを格納しているバッファーを指し示します</span><span class="sxs-lookup"><span data-stu-id="5005a-160">**key** Points to a buffer containing the AES key</span></span>
- <span data-ttu-id="5005a-161">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-161">**key_size_in_bits** Size of the key, in bits.</span></span> <span data-ttu-id="5005a-162">次の値を指定できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-162">Valid values are:</span></span>
  - <span data-ttu-id="5005a-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span><span class="sxs-lookup"><span data-stu-id="5005a-163">*NX_CRYPTO_AES_KEY_SIZE_128_BITS*</span></span>
  - <span data-ttu-id="5005a-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span><span class="sxs-lookup"><span data-stu-id="5005a-164">*NX_CRYPTO_AES_KEY_SIZE_192_BITS*</span></span>
  - <span data-ttu-id="5005a-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span><span class="sxs-lookup"><span data-stu-id="5005a-165">*NX_CRYPTO_AES_KEY_SIZE_256_BITS*</span></span>
  - <span data-ttu-id="5005a-166">**その他のすべての値は無効です。**</span><span class="sxs-lookup"><span data-stu-id="5005a-166">**All other values are invalid.**</span></span>
- <span data-ttu-id="5005a-167">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-167">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-168">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-168">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-169">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-169">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-170">**crypto_metadata** AES 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-170">**crypto_metadata** Pointer to a valid memory space for the AES control block.</span></span> <span data-ttu-id="5005a-171">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-171">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-172">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-172">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-173">AES の場合、メタデータ サイズは *sizeof(NX_AES)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-173">For AES, the metadata size must be *sizeof(NX_AES)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-174">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-174">Return Values</span></span>

- <span data-ttu-id="5005a-175">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、AES 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-175">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the AES control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-176">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-177">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-177">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) キー サイズが、AES では有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-178">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for AES.</span></span>

## <a name="_nx_crypto_method_aes_operation"></a><span data-ttu-id="5005a-179">_nx_crypto_method_aes_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-179">_nx_crypto_method_aes_operation</span></span>

<span data-ttu-id="5005a-180">AES 操作 (暗号化または暗号化解除) を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-180">Perform an AES operation (encryption or decryption).</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-181">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-181">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="5005a-182">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-182">Description</span></span>

<span data-ttu-id="5005a-183">この関数では、AES の暗号化または暗号化解除の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-183">This function performs AES encryption or decryption operation.</span></span> <span data-ttu-id="5005a-184">AES 制御ブロックは、_ *nx_crypto_method_aes_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-184">The AES control block must have been initialized with _ *nx_crypto_method_aes_init()*.</span></span> <span data-ttu-id="5005a-185">実行される AES アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-185">The AES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-186">入力バッファーのサイズは、16 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-186">The input buffer size must be a multiple of 16 bytes.</span></span> <span data-ttu-id="5005a-187">暗号化が解除されたデータのサイズは、入力データ サイズと同じサイズです。</span><span class="sxs-lookup"><span data-stu-id="5005a-187">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="5005a-188">AES ブロック サイズの偶数倍にするために、暗号化されたデータがパディングされた場合、そのパディングは出力バッファーに含められます。また、そのパディングはアプリケーションによって処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-188">If the encrypted data was padded to achieve an even multiple of the AES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="5005a-189">この操作では、状態情報は保持されず、AES 制御ブロック内のキー マテリアルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-189">This operation does not keep state information, and does not alter the key material in the AES control block.</span></span>

<span data-ttu-id="5005a-190">op が NX_CRYPTO_SET_ADDITIONAL_DATA で、アルゴリズムが AES-CCM8 の場合、入力は追加データを指し示し、input_length_in_byte は追加データの長さになります。</span><span class="sxs-lookup"><span data-stu-id="5005a-190">When the op is NX_CRYPTO_SET_ADDITIONAL_DATA and algoritm is AES-CCM8, the input points to additional data and input_length_in_byte is the length of additional data.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-191">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-191">Parameters</span></span>

- <span data-ttu-id="5005a-192">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-192">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-193">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-193">Valid opertions are:</span></span>
  - <span data-ttu-id="5005a-194">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="5005a-194">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="5005a-195">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="5005a-195">*NX_CRYPTO_DECRYPT*</span></span>
  - <span data-ttu-id="5005a-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC のみ)*</span><span class="sxs-lookup"><span data-stu-id="5005a-196">*NX_CRYPTO_AUTHENTICATE (AES-XCBC only)*</span></span>
  - <span data-ttu-id="5005a-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 のみ)*</span><span class="sxs-lookup"><span data-stu-id="5005a-197">*NX_CRYPTO_SET_ADDITIONAL_DATA (AES-CCM8 only)*</span></span>
- <span data-ttu-id="5005a-198">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-198">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-199">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-199">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-200">**method** 有効な AES 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-200">**method** Pointer to the valid AES crypto method.</span></span> <span data-ttu-id="5005a-201">ここで使用される暗号化メソッドは、*nx_crypto_method_aes_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-201">The crypto method used here must be the same used in the *nx_crypto_method_aes_init().*</span></span>
- <span data-ttu-id="5005a-202">**input_data** 暗号化されたテキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-202">**input_data** Points to a buffer containing encrypted text data.</span></span> <span data-ttu-id="5005a-203">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-203">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-204">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-204">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="5005a-205">入力データのサイズは、16 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-205">The input data size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="5005a-206">**iv_ptr** 初期ベクトルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-206">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="5005a-207">IV バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-207">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="5005a-208">**iv_size** 初期ベクトル ブロックのサイズ (バイト単位)。このフィールドは 16 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-208">**iv_size** Size of the Initial Vector block, in bytes This field must be 16.</span></span>
- <span data-ttu-id="5005a-209">**output_buffer** クリア テキスト データを格納する AES 用メモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-209">**output_buffer** Pointer to the memory area for AES to store the clear text data.</span></span> <span data-ttu-id="5005a-210">アプリケーションで出力バッファーに領域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-210">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="5005a-211">出力バッファーは、入力バッファーと重複することがあります。</span><span class="sxs-lookup"><span data-stu-id="5005a-211">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="5005a-212">出力バッファーと入力バッファーが同じ開始アドレスを共有している場合は、これらが重複することがあります。</span><span class="sxs-lookup"><span data-stu-id="5005a-212">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="5005a-213">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-213">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="5005a-214">出力バッファー サイズは、少なくとも入力バッファー サイズと同じである必要があり、出力バッファー サイズは 16 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-214">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 16 bytes.</span></span>
- <span data-ttu-id="5005a-215">**crypto_metadata** *_nx_crypto_method_aes_init()\*\** で使用される AES 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-215">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>
- <span data-ttu-id="5005a-216">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-216">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-217">AES の場合、メタデータ サイズは *sizeof(NX_AES)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-217">For AES, the metadata size must *sizeof(NX_AES)*</span></span>
- <span data-ttu-id="5005a-218">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-218">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-219">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-219">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-220">**nx_crypto_hw_process_callback** - このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-220">**nx_crypto_hw_process_callback** - This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-221">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-221">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-222">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-222">Return Values</span></span>

- <span data-ttu-id="5005a-223">**NX_CRYPTO_SUCCESS** (0x00) AES 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-223">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the AES operation.</span></span>
- <span data-ttu-id="5005a-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-224">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-225">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-225">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な AES アルゴリズムが指定されています\*\*。</span><span class="sxs-lookup"><span data-stu-id="5005a-226">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid AES algorithm being specified\*\*.</span></span>

## <a name="_nx_crypto_method_aes_cleanup"></a><span data-ttu-id="5005a-227">_nx_crypto_method_aes_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-227">_nx_crypto_method_aes_cleanup</span></span>

<span data-ttu-id="5005a-228">AES 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-228">Clean up the AES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-229">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-229">Prototype</span></span>

```c
UINT _nx_crypto_method_aes_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-230">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-230">Description</span></span>

<span data-ttu-id="5005a-231">アプリケーションでは、この AES セッションが不要になったと判断した後にこの関数を呼び出して、AES 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-231">Application calls this function to clean up the AES control block after it determines this AES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-232">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-232">Parameters</span></span>

- <span data-ttu-id="5005a-233">**crypto_metadata** *_nx_crypto_method_aes_init()\*\** で使用される AES 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-233">**crypto_metadata** Pointer to the AES control block used in *_nx_crypto_method_aes_init()\*.\**</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-234">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-234">Return Values</span></span>

- <span data-ttu-id="5005a-235">**NX_CRYPTO_SUCCESS** (0x00) AES セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-235">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the AES session.</span></span>
- <span data-ttu-id="5005a-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-236">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_3des_init"></a><span data-ttu-id="5005a-237">_nx_crypto_method_3des_init</span><span class="sxs-lookup"><span data-stu-id="5005a-237">_nx_crypto_method_3des_init</span></span>

<span data-ttu-id="5005a-238">3DES 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-238">Initialize the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-239">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-239">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-240">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-240">Description</span></span>

<span data-ttu-id="5005a-241">この関数では、指定された 3 つのキー文字列を使用して、Triple DES (3DES) 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-241">This function initializes the Triple DES (3DES) control block with the given three key strings.</span></span> <span data-ttu-id="5005a-242">キー文字列は、それぞれ 8 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-242">The key strings must be 8 bytes each.</span></span> <span data-ttu-id="5005a-243">3 つの DES キーは、24 バイトのバッファーの連続するメモリに連結する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-243">The three DES keys must be concatenated into contiguous memory of 24-byte buffer.</span></span> <span data-ttu-id="5005a-244">FIPS に準拠しているビルドの場合、3 つのキーがそれぞれ異なっている必要があります。そうでないと、関数から NX_CRYPTO_INVALID_KEY エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-244">For FIPS-compliant build, the three keys must be different from each or the function will return the NX_CRYPTO_INVALID_KEY error.</span></span> <span data-ttu-id="5005a-245">いったん 3DES 制御ブロックが初期化されると、後続の 3DES 操作では同じキーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-245">Once the 3DES control block is initialized, subsequent 3DES operations will use the same keys.</span></span>

<span data-ttu-id="5005a-246">アプリケーションは複数の 3DES 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-246">An application may create multiple 3DES control blocks, each representing a session.</span></span> <span data-ttu-id="5005a-247">キーは制御ブロックに割り当てられ、後続の暗号化または暗号化解除の操作では、再初期化不要で同じ制御ブロックを参照できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-247">A key is assigned to a control block and subsequent encryption or decryption operations can reference the same control block without needing to re-initialize.</span></span> <span data-ttu-id="5005a-248">セッションのキーが変更された場合、アプリケーションでは、更新されたキーを使用して制御ブロックを再初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-248">If the key for a session is changed, the application will need to re-initialize the control block with the updated key.</span></span>

<span data-ttu-id="5005a-249">_ *nx_crypto_method_3des_init()* を呼び出すと、以前に構成されたキーが、新しいキーに自動的に更新されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-249">Calling _ *nx_crypto_method_3des_init()* automatically updates a previously configured key to the new keys.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-250">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-250">Parameters</span></span>

- <span data-ttu-id="5005a-251">**method** 有効な 3DES 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-251">**method** Pointer to a valid 3DES crypto method control block.</span></span> <span data-ttu-id="5005a-252">次の定義済み 3DES 暗号化メソッドを使用できます: ***crypto_method_3des***</span><span class="sxs-lookup"><span data-stu-id="5005a-252">The following pre-defined 3DES crypto method is available: ***crypto_method_3des***</span></span>
- <span data-ttu-id="5005a-253">**key** 3 つの DES キーを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-253">**key** Points to a buffer containing the three (3) DES key</span></span>
- <span data-ttu-id="5005a-254">**key_size_in_bits** 192 である必要があります (それぞれが 64 ビットのキーが 3 つ)。</span><span class="sxs-lookup"><span data-stu-id="5005a-254">**key_size_in_bits** Must be 192 (3 keys, each 64 bits).</span></span>
- <span data-ttu-id="5005a-255">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-255">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-256">このハンドルで、初期化中の 3DES 制御ブロックが識別されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-256">The handle identifies the 3DES control block being initialized.</span></span> <span data-ttu-id="5005a-257">後続の 3DES 操作 (暗号化、暗号化の解除、クリーンアップ) では、このハンドルを使用して 3DES 制御ブロックにアクセスします。</span><span class="sxs-lookup"><span data-stu-id="5005a-257">Subsequent 3DES operations (encryption, decryption, and cleanup) use this handle to access the 3DES control block</span></span>
- <span data-ttu-id="5005a-258">**crypto_metadata** 3DES 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-258">**crypto_metadata** Pointer to a valid memory space for the 3DES control block.</span></span> <span data-ttu-id="5005a-259">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-259">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-260">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-260">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-261">3DES の場合、メタデータ サイズは *sizeof(NX_3DES)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-261">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>

### <a name="return-value"></a><span data-ttu-id="5005a-262">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-262">Return Value</span></span>

- <span data-ttu-id="5005a-263">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、3DES 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-263">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-264">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-265">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-265">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) キー サイズが、3DES では有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-266">**NX_CRYPTO_UNSUPPORTED_KEY_SIZE** (0x20002) Key size is not a valid for 3DES.</span></span>

## <a name="_nx_crypto_method_3des_operation"></a><span data-ttu-id="5005a-267">_nx_crypto_method_3des_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-267">_nx_crypto_method_3des_operation</span></span>

<span data-ttu-id="5005a-268">3DES を使用して暗号化または暗号化解除を行います。</span><span class="sxs-lookup"><span data-stu-id="5005a-268">Encrypt or Decrypt with 3DES.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-269">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-269">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-270">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-270">Description</span></span>

<span data-ttu-id="5005a-271">この関数では、3DES の暗号化または暗号化解除の操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-271">This function performs 3DES encryption or decryption operation.</span></span> <span data-ttu-id="5005a-272">3DES 制御ブロックは、_ *nx_crypto_method_3des_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-272">The 3DES control block must have been initialized with _ *nx_crypto_method_3des_init()*.</span></span> <span data-ttu-id="5005a-273">実行される 3DES アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-273">The 3DES algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-274">入力バッファーのサイズは、8 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-274">The input buffer size must be a multiple of 8 bytes.</span></span> <span data-ttu-id="5005a-275">暗号化が解除されたデータのサイズは、入力データ サイズと同じサイズです。</span><span class="sxs-lookup"><span data-stu-id="5005a-275">The size of the decrypted data is the same size of the input data size.</span></span> <span data-ttu-id="5005a-276">3DES ブロック サイズの偶数倍にするために、暗号化されたデータがパディングされた場合、そのパディングは出力バッファーに含められます。また、そのパディングはアプリケーションによって処理される必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-276">If the encrypted data was padded to achieve an even multiple of the 3DES block size, the padding will be included in the output buffer and must be handled by the application.</span></span>

<span data-ttu-id="5005a-277">この操作では、状態情報は保持されず、3DES 制御ブロック内のキー マテリアルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-277">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-278">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-278">Parameters</span></span>

- <span data-ttu-id="5005a-279">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-279">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-280">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-280">Valid operations are:</span></span>
  - <span data-ttu-id="5005a-281">*NX_CRYPTO_ENCRYPT*</span><span class="sxs-lookup"><span data-stu-id="5005a-281">*NX_CRYPTO_ENCRYPT*</span></span>
  - <span data-ttu-id="5005a-282">*NX_CRYPTO_DECRYPT*</span><span class="sxs-lookup"><span data-stu-id="5005a-282">*NX_CRYPTO_DECRYPT*</span></span>
- <span data-ttu-id="5005a-283">**handle** *_nx_crypto_method_3des_init()* によって初期化されたハンドル。</span><span class="sxs-lookup"><span data-stu-id="5005a-283">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="5005a-284">**method** 有効な 3DES 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-284">**method** Pointer to the valid 3DES crypto method.</span></span> <span data-ttu-id="5005a-285">ここで使用される暗号化メソッドは、*nx_crypto_method_3des_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-285">The crypto method used here must be the same used in the *nx_crypto_method_3des_init().*</span></span>
- <span data-ttu-id="5005a-286">**input_data** 暗号化されたテキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-286">**input_data** Points to a buffer containing encrypted text data.</span></span>
<span data-ttu-id="5005a-287">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-287">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-288">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-288">**input_data_size** Size of the input data, in bytes.</span></span> <span data-ttu-id="5005a-289">入力データのサイズは、8 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-289">The input data size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="5005a-290">**iv_ptr** 初期ベクトルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-290">**iv_ptr** Pointer to the Initial Vector.</span></span> <span data-ttu-id="5005a-291">IV バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-291">There are no restrictions on the IV buffer.</span></span>
- <span data-ttu-id="5005a-292">**iv_size** 初期ベクトル ブロックのサイズ (バイト単位)。このフィールドは 8 である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-292">**iv_size** Size of the Initial Vector block, in bytes This field must be 8.</span></span>
- <span data-ttu-id="5005a-293">**output_buffer** クリア テキスト データを格納する 3DES 用メモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-293">**output_buffer** Pointer to the memory area for 3DES to store the clear text data.</span></span> <span data-ttu-id="5005a-294">アプリケーションで出力バッファーに領域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-294">Application must allocate space for the output buffer.</span></span> <span data-ttu-id="5005a-295">出力バッファーは、入力バッファーと重複することがあります。</span><span class="sxs-lookup"><span data-stu-id="5005a-295">Output buffer may overlap with input buffer.</span></span> <span data-ttu-id="5005a-296">出力バッファーと入力バッファーが同じ開始アドレスを共有している場合は、これらが重複することがあります。</span><span class="sxs-lookup"><span data-stu-id="5005a-296">The output buffer may overlap with the input buffer if they share the same starting address.</span></span>
- <span data-ttu-id="5005a-297">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-297">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="5005a-298">出力バッファー サイズは、少なくとも入力バッファー サイズと同じである必要があり、出力バッファー サイズは 8 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-298">Output buffer size must be at least the same of the input buffer size, and the output buffer size must be a multiple of 8 bytes.</span></span>
- <span data-ttu-id="5005a-299">**crypto_metadata** *_nx_crypto_method_3des_init()* で使用される 3DES 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-299">**crypto_metadata** Pointer to the 3DES control block used in *_nx_crypto_method_3des_init()*.</span></span>
- <span data-ttu-id="5005a-300">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-300">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-301">3DES の場合、メタデータ サイズは *sizeof(NX_3DES)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-301">For 3DES, the metadata size must be *sizeof(NX_3DES)*</span></span>
- <span data-ttu-id="5005a-302">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-302">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-303">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-303">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-304">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-304">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-305">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-305">Any values passed in are silently ignored.</span></span>

### <a name="description"></a><span data-ttu-id="5005a-306">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-306">Description</span></span>

<span data-ttu-id="5005a-307">この関数では、3DES 暗号化を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-307">This function performs 3DES encryption.</span></span> <span data-ttu-id="5005a-308">3DES 制御ブロックは、_ *nx_crypto_moethod_3des_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-308">The 3DES control block must have been initialized with _ *nx_crypto_moethod_3des_init()*.</span></span> <span data-ttu-id="5005a-309">この操作では、状態情報は保持されず、3DES 制御ブロック内のキー マテリアルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-309">This operation does not keep state information, and does not alter the key material in the 3DES control block.</span></span> <span data-ttu-id="5005a-310">この関数ではパディングは追加されないため、暗号化操作を呼び出す前に、呼び出し元でパディングを処理する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="5005a-310">Note that padding is not added by this function so the caller will need to handle padding before invoking the encryption operation.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-311">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-311">Return Values</span></span>

- <span data-ttu-id="5005a-312">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、3DES 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-312">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the 3DES control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-313">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-314">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-314">**NX_PTR_ERROR (0x07)** Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_3des_cleanup"></a><span data-ttu-id="5005a-315">_nx_crypto_method_3des_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-315">_nx_crypto_method_3des_cleanup</span></span>

<span data-ttu-id="5005a-316">3DES 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-316">Clean up the 3DES control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-317">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-317">Prototype</span></span>

```c
UINT _nx_crypto_method_3des_cleanup(VOID *crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-318">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-318">Description</span></span>

<span data-ttu-id="5005a-319">アプリケーションでは、この 3DES セッションが不要になったと判断した後にこの関数を呼び出して、3DES 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-319">Application calls this function to clean up the 3DES control block after it determines this 3DES session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-320">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-320">Parameters</span></span>

- <span data-ttu-id="5005a-321">**handle** *_nx_crypto_method_3des_init()* によって初期化されたハンドル。</span><span class="sxs-lookup"><span data-stu-id="5005a-321">**handle** The handle initialized by *_nx_crypto_method_3des_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-322">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-322">Return Values</span></span>

- <span data-ttu-id="5005a-323">**NX_CRYPTO_SUCCESS** (0x00) 3DES セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-323">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the 3DES session.</span></span>
- <span data-ttu-id="5005a-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-324">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_drbg_init"></a><span data-ttu-id="5005a-325">_nx_crypto_method_drbg_init</span><span class="sxs-lookup"><span data-stu-id="5005a-325">_nx_crypto_method_drbg_init</span></span>

<span data-ttu-id="5005a-326">DRBG 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-326">Initializes the DRBG crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-327">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-327">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-328">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-328">Description</span></span>

<span data-ttu-id="5005a-329">この関数では、指定されたキー文字列を使用して、DRBG 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-329">This function initializes the DRBG control block with the given key string.</span></span> <span data-ttu-id="5005a-330">いったん DRBG 制御ブロックが初期化されると、後続の DRBG 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-330">Once the DRBG control block is initialized, subsequent DRBG operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-331">アプリケーションは複数の DRBG 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-331">Application may create multiple DRBG control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-332">DRBG 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-332">Initializing the DRBG control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-333">DRBG 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-333">Re-initializing the DRBG control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-334">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-334">Parameters</span></span>

- <span data-ttu-id="5005a-335">**method** 有効な DRBG 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-335">**method** Pointer to a valid DRBG crypto method control block.</span></span> <span data-ttu-id="5005a-336">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-336">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-337">*crypto_method_drbg*</span><span class="sxs-lookup"><span data-stu-id="5005a-337">*crypto_method_drbg*</span></span>
- <span data-ttu-id="5005a-338">**key** このフィールドは DRBG では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-338">**key** This field is not used for DRBG.</span></span>
- <span data-ttu-id="5005a-339">**key_size_in_bits** このフィールドは DRBG では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-339">**key_size_in_bits** This field is not used for DRBG.</span></span>
- <span data-ttu-id="5005a-340">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-340">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-341">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-341">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-342">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-342">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-343">**crypto_metadata** DRBG 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-343">**crypto_metadata** Pointer to a valid memory space for the DRBG control block.</span></span> <span data-ttu-id="5005a-344">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-344">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-345">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-345">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-346">DRBG の場合、メタデータ サイズは *sizeof(NX_CRYPTO_DRBG)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-346">For DRBG, the metadata size must be *sizeof(NX_CRYPTO_DRBG)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-347">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-347">Return Values</span></span>

- <span data-ttu-id="5005a-348">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、DRBG 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-348">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the DRBG control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-349">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-350">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-350">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_drbg_operation"></a><span data-ttu-id="5005a-351">_nx_crypto_method_drbg_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-351">_nx_crypto_method_drbg_operation</span></span>

<span data-ttu-id="5005a-352">DRBG 操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-352">Perform DRBG operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-353">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-353">Prototype</span></span>

```c
UINT __nx_crypto_method_drbg_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-354">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-354">Description</span></span>

<span data-ttu-id="5005a-355">この関数では、DRBG 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-355">This function performs DRBG operation.</span></span> <span data-ttu-id="5005a-356">DRBG 制御ブロックは、_ *nx_crypto_method_drbg_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-356">The DRBG control block must have been initialized with _ *nx_crypto_method_drbg_init()*.</span></span> <span data-ttu-id="5005a-357">実行される DRBG アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-357">The DRBG algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span> <span data-ttu-id="5005a-358">既定では、DRBG には AE-128 が使用されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-358">By default AES-128 is used for DRBG.</span></span>

<span data-ttu-id="5005a-359">操作が NX_CRYPTO_DRBG_OPTIONS_SET である場合、入力は、NX_CRYPTO_DRBG_OPTIONS 構造体を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-359">When the operation is NX_CRYPTO_DRBG_OPTIONS_SET, the input points to NX_CRYPTO_DRBG_OPTIONS structure.</span></span> <span data-ttu-id="5005a-360">操作が NX_CRYPTO_DRBG_INSTANTIATE である場合、キーは nonce を指し示し、入力はパーソナル化文字列を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-360">When the operation is NX_CRYPTO_DRBG_INSTANTIATE, the key points to nonce, input points to personalization string.</span></span> <span data-ttu-id="5005a-361">操作が NX_CRYPTO_DRBG_RESEED または NX_CRYPTO_DRBG_GENERATE である場合、入力は追加の入力を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-361">When the operation is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, the input points to additional input.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-362">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-362">Parameters</span></span>

- <span data-ttu-id="5005a-363">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-363">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-364">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-364">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span><span class="sxs-lookup"><span data-stu-id="5005a-365">*NX_CRYPTO_DRBG_OPTIONS_SET*</span></span>
  - <span data-ttu-id="5005a-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-366">*NX_CRYPTO_DRBG_INSTANTIATE*</span></span>
  - <span data-ttu-id="5005a-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-367">*NX_CRYPTO_DRBG_RESEED NX_CRYPTO_DRBG_GENERATE*</span></span>
- <span data-ttu-id="5005a-368">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-368">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-369">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-369">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-370">**method** 有効な DRBG 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-370">**method** Pointer to the valid DRBG crypto method.</span></span> <span data-ttu-id="5005a-371">ここで使用される暗号化メソッドは、_ *nx_crypto_method_drbg_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-371">The crypto method used here must be the same used in the _ *nx_crypto_method_drbg_init().*</span></span>
- <span data-ttu-id="5005a-372">**key** インスタンス作成操作の nonce へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-372">**key** Pointer to the the nonce for the instantiate operation.</span></span> <span data-ttu-id="5005a-373">このフィールドは他の操作には使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-373">This field is not used for other operations.</span></span>
- <span data-ttu-id="5005a-374">**key_size_in_bits** nonce のサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-374">**key_size_in_bits** Size of the nonce, in bits.</span></span> <span data-ttu-id="5005a-375">このフィールドは他の操作には使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-375">This field is not used for other operations.</span></span>
- <span data-ttu-id="5005a-376">**input** op が NX_CRYPTO_DRBG_OPTIONS_SET である場合、このフィールドは DRBG オプションを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-376">**input** When op is NX_CRYPTO_DRBG_OPTIONS_SET, this field points to DRBG options.</span></span> <span data-ttu-id="5005a-377">op が NX_CRYPTO_DRBG_INSTANTIATE である場合、このフィールドはパーソナル化文字列を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-377">When op is NX_CRYPTO_DRBG_INSTANTIATE, this field points to personalization string.</span></span> <span data-ttu-id="5005a-378">op が NX_CRYPTO_DRBG_RESEED または NX_CRYPTO_DRBG_GENERATE である場合、このフィールドは追加の入力データを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-378">When op is NX_CRYPTO_DRBG_RESEED or NX_CRYPTO_DRBG_GENERATE, this field points to additional input data.</span></span>
- <span data-ttu-id="5005a-379">**input_length_in_byte** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-379">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-380">**iv_ptr** このフィールドは DRBG では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-380">**iv_ptr** This field is not used for DRBG.</span></span>
- <span data-ttu-id="5005a-381">**output** op が NX_CRYPTO_DRBG_GENERATE である場合、このフィールドは、生成された DRBG のメモリ領域を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-381">**output** When op is NX_CRYPTO_DRBG_GENERATE, this field points to the memory area for the generated DRBG.</span></span> <span data-ttu-id="5005a-382">その他の場合、このフィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-382">Otherwise, this field is not used.</span></span>
- <span data-ttu-id="5005a-383">**output_length_in_byte** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-383">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-384">**crypto_metadata** *_nx_crypto_method_drbg_init()* で使用される DRBG 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-384">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>
- <span data-ttu-id="5005a-385">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-385">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-386">DRBG の場合、メタデータ サイズは *sizeof(NX_CRYPTO_DRBG)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-386">For DRBG, the metadata size must *sizeof(NX_CRYPTO_DRBG)*</span></span>
- <span data-ttu-id="5005a-387">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-387">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-388">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-388">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-389">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-389">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-390">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-390">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-391">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-391">Return Values</span></span>

- <span data-ttu-id="5005a-392">**NX_CRYPTO_SUCCESS** (0x00) DRBG 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-392">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the DRBG operation.</span></span>
- <span data-ttu-id="5005a-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-393">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-394">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-394">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な DRBG アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-395">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid DRBG algorithm being specified.</span></span>
- <span data-ttu-id="5005a-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-396">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_drbg_cleanup"></a><span data-ttu-id="5005a-397">_nx_crypto_method_drbg_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-397">_nx_crypto_method_drbg_cleanup</span></span>

<span data-ttu-id="5005a-398">DRBG 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-398">Clean up the DRBG control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-399">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-399">Prototype</span></span>

```c
UINT _nx_crypto_method_drbg_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-400">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-400">Description</span></span>

<span data-ttu-id="5005a-401">アプリケーションでは、この DRBG セッションが不要になったと判断した後にこの関数を呼び出して、DRBG 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-401">Application calls this function to clean up the DRBG control block after it determines this DRBG session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-402">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-402">Parameters</span></span>

- <span data-ttu-id="5005a-403">**crypto_metadata** *_nx_crypto_method_drbg_init()* で使用される DRBG 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-403">**crypto_metadata** Pointer to the DRBG control block used in *_nx_crypto_method_drbg_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-404">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-404">Return Values</span></span>

- <span data-ttu-id="5005a-405">**NX_CRYPTO_SUCCESS** (0x00) DRBG セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-405">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the DRBG session.</span></span>
- <span data-ttu-id="5005a-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-406">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdh_init"></a><span data-ttu-id="5005a-407">_nx_crypto_method_ecdh_init</span><span class="sxs-lookup"><span data-stu-id="5005a-407">_nx_crypto_method_ecdh_init</span></span>

<span data-ttu-id="5005a-408">ECDH 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-408">Initializes the ECDH crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-409">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-409">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-410">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-410">Description</span></span>

<span data-ttu-id="5005a-411">この関数では、指定されたキー文字列を使用して、ECDH 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-411">This function initializes the ECDH control block with the given key string.</span></span> <span data-ttu-id="5005a-412">いったん ECDH 制御ブロックが初期化されると、後続の ECDH 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-412">Once the ECDH control block is initialized, subsequent ECDH operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-413">アプリケーションは複数の ECDH 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-413">Application may create multiple ECDH control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-414">ECDH 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-414">Initializing the ECDH control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-415">ECDH 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-415">Re-initializing the ECDH control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-416">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-416">Parameters</span></span>

- <span data-ttu-id="5005a-417">**method** 有効な ECDH 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-417">**method** Pointer to a valid ECDH crypto method control block.</span></span> <span data-ttu-id="5005a-418">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-418">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-419">*crypto_method_ecdh*</span><span class="sxs-lookup"><span data-stu-id="5005a-419">*crypto_method_ecdh*</span></span>
- <span data-ttu-id="5005a-420">**key** このフィールドは ECDH では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-420">**key** This field is not used for ECDH.</span></span>
- <span data-ttu-id="5005a-421">**key_size_in_bits** このフィールドは ECDH では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-421">**key_size_in_bits** This field is not used for ECDH.</span></span>
- <span data-ttu-id="5005a-422">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-422">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-423">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-423">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-424">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-424">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-425">**crypto_metadata** ECDH 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-425">**crypto_metadata** Pointer to a valid memory space for the ECDH control block.</span></span> <span data-ttu-id="5005a-426">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-426">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-427">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-427">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-428">ECDH の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDH)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-428">For ECDH, the metadata size must be *sizeof(NX_CRYPTO_ECDH)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-429">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-429">Return Values</span></span>

- <span data-ttu-id="5005a-430">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、ECDH 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-430">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDH control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-431">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-432">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-432">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdh_operation"></a><span data-ttu-id="5005a-433">_nx_crypto_method_ecdh_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-433">_nx_crypto_method_ecdh_operation</span></span>

<span data-ttu-id="5005a-434">ECDH 操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-434">Perform ECDH operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-435">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-435">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-436">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-436">Description</span></span>

<span data-ttu-id="5005a-437">この関数では、ECDH 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-437">This function performs ECDH operation.</span></span> <span data-ttu-id="5005a-438">ECDH 制御ブロックは、_ *nx_crypto_method_ecdh_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-438">The ECDH control block must have been initialized with _ *nx_crypto_method_ecdh_init()*.</span></span> <span data-ttu-id="5005a-439">実行される ECDH アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-439">The ECDH algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-440">操作が NX_CRYPTO_EC_CURVE_SET である場合、入力は楕円曲線暗号化メソッドを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-440">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="5005a-441">操作が NX_CRYPTO_EC_KEY_PAIR_GENERATE である場合、出力は NX_CRYPTO_EXTENDED_OUTPUT 構造体を指し示し、キーの組が nx_crypto_extended_output_data にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5005a-441">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="5005a-442">操作が NX_CRYPTO_DH_SETUP である場合、公開キーが nx_crypto_extended_output_data に返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-442">When the operation is NX_CRYPTO_DH_SETUP, the public key is returned to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="5005a-443">操作が NX_CRYPTO_DH_KEY_PAIR_IMPORT である場合、入力は公開キーを指し示し、キーは秘密キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-443">When the operation is NX_CRYPTO_DH_KEY_PAIR_IMPORT, the input points to public key and key points to private key.</span></span> <span data-ttu-id="5005a-444">操作が NX_CRYPTO_DH_PRIVATE_KEY_EXPORT である場合、秘密キーが nx_crypto_extended_output_data にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5005a-444">When the operation is NX_CRYPTO_DH_PRIVATE_KEY_EXPORT, the private key is copied to nx_crypto_extended_output_data.</span></span> <span data-ttu-id="5005a-445">操作が NX_CRYPTO_DH_CALCULATE である場合、入力はリモートの公開キーを指し示し、共有シークレットが nx_crypto_extended_output_data にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5005a-445">When the operation is NX_CRYPTO_DH_CALCULATE, the input points to remote public key and the shared secret is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-446">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-446">Parameters</span></span>

- <span data-ttu-id="5005a-447">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-447">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-448">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-448">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-449">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="5005a-449">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="5005a-450">*NX_CRYPTO_DH_SETUP*</span><span class="sxs-lookup"><span data-stu-id="5005a-450">*NX_CRYPTO_DH_SETUP*</span></span>
  - <span data-ttu-id="5005a-451">*NX_CRYPTO_DH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-451">*NX_CRYPTO_DH_CALCULATE*</span></span>
  - <span data-ttu-id="5005a-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span><span class="sxs-lookup"><span data-stu-id="5005a-452">*NX_CRYPTO_DH_KEY_PAIR_IMPOPRT*</span></span>
  - <span data-ttu-id="5005a-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-453">*NX_CRYPTO_DH_KEY_PAIR_GENERATE*</span></span>
  - <span data-ttu-id="5005a-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span><span class="sxs-lookup"><span data-stu-id="5005a-454">*NX_CRYPTO_DH_PRIVATE_KEY_EXPORT*</span></span>
- <span data-ttu-id="5005a-455">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-455">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-456">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-456">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-457">**method** 有効な ECDH 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-457">**method** Pointer to the valid ECDH crypto method.</span></span> <span data-ttu-id="5005a-458">ここで使用される暗号化メソッドは、_ *nx_crypto_method_ecdh_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-458">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdh_init().*</span></span>
- <span data-ttu-id="5005a-459">**key** op が NX_CRYPTO_DH_IMPORT_KEY_PAIR である場合、このフィールドは秘密キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-459">**key** When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to private key.</span></span> <span data-ttu-id="5005a-460">その他の場合、このフィールドは ECDH では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-460">Otherwise, this field is not used for ECDH.</span></span>
- <span data-ttu-id="5005a-461">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-461">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-462">**input** op が NX_CRYPTO_EC_CURVE_SET である場合、このフィールドは楕円曲線暗号化メソッドを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-462">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="5005a-463">op が NX_CRYPTO_DH_SETUP である場合、このフィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-463">When op is NX_CRYPTO_DH_SETUP, this field is not used.</span></span> <span data-ttu-id="5005a-464">op が NX_CRYPTO_DH_CALCULATE である場合、このフィールドは、入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-464">When op is NX_CRYPTO_DH_CALCULATE, this field points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-465">op が NX_CRYPTO_DH_IMPORT_KEY_PAIR である場合、このフィールドは公開キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-465">When op is NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field points to public key.</span></span>
- <span data-ttu-id="5005a-466">**input_length_in_byte** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-466">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-467">**iv_ptr** このフィールドは ECDH では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-467">**iv_ptr** This field is not used for ECDH.</span></span>
- <span data-ttu-id="5005a-468">**output** op が NX_CRYPTO_EC_CURVE_SET または NX_CRYPTO_DH_IMPORT_KEY_PAIR である場合、このフィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-468">**output** When op is NX_CRYPTO_EC_CURVE_SET or NX_CRYPTO_DH_IMPORT_KEY_PAIR, this field is not used.</span></span> <span data-ttu-id="5005a-469">op が NX_CRYPTO_DH_SETUP である場合、このフィールドは、生成された ECDH 公開キーのメモリ領域を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-469">When op is NX_CRYPTO_DH_SETUP, this field points to the memory area for the generated ECDH public key.</span></span> <span data-ttu-id="5005a-470">op が NX_CRYPTO_DH_CALCULATE である場合、このフィールドは、生成された ECDH 共有シークレットのメモリ領域を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-470">When op is NX_CRYPTO_DH_CALCULATE, this field points to the memory area for the generated ECDH shared secret.</span></span>
- <span data-ttu-id="5005a-471">**output_length_in_byte** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-471">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-472">**crypto_metadata** *_nx_crypto_method_ecdh_init()* で使用される ECDH 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-472">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>
- <span data-ttu-id="5005a-473">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-473">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-474">ECDH の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDH)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-474">For ECDH, the metadata size must *sizeof(NX_CRYPTO_ECDH)*</span></span>
- <span data-ttu-id="5005a-475">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-475">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-476">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-476">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-477">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-477">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-478">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-478">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-479">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-479">Return Values</span></span>

- <span data-ttu-id="5005a-480">**NX_CRYPTO_SUCCESS** (0x00) ECDH 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-480">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDH operation.</span></span>
- <span data-ttu-id="5005a-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-481">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-482">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-482">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な ECDH アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-483">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDH algorithm being specified.</span></span>
- <span data-ttu-id="5005a-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-484">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdh_cleanup"></a><span data-ttu-id="5005a-485">_nx_crypto_method_ecdh_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-485">_nx_crypto_method_ecdh_cleanup</span></span>

<span data-ttu-id="5005a-486">ECDH 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-486">Clean up the ECDH control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-487">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-487">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdh_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-488">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-488">Description</span></span>

<span data-ttu-id="5005a-489">アプリケーションでは、この ECDH セッションが不要になったと判断した後にこの関数を呼び出して、ECDH 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-489">Application calls this function to clean up the ECDH control block after it determines this ECDH session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-490">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-490">Parameters</span></span>

- <span data-ttu-id="5005a-491">**crypto_metadata** *_nx_crypto_method_ecdh_init()* で使用される ECDH 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-491">**crypto_metadata** Pointer to the ECDH control block used in *_nx_crypto_method_ecdh_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-492">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-492">Return Values</span></span>

- <span data-ttu-id="5005a-493">**NX_CRYPTO_SUCCESS** (0x00) ECDH セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-493">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDH session.</span></span>
- <span data-ttu-id="5005a-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-494">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_ecdsa_init"></a><span data-ttu-id="5005a-495">_nx_crypto_method_ecdsa_init</span><span class="sxs-lookup"><span data-stu-id="5005a-495">_nx_crypto_method_ecdsa_init</span></span>

<span data-ttu-id="5005a-496">ECDSA 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-496">Initializes the ECDSA crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-497">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-497">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-498">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-498">Description</span></span>

<span data-ttu-id="5005a-499">この関数では、指定されたキー文字列を使用して、ECDSA 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-499">This function initializes the ECDSA control block with the given key string.</span></span> <span data-ttu-id="5005a-500">いったん ECDSA 制御ブロックが初期化されると、後続の ECDSA 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-500">Once the ECDSA control block is initialized, subsequent ECDSA operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-501">アプリケーションは複数の ECDSA 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-501">Application may create multiple ECDSA control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-502">ECDSA 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-502">Initializing the ECDSA control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-503">ECDSA 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-503">Re-initializing the ECDSA control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-504">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-504">Parameters</span></span>

- <span data-ttu-id="5005a-505">**method** 有効な ECDSA 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-505">**method** Pointer to a valid ECDSA crypto method control block.</span></span> <span data-ttu-id="5005a-506">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-506">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-507">*crypto_method_ecdsa*</span><span class="sxs-lookup"><span data-stu-id="5005a-507">*crypto_method_ecdsa*</span></span>
- <span data-ttu-id="5005a-508">**key** このフィールドは ECDSA では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-508">**key** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="5005a-509">**key_size_in_bits** このフィールドは ECDSA では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-509">**key_size_in_bits** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="5005a-510">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-510">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-511">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-511">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-512">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-512">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-513">**crypto_metadata** ECDSA 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-513">**crypto_metadata** Pointer to a valid memory space for the ECDSA control block.</span></span> <span data-ttu-id="5005a-514">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-514">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-515">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-515">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-516">ECDSA の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDSA)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-516">For ECDSA, the metadata size must be *sizeof(NX_CRYPTO_ECDSA)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-517">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-517">Return Values</span></span>

- <span data-ttu-id="5005a-518">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、ECDSA 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-518">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the ECDSA control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-519">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-520">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-520">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_ecdsa_operation"></a><span data-ttu-id="5005a-521">_nx_crypto_method_ecdsa_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-521">_nx_crypto_method_ecdsa_operation</span></span>

<span data-ttu-id="5005a-522">ECDSA 操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-522">Perform ECDSA operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-523">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-523">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-524">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-524">Description</span></span>

<span data-ttu-id="5005a-525">この関数では、ECDSA 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-525">This function performs ECDSA operation.</span></span> <span data-ttu-id="5005a-526">ECDSA 制御ブロックは、_ *nx_crypto_method_ecdsa_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-526">The ECDSA control block must have been initialized with _ *nx_crypto_method_ecdsa_init()*.</span></span> <span data-ttu-id="5005a-527">実行される ECDH アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-527">The ECDSA algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-528">操作が NX_CRYPTO_EC_CURVE_SET である場合、入力は楕円曲線暗号化メソッドを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-528">When the operation is NX_CRYPTO_EC_CURVE_SET, the input points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="5005a-529">操作が NX_CRYPTO_EC_KEY_PAIR_GENERATE である場合、出力は NX_CRYPTO_EXTENDED_OUTPUT 構造体を指し示し、キーの組が nx_crypto_extended_output_data にコピーされます。</span><span class="sxs-lookup"><span data-stu-id="5005a-529">When the operation is NX_CRYPTO_EC_KEY_PAIR_GENERATE, the output points to NX_CRYPTO_EXTENDED_OUTPUT structure and the key pair is copied to nx_crypto_extended_output_data.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-530">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-530">Parameters</span></span>

- <span data-ttu-id="5005a-531">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-531">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-532">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-532">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-533">*NX_CRYPTO_EC_CURVE_SET*</span><span class="sxs-lookup"><span data-stu-id="5005a-533">*NX_CRYPTO_EC_CURVE_SET*</span></span>
  - <span data-ttu-id="5005a-534">*NX_CRYPTO_AUTHENTICATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-534">*NX_CRYPTO_AUTHENTICATE*</span></span>
  - <span data-ttu-id="5005a-535">*NX_CRYPTO_VERIFY*</span><span class="sxs-lookup"><span data-stu-id="5005a-535">*NX_CRYPTO_VERIFY*</span></span>
- <span data-ttu-id="5005a-536">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-536">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-537">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-537">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-538">**method** 有効な ECDSA 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-538">**method** Pointer to the valid ECDSA crypto method.</span></span> <span data-ttu-id="5005a-539">ここで使用される暗号化メソッドは、_ *nx_crypto_method_ecdsa_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-539">The crypto method used here must be the same used in the _ *nx_crypto_method_ecdsa_init().*</span></span>
- <span data-ttu-id="5005a-540">**key** op が NX_CRYPTO_VERIFY である場合にキーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-540">**key** Points to the key when op is NX_CRYPTO_VERIFY.</span></span> <span data-ttu-id="5005a-541">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-541">There are not restrictions on key buffer.</span></span> <span data-ttu-id="5005a-542">このフィールドは、op の他の値に対しては使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-542">This field is not used for other values of op.</span></span>
- <span data-ttu-id="5005a-543">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-543">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-544">**input** op が NX_CRYPTO_EC_CURVE_SET である場合、このフィールドは楕円曲線暗号化メソッドを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-544">**input** When op is NX_CRYPTO_EC_CURVE_SET, this field points to Elliptic Curve crypto method.</span></span> <span data-ttu-id="5005a-545">それ以外の場合、このフィールドは入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-545">Otherwise, this field points to a buffer containing input text data.</span></span>
- <span data-ttu-id="5005a-546">**input_length_in_byte** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-546">**input_length_in_byte** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-547">**iv_ptr** このフィールドは ECDSA では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-547">**iv_ptr** This field is not used for ECDSA.</span></span>
- <span data-ttu-id="5005a-548">**output** op が NX_CRYPTO_EC_CURVE_SET である場合、このフィールドは使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-548">**output** When op is NX_CRYPTO_EC_CURVE_SET, this field is not used.</span></span> <span data-ttu-id="5005a-549">op が NX_CRYPTO_AUTHENTICATE である場合、このフィールドは、生成された ECDSA シグネチャのメモリ領域を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-549">When op is NX_CRYPTO_AUTHENTICATE, this field points to the memory area for the generated ECDSA signature.</span></span> <span data-ttu-id="5005a-550">op が NX_CRYPTO_VERIFY である場合、このフィールドは、検証される ECDSA シグネチャのメモリ領域を指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-550">When op is NX_CRYPTO_VERIFY, this field points to the memory area for the verified ECDSA signature.</span></span>
- <span data-ttu-id="5005a-551">**output_length_in_byte** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-551">**output_length_in_byte** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-552">**crypto_metadata** *_nx_crypto_method_ecdsa_init()* で使用される ECDSA 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-552">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>
- <span data-ttu-id="5005a-553">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-553">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-554">ECDSA の場合、メタデータ サイズは *sizeof(NX_CRYPTO_ECDSA)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-554">For ECDSA, the metadata size must *sizeof(NX_CRYPTO_ECDSA)*</span></span>
- <span data-ttu-id="5005a-555">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-555">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-556">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-556">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-557">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-557">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-558">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-558">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-559">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-559">Return Values</span></span>

- <span data-ttu-id="5005a-560">**NX_CRYPTO_SUCCESS** (0x00) ECDSA 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-560">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the ECDSA operation.</span></span>
- <span data-ttu-id="5005a-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-561">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-562">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-562">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な ECDSA アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-563">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid ECDSA algorithm being specified.</span></span>
- <span data-ttu-id="5005a-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-564">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_ecdsa_cleanup"></a><span data-ttu-id="5005a-565">_nx_crypto_method_ecdsa_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-565">_nx_crypto_method_ecdsa_cleanup</span></span>

<span data-ttu-id="5005a-566">ECDSA 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-566">Clean up the ECDSA control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-567">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-567">Prototype</span></span>

```c
UINT _nx_crypto_method_ecdsa_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-568">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-568">Description</span></span>

<span data-ttu-id="5005a-569">アプリケーションでは、この ECDSA セッションが不要になったと判断した後にこの関数を呼び出して、ECDSA 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-569">Application calls this function to clean up the ECDSA control block after it determines this ECDSA session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-570">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-570">Parameters</span></span>

- <span data-ttu-id="5005a-571">**crypto_metadata** *_nx_crypto_method_ecdsa_init()* で使用される ECDSA 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-571">**crypto_metadata** Pointer to the ECDSA control block used in *_nx_crypto_method_ecdsa_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-572">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-572">Return Values</span></span>

- <span data-ttu-id="5005a-573">**NX_CRYPTO_SUCCESS** (0x00) ECDSA セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-573">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the ECDSA session.</span></span>
- <span data-ttu-id="5005a-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-574">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_md5_init"></a><span data-ttu-id="5005a-575">_nx_crypto_method_hmac_md5_init</span><span class="sxs-lookup"><span data-stu-id="5005a-575">_nx_crypto_method_hmac_md5_init</span></span>

<span data-ttu-id="5005a-576">HMAC MD5 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-576">Initializes the HMAC MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-577">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-577">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-578">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-578">Description</span></span>

<span data-ttu-id="5005a-579">この関数では、指定されたキー文字列を使用して、HMAC MD5 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-579">This function initializes the HMAC MD5 control block with the given key string.</span></span> <span data-ttu-id="5005a-580">いったん HMAC MD5 制御ブロックが初期化されると、後続の HMAC MD5 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-580">Once the HMAC MD5 control block is initialized, subsequent HMAC MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-581">アプリケーションは複数の HMAC MD5 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-581">Application may create multiple HMAC MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-582">HMAC MD5 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-582">Initializing the HMAC MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-583">HMAC MD5 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-583">Re-initializing the HMAC MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-584">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-584">Parameters</span></span>

- <span data-ttu-id="5005a-585">**method** 有効な HMAC MD5 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-585">**method** Pointer to a valid HMAC MD5 crypto method control block.</span></span>
<span data-ttu-id="5005a-586">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-586">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-587">*crypto_method_hmac_md5*</span><span class="sxs-lookup"><span data-stu-id="5005a-587">*crypto_method_hmac_md5*</span></span>
- <span data-ttu-id="5005a-588">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-588">**key** Points to the key.</span></span> <span data-ttu-id="5005a-589">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-589">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-590">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-590">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-591">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-591">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-592">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-592">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-593">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-593">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-594">**crypto_metadata** HMAC MD5 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-594">**crypto_metadata** Pointer to a valid memory space for the HMAC MD5 control block.</span></span> <span data-ttu-id="5005a-595">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-595">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-596">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-596">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-597">HMAC MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-597">For HMAC MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-598">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-598">Return Values</span></span>

- <span data-ttu-id="5005a-599">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC MD5 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-599">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-600">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-601">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-601">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_md5_operation"></a><span data-ttu-id="5005a-602">_nx_crypto_method_hmac_md5_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-602">_nx_crypto_method_hmac_md5_operation</span></span>

<span data-ttu-id="5005a-603">HMAC MD5 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-603">Perform an HMAC MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-604">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-604">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-605">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-605">Description</span></span>

<span data-ttu-id="5005a-606">この関数では、HMAC MD5 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-606">This function performs HMAC MD5 hash operation.</span></span> <span data-ttu-id="5005a-607">HMAC MD5 制御ブロックは、_ *nx_crypto_method_hmac_md5_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-607">The HMAC MD5 control block must have been initialized with _ *nx_crypto_method_hmac_md5_init()*.</span></span> <span data-ttu-id="5005a-608">実行される HMAC MD5 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-608">The HMAC MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-609">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 16 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-609">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="5005a-610">この操作では、状態情報は保持されず、HMAC MD5 制御ブロック内のキー マテリアルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-610">This operation does not keep state information, and does not alter the key material in the HMAC MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-611">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-611">Parameters</span></span>

- <span data-ttu-id="5005a-612">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-612">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-613">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-613">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-614">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-614">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-615">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-615">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-616">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-616">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-617">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-617">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-618">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-618">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-619">**method** 有効な HMAC MD5 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-619">**method** Pointer to the valid HMAC MD5 crypto method.</span></span> <span data-ttu-id="5005a-620">ここで使用される暗号化メソッドは、*nx_crypto_method_hmac_md5_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-620">The crypto method used here must be the same used in the *nx_crypto_method_hmac_md5_init().*</span></span>
- <span data-ttu-id="5005a-621">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-621">**key** Points to the key.</span></span> <span data-ttu-id="5005a-622">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-622">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-623">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-623">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-624">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-624">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-625">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-625">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-626">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-626">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-627">**iv_ptr** このフィールドは HMAC MD5 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-627">**iv_ptr** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="5005a-628">**iv_size** このフィールドは HMAC MD5 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-628">**iv_size** This field is not used for HMAC MD5.</span></span>
- <span data-ttu-id="5005a-629">**output_buffer** 生成された HMAC MD5 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-629">**output_buffer** Pointer to the memory area for the generated HMAC MD5 hash.</span></span>
- <span data-ttu-id="5005a-630">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-630">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-631">**crypto_metadata** *_nx_crypto_method_hmac_md5_init()* で使用される HMAC MD5 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-631">**crypto_metadata** Pointer to the HMAC MD5 control block used in *_nx_crypto_method_hmac_md5_init()*.</span></span>
- <span data-ttu-id="5005a-632">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-632">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-633">HMAC MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-633">For HMAC MD5, the metadata size must *sizeof(NX_CRYPTO_MD5_HMAC)*</span></span>
- <span data-ttu-id="5005a-634">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-634">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-635">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-635">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-636">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-636">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-637">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-637">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-638">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-638">Return Values</span></span>

- <span data-ttu-id="5005a-639">**NX_CRYPTO_SUCCESS** (0x00) HMAC MD5 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-639">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC MD5 operation.</span></span>
- <span data-ttu-id="5005a-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-640">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-641">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-641">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC MD5 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-642">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC MD5 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-643">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_init"></a><span data-ttu-id="5005a-644">_nx_crypto_method_hmac_sha1_init</span><span class="sxs-lookup"><span data-stu-id="5005a-644">_nx_crypto_method_hmac_sha1_init</span></span>

<span data-ttu-id="5005a-645">HMAC SHA1 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-645">Initializes the HMAC SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-646">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-646">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-647">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-647">Description</span></span>

<span data-ttu-id="5005a-648">この関数では、指定されたキー文字列を使用して、HMAC SHA1 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-648">This function initializes the HMAC SHA1 control block with the given key string.</span></span> <span data-ttu-id="5005a-649">いったん HMAC SHA1 制御ブロックが初期化されると、後続の HMAC SHA1 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-649">Once the HMAC SHA1 control block is initialized, subsequent HMAC SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-650">アプリケーションは複数の HMAC SHA1 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-650">Application may create multiple HMAC SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-651">HMAC SHA1 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-651">Initializing the HMAC SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-652">HMAC SHA1 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-652">Re-initializing the HMAC SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-653">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-653">Parameters</span></span>

- <span data-ttu-id="5005a-654">**method** 有効な HMAC SHA1 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-654">**method** Pointer to a valid HMAC SHA1 crypto method control block.</span></span> <span data-ttu-id="5005a-655">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-655">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-656">*crypto_method_hmac_sha1*</span><span class="sxs-lookup"><span data-stu-id="5005a-656">*crypto_method_hmac_sha1*</span></span>
- <span data-ttu-id="5005a-657">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-657">**key** Points to the key.</span></span> <span data-ttu-id="5005a-658">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-658">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-659">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-659">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-660">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-660">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-661">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-661">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-662">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-662">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-663">**crypto_metadata** HMAC SHA1 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-663">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA1 control block.</span></span> <span data-ttu-id="5005a-664">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-664">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-665">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-665">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-666">HMAC SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-666">For HMAC SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-667">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-667">Return Values</span></span>

- <span data-ttu-id="5005a-668">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC SHA1 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-668">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-669">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-670">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-670">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_operation"></a><span data-ttu-id="5005a-671">_nx_crypto_method_hmac_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-671">_nx_crypto_method_hmac_sha1_operation</span></span>

<span data-ttu-id="5005a-672">HMAC SHA1 ハッシュ操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-672">Perform HMAC SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-673">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-673">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-674">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-674">Description</span></span>

<span data-ttu-id="5005a-675">この関数では、HMAC SHA1 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-675">This function performs HMAC SHA1 hash operation.</span></span> <span data-ttu-id="5005a-676">HMAC SHA1 制御ブロックは、_ *nx_crypto_method_hmac_sha1_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-676">The HMAC SHA1 control block must have been initialized with _ *nx_crypto_method_hmac_sha1_init()*.</span></span> <span data-ttu-id="5005a-677">実行される HMAC SHA1 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-677">The HMAC SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-678">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 20 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-678">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-679">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-679">Parameters</span></span>

- <span data-ttu-id="5005a-680">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-680">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-681">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-681">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-682">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-682">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-683">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-683">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-684">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-684">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-685">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-685">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-686">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-686">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-687">**method** 有効な HMAC SHA1 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-687">**method** Pointer to the valid HMAC SHA1 crypto method.</span></span> <span data-ttu-id="5005a-688">ここで使用される暗号化メソッドは、_ *nx_crypto_method_hmac_sha1_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-688">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha1_init().*</span></span>
- <span data-ttu-id="5005a-689">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-689">**key** Points to the key.</span></span> <span data-ttu-id="5005a-690">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-690">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-691">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-691">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-692">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-692">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-693">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-693">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-694">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-694">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-695">**iv_ptr** このフィールドは HMAC SHA1 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-695">**iv_ptr** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="5005a-696">**iv_size** このフィールドは HMAC SHA1 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-696">**iv_size** This field is not used for HMAC SHA1.</span></span>
- <span data-ttu-id="5005a-697">**output_buffer** 生成された HMAC SHA1 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-697">**output_buffer** Pointer to the memory area for the generated HMAC SHA1 hash.</span></span>
- <span data-ttu-id="5005a-698">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-698">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-699">**crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* で使用される HMAC SHA1 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-699">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>
- <span data-ttu-id="5005a-700">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-700">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-701">HMAC SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-701">For HMAC SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1_HMAC)*</span></span>
- <span data-ttu-id="5005a-702">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-702">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-703">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-703">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-704">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-704">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-705">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-705">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-706">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-706">Return Values</span></span>

- <span data-ttu-id="5005a-707">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-707">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA1 operation.</span></span>
- <span data-ttu-id="5005a-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-708">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-709">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-709">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC SHA1 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-710">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-711">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha1_cleanup"></a><span data-ttu-id="5005a-712">_nx_crypto_method_hmac_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-712">_nx_crypto_method_hmac_sha1_cleanup</span></span>

<span data-ttu-id="5005a-713">HMAC SHA1 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-713">Clean up the HMAC SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-714">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-714">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-715">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-715">Description</span></span>

<span data-ttu-id="5005a-716">アプリケーションでは、この HMAC SHA1 セッションが不要になったと判断した後にこの関数を呼び出して、HMAC SHA1 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-716">Application calls this function to clean up the HMAC SHA1 control block after it determines this HMAC SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-717">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-717">Parameters</span></span>

- <span data-ttu-id="5005a-718">**crypto_metadata** *_nx_crypto_method_hmac_sha1_init()* で使用される HMAC SHA1 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-718">**crypto_metadata** Pointer to the HMAC SHA1 control block used in *_nx_crypto_method_hmac_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-719">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-719">Return Values</span></span>

- <span data-ttu-id="5005a-720">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA1 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-720">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA1 session.</span></span>
- <span data-ttu-id="5005a-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-721">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_init"></a><span data-ttu-id="5005a-722">_nx_crypto_method_hmac_sha256_init</span><span class="sxs-lookup"><span data-stu-id="5005a-722">_nx_crypto_method_hmac_sha256_init</span></span>

<span data-ttu-id="5005a-723">HMAC SHA256 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-723">Initializes the HMAC SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-724">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-724">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-725">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-725">Description</span></span>

<span data-ttu-id="5005a-726">この関数では、指定されたキー文字列を使用して、HMAC SHA256 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-726">This function initializes the HMAC SHA256 control block with the given key string.</span></span> <span data-ttu-id="5005a-727">いったん HMAC SHA256 制御ブロックが初期化されると、後続の HMAC SHA256 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-727">Once the HMAC SHA256 control block is initialized, subsequent HMAC SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-728">アプリケーションは複数の HMAC SHA256 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-728">Application may create multiple HMAC SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-729">HMAC SHA256 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-729">Initializing the HMAC SH256 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-730">HMAC SHA256 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-730">Re-initializing the HMAC SHA256 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-731">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-731">Parameters</span></span>

- <span data-ttu-id="5005a-732">**method** 有効な HMAC SHA256 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-732">**method** Pointer to a valid HMAC SHA256 crypto method control block.</span></span> <span data-ttu-id="5005a-733">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-733">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-734">*crypto_method_hmac_sha224*</span><span class="sxs-lookup"><span data-stu-id="5005a-734">*crypto_method_hmac_sha224*</span></span>
  - <span data-ttu-id="5005a-735">*crypto_method_hmac_sha256*</span><span class="sxs-lookup"><span data-stu-id="5005a-735">*crypto_method_hmac_sha256*</span></span>
- <span data-ttu-id="5005a-736">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-736">**key** Points to the key.</span></span> <span data-ttu-id="5005a-737">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-737">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-738">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-738">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-739">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-739">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-740">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-740">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-741">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-741">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-742">**crypto_metadata** HMAC SHA256 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-742">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA256 control block.</span></span> <span data-ttu-id="5005a-743">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-743">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-744">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-744">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-745">HMAC SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYTPO_SHA256_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-745">For HMAC SHA256, the metadata size must be *sizeof(NX_CRYTPO_SHA256_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-746">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-746">Return Values</span></span>

- <span data-ttu-id="5005a-747">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC SHA256 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-747">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-748">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-749">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-749">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_operation"></a><span data-ttu-id="5005a-750">_nx_crypto_method_hmac_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-750">_nx_crypto_method_hmac_sha256_operation</span></span>

<span data-ttu-id="5005a-751">HMAC SHA256 ハッシュ操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-751">Perform HMAC SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-752">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-752">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-753">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-753">Description</span></span>

<span data-ttu-id="5005a-754">この関数では、HMAC SHA256 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-754">This function performs HMAC SHA256 hash operation.</span></span> <span data-ttu-id="5005a-755">HMAC SHA256 制御ブロックは、_ *nx_crypto_method_hmac_sha256_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-755">The HMAC SHA256 control block must have been initialized with _ *nx_crypto_method_hmac_sha256_init()*.</span></span> <span data-ttu-id="5005a-756">実行される HMAC SHA256 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-756">The HMAC SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-757">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA256 の場合は 32 バイト、SHA224 の場合は 28 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-757">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-758">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-758">Parameters</span></span>

- <span data-ttu-id="5005a-759">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-759">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-760">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-760">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-761">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-761">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-762">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-762">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-763">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-763">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-764">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-764">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-765">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-765">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-766">**method** 有効な HMAC SHA256 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-766">**method** Pointer to the valid HMAC SHA256 crypto method.</span></span> <span data-ttu-id="5005a-767">ここで使用される暗号化メソッドは、_ *nx_crypto_method_hmac_sha256_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-767">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha256_init().*</span></span>
- <span data-ttu-id="5005a-768">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-768">**key** Points to the key.</span></span> <span data-ttu-id="5005a-769">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-769">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-770">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-770">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-771">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-771">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-772">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-772">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-773">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-773">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-774">**iv_ptr** このフィールドは HMAC SHA256 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-774">**iv_ptr** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="5005a-775">**iv_size** このフィールドは HMAC SHA256 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-775">**iv_size** This field is not used for HMAC SHA256.</span></span>
- <span data-ttu-id="5005a-776">**output_buffer** 生成された HMAC SHA256 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-776">**output_buffer** Pointer to the memory area for the generated HMAC SHA256 hash.</span></span>
- <span data-ttu-id="5005a-777">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-777">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-778">**crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* で使用される HMAC SHA256 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-778">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>
- <span data-ttu-id="5005a-779">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-779">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-780">HMAC SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA256_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-780">For HMAC SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256_HMAC)*</span></span>
- <span data-ttu-id="5005a-781">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-781">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-782">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-782">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-783">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-783">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-784">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-784">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-785">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-785">Return Values</span></span>

- <span data-ttu-id="5005a-786">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-786">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA256 operation.</span></span>
- <span data-ttu-id="5005a-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-787">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-788">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-788">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC SHA256 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-789">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-790">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha256_cleanup"></a><span data-ttu-id="5005a-791">_nx_crypto_method_hmac_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-791">_nx_crypto_method_hmac_sha256_cleanup</span></span>

<span data-ttu-id="5005a-792">HMAC SHA256 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-792">Clean up the HMAC SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-793">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-793">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-794">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-794">Description</span></span>

<span data-ttu-id="5005a-795">アプリケーションでは、この HMAC SHA256 セッションが不要になったと判断した後にこの関数を呼び出して、HMAC SHA256 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-795">Application calls this function to clean up the HMAC SHA256 control block after it determines this HMAC SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-796">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-796">Parameters</span></span>

- <span data-ttu-id="5005a-797">**crypto_metadata** *_nx_crypto_method_hmac_sha256_init()* で使用される HMAC SHA256 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-797">**crypto_metadata** Pointer to the HMAC SHA256 control block used in *_nx_crypto_method_hmac_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-798">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-798">Return Values</span></span>

- <span data-ttu-id="5005a-799">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA256 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-799">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA256 session.</span></span>
- <span data-ttu-id="5005a-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-800">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_init"></a><span data-ttu-id="5005a-801">_nx_crypto_method_hmac_sha512_init</span><span class="sxs-lookup"><span data-stu-id="5005a-801">_nx_crypto_method_hmac_sha512_init</span></span>

<span data-ttu-id="5005a-802">HMAC SHA512 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-802">Initializes the HMAC SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-803">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-803">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-804">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-804">Description</span></span>

<span data-ttu-id="5005a-805">この関数では、指定されたキー文字列を使用して、HMAC SHA512 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-805">This function initializes the HMAC SHA512 control block with the given key string.</span></span> <span data-ttu-id="5005a-806">いったん HMAC SHA512 制御ブロックが初期化されると、後続の HMAC SHA512 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-806">Once the HMAC SHA512 control block is initialized, subsequent HMAC SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-807">アプリケーションは複数の HMAC SHA512 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-807">Application may create multiple HMAC SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-808">HMAC SHA512 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-808">Initializing the HMAC SH512 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-809">HMAC SHA512 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-809">Re-initializing the HMAC SHA512 control block abandons the current session and stars a new one with a new key.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-810">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-810">Parameters</span></span>

- <span data-ttu-id="5005a-811">**method** 有効な HMAC SHA512 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-811">**method** Pointer to a valid HMAC SHA512 crypto method control block.</span></span> <span data-ttu-id="5005a-812">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-812">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-813">*crypto_method_hmac_sha384*</span><span class="sxs-lookup"><span data-stu-id="5005a-813">*crypto_method_hmac_sha384*</span></span>
  - <span data-ttu-id="5005a-814">*crypto_method_hmac_sha512*</span><span class="sxs-lookup"><span data-stu-id="5005a-814">*crypto_method_hmac_sha512*</span></span>
- <span data-ttu-id="5005a-815">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-815">**key** Points to the key.</span></span> <span data-ttu-id="5005a-816">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-816">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-817">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-817">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-818">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-818">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-819">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-819">The handle is implementation-dependent, and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-820">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-820">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-821">**crypto_metadata** HMAC SHA512 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-821">**crypto_metadata** Pointer to a valid memory space for the HMAC SHA512 control block.</span></span> <span data-ttu-id="5005a-822">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-822">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-823">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-823">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-824">HMAC SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-824">For HMAC SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-825">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-825">Return Values</span></span>

- <span data-ttu-id="5005a-826">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、HMAC SHA512 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-826">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the HMAC SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-827">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-828">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-828">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_operation"></a><span data-ttu-id="5005a-829">_nx_crypto_method_hmac_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-829">_nx_crypto_method_hmac_sha512_operation</span></span>

<span data-ttu-id="5005a-830">HMAC SHA512 ハッシュ操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-830">Perform HMAC SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-831">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-831">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-832">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-832">Description</span></span>

<span data-ttu-id="5005a-833">この関数では、HMAC SHA512 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-833">This function performs HMAC SHA512 hash operation.</span></span> <span data-ttu-id="5005a-834">HMAC SHA512 制御ブロックは、_ *nx_crypto_method_hmac_sha512_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-834">The HMAC SHA512 control block must have been initialized with _ *nx_crypto_method_hmac_sha512_init()*.</span></span> <span data-ttu-id="5005a-835">実行される HMAC SHA512 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-835">The HMAC SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-836">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA512 の場合は 64 バイト、SHA384 の場合は 48 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-836">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-837">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-837">Parameters</span></span>

- <span data-ttu-id="5005a-838">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-838">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-839">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-839">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-840">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-840">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-841">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-841">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-842">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-842">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-843">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-843">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-844">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-844">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-845">**method** 有効な HMAC SHA512 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-845">**method** Pointer to the valid HMAC SHA512 crypto method.</span></span> <span data-ttu-id="5005a-846">ここで使用される暗号化メソッドは、_ *nx_crypto_method_hmac_sha512_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-846">The crypto method used here must be the same used in the _ *nx_crypto_method_hmac_sha512_init().*</span></span>
- <span data-ttu-id="5005a-847">**key** キーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-847">**key** Points to the key.</span></span> <span data-ttu-id="5005a-848">キー バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-848">There are not restrictions on key buffer.</span></span>
- <span data-ttu-id="5005a-849">**key_size_in_bits** キーのサイズ (ビット単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-849">**key_size_in_bits** Size of the key, in bits.</span></span>
- <span data-ttu-id="5005a-850">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-850">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-851">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-851">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-852">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-852">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-853">**iv_ptr** このフィールドは HMAC SHA512 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-853">**iv_ptr** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="5005a-854">**iv_size** このフィールドは HMAC SHA512 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-854">**iv_size** This field is not used for HMAC SHA512.</span></span>
- <span data-ttu-id="5005a-855">**output_buffer** 生成された HMAC SHA512 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-855">**output_buffer** Pointer to the memory area for the generated HMAC SHA512 hash.</span></span>
- <span data-ttu-id="5005a-856">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-856">**output_buffer_size** Size of the output buffer in bytes.</span></span>
- <span data-ttu-id="5005a-857">**crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* で使用される HMAC SHA512 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-857">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>
- <span data-ttu-id="5005a-858">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-858">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-859">HMAC SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512_HMAC)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-859">For HMAC SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512_HMAC)*</span></span>
- <span data-ttu-id="5005a-860">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-860">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-861">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-861">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-862">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-862">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-863">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-863">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-864">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-864">Return Values</span></span>

- <span data-ttu-id="5005a-865">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-865">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the HMAC SHA512 operation.</span></span>
- <span data-ttu-id="5005a-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-866">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-867">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-867">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な HMAC SHA512 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-868">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid HMAC SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-869">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_hmac_sha512_cleanup"></a><span data-ttu-id="5005a-870">_nx_crypto_method_hmac_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-870">_nx_crypto_method_hmac_sha512_cleanup</span></span>

<span data-ttu-id="5005a-871">HMAC SHA512 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-871">Clean up the HMAC SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-872">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-872">Prototype</span></span>

```c
UINT _nx_crypto_method_hmac_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-873">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-873">Description</span></span>

<span data-ttu-id="5005a-874">アプリケーションでは、この HMAC SHA512 セッションが不要になったと判断した後にこの関数を呼び出して、HMAC SHA512 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-874">Application calls this function to clean up the HMAC SHA512 control block after it determines this HMAC SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-875">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-875">Parameters</span></span>

- <span data-ttu-id="5005a-876">**crypto_metadata** *_nx_crypto_method_hmac_sha512_init()* で使用される HMAC SHA512 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-876">**crypto_metadata** Pointer to the HMAC SHA512 control block used in *_nx_crypto_method_hmac_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-877">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-877">Return Values</span></span>

- <span data-ttu-id="5005a-878">**NX_CRYPTO_SUCCESS** (0x00) HMAC SHA512 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-878">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the HMAC SHA512 session.</span></span>
- <span data-ttu-id="5005a-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-879">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

### <a name="example"></a><span data-ttu-id="5005a-880">例</span><span class="sxs-lookup"><span data-stu-id="5005a-880">Example</span></span> 

## <a name="_nx_crypto_method_md5_init"></a><span data-ttu-id="5005a-881">_nx_crypto_method_md5_init</span><span class="sxs-lookup"><span data-stu-id="5005a-881">_nx_crypto_method_md5_init</span></span>

<span data-ttu-id="5005a-882">MD5 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-882">Initializes the MD5 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-883">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-883">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-884">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-884">Description</span></span>

<span data-ttu-id="5005a-885">この関数では、指定されたキー文字列を使用して、MD5 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-885">This function initializes the MD5 control block with the given key string.</span></span> <span data-ttu-id="5005a-886">いったん MD5 制御ブロックが初期化されると、後続の MD5 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-886">Once the MD5 control block is initialized, subsequent MD5 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-887">アプリケーションは複数の MD5 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-887">Application may create multiple MD5 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-888">MD5 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-888">Initializing the MD5 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-889">MD5 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-889">Re-initializing the MD5 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-890">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-890">Parameters</span></span>

- <span data-ttu-id="5005a-891">**method** 有効な MD5 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-891">**method** Pointer to a valid MD5 crypto method control block.</span></span> <span data-ttu-id="5005a-892">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-892">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-893">*crypto_method_md5*</span><span class="sxs-lookup"><span data-stu-id="5005a-893">*crypto_method_md5*</span></span>
- <span data-ttu-id="5005a-894">**key** このフィールドは MD5 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-894">**key** This field is not used for MD5.</span></span>
- <span data-ttu-id="5005a-895">**key_size_in_bits** このフィールドは MD5 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-895">**key_size_in_bits** This field is not used for MD5</span></span>
- <span data-ttu-id="5005a-896">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-896">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-897">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-897">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-898">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-898">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-899">**crypto_metadata** MD5 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-899">**crypto_metadata** Pointer to a valid memory space for the MD5 control block.</span></span> <span data-ttu-id="5005a-900">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-900">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-901">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-901">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-902">MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-902">For MD5, the metadata size must be *sizeof(NX_CRYPTO_MD5)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-903">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-903">Return Values</span></span>

- <span data-ttu-id="5005a-904">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、MD5 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-904">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the MD5 control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-905">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-906">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-906">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

### <a name="example"></a><span data-ttu-id="5005a-907">例</span><span class="sxs-lookup"><span data-stu-id="5005a-907">Example</span></span>

## <a name="_nx_crypto_method_md5_operation"></a><span data-ttu-id="5005a-908">_nx_crypto_method_md5_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-908">_nx_crypto_method_md5_operation</span></span>

<span data-ttu-id="5005a-909">MD5 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-909">Perform an MD5 hash operation.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-910">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-910">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-911">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-911">Description</span></span>

<span data-ttu-id="5005a-912">この関数では、MD5 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-912">This function performs MD5 hash operation.</span></span> <span data-ttu-id="5005a-913">MD5 制御ブロックは、_ *nx_crypto_method_md5_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-913">The MD5 control block must have been initialized with _ *nx_crypto_method_md5_init()*.</span></span> <span data-ttu-id="5005a-914">実行される MD5 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-914">The MD5 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-915">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 16 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-915">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 16 bytes.</span></span>

<span data-ttu-id="5005a-916">この操作では、状態情報は保持されず、MD5 制御ブロック内のキー マテリアルは変更されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-916">This operation does not keep state information and does not alter the key material in the MD5 control block.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-917">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-917">Parameters</span></span>

- <span data-ttu-id="5005a-918">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-918">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-919">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-919">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-920">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-920">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-921">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-921">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-922">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-922">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-923">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-923">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-924">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-924">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-925">**method** 有効な MD5 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-925">**method** Pointer to the valid MD5 crypto method.</span></span> <span data-ttu-id="5005a-926">ここで使用される暗号化メソッドは、*nx_crypto_method_md5_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-926">The crypto method used here must be the same used in the _ *nx_crypto_method_md5_init().*</span></span>
- <span data-ttu-id="5005a-927">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-927">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-928">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-928">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-929">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-929">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-930">**iv_ptr** このフィールドは MD5 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-930">**iv_ptr** This field is not used for MD5.</span></span>
- <span data-ttu-id="5005a-931">**iv_size** このフィールドは MD5 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-931">**iv_size** This field is not used for MD5.</span></span>
- <span data-ttu-id="5005a-932">**output_buffer** 生成された MD5 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-932">**output_buffer** Pointer to the memory area for the generated MD5 hash.</span></span>
- <span data-ttu-id="5005a-933">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-933">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="5005a-934">MD5 の場合、バッファー サイズは 16 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-934">For MD5 the buffer size must be 16 bytes.</span></span>
- <span data-ttu-id="5005a-935">**crypto_metadata** *_nx_crypto_method_md5_init()* で使用される MD5 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-935">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>
- <span data-ttu-id="5005a-936">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-936">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-937">MD5 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_MD5)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-937">For MD5, the metadata size must *sizeof(NX_CRYPTO_MD5)*</span></span>
- <span data-ttu-id="5005a-938">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-938">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-939">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-939">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-940">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-940">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-941">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-941">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-942">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-942">Return Values</span></span>

- <span data-ttu-id="5005a-943">**NX_CRYPTO_SUCCESS** (0x00) MD5 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-943">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the MD5 operation.</span></span>
- <span data-ttu-id="5005a-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-944">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-945">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-945">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な MD5 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-946">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid MD5 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-947">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_md5_cleanup"></a><span data-ttu-id="5005a-948">_nx_crypto_method_md5_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-948">_nx_crypto_method_md5_cleanup</span></span>

<span data-ttu-id="5005a-949">MD5 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-949">Clean up the MD5 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-950">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-950">Prototype</span></span>

```c
UINT _nx_crypto_method_md5_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-951">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-951">Description</span></span>

<span data-ttu-id="5005a-952">アプリケーションでは、この MD5 セッションが不要になったと判断した後にこの関数を呼び出して、MD5 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-952">Application calls this function to clean up the MD5 control block after it determines this MD5 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-953">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-953">Parameters</span></span>

- <span data-ttu-id="5005a-954">**crypto_metadata** *_nx_crypto_method_md5_init()* で使用される MD5 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-954">**crypto_metadata** Pointer to the MD5 control block used in *_nx_crypto_method_md5_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-955">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-955">Return Values</span></span>

- <span data-ttu-id="5005a-956">**NX_CRYPTO_SUCCESS** (0x00) MD5 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-956">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the MD5 session.</span></span>
- <span data-ttu-id="5005a-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-957">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha1_init"></a><span data-ttu-id="5005a-958">_nx_crypto_method_sha1_init</span><span class="sxs-lookup"><span data-stu-id="5005a-958">_nx_crypto_method_sha1_init</span></span>

<span data-ttu-id="5005a-959">SHA1 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-959">Initializes the SHA1 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-960">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-960">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-961">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-961">Description</span></span>

<span data-ttu-id="5005a-962">この関数では、指定されたキー文字列を使用して、SHA1 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-962">This function initializes the SHA1 control block with the given key string.</span></span> <span data-ttu-id="5005a-963">いったん SHA1 制御ブロックが初期化されると、後続の SHA1 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-963">Once the SHA1 control block is initialized, subsequent SHA1 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-964">アプリケーションは複数の SHA1 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-964">Application may create multiple SHA1 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-965">SHA1 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-965">Initializing the SHA1 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-966">SHA1 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-966">Re-initializing the SHA1 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-967">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-967">Parameters</span></span>

- <span data-ttu-id="5005a-968">**method** 有効な SHA1 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-968">**method** Pointer to a valid SHA1 crypto method control block.</span></span> <span data-ttu-id="5005a-969">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-969">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-970">*crypto_method_sha1*</span><span class="sxs-lookup"><span data-stu-id="5005a-970">*crypto_method_sha1*</span></span>
- <span data-ttu-id="5005a-971">**key** このフィールドは SHA1 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-971">**key** This field is not used for SHA1.</span></span>
- <span data-ttu-id="5005a-972">**key_size_in_bits** このフィールドは SHA1 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-972">**key_size_in_bits** This field is not used for SHA1</span></span>
- <span data-ttu-id="5005a-973">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-973">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-974">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-974">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-975">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-975">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-976">**crypto_metadata** SHA1 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-976">**crypto_metadata** Pointer to a valid memory space for the SHA1 control block.</span></span> <span data-ttu-id="5005a-977">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-977">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-978">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-978">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-979">SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-979">For SHA1, the metadata size must be *sizeof(NX_CRYPTO_SHA1)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-980">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-980">Return Values</span></span>

- <span data-ttu-id="5005a-981">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、SHA1 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-981">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA1control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-982">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-983">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-983">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha1_operation"></a><span data-ttu-id="5005a-984">_nx_crypto_method_sha1_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-984">_nx_crypto_method_sha1_operation</span></span>

<span data-ttu-id="5005a-985">SHA1 ハッシュ操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-985">Perform SHA1 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-986">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-986">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-987">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-987">Description</span></span>

<span data-ttu-id="5005a-988">この関数では、SHA1 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-988">This function performs SHA1 hash operation.</span></span> <span data-ttu-id="5005a-989">SHA1 制御ブロックは、_ *nx_crypto_method_sha1_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-989">The SHA1 control block must have been initialized with _ *nx_crypto_method_sha1_init()*.</span></span> <span data-ttu-id="5005a-990">実行される SHA1 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-990">The SHA1 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-991">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは 20 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-991">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 20 bytes.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-992">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-992">Parameters</span></span>

- <span data-ttu-id="5005a-993">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-993">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-994">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-994">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-995">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-995">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-996">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-996">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-997">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-997">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-998">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-998">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-999">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-999">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-1000">**method** 有効な SHA1 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1000">**method** Pointer to the valid SHA1 crypto method.</span></span> <span data-ttu-id="5005a-1001">ここで使用される暗号化メソッドは、*nx_crypto_method_sha1_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1001">The crypto method used here must be the same used in the *nx_crypto_method_sha1_init().*</span></span>
- <span data-ttu-id="5005a-1002">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1002">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-1003">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1003">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-1004">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1004">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-1005">**iv_ptr** このフィールドは SHA1 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1005">**iv_ptr** This field is not used for SHA1.</span></span>
- <span data-ttu-id="5005a-1006">**iv_size** このフィールドは SHA1 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1006">**iv_size** This field is not used for SHA1.</span></span>
- <span data-ttu-id="5005a-1007">**output_buffer** 生成された SHA1 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1007">**output_buffer** Pointer to the memory area for the generated SHA1 hash.</span></span>
- <span data-ttu-id="5005a-1008">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1008">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="5005a-1009">SHA1 の場合、バッファー サイズは 20 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1009">For SHA1 the buffer size must be 20 bytes.</span></span>
- <span data-ttu-id="5005a-1010">**crypto_metadata** *_nx_crypto_method_sha1_init()* で使用される SHA1 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1010">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>
- <span data-ttu-id="5005a-1011">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1011">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-1012">SHA1 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA1)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-1012">For SHA1, the metadata size must *sizeof(NX_CRYPTO_SHA1)*</span></span>
- <span data-ttu-id="5005a-1013">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1013">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1014">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1014">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-1015">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1015">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1016">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1016">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1017">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1017">Return Values</span></span>

- <span data-ttu-id="5005a-1018">**NX_CRYPTO_SUCCESS** (0x00) SHA1 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1018">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA1 operation.</span></span>
- <span data-ttu-id="5005a-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1019">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-1020">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-1020">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な SHA1 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-1021">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA1 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-1022">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

### <a name="example"></a><span data-ttu-id="5005a-1023">例</span><span class="sxs-lookup"><span data-stu-id="5005a-1023">Example</span></span>

## <a name="_nx_crypto_method_sha1_cleanup"></a><span data-ttu-id="5005a-1024">_nx_crypto_method_sha1_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-1024">_nx_crypto_method_sha1_cleanup</span></span>

<span data-ttu-id="5005a-1025">SHA1 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-1025">Clean up the SHA1 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1026">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1026">Prototype</span></span>

```c
UINT _nx_crypto_method_sha1_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-1027">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1027">Description</span></span>

<span data-ttu-id="5005a-1028">アプリケーションでは、この SHA1 セッションが不要になったと判断した後にこの関数を呼び出して、SHA1 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-1028">Application calls this function to clean up the SHA1 control block after it determines this SHA1 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1029">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1029">Parameters</span></span>

- <span data-ttu-id="5005a-1030">**crypto_metadata** *_nx_crypto_method_sha1_init()* で使用される SHA1 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1030">**crypto_metadata** Pointer to the SHA1 control block used in *_nx_crypto_method_sha1_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1031">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1031">Return Values</span></span>

- <span data-ttu-id="5005a-1032">**NX_CRYPTO_SUCCESS** (0x00) SHA1 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1032">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA1 session.</span></span>
- <span data-ttu-id="5005a-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1033">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha256_init"></a><span data-ttu-id="5005a-1034">_nx_crypto_method_sha256_init</span><span class="sxs-lookup"><span data-stu-id="5005a-1034">_nx_crypto_method_sha256_init</span></span>

<span data-ttu-id="5005a-1035">SHA256 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-1035">Initializes the SHA256 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1036">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1036">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size)
```

### <a name="description"></a><span data-ttu-id="5005a-1037">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1037">Description</span></span>

<span data-ttu-id="5005a-1038">この関数では、指定されたキー文字列を使用して、SHA256 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1038">This function initializes the SHA256 control block with the given key string.</span></span> <span data-ttu-id="5005a-1039">いったん SHA256 制御ブロックが初期化されると、後続の SHA256 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-1039">Once the SHA256 control block is initialized, subsequent SHA256 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-1040">アプリケーションは複数の SHA256 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1040">Application may create multiple SHA256 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-1041">SHA256 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1041">Initializing the SHA256 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-1042">SHA256 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1042">Re-initializing the SHA256 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1043">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1043">Parameters</span></span>

- <span data-ttu-id="5005a-1044">**method** 有効な SHA256 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1044">**method** Pointer to a valid SHA256 crypto method control block.</span></span> <span data-ttu-id="5005a-1045">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1045">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-1046">*crypto_method_sha256*</span><span class="sxs-lookup"><span data-stu-id="5005a-1046">*crypto_method_sha256*</span></span>
  - <span data-ttu-id="5005a-1047">*crypto_method_sha224*</span><span class="sxs-lookup"><span data-stu-id="5005a-1047">*crypto_method_sha224*</span></span>
- <span data-ttu-id="5005a-1048">**key** このフィールドは SHA256 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1048">**key** This field is not used for SHA256.</span></span>
- <span data-ttu-id="5005a-1049">**key_size_in_bits** このフィールドは SHA256 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1049">**key_size_in_bits** This field is not used for SHA256</span></span>
- <span data-ttu-id="5005a-1050">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1050">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-1051">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1051">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-1052">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1052">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-1053">**crypto_metadata** SHA256 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1053">**crypto_metadata** Pointer to a valid memory space for the SHA256 control block.</span></span> <span data-ttu-id="5005a-1054">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1054">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-1055">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1055">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-1056">SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA256)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-1056">For SHA256, the metadata size must be *sizeof(NX_CRYPTO_SHA256)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1057">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1057">Return Values</span></span>

- <span data-ttu-id="5005a-1058">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、SHA256 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1058">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA256 control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1059">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-1060">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1060">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha256_operation"></a><span data-ttu-id="5005a-1061">_nx_crypto_method_sha256_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-1061">_nx_crypto_method_sha256_operation</span></span>

<span data-ttu-id="5005a-1062">SHA256 ハッシュ操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-1062">Perform SHA256 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1063">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1063">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT
    status));
```

### <a name="description"></a><span data-ttu-id="5005a-1064">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1064">Description</span></span>

<span data-ttu-id="5005a-1065">この関数では、SHA256 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1065">This function performs SHA256 hash operation.</span></span> <span data-ttu-id="5005a-1066">SHA256 制御ブロックは、_ ***nx_crypto_method_sha256_init()*** を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1066">The SHA256 control block must have been initialized with _ ***nx_crypto_method_sha256_init()***.</span></span> <span data-ttu-id="5005a-1067">実行される SHA256 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1067">The SHA256 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-1068">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA256 の場合は 32 バイト、SHA224 の場合は 28 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1068">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 32 bytes for SHA256, or 28 bytes for SHA224.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1069">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1069">Parameters</span></span>

- <span data-ttu-id="5005a-1070">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-1070">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-1071">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-1071">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-1072">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-1072">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-1073">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-1073">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-1074">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-1074">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-1075">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1075">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1076">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1076">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-1077">**method** 有効な SHA256 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1077">**method** Pointer to the valid SHA256 crypto method.</span></span> <span data-ttu-id="5005a-1078">ここで使用される暗号化メソッドは、_ *nx_crypto_method_sha256_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1078">The crypto method used here must be the same used in the _ *nx_crypto_method_sha256_init().*</span></span>
- <span data-ttu-id="5005a-1079">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1079">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-1080">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1080">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-1081">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1081">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-1082">**iv_ptr** このフィールドは SHA256 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1082">**iv_ptr** This field is not used for SHA256.</span></span>
- <span data-ttu-id="5005a-1083">**iv_size** このフィールドは SHA256 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1083">**iv_size** This field is not used for SHA256.</span></span>
- <span data-ttu-id="5005a-1084">**output_buffer** 生成された SHA256 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1084">**output_buffer** Pointer to the memory area for the generated SHA256 hash.</span></span>
- <span data-ttu-id="5005a-1085">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1085">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="5005a-1086">SHA256 の場合、バッファー サイズは 32 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1086">For SHA256 the buffer size must be 32 bytes.</span></span> <span data-ttu-id="5005a-1087">SHA224 の場合、バッファー サイズは 28 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1087">For SHA224 the buffer size must be 28 bytes.</span></span>
- <span data-ttu-id="5005a-1088">**crypto_metadata** *_nx_crypto_method_sha2_init()* で使用される SHA2 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1088">**crypto_metadata** Pointer to the SHA2 control block used in *_nx_crypto_method_sha2_init()*.</span></span>
- <span data-ttu-id="5005a-1089">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1089">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-1090">SHA256 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA256)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-1090">For SHA256, the metadata size must *sizeof(NX_CRYPTO_SHA256)*</span></span>
- <span data-ttu-id="5005a-1091">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1091">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1092">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1092">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-1093">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1093">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1094">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1094">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1095">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1095">Return Values</span></span>

- <span data-ttu-id="5005a-1096">**NX_CRYPTO_SUCCESS** (0x00) SHA256 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1096">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA256 operation.</span></span>
- <span data-ttu-id="5005a-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1097">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-1098">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-1098">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な SHA256 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-1099">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA256 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-1100">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha256_cleanup"></a><span data-ttu-id="5005a-1101">_nx_crypto_method_sha256_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-1101">_nx_crypto_method_sha256_cleanup</span></span>

<span data-ttu-id="5005a-1102">SHA256 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-1102">Clean up the SHA256 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1103">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1103">Prototype</span></span>

```c
UINT _nx_crypto_method_sha256_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-1104">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1104">Description</span></span>

<span data-ttu-id="5005a-1105">アプリケーションでは、この SHA256 セッションが不要になったと判断した後にこの関数を呼び出して、SHA256 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-1105">Application calls this function to clean up the SHA256 control block after it determines this SHA256 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1106">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1106">Parameters</span></span>

- <span data-ttu-id="5005a-1107">**crypto_metadata** *_nx_crypto_method_sha256_init()* で使用される SHA256 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1107">**crypto_metadata** Pointer to the SHA256 control block used in *_nx_crypto_method_sha256_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1108">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1108">Return Values</span></span>

- <span data-ttu-id="5005a-1109">**NX_CRYPTO_SUCCESS** (0x00) SHA256 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1109">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA256 session.</span></span>
- <span data-ttu-id="5005a-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1110">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>

## <a name="_nx_crypto_method_sha512_init"></a><span data-ttu-id="5005a-1111">_nx_crypto_method_sha512_init</span><span class="sxs-lookup"><span data-stu-id="5005a-1111">_nx_crypto_method_sha512_init</span></span>

<span data-ttu-id="5005a-1112">SHA512 暗号化制御ブロックを初期化します</span><span class="sxs-lookup"><span data-stu-id="5005a-1112">Initializes the SHA512 crypto control block</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1113">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1113">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_init(
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    VOID **handle,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size);
```

### <a name="description"></a><span data-ttu-id="5005a-1114">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1114">Description</span></span>

<span data-ttu-id="5005a-1115">この関数では、指定されたキー文字列を使用して、SHA512 制御ブロックを初期化します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1115">This function initializes the SHA512 control block with the given key string.</span></span> <span data-ttu-id="5005a-1116">いったん SHA512 制御ブロックが初期化されると、後続の SHA512 操作では、同じ制御ブロックが使用されることになっています。</span><span class="sxs-lookup"><span data-stu-id="5005a-1116">Once the SHA512 control block is initialized, subsequent SHA512 operation shall be using the same control block.</span></span>

<span data-ttu-id="5005a-1117">アプリケーションは複数の SHA512 制御ブロックを作成することがあり、それぞれがセッションを表します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1117">Application may create multiple SHA512 control blocks, each represents a session.</span></span> <span data-ttu-id="5005a-1118">SHA512 制御ブロックを初期化すると、新しいハッシュ評価セッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1118">Initializing the SHA512 control block starts a new hash computation session.</span></span> <span data-ttu-id="5005a-1119">SHA512 制御ブロックを再初期化すると、現在のセッションは破棄されて、新しいセッションが開始されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1119">Re-initializing the SHA512 control block abandons the current session and stars a new one.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1120">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1120">Parameters</span></span>

- <span data-ttu-id="5005a-1121">**method** 有効な SHA512 暗号化メソッド制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1121">**method** Pointer to a valid SHA512 crypto method control block.</span></span> <span data-ttu-id="5005a-1122">以下の定義済み DRBG 暗号化メソッドを使用できます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1122">The following pre-defined crypto methods are available:</span></span>
  - <span data-ttu-id="5005a-1123">*crypto_method_sha512*</span><span class="sxs-lookup"><span data-stu-id="5005a-1123">*crypto_method_sha512*</span></span>
  - <span data-ttu-id="5005a-1124">*crypto_method_sha384*</span><span class="sxs-lookup"><span data-stu-id="5005a-1124">*crypto_method_sha384*</span></span>
- <span data-ttu-id="5005a-1125">**key** このフィールドは SHA512 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1125">**key** This field is not used for SHA512.</span></span>
- <span data-ttu-id="5005a-1126">**key_size_in_bits** このフィールドは SHA512 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1126">**key_size_in_bits** This field is not used for SHA512</span></span>
- <span data-ttu-id="5005a-1127">**handle** このサービスでは、呼び出し元へのハンドルが返されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1127">**handle** This service returns a handle to the caller.</span></span> <span data-ttu-id="5005a-1128">ハンドルは実装に依存しており、この実装では使用されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1128">The handle is implementation-dependent and is not being used in this implementation.</span></span> <span data-ttu-id="5005a-1129">アプリケーションでは、このハンドルには NULL を渡す必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1129">Application shall pass NULL for the handle.</span></span>
- <span data-ttu-id="5005a-1130">**crypto_metadata** SHA512 制御ブロック用の有効なメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1130">**crypto_metadata** Pointer to a valid memory space for the SHA512 control block.</span></span> <span data-ttu-id="5005a-1131">メモリ領域の開始アドレスは、4 バイトで整列している必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1131">The starting address of the memory space must be 4-byte aligned.</span></span>
- <span data-ttu-id="5005a-1132">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1132">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-1133">SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-1133">For SHA512, the metadata size must be *sizeof(NX_CRYPTO_SHA512)*</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1134">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1134">Return Values</span></span>

- <span data-ttu-id="5005a-1135">**NX_CRYPTO_SUCCESS** (0x00) そのキーとキー サイズで、SHA512 制御ブロックが正常に初期化されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1135">**NX_CRYPTO_SUCCESS** (0x00) Successful initialization of the SHA512 control block with the key and key size.</span></span>
- <span data-ttu-id="5005a-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1136">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-1137">**NX_PTR_ERROR (0x07)** キーへのポインターが無効であるか、crypto_metadata または crypto_metadata_size が無効であるか、crypto_metadata が 4 バイトで整列されていません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1137">**NX_PTR_ERROR** (0x07) Invalid pointer to the key, or invalid crypto_metadata or crypto_metadata_size, or crypto_metadata is not 4-byte aligned.</span></span>

## <a name="_nx_crypto_method_sha512_operation"></a><span data-ttu-id="5005a-1138">_nx_crypto_method_sha512_operation</span><span class="sxs-lookup"><span data-stu-id="5005a-1138">_nx_crypto_method_sha512_operation</span></span>

<span data-ttu-id="5005a-1139">SHA512 ハッシュ操作を実行します</span><span class="sxs-lookup"><span data-stu-id="5005a-1139">Perform SHA512 hash operation</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1140">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1140">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_operation(UINT op,
    VOID *handle,
    struct NX_CRYPTO_METHOD_STRUCT *method,
    UCHAR *key,
    NX_CRYPTO_KEY_SIZE key_size_in_bits,
    UCHAR *input,
    ULONG input_length_in_byte,
    UCHAR *iv_ptr,
    UCHAR *output,
    ULONG output_length_in_byte,
    VOID *crypto_metadata,
    ULONG crypto_metadata_size,
    VOID *packet_ptr,
    VOID (*nx_crypto_hw_process_callback)(VOID *packet_ptr, UINT status));
```

### <a name="description"></a><span data-ttu-id="5005a-1141">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1141">Description</span></span>

<span data-ttu-id="5005a-1142">この関数では、SHA512 ハッシュ操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1142">This function performs SHA512 hash operation.</span></span> <span data-ttu-id="5005a-1143">SHA512 制御ブロックは、_ *nx_crypto_method_sha512_init()* を使用して初期化されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1143">The SHA512 control block must have been initialized with _ *nx_crypto_method_sha512_init()*.</span></span> <span data-ttu-id="5005a-1144">実行される SHA512 アルゴリズムは、*method* 制御ブロックで指定されたアルゴリズムに基づきます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1144">The SHA512 algorithm to be performed is based on the algorithm specified in the *method* control block.</span></span>

<span data-ttu-id="5005a-1145">最終的な *NX_CRYPTO_HASH_CALCULATE* 操作では、出力バッファー サイズは、SHA512 の場合は 64 バイト、SHA384 の場合は 48 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1145">For the final *NX_CRYPTO_HASH_CALCULATE* operation, the output buffer size must be 64 bytes for SHA512, or 48 bytes for SHA384.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1146">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1146">Parameters</span></span>

- <span data-ttu-id="5005a-1147">**op** 実行する操作の種類。</span><span class="sxs-lookup"><span data-stu-id="5005a-1147">**op** Type of operation to perform.</span></span> <span data-ttu-id="5005a-1148">有効な操作は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="5005a-1148">Valid operation is:</span></span>
  - <span data-ttu-id="5005a-1149">*NX_CRYPTO_HASH_INITIALIZE*</span><span class="sxs-lookup"><span data-stu-id="5005a-1149">*NX_CRYPTO_HASH_INITIALIZE*</span></span>
  - <span data-ttu-id="5005a-1150">*NX_CRYPTO_HASH_UPDATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-1150">*NX_CRYPTO_HASH_UPDATE*</span></span>
  - <span data-ttu-id="5005a-1151">*NX_CRYPTO_HASH_CALCULATE*</span><span class="sxs-lookup"><span data-stu-id="5005a-1151">*NX_CRYPTO_HASH_CALCULATE*</span></span>
- <span data-ttu-id="5005a-1152">**handle** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1152">**handle** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1153">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1153">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-1154">**method** 有効な SHA512 暗号化メソッドへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1154">**method** Pointer to the valid SHA512 crypto method.</span></span> <span data-ttu-id="5005a-1155">ここで使用される暗号化メソッドは、_ *nx_crypto_method_sha512_init()* で使用されるものと同じである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1155">The crypto method used here must be the same used in the _ *nx_crypto_method_sha512_init().*</span></span>
- <span data-ttu-id="5005a-1156">**input_data** 入力テキスト データを格納しているバッファーを指し示します。</span><span class="sxs-lookup"><span data-stu-id="5005a-1156">**input_data** Points to a buffer containing input text data.</span></span> <span data-ttu-id="5005a-1157">入力バッファーに関する制限はありません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1157">There are not restrictions on input buffer.</span></span>
- <span data-ttu-id="5005a-1158">**input_data_size** 入力データのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1158">**input_data_size** Size of the input data, in bytes.</span></span>
- <span data-ttu-id="5005a-1159">**iv_ptr** このフィールドは SHA512 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1159">**iv_ptr** This field is not used for SHA512.</span></span>
- <span data-ttu-id="5005a-1160">**iv_size** このフィールドは SHA512 では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1160">**iv_size** This field is not used for SHA512.</span></span>
- <span data-ttu-id="5005a-1161">**output_buffer** 生成された SHA512 ハッシュのメモリ領域へのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1161">**output_buffer** Pointer to the memory area for the generated SHA512 hash.</span></span>
- <span data-ttu-id="5005a-1162">**output_buffer_size** 出力バッファーのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1162">**output_buffer_size** Size of the output buffer in bytes.</span></span> <span data-ttu-id="5005a-1163">SHA512 の場合、バッファー サイズは 64 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1163">For SHA512 the buffer size must be 64 bytes.</span></span> <span data-ttu-id="5005a-1164">SHA384 の場合、バッファー サイズは 48 バイトである必要があります。</span><span class="sxs-lookup"><span data-stu-id="5005a-1164">For SHA384 the buffer size must be 48 bytes.</span></span>
- <span data-ttu-id="5005a-1165">**crypto_metadata** *_nx_crypto_method_sha512_init()* で使用される SHA512 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1165">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>
- <span data-ttu-id="5005a-1166">**crypto_metadata_size** crypto_metadata 領域のサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="5005a-1166">**crypto_metadata_size** Size, in bytes, of the crypto_metadata area.</span></span> <span data-ttu-id="5005a-1167">SHA512 の場合、メタデータ サイズは *sizeof (NX_CRYPTO_SHA512)* である必要があります</span><span class="sxs-lookup"><span data-stu-id="5005a-1167">For SHA512, the metadata size must *sizeof(NX_CRYPTO_SHA512)*</span></span>
- <span data-ttu-id="5005a-1168">**packet_ptr** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1168">**packet_ptr** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1169">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1169">Any values passed in are silently ignored.</span></span>
- <span data-ttu-id="5005a-1170">**nx_crypto_hw_process_callback** このフィールドは、NetX Crypto ライブラリのソフトウェア実装では使用されません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1170">**nx_crypto_hw_process_callback** This field is not used in the software implementation of NetX Crypto library.</span></span> <span data-ttu-id="5005a-1171">渡された値はすべて暗黙的に無視されます。</span><span class="sxs-lookup"><span data-stu-id="5005a-1171">Any values passed in are silently ignored.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1172">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1172">Return Values</span></span>

- <span data-ttu-id="5005a-1173">**NX_CRYPTO_SUCCESS** (0x00) SHA512 操作が正常に実行されました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1173">**NX_CRYPTO_SUCCESS** (0x00) Successfully executed the SHA512 operation.</span></span>
- <span data-ttu-id="5005a-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1174">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>
- <span data-ttu-id="5005a-1175">**NX_PTR_ERROR** (0x07) 無効な入力ポインターまたは無効な長さです。</span><span class="sxs-lookup"><span data-stu-id="5005a-1175">**NX_PTR_ERROR** (0x07) Invalid input pointer or invalid length.</span></span>
- <span data-ttu-id="5005a-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) 無効な SHA512 アルゴリズムが指定されています。</span><span class="sxs-lookup"><span data-stu-id="5005a-1176">**NX_CRYPTO_INVALID_ALGORITHM** (0x20004) Invalid SHA512 algorithm being specified.</span></span>
- <span data-ttu-id="5005a-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) 出力バッファー サイズが無効です。</span><span class="sxs-lookup"><span data-stu-id="5005a-1177">**NX_CRYPTO_INVALID_BUFFER_SIZE** (0x20005) Invalid output buffer size.</span></span>

## <a name="_nx_crypto_method_sha512_cleanup"></a><span data-ttu-id="5005a-1178">_nx_crypto_method_sha512_cleanup</span><span class="sxs-lookup"><span data-stu-id="5005a-1178">_nx_crypto_method_sha512_cleanup</span></span>

<span data-ttu-id="5005a-1179">SHA512 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-1179">Clean up the SHA512 control block.</span></span>

### <a name="prototype"></a><span data-ttu-id="5005a-1180">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="5005a-1180">Prototype</span></span>

```c
UINT _nx_crypto_method_sha512_cleanup(VOID* crypto_metadata);
```

### <a name="description"></a><span data-ttu-id="5005a-1181">説明</span><span class="sxs-lookup"><span data-stu-id="5005a-1181">Description</span></span>

<span data-ttu-id="5005a-1182">アプリケーションでは、この SHA512 セッションが不要になったと判断した後にこの関数を呼び出して、SHA512 制御ブロックをクリーンアップします。</span><span class="sxs-lookup"><span data-stu-id="5005a-1182">Application calls this function to clean up the SHA512 control block after it determines this SHA512 session is no longer needed.</span></span>

### <a name="parameters"></a><span data-ttu-id="5005a-1183">パラメーター</span><span class="sxs-lookup"><span data-stu-id="5005a-1183">Parameters</span></span>

- <span data-ttu-id="5005a-1184">**crypto_metadata** *_nx_crypto_method_sha512_init()* で使用される SHA512 制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="5005a-1184">**crypto_metadata** Pointer to the SHA512 control block used in *_nx_crypto_method_sha512_init()*.</span></span>

### <a name="return-values"></a><span data-ttu-id="5005a-1185">戻り値</span><span class="sxs-lookup"><span data-stu-id="5005a-1185">Return Values</span></span>

- <span data-ttu-id="5005a-1186">**NX_CRYPTO_SUCCESS** (0x00) SHA512 セッションが正常にクリーンアップされました。</span><span class="sxs-lookup"><span data-stu-id="5005a-1186">**NX_CRYPTO_SUCCESS** (0x00) Successfully cleaned up the SHA512 session.</span></span>
- <span data-ttu-id="5005a-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) 暗号化ライブラリが無効な状態になっていて使用できません。</span><span class="sxs-lookup"><span data-stu-id="5005a-1187">**NX_CRYPTO_INVALID_LIBRARY** (0x20001) The crypto library is in an invalid state and cannot be used.</span></span>