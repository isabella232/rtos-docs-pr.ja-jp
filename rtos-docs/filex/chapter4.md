---
title: 第 4 章 - Azure RTOS FileX サービスの説明
description: この章は、すべての Azure RTOS FileX サービスの説明をアルファベット順にまとめたものです。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f70b8890be6b12f917ac1724a29559afab33b88d
ms.sourcegitcommit: 0520b2afb6b7f8ae1ea48581e160459fc9292ca7
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2021
ms.locfileid: "108297498"
---
# <a name="chapter-4--description-of-azure-rtos-filex-services"></a><span data-ttu-id="aa949-103">第 4 章 - Azure RTOS FileX サービスの説明</span><span class="sxs-lookup"><span data-stu-id="aa949-103">Chapter 4- Description of Azure RTOS FileX services</span></span>

<span data-ttu-id="aa949-104">この章は、すべての Azure RTOS FileX サービスの説明をアルファベット順にまとめたものです。</span><span class="sxs-lookup"><span data-stu-id="aa949-104">This chapter contains a description of all Azure RTOS FileX services in alphabetic order.</span></span> <span data-ttu-id="aa949-105">サービス名は、類似するすべてのサービスがグループ化されるよう命名されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-105">Service names are designed so all similar services are grouped together.</span></span>

## <a name="fx_directory_attributes_read"></a><span data-ttu-id="aa949-106">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-106">fx_directory_attributes_read</span></span>

<span data-ttu-id="aa949-107">ディレクトリ属性を読み取ります</span><span class="sxs-lookup"><span data-stu-id="aa949-107">Reads directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-108">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-108">Prototype</span></span>

```c
UINT fx_directory_attributes_read ( 
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes_ptr);
```

### <a name="description"></a><span data-ttu-id="aa949-109">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-109">Description</span></span>

<span data-ttu-id="aa949-110">このサービスは、指定されたメディアからディレクトリの属性を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="aa949-110">This service reads the directory's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-111">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-111">Input Parameters</span></span>

- <span data-ttu-id="aa949-112">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-112">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-113">**directory_name**: 要求されたディレクトリの名前へのポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-113">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="aa949-114">**attributes** _ptr: 配置されるディレクトリの属性の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-114">**attributes** _ptr: Pointer to the destination for the directory's attributes to be placed.</span></span> <span data-ttu-id="aa949-115">ディレクトリ属性は、次の設定が可能なビットマップ形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-115">The directory attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="aa949-116">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-116">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="aa949-117">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-117">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="aa949-118">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-118">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="aa949-119">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="aa949-119">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="aa949-120">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="aa949-120">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="aa949-121">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="aa949-121">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-122">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-122">Return Values</span></span>

- <span data-ttu-id="aa949-123">**FX_SUCCESS** (0x00) ディレクトリ属性の読み取りに成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-123">**FX_SUCCESS** (0x00) Successful directory attributes read</span></span>
- <span data-ttu-id="aa949-124">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-124">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-125">**FX _NOT FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-125">**FX _NOT FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="aa949-126">**FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-126">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="aa949-127">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-127">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-128">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-128">**FX_FILE_CORRUPT** 0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-129">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-129">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-130">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-130">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-131">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-131">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-132">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-132">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-133">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-133">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="aa949-134">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-134">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-135">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-135">Allowed From</span></span>

<span data-ttu-id="aa949-136">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-136">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-137">例</span><span class="sxs-lookup"><span data-stu-id="aa949-137">Example</span></span>

```c
FX_MEDIA     my_media;
UINT     status;
/* Retrieve the attributes of "mydir" from the specified media.*/
status = fx_directory_attributes_read(&my_media, "mydir", &attributes);
/* If status equals FX_SUCCESS, "attributes" contains the directory attributes of "mydir". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-138">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-138">See Also</span></span>

- <span data-ttu-id="aa949-139">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-139">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-140">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-140">fx_directory_create</span></span>
- <span data-ttu-id="aa949-141">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-141">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-142">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-142">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-143">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-143">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-144">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-144">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-145">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-145">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-146">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-146">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-147">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-147">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-148">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-148">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-149">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-149">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-150">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-150">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-151">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-151">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-152">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-152">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-153">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-153">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-154">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-154">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-155">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-155">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-156">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-156">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-157">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-157">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-158">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-158">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_attributes_set"></a><span data-ttu-id="aa949-159">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-159">fx_directory_attributes_set</span></span>

<span data-ttu-id="aa949-160">ディレクトリ属性を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-160">Sets directory attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-161">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-161">Prototype</span></span>

```c
UINT fx_directory_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes);
```

### <a name="description"></a><span data-ttu-id="aa949-162">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-162">Description</span></span>

<span data-ttu-id="aa949-163">このサービスは、ディレクトリの属性を、呼び出し元によって指定された属性に設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-163">This service sets the directory's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-164">*このアプリケーションでは、このサービスを使用してディレクトリの属性のサブセットを変更することのみが許可されています。追加の属性を設定しようとすると、エラーが発生します。*</span><span class="sxs-lookup"><span data-stu-id="aa949-164">*This application is only allowed to modify a subset of the directory's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-165">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-165">Input Parameters</span></span>

- <span data-ttu-id="aa949-166">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-166">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-167">**directory_name**: 要求されたディレクトリの名前へのポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-167">**directory_name**: Pointer to the name of the requested directory (directory path is optional).</span></span>
- <span data-ttu-id="aa949-168">**attributes**: このディレクトリへの新しい属性。</span><span class="sxs-lookup"><span data-stu-id="aa949-168">**attributes**: The new attributes to this directory.</span></span> <span data-ttu-id="aa949-169">有効なディレクトリ属性は次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-169">The valid directory attributes are defined as follows:</span></span>
  - <span data-ttu-id="aa949-170">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-170">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="aa949-171">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-171">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="aa949-172">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-172">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="aa949-173">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="aa949-173">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-174">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-174">Return Values</span></span>

- <span data-ttu-id="aa949-175">**FX_SUCCESS** (0x00) ディレクトリ属性の設定に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-175">**FX_SUCCESS** (0x00) Successful directory attribute set</span></span>
- <span data-ttu-id="aa949-176">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-176">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-177">**FX_NOT_FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-177">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="aa949-178">**FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-178">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="aa949-179">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-179">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-180">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています</span><span class="sxs-lookup"><span data-stu-id="aa949-180">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="aa949-181">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-181">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-182">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-182">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-183">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-183">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-184">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-184">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-185">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-185">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-186">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません</span><span class="sxs-lookup"><span data-stu-id="aa949-186">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="aa949-187">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-187">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="aa949-188">**FX_INVALID_ATTR** (0x19) 無効な属性が選択されました。</span><span class="sxs-lookup"><span data-stu-id="aa949-188">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="aa949-189">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-190">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-190">Allowed From</span></span>

<span data-ttu-id="aa949-191">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-192">例</span><span class="sxs-lookup"><span data-stu-id="aa949-192">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
status = fx_directory_attributes_set(&my_media, "mydir", FX_READ_ONLY);
/*Set the attributes of "mydir" to read-only. */
/* If status equals FX_SUCCESS, the directory "mydir" is read-only. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-193">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-193">See Also</span></span>

- <span data-ttu-id="aa949-194">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-194">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-195">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-195">fx_directory_create</span></span>
- <span data-ttu-id="aa949-196">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-196">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-197">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-197">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-198">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-198">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-199">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-199">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-200">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-200">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-201">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-201">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-202">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-202">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-203">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-203">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-204">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-204">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-205">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-205">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-206">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-206">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-207">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-207">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-208">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-208">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-209">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-209">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-210">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-210">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-211">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-211">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-212">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-212">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-213">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-213">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_create"></a><span data-ttu-id="aa949-214">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-214">fx_directory_create</span></span>

<span data-ttu-id="aa949-215">サブディレクトリを作成します</span><span class="sxs-lookup"><span data-stu-id="aa949-215">Creates subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-216">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-216">Prototype</span></span>

```c
UINT fx_directory_create(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```
### <a name="description"></a><span data-ttu-id="aa949-217">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-217">Description</span></span>

<span data-ttu-id="aa949-218">このサービスは、現在のデフォルト ディレクトリ、またはディレクトリ名に指定されたパスにサブディレクトリを作成します。</span><span class="sxs-lookup"><span data-stu-id="aa949-218">This service creates a subdirectory in the current default directory or in the path supplied in the directory name.</span></span> <span data-ttu-id="aa949-219">ルート ディレクトリとは異なり、サブディレクトリには、保持できるファイルの数に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-219">Unlike the root directory, subdirectories do not have a limit on the number of files they can hold.</span></span> <span data-ttu-id="aa949-220">ルート ディレクトリには、ブート レコードによって決定されたエントリの数のみ保持できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-220">The root directory can only hold the number of entries determined by the boot record.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-221">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-221">Input Parameters</span></span>

- <span data-ttu-id="aa949-222">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-222">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-223">**directory_name**: 作成するディレクトリの名前を指すポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-223">**directory_name**: Pointer to the name of the directory to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-224">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-224">Return Values</span></span>

- <span data-ttu-id="aa949-225">**FX_SUCCESS** (0x00) ディレクトリの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-225">**FX_SUCCESS** (0x00) Successful directory create.</span></span>
- <span data-ttu-id="aa949-226">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-226">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-227">**FX_NOT_FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-227">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="aa949-228">**FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-228">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory</span></span>
- <span data-ttu-id="aa949-229">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-229">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-230">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-230">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-231">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-231">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-232">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-232">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-233">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-233">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-234">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-234">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-235">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません</span><span class="sxs-lookup"><span data-stu-id="aa949-235">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="aa949-236">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-236">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="aa949-237">**FX_INVALID_ATTR** (0x19) 無効な属性が選択されました。</span><span class="sxs-lookup"><span data-stu-id="aa949-237">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="aa949-238">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-238">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-239">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-239">Allowed From</span></span>

<span data-ttu-id="aa949-240">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-240">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-241">例</span><span class="sxs-lookup"><span data-stu-id="aa949-241">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Create a subdirectory called "temp" in the current default directory. */

status = fx_directory_create(&my_media, "temp");

/* If status equals FX_SUCCESS, the new subdirectory "temp" has been created. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-242">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-242">See Also</span></span>

- <span data-ttu-id="aa949-243">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-243">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-244">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-244">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-245">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-245">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-246">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-246">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-247">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-247">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-248">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-248">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-249">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-249">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-250">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-250">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-251">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-251">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-252">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-252">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-253">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-253">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-254">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-254">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-255">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-255">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-256">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-256">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-257">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-257">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-258">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-258">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-259">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-259">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-260">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-260">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-261">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-261">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-262">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-262">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_get"></a><span data-ttu-id="aa949-263">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-263">fx_directory_default_get</span></span>

<span data-ttu-id="aa949-264">最後のデフォルト ディレクトリを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-264">Gets last default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-265">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-265">Prototype</span></span>

```c
UINT fx_directory_default_get(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="aa949-266">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-266">Description</span></span>

<span data-ttu-id="aa949-267">このサービスは、***fx_directory_default_set*** によって最後に設定されたパスへのポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-267">This service returns the pointer to the path last set by ***fx_directory_default_set***.</span></span> <span data-ttu-id="aa949-268">デフォルト ディレクトリが設定されていない場合、または現在のデフォルト ディレクトリがルート ディレクトリである場合は、FX_NULL の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-268">If the default directory has not been set or if the current default directory is the root directory, a value of FX_NULL is returned.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-269">*内部パス文字列のデフォルト サイズは 256 文字です。これは **fx_api.h** の **FX_MAXIMUM_PATH** を変更し、FileX ライブラリ全体を再構築することによって変更できます。文字列のパスはアプリケーション用に保持され、FileX によって内部的に使用されません。*</span><span class="sxs-lookup"><span data-stu-id="aa949-269">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-270">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-270">Input Parameters</span></span>

- <span data-ttu-id="aa949-271">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-271">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-272">**return_path_name**: 最後のデフォルト ディレクトリ文字列の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-272">**return_path_name**: Pointer to the destination for the last default directory string.</span></span> <span data-ttu-id="aa949-273">デフォルト ディレクトリの現在の設定がルートである場合は、FX_NULL の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-273">A value of FX_NULL is returned if the current setting of the default directory is the root.</span></span> <span data-ttu-id="aa949-274">メディアをオープンしたとき、ルートが既定値になります。</span><span class="sxs-lookup"><span data-stu-id="aa949-274">When the media is opened, root is the default.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-275">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-275">Return Values</span></span>

- <span data-ttu-id="aa949-276">**FX_SUCCESS** (0x00) デフォルト ディレクトリの取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-276">**FX_SUCCESS** (0x00) Successful default directory get</span></span>
- <span data-ttu-id="aa949-277">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-278">**FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-278">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="aa949-279">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-279">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-280">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-280">Allowed From</span></span>

<span data-ttu-id="aa949-281">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-281">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-282">例</span><span class="sxs-lookup"><span data-stu-id="aa949-282">Example</span></span>

```c
FX_MEDIA my_media;
CHAR *current_default_dir;
UINT status;
/* Retrieve the current default directory. */
status = fx_directory_default_get(&my_media, &current_default_dir);
/* If status equals FX_SUCCESS, "current_default_dir" 
    contains a pointer to the current default directory).*/
```

### <a name="see-also"></a><span data-ttu-id="aa949-283">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-283">See Also</span></span>

- <span data-ttu-id="aa949-284">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-284">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-285">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-285">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-286">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-286">fx_directory_create</span></span>
- <span data-ttu-id="aa949-287">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-287">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-288">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-288">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-289">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-289">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-290">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-290">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-291">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-291">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-292">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-292">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-293">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-293">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-294">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-294">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-295">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-295">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-296">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-296">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-297">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-297">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-298">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-298">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-299">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-299">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-300">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-300">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-301">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-301">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-302">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-302">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-303">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-303">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_default_set"></a><span data-ttu-id="aa949-304">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-304">fx_directory_default_set</span></span>

<span data-ttu-id="aa949-305">デフォルト ディレクトリを設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-305">Sets default directory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-306">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-306">Prototype</span></span>

```c

UINT fx_directory_default_set(
    FX_MEDIA *media_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="aa949-307">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-307">Description</span></span>

<span data-ttu-id="aa949-308">このサービスは、メディアのデフォルト ディレクトリを設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-308">This service sets the default directory of the media.</span></span> <span data-ttu-id="aa949-309">FX_NULL の値が指定されている場合、デフォルト ディレクトリはメディアのルート ディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-309">If a value of FX_NULL is supplied, the default directory is set to the media's root directory.</span></span> <span data-ttu-id="aa949-310">パスを明示的に指定していない後続のすべてのファイル操作は、デフォルトでこのディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-310">All subsequent file operations that do not explicitly specify a path will default to this directory.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-311">*内部パス文字列のデフォルト サイズは 256 文字です。これは **fx_api.h** の **FX_MAXIMUM_PATH** を変更し、FileX ライブラリ全体を再構築することによって変更できます。文字列のパスはアプリケーション用に保持され、FileX によって内部的に使用されません。*</span><span class="sxs-lookup"><span data-stu-id="aa949-311">*The default size of the internal path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-312">*アプリケーションによって提供される名前の場合、FileX では、ディレクトリ、サブディレクトリ、およびファイル名を区切るために円記号 (\\) とスラッシュ (/) の両方の文字がサポートされます。ただし FileX では、アプリケーションに返されるパスで円記号のみを使用します。*</span><span class="sxs-lookup"><span data-stu-id="aa949-312">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-313">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-313">Input Parameters</span></span>

- <span data-ttu-id="aa949-314">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-314">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-315">**new_path_name**: 新しいデフォルト ディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-315">**new_path_name**: Pointer to new default directory name.</span></span> <span data-ttu-id="aa949-316">FX_NULL の値が指定されている場合、メディアのデフォルト ディレクトリはメディアのルート ディレクトリに設定されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-316">If a value of FX_NULL is supplied, the default directory of the media is set to the media's root directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-317">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-317">Return Values</span></span>

- <span data-ttu-id="aa949-318">**FX_SUCCESS** (0x00) デフォルト ディレクトリの設定に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-318">**FX_SUCCESS** (0x00)  Successful default directory set</span></span>
- <span data-ttu-id="aa949-319">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-319">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-320">**FX_INVALID_PATH** (0x0D) 新しいディレクトリが見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-320">**FX_INVALID_PATH** (0x0D) New directory could not be found</span></span>
- <span data-ttu-id="aa949-321">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-321">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-322">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-322">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-323">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-323">Allowed From</span></span>

<span data-ttu-id="aa949-324">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-324">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-325">例</span><span class="sxs-lookup"><span data-stu-id="aa949-325">Example</span></span>

```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_default_set(&my_media, "\\abc\\def\\ghi");
/* If status equals FX_SUCCESS, the default directory for this media is \abc\def\ghi. All subsequent file operations that do not explicitly specify a path will default to this directory. Note that the character "\" serves as an escape character in a string. To represent the character "\", use the construct "\\". This is done because of the C language- only one "\" is really present in the string. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-326">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-326">See Also</span></span>

- <span data-ttu-id="aa949-327">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-327">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-328">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-328">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-329">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-329">fx_directory_create</span></span>
- <span data-ttu-id="aa949-330">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-330">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-331">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-331">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-332">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-332">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-333">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-333">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-334">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-334">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-335">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-335">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-336">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-336">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-337">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-337">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-338">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-338">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-339">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-339">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-340">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-340">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-341">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-341">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-342">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-342">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-343">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-343">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-344">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-344">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-345">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-345">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-346">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-346">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_delete"></a><span data-ttu-id="aa949-347">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-347">fx_directory_delete</span></span>

<span data-ttu-id="aa949-348">サブディレクトリを削除します</span><span class="sxs-lookup"><span data-stu-id="aa949-348">Deletes subdirectory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-349">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-349">Prototype</span></span>

```c
UINT fx_directory_delete(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="aa949-350">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-350">Description</span></span>

<span data-ttu-id="aa949-351">このサービスは、指定されたディレクトリを削除します。</span><span class="sxs-lookup"><span data-stu-id="aa949-351">This service deletes the specified directory.</span></span> <span data-ttu-id="aa949-352">削除するにはディレクトリを空にする必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa949-352">Note that the directory must be empty to delete it.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-353">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-353">Input Parameters</span></span>

- <span data-ttu-id="aa949-354">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-354">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-355">**directory_name**: 削除するディレクトリの名前へのポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-355">**directory_name**: Pointer to name of directory to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-356">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-356">Return Values</span></span>

- <span data-ttu-id="aa949-357">**FX_SUCCESS** (0x00) ディレクトリの削除に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-357">**FX_SUCCESS** (0x00) Successful directory delete</span></span>
- <span data-ttu-id="aa949-358">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-358">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-359">**FX_NOT_FOUND** (0x04) 指定されたディレクトリが見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-359">**FX_NOT_FOUND** (0x04) Specified directory was not found</span></span>
- <span data-ttu-id="aa949-360">**FX_DIR_NOT_EMPTY** (0x10) 指定されたディレクトリは空ではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-360">**FX_DIR_NOT_EMPTY** (0x10) Specified directory is not empty</span></span>
- <span data-ttu-id="aa949-361">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-361">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-362">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています</span><span class="sxs-lookup"><span data-stu-id="aa949-362">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="aa949-363">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-363">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-364">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-364">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-365">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-365">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-366">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-366">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-367">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-367">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-368">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません</span><span class="sxs-lookup"><span data-stu-id="aa949-368">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="aa949-369">**FX_NOT_DIRECTORY** (0x0E) ディレクトリ エントリではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-369">**FX_NOT_DIRECTORY** (0x0E) Not a directory entry</span></span>
- <span data-ttu-id="aa949-370">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-370">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>
- <span data-ttu-id="aa949-371">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-371">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-372">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-372">Allowed From</span></span>

<span data-ttu-id="aa949-373">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-373">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-374">例</span><span class="sxs-lookup"><span data-stu-id="aa949-374">Example</span></span>
```c
FX_MEDIA     my_media;
UINT status;
/* Set the default directory to \abc\def\ghi. */
status = fx_directory_delete(&my_media, "abc");
/* Delete the subdirectory "abc." */
/* If status equals FX_SUCCESS, the subdirectory "abc" was deleted. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-375">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-375">See Also</span></span>

- <span data-ttu-id="aa949-376">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-376">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-377">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-377">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-378">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-378">fx_directory_create</span></span>
- <span data-ttu-id="aa949-379">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-379">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-380">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-380">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-381">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-381">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-382">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-382">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-383">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-383">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-384">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-384">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-385">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-385">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-386">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-386">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-387">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-387">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-388">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-388">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-389">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-389">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-390">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-390">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-391">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-391">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-392">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-392">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-393">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-393">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-394">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-394">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-395">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-395">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_entry_find"></a><span data-ttu-id="aa949-396">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-396">fx_directory_first_entry_find</span></span>

<span data-ttu-id="aa949-397">最初のディレクトリ エントリを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-397">Gets first directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-398">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-398">Prototype</span></span>

```c
UINT fx_directory_first_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="aa949-399">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-399">Description</span></span>

<span data-ttu-id="aa949-400">このサービスは、デフォルト ディレクトリ内の最初のエントリ名を取得し、指定した宛先にコピーします。</span><span class="sxs-lookup"><span data-stu-id="aa949-400">This service retrieves the first entry name in the default directory and copies it to the specified destination.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-401">*指定された宛先は、\*\*FX_MAX_LONG_NAME_LEN*\* で定義されているように、最大サイズの FileX 名を保持するのに十分な大きさである必要があります。\*</span><span class="sxs-lookup"><span data-stu-id="aa949-401">*The specified destination must be large enough to hold the maximum sized FileX name, as defined by **FX_MAX_LONG_NAME_LEN.***</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-402">*ローカル以外のパスを使用する場合は、ディレクトリ トラバーサルの実行中に他のアプリケーション スレッドによってこのディレクトリが変更されることを (ThreadX セマフォ、ミューテックス、または優先度レベルの変更により) 防ぐことが重要です。そうでないと、無効な結果が得られる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-402">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-403">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-403">Input Parameters</span></span>

- <span data-ttu-id="aa949-404">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-404">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-405">**return_entry_name**: デフォルト ディレクトリにある最初のエントリ名の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-405">**return_entry_name**: Pointer to destination for the first entry name in the default directory.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-406">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-406">Return Values</span></span>

- <span data-ttu-id="aa949-407">**FX_SUCCESS** (0x00) 最初のディレクトリ エントリの検索に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-407">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="aa949-408">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-408">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-409">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません</span><span class="sxs-lookup"><span data-stu-id="aa949-409">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="aa949-410">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-410">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-411">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-411">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-412">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-412">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-413">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-413">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-414">**FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-414">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer</span></span>
- <span data-ttu-id="aa949-415">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-415">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-416">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-416">Allowed From</span></span>

<span data-ttu-id="aa949-417">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-417">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-418">例</span><span class="sxs-lookup"><span data-stu-id="aa949-418">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
CHAR             entry[FX_MAX_LONG_NAME_LEN];
/* Retrieve the first directory entry in the current directory. */
status = fx_directory_first_entry_find(&my_media, entry);
/* If status equals FX_SUCCESS, the entry in the directory is the "entry" string. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-419">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-419">See Also</span></span>

- <span data-ttu-id="aa949-420">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-420">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-421">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-421">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-422">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-422">fx_directory_create</span></span>
- <span data-ttu-id="aa949-423">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-423">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-424">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-424">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-425">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-425">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-426">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-426">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-427">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-427">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-428">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-428">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-429">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-429">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-430">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-430">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-431">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-431">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-432">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-432">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-433">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-433">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-434">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-434">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-435">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-435">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-436">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-436">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-437">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-437">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-438">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-438">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-439">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-439">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_first_full_entry_find"></a><span data-ttu-id="aa949-440">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-440">fx_directory_first_full_entry_find</span></span>

<span data-ttu-id="aa949-441">完全な情報を含む最初のディレクトリ エントリを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-441">Gets first directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-442">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-442">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="aa949-443">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-443">Input Parameters</span></span>

- <span data-ttu-id="aa949-444">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-444">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-445">**directory_name**: ディレクトリ エントリの名前の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-445">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="aa949-446">FX_MAX_LONG_NAME_LEN 以上の大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-446">Must be at least as big as FX_MAX_LONG_NAME_LEN.</span></span>
- <span data-ttu-id="aa949-447">**attributes**: null 以外の場合、配置されるエントリの属性の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-447">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.</span></span> <span data-ttu-id="aa949-448">属性は、次の設定が可能なビットマップ形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-448">The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="aa949-449">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-449">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="aa949-450">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-450">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="aa949-451">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-451">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="aa949-452">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="aa949-452">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="aa949-453">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="aa949-453">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="aa949-454">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="aa949-454">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="aa949-455">**size**: null 以外の場合、エントリのサイズの宛先を指すポインター (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="aa949-455">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="aa949-456">**year**: null 以外の場合、エントリが変更された年の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-456">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="aa949-457">**month**: null 以外の場合、エントリが変更された月の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-457">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="aa949-458">**day**: null 以外の場合、エントリが変更された日の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-458">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="aa949-459">**hour**: null 以外の場合、エントリが変更された時間の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-459">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="aa949-460">**minute**: null 以外の場合、エントリが変更された分の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-460">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="aa949-461">**second**: null 以外の場合、エントリが変更された秒の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-461">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-462">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-462">Return Values</span></span>

- <span data-ttu-id="aa949-463">**FX_SUCCESS** (0x00) 最初のディレクトリ エントリの検索に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-463">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="aa949-464">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-464">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-465">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません</span><span class="sxs-lookup"><span data-stu-id="aa949-465">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory</span></span>
- <span data-ttu-id="aa949-466">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-466">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-467">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています</span><span class="sxs-lookup"><span data-stu-id="aa949-467">**FX_WRITE_PROTECT** (0x23) Specified media is write protected</span></span>
- <span data-ttu-id="aa949-468">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-468">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-469">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-469">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-470">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-470">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-471">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-471">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-472">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-472">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-473">**FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-473">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="aa949-474">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-474">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-475">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-475">Allowed From</span></span>

<span data-ttu-id="aa949-476">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-476">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-477">例</span><span class="sxs-lookup"><span data-stu-id="aa949-477">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
UINT         attributes;
ULONG        size;
UINT         year;
UINT         month;
UINT         day;
UINT         hour;
UINT         minute;
UINT         second;
/* Get the first directory entry in the default directory with full information. */
status = fx_directory_first_full_entry_find(&my_media, entry_name,
    &attributes, &size, &year, &month, &day, &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-478">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-478">See Also</span></span>

- <span data-ttu-id="aa949-479">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-479">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-480">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-480">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-481">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-481">fx_directory_create</span></span>
- <span data-ttu-id="aa949-482">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-482">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-483">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-483">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-484">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-484">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-485">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-485">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-486">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-486">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-487">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-487">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-488">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-488">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-489">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-489">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-490">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-490">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-491">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-491">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-492">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-492">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-493">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-493">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-494">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-494">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-495">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-495">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-496">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-496">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-497">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-497">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-498">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-498">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_information_get"></a><span data-ttu-id="aa949-499">fx_directory_information_get:</span><span class="sxs-lookup"><span data-stu-id="aa949-499">fx_directory_information_get:</span></span>

<span data-ttu-id="aa949-500">ディレクトリ エントリの情報を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-500">Gets directory entry information</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-501">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-501">Prototype</span></span>

```c
UINT fx_directory_first_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes,
    ULONG *size,
    UINT *year, UINT *month, UINT *day,
    UINT *hour, UINT *minute, UINT *second);
```
### <a name="input-parameters"></a><span data-ttu-id="aa949-502">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-502">Input Parameters</span></span>

- <span data-ttu-id="aa949-503">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-503">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-504">**directory_name**: ディレクトリ エントリの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-504">**directory_name**: Pointer to name of the directory entry.</span></span>
- <span data-ttu-id="aa949-505">**attributes**: 属性の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-505">**attributes**: Pointer to the destination for the attributes.</span></span>
- <span data-ttu-id="aa949-506">**size**: サイズの宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-506">**size**: Pointer to the destination for the size.</span></span>
- <span data-ttu-id="aa949-507">**year**: 年の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-507">**year**: Pointer to the destination for the year.</span></span>
- <span data-ttu-id="aa949-508">**month**: 月の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-508">**month**: Pointer to the destination for the month.</span></span>
- <span data-ttu-id="aa949-509">**day**: 日の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-509">**day**: Pointer to the destination for the day.</span></span>
- <span data-ttu-id="aa949-510">**hour**: 時間の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-510">**hour**: Pointer to the destination for the hour.</span></span>
- <span data-ttu-id="aa949-511">**minute**: 分の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-511">**minute**: Pointer to the destination for the minute.</span></span>
- <span data-ttu-id="aa949-512">**second**: 秒の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-512">**second**: Pointer to the destination for the second.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-513">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-513">Return Values</span></span>

- <span data-ttu-id="aa949-514">**FX_SUCCESS** (0x00) 最初のディレクトリ エントリの検索に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-514">**FX_SUCCESS** (0x00) Successful first directory entry find</span></span>
- <span data-ttu-id="aa949-515">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-515">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-516">**FX_NOT_FOUND** (0x04) 指定されたディレクトリがメディアに見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-516">**FX_NOT_FOUND** (0x04) Specified directory was not found in the media</span></span>
- <span data-ttu-id="aa949-517">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-517">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-518">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-518">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-519">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-519">**FX_FILE _CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-520">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-520">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-521">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-521">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-522">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-522">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-523">**FX_PTR_ERROR** (0x18) 無効なメディアまたは宛先ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-523">**FX_PTR_ERROR** (0x18) Invalid media or destination pointer.</span></span>
- <span data-ttu-id="aa949-524">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-524">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-525">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-525">Allowed From</span></span>

<span data-ttu-id="aa949-526">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-526">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-527">例</span><span class="sxs-lookup"><span data-stu-id="aa949-527">Example</span></span>

```c
FX_MEDIA     my_media;
UINT         status; attributes; year; month; day;
CHAR         entry_name[FX_MAX_LONG_NAME_LEN];
ULONG        size;
UINT         hour; minute; second;
/* Retrieve information about the directory entry "myfile.txt".*/
status = fx_directory_information_get(&my_media, "myfile.txt", &attributes, &size,
                                      &year, &month, &day,
                                      &hour, &minute, &second);
/* If status equals FX_SUCCESS, the directory entry information is available in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-528">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-528">See Also</span></span>

- <span data-ttu-id="aa949-529">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-529">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-530">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-530">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-531">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-531">fx_directory_create</span></span>
- <span data-ttu-id="aa949-532">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-532">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-533">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-533">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-534">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-534">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-535">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-535">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-536">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-536">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-537">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-537">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-538">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-538">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-539">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-539">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-540">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-540">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-541">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-541">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-542">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-542">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-543">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-543">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-544">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-544">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-545">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-545">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-546">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-546">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-547">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-547">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-548">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-548">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_clear"></a><span data-ttu-id="aa949-549">fx_directory_local_path_clear:</span><span class="sxs-lookup"><span data-stu-id="aa949-549">fx_directory_local_path_clear:</span></span>

<span data-ttu-id="aa949-550">デフォルト ローカル パスをクリアします</span><span class="sxs-lookup"><span data-stu-id="aa949-550">Clears default local path</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-551">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-551">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="aa949-552">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-552">Description</span></span>

<span data-ttu-id="aa949-553">このサービスは、呼び出し元のスレッド用に設定された前のローカル パスをクリアします。</span><span class="sxs-lookup"><span data-stu-id="aa949-553">This service clears the previous local path set up for the calling thread.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-554">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-554">Input Parameters</span></span>

- <span data-ttu-id="aa949-555">**media_ptr**: 以前に開いたメディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-555">**media_ptr**: Pointer to a previously opened media.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-556">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-556">Return Values</span></span>

- <span data-ttu-id="aa949-557">**FX_SUCCESS** (0x00) ローカル パスのクリアに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-557">**FX_SUCCESS** (0x00) Successful local path clear.</span></span>
- <span data-ttu-id="aa949-558">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが現在開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-558">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="aa949-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH が定義されています</span><span class="sxs-lookup"><span data-stu-id="aa949-559">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined</span></span>
- <span data-ttu-id="aa949-560">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-560">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-561">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-561">Allowed From</span></span>

<span data-ttu-id="aa949-562">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-562">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-563">例</span><span class="sxs-lookup"><span data-stu-id="aa949-563">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
/* Clear the previously setup local path for this media. */
status = fx_directory_local_path_clear(&my_media);
/* If status equals FX_SUCCESS the local path is cleared. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-564">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-564">See Also</span></span>

- <span data-ttu-id="aa949-565">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-565">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-566">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-566">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-567">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-567">fx_directory_create</span></span>
- <span data-ttu-id="aa949-568">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-568">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-569">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-569">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-570">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-570">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-571">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-571">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-572">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-572">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-573">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-573">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-574">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-574">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-575">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-575">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-576">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-576">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-577">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-577">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-578">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-578">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-579">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-579">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-580">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-580">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-581">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-581">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-582">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-582">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-583">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-583">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-584">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-584">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_get"></a><span data-ttu-id="aa949-585">fx_directory_local_path_get:</span><span class="sxs-lookup"><span data-stu-id="aa949-585">fx_directory_local_path_get:</span></span>

<span data-ttu-id="aa949-586">現在のローカル パス文字列を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-586">Gets the current local path string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-587">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-587">Prototype</span></span>

```c
UINT fx_directory_local_path_clear(
    FX_MEDIA *media_ptr,
    CHAR **return_path_name);
```

### <a name="description"></a><span data-ttu-id="aa949-588">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-588">Description</span></span>

<span data-ttu-id="aa949-589">このサービスは、指定されたメディアのローカル パス ポインターを返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-589">This service returns the local path pointer of the specified media.</span></span> <span data-ttu-id="aa949-590">ローカル パスが設定されていない場合は、呼び出し元に NULL が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-590">If there is no local path set, a NULL is returned to the caller.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-591">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-591">Input Parameters</span></span>

- <span data-ttu-id="aa949-592">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-592">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-593">**return_path_name**: 格納されるローカル パス文字列の宛先文字列ポインターへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-593">**return_path_name**: Pointer to the destination string pointer for the local path string to be stored.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-594">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-594">Return Values</span></span>

- <span data-ttu-id="aa949-595">**FX_SUCCESS** (0x00) ローカル パスの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-595">**FX_SUCCESS** (0x00) Successful local path get.</span></span>
- <span data-ttu-id="aa949-596">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが現在開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-596">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open</span></span>
- <span data-ttu-id="aa949-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="aa949-597">**FX_NOT_IMPLEMENTED** (0x22) NX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="aa949-598">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-598">**FX_PTR_ERROR** (0x18) Invalid media pointer</span></span>


### <a name="allowed-from"></a><span data-ttu-id="aa949-599">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-599">Allowed From</span></span>

<span data-ttu-id="aa949-600">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-600">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-601">例</span><span class="sxs-lookup"><span data-stu-id="aa949-601">Example</span></span>

```c
FX_MEDIA         my_media;
CHAR             *my_path;
UINT             status;
/* Retrieve the current local path string. */
status = fx_directory_local_path_get(&my_media, &my_path);
/* If status equals FX_SUCCESS, "my_path" points to the local path string. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-602">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-602">See Also</span></span>

- <span data-ttu-id="aa949-603">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-603">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-604">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-604">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-605">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-605">fx_directory_create</span></span>
- <span data-ttu-id="aa949-606">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-606">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-607">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-607">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-608">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-608">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-609">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-609">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-610">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-610">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-611">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-611">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-612">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-612">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-613">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-613">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-614">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-614">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-615">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-615">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-616">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-616">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-617">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-617">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-618">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-618">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-619">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-619">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-620">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-620">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-621">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-621">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-622">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-622">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_restore"></a><span data-ttu-id="aa949-623">fx_directory_local_path_restore:</span><span class="sxs-lookup"><span data-stu-id="aa949-623">fx_directory_local_path_restore:</span></span>

<span data-ttu-id="aa949-624">前のローカル パスを復元します</span><span class="sxs-lookup"><span data-stu-id="aa949-624">Restores previous local path</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-625">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-625">Prototype</span></span>

```c
UINT fx_directory_local_path_restore(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr);
```

### <a name="description"></a><span data-ttu-id="aa949-626">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-626">Description</span></span>

<span data-ttu-id="aa949-627">このサービスは、以前に設定したローカル パスを復元します。</span><span class="sxs-lookup"><span data-stu-id="aa949-627">This service restores a previously set local path.</span></span> <span data-ttu-id="aa949-628">このローカル パスに対して行われたディレクトリの検索位置も復元されるため、このルーチンは、アプリケーションによる再帰的なディレクトリのトラバーサルに役立ちます。</span><span class="sxs-lookup"><span data-stu-id="aa949-628">The directory search position made on this local path is also restored, which makes this routine useful in recursive directory traversals by the application.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-629">*各ローカル パスには **FX_MAXIMUM_PATH** のローカル パス文字列のサイズが含まれており、既定で 256 文字です。この内部パス文字列は FileX では使用されず、アプリケーションで使用するためにのみ提供されています。\*\*FX_LOCAL_PATH*\* がローカル変数として宣言される場合、ユーザーは、この構造体のサイズによって増加しているスタックに注意する必要があります。ユーザーは **FX_MAXIMUM_PATH** のサイズを小さくし、FileX ライブラリ ソースを再構築することが推奨されます。\*</span><span class="sxs-lookup"><span data-stu-id="aa949-629">*Each local path contains a local path string of **FX_MAXIMUM_PATH** in size, which by default is 256 characters. This internal path string is not used by FileX and is provided only for the application's use. If **FX_LOCAL_PATH** is going to be declared as a local variable, users should beware of the stack growing by the size of this structure. Users are welcome to reduce the size of **FX_MAXIMUM_PATH** and rebuild the FileX library source.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-630">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-630">Input Parameters</span></span>

- <span data-ttu-id="aa949-631">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-631">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-632">**local_path_ptr**: 以前に設定されたローカル パスへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-632">**local_path_ptr**: Pointer to the previously set local path.</span></span> <span data-ttu-id="aa949-633">このポインターが、以前に使用されていてそのまま保持されているローカル パスをポイントするようにすることは非常に重要です。</span><span class="sxs-lookup"><span data-stu-id="aa949-633">It's very important to ensure that this pointer does indeed point to a previously used and still intact local path.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-634">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-634">Return Values</span></span>

- <span data-ttu-id="aa949-635">**FX_SUCCESS** (0x00) ローカル パスの復元に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-635">**FX_SUCCESS** (0x00) Successful local path restore.</span></span>
- <span data-ttu-id="aa949-636">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not currently open.</span></span>
- <span data-ttu-id="aa949-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH が定義されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-637">**FX_NOT_IMPLEMENTED** (0x22) FX_NO_LCOAL_PATH is defined.</span></span>
- <span data-ttu-id="aa949-638">**FX_PTR_ERROR** (0x18) 無効なメディアまたはローカル パス ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-638">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-639">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-639">Allowed From</span></span>

<span data-ttu-id="aa949-640">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-640">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-641">例</span><span class="sxs-lookup"><span data-stu-id="aa949-641">Example</span></span>

```c
FX_MEDIA                  my_media;
FX_LOCAL_PATH             my_previous_local_path;
UINT                      status;
/* Restore the previous local path. */
status = fx_directory_local_path_restore(&my_media, &my_previous_local_path);
/* If status equals FX_SUCCESS, the previous local path has been restored. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-642">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-642">See Also</span></span>

- <span data-ttu-id="aa949-643">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-643">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-644">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-644">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-645">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-645">fx_directory_create</span></span>
- <span data-ttu-id="aa949-646">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-646">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-647">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-647">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-648">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-648">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-649">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-649">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-650">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-650">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-651">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-651">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-652">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-652">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-653">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-653">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-654">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-654">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-655">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-655">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-656">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-656">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-657">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-657">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-658">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-658">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-659">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-659">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-660">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-660">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-661">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-661">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-662">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-662">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_local_path_set"></a><span data-ttu-id="aa949-663">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-663">fx_directory_local_path_set</span></span>

<span data-ttu-id="aa949-664">スレッド固有のローカルパスを設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-664">Sets up a thread-specific local path</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-665">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-665">Prototype</span></span>

```c
UINT fx_directory_local_path_set(
    FX_MEDIA *media_ptr,
    FX_LOCAL_PATH *local_path_ptr,
    CHAR *new_path_name);
```

### <a name="description"></a><span data-ttu-id="aa949-666">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-666">Description</span></span>

<span data-ttu-id="aa949-667">このサービスは、\***new_path_string** _ によって指定されたスレッド固有のパスを設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-667">This service sets up a thread-specific path as specified by the \***new_path_string** _.</span></span> <span data-ttu-id="aa949-668">このルーチンが正常に完了すると、_ *_local_path_ptr_*\* に格納されているローカル パス情報が、このスレッドによって実行されるすべてのファイルおよびディレクトリ操作のグローバル メディア パスよりも優先されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-668">After successful completion of this routine, the local path information stored in _ *_local_path_ptr_*\* will take precedence over the global media path for all file and directory operations made by this thread.</span></span> <span data-ttu-id="aa949-669">これは、システム内の他のスレッドには影響しません</span><span class="sxs-lookup"><span data-stu-id="aa949-669">This will have no impact on any other thread in the system</span></span> 
> [!IMPORTANT]
> <span data-ttu-id="aa949-670">*ローカル パス文字列のデフォルト サイズは 256 文字です。これは **fx_api.h** の **FX_MAXIMUM_PATH** を変更し、FileX ライブラリ全体を再構築することによって変更できます。文字列のパスはアプリケーション用に保持され、FileX によって内部的に使用されません。*</span><span class="sxs-lookup"><span data-stu-id="aa949-670">*The default size of the local path string is 256 characters; it can be changed by modifying **FX_MAXIMUM_PATH** in **fx_api.h** and rebuilding the entire FileX library. The character string path is maintained for the application and is not used internally by FileX.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-671">*アプリケーションによって提供される名前の場合、FileX では、ディレクトリ、サブディレクトリ、およびファイル名を区切るために円記号 (\\) とスラッシュ (/) の両方の文字がサポートされます。ただし FileX では、アプリケーションに返されるパスで円記号のみを使用します。*</span><span class="sxs-lookup"><span data-stu-id="aa949-671">*For names supplied by the application, FileX supports both backslash (\\) and forward slash (/) characters to separate directories, subdirectories, and file names. However, FileX only uses the backslash character in paths returned to the application.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-672">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-672">Input Parameters</span></span>

- <span data-ttu-id="aa949-673">**media_ptr**: 以前に開いたメディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-673">**media_ptr**: Pointer to the previously opened media.</span></span>
- <span data-ttu-id="aa949-674">**local_path_ptr**: スレッド固有のローカル パス情報を保持するための宛先。</span><span class="sxs-lookup"><span data-stu-id="aa949-674">**local_path_ptr**: Destination for holding the thread-specific local path information.</span></span> <span data-ttu-id="aa949-675">この構造体のアドレスは、後でローカル パスの復元関数に渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="aa949-675">The address of this structure may be supplied to the local path restore function in the future.</span></span>
- <span data-ttu-id="aa949-676">**new_path_name**: セットアップするローカル パスを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-676">**new_path_name**: Specifies the local path to setup.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-677">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-677">Return Values</span></span>

- <span data-ttu-id="aa949-678">**FX_SUCCESS** (0x00) デフォルト ディレクトリの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-678">**FX_SUCCESS** (0x00) Successful default directory set.</span></span>
- <span data-ttu-id="aa949-679">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-679">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span><span class="sxs-lookup"><span data-stu-id="aa949-680">**FX_NOT_IMPLEMENTED** (0x22) \*\*FX_NO_LCOAL_PATH</span></span>
- <span data-ttu-id="aa949-681">**FX_INVALID_PATH** (0x0D) 新しいディレクトリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-681">**FX_INVALID_PATH** (0x0D) New directory could not be found.</span></span>
- <span data-ttu-id="aa949-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH が定義されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-682">**FX_NOT_IMPLEMENTED** (0x22)- \*\*FX_NO_LOCAL_PATH is defined.</span></span>
- <span data-ttu-id="aa949-683">**FX_PTR_ERROR** (0x18) 無効なメディアまたはローカル パス ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-683">**FX_PTR_ERROR** (0x18) Invalid media or local path pointer.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-684">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-684">Allowed From</span></span>

<span data-ttu-id="aa949-685">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-685">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-686">例</span><span class="sxs-lookup"><span data-stu-id="aa949-686">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;
FX_LOCAL_PATH     my_previous_local_path;
/* Set the local path to \abc\def\ghi. */
status = fx_directory_local_path_set (&my_media,&local_path,"\\abc\\def\\ghi");

/* If status equals FX_SUCCESS, the default directory for this thread
is \abc\def\ghi. All subsequent file operations that do not explicitly
specify a path will default to this directory. Note that the character
"\" serves as an escape character in a string. To represent the
character "\", use the construct "\\".*/
```

### <a name="see-also"></a><span data-ttu-id="aa949-687">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-687">See Also</span></span>

- <span data-ttu-id="aa949-688">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-688">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-689">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-689">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-690">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-690">fx_directory_create</span></span>
- <span data-ttu-id="aa949-691">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-691">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-692">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-692">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-693">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-693">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-694">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-694">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-695">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-695">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-696">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-696">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-697">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-697">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-698">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-698">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-699">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-699">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-700">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-700">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-701">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-701">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-702">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-702">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-703">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-703">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-704">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-704">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-705">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-705">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-706">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-706">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-707">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-707">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get"></a><span data-ttu-id="aa949-708">fx_directory_long_name_get:</span><span class="sxs-lookup"><span data-stu-id="aa949-708">fx_directory_long_name_get:</span></span>

<span data-ttu-id="aa949-709">短い名前から長い名前を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-709">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-710">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-710">Prototype</span></span>

```c
UINT fx_directory_long_name_get(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name);
```

### <a name="description"></a><span data-ttu-id="aa949-711">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-711">Description</span></span>

<span data-ttu-id="aa949-712">このサービスは、指定された短い名前 (8.3 形式) に関連付けられている長い名前 (存在する場合) を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-712">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="aa949-713">短い名前には、ファイル名またはディレクトリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-713">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-714">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-714">Input Parameters</span></span>

- <span data-ttu-id="aa949-715">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-715">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-716">**short_name**: ソースの短い名前 (8.3 形式) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-716">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="aa949-717">**long_name**: 長い名前の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-717">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="aa949-718">長い名前がない場合は、短い名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-718">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="aa949-719">長い名前の宛先は、FX_MAX_LONG_NAME_LEN 文字を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa949-719">Note that the destination for the long name must be large enough to hold FX_MAX_LONG_NAME_LEN characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-720">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-720">Return Values</span></span>

- <span data-ttu-id="aa949-721">**FX_SUCCESS** (0x00) 長い名前の取得に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-721">**FX_SUCCESS** (0x00) Successful long name get</span></span>
- <span data-ttu-id="aa949-722">**FX_NOT_FOUND** (0x04) 短い名前が見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="aa949-722">**FX_NOT_FOUND** (0x04) Short name was not found</span></span>
- <span data-ttu-id="aa949-723">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー</span><span class="sxs-lookup"><span data-stu-id="aa949-723">**FX_IO_ERROR** (0x90) Driver I/O error</span></span>
- <span data-ttu-id="aa949-724">**FX_MEDIA_INVALID** (0x02) 無効なメディア</span><span class="sxs-lookup"><span data-stu-id="aa949-724">**FX_MEDIA_INVALID** (0x02) Invalid media</span></span>
- <span data-ttu-id="aa949-725">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-725">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-726">**FX_SECTOR_INVALID** (0x89) 無効なセクター</span><span class="sxs-lookup"><span data-stu-id="aa949-726">**FX_SECTOR_INVALID** (0x89) Invalid sector</span></span>
- <span data-ttu-id="aa949-727">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません</span><span class="sxs-lookup"><span data-stu-id="aa949-727">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry</span></span>
- <span data-ttu-id="aa949-728">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-728">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-729">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-729">**FX_PTR_ERROR** (0x18) Invalid media or name pointer</span></span>
- <span data-ttu-id="aa949-730">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-730">**FX_CALLER_ERROR** (0x20) Caller is not a thread</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-731">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-731">Allowed From</span></span>

<span data-ttu-id="aa949-732">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-732">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-733">例</span><span class="sxs-lookup"><span data-stu-id="aa949-733">Example</span></span>

```c
FX_MEDIA            my_media;
UCHAR               my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */
status = fx_directory_long_name_get(&my_media, "TEXT~01.TXT", my_long_name);
/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-734">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-734">See Also</span></span>

- <span data-ttu-id="aa949-735">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-735">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-736">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-736">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-737">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-737">fx_directory_create</span></span>
- <span data-ttu-id="aa949-738">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-738">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-739">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-739">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-740">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-740">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-741">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-741">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-742">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-742">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-743">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-743">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-744">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-744">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-745">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-745">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-746">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-746">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-747">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-747">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-748">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-748">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-749">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-749">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-750">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-750">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-751">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-751">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-752">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-752">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-753">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-753">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-754">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-754">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_long_name_get_extended"></a><span data-ttu-id="aa949-755">fx_directory_long_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="aa949-755">fx_directory_long_name_get_extended</span></span>

<span data-ttu-id="aa949-756">短い名前から長い名前を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-756">Gets long name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-757">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-757">Prototype</span></span>

```c
UINT fx_directory_long_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *short_name,
    CHAR *long_name,
    UINT long_file_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="aa949-758">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-758">Description</span></span>

<span data-ttu-id="aa949-759">このサービスは、指定された短い名前 (8.3 形式) に関連付けられている長い名前 (存在する場合) を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-759">This service retrieves the long name (if any) associated with the supplied short (8.3 format) name.</span></span> <span data-ttu-id="aa949-760">短い名前には、ファイル名またはディレクトリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-760">The short name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-761">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-761">Input Parameters</span></span>

- <span data-ttu-id="aa949-762">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-762">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-763">**short_name**: ソースの短い名前 (8.3 形式) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-763">**short_name**: Pointer to source short name (8.3 format).</span></span>
- <span data-ttu-id="aa949-764">**long_name**: 長い名前の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-764">**long_name**: Pointer to destination for the long name.</span></span> <span data-ttu-id="aa949-765">長い名前がない場合は、短い名前が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-765">If there is no long name, the short name is returned.</span></span> <span data-ttu-id="aa949-766">注: 長い名前の宛先は、**FX_MAX_LONG_NAME_LEN** 文字を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa949-766">Note: Destination for the long name must be large enough to hold **FX_MAX_LONG_NAME_LEN** characters.</span></span>
- <span data-ttu-id="aa949-767">**long_file_name_buffer_length**: 長い名前バッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-767">**long_file_name_buffer_length**: Length of the long name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-768">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-768">Return Values</span></span>

- <span data-ttu-id="aa949-769">**FX_SUCCESS** (0x00) 長い名前の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-769">**FX_SUCCESS** (0x00) Successful long name get.</span></span>
- <span data-ttu-id="aa949-770">**FX_NOT_FOUND** (0x04) 短い名前が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-770">**FX_NOT_FOUND** (0x04) Short name was not found.</span></span>
- <span data-ttu-id="aa949-771">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-771">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-772">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-772">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-773">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-773">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-774">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-774">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-775">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-775">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-776">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-776">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-777">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-777">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="aa949-778">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-778">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-779">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-779">Allowed From</span></span>

<span data-ttu-id="aa949-780">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-780">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-781">例</span><span class="sxs-lookup"><span data-stu-id="aa949-781">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_long_name[FX_MAX_LONG_NAME_LEN];
/* Retrieve the long name associated with "TEXT~01.TXT". */

status = fx_directory_long_name_get_extended(&my_media,
    "TEXT~01.TXT", my_long_name), sizeof(my_long_name));

/* If status is FX_SUCCESS the long name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-782">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-782">See Also</span></span>

- <span data-ttu-id="aa949-783">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-783">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-784">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-784">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-785">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-785">fx_directory_create</span></span>
- <span data-ttu-id="aa949-786">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-786">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-787">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-787">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-788">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-788">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-789">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-789">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-790">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-790">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-791">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-791">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-792">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-792">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-793">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-793">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-794">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-794">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-795">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-795">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-796">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-796">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-797">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-797">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-798">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-798">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-799">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-799">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-800">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-800">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-801">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-801">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-802">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-802">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_name_test"></a><span data-ttu-id="aa949-803">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-803">fx_directory_name_test</span></span>

<span data-ttu-id="aa949-804">ディレクトリをテストします</span><span class="sxs-lookup"><span data-stu-id="aa949-804">Tests for directory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-805">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-805">Prototype</span></span>

```c
UINT fx_directory_name_test(
    FX_MEDIA *media_ptr,
    CHAR *directory_name);
```

### <a name="description"></a><span data-ttu-id="aa949-806">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-806">Description</span></span>

<span data-ttu-id="aa949-807">このサービスは、指定された名前がディレクトリであるかどうかをテストします。</span><span class="sxs-lookup"><span data-stu-id="aa949-807">This service tests whether or not the supplied name is a directory.</span></span> <span data-ttu-id="aa949-808">そうであれば、FX_SUCCESS が返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-808">If so, a FX_SUCCESS is returned.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-809">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-809">Input Parameters</span></span>

- <span data-ttu-id="aa949-810">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-810">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-811">**directory_name**: ディレクトリ エントリの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-811">**directory_name**: Pointer to name of the directory entry.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-812">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-812">Return Values</span></span>

- <span data-ttu-id="aa949-813">**FX_SUCCESS** (0x00) 指定された名前はディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="aa949-813">**FX_SUCCESS** (0x00) Supplied name is a directory.</span></span>
- <span data-ttu-id="aa949-814">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません</span><span class="sxs-lookup"><span data-stu-id="aa949-814">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open</span></span>
- <span data-ttu-id="aa949-815">**FX_NOT_FOUND** (0x04) ディレクトリ エントリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-815">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="aa949-816">**FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません</span><span class="sxs-lookup"><span data-stu-id="aa949-816">**FX_NOT_DIRECTORY** (0x0E)  Entry is not a directory</span></span>
- <span data-ttu-id="aa949-817">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-817">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-818">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-818">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-819">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-819">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-820">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-820">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-821">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-821">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-822">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-822">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-823">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-823">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="aa949-824">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-824">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-825">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-825">Allowed From</span></span>

<span data-ttu-id="aa949-826">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-826">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-827">例</span><span class="sxs-lookup"><span data-stu-id="aa949-827">Example</span></span>

```c
FX_MEDIA        my_media;
UNIT             status;
/* Check to see if the name "abc" is directory */

status = fx_directory_name_test(&my_media, "abc");

/* If status equals FX_SUCCESS "abc" is a directory. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-828">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-828">See Also</span></span>

- <span data-ttu-id="aa949-829">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-829">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-830">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-830">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-831">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-831">fx_directory_create</span></span>
- <span data-ttu-id="aa949-832">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-832">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-833">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-833">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-834">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-834">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-835">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-835">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-836">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-836">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-837">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-837">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-838">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-838">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-839">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-839">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-840">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-840">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-841">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-841">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-842">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-842">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-843">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-843">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-844">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-844">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-845">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-845">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-846">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-846">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-847">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-847">fx_unicode_directory_create</span></span>

## <a name="fx_directory_next_entry_find"></a><span data-ttu-id="aa949-848">fx_directory_next_entry_find:</span><span class="sxs-lookup"><span data-stu-id="aa949-848">fx_directory_next_entry_find:</span></span>

<span data-ttu-id="aa949-849">次のディレクトリ エントリを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-849">Picks up next directory entry</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-850">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-850">Prototype</span></span>

```c
UINT fx_directory_next_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *return_entry_name);
```

### <a name="description"></a><span data-ttu-id="aa949-851">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-851">Description</span></span>

<span data-ttu-id="aa949-852">このサービスは、現在のデフォルト ディレクトリ内の次のエントリ名を返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-852">This service returns the next entry name in the current default directory.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-853">*ローカル以外のパスを使用する場合は、ディレクトリ トラバーサルの実行中に他のアプリケーション スレッドによってこのディレクトリが変更されることを (ThreadX セマフォまたはスレッド優先度レベルにより) 防ぐことも重要です。そうでないと、無効な結果が得られる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-853">*If using a non-local path, it is also important to prevent (with a ThreadX semaphore or thread priority level) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-854">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-854">Input Parameters</span></span>

- <span data-ttu-id="aa949-855">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-855">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-856">**return_entry_name**: デフォルト ディレクトリ内の次のエントリ名の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-856">**return_entry_name**: Pointer to destination for the next entry name in the default directory.</span></span> <span data-ttu-id="aa949-857">このポインターが指すバッファーは、**_FX_MAX_LONG_NAME_LEN_** によって定義される FileX 名の最大サイズを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-857">The buffer this pointer points to must be large enough to hold the maximum size of FileX name, defined by **_FX_MAX_LONG_NAME_LEN_**.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-858">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-858">Return Values</span></span>

- <span data-ttu-id="aa949-859">**FX_SUCCESS** (0x00) 次のエントリの検索に成功しました</span><span class="sxs-lookup"><span data-stu-id="aa949-859">**FX_SUCCESS** (0x00) Successful next entry find</span></span>
- <span data-ttu-id="aa949-860">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-860">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-861">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-861">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="aa949-862">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-862">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-863">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-863">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-864">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-864">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-865">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-865">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-866">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-866">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-867">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-867">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-868">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-868">**FX_CALLER_ERROR** (0x20)     Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-869">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-869">Allowed From</span></span>

<span data-ttu-id="aa949-870">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-870">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-871">例</span><span class="sxs-lookup"><span data-stu-id="aa949-871">Example</span></span>

```c
FX_MEDIA        my_media;
CHAR            next_name[FX_MAX_LONG_NAME_LEN];
UINT            status;

/* Retrieve the next entry in the default directory. */

status = fx_directory_next_entry_find(&my_media, next_name);

/* If status equals TX_SUCCESS, the name of the next directory entry is in "next_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-872">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-872">See Also</span></span>

- <span data-ttu-id="aa949-873">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-873">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-874">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-874">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-875">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-875">fx_directory_create</span></span>
- <span data-ttu-id="aa949-876">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-876">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-877">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-877">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-878">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-878">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-879">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-879">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-880">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-880">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-881">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-881">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-882">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-882">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-883">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-883">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-884">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-884">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-885">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-885">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-886">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-886">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-887">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-887">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-888">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-888">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-889">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-889">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-890">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-890">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-891">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-891">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-892">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-892">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_next_full_entry_find"></a><span data-ttu-id="aa949-893">fx_directory_next_full_entry_find:</span><span class="sxs-lookup"><span data-stu-id="aa949-893">fx_directory_next_full_entry_find:</span></span>

<span data-ttu-id="aa949-894">完全な情報を含む次のディレクトリ エントリを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-894">Gets next directory entry with full information</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-895">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-895">Prototype</span></span>

```c
UINT fx_directory_next_full_entry_find(
    FX_MEDIA *media_ptr,
    CHAR *directory_name,
    UINT *attributes, 
    ULONG *size,
    UINT *year, 
    UINT *month, 
    UINT *day,
    UINT *hour, 
    UINT *minute, 
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="aa949-896">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-896">Description</span></span>

<span data-ttu-id="aa949-897">このサービスは、デフォルト ディレクトリ内の次のエントリ名を取得し、指定した宛先にコピーします。</span><span class="sxs-lookup"><span data-stu-id="aa949-897">This service retrieves the next entry name in the default directory and copies it to the specified destination.</span></span> <span data-ttu-id="aa949-898">また、追加の入力パラメーターによって指定されたエントリに関する完全な情報も返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-898">It also returns full information about the entry as specified by the additional input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-899">*指定された宛先は、\*\*\*FX_MAX_LONG_NAME_LEN*\*\* で定義されているように、最大サイズの FileX 名を保持するのに十分な大きさである必要があります\*</span><span class="sxs-lookup"><span data-stu-id="aa949-899">\*The specified destination must be large enough to hold the maximum sized FileX name, as defined by \*\*\*FX_MAX_LONG_NAME_LEN\*\*\*\*</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-900">*ローカル以外のパスを使用する場合は、ディレクトリ トラバーサルの実行中に他のアプリケーション スレッドによってこのディレクトリが変更されることを (ThreadX セマフォ、ミューテックス、または優先度レベルの変更により) 防ぐことが重要です。そうでないと、無効な結果が得られる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-900">*If using a non-local path, it is important to prevent (with a ThreadX semaphore, mutex, or priority level change) other application threads from changing this directory while a directory traversal is taking place. Otherwise, invalid results may be obtained.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-901">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-901">Input Parameters</span></span>

- <span data-ttu-id="aa949-902">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-902">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-903">**directory_name**: ディレクトリ エントリの名前の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-903">**directory_name**: Pointer to the destination for the name of a directory entry.</span></span> <span data-ttu-id="aa949-904">**FX_MAX_LONG_NAME_LEN** 以上の大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-904">Must be at least as big as **FX_MAX_LONG_NAME_LEN**.</span></span>
- <span data-ttu-id="aa949-905">**attributes**: null 以外の場合、配置されるエントリの属性の宛先へのポインター。属性は、次の設定が可能なビットマップ形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-905">**attributes**: If non-null, pointer to the destination for the entry's attributes to be placed.The attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="aa949-906">**FX_READ_ONLY** (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-906">**FX_READ_ONLY** (0x01)</span></span>
  - <span data-ttu-id="aa949-907">**FX_HIDDEN** (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-907">**FX_HIDDEN** (0x02)</span></span>
  - <span data-ttu-id="aa949-908">**FX_SYSTEM** (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-908">**FX_SYSTEM** (0x04)</span></span>
  - <span data-ttu-id="aa949-909">**FX_VOLUME** (0x08)</span><span class="sxs-lookup"><span data-stu-id="aa949-909">**FX_VOLUME** (0x08)</span></span>
  - <span data-ttu-id="aa949-910">**FX_DIRECTORY** (0x10)</span><span class="sxs-lookup"><span data-stu-id="aa949-910">**FX_DIRECTORY** (0x10)</span></span>
  - <span data-ttu-id="aa949-911">**FX_ARCHIVE** (0x20)</span><span class="sxs-lookup"><span data-stu-id="aa949-911">**FX_ARCHIVE** (0x20)</span></span>
- <span data-ttu-id="aa949-912">**size**: null 以外の場合、エントリのサイズの宛先を指すポインター (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="aa949-912">**size**: If non-null, pointer to the destination for the entry's size in bytes.</span></span>
- <span data-ttu-id="aa949-913">**month**: null 以外の場合、エントリが変更された月の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-913">**month**: If non-null, pointer to the destination for the entry's month of modification.</span></span>
- <span data-ttu-id="aa949-914">**year**: null 以外の場合、エントリが変更された年の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-914">**year**: If non-null, pointer to the destination for the entry's year of modification.</span></span>
- <span data-ttu-id="aa949-915">**day**: null 以外の場合、エントリが変更された日の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-915">**day**: If non-null, pointer to the destination for the entry's day of modification.</span></span>
- <span data-ttu-id="aa949-916">**hour**: null 以外の場合、エントリが変更された時間の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-916">**hour**: If non-null, pointer to the destination for the entry's hour of modification.</span></span>
- <span data-ttu-id="aa949-917">**minute**: null 以外の場合、エントリが変更された分の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-917">**minute**: If non-null, pointer to the destination for the entry's minute of modification.</span></span>
- <span data-ttu-id="aa949-918">**second**: null 以外の場合、エントリが変更された秒の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-918">**second**: If non-null, pointer to the destination for the entry's second of modification.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-919">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-919">Return Values</span></span>

- <span data-ttu-id="aa949-920">**FX_SUCCESS** (0x00) ディレクトリ内の次のエントリの検索に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-920">**FX_SUCCESS** (0x00) Successful directory next entry find.</span></span>
- <span data-ttu-id="aa949-921">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-921">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-922">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-922">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="aa949-923">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-923">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-924">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-924">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-925">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-925">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-926">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-926">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-927">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-927">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-928">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-928">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-929">**FX_PTR_ERROR** (0x18) 無効なメディア ポインターまたはすべての入力パラメーターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-929">**FX_PTR_ERROR** (0x18) Invalid media pointer or all input parameters are NULL.</span></span>
- <span data-ttu-id="aa949-930">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-930">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-931">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-931">Allowed From</span></span>

<span data-ttu-id="aa949-932">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-932">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-933">例</span><span class="sxs-lookup"><span data-stu-id="aa949-933">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
CHAR        entry_name[FX_MAX_LONG_NAME_LEN];
UINT        attributes;
ULONG       size;
UINT        year;
UINT        month;
UINT        day;
UINT        hour;
UINT        minute;
UINT        second;

/* Get the next directory entry in the default directory with full information. */
status = fx_directory_next_full_entry_find(&my_media, entry_name, &attributes, &size,
                                           &year, &month, &day,
                                           &hour, &minute, &second);

/* If status equals FX_SUCCESS, the entry's information is in the local variables. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-934">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-934">See Also</span></span>

- <span data-ttu-id="aa949-935">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-935">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-936">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-936">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-937">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-937">fx_directory_create</span></span>
- <span data-ttu-id="aa949-938">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-938">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-939">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-939">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-940">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-940">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-941">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-941">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-942">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-942">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-943">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-943">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-944">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-944">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-945">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-945">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-946">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-946">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-947">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-947">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-948">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-948">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-949">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-949">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-950">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-950">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-951">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-951">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-952">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-952">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-953">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-953">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-954">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-954">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_rename"></a><span data-ttu-id="aa949-955">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-955">fx_directory_rename</span></span>

<span data-ttu-id="aa949-956">ディレクトリ名を変更します</span><span class="sxs-lookup"><span data-stu-id="aa949-956">Renames directory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-957">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-957">Prototype</span></span>

```c
UINT fx_directory_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_directory_name,
    CHAR *new_directory_name);
```

### <a name="description"></a><span data-ttu-id="aa949-958">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-958">Description</span></span>

<span data-ttu-id="aa949-959">このサービスは、ディレクトリ名を、指定された新しいディレクトリ名に変更します。</span><span class="sxs-lookup"><span data-stu-id="aa949-959">This service changes the directory name to the specified new directory name.</span></span> <span data-ttu-id="aa949-960">名前の変更は、指定されたパスまたはデフォルト パスに対しても実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-960">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="aa949-961">新しいディレクトリ名にパスが指定されている場合、名前が変更されたディレクトリは指定したパスに事実上移動します。</span><span class="sxs-lookup"><span data-stu-id="aa949-961">If a path is specified in the new directory name, the renamed directory is effectively moved to the specified path.</span></span> <span data-ttu-id="aa949-962">パスが指定されていない場合、名前が変更されたディレクトリは現在のデフォルト パスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-962">If no path is specified, the renamed directory is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-963">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-963">Input Parameters</span></span>

- <span data-ttu-id="aa949-964">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-964">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-965">**old_directory_name**: 現在のディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-965">**old_directory_name**: Pointer to current directory name.</span></span>
- <span data-ttu-id="aa949-966">**new_directory_name**: 新しいディレクトリ名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-966">**new_directory_name**: Pointer to new directory name.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-967">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-967">Return Values</span></span>

- <span data-ttu-id="aa949-968">**FX_SUCCESS** (0x00) ディレクトリの名前変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-968">**FX_SUCCESS** (0x00) Successful directory rename.</span></span>
- <span data-ttu-id="aa949-969">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-969">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-970">**FX_NOT_FOUND** (0x04) ディレクトリ エントリが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-970">**FX_NOT_FOUND** (0x04) Directory entry could not be found.</span></span>
- <span data-ttu-id="aa949-971">**FX_NOT_DIRECTORY** (0x0E) エントリはディレクトリではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-971">**FX_NOT_DIRECTORY** (0x0E) Entry is not a directory.</span></span>
- <span data-ttu-id="aa949-972">**FX_INVALID_NAME** (0x0C) 新しいディレクトリ名が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-972">**FX_INVALID_NAME** (0x0C) New directory name is invalid.</span></span>
- <span data-ttu-id="aa949-973">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-973">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-974">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-974">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-975">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-975">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-976">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-976">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-977">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-977">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-978">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-978">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-979">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-979">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-980">**FX_NO_MORE_ENTRIES** (0x0F) このディレクトリにはこれ以上エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-980">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in this directory.</span></span>
- <span data-ttu-id="aa949-981">**FX_INVALID_PATH** (0x0D) ディレクトリ名に無効なパスが指定されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-981">**FX_INVALID_PATH** (0x0D) Invalid path supplied with directory name.</span></span>
- <span data-ttu-id="aa949-982">**FX_ALREADY_CREATED** (0x0B) 指定されたディレクトリは既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-982">**FX_ALREADY_CREATED** (0x0B) Specified directory was already created.</span></span>
- <span data-ttu-id="aa949-983">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-983">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-984">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-984">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-985">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-985">Allowed From</span></span>

<span data-ttu-id="aa949-986">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-986">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-987">例</span><span class="sxs-lookup"><span data-stu-id="aa949-987">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Change the directory "abc" to "def". */
status = fx_directory_rename(&my_media, "abc", "def");

/* If status equals FX_SUCCESS, the directory was changed to "def". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-988">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-988">See Also</span></span>

- <span data-ttu-id="aa949-989">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-989">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-990">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-990">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-991">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-991">fx_directory_create</span></span>
- <span data-ttu-id="aa949-992">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-992">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-993">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-993">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-994">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-994">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-995">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-995">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-996">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-996">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-997">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-997">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-998">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-998">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-999">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-999">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-1000">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-1000">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-1001">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1001">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-1002">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1002">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-1003">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-1003">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-1004">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1004">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-1005">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1005">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-1006">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1006">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-1007">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1007">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-1008">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1008">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get"></a><span data-ttu-id="aa949-1009">fx_directory_short_name_get:</span><span class="sxs-lookup"><span data-stu-id="aa949-1009">fx_directory_short_name_get:</span></span>

<span data-ttu-id="aa949-1010">長い名前から短い名前を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-1010">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1011">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1011">Prototype</span></span>

```c
UINT fx_directory_short_name_get(
    FX_MEDIA *media_ptr,
    CHAR *long_name, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="aa949-1012">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1012">Description</span></span>

<span data-ttu-id="aa949-1013">このサービスは、指定された長い名前に関連付けられている短い名前 (8.3 形式) を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1013">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="aa949-1014">長い名前には、ファイル名またはディレクトリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1014">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1015">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1015">Input Parameters</span></span>

- <span data-ttu-id="aa949-1016">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1016">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-1017">**long_name**: ソースの長い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1017">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="aa949-1018">**short_name**: 短い名前 (8.3 形式) の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1018">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="aa949-1019">短い名前の宛先は、14 文字を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa949-1019">Note that the destination for the short name must be large enough to hold 14 characters.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1020">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1020">Return Values</span></span>

- <span data-ttu-id="aa949-1021">**FX_SUCCESS** (0x00) 短い名前の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1021">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="aa949-1022">**FX_NOT_FOUND** (0x04) 長い名前が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1022">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="aa949-1023">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1023">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1024">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1024">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1025">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1025">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1026">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1026">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1027">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1027">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1028">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1028">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1029">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-1029">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-1030">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1030">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="aa949-1031">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1031">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1032">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1032">Allowed From</span></span>

<span data-ttu-id="aa949-1033">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1033">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1034">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1034">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get(&my_media,
    "my_really_long_name", my_short_name);

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1035">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1035">See Also</span></span>

- <span data-ttu-id="aa949-1036">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1036">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-1037">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1037">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-1038">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1038">fx_directory_create</span></span>
- <span data-ttu-id="aa949-1039">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1039">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-1040">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1040">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-1041">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1041">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-1042">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1042">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-1043">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1043">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-1044">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1044">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-1045">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-1045">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-1046">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1046">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-1047">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-1047">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-1048">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1048">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-1049">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1049">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-1050">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-1050">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-1051">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1051">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-1052">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1052">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-1053">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1053">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-1054">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1054">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-1055">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1055">fx_unicode_directory_rename</span></span>

## <a name="fx_directory_short_name_get_extended"></a><span data-ttu-id="aa949-1056">fx_directory_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="aa949-1056">fx_directory_short_name_get_extended</span></span>

<span data-ttu-id="aa949-1057">長い名前から短い名前を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-1057">Gets short name from a long name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1058">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1058">Prototype</span></span>

```csharp
UINT fx_directory_short_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *long_name,
    CHAR *short_name,
    UINT short_file_name_length);
```

### <a name="description"></a><span data-ttu-id="aa949-1059">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1059">Description</span></span>

<span data-ttu-id="aa949-1060">このサービスは、指定された長い名前に関連付けられている短い名前 (8.3 形式) を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1060">This service retrieves the short (8.3 format) name associated with the supplied long name.</span></span> <span data-ttu-id="aa949-1061">長い名前には、ファイル名またはディレクトリ名を指定できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1061">The long name can be either a file name or a directory name.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1062">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1062">Input Parameters</span></span>

- <span data-ttu-id="aa949-1063">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1063">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-1064">**long_name**: ソースの長い名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1064">**long_name**: Pointer to source long name.</span></span>
- <span data-ttu-id="aa949-1065">**short_name**: 短い名前 (8.3 形式) の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1065">**short_name**: Pointer to destination short name (8.3 format).</span></span> <span data-ttu-id="aa949-1066">注: 短い名前の宛先は、14 文字を保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-1066">Note: Destination for the short name must be large enough to hold 14 characters.</span></span>
- <span data-ttu-id="aa949-1067">**short_file_name_length**: 短い名前のバッファーの長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-1067">**short_file_name_length**: Length of short name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1068">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1068">Return Values</span></span>

- <span data-ttu-id="aa949-1069">**FX_SUCCESS** (0x00) 短い名前の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1069">**FX_SUCCESS** (0x00) Successful short name get.</span></span>
- <span data-ttu-id="aa949-1070">**FX_NOT_FOUND** (0x04) 長い名前が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1070">**FX_NOT_FOUND** (0x04) Long name was not found.</span></span>
- <span data-ttu-id="aa949-1071">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1071">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1072">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1072">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1073">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1074">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1075">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1075">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1076">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1076">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1077">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-1077">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-1078">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1078">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="aa949-1079">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1079">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1080">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1080">Allowed From</span></span>

<span data-ttu-id="aa949-1081">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1081">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1082">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1082">Example</span></span>

```c
FX_MEDIA        my_media;
UCHAR            my_short_name[14];

/* Retrieve the short name associated with "my_really_long_name". */

status = fx_directory_short_name_get_extended(&my_media,
    "my_really_long_name", my_short_name, sizeof(my_short_name));

/* If status is FX_SUCCESS the short name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1083">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1083">See Also</span></span>

- <span data-ttu-id="aa949-1084">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1084">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-1085">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1085">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-1086">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1086">fx_directory_create</span></span>
- <span data-ttu-id="aa949-1087">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1087">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-1088">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1088">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-1089">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1089">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-1090">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1090">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-1091">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1091">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-1092">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1092">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-1093">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-1093">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-1094">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1094">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-1095">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-1095">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-1096">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1096">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-1097">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1097">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-1098">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-1098">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-1099">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1099">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-1100">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-1100">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-1101">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1101">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-1102">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1102">fx_unicode_directory_create</span></span>
- <span data-ttu-id="aa949-1103">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1103">fx_unicode_directory_rename</span></span>

## <a name="fx_fault_tolerant_enable"></a><span data-ttu-id="aa949-1104">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-1104">fx_fault_tolerant_enable</span></span>

<span data-ttu-id="aa949-1105">フォールト トレラント サービスを有効にします</span><span class="sxs-lookup"><span data-stu-id="aa949-1105">Enables the fault tolerant service</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1106">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1106">Prototype</span></span>

```csharp
UINT fx_fault_tolerant_enable(
    FX_MEDIA *media_ptr,
    VOID *memory_buffer,
    UINT memory_size);
```

### <a name="description"></a><span data-ttu-id="aa949-1107">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1107">Description</span></span>

<span data-ttu-id="aa949-1108">このサービスは、フォールト トレラント モジュールを有効にします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1108">This service enables the fault tolerant module.</span></span> <span data-ttu-id="aa949-1109">開始時に、フォールト トレラント モジュールは、ファイル システムが FileX フォールト トレラントで保護されているかどうかを検出します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1109">Upon starting, the fault tolerant module detects whether or not the file system is under FileX fault tolerant protection.</span></span> <span data-ttu-id="aa949-1110">されていない場合、このサービスはファイル システム上で使用可能なセクターを検出し、ファイル システムのトランザクションに関するログを格納します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1110">If it is not, the service finds available sectors on the file system to store logs on file system transactions.</span></span> <span data-ttu-id="aa949-1111">ファイル システムが FileX フォールト トレラントで保護されている場合は、ログをファイル システムに適用して整合性を維持します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1111">If the file system is under FileX fault tolerant protection, it applies the logs to the file system to maintain its integrity.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1112">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1112">Input Parameters</span></span>

- <span data-ttu-id="aa949-1113">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1113">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-1114">**memory_ptr**: フォールト トレラント モジュールによってスクラッチ メモリとして使用されるメモリのブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1114">**memory_ptr**: Pointer to a block of memory used by the fault tolerant module as scratch memory.</span></span>
- <span data-ttu-id="aa949-1115">**memory_size**: スクラッチ メモリのサイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-1115">**memory_size**: The size of the scratch memory.</span></span> <span data-ttu-id="aa949-1116">フォールト トレラントを正常に機能させるには、スクラッチ メモリのサイズが 3072 バイト以上で、セクター サイズの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-1116">In order for fault tolerant to work properly, the scratch memory size shall be at least 3072 bytes,- and must be multiple of sector size.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1117">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1117">Return Values</span></span>

- <span data-ttu-id="aa949-1118">**FX_SUCCESS** (0x00) フォールト トレラントが正常に有効になりました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1118">**FX_SUCCESS** (0x00) Successfully enabled fault tolerant.</span></span>
- <span data-ttu-id="aa949-1119">**FX_NOT_ENOUGH_MEMORY** (0x91) メモリ サイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1119">**FX_NOT_ENOUGH_MEMORY** (0x91)    memory size too small.</span></span>
- <span data-ttu-id="aa949-1120">**FX_BOOT_ERROR** (0x01) ブート セクター エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1120">**FX_BOOT_ERROR** (0x01) Boot sector error.</span></span>
- <span data-ttu-id="aa949-1121">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1121">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1122">**FX_NO_MORE_ENTRIES** (0x0F) 使用可能な空きクラスターがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1122">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="aa949-1123">**FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1123">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="aa949-1124">**FX_SECTOR_INVALID** (0x89) セクターが無効です</span><span class="sxs-lookup"><span data-stu-id="aa949-1124">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="aa949-1125">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1125">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1126">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1126">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-1127">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1127">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1128">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1128">Allowed From</span></span>

<span data-ttu-id="aa949-1129">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="aa949-1129">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1130">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1130">Example</span></span>

```c

/* Declare memory space used for fault tolerant. */

ULONG fault tolerant_memory[3072 / sizeof(ULONG)];

/* Enable fault tolerant. */

fx_fault_tolerant_enable(media_ptr, fault_tolerant_memory, sizeof(fault_tolerant_memory));

```

### <a name="see-also"></a><span data-ttu-id="aa949-1131">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1131">See Also</span></span>

- <span data-ttu-id="aa949-1132">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-1132">fx_system_initialize</span></span>
- <span data-ttu-id="aa949-1133">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-1133">fx_media_abort</span></span>
- <span data-ttu-id="aa949-1134">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-1134">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-1135">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-1135">fx_media_check</span></span>
- <span data-ttu-id="aa949-1136">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1136">fx_media_close</span></span>
- <span data-ttu-id="aa949-1137">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1137">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-1138">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-1138">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-1139">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-1139">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-1140">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-1140">fx_media_flush</span></span>
- <span data-ttu-id="aa949-1141">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-1141">fx_media_format</span></span>
- <span data-ttu-id="aa949-1142">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1142">fx_media_open</span></span>
- <span data-ttu-id="aa949-1143">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1143">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-1144">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1144">fx_media_read</span></span>
- <span data-ttu-id="aa949-1145">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-1145">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-1146">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1146">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-1147">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1147">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-1148">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1148">fx_media_write</span></span>

## <a name="fx_file_allocate"></a><span data-ttu-id="aa949-1149">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1149">fx_file_allocate</span></span>

<span data-ttu-id="aa949-1150">ファイルの領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="aa949-1150">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1151">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1151">Prototype</span></span>

```csharp
UINT fx_file_allocate(
    FX_FILE *file_ptr, 
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="aa949-1152">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1152">Description</span></span>

<span data-ttu-id="aa949-1153">このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1153">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="aa949-1154">FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1154">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="aa949-1155">結果はクラスター数が整数になるように切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1155">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="aa949-1156">4 GB を超える領域を割り当てるには、アプリケーションでサービス *fx_file_extended_allocate* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-1156">To allocate space beyond 4GB, application shall use the service *fx_file_extended_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1157">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1157">Input Parameters</span></span>

- <span data-ttu-id="aa949-1158">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1158">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-1159">**size**: ファイルに割り当てるバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-1159">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1160">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1160">Return Values</span></span>

- <span data-ttu-id="aa949-1161">**FX_SUCCESS** (0x00) ファイルの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1161">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="aa949-1162">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1162">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-1163">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1163">**FX_FAT_READ_ERROR** (0x03) Failed to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1164">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1164">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1165">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1165">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-1166">**FX_NO_MORE_ENTRIES** (0x0F) 使用可能な空きクラスターがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1166">**FX_NO_MORE_ENTRIES** (0x0F) No more free cluster available.</span></span>
- <span data-ttu-id="aa949-1167">**FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1167">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="aa949-1168">**FX_SECTOR_INVALID** (0x89) セクターが無効です</span><span class="sxs-lookup"><span data-stu-id="aa949-1168">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="aa949-1169">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1169">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1170">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1170">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1171">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1171">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1172">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1172">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1173">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1173">Allowed From</span></span>

<span data-ttu-id="aa949-1174">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1174">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1175">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1175">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;

/* Allocate 1024 bytes to the end of my_file. */

status = fx_file_allocate(&my_file, 1024);

/* If status equals FX_SUCCESS the file now has one or more
    contiguous cluster(s) that can accommodate at least 1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1176">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1176">See Also</span></span>

- <span data-ttu-id="aa949-1177">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1177">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1178">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1178">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1179">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1179">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1180">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1180">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="aa949-1181">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1181">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1182">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1182">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1183">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1183">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1184">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1184">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1185">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1185">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1186">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1186">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1187">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1187">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1188">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1188">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1189">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1189">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="aa949-1190">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1190">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1191">fx_file_rename- fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1191">fx_file_rename- fx_file_seek</span></span>
- <span data-ttu-id="aa949-1192">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1192">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1193">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1193">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1194">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1194">fx_file_write</span></span>
- <span data-ttu-id="aa949-1195">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1195">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1196">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1196">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1197">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1197">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1198">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1198">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1199">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1199">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_read"></a><span data-ttu-id="aa949-1200">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1200">fx_file_attributes_read</span></span>

<span data-ttu-id="aa949-1201">ファイル属性を読み取ります</span><span class="sxs-lookup"><span data-stu-id="aa949-1201">Reads file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1202">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1202">Prototype</span></span>

```c
    UINT fx_file_attributes_read(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT *attributes_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-1203">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1203">Description</span></span>

<span data-ttu-id="aa949-1204">このサービスは、指定されたメディアからファイル属性を読み取ります。</span><span class="sxs-lookup"><span data-stu-id="aa949-1204">This service reads the file's attributes from the specified media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1205">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1205">Input Parameters</span></span>

- <span data-ttu-id="aa949-1206">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1206">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-1207">**file_name**: 要求されたファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1207">**file_name**: Pointer to the name of the requested file (directory path is optional).</span></span>
- <span data-ttu-id="aa949-1208">**attributes_ptr**: 配置されるファイルの属性の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1208">**attributes_ptr**: Pointer to the destination for the file's attributes to be placed.</span></span> <span data-ttu-id="aa949-1209">ファイル属性は、次の設定が可能なビットマップ形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1209">The file attributes are returned in a bit-map format with the following possible settings:</span></span>
  - <span data-ttu-id="aa949-1210">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-1210">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="aa949-1211">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-1211">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="aa949-1212">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-1212">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="aa949-1213">FX_VOLUME (0x08)</span><span class="sxs-lookup"><span data-stu-id="aa949-1213">FX_VOLUME (0x08)</span></span>
  - <span data-ttu-id="aa949-1214">FX_DIRECTORY (0x10)</span><span class="sxs-lookup"><span data-stu-id="aa949-1214">FX_DIRECTORY (0x10)</span></span>
  - <span data-ttu-id="aa949-1215">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="aa949-1215">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1216">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1216">Return Values</span></span>

- <span data-ttu-id="aa949-1217">**FX_SUCCESS** (0x00) 属性の読み取りに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1217">**FX_SUCCESS** (0x00) Successful attribute read.</span></span>
- <span data-ttu-id="aa949-1218">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1218">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-1219">**FX_NOT_FOUND** (0x04) 指定されたファイルはメディア内で見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1219">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="aa949-1220">**FX_NOT_A_FILE** (0x05) 指定されたファイルはディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="aa949-1220">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="aa949-1221">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1221">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1222">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1222">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1223">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1223">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1224">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1224">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1225">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1225">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1226">**FX_PTR_ERROR** (0x18) 無効なメディアまたは属性ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1226">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="aa949-1227">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1227">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1228">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1228">Allowed From</span></span>

<span data-ttu-id="aa949-1229">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1229">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1230">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1230">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;
UINT             attributes;

/* Retrieve the attributes of "myfile.txt" from the specified media. */

status = fx_file_attributes_read(&my_media, "myfile.txt", &attributes);

/* If status equals FX_SUCCESS, "attributes"
    contains the file attributes for "myfile.txt". */

```

### <a name="see-also"></a><span data-ttu-id="aa949-1231">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1231">See Also</span></span>

- <span data-ttu-id="aa949-1232">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1232">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1233">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1233">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1234">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1234">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1235">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1235">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="aa949-1236">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1236">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1237">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1237">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1238">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1238">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1239">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1239">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1240">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1240">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1241">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1241">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1242">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1242">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1243">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1243">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1244">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1244">fx_file_open</span></span>
- <span data-ttu-id="aa949-1245">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1245">fx_file_read</span></span>
- <span data-ttu-id="aa949-1246">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1246">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1247">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1247">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1248">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1248">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1249">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1249">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1250">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1250">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1251">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1251">fx_file_write</span></span>
- <span data-ttu-id="aa949-1252">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1252">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1253">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1253">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1254">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1254">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1255">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1255">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1256">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1256">fx_unicode_short_name_get</span></span>

## <a name="fx_file_attributes_set"></a><span data-ttu-id="aa949-1257">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1257">fx_file_attributes_set</span></span>

<span data-ttu-id="aa949-1258">ファイル属性を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-1258">Sets file attributes</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1259">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1259">Prototype</span></span>

```c
UINT fx_file_attributes_set(
    FX_MEDIA *media_ptr,
    CHAR *file_name,
    UINT attributes);
```
### <a name="description"></a><span data-ttu-id="aa949-1260">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1260">Description</span></span>

<span data-ttu-id="aa949-1261">このサービスは、ファイルの属性を、呼び出し元によって指定された属性に設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1261">This service sets the file's attributes to those specified by the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-1262">*このアプリケーションでは、このサービスを使用してファイルの属性のサブセットを変更することのみが許可されています。追加の属性を設定しようとすると、エラーが発生します。*</span><span class="sxs-lookup"><span data-stu-id="aa949-1262">*The application is only allowed to modify a subset of the file's attributes with this service. Any attempt to set additional attributes will result in an error.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1263">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1263">Input Parameters</span></span>

- <span data-ttu-id="aa949-1264">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1264">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-1265">**file_name**: 要求されたファイルの名前を指すポインター\*\* (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1265">**file_name**: Pointer to the name of the requested file\*\* (directory path is optional).</span></span>
- <span data-ttu-id="aa949-1266">**attributes**: ファイルの新しい属性。</span><span class="sxs-lookup"><span data-stu-id="aa949-1266">**attributes**: The new attributes for the file.</span></span> <span data-ttu-id="aa949-1267">有効なファイル属性は次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1267">The valid file attributes are defined as follows:</span></span>
  - <span data-ttu-id="aa949-1268">FX_READ_ONLY (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-1268">FX_READ_ONLY (0x01)</span></span>
  - <span data-ttu-id="aa949-1269">FX_HIDDEN (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-1269">FX_HIDDEN (0x02)</span></span>
  - <span data-ttu-id="aa949-1270">FX_SYSTEM (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-1270">FX_SYSTEM (0x04)</span></span>
  - <span data-ttu-id="aa949-1271">FX_ARCHIVE (0x20)</span><span class="sxs-lookup"><span data-stu-id="aa949-1271">FX_ARCHIVE (0x20)</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1272">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1272">Return Values</span></span>

- <span data-ttu-id="aa949-1273">**FX_SUCCESS** (0x00) 属性の設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1273">**FX_SUCCESS** (0x00) Successful attribute set.</span></span>
- <span data-ttu-id="aa949-1274">**FX_ACCESS_ERROR** (0x06) ファイルが開いているため属性を設定できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1274">**FX_ACCESS_ERROR** (0x06) File is open and cannot have its attributes set.</span></span>
- <span data-ttu-id="aa949-1275">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1275">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1276">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1276">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1277">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1277">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-1278">**FX_NO_MORE_ENTRIES** (0x0F) FAT テーブルまたは exFAT クラスター マップにはこれ以上エントリがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1278">**FX_NO_MORE_ENTRIES** (0x0F) No more entries in the FAT table or exFAT cluster map.</span></span>
- <span data-ttu-id="aa949-1279">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1279">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-1280">**FX_NOT_FOUND** (0x04) 指定されたファイルはメディア内で見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1280">**FX_NOT_FOUND** (0x04) Specified file was not found in the media.</span></span>
- <span data-ttu-id="aa949-1281">**FX_NOT_A_FILE** (0x05) 指定されたファイルはディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="aa949-1281">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="aa949-1282">**FX_SECTOR_INVALID** (0x89) セクターが無効です</span><span class="sxs-lookup"><span data-stu-id="aa949-1282">**FX_SECTOR_INVALID** (0x89) Sector is invalid</span></span>
- <span data-ttu-id="aa949-1283">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1283">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1284">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1284">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1285">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-1285">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-1286">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1286">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-1287">**FX_INVALID_ATTR** (0x19) 無効な属性が選択されました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1287">**FX_INVALID_ATTR** (0x19) Invalid attributes selected.</span></span>
- <span data-ttu-id="aa949-1288">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1288">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1289">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1289">Allowed From</span></span>

<span data-ttu-id="aa949-1290">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1290">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1291">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1291">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Set the attributes of "myfile.txt" to read-only. */

status = fx_file_attributes_set(&my_media, "myfile.txt", FX_READ_ONLY);

/* If status equals FX_SUCCESS, the file is now read-only. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-1292">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1292">See Also</span></span>

- <span data-ttu-id="aa949-1293">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1293">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1294">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1294">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1295">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1295">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1296">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1296">fx_file_close</span></span>
- <span data-ttu-id="aa949-1297">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1297">fx_file_create</span></span>
- <span data-ttu-id="aa949-1298">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1298">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1299">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1299">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1300">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1300">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1301">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1301">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1302">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1302">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1303">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1303">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1304">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1304">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1305">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1305">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1306">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1306">fx_file_open</span></span>
- <span data-ttu-id="aa949-1307">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1307">fx_file_read</span></span>
- <span data-ttu-id="aa949-1308">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1308">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1309">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1309">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1310">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1310">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1311">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1311">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1312">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1312">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1313">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1313">fx_file_write</span></span>
- <span data-ttu-id="aa949-1314">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1314">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1315">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1315">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1316">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1316">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1317">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1317">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1318">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1318">fx_unicode_short_name_get</span></span>

## <a name="fx_file_best_effort_allocate"></a><span data-ttu-id="aa949-1319">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1319">fx_file_best_effort_allocate</span></span>

<span data-ttu-id="aa949-1320">ファイルの領域をベスト エフォートで割り当てます</span><span class="sxs-lookup"><span data-stu-id="aa949-1320">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1321">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1321">Prototype</span></span>

```c
UINT fx_file_best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG size,
    ULONG *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="aa949-1322">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1322">Description</span></span>

<span data-ttu-id="aa949-1323">このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1323">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="aa949-1324">FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1324">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="aa949-1325">結果はクラスター数が整数になるように切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1325">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="aa949-1326">利用可能な連続するクラスターがメディア内に不足している場合、このサービスでは、利用可能な最大の連続するクラスターのブロックをファイルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1326">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="aa949-1327">ファイルに実際に割り当てられた領域の量が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1327">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="aa949-1328">4 GB を超える領域を割り当てるには、アプリケーションでサービス *fx_file_extended_best_effort_allocate* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-1328">To allocate space beyond 4GB, application shall use the service *fx_file_extended_best_effort_allocate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1329">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1329">Input Parameters</span></span>

- <span data-ttu-id="aa949-1330">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1330">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-1331">**size**: ファイルに割り当てるバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-1331">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1332">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1332">Return Values</span></span>

- <span data-ttu-id="aa949-1333">**FX_SUCCESS** (0x00) ベストエフォートのファイル割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1333">**FX_SUCCESS** (0x00) Successful best-effort file allocation.</span></span>
- <span data-ttu-id="aa949-1334">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1334">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-1335">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1335">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-1336">**FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1336">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="aa949-1337">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1337">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1338">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1338">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1339">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1339">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1340">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1340">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1341">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1341">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1342">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1342">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1343">**FX_PTR_ERROR** (0x18) 無効なファイル ポインターまたは宛先。</span><span class="sxs-lookup"><span data-stu-id="aa949-1343">**FX_PTR_ERROR** (0x18) Invalid file pointer or destination.</span></span>
- <span data-ttu-id="aa949-1344">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1344">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1345">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1345">Allowed From</span></span>

<span data-ttu-id="aa949-1346">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1346">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1347">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1347">Example</span></span>

```c

FX_FILE         my_file;
UINT             status;
ULONG             actual_allocation;

/* Attempt to allocate 1024 bytes to the end of my_file. */

status = fx_file_best_effort_allocate(&my_file, 1024, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-1348">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1348">See Also</span></span>

- <span data-ttu-id="aa949-1349">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1349">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1350">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1350">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1351">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1351">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1352">fx_file_close</span></span>
- <span data-ttu-id="aa949-1353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1353">fx_file_create</span></span>
- <span data-ttu-id="aa949-1354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1354">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1355">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1359">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1362">fx_file_open</span></span>
- <span data-ttu-id="aa949-1363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1363">fx_file_read</span></span>
- <span data-ttu-id="aa949-1364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1364">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1365">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1366">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1367">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1368">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1369">fx_file_write</span></span>
- <span data-ttu-id="aa949-1370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1371">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1371">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1372">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1372">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1373">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1373">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1374">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1374">fx_unicode_short_name_get</span></span>

## <a name="fx_file_close"></a><span data-ttu-id="aa949-1375">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1375">fx_file_close</span></span>

<span data-ttu-id="aa949-1376">ファイルを閉じます</span><span class="sxs-lookup"><span data-stu-id="aa949-1376">Closes file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1377">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1377">Prototype</span></span>

```c
UINT fx_file_close(FX_FILE *file_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-1378">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1378">Description</span></span>

<span data-ttu-id="aa949-1379">このサービスは、指定されたファイルをクローズします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1379">This service closes the specified file.</span></span> <span data-ttu-id="aa949-1380">ファイルが書き込み用に開かれており、ファイルが変更されている場合、このサービスは、新しいサイズと現在のシステム時刻および日付を使用してディレクトリ エントリを更新することで、ファイル変更プロセスを完了します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1380">If the file was open for writing and if it was modified, this service completes the file modification process by updating its directory entry with the new size and the current system time and date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1381">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1381">Input Parameters</span></span>

- <span data-ttu-id="aa949-1382">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1382">**file_ptr**: Pointer to a previously opened file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1383">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1383">Return Values</span></span>

- <span data-ttu-id="aa949-1384">**FX_SUCCESS** (0x00) ファイルのクローズに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1384">**FX_SUCCESS** (0x00) Successful file close.</span></span>
- <span data-ttu-id="aa949-1385">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1385">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-1386">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1386">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1387">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1387">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1388">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1388">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1389">**FX_PTR_ERROR** (0x18) 無効なメディアまたは属性ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1389">**FX_PTR_ERROR** (0x18) Invalid media or attributes pointer.</span></span>
- <span data-ttu-id="aa949-1390">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1390">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1391">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1391">Allowed From</span></span>

<span data-ttu-id="aa949-1392">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1392">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1393">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1393">Example</span></span>

```c

FX_FILE        my_file;
UINT        status;

/* Close the previously opened file "my_file". */
status = fx_file_close(&my_file);

/* If status equals FX_SUCCESS, the file was closed successfully. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1394">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1394">See Also</span></span>

- <span data-ttu-id="aa949-1395">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1395">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1396">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1396">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1397">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1397">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1398">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1398">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1399">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1399">fx_file_create</span></span>
- <span data-ttu-id="aa949-1400">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1400">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1401">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1401">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1402">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1402">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1403">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1403">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1404">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1404">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1405">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1405">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1406">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1406">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1407">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1407">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1408">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1408">fx_file_open</span></span>
- <span data-ttu-id="aa949-1409">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1409">fx_file_read</span></span>
- <span data-ttu-id="aa949-1410">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1410">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1411">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1411">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1412">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1412">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1413">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1413">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1414">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1414">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1415">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1415">fx_file_write</span></span>
- <span data-ttu-id="aa949-1416">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1416">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1417">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1417">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1418">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1418">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1419">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1419">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1420">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1420">fx_unicode_short_name_get</span></span>

## <a name="fx_file_create"></a><span data-ttu-id="aa949-1421">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1421">fx_file_create</span></span>

<span data-ttu-id="aa949-1422">ファイルを作成します</span><span class="sxs-lookup"><span data-stu-id="aa949-1422">Creates file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1423">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1423">Prototype</span></span>

```c
UINT fx_file_create(
    FX_MEDIA *media_ptr,
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="aa949-1424">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1424">Description</span></span>

<span data-ttu-id="aa949-1425">このサービスは、指定されたファイルを、デフォルト ディレクトリまたはファイル名と共に指定されたディレクトリ パスに作成します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1425">This service creates the specified file in the default directory or in the directory path supplied with the file name.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-1426">*このサービスでは、長さゼロのファイルが作成されます。つまり、クラスターが割り当てられません。割り当ては、以降のファイルの書き込み時に自動的に実行されます。または、fx_file_allocate サービス (または 4 GB を超える領域の場合は fx_file_extended_allocate サービス) で事前に行うことができます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-1426">*This service creates a file of zero length, i.e., no clusters allocated. Allocation will automatically take place on subsequent file writes or can be done in advance with the fx_file_allocate service or fx_file_extended_allocate for space beyond 4GB) service.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1427">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1427">Input Parameters</span></span>

- <span data-ttu-id="aa949-1428">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1428">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-1429">**file_name**: 作成するファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1429">**file_name**: Pointer to the name of the file to create (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1430">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1430">Return Values</span></span>

- <span data-ttu-id="aa949-1431">**FX_SUCCESS** (0x00) ファイルの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1431">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="aa949-1432">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1432">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-1433">**FX_ALREADY_CREATED** (0x0B) 指定されたファイルは既に作成されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1433">**FX_ALREADY_CREATED** (0x0B) Specified file was already created.</span></span>
- <span data-ttu-id="aa949-1434">**FX_NO_MORE_SPACE** (0x0A) ルート ディレクトリにエントリがこれ以上存在しないか、使用可能なクラスターがありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1434">**FX_NO_MORE_SPACE** (0x0A)    Either there are no more entries in the root directory or there are no more clusters available.</span></span>
- <span data-ttu-id="aa949-1435">**FX_INVALID_PATH** (0x0D) ファイル名に無効なパスが指定されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1435">**FX_INVALID_PATH** (0x0D) Invalid path supplied with file name.</span></span>
- <span data-ttu-id="aa949-1436">**FX_INVALID_NAME** (0x0C) ファイル名が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1436">**FX_INVALID_NAME** (0x0C) File name is invalid.</span></span>
- <span data-ttu-id="aa949-1437">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1437">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1438">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1438">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1439">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1439">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1440">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1440">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1441">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1441">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1442">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-1442">**FX_MEDIA_INVALID** (0x02)Invalid media.</span></span>
- <span data-ttu-id="aa949-1443">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1443">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1444">**FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1444">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="aa949-1445">**FX_PTR_ERROR** (0x18) 無効なメディアまたはファイル名のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1445">**FX_PTR_ERROR** (0x18) Invalid media or file name pointer.</span></span>
- <span data-ttu-id="aa949-1446">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1446">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1447">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1447">Allowed From</span></span>

<span data-ttu-id="aa949-1448">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1448">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1449">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1449">Example</span></span>

```c

FX_MEDIA         my_media;
UINT             status;

/* Create a file called "myfile.txt" in the
    root or the default directory of the media. */

status = fx_file_create(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, a zero sized file named "myfile.txt". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1450">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1450">See Also</span></span>
- <span data-ttu-id="aa949-1451">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1451">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1452">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1452">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1453">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1453">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1454">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1454">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1455">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1455">fx_file_close</span></span>
- <span data-ttu-id="aa949-1456">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1456">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1457">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1457">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1458">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1458">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1459">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1459">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1460">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1460">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1461">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1461">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1462">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1462">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1463">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1463">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1464">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1464">fx_file_open</span></span>
- <span data-ttu-id="aa949-1465">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1465">fx_file_read</span></span>
- <span data-ttu-id="aa949-1466">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1466">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1467">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1467">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1468">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1468">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1469">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1469">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1470">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1470">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1471">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1471">fx_file_write</span></span>
- <span data-ttu-id="aa949-1472">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1472">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1473">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1473">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1474">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1474">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1475">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1475">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1476">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1476">fx_unicode_short_name_get</span></span>

## <a name="fx_file_date_time_set"></a><span data-ttu-id="aa949-1477">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1477">fx_file_date_time_set</span></span>

### <a name="sets-file-date-and-time"></a><span data-ttu-id="aa949-1478">ファイルの日付と時刻を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-1478">Sets file date and time</span></span>

<span data-ttu-id="aa949-1479">ファイルの日付と時刻の設定</span><span class="sxs-lookup"><span data-stu-id="aa949-1479">Setting File Date and Time</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1480">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1480">Prototype</span></span>

```c
UINT fx_file_date_time_set(
    FX_MEDIA *media_ptr, 
    CHAR *file_name,
    UINT year, 
    UINT month, 
    UINT day,
    UINT hour, 
    UINT minute, 
    UINT second);
```
### <a name="description"></a><span data-ttu-id="aa949-1481">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1481">Description</span></span>

<span data-ttu-id="aa949-1482">このサービスは、指定されたファイルの日付と時刻を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1482">This service sets the date and time of the specified file.</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="input-parameters"></a><span data-ttu-id="aa949-1483">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1483">Input Parameters</span></span>

- <span data-ttu-id="aa949-1484">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1484">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-1485">**file_name**: ファイルの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1485">**file_name**: Pointer to name of the file.</span></span>
- <span data-ttu-id="aa949-1486">**year**: 年の値 (1980 から 2107、両端を含む)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1486">**year**: Value of year (1980-2107 inclusive).</span></span>
- <span data-ttu-id="aa949-1487">**month**: 月の値 (1 から 12、両端を含む)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1487">**month**: Value of month (1-12 inclusive).</span></span>
- <span data-ttu-id="aa949-1488">**day**: 日の値 (1 から 31、両端を含む)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1488">**day**: Value of day (1-31 inclusive).</span></span>
- <span data-ttu-id="aa949-1489">**hour**: 時間の値 (0 から 23、両端を含む)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1489">**hour**: Value of hour (0-23 inclusive).</span></span>
- <span data-ttu-id="aa949-1490">**minute**: 分の値 (0 から 59、両端を含む)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1490">**minute**: Value of minute (0-59 inclusive).</span></span>
- <span data-ttu-id="aa949-1491">**second**: 秒の値 (0 から 59、両端を含む)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1491">**second**: Value of second (0-59 inclusive).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1492">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1492">Return Values</span></span>

- <span data-ttu-id="aa949-1493">**FX_SUCCESS** (0x00) 日付/時刻の設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1493">**FX_SUCCESS** (0x00) Successful date/time set.</span></span>
- <span data-ttu-id="aa949-1494">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1494">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-1495">**FX_NOT_FOUND** (0x04) ファイルが見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1495">**FX_NOT_FOUND** (0x04)    File was not found.</span></span>
- <span data-ttu-id="aa949-1496">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1496">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="aa949-1497">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1497">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1498">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1498">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1499">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1499">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1500">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1500">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-1501">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1501">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1502">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1502">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1503">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1503">**FX_PTR_ERROR** (0x18) Invalid media or name pointer.</span></span>
- <span data-ttu-id="aa949-1504">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1504">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="aa949-1505">**FX_INVALID_YEAR** (0x12) 年が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1505">**FX_INVALID_YEAR** (0x12) Year is invalid.</span></span>
- <span data-ttu-id="aa949-1506">**FX_INVALID_MONTH** (0x13) 月が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1506">**FX_INVALID_MONTH** (0x13) Month is invalid.</span></span>
- <span data-ttu-id="aa949-1507">**FX_INVALID_DAY** (0x14) 日が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1507">**FX_INVALID_DAY** (0x14) Day is invalid.</span></span>
- <span data-ttu-id="aa949-1508">**FX_INVALID_HOUR** (0x15) 時間が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1508">**FX_INVALID_HOUR** (0x15)    Hour is invalid.</span></span>
- <span data-ttu-id="aa949-1509">**FX_INVALID_MINUTE** (0x16) 分が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1509">**FX_INVALID_MINUTE** (0x16) Minute is invalid.</span></span>
- <span data-ttu-id="aa949-1510">**FX_INVALID_SECOND** (0x17) 秒が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1510">**FX_INVALID_SECOND** (0x17) Second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1511">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1511">Allowed From</span></span>

<span data-ttu-id="aa949-1512">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1512">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1513">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1513">Example</span></span>

```c

FX_MEDIA         my_media;
/* Set the date/time of "my_file". */
status = fx_file_date_time_set(&my_media, "my_file", 1999, 12, 31, 23, 59, 59);

/* If status is FX_SUCCESS the file's date/time was successfully set. /*
```

### <a name="see-also"></a><span data-ttu-id="aa949-1514">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1514">See Also</span></span>

- <span data-ttu-id="aa949-1515">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1515">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1516">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1516">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1517">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1517">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1518">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1518">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1519">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1519">fx_file_close</span></span>
- <span data-ttu-id="aa949-1520">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1520">fx_file_create</span></span>
- <span data-ttu-id="aa949-1521">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1521">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1522">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1522">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1523">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1523">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1524">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1524">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1525">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1525">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1526">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1526">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1527">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1527">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1528">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1528">fx_file_open</span></span>
- <span data-ttu-id="aa949-1529">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1529">fx_file_read</span></span>
- <span data-ttu-id="aa949-1530">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1530">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1531">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1531">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1532">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1532">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1533">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1533">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1534">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1534">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1535">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1535">fx_file_write</span></span>
- <span data-ttu-id="aa949-1536">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1536">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1537">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1537">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1538">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1538">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1539">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1539">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1540">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1540">fx_unicode_short_name_get</span></span>

## <a name="fx_file_delete"></a><span data-ttu-id="aa949-1541">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1541">fx_file_delete</span></span>

### <a name="deletes-file"></a><span data-ttu-id="aa949-1542">ファイルを削除します</span><span class="sxs-lookup"><span data-stu-id="aa949-1542">Deletes file</span></span>

<span data-ttu-id="aa949-1543">ファイルの削除</span><span class="sxs-lookup"><span data-stu-id="aa949-1543">File Deletion</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1544">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1544">Prototype</span></span>

```c
UINT fx_file_delete(
    FX_MEDIA *media_ptr, 
    CHAR *file_name);
```
### <a name="description"></a><span data-ttu-id="aa949-1545">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1545">Description</span></span>

<span data-ttu-id="aa949-1546">このサービスは、指定されたファイルを削除します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1546">This service deletes the specified file.</span></span>


### <a name="input-parameters"></a><span data-ttu-id="aa949-1547">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1547">Input Parameters</span></span>

- <span data-ttu-id="aa949-1548">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1548">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-1549">**file_name**: 削除するファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1549">**file_name**: Pointer to the name of the file to delete (directory path is optional).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1550">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1550">Return Values</span></span>

- <span data-ttu-id="aa949-1551">**FX_SUCCESS** (0x00) ファイルの削除に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1551">**FX_SUCCESS** (0x00) Successful file delete.</span></span>
- <span data-ttu-id="aa949-1552">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1552">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-1553">**FX_NOT_FOUND** (0x04) 指定されたファイルは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1553">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="aa949-1554">**FX_NOT_A_FILE** (0x05) 指定されたファイル名はディレクトリまたはボリュームでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1554">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="aa949-1555">**FX_ACCESS_ERROR** (0x06) 指定されたファイルは現在開いています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1555">**FX_ACCESS_ERROR** (0x06) Specified file is currently open.</span></span>
- <span data-ttu-id="aa949-1556">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1556">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1557">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1557">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1558">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1558">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1559">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1559">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1560">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1560">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1561">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1561">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1562">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1562">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1563">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-1563">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-1564">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1564">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-1565">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1565">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1566">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1566">Allowed From</span></span>

<span data-ttu-id="aa949-1567">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1567">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1568">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1568">Example</span></span>

```c

FX_MEDIA            my_media;
UINT                 status;
/* Delete the file "myfile.txt". */

status = fx_file_delete(&my_media, "myfile.txt");

/* If status equals FX_SUCCESS, "myfile.txt" has been deleted. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1569">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1569">See Also</span></span>

- <span data-ttu-id="aa949-1570">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1570">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1571">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1571">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1572">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1572">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1573">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1573">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1574">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1574">fx_file_close</span></span>
- <span data-ttu-id="aa949-1575">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1575">fx_file_create</span></span>
- <span data-ttu-id="aa949-1576">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1576">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1577">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1577">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1578">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1578">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1579">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1579">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1580">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1580">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1581">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1581">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1582">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1582">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1583">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1583">fx_file_open</span></span>
- <span data-ttu-id="aa949-1584">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1584">fx_file_read</span></span>
- <span data-ttu-id="aa949-1585">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1585">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1586">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1586">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1587">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1587">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1588">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1588">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1589">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1589">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1590">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1590">fx_file_write</span></span>
- <span data-ttu-id="aa949-1591">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1591">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1592">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1592">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1593">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1593">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1594">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1594">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1595">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1595">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_allocate"></a><span data-ttu-id="aa949-1596">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1596">fx_file_extended_allocate</span></span>

<span data-ttu-id="aa949-1597">ファイルの領域を割り当てます</span><span class="sxs-lookup"><span data-stu-id="aa949-1597">Allocates space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1598">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1598">Prototype</span></span>

```c
UINT fx_file_extended_allocate(
    FX_FILE *file_ptr, 
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="aa949-1599">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1599">Description</span></span>

<span data-ttu-id="aa949-1600">このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1600">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="aa949-1601">FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1601">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="aa949-1602">結果はクラスター数が整数になるように切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1602">The result is then rounded up to the next whole cluster.</span></span>

<span data-ttu-id="aa949-1603">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1603">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-1604">*size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて領域を事前に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1604">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1605">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1605">Input Parameters</span></span>

- <span data-ttu-id="aa949-1606">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1606">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-1607">**size**: ファイルに割り当てるバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-1607">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1608">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1608">Return Values</span></span>

- <span data-ttu-id="aa949-1609">**FX_SUCCESS** (0x00) ファイルの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1609">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="aa949-1610">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1610">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-1611">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1611">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-1612">**FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1612">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="aa949-1613">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1613">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1614">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1614">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1615">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1615">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1616">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1616">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1617">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1617">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1618">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1618">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1619">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1619">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1620">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1620">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1621">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1621">Allowed From</span></span>

<span data-ttu-id="aa949-1622">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1622">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1623">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1623">Example</span></span>

```c

FX_FILE            my_file;
UINT            status;
/* Allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_allocate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS the file now has
    one or more contiguous cluster(s) that can accommodate at least
    1024 bytes of user data. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1624">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1624">See Also</span></span>

- <span data-ttu-id="aa949-1625">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1625">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1626">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1626">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1627">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1627">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1628">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1628">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1629">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1629">fx_file_close</span></span>
- <span data-ttu-id="aa949-1630">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1630">fx_file_create</span></span>
- <span data-ttu-id="aa949-1631">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1631">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1632">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1632">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1633">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1633">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1634">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1634">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1635">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1635">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1636">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1636">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1637">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1637">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1638">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1638">fx_file_open</span></span>
- <span data-ttu-id="aa949-1639">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1639">fx_file_read</span></span>
- <span data-ttu-id="aa949-1640">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1640">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1641">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1641">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1642">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1642">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1643">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1643">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1644">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1644">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1645">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1645">fx_file_write</span></span>
- <span data-ttu-id="aa949-1646">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1646">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1647">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1647">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1648">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1648">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1649">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1649">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1650">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1650">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_best_effort_allocate"></a><span data-ttu-id="aa949-1651">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1651">fx_file_extended_best_effort_allocate</span></span>

<span data-ttu-id="aa949-1652">ファイルの領域をベスト エフォートで割り当てます</span><span class="sxs-lookup"><span data-stu-id="aa949-1652">Best effort to allocate space for a file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1653">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1653">Prototype</span></span>

```c
UINT fx_file_extended best_effort_allocate(
    FX_FILE *file_ptr,
    ULONG64 size,
    ULONG64 *actual_size_allocated);
```
### <a name="description"></a><span data-ttu-id="aa949-1654">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1654">Description</span></span>

<span data-ttu-id="aa949-1655">このサービスは、1 つまたは複数の連続したクラスターを割り当てて、指定されたファイルの末尾にリンクします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1655">This service allocates and links one or more contiguous clusters to the end of the specified file.</span></span> <span data-ttu-id="aa949-1656">FileX は、要求されたサイズをクラスターあたりのバイト数で割ることによって、必要とされるクラスターの数を決定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1656">FileX determines the number of clusters required by dividing the requested size by the number of bytes per cluster.</span></span> <span data-ttu-id="aa949-1657">結果はクラスター数が整数になるように切り上げられます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1657">The result is then rounded up to the next whole cluster.</span></span> <span data-ttu-id="aa949-1658">利用可能な連続するクラスターがメディア内に不足している場合、このサービスでは、利用可能な最大の連続するクラスターのブロックをファイルにリンクします。</span><span class="sxs-lookup"><span data-stu-id="aa949-1658">If there are not enough consecutive clusters available in the media, this service links the largest available block of consecutive clusters to the file.</span></span> <span data-ttu-id="aa949-1659">ファイルに実際に割り当てられた領域の量が呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1659">The amount of space actually allocated to the file is returned to the caller.</span></span>

<span data-ttu-id="aa949-1660">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1660">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-1661">*size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて領域を事前に割り当てることができます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1661">The *size* parameter takes a 64-bit integer value, which allows the caller to pre-allocate space beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1662">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1662">Input Parameters</span></span>

- <span data-ttu-id="aa949-1663">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1663">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-1664">**size**: ファイルに割り当てるバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-1664">**size**: Number of bytes to allocate for the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1665">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1665">Return Values</span></span>

- <span data-ttu-id="aa949-1666">**FX_SUCCESS** (0x00) ファイルの割り当てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1666">**FX_SUCCESS** (0x00) Successful file allocation.</span></span>
- <span data-ttu-id="aa949-1667">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1667">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-1668">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1668">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-1669">**FX_NO_MORE_SPACE** (0x0A) このファイルに関連付けられているメディアには、使用可能なクラスターが不足しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1669">**FX_NO_MORE_SPACE** (0x0A) Media associated with this file does not have enough available clusters.</span></span>
- <span data-ttu-id="aa949-1670">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1670">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1671">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1671">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1672">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1672">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1673">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1673">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1674">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1674">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1675">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1675">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1676">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1676">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1677">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1677">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1678">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1678">Allowed From</span></span>

<span data-ttu-id="aa949-1679">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1679">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1680">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1680">Example</span></span>

```c

FX_FILE my_file;
UINT             status;
ULONG64         actual_allocation;

/* Attempt to allocate 0x100000000 bytes to the end of my_file. */

status = fx_file_extended_best_effort_allocate(&my_file,
    0x100000000, &actual_allocation);

/* If status equals FX_SUCCESS, the number of bytes
    allocated to the file is found in actual_allocation. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1681">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1681">See Also</span></span>

- <span data-ttu-id="aa949-1682">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1682">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1683">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1683">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1684">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1684">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1685">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1685">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1686">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1686">fx_file_close</span></span>
- <span data-ttu-id="aa949-1687">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1687">fx_file_create</span></span>
- <span data-ttu-id="aa949-1688">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1688">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1689">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1689">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1690">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1690">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1691">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1691">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1692">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1692">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1693">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1693">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1694">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1694">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1695">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1695">fx_file_open</span></span>
- <span data-ttu-id="aa949-1696">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1696">fx_file_read</span></span>
- <span data-ttu-id="aa949-1697">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1697">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1698">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1698">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1699">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1699">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1700">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1700">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1701">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1701">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1702">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1702">fx_file_write</span></span>
- <span data-ttu-id="aa949-1703">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1703">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1704">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1704">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1705">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1705">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1706">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1706">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1707">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1707">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_relative_seek"></a><span data-ttu-id="aa949-1708">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1708">fx_file_extended_relative_seek</span></span>

<span data-ttu-id="aa949-1709">相対バイト オフセットに配置します</span><span class="sxs-lookup"><span data-stu-id="aa949-1709">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1710">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1710">Prototype</span></span>

```c
UINT fx_file_extended_relative_seek(
    FX_FILE *file_ptr,
    ULONG64 byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="aa949-1711">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1711">Description</span></span>

<span data-ttu-id="aa949-1712">このサービスは、指定された相対バイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1712">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="aa949-1713">それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1713">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="aa949-1714">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1714">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-1715">*byte_offset* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は読み取り/書き込みポインターを 4 GB の範囲を超えて再配置できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1715">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-1716">*シーク操作がファイルの末尾を越えてシークしようとすると、ファイルの読み取り/書き込みポインターはファイルの末尾に配置されます。逆に、シーク操作によってファイルの先頭を越える位置に移動しようとすると、ファイルの読み取り/書き込みポインターはファイルの先頭に配置されます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-1716">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1717">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1717">Input Parameters</span></span>

- <span data-ttu-id="aa949-1718">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1718">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-1719">**byte_offset**: ファイル内の目標の相対バイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="aa949-1719">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="aa949-1720">**seek_from**: 相対シークの実行元の方向と位置。</span><span class="sxs-lookup"><span data-stu-id="aa949-1720">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="aa949-1721">有効なシーク オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1721">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="aa949-1722">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="aa949-1722">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="aa949-1723">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-1723">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="aa949-1724">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-1724">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="aa949-1725">FX_SEEK_BACK (0x03) FX_SEEK_BEGIN を指定した場合、シーク操作はファイルの先頭から実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1725">FX_SEEK_BACK (0x03) If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="aa949-1726">FX_SEEK_END を指定した場合、シーク操作はファイルの末尾からさかのぼって実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1726">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="aa949-1727">FX_SEEK_FORWARD を指定した場合、シーク操作は現在のファイルの位置から順に実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1727">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="aa949-1728">FX_SEEK_BACK を指定した場合、シーク操作は現在のファイルの位置からさかのぼって実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1728">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1729">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1729">Return Values</span></span>

- <span data-ttu-id="aa949-1730">**FX_SUCCESS** (0x00) ファイルの相対シークに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1730">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="aa949-1731">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1731">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-1732">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1732">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1733">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1733">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1734">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1734">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1735">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1735">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1736">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1736">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1737">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1737">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1738">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1738">Allowed From</span></span>

<span data-ttu-id="aa949-1739">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1739">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1740">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1740">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to seek forward 0x100000000 bytes in "my_file". */

status = fx_file_extended_relative_seek(&my_file, 0x100000000, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write
    pointers are positioned 0x100000000 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1741">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1741">See Also</span></span>

- <span data-ttu-id="aa949-1742">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1742">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1743">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1743">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1744">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1744">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1745">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1745">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1746">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1746">fx_file_close</span></span>
- <span data-ttu-id="aa949-1747">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1747">fx_file_create</span></span>
- <span data-ttu-id="aa949-1748">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1748">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1749">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1749">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1750">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1750">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1751">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1751">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1752">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1752">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1753">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1753">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1754">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1754">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1755">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1755">fx_file_open</span></span>
- <span data-ttu-id="aa949-1756">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1756">fx_file_read</span></span>
- <span data-ttu-id="aa949-1757">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1757">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1758">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1758">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1759">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1759">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1760">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1760">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1761">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1761">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1762">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1762">fx_file_write</span></span>
- <span data-ttu-id="aa949-1763">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1763">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1764">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1764">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1765">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1765">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1766">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1766">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1767">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1767">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_seek"></a><span data-ttu-id="aa949-1768">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1768">fx_file_extended_seek</span></span>

<span data-ttu-id="aa949-1769">バイト オフセットに配置します</span><span class="sxs-lookup"><span data-stu-id="aa949-1769">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1770">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1770">Prototype</span></span>

```c
UINT fx_file_extended_seek(
    FX_FILE *file_ptr, 
    ULONG64 byte_offset);
```
### <a name="description"></a><span data-ttu-id="aa949-1771">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1771">Description</span></span>

<span data-ttu-id="aa949-1772">このサービスは、指定されたバイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1772">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="aa949-1773">それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1773">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="aa949-1774">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1774">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-1775">*byte_offset* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は読み取り/書き込みポインターを 4 GB の範囲を超えて再配置できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1775">The *byte_offset* parameter takes a 64bit integer value, which allows the caller to reposition the read/write pointer beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1776">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1776">Input Parameters</span></span>

- <span data-ttu-id="aa949-1777">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1777">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-1778">**byte_offset**: ファイル内の目標のバイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="aa949-1778">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="aa949-1779">値を 0 にすると、読み取り/書き込みポインターがファイルの先頭に配置され、ファイルのサイズより大きい値にすると、読み取り/書き込みポインターがファイルの末尾に配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1779">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1780">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1780">Return Values</span></span>

- <span data-ttu-id="aa949-1781">**FX_SUCCESS** (0x00) ファイルのシークに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1781">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="aa949-1782">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1782">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-1783">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1783">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1784">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1784">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1785">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1785">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1786">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1786">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1787">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1787">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1788">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1788">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1789">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1789">Allowed From</span></span>

<span data-ttu-id="aa949-1790">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1790">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1791">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1791">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;
/* Seek to position 0x100000000 of "my_file." */

status = fx_file_extended_seek(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned 0x100000000 bytes from the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1792">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1792">See Also</span></span>

- <span data-ttu-id="aa949-1793">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1793">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1794">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1794">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1795">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1795">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1796">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1796">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1797">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1797">fx_file_close</span></span>
- <span data-ttu-id="aa949-1798">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1798">fx_file_create</span></span>
- <span data-ttu-id="aa949-1799">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1799">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1800">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1800">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1801">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1801">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1802">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1802">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1803">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1803">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1804">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1804">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1805">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1805">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1806">fx_file_open- fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1806">fx_file_open- fx_file_read</span></span>
- <span data-ttu-id="aa949-1807">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1807">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1808">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1808">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1809">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1809">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1810">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1810">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1811">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1811">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1812">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1812">fx_file_write</span></span>
- <span data-ttu-id="aa949-1813">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1813">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1814">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1814">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1815">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1815">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1816">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1816">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1817">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1817">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate"></a><span data-ttu-id="aa949-1818">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1818">fx_file_extended_truncate</span></span>

<span data-ttu-id="aa949-1819">ファイルを切り捨てます</span><span class="sxs-lookup"><span data-stu-id="aa949-1819">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1820">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1820">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG64 size);
```
### <a name="description"></a><span data-ttu-id="aa949-1821">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1821">Description</span></span>

<span data-ttu-id="aa949-1822">このサービスは、指定されたサイズにファイルのサイズを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1822">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="aa949-1823">指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1823">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="aa949-1824">ファイルに関連付けられているメディア クラスターは解放されません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1824">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-1825">*読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-1825">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="aa949-1826">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1826">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-1827">*size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて動作できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1827">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1828">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1828">Input Parameters</span></span>

- <span data-ttu-id="aa949-1829">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1829">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-1830">**size**: 新しいファイル サイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-1830">**size**: New file size.</span></span> <span data-ttu-id="aa949-1831">この新しいファイル サイズを超えるバイトは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1831">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1832">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1832">Return Values</span></span>

- <span data-ttu-id="aa949-1833">**FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1833">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="aa949-1834">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1834">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-1835">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1835">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-1836">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1836">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1837">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1837">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1838">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1838">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1839">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1839">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1840">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1840">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1841">**FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1841">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="aa949-1842">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1842">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1843">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1843">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1844">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1844">Allowed From</span></span>

<span data-ttu-id="aa949-1845">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1845">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1846">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1846">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Truncate "my_file" to 0x100000000 bytes. */

status = fx_file_extended_truncate(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, "my_file" contains 0x100000000 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1847">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1847">See Also</span></span>

- <span data-ttu-id="aa949-1848">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1848">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1849">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1849">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1850">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1850">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1851">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1851">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1852">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1852">fx_file_close</span></span>
- <span data-ttu-id="aa949-1853">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1853">fx_file_create</span></span>
- <span data-ttu-id="aa949-1854">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1854">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1855">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1855">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1856">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1856">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1857">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1857">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1858">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1858">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1859">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1859">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1860">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1860">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1861">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1861">fx_file_open</span></span>
- <span data-ttu-id="aa949-1862">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1862">fx_file_read</span></span>
- <span data-ttu-id="aa949-1863">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1863">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1864">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1864">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1865">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1865">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1866">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1866">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1867">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1867">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1868">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1868">fx_file_write</span></span>
- <span data-ttu-id="aa949-1869">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1869">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1870">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1870">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1871">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1871">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1872">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1872">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1873">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1873">fx_unicode_short_name_get</span></span>

## <a name="fx_file_extended_truncate_release"></a><span data-ttu-id="aa949-1874">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1874">fx_file_extended_truncate_release</span></span>

<span data-ttu-id="aa949-1875">ファイルを切り捨ててクラスターを解放します</span><span class="sxs-lookup"><span data-stu-id="aa949-1875">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1876">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1876">Prototype</span></span>

```c
UINT fx_file_extended_truncate_release(
    FX_FILE *file_ptr, 
    ULONG64 size);
```

### <a name="description"></a><span data-ttu-id="aa949-1877">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1877">Description</span></span>

<span data-ttu-id="aa949-1878">このサービスは、指定されたサイズにファイルのサイズを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1878">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="aa949-1879">指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1879">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="aa949-1880">***fx_file_extended_truncate*** サービスとは異なり、このサービスでは未使用のクラスターが解放されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1880">Unlike the ***fx_file_extended_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-1881">*読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-1881">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="aa949-1882">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1882">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-1883">*size* パラメーターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB の範囲を超えて動作できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1883">The *size* parameter takes a 64-bit integer value, which allows the caller to operate beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1884">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1884">Input Parameters</span></span>

- <span data-ttu-id="aa949-1885">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1885">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-1886">**size**: 新しいファイル サイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-1886">**size**: New file size.</span></span> <span data-ttu-id="aa949-1887">この新しいファイル サイズを超えるバイトは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1887">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1888">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1888">Return Values</span></span>

- <span data-ttu-id="aa949-1889">**FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1889">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="aa949-1890">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1890">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-1891">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1891">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-1892">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1892">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1893">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1893">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-1894">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1894">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1895">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1895">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-1896">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1896">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1897">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1897">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1898">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1898">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-1899">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1899">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-1900">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1900">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1901">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1901">Allowed From</span></span>

<span data-ttu-id="aa949-1902">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1902">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1903">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1903">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Attempt to truncate everything after the first 0x100000000 bytes of "my_file". */

status = fx_file_extended_truncate_release(&my_file, 0x100000000);

/* If status equals FX_SUCCESS, the file is now 0x100000000
    bytes or fewer and all unused clusters have been released. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1904">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1904">See Also</span></span>

- <span data-ttu-id="aa949-1905">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1905">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1906">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1906">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1907">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1907">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1908">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1908">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1909">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-1909">fx_file_close</span></span>
- <span data-ttu-id="aa949-1910">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1910">fx_file_create</span></span>
- <span data-ttu-id="aa949-1911">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1911">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1912">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1912">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1913">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1913">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1914">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1914">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1915">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1915">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1916">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1916">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1917">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1917">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1918">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1918">fx_file_open</span></span>
- <span data-ttu-id="aa949-1919">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1919">fx_file_read</span></span>
- <span data-ttu-id="aa949-1920">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1920">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1921">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1921">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1922">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1922">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1923">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1923">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1924">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1924">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1925">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1925">fx_file_write</span></span>
- <span data-ttu-id="aa949-1926">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1926">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1927">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1927">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1928">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1928">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1929">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1929">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1930">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1930">fx_unicode_short_name_get</span></span>

## <a name="fx_file_open"></a><span data-ttu-id="aa949-1931">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-1931">fx_file_open</span></span>

<span data-ttu-id="aa949-1932">ファイルを開きます</span><span class="sxs-lookup"><span data-stu-id="aa949-1932">Opens file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1933">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1933">Prototype</span></span>

```c
UINT fx_file_open(
    FX_MEDIA *media_ptr,
    FX_FILE *file_ptr,
    CHAR *file_name,
    UINT open_type);
```
### <a name="description"></a><span data-ttu-id="aa949-1934">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1934">Description</span></span>

<span data-ttu-id="aa949-1935">このサービスは、指定されたファイルを読み取りまたは書き込み用に開きます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1935">This service opens the specified file for either reading or writing.</span></span> <span data-ttu-id="aa949-1936">ファイルは、読み取り用には複数回開くことができますが、書き込み用には、書き込み側がファイルを閉じるまで 1 回だけ開くことができます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1936">A file may be opened for reading multiple times, while a file can only be opened for writing once until the writer closes the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-1937">*ファイルを読み取りと書き込み用に同時に開いている場合は、注意が必要です。読み取り用にファイルを開くのと同時に実行されたファイルの書き込みは、読み取り側がファイルを閉じて再度読み取り用に開かない限り、読み取り側に表示されない場合があります。同様に、ファイルの書き込み側はファイルの切り捨てサービスを使用する場合に注意する必要があります。ファイルが書き込み側によって切り捨てられた場合、同じファイルの読み取り側が無効なデータを返す可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-1937">*Care must be taken if a file is concurrently open for reading and writing. File writing performed when a file is simultaneously opened for reading may not be seen by the reader, unless the reader closes and reopens the file for reading. Similarly, the file writer should be careful when using file truncate services. If a file is truncated by the writer, readers of the same file could return invalid data.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-1938">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-1938">Input Parameters</span></span>

- <span data-ttu-id="aa949-1939">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1939">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-1940">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1940">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-1941">**file_name**: 開くファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-1941">**file_name**: Pointer to the name of the file to open (directory path is optional).</span></span>
- <span data-ttu-id="aa949-1942">**open_type**: ファイルのオープンの型。</span><span class="sxs-lookup"><span data-stu-id="aa949-1942">**open_type**: Type of file open.</span></span> <span data-ttu-id="aa949-1943">オープンの型の有効なオプションは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa949-1943">Valid open type options are:</span></span>
  - <span data-ttu-id="aa949-1944">FX_OPEN_FOR_READ (0x00)</span><span class="sxs-lookup"><span data-stu-id="aa949-1944">FX_OPEN_FOR_READ (0x00)</span></span>
  - <span data-ttu-id="aa949-1945">FX_OPEN_FOR_WRITE (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-1945">FX_OPEN_FOR_WRITE (0x01)</span></span>
  - <span data-ttu-id="aa949-1946">FX_OPEN_FOR_READ_FAST (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-1946">FX_OPEN_FOR_READ_FAST (0x02)</span></span>

<span data-ttu-id="aa949-1947">FX_OPEN_FOR_READ および FX_OPEN_FOR_READ_FAST でのファイルのオープンは類似しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1947">Opening files with FX_OPEN_FOR_READ and FX_OPEN_FOR_READ_FAST is similar:</span></span>

- <span data-ttu-id="aa949-1948">FX_OPEN_FOR_READ では、ファイルを構成するクラスターのリンクされたリストが破損していないことを検査します。 FX_OPEN_FOR_READ_FAST では、この検査が行われないため、処理が高速になります。</span><span class="sxs-lookup"><span data-stu-id="aa949-1948">FX_OPEN_FOR_READ includes verification that the linked-list of clusters that comprise the file are intact, and FX_OPEN_FOR_READ_FAST does not perform this verification, which makes it faster.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-1949">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-1949">Return Values</span></span>

- <span data-ttu-id="aa949-1950">**FX_SUCCESS** (0x00) ファイルのオープンに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-1950">**FX_SUCCESS** (0x00) Successful file open.</span></span>
- <span data-ttu-id="aa949-1951">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1951">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-1952">**FX_NOT_FOUND** (0x04) 指定されたファイルは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1952">**FX_NOT_FOUND** (0x04) Specified file was not found.</span></span>
- <span data-ttu-id="aa949-1953">**FX_NOT_A_FILE** (0x05) 指定されたファイル名はディレクトリまたはボリュームでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1953">**FX_NOT_A_FILE** (0x05) Specified file name was a directory or volume.</span></span>
- <span data-ttu-id="aa949-1954">**FX_FILE_CORRUPT** (0x08) 指定されたファイルが壊れており、開けませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-1954">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the open failed.</span></span>
- <span data-ttu-id="aa949-1955">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが既に開いているか、オープンの型が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-1955">**FX_ACCESS_ERROR** (0x06) Specified file is already open or open type is invalid.</span></span>
- <span data-ttu-id="aa949-1956">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1956">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-1957">**FX_MEDIA_INVALID** (0x02) 無効なメディア。</span><span class="sxs-lookup"><span data-stu-id="aa949-1957">**FX_MEDIA_INVALID** (0x02) Invalid media.</span></span>
- <span data-ttu-id="aa949-1958">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1958">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-1959">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-1959">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-1960">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-1960">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-1961">**FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-1961">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="aa949-1962">**FX_PTR_ERROR** (0x18) 無効なメディアまたはファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-1962">**FX_PTR_ERROR** (0x18) Invalid media or file pointer.</span></span>
- <span data-ttu-id="aa949-1963">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-1963">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-1964">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-1964">Allowed From</span></span>

<span data-ttu-id="aa949-1965">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-1965">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-1966">例</span><span class="sxs-lookup"><span data-stu-id="aa949-1966">Example</span></span>

```c
FX_MEDIA     my_media;
FX_FILE     my_file;
UINT         status;

/* Open the file "myfile.txt" for reading. */

status = fx_file_open(&my_media, &my_file, "myfile.txt", FX_OPEN_FOR_READ);

/* If status equals FX_SUCCESS, file "myfile.txt" is now
    open and may be accessed now with the my_file pointer. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-1967">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-1967">See Also</span></span>

- <span data-ttu-id="aa949-1968">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1968">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-1969">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1969">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-1970">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1970">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-1971">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1971">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1972">fx_file_close- fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1972">fx_file_close- fx_file_create</span></span>
- <span data-ttu-id="aa949-1973">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1973">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-1974">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-1974">fx_file_delete</span></span>
- <span data-ttu-id="aa949-1975">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1975">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-1976">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-1976">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-1977">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1977">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-1978">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1978">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-1979">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1979">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-1980">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1980">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-1981">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1981">fx_file_read</span></span>
- <span data-ttu-id="aa949-1982">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1982">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-1983">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1983">fx_file_rename</span></span>
- <span data-ttu-id="aa949-1984">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-1984">fx_file_seek</span></span>
- <span data-ttu-id="aa949-1985">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-1985">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-1986">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-1986">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-1987">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-1987">fx_file_write</span></span>
- <span data-ttu-id="aa949-1988">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-1988">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-1989">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-1989">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-1990">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-1990">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-1991">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1991">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-1992">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-1992">fx_unicode_short_name_get</span></span>

## <a name="fx_file_read"></a><span data-ttu-id="aa949-1993">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-1993">fx_file_read</span></span>

<span data-ttu-id="aa949-1994">ファイルからバイトを読み取ります</span><span class="sxs-lookup"><span data-stu-id="aa949-1994">Reads bytes from file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-1995">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-1995">Prototype</span></span>

```c
UINT fx_file_read(
    FX_FILE *file_ptr, 
    VOID *buffer_ptr,
    ULONG request_size, 
    ULONG *actual_size);
```
### <a name="description"></a><span data-ttu-id="aa949-1996">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-1996">Description</span></span>

<span data-ttu-id="aa949-1997">このサービスは、ファイルからバイトを読み取り、指定されたバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="aa949-1997">This service reads bytes from the file and stores them in the supplied buffer.</span></span> <span data-ttu-id="aa949-1998">読み取りが完了すると、ファイルの内部読み取りポインターは、ファイル内の次のバイトを指すように調整されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1998">After the read is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span> <span data-ttu-id="aa949-1999">要求に残っているバイトが少ない場合、残っているバイトだけがバッファーに格納されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-1999">If there are fewer bytes remaining in the request, only the bytes remaining are stored in the buffer.</span></span> <span data-ttu-id="aa949-2000">いずれの場合も、バッファーに配置されたバイトの総数が、呼び出し元に返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2000">In any case, the total number of bytes placed in the buffer is returned to the caller.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2001">*アプリケーションでは、指定されたバッファーが、指定された数の要求バイトを格納できるようにする必要があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2001">*The application must ensure that the buffer supplied is able to store the specified number of requested bytes.*</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2002">*宛先バッファーが長いワード境界にあり、要求されたサイズが sizeof (**ULONG**) で均等に割り切れる場合、パフォーマンスが向上します。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2002">*Faster performance is achieved if the destination buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2003">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2003">Input Parameters</span></span>

- <span data-ttu-id="aa949-2004">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2004">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-2005">**buffer_ptr**: 読み取り用の宛先バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2005">**buffer_ptr**: Pointer to the destination buffer for the read.</span></span>
- <span data-ttu-id="aa949-2006">**request_size**: 読み取る最大バイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2006">**request_size**: Maximum number of bytes to read.</span></span>
- <span data-ttu-id="aa949-2007">**actual_size**: 指定されたバッファーに読み取られた実際のバイト数を保持する変数へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2007">**actual_size**: Pointer to the variable to hold the actual number of bytes read into the supplied buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2008">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2008">Return Values</span></span>

- <span data-ttu-id="aa949-2009">**FX_SUCCESS** (0x00) ファイルの読み取りに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2009">**FX_SUCCESS** (0x00) Successful file read.</span></span>
- <span data-ttu-id="aa949-2010">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2010">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-2011">**FX_FILE_CORRUPT** (0x08) 指定されたファイルが壊れており、読み取れませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-2011">**FX_FILE_CORRUPT** (0x08) Specified file is corrupt and the read failed.</span></span>
- <span data-ttu-id="aa949-2012">**FX_END_OF_FILE** (0x09) ファイルの終わりに達しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2012">**FX_END_OF_FILE** (0x09) End of file has been reached.</span></span>
- <span data-ttu-id="aa949-2013">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2013">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2014">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-2014">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-2015">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2015">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2016">**FX_PTR_ERROR** (0x18) 無効なファイルまたはバッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2016">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="aa949-2017">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2017">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2018">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2018">Allowed From</span></span>

<span data-ttu-id="aa949-2019">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2019">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2020">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2020">Example</span></span>

```c
FX_FILE                 my_file;
unsigned char           my_buffer[1024];
ULONG                   actual_bytes;
UINT                    status;

/* Read up to 1024 bytes into "my_buffer." */
status = fx_file_read(&my_file, my_buffer, 1024, &actual_bytes);

/* If status equals FX_SUCCESS, "my_buffer" contains the bytes
    read from the file. The total number of bytes read is in "actual_bytes." */
```
### <a name="see-also"></a><span data-ttu-id="aa949-2021">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2021">See Also</span></span>

- <span data-ttu-id="aa949-2022">fx_file_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2022">fx_file_allocate,</span></span>
- <span data-ttu-id="aa949-2023">fx_file_attributes_read、</span><span class="sxs-lookup"><span data-stu-id="aa949-2023">fx_file_attributes_read,</span></span>
- <span data-ttu-id="aa949-2024">fx_file_attributes_set、</span><span class="sxs-lookup"><span data-stu-id="aa949-2024">fx_file_attributes_set,</span></span>
- <span data-ttu-id="aa949-2025">fx_file_best_effort_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2025">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="aa949-2026">fx_file_close、</span><span class="sxs-lookup"><span data-stu-id="aa949-2026">fx_file_close,</span></span>
- <span data-ttu-id="aa949-2027">fx_file_create、</span><span class="sxs-lookup"><span data-stu-id="aa949-2027">fx_file_create,</span></span>
- <span data-ttu-id="aa949-2028">fx_file_date_time_set、</span><span class="sxs-lookup"><span data-stu-id="aa949-2028">fx_file_date_time_set,</span></span>
- <span data-ttu-id="aa949-2029">fx_file_delete、</span><span class="sxs-lookup"><span data-stu-id="aa949-2029">fx_file_delete,</span></span>
- <span data-ttu-id="aa949-2030">fx_file_extended_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2030">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="aa949-2031">fx_file_extended_best_effort_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2031">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="aa949-2032">fx_file_extended_relative_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2032">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="aa949-2033">fx_file_extended_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2033">fx_file_extended_seek,</span></span>
- <span data-ttu-id="aa949-2034">fx_file_extended_truncate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2034">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="aa949-2035">fx_file_extended_truncate_release、</span><span class="sxs-lookup"><span data-stu-id="aa949-2035">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="aa949-2036">fx_file_open、</span><span class="sxs-lookup"><span data-stu-id="aa949-2036">fx_file_open,</span></span>
- <span data-ttu-id="aa949-2037">fx_file_relative_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2037">fx_file_relative_seek,</span></span>
- <span data-ttu-id="aa949-2038">fx_file_rename、</span><span class="sxs-lookup"><span data-stu-id="aa949-2038">fx_file_rename,</span></span>
- <span data-ttu-id="aa949-2039">fx_file_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2039">fx_file_seek,</span></span>
- <span data-ttu-id="aa949-2040">fx_file_truncate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2040">fx_file_truncate,</span></span>
- <span data-ttu-id="aa949-2041">fx_file_truncate_release、</span><span class="sxs-lookup"><span data-stu-id="aa949-2041">fx_file_truncate_release,</span></span>
- <span data-ttu-id="aa949-2042">fx_file_write、</span><span class="sxs-lookup"><span data-stu-id="aa949-2042">fx_file_write,</span></span>
- <span data-ttu-id="aa949-2043">fx_file_write_notify_set、</span><span class="sxs-lookup"><span data-stu-id="aa949-2043">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="aa949-2044">fx_unicode_file_create、</span><span class="sxs-lookup"><span data-stu-id="aa949-2044">fx_unicode_file_create,</span></span>
- <span data-ttu-id="aa949-2045">fx_unicode_file_rename、</span><span class="sxs-lookup"><span data-stu-id="aa949-2045">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="aa949-2046">fx_unicode_name_get、</span><span class="sxs-lookup"><span data-stu-id="aa949-2046">fx_unicode_name_get,</span></span>
- <span data-ttu-id="aa949-2047">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2047">fx_unicode_short_name_get</span></span>

## <a name="fx_file_relative_seek"></a><span data-ttu-id="aa949-2048">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2048">fx_file_relative_seek</span></span>

<span data-ttu-id="aa949-2049">相対バイト オフセットに配置します</span><span class="sxs-lookup"><span data-stu-id="aa949-2049">Positions to a relative byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2050">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2050">Prototype</span></span>

```c
UINT fx_file_relative_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset,
    UINT seek_from);
```
### <a name="description"></a><span data-ttu-id="aa949-2051">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2051">Description</span></span>

<span data-ttu-id="aa949-2052">このサービスは、指定された相対バイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2052">This service positions the internal file read/write pointer to the specified relative byte offset.</span></span> <span data-ttu-id="aa949-2053">それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2053">Any subsequent file read or write request will begin at this location in the file.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-2054">*シーク操作がファイルの末尾を越えてシークしようとすると、ファイルの読み取り/書き込みポインターはファイルの末尾に配置されます。逆に、シーク操作によってファイルの先頭を越える位置に移動しようとすると、ファイルの読み取り/書き込みポインターはファイルの先頭に配置されます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2054">*If the seek operation attempts to seek past the end of the file, the file's read/write pointer is positioned to the end of the file. Conversely, if the seek operation attempts to position past the beginning of the file, the file's read/write pointer is positioned to the beginning of the file.*</span></span>

<span data-ttu-id="aa949-2055">4 GB を超えるオフセット値を使用してシークするには、アプリケーションでサービス *fx_file_extended_relative_seek* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2055">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_relative_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2056">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2056">Input Parameters</span></span>

- <span data-ttu-id="aa949-2057">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2057">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-2058">**byte_offset**: ファイル内の目標の相対バイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="aa949-2058">**byte_offset**: Desired relative byte offset in file.</span></span>
- <span data-ttu-id="aa949-2059">**seek_from**: 相対シークの実行元の方向と位置。</span><span class="sxs-lookup"><span data-stu-id="aa949-2059">**seek_from**: The direction and location of where to perform the relative seek from.</span></span> <span data-ttu-id="aa949-2060">有効なシーク オプションは次のように定義されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2060">Valid seek options are defined as follows:</span></span>
  - <span data-ttu-id="aa949-2061">FX_SEEK_BEGIN (0x00)</span><span class="sxs-lookup"><span data-stu-id="aa949-2061">FX_SEEK_BEGIN (0x00)</span></span>
  - <span data-ttu-id="aa949-2062">FX_SEEK_END (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-2062">FX_SEEK_END (0x01)</span></span>
  - <span data-ttu-id="aa949-2063">FX_SEEK_FORWARD (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-2063">FX_SEEK_FORWARD (0x02)</span></span>
  - <span data-ttu-id="aa949-2064">FX_SEEK_BACK (0x03)</span><span class="sxs-lookup"><span data-stu-id="aa949-2064">FX_SEEK_BACK (0x03)</span></span>

<span data-ttu-id="aa949-2065">FX_SEEK_BEGIN を指定した場合、シーク操作はファイルの先頭から実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2065">If FX_SEEK_BEGIN is specified, the seek operation is performed from the beginning of the file.</span></span> <span data-ttu-id="aa949-2066">FX_SEEK_END を指定した場合、シーク操作はファイルの末尾からさかのぼって実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2066">If FX_SEEK_END is specified the seek operation is performed backward from the end of the file.</span></span> <span data-ttu-id="aa949-2067">FX_SEEK_FORWARD を指定した場合、シーク操作は現在のファイルの位置から順に実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2067">If FX_SEEK_FORWARD is specified, the seek operation is performed forward from the current file position.</span></span> <span data-ttu-id="aa949-2068">FX_SEEK_BACK を指定した場合、シーク操作は現在のファイルの位置からさかのぼって実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2068">If FX_SEEK_BACK is specified, the seek operation is performed backward from the current file position.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2069">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2069">Return Values</span></span>

- <span data-ttu-id="aa949-2070">**FX_SUCCESS** (0x00) ファイルの相対シークに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2070">**FX_SUCCESS** (0x00) Successful file relative seek.</span></span>
- <span data-ttu-id="aa949-2071">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2071">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-2072">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2072">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2073">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2073">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2074">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2074">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2075">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2075">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-2076">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2076">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-2077">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2077">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2078">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2078">Allowed From</span></span>

<span data-ttu-id="aa949-2079">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2079">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2080">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2080">Example</span></span>

```c
FX_FILE     my_file;
UINT         status;

/* Attempt to move 10 bytes forward in "my_file". */

status = fx_file_relative_seek(&my_file, 10, FX_SEEK_FORWARD);

/* If status equals FX_SUCCESS, the file read/write pointers
    are positioned 10 bytes forward. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-2081">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2081">See Also</span></span>

- <span data-ttu-id="aa949-2082">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2082">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-2083">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2083">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-2084">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2084">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-2085">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2085">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2086">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2086">fx_file_close</span></span>
- <span data-ttu-id="aa949-2087">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2087">fx_file_create</span></span>
- <span data-ttu-id="aa949-2088">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2088">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-2089">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-2089">fx_file_delete</span></span>
- <span data-ttu-id="aa949-2090">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2090">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-2091">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2091">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2092">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2092">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-2093">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2093">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-2094">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2094">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-2095">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2095">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-2096">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2096">fx_file_open</span></span>
- <span data-ttu-id="aa949-2097">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2097">fx_file_read</span></span>
- <span data-ttu-id="aa949-2098">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2098">fx_file_rename</span></span>
- <span data-ttu-id="aa949-2099">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2099">fx_file_seek</span></span>
- <span data-ttu-id="aa949-2100">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2100">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-2101">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2101">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-2102">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2102">fx_file_write</span></span>
- <span data-ttu-id="aa949-2103">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2103">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-2104">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2104">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-2105">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2105">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-2106">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2106">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-2107">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2107">fx_unicode_short_name_get</span></span>

## <a name="fx_file_rename"></a><span data-ttu-id="aa949-2108">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2108">fx_file_rename</span></span>

<span data-ttu-id="aa949-2109">ファイルの名前を変更します</span><span class="sxs-lookup"><span data-stu-id="aa949-2109">Renames  file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2110">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2110">Prototype</span></span>

```c
UINT fx_file_rename(
    FX_MEDIA *media_ptr,
    CHAR *old_file_name,
    CHAR *new_file_name);
```
### <a name="description"></a><span data-ttu-id="aa949-2111">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2111">Description</span></span>

<span data-ttu-id="aa949-2112">このサービスは、*old_file_name* によって指定されたファイルの名前を変更します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2112">This service changes the name of the file specified by *old_file_name*.</span></span> <span data-ttu-id="aa949-2113">名前の変更は、指定されたパスまたはデフォルト パスに対しても実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2113">Renaming is also done relative to the specified path or the default path.</span></span> <span data-ttu-id="aa949-2114">新しいファイル名にパスが指定されている場合、名前が変更されたファイルは指定したパスに事実上移動します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2114">If a path is specified in the new file name, the renamed file is effectively moved to the specified path.</span></span> <span data-ttu-id="aa949-2115">パスが指定されていない場合、名前が変更されたファイルは現在のデフォルト パスに配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2115">If no path is specified, the renamed file is placed in the current default path.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2116">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2116">Input Parameters</span></span>

- <span data-ttu-id="aa949-2117">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2117">**media_ptr**: Pointer to a media control block.</span></span>
- <span data-ttu-id="aa949-2118">**old_file_name**: 名前を変更するファイルの名前を指すポインター (ディレクトリ パスは省略可能です)。</span><span class="sxs-lookup"><span data-stu-id="aa949-2118">**old_file_name**: Pointer to the name of the file to rename (directory path is optional).</span></span>
- <span data-ttu-id="aa949-2119">**new_file_name**: 新しいファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2119">**new_file_name**: Pointer to the new file name.</span></span> <span data-ttu-id="aa949-2120">ディレクトリ パスは許可されていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2120">The directory path is not allowed.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2121">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2121">Return Values</span></span>

- <span data-ttu-id="aa949-2122">**FX_SUCCESS** (0x00) ファイルの名前変更に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2122">**FX_SUCCESS** (0x00) Successful file rename.</span></span>
- <span data-ttu-id="aa949-2123">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2123">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2124">**FX_NOT_FOUND** (0x04) 指定されたファイルは見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-2124">**FX_NOT_FOUND** (0x04)    Specified file was not found.</span></span>
- <span data-ttu-id="aa949-2125">**FX_NOT_A_FILE** (0x05) 指定されたファイルはディレクトリです。</span><span class="sxs-lookup"><span data-stu-id="aa949-2125">**FX_NOT_A_FILE** (0x05) Specified file is a directory.</span></span>
- <span data-ttu-id="aa949-2126">**FX_ACCESS_ERROR** (0x06) 指定されたファイルは既に開いています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2126">**FX_ACCESS_ERROR** (0x06) Specified file is already open.</span></span>
- <span data-ttu-id="aa949-2127">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2127">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2128">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2128">**FX_WRITE_PROTECT** (0x23)    Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-2129">**FX_INVALID_NAME** (0x0C) 指定された新しいファイル名は有効なファイル名ではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2129">**FX_INVALID_NAME** (0x0C) Specified new file name is not a valid file name.</span></span>
- <span data-ttu-id="aa949-2130">**FX_INVALID_PATH** (0x0D) パスが無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2130">**FX_INVALID_PATH** (0x0D)    Path is invalid.</span></span>
- <span data-ttu-id="aa949-2131">**FX_ALREADY_CREATED** (0x0B) 新しいファイル名は使用されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2131">**FX_ALREADY_CREATED** (0x0B) The new file name is used.</span></span>
- <span data-ttu-id="aa949-2132">**FX_MEDIA_INVALID** (0x02) メディアが無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2132">**FX_MEDIA_INVALID** (0x02)    Media is invalid.</span></span>
- <span data-ttu-id="aa949-2133">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2133">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2134">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2134">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2135">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2135">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-2136">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-2136">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-2137">**FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2137">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="aa949-2138">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2138">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-2139">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2139">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2140">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2140">Allowed From</span></span>

<span data-ttu-id="aa949-2141">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2141">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2142">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2142">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Rename "myfile1.txt" to "myfile2.txt" in the default directory of the media. */

status = fx_file_rename(&my_media, "myfile1.txt", "myfile2.txt");

/* If status equals FX_SUCCESS, the file was successfully renamed. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-2143">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2143">See Also</span></span>

- <span data-ttu-id="aa949-2144">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2144">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-2145">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2145">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-2146">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2146">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-2147">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2147">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2148">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2148">fx_file_close</span></span>
- <span data-ttu-id="aa949-2149">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2149">fx_file_create</span></span>
- <span data-ttu-id="aa949-2150">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2150">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-2151">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-2151">fx_file_delete</span></span>
- <span data-ttu-id="aa949-2152">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2152">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-2153">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2153">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2154">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2154">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-2155">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2155">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-2156">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2156">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-2157">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2157">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-2158">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2158">fx_file_open</span></span>
- <span data-ttu-id="aa949-2159">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2159">fx_file_read</span></span>
- <span data-ttu-id="aa949-2160">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2160">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-2161">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2161">fx_file_seek</span></span>
- <span data-ttu-id="aa949-2162">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2162">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-2163">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2163">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-2164">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2164">fx_file_write</span></span>
- <span data-ttu-id="aa949-2165">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2165">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-2166">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2166">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-2167">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2167">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-2168">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2168">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-2169">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2169">fx_unicode_short_name_get</span></span>

## <a name="fx_file_seek"></a><span data-ttu-id="aa949-2170">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2170">fx_file_seek</span></span>

<span data-ttu-id="aa949-2171">バイト オフセットに配置します</span><span class="sxs-lookup"><span data-stu-id="aa949-2171">Positions to byte offset</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2172">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2172">Prototype</span></span>

```c
UINT fx_file_seek(
    FX_FILE *file_ptr,
    ULONG byte_offset);
```
### <a name="description"></a><span data-ttu-id="aa949-2173">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2173">Description</span></span>

<span data-ttu-id="aa949-2174">このサービスは、指定されたバイト オフセットに、内部ファイルの読み取り/書き込みポインターを配置します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2174">This service positions the internal file read/write pointer to the specified byte offset.</span></span> <span data-ttu-id="aa949-2175">それ以降のファイルの読み取りまたは書き込み要求は、ファイル内のこの場所から開始されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2175">Any subsequent file read or write request will begin at this location in the file.</span></span>

<span data-ttu-id="aa949-2176">4 GB を超えるオフセット値を使用してシークするには、アプリケーションでサービス *fx_file_extended_seek* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2176">To seek with an offset value beyond 4GB, application shall use the service *fx_file_extended_seek*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2177">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2177">Input Parameters</span></span>

- <span data-ttu-id="aa949-2178">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2178">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-2179">**byte_offset**: ファイル内の目標のバイト オフセット。</span><span class="sxs-lookup"><span data-stu-id="aa949-2179">**byte_offset**: Desired byte offset in file.</span></span> <span data-ttu-id="aa949-2180">値を 0 にすると、読み取り/書き込みポインターがファイルの先頭に配置され、ファイルのサイズより大きい値にすると、読み取り/書き込みポインターがファイルの末尾に配置されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2180">A value of zero will position the read/write pointer at the beginning of the file, while a value greater than the file's size will position the read/write pointer at the end of the file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2181">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2181">Return Values</span></span>

- <span data-ttu-id="aa949-2182">**FX_SUCCESS** (0x00) ファイルのシークに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2182">**FX_SUCCESS** (0x00) Successful file seek.</span></span>
- <span data-ttu-id="aa949-2183">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2183">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-2184">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2184">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2185">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2185">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2186">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2186">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2187">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-2187">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-2188">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2188">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-2189">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2189">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2190">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2190">Allowed From</span></span>

<span data-ttu-id="aa949-2191">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2191">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2192">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2192">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Seek to the beginning of "my_file." */
status = fx_file_seek(&my_file, 0);
/* If status equals FX_SUCCESS, the file read/write pointer
    is now positioned to the beginning of the file. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-2193">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2193">See Also</span></span>

- <span data-ttu-id="aa949-2194">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2194">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-2195">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2195">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-2196">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2196">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-2197">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2197">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2198">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2198">fx_file_close</span></span>
- <span data-ttu-id="aa949-2199">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2199">fx_file_create</span></span>
- <span data-ttu-id="aa949-2200">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2200">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-2201">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-2201">fx_file_delete</span></span>
- <span data-ttu-id="aa949-2202">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2202">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-2203">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2203">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2204">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2204">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-2205">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2205">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-2206">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2206">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-2207">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2207">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-2208">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2208">fx_file_open</span></span>
- <span data-ttu-id="aa949-2209">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2209">fx_file_read</span></span>
- <span data-ttu-id="aa949-2210">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2210">fx_file_rename</span></span>
- <span data-ttu-id="aa949-2211">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2211">fx_file_seek</span></span>
- <span data-ttu-id="aa949-2212">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2212">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-2213">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2213">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-2214">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2214">fx_file_write</span></span>
- <span data-ttu-id="aa949-2215">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2215">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-2216">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2216">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-2217">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2217">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-2218">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2218">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-2219">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2219">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate"></a><span data-ttu-id="aa949-2220">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2220">fx_file_truncate</span></span>

<span data-ttu-id="aa949-2221">ファイルを切り捨てます</span><span class="sxs-lookup"><span data-stu-id="aa949-2221">Truncates file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2222">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2222">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```

### <a name="description"></a><span data-ttu-id="aa949-2223">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2223">Description</span></span>

<span data-ttu-id="aa949-2224">このサービスは、指定されたサイズにファイルのサイズを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2224">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="aa949-2225">指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2225">If the supplied size is greater than the actual file size, this service doesn't do anything.</span></span> <span data-ttu-id="aa949-2226">ファイルに関連付けられているメディア クラスターは解放されません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2226">None of the media clusters associated with the file are released.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2227">*読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2227">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="aa949-2228">4 GB を超える操作を行うには、アプリケーションでサービス *fx_file_extended_truncate* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2228">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2229">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2229">Input Parameters</span></span>

- <span data-ttu-id="aa949-2230">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2230">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-2231">**size**: 新しいファイル サイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-2231">**size**: New file size.</span></span> <span data-ttu-id="aa949-2232">この新しいファイル サイズを超えるバイトは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2232">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2233">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2233">Return Values</span></span>

- <span data-ttu-id="aa949-2234">**FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2234">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="aa949-2235">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2235">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-2236">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2236">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-2237">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2237">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2238">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2238">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-2239">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2239">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2240">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2240">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2241">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2241">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-2242">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません</span><span class="sxs-lookup"><span data-stu-id="aa949-2242">**FX_NO_MORE_SPACE** (0x0A) No more space to complete the operation</span></span>
- <span data-ttu-id="aa949-2243">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2243">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-2244">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2244">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2245">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2245">Allowed From</span></span>

<span data-ttu-id="aa949-2246">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2246">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2247">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2247">Example</span></span>

```c
FX_FILE                my_file;
UINT                status;
/* Truncate "my_file" to 100 bytes. */

status = fx_file_truncate(&my_file, 100);

/* If status equals FX_SUCCESS, "my_file" contains 100 or fewer bytes. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-2248">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2248">See Also</span></span>

- <span data-ttu-id="aa949-2249">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2249">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-2250">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2250">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-2251">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2251">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-2252">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2252">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2253">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2253">fx_file_close</span></span>
- <span data-ttu-id="aa949-2254">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2254">fx_file_create</span></span>
- <span data-ttu-id="aa949-2255">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2255">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-2256">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-2256">fx_file_delete</span></span>
- <span data-ttu-id="aa949-2257">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2257">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-2258">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2258">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2259">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2259">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-2260">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2260">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-2261">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2261">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-2262">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2262">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-2263">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2263">fx_file_open</span></span>
- <span data-ttu-id="aa949-2264">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2264">fx_file_read</span></span>
- <span data-ttu-id="aa949-2265">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2265">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-2266">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2266">fx_file_rename</span></span>
- <span data-ttu-id="aa949-2267">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2267">fx_file_seek</span></span>
- <span data-ttu-id="aa949-2268">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2268">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-2269">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2269">fx_file_write</span></span>
- <span data-ttu-id="aa949-2270">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2270">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-2271">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2271">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-2272">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2272">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-2273">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2273">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-2274">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2274">fx_unicode_short_name_get</span></span>

## <a name="fx_file_truncate_release"></a><span data-ttu-id="aa949-2275">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2275">fx_file_truncate_release</span></span>

<span data-ttu-id="aa949-2276">ファイルを切り捨ててクラスターを解放します</span><span class="sxs-lookup"><span data-stu-id="aa949-2276">Truncates file and releases cluster(s)</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2277">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2277">Prototype</span></span>

```c
UINT fx_file_truncate(
    FX_FILE *file_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="aa949-2278">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2278">Description</span></span>

<span data-ttu-id="aa949-2279">このサービスは、指定されたサイズにファイルのサイズを切り捨てます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2279">This service truncates the size of the file to the specified size.</span></span> <span data-ttu-id="aa949-2280">指定されたサイズが実際のファイル サイズより大きい場合、このサービスは何も行いません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2280">If the supplied size is greater than the actual file size, this service does not do anything.</span></span> <span data-ttu-id="aa949-2281">***fx_file_truncate*** サービスとは異なり、このサービスでは未使用のクラスターが解放されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2281">Unlike the ***fx_file_truncate*** service, this service does release any unused clusters.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2282">*読み取り用に同時に開いている可能性があるファイルの切り捨てに注意してください。読み取り用にも開かれているファイルを切り捨てると、無効なデータが読み込まれる可能性があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2282">*Use caution truncating files that may also be simultaneously open for reading. Truncating a file also opened for reading can result in reading invalid data.*</span></span>

<span data-ttu-id="aa949-2283">4 GB を超える操作を行うには、アプリケーションでサービス *fx_file_extended_truncate_release* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2283">To operate beyond 4GB, application shall use the service *fx_file_extended_truncate_release*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2284">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2284">Input Parameters</span></span>

- <span data-ttu-id="aa949-2285">**file_ptr**: 以前に開いたファイルへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2285">**file_ptr**: Pointer to a previously opened file.</span></span>
- <span data-ttu-id="aa949-2286">**size**: 新しいファイル サイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-2286">**size**: New file size.</span></span> <span data-ttu-id="aa949-2287">この新しいファイル サイズを超えるバイトは破棄されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2287">Bytes past this new file size are discarded.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2288">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2288">Return Values</span></span>

- <span data-ttu-id="aa949-2289">**FX_SUCCESS** (0x00) ファイルの切り捨てに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2289">**FX_SUCCESS** (0x00) Successful file truncate.</span></span>
- <span data-ttu-id="aa949-2290">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2290">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-2291">**FX_NOT_OPEN** (0x07) 指定されたファイルは現在開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2291">**FX_NOT_OPEN** (0x07) Specified file is not currently open.</span></span>
- <span data-ttu-id="aa949-2292">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2292">**FX_IO_ERROR** (0x90)    Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2293">**FX_WRITE_PROTECT** (0x23) 基になるメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2293">**FX_WRITE_PROTECT** (0x23) Underlying media is write protected.</span></span>
- <span data-ttu-id="aa949-2294">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2294">**FX_FILE_CORRUPT** (0x08)    File is corrupted.</span></span>
- <span data-ttu-id="aa949-2295">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2295">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2296">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2296">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-2297">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2297">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-2298">**FX_NO_MORE_SPACE** (0x0A) 操作を完了するための空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2298">**FX_NO_MORE_SPACE** (0x0A)    No more space to complete the operation.</span></span>
- <span data-ttu-id="aa949-2299">**FX_PTR_ERROR** (0x18) 無効なファイル ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2299">**FX_PTR_ERROR** (0x18) Invalid file pointer.</span></span>
- <span data-ttu-id="aa949-2300">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2300">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2301">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2301">Allowed From</span></span>

<span data-ttu-id="aa949-2302">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2302">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2303">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2303">Example</span></span>

```c
FX_FILE         my_file;
UINT             status;

/* Attempt to truncate everything after the first 100 bytes of "my_file". */

status = fx_file_truncate_release(&my_file, 100);

/* If status equals FX_SUCCESS, the file is now 100 bytes
    or fewer and all unused clusters have been released. */
```
### <a name="see-also"></a><span data-ttu-id="aa949-2304">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2304">See Also</span></span>

- <span data-ttu-id="aa949-2305">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2305">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-2306">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2306">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-2307">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2307">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-2308">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2308">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2309">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2309">fx_file_close</span></span>
- <span data-ttu-id="aa949-2310">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2310">fx_file_create</span></span>
- <span data-ttu-id="aa949-2311">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2311">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-2312">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-2312">fx_file_delete</span></span>
- <span data-ttu-id="aa949-2313">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2313">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-2314">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2314">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2315">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2315">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-2316">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2316">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-2317">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2317">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-2318">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2318">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-2319">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2319">fx_file_open</span></span>
- <span data-ttu-id="aa949-2320">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2320">fx_file_read</span></span>
- <span data-ttu-id="aa949-2321">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2321">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-2322">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2322">fx_file_rename</span></span>
- <span data-ttu-id="aa949-2323">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2323">fx_file_seek</span></span>
- <span data-ttu-id="aa949-2324">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2324">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-2325">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2325">fx_file_write</span></span>
- <span data-ttu-id="aa949-2326">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2326">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-2327">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2327">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-2328">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2328">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-2329">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2329">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-2330">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2330">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write"></a><span data-ttu-id="aa949-2331">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2331">fx_file_write</span></span>

<span data-ttu-id="aa949-2332">ファイルにバイトを書き込みます</span><span class="sxs-lookup"><span data-stu-id="aa949-2332">Writes bytes to file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2333">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2333">Prototype</span></span>

```c
UINT fx_file_write(
    FX_FILE *file_ptr,
    VOID *buffer_ptr,
    ULONG size);
```
### <a name="description"></a><span data-ttu-id="aa949-2334">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2334">Description</span></span>

<span data-ttu-id="aa949-2335">このサービスは、ファイルの現在位置を開始位置として、指定されたバッファーからバイトを書き込みます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2335">This service writes bytes from the specified buffer starting at the file's current position.</span></span> <span data-ttu-id="aa949-2336">書き込みが完了すると、ファイルの内部読み取りポインターは、ファイル内の次のバイトを指すように調整されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2336">After the write is complete, the file's internal read pointer is adjusted to point at the next byte in the file.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2337">*ソース バッファーが長いワード境界にあり、要求されたサイズが sizeof (**ULONG**) で均等に割り切れる場合、パフォーマンスが向上します。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2337">*Faster performance is achieved if the source buffer is on a long-word boundary and the requested size is evenly divisible by sizeof(**ULONG**).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2338">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2338">Input Parameters</span></span>

- <span data-ttu-id="aa949-2339">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2339">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-2340">**buffer_ptr**: 書き込み用のソース バッファーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2340">**buffer_ptr**: Pointer to the source buffer for the write.</span></span>
- <span data-ttu-id="aa949-2341">**size**: 書き込むバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2341">**size**: Number of bytes to write.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2342">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2342">Return Values</span></span>

- <span data-ttu-id="aa949-2343">**FX_SUCCESS** (0x00) ファイルの書き込みに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2343">**FX_SUCCESS** (0x00) Successful file write.</span></span>
- <span data-ttu-id="aa949-2344">**FX_NOT_OPEN** (0x07) 指定されたファイルが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2344">**FX_NOT_OPEN** (0x07) Specified file is not open.</span></span>
- <span data-ttu-id="aa949-2345">**FX_ACCESS_ERROR** (0x06) 指定されたファイルが書き込み用に開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2345">**FX_ACCESS_ERROR** (0x06) Specified file is not open for writing.</span></span>
- <span data-ttu-id="aa949-2346">**FX_NO_MORE_SPACE** (0x0A) この書き込みを実行するための空き領域がメディアにありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2346">**FX_NO_MORE_SPACE** (0x0A) There is no more room available in the media to perform this write.</span></span>
- <span data-ttu-id="aa949-2347">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2347">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2348">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2348">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-2349">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2349">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2350">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2350">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2351">**FX_FAT_READ_ERROR** (0x03) FAT エントリを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2351">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT entry.</span></span>
- <span data-ttu-id="aa949-2352">**FX_NO_MORE_ENTRIES** (0x0F) FAT エントリはこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2352">**FX_NO_MORE_ENTRIES** (0x0F) No more FAT entries.</span></span>
- <span data-ttu-id="aa949-2353">**FX_PTR_ERROR** (0x18) 無効なファイルまたはバッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2353">**FX_PTR_ERROR** (0x18) Invalid file or buffer pointer.</span></span>
- <span data-ttu-id="aa949-2354">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2354">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2355">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2355">Allowed From</span></span>

<span data-ttu-id="aa949-2356">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2356">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2357">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2357">Example</span></span>

```c
FX_FILE            my_file;
UINT            status;
/* Write a 10 character buffer to "my_file." */

status = fx_file_write(&my_file, "1234567890", 10);

/* If status equals FX_SUCCESS, the small text string was written out to the file. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-2358">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2358">See Also</span></span>

- <span data-ttu-id="aa949-2359">fx_file_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2359">fx_file_allocate,</span></span>
- <span data-ttu-id="aa949-2360">fx_file_attributes_read、</span><span class="sxs-lookup"><span data-stu-id="aa949-2360">fx_file_attributes_read,</span></span>
- <span data-ttu-id="aa949-2361">fx_file_attributes_set、</span><span class="sxs-lookup"><span data-stu-id="aa949-2361">fx_file_attributes_set,</span></span>
- <span data-ttu-id="aa949-2362">fx_file_best_effort_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2362">fx_file_best_effort_allocate,</span></span>
- <span data-ttu-id="aa949-2363">fx_file_close、</span><span class="sxs-lookup"><span data-stu-id="aa949-2363">fx_file_close,</span></span>
- <span data-ttu-id="aa949-2364">fx_file_create、</span><span class="sxs-lookup"><span data-stu-id="aa949-2364">fx_file_create,</span></span>
- <span data-ttu-id="aa949-2365">fx_file_date_time_set、</span><span class="sxs-lookup"><span data-stu-id="aa949-2365">fx_file_date_time_set,</span></span>
- <span data-ttu-id="aa949-2366">fx_file_delete、</span><span class="sxs-lookup"><span data-stu-id="aa949-2366">fx_file_delete,</span></span>
- <span data-ttu-id="aa949-2367">fx_file_extended_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2367">fx_file_extended_allocate,</span></span>
- <span data-ttu-id="aa949-2368">fx_file_extended_best_effort_allocate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2368">fx_file_extended_best_effort_allocate,</span></span>
- <span data-ttu-id="aa949-2369">fx_file_extended_relative_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2369">fx_file_extended_relative_seek,</span></span>
- <span data-ttu-id="aa949-2370">fx_file_extended_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2370">fx_file_extended_seek,</span></span>
- <span data-ttu-id="aa949-2371">fx_file_extended_truncate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2371">fx_file_extended_truncate,</span></span>
- <span data-ttu-id="aa949-2372">fx_file_extended_truncate_release、</span><span class="sxs-lookup"><span data-stu-id="aa949-2372">fx_file_extended_truncate_release,</span></span>
- <span data-ttu-id="aa949-2373">fx_file_open、</span><span class="sxs-lookup"><span data-stu-id="aa949-2373">fx_file_open,</span></span>
- <span data-ttu-id="aa949-2374">fx_file_read、</span><span class="sxs-lookup"><span data-stu-id="aa949-2374">fx_file_read,</span></span>
- <span data-ttu-id="aa949-2375">fx_file_relative_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2375">fx_file_relative_seek,</span></span>
- <span data-ttu-id="aa949-2376">fx_file_rename、</span><span class="sxs-lookup"><span data-stu-id="aa949-2376">fx_file_rename,</span></span>
- <span data-ttu-id="aa949-2377">fx_file_seek、</span><span class="sxs-lookup"><span data-stu-id="aa949-2377">fx_file_seek,</span></span>
- <span data-ttu-id="aa949-2378">fx_file_truncate、</span><span class="sxs-lookup"><span data-stu-id="aa949-2378">fx_file_truncate,</span></span>
- <span data-ttu-id="aa949-2379">fx_file_truncate_release、</span><span class="sxs-lookup"><span data-stu-id="aa949-2379">fx_file_truncate_release,</span></span>
- <span data-ttu-id="aa949-2380">fx_file_write_notify_set、</span><span class="sxs-lookup"><span data-stu-id="aa949-2380">fx_file_write_notify_set,</span></span>
- <span data-ttu-id="aa949-2381">fx_unicode_file_create、</span><span class="sxs-lookup"><span data-stu-id="aa949-2381">fx_unicode_file_create,</span></span>
- <span data-ttu-id="aa949-2382">fx_unicode_file_rename、</span><span class="sxs-lookup"><span data-stu-id="aa949-2382">fx_unicode_file_rename,</span></span>
- <span data-ttu-id="aa949-2383">fx_unicode_name_get、</span><span class="sxs-lookup"><span data-stu-id="aa949-2383">fx_unicode_name_get,</span></span>
- <span data-ttu-id="aa949-2384">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2384">fx_unicode_short_name_get</span></span>

## <a name="fx_file_write_notify_set"></a><span data-ttu-id="aa949-2385">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2385">fx_file_write_notify_set</span></span>

<span data-ttu-id="aa949-2386">ファイル書き込み通知関数を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-2386">Sets the file write notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2387">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2387">Prototype</span></span>

```c
UINT fx_file_write_notify_set(
    FX_FILE *file_ptr,
    VOID (*file_write_notify)(FX_FILE*));
```
### <a name="description"></a><span data-ttu-id="aa949-2388">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2388">Description</span></span>

<span data-ttu-id="aa949-2389">このサービスは、ファイル書き込み操作に成功した後に呼び出されるコールバック関数をインストールします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2389">This service installs callback function that is invoked after a successful file write operation.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2390">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2390">Input Parameters</span></span>

- <span data-ttu-id="aa949-2391">**file_ptr**: ファイル制御ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2391">**file_ptr**: Pointer to the file control block.</span></span>
- <span data-ttu-id="aa949-2392">**file_write_notify**: インストールするファイル書き込みコールバック関数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2392">**file_write_notify**: File write callback function to be installed.</span></span> <span data-ttu-id="aa949-2393">コールバック関数を NULL に設定すると、コールバック関数が無効になります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2393">Set the callback function to NULL disables the callback function.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2394">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2394">Return Values</span></span>

- <span data-ttu-id="aa949-2395">**FX_SUCCESS** (0x00) コールバック関数が正常にインストールされました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2395">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="aa949-2396">**FX_PTR_ERROR** (0x18) file_ptr が NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2396">**FX_PTR_ERROR** (0x18) file_ptr is NULL.</span></span>
- <span data-ttu-id="aa949-2397">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2397">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2398">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2398">Allowed From</span></span>

<span data-ttu-id="aa949-2399">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2399">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2400">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2400">Example</span></span>

```c
fx_file_write_notify_set(file_ptr, my_file_close_callback);

```

### <a name="see-also"></a><span data-ttu-id="aa949-2401">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2401">See Also</span></span>

- <span data-ttu-id="aa949-2402">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2402">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-2403">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2403">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-2404">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2404">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-2405">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2405">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2406">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2406">fx_file_close</span></span>
- <span data-ttu-id="aa949-2407">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2407">fx_file_create</span></span>
- <span data-ttu-id="aa949-2408">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2408">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-2409">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-2409">fx_file_delete</span></span>
- <span data-ttu-id="aa949-2410">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2410">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-2411">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-2411">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-2412">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2412">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-2413">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2413">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-2414">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2414">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-2415">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2415">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-2416">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2416">fx_file_open</span></span>
- <span data-ttu-id="aa949-2417">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2417">fx_file_read</span></span>
- <span data-ttu-id="aa949-2418">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2418">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-2419">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2419">fx_file_rename</span></span>
- <span data-ttu-id="aa949-2420">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-2420">fx_file_seek</span></span>
- <span data-ttu-id="aa949-2421">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-2421">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-2422">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-2422">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-2423">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2423">fx_file_write</span></span>
- <span data-ttu-id="aa949-2424">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-2424">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-2425">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-2425">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-2426">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2426">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-2427">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2427">fx_unicode_short_name_get</span></span>

## <a name="fx_media_abort"></a><span data-ttu-id="aa949-2428">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2428">fx_media_abort</span></span>

<span data-ttu-id="aa949-2429">メディア アクティビティを中止します</span><span class="sxs-lookup"><span data-stu-id="aa949-2429">Aborts media activities</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2430">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2430">Prototype</span></span>

```c
UINT fx_media_abort(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-2431">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2431">Description</span></span>

<span data-ttu-id="aa949-2432">このサービスは、メディアに関連付けられている現在のすべてのアクティビティを中止します。たとえば、開いているすべてのファイルを閉じ、関連付けられているドライバーに中止要求を送信し、メディアを中止状態にします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2432">This service aborts all current activities associated with the media, including closing all open files, sending an abort request to the associated driver, and placing the media in an aborted state.</span></span> <span data-ttu-id="aa949-2433">このサービスは通常、I/O エラーが検出されたときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2433">This service is typically called when I/O errors are detected.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2434">*中止操作の実行後にメディアを再度使用するには、再度開く必要があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2434">*The media must be re-opened to use it again after an abort operation is performed.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2435">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2435">Input Parameters</span></span>

- <span data-ttu-id="aa949-2436">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2436">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2437">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2437">Return Values</span></span>

- <span data-ttu-id="aa949-2438">**FX_SUCCESS** (0x00) メディアの中止に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2438">**FX_SUCCESS** (0x00) Successful media abort.</span></span>
- <span data-ttu-id="aa949-2439">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2439">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2440">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2440">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-2441">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2441">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2442">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2442">Allowed From</span></span>

<span data-ttu-id="aa949-2443">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2443">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2444">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2444">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Abort all activity associated with "my_media". */

status = fx_media_abort(&my_media);

/* If status equals FX_SUCCESS, all activity
    associated with the media has been aborted. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2445">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2445">See Also</span></span>

- <span data-ttu-id="aa949-2446">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2446">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2447">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2447">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2448">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2448">fx_media_check</span></span>
- <span data-ttu-id="aa949-2449">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2449">fx_media_close</span></span>
- <span data-ttu-id="aa949-2450">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2450">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2451">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2451">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2452">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2452">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2453">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2453">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2454">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2454">fx_media_format</span></span>
- <span data-ttu-id="aa949-2455">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2455">fx_media_open</span></span>
- <span data-ttu-id="aa949-2456">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2456">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2457">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2457">fx_media_read</span></span>
- <span data-ttu-id="aa949-2458">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2458">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2459">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2459">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2460">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2460">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2461">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2461">fx_media_write</span></span>
- <span data-ttu-id="aa949-2462">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2462">fx_system_initialize</span></span>

## <a name="fx_media_cache_invalidate"></a><span data-ttu-id="aa949-2463">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2463">fx_media_cache_invalidate</span></span>

<span data-ttu-id="aa949-2464">論理セクター キャッシュを無効にします</span><span class="sxs-lookup"><span data-stu-id="aa949-2464">Invalidates logical sector cache</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2465">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2465">Prototype</span></span>

```c
UINT fx_media_cache_invalidate(FX_MEDIA *media_ptr);
```

### <a name="description"></a><span data-ttu-id="aa949-2466">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2466">Description</span></span>

<span data-ttu-id="aa949-2467">このサービスは、キャッシュ内のすべてのダーティ セクターをフラッシュし、論理セクター キャッシュ全体を無効にします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2467">This service flushes all dirty sectors in the cache and then invalidates the entire logical sector cache.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2468">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2468">Input Parameters</span></span>

- <span data-ttu-id="aa949-2469">**media_ptr**: メディア コントロール ブロックへのポインター</span><span class="sxs-lookup"><span data-stu-id="aa949-2469">**media_ptr**: Pointer to media control block</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2470">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2470">Return Values</span></span>

- <span data-ttu-id="aa949-2471">**FX_SUCCESS** (0x00) メディア キャッシュの無効化に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2471">**FX_SUCCESS** (0x00) Successful media cache invalidate.</span></span>
- <span data-ttu-id="aa949-2472">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2472">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2473">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2473">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2474">**FX_PTR_ERROR** (0x18) 無効なメディアまたはスクラッチ ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2474">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="aa949-2475">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2475">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2476">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2476">Allowed From</span></span>

<span data-ttu-id="aa949-2477">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2477">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2478">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2478">Example</span></span>

```c
FX_MEDIA     my_media;

/* Invalidate the cache of the media. */
status = fx_media_cache_invalidate(&my_media);

/* If status is FX_SUCCESS the cache in the media
    was successfully flushed and invalidated. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2479">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2479">See Also</span></span>

- <span data-ttu-id="aa949-2480">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2480">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2481">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2481">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2482">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2482">fx_media_check</span></span>
- <span data-ttu-id="aa949-2483">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2483">fx_media_close</span></span>
- <span data-ttu-id="aa949-2484">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2484">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2485">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2485">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2486">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2486">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2487">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2487">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2488">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2488">fx_media_format</span></span>
- <span data-ttu-id="aa949-2489">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2489">fx_media_open</span></span>
- <span data-ttu-id="aa949-2490">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2490">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2491">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2491">fx_media_read</span></span>
- <span data-ttu-id="aa949-2492">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2492">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2493">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2493">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2494">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2494">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2495">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2495">fx_media_write</span></span>
- <span data-ttu-id="aa949-2496">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2496">fx_system_initialize</span></span>

## <a name="fx_media_check"></a><span data-ttu-id="aa949-2497">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2497">fx_media_check</span></span>

<span data-ttu-id="aa949-2498">メディアにエラーがないかチェックします</span><span class="sxs-lookup"><span data-stu-id="aa949-2498">Checks media for errors</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2499">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2499">Prototype</span></span>

```c
UINT fx_media_check(
    FX_MEDIA *media_ptr,
    UCHAR *scratch_memory_ptr,
    ULONG scratch_memory_size,
    ULONG error_correction_option,
    ULONG *errors_detected_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-2500">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2500">Description</span></span>

<span data-ttu-id="aa949-2501">このサービスは、ファイルまたはディレクトリのクロスリンク、無効な FAT チェーン、および失われたクラスターなど、指定されたメディアの基本的な構造エラーを確認します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2501">This service checks the specified media for basic structural errors, including file/directory cross-linking, invalid FAT chains, and lost clusters.</span></span> <span data-ttu-id="aa949-2502">このサービスには、検出されたエラーを修正する機能も用意されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2502">This service also provides the capability to correct detected errors.</span></span>

<span data-ttu-id="aa949-2503">fx_media_check サービスでは、メディア内のディレクトリとファイルの深さ優先分析用のスクラッチ メモリが必要です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2503">The fx_media_check service requires scratch memory for its depth-first analysis of directories and files in the media.</span></span> <span data-ttu-id="aa949-2504">具体的には、メディア チェック サービスに提供されるスクラッチ メモリは、複数のディレクトリ エントリ、サブディレクトリに入る前に現在のディレクトリ エントリの位置を "スタック" するデータ構造、そして論理的な FAT のビットマップを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2504">Specifically, the scratch memory supplied to the media check service must be large enough to hold several directory entries, a data structure to "stack" the current directory entry position before entering into subdirectories, and finally the logical FAT bit map.</span></span> <span data-ttu-id="aa949-2505">スクラッチ メモリには、少なくとも 512 から 1024 バイトと、論理的な FAT のビットマップ用のメモリが必要で、これにはメディア内のクラスターと同じ数のビットが必要です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2505">The scratch memory should be at least 512-1024 bytes plus memory for the logical FAT bit map, which requires as many bits as there are clusters in the media.</span></span> <span data-ttu-id="aa949-2506">たとえば、8000 クラスターを持つデバイスを表すのに 1000 バイトが必要な場合、必要なスクラッチ領域の合計は約 2048 バイトとなります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2506">For example, a device with 8000 clusters would require 1000 bytes to represent and thus require a total scratch area on the order of 2048 bytes.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2507">*このサービスは、fx_media_open の直後に、他のファイル システムの活動がないときにのみ呼び出す必要があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2507">*This service should only be called immediately after fx_media_open and without any other file system activity.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2508">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2508">Input Parameters</span></span>

- <span data-ttu-id="aa949-2509">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2509">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-2510">**scratch_memory_ptr**: スクラッチ メモリの先頭へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2510">**scratch_memory_ptr**: Pointer to the start of scratch memory.</span></span>
- <span data-ttu-id="aa949-2511">**scratch_memory_size**: スクラッチ メモリのサイズ (バイト単位)。</span><span class="sxs-lookup"><span data-stu-id="aa949-2511">**scratch_memory_size**: Size of scratch memory in bytes.</span></span>
- <span data-ttu-id="aa949-2512">**error_correction_option**: エラー修正オプション ビット。ビットが設定されると、エラー修正が実行されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2512">**error_correction_option**: Error correction option bits, when the bit is set, error correction is performed.</span></span> <span data-ttu-id="aa949-2513">エラー修正オプション ビットは次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2513">The error correction option bits are defined as follows:</span></span>
  - <span data-ttu-id="aa949-2514">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-2514">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="aa949-2515">FX_DIRECTORY_ERROR (0x02)</span><span class="sxs-lookup"><span data-stu-id="aa949-2515">FX_DIRECTORY_ERROR (0x02)</span></span>
  - <span data-ttu-id="aa949-2516">FX_LOST_CLUSTER_ERROR (0x04) 必要なエラー修正オプションを単純に、または組み合わせて指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2516">FX_LOST_CLUSTER_ERROR (0x04) Simply OR together the required error correction options.</span></span> <span data-ttu-id="aa949-2517">エラー修正が不要な場合は、値 0 を指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2517">If no error correction is required, a value of 0 should be supplied.</span></span>
- <span data-ttu-id="aa949-2518">**errors_detected_ptr**: 下のように定義されているエラー検出ビットの宛先。</span><span class="sxs-lookup"><span data-stu-id="aa949-2518">**errors_detected_ptr**: Destination for error detection bits, as defined below:</span></span>
  - <span data-ttu-id="aa949-2519">FX_FAT_CHAIN_ERROR (0x01)</span><span class="sxs-lookup"><span data-stu-id="aa949-2519">FX_FAT_CHAIN_ERROR (0x01)</span></span>
  - <span data-ttu-id="aa949-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span><span class="sxs-lookup"><span data-stu-id="aa949-2520">FX_DIRECTORY_ERROR (0x02) FX_LOST_CLUSTER_ERROR (0x04)</span></span>
  - <span data-ttu-id="aa949-2521">FX_FILE_SIZE_ERROR (0x08)</span><span class="sxs-lookup"><span data-stu-id="aa949-2521">FX_FILE_SIZE_ERROR (0x08)</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2522">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2522">Return Values</span></span>

- <span data-ttu-id="aa949-2523">**FX_SUCCESS** (0x00) メディア チェックに成功し、検出されたエラーの詳細を確認します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2523">**FX_SUCCESS** (0x00) Successful media check, view the errors detected destination for details.</span></span>
- <span data-ttu-id="aa949-2524">**FX_ACCESS_ERROR** (0x06) 開いているファイルでチェックを実行できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2524">**FX_ACCESS_ERROR** (0x06) Unable to perform check with open files.</span></span>
- <span data-ttu-id="aa949-2525">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2525">**FX_FILE_CORRUPT** (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2526">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2526">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2527">**FX_NO_MORE_SPACE** (0x0A) メディアに空き領域がありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2527">**FX_NO_MORE_SPACE** (0x0A) No more space on the media.</span></span>
- <span data-ttu-id="aa949-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) 指定されたスクラッチ メモリの大きさが十分ではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2528">**FX_NOT_ENOUGH_MEMORY** (0x91) Supplied scratch memory is not large enough.</span></span>
- <span data-ttu-id="aa949-2529">**FX_ERROR_NOT_FIXED** (0x93) 修正できない FAT32 ルート ディレクトリの破損。</span><span class="sxs-lookup"><span data-stu-id="aa949-2529">**FX_ERROR_NOT_FIXED** (0x93) Corruption of FAT32 root directory that could not be fixed.</span></span>
- <span data-ttu-id="aa949-2530">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2530">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2531">**FX_SECTOR_INVALID** (0x89) セクターが無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2531">**FX_SECTOR_INVALID** (0x89) Sector is invalid.</span></span>
- <span data-ttu-id="aa949-2532">**FX_PTR_ERROR** (0x18) 無効なメディアまたはスクラッチ ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2532">**FX_PTR_ERROR** (0x18) Invalid media or scratch pointer.</span></span>
- <span data-ttu-id="aa949-2533">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>


### <a name="allowed-from"></a><span data-ttu-id="aa949-2534">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2534">Allowed From</span></span>

<span data-ttu-id="aa949-2535">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2536">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2536">Example</span></span>

```c
FX_MEDIA         my_media;
ULONG             detected_errors;
UCHAR             sratch_memory[4096];

/* Check the media and correct all errors. */

status = fx_media_check(&my_media, sratch_memory, 4096,
                        FX_FAT_CHAIN_ERROR |
                        FX_DIRECTORY_ERROR |
                        FX_LOST_CLUSTER_ERROR, &detected_errors);

/* If status is FX_SUCCESS and detected_errors is 0,
    the media was successfully checked and found to be error free. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2537">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2537">See Also</span></span>

- <span data-ttu-id="aa949-2538">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2538">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2539">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2539">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2540">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2540">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2541">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2541">fx_media_close</span></span>
- <span data-ttu-id="aa949-2542">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2542">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2543">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2543">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2544">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2544">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2545">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2545">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2546">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2546">fx_media_format</span></span>
- <span data-ttu-id="aa949-2547">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2547">fx_media_open</span></span>
- <span data-ttu-id="aa949-2548">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2548">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2549">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2549">fx_media_read</span></span>
- <span data-ttu-id="aa949-2550">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2550">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2551">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2551">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2552">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2552">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2553">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2553">fx_media_write</span></span>
- <span data-ttu-id="aa949-2554">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2554">fx_system_initialize</span></span>

## <a name="fx_media_close"></a><span data-ttu-id="aa949-2555">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2555">fx_media_close</span></span>

<span data-ttu-id="aa949-2556">メディアをクローズします</span><span class="sxs-lookup"><span data-stu-id="aa949-2556">Closes media</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2557">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2557">Prototype</span></span>

```c
UINT fx_media_close(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-2558">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2558">Description</span></span>

<span data-ttu-id="aa949-2559">このサービスは、指定されたメディアをクローズします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2559">This service closes the specified media.</span></span> <span data-ttu-id="aa949-2560">メディアをクローズするプロセスでは、開いているすべてのファイルがクローズされ、残っているバッファーは物理メディアにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2560">In the process of closing the media, all open files are closed and any remaining buffers are flushed to the physical media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2561">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2561">Input Parameters</span></span>

- <span data-ttu-id="aa949-2562">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2562">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2563">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2563">Return Values</span></span>

- <span data-ttu-id="aa949-2564">**FX_SUCCESS** (0x00) メディアのクローズに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2564">**FX_SUCCESS** (0x00) Successful media close.</span></span>
- <span data-ttu-id="aa949-2565">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2565">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2566">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2566">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2567">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2567">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-2568">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2568">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2569">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2569">Allowed From</span></span>

<span data-ttu-id="aa949-2570">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2570">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2571">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2571">Example</span></span>

```c
FX_MEDIA    my_media;
UINT        status;
/* Close "my_media". */

status = fx_media_close(&my_media);

/* If status equals FX_SUCCESS, "my_media" is closed. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2572">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2572">See Also</span></span>

- <span data-ttu-id="aa949-2573">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2573">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2574">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2574">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2575">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2575">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2576">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2576">fx_media_check</span></span>
- <span data-ttu-id="aa949-2577">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2577">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2578">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2578">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2579">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2579">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2580">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2580">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2581">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2581">fx_media_format</span></span>
- <span data-ttu-id="aa949-2582">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2582">fx_media_open</span></span>
- <span data-ttu-id="aa949-2583">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2583">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2584">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2584">fx_media_read</span></span>
- <span data-ttu-id="aa949-2585">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2585">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2586">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2586">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2587">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2587">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2588">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2588">fx_media_write</span></span>
- <span data-ttu-id="aa949-2589">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2589">fx_system_initialize</span></span>

## <a name="fx_media_close_notify_set"></a><span data-ttu-id="aa949-2590">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2590">fx_media_close_notify_set</span></span>

<span data-ttu-id="aa949-2591">メディア クローズ通知関数を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-2591">Sets the media close notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2592">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2592">Prototype</span></span>

```c
UINT fx_media_close_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_close_notify)(FX_MEDIA*));
```

### <a name="description"></a><span data-ttu-id="aa949-2593">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2593">Description</span></span>

<span data-ttu-id="aa949-2594">このサービスは、メディアのクローズに成功した後に呼び出される通知コールバック関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2594">This service sets a notify callback function which will be invoked after a media is successfully closed.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2595">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2595">Input Parameters</span></span>

- <span data-ttu-id="aa949-2596">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2596">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-2597">**media_close_notify**: インストールされるメディア クローズ通知コールバック関数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2597">**media_close_notify**: Media close notify callback function to be installed.</span></span> <span data-ttu-id="aa949-2598">コールバック関数として NULL を渡すと、メディア クローズ コールバックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2598">Passing NULL as the callback function disables the media close callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2599">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2599">Return Values</span></span>

- <span data-ttu-id="aa949-2600">**FX_SUCCESS** (0x00) コールバック関数が正常にインストールされました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2600">**FX_SUCCESS** (0x00) Successfully installed the callback function.</span></span>
- <span data-ttu-id="aa949-2601">**FX_PTR_ERROR** (0x18) media_ptr is が NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2601">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="aa949-2602">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2602">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2603">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2603">Allowed From</span></span>

<span data-ttu-id="aa949-2604">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2604">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2605">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2605">Example</span></span>

```c
fx_media_close_notify_set(media_ptr, my_media_close_callback);

```
### <a name="see-also"></a><span data-ttu-id="aa949-2606">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2606">See Also</span></span>

- <span data-ttu-id="aa949-2607">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2607">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2608">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2608">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2609">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2609">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2610">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2610">fx_media_check</span></span>
- <span data-ttu-id="aa949-2611">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2611">fx_media_close</span></span>
- <span data-ttu-id="aa949-2612">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2612">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2613">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2613">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2614">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2614">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2615">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2615">fx_media_format</span></span>
- <span data-ttu-id="aa949-2616">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2616">fx_media_open</span></span>
- <span data-ttu-id="aa949-2617">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2617">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2618">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2618">fx_media_read</span></span>
- <span data-ttu-id="aa949-2619">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2619">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2620">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2620">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2621">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2621">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2622">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2622">fx_media_write</span></span>
- <span data-ttu-id="aa949-2623">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2623">fx_system_initialize</span></span>

## <a name="fx_media_exfat_format"></a><span data-ttu-id="aa949-2624">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2624">fx_media_exFAT_format</span></span>

<span data-ttu-id="aa949-2625">メディアをフォーマットします</span><span class="sxs-lookup"><span data-stu-id="aa949-2625">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2626">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2626">Prototype</span></span>

```c
UINT fx_media_exFAT_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr, 
    UCHAR *memory_ptr,
    UINT memory_size, 
    CHAR *volume_name,
    UINT number_of_fats,
    ULONG64 hidden_sectors, 
    ULONG64 total_sectors,
    UINT bytes_per_sector, 
    UINT sectors_per_cluster,
    UINT volume_serial_number, 
    UINT boundary_unit);
```
### <a name="description"></a><span data-ttu-id="aa949-2627">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2627">Description</span></span>

<span data-ttu-id="aa949-2628">このサービスは、指定されたパラメーターに基づいて、指定されたメディアを exFAT 互換の方法でフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2628">This service formats the supplied media in an exFAT compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="aa949-2629">このサービスは、メディアを開く前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2629">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2630">*既にフォーマットされたメディアをフォーマットすると、メディア上のすべてのファイルとディレクトリが実質的に消去されます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2630">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-2631">*exFAT ボリューム サイズは、MBR または GPT レイアウトがある場合はパーティションのサイズと、または、パーティション レイアウトがない場合 (MBR または GPT がない場合) はデバイス全体のサイズと一致する必要があります。Windows には、使用可能なセクターよりも少ない合計セクターの値を使用してフォーマットした場合に exFAT Disk が認識されないという制限があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2631">*The exFAT volume size should match the size of the partition (if there is an MBR or GPT layout), or the size of the whole device if there is no partition layout (no MBR or GPT). There is a limitation on Windows that exFAT Disk will not be recoginzed if formatted with some values of total sectors that are less than available sectors*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2632">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2632">Input Parameters</span></span>

- <span data-ttu-id="aa949-2633">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2633">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="aa949-2634">これは、ドライバーが動作するために必要な基本的な情報を提供するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2634">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="aa949-2635">**driver**: このメディアの I/O ドライバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2635">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="aa949-2636">これは通常、後続の fx_media_open 呼び出しに指定されたドライバーと同じです。</span><span class="sxs-lookup"><span data-stu-id="aa949-2636">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="aa949-2637">**driver_info_ptr**: I/O ドライバーが使用できるオプション情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2637">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="aa949-2638">**memory_ptr**: メディアの作業メモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2638">**memory_ptr**: Pointer to the working memory for the media.</span></span> <span data-ttu-id="aa949-2639">memory_size: 作業メディア メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2639">memory_size Specifies the size of the working media memory.</span></span> <span data-ttu-id="aa949-2640">サイズは、メディアのセクター サイズ以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2640">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="aa949-2641">**volume_name**: 最大 11 文字のボリューム名の文字列を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2641">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="aa949-2642">**number_of_fats**: メディア内の FAT の数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2642">**number_of_fats**: Number of FATs on the media.</span></span> <span data-ttu-id="aa949-2643">現在の実装では、メディア上に 1 つの FAT がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2643">Current implementation supports one FAT on the media.</span></span>
- <span data-ttu-id="aa949-2644">**hidden_sectors**: このメディアのブート セクターの前に隠されたセクターの数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2644">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="aa949-2645">これは複数のパーティションが存在する場合に一般的です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2645">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="aa949-2646">**total_sectors**: メディア内のセクターの合計数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2646">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="aa949-2647">**bytes_per_sector**: 1 セクターあたりのバイト数 (通常は 512)。</span><span class="sxs-lookup"><span data-stu-id="aa949-2647">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="aa949-2648">FileX では 32 の倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2648">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="aa949-2649">**sectors_per_cluster**: 各クラスター内のセクター数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2649">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="aa949-2650">クラスターは FAT ファイル システムの最小のアロケーション ユニットです。</span><span class="sxs-lookup"><span data-stu-id="aa949-2650">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="aa949-2651">**volumne_serial_number**: このボリュームに使用するシリアル番号。</span><span class="sxs-lookup"><span data-stu-id="aa949-2651">**volumne_serial_number**: Serial number to be used for this volume.</span></span>
- <span data-ttu-id="aa949-2652">**boundary_unit**: 物理データ領域の配置サイズ (セクターの数)。</span><span class="sxs-lookup"><span data-stu-id="aa949-2652">**boundary_unit**: Physical data area alignment size, in number of sectors.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2653">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2653">Return Values</span></span>

- <span data-ttu-id="aa949-2654">**FX_SUCCESS** (0x00) メディアのフォーマットに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2654">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="aa949-2655">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2655">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2656">**FX_PTR_ERROR** (0x18) 無効なメディア、ドライバー、またはメモリ ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2656">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="aa949-2657">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2657">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2658">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2658">Allowed From</span></span>

<span data-ttu-id="aa949-2659">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2659">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2660">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2660">Example</span></span>

```c
FX_MEDIA             sd_card;
UCHAR                 media_memory[512];

/* Format a 64GB SD card with exFAT file system. The media has
    been properly partitioned, with the partition starts from sector 32768.
    For 64GB, there are total of 120913920 sectors, each sector 512 bytes. */

status = fx_media_exFAT_format(&sd_card, _fx_sd_driver,
                                driver_information, media_memory,
                                sizeof(media_memory),
                                "exFAT_DISK" /* Volume Name */,
                                1 /* Number of FATs */,
                                32768 /* Hidden sectors */,
                                120913920 /* Total sectors */,
                                512 /* Sector size */,
                                256 /* Sectors per cluster */,
                                12345 /* Volume ID */,
                                8192 /* Boundary unit */);

/* If status is FX_SUCCESS, the media was successfully formatted. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2661">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2661">See Also</span></span>

- <span data-ttu-id="aa949-2662">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2662">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2663">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2663">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2664">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2664">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2665">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2665">fx_media_check</span></span>
- <span data-ttu-id="aa949-2666">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2666">fx_media_close</span></span>
- <span data-ttu-id="aa949-2667">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2667">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2668">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2668">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2669">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2669">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2670">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2670">fx_media_format</span></span>
- <span data-ttu-id="aa949-2671">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2671">fx_media_open</span></span>
- <span data-ttu-id="aa949-2672">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2672">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2673">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2673">fx_media_read</span></span>
- <span data-ttu-id="aa949-2674">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2674">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2675">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2675">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2676">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2676">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2677">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2677">fx_media_write</span></span>
- <span data-ttu-id="aa949-2678">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2678">fx_system_initialize</span></span>

## <a name="fx_media_extended_space_available"></a><span data-ttu-id="aa949-2679">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2679">fx_media_extended_space_available</span></span>

<span data-ttu-id="aa949-2680">利用可能なメディア領域を返します</span><span class="sxs-lookup"><span data-stu-id="aa949-2680">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2681">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2681">Prototype</span></span>

```c
UINT fx_media_extended_space_available(
    FX_MEDIA *media_ptr,
    ULONG64 *available_bytes_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-2682">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2682">Description</span></span>

<span data-ttu-id="aa949-2683">このサービスは、メディアで使用可能なバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2683">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="aa949-2684">このサービスは、exFAT 向けに設計されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2684">This service is designed for exFAT.</span></span> <span data-ttu-id="aa949-2685">*available_bytes* パラメーターへのポインターは 64 ビットの整数値を取ります。これにより、呼び出し元は 4 GB を超えるメディアを操作できます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2685">The pointer to *available_bytes* parameter takes a 64-bit integer value, which allows the caller to work with media beyond 4GB range.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2686">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2686">Input Parameters</span></span>

- <span data-ttu-id="aa949-2687">**media_ptr**: 以前に開いたメディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2687">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="aa949-2688">**available_bytes_ptr**: メディアに残っている使用可能なバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2688">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2689">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2689">Return Values</span></span>

- <span data-ttu-id="aa949-2690">**FX_SUCCESS** (0x00) メディア上の使用可能な領域を正常に取得しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2690">**FX_SUCCESS** (0x00) Successfully retrieved space available on the media.</span></span>
- <span data-ttu-id="aa949-2691">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2691">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2692">**FX_PTR_ERROR** (0x18) 無効なメディアポインターまたは使用可能なバイト ポインターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2692">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="aa949-2693">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2693">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2694">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2694">Allowed From</span></span>

<span data-ttu-id="aa949-2695">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2695">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2696">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2696">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG64            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_extended_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2697">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2697">See Also</span></span>

- <span data-ttu-id="aa949-2698">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2698">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2699">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2699">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2700">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2700">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2701">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2701">fx_media_check</span></span>
- <span data-ttu-id="aa949-2702">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2702">fx_media_close</span></span>
- <span data-ttu-id="aa949-2703">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2703">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2704">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2704">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2705">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2705">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2706">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2706">fx_media_format</span></span>
- <span data-ttu-id="aa949-2707">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2707">fx_media_open</span></span>
- <span data-ttu-id="aa949-2708">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2708">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2709">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2709">fx_media_read</span></span>
- <span data-ttu-id="aa949-2710">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2710">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2711">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2711">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2712">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2712">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2713">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2713">fx_media_write</span></span>
- <span data-ttu-id="aa949-2714">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2714">fx_system_initialize</span></span>

## <a name="fx_media_flush"></a><span data-ttu-id="aa949-2715">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2715">fx_media_flush</span></span>

<span data-ttu-id="aa949-2716">物理メディアにデータをフラッシュします</span><span class="sxs-lookup"><span data-stu-id="aa949-2716">Flushes data to physical media</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2717">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2717">Prototype</span></span>

```c
UINT fx_media_flush(FX_MEDIA *media_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-2718">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2718">Description</span></span>

<span data-ttu-id="aa949-2719">このサービスは、変更されたファイルのキャッシュされたセクターとディレクトリ エントリを物理メディアにフラッシュします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2719">This service flushes all cached sectors and directory entries of any modified files to the physical media.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2720">*このルーチンは、ターゲットで突然電力が失われた場合に、ファイルの破損やデータ損失のリスクを軽減するために、アプリケーションによって定期的に呼び出されることがあります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2720">*This routine may be called periodically by the application to reduce the risk of file corruption and/or data loss in the event of a sudden loss of power on the target.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2721">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2721">Input Parameters</span></span>

- <span data-ttu-id="aa949-2722">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2722">**media_ptr**: Pointer to media control block.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2723">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2723">Return Values</span></span>

- <span data-ttu-id="aa949-2724">**FX_SUCCESS** (0x00) メディアのフラッシュに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2724">**FX_SUCCESS** (0x00) Successful media flush.</span></span>
- <span data-ttu-id="aa949-2725">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2725">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2726">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2726">**FX_FILE_CORRUPT**    (0x08) File is corrupted.</span></span>
- <span data-ttu-id="aa949-2727">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2727">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2728">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2728">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2729">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-2729">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-2730">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2730">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-2731">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2731">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2732">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2732">Allowed From</span></span>

<span data-ttu-id="aa949-2733">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2733">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2734">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2734">Example</span></span>

```c
FX_MEDIA         my_media;
UINT             status;

/* Flush all cached sectors and modified file entries to the physical media. */

status = fx_media_flush(&my_media);

/* If status equals FX_SUCCESS, the physical media is completely up-to-date. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2735">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2735">See Also</span></span>

- <span data-ttu-id="aa949-2736">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2736">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2737">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2737">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2738">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2738">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2739">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2739">fx_media_check</span></span>
- <span data-ttu-id="aa949-2740">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2740">fx_media_close</span></span>
- <span data-ttu-id="aa949-2741">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2741">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2742">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2742">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2743">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2743">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2744">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2744">fx_media_format</span></span>
- <span data-ttu-id="aa949-2745">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2745">fx_media_open</span></span>
- <span data-ttu-id="aa949-2746">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2746">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2747">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2747">fx_media_read</span></span>
- <span data-ttu-id="aa949-2748">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2748">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2749">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2749">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2750">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2750">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2751">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2751">fx_media_write</span></span>
- <span data-ttu-id="aa949-2752">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2752">fx_system_initialize</span></span>

## <a name="fx_media_format"></a><span data-ttu-id="aa949-2753">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2753">fx_media_format</span></span>

<span data-ttu-id="aa949-2754">メディアをフォーマットします</span><span class="sxs-lookup"><span data-stu-id="aa949-2754">Formats media</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2755">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2755">Prototype</span></span>

```c
UINT fx_media_format(
    FX_MEDIA *media_ptr,
    VOID (*driver)(FX_MEDIA *media),
    VOID *driver_info_ptr,
    UCHAR *memory_ptr, 
    UINT memory_size,
    CHAR *volume_name, 
    UINT number_of_fats,
    UINT directory_entries, 
    UINT hidden_sectors,
    ULONG total_sectors, 
    UINT bytes_per_sector,
    UINT sectors_per_cluster,
    UINT heads,
    UINT sectors_per_track);
```
### <a name="description"></a><span data-ttu-id="aa949-2756">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2756">Description</span></span>

<span data-ttu-id="aa949-2757">このサービスは、指定されたパラメーターに基づいて、指定されたメディアを FAT 12/16/32 互換の方法でフォーマットします。</span><span class="sxs-lookup"><span data-stu-id="aa949-2757">This service formats the supplied media in a FAT 12/16/32 compatible manner based on the supplied parameters.</span></span> <span data-ttu-id="aa949-2758">このサービスは、メディアを開く前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2758">This service must be called prior to opening the media.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2759">*既にフォーマットされたメディアをフォーマットすると、メディア上のすべてのファイルとディレクトリが実質的に消去されます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2759">*Formatting an already formatted media effectively erases all files and directories on the media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2760">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2760">Input Parameters</span></span>

- <span data-ttu-id="aa949-2761">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2761">**media_ptr**: Pointer to media control block.</span></span> <span data-ttu-id="aa949-2762">これは、ドライバーが動作するために必要な基本的な情報を提供するためにのみ使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2762">This is used only to provide some basic information necessary for the driver to operate.</span></span>
- <span data-ttu-id="aa949-2763">**driver**: このメディアの I/O ドライバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2763">**driver**: Pointer to the I/O driver for this media.</span></span> <span data-ttu-id="aa949-2764">これは通常、後続の fx_media_open 呼び出しに指定されたドライバーと同じです。</span><span class="sxs-lookup"><span data-stu-id="aa949-2764">This will typically be the same driver supplied to the subsequent fx_media_open call.</span></span>
- <span data-ttu-id="aa949-2765">**driver_info_ptr**: I/O ドライバーが使用できるオプション情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2765">**driver_info_ptr**: Pointer to optional information that the I/O driver may utilize.</span></span>
- <span data-ttu-id="aa949-2766">**memory_ptr**: メディアの作業メモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2766">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="aa949-2767">**memory_size**: 作業メディア メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2767">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="aa949-2768">サイズは、メディアのセクター サイズ以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2768">The size must be at least as large as the media's sector size.</span></span>
- <span data-ttu-id="aa949-2769">**volume_name**: 最大 11 文字のボリューム名の文字列を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2769">**volume_name**: Pointer to the volume name string, which is a maximum of 11 characters.</span></span>
- <span data-ttu-id="aa949-2770">**number_of_fats**: メディア内の FAT の数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2770">**number_of_fats**: Number of FATs in the media.</span></span> <span data-ttu-id="aa949-2771">最小値は、プライマリ FAT を示す 1 になります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2771">The minimal value is 1 for the primary FAT.</span></span> <span data-ttu-id="aa949-2772">1 より大きい値を指定すると、FAT の追加のコピーが実行時に維持されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2772">Values greater than 1 result in additional FAT copies being maintained at run-time.</span></span>
- <span data-ttu-id="aa949-2773">**directory_entries**: ルート ディレクトリ内のディレクトリ エントリの数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2773">**directory_entries**: Number of directory entries in the root directory.</span></span>
- <span data-ttu-id="aa949-2774">**hidden_sectors**: このメディアのブート セクターの前に隠されたセクターの数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2774">**hidden_sectors**: Number of sectors hidden before this media's boot sector.</span></span> <span data-ttu-id="aa949-2775">これは複数のパーティションが存在する場合に一般的です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2775">This is typical when multiple partitions are present.</span></span>
- <span data-ttu-id="aa949-2776">**total_sectors**: メディア内のセクターの合計数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2776">**total_sectors**: Total number of sectors in the media.</span></span>
- <span data-ttu-id="aa949-2777">**bytes_per_sector**: 1 セクターあたりのバイト数 (通常は 512)。</span><span class="sxs-lookup"><span data-stu-id="aa949-2777">**bytes_per_sector**: Number of bytes per sector, which is typically 512.</span></span> <span data-ttu-id="aa949-2778">FileX では 32 の倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2778">FileX requires this to be a multiple of 32.</span></span>
- <span data-ttu-id="aa949-2779">**sectors_per_cluster**: 各クラスター内のセクター数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2779">**sectors_per_cluster**: Number of sectors in each cluster.</span></span> <span data-ttu-id="aa949-2780">クラスターは FAT ファイル システムの最小のアロケーション ユニットです。</span><span class="sxs-lookup"><span data-stu-id="aa949-2780">The cluster is the minimum allocation unit in a FAT file system.</span></span>
- <span data-ttu-id="aa949-2781">**head**: 物理ヘッドの数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2781">**heads**: Number of physical heads.</span></span>
- <span data-ttu-id="aa949-2782">**sectors_per_track**: 1 トラックあたりのセクター数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2782">**sectors_per_track**: Number of sectors per track.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2783">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2783">Return Values</span></span>

- <span data-ttu-id="aa949-2784">**FX_SUCCESS** (0x00) メディアのフォーマットに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2784">**FX_SUCCESS** (0x00) Successful media format.</span></span>
- <span data-ttu-id="aa949-2785">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2785">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2786">**FX_PTR_ERROR** (0x18) 無効なメディア、ドライバー、またはメモリ ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2786">**FX_PTR_ERROR** (0x18) Invalid media, driver, or memory pointer.</span></span>
- <span data-ttu-id="aa949-2787">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2787">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2788">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2788">Allowed From</span></span>

<span data-ttu-id="aa949-2789">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2789">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2790">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2790">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             media_memory[512];
UCHAR             ram_disk_memory[32768];

/* Format a RAM disk with 32768 bytes and 512 bytes per sector. */

status = fx_media_format(&ram_disk, _fx_ram_driver,
                         ram_disk_memory, media_memory,
                         sizeof(media_memory),
                         "MY_RAM_DISK" /* Volume Name */,
                         1 /* Number of FATs */,
                         32 /* Directory Entries */,
                         0 /* Hidden sectors */,
                         64 /* Total sectors */,
                         512 /* Sector size */,
                         1 /* Sectors per cluster */,
                         1 /* Heads */,
                         1 /* Sectors per track */);

/* If status is FX_SUCCESS, the media was successfully formatted
    and can now be opened with the following call: */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2791">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2791">See Also</span></span>

- <span data-ttu-id="aa949-2792">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2792">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2793">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2793">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2794">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2794">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2795">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2795">fx_media_check</span></span>
- <span data-ttu-id="aa949-2796">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2796">fx_media_close</span></span>
- <span data-ttu-id="aa949-2797">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2797">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2798">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2798">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2799">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2799">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2800">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2800">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2801">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2801">fx_media_open</span></span>
- <span data-ttu-id="aa949-2802">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2802">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2803">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2803">fx_media_read</span></span>
- <span data-ttu-id="aa949-2804">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2804">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2805">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2805">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2806">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2806">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2807">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2807">fx_media_write</span></span>
- <span data-ttu-id="aa949-2808">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2808">fx_system_initialize</span></span>

## <a name="fx_media_open"></a><span data-ttu-id="aa949-2809">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2809">fx_media_open</span></span>

<span data-ttu-id="aa949-2810">ファイル アクセス用のメディアを開きます</span><span class="sxs-lookup"><span data-stu-id="aa949-2810">Opens media for file access</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2811">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2811">Prototype</span></span>

```c
UINT fx_media_open(
    FX_MEDIA *media_ptr, 
    CHAR *media_name,
    VOID(*media_driver)(FX_MEDIA *),
    VOID *driver_info_ptr,
    VOID *memory_ptr, 
    ULONG memory_size);
```
### <a name="description"></a><span data-ttu-id="aa949-2812">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2812">Description</span></span>

<span data-ttu-id="aa949-2813">このサービスは、指定された I/O ドライバーを使用してファイル アクセス用のメディアを開きます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2813">This service opens a media for file access using the supplied I/O driver.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-2814">*このサービスに提供されるメモリは、内部論理セクター キャッシュの実装に使用されるため、提供されるメモリが多くなるほど、多くの物理 I/O が削減されます。FileX では、少なくとも 1 つの論理セクター (メディアの 1 セクターあたりのバイト数) のキャッシュが必要です。*</span><span class="sxs-lookup"><span data-stu-id="aa949-2814">*The memory supplied to this service is used to implement an internal logical sector cache, hence, the more memory supplied the more physical I/O is reduced. FileX requires a cache of at least one logical sector (bytes per sector of the media).*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2815">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2815">Input Parameters</span></span>

- <span data-ttu-id="aa949-2816">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2816">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-2817">**media_name**: メディアの名前へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2817">**media_name**: Pointer to media's name.</span></span>
- <span data-ttu-id="aa949-2818">**media_driver**: このメディアの I/O ドライバーへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2818">**media_driver**: Pointer to I/O driver for this media.</span></span> <span data-ttu-id="aa949-2819">I/O ドライバーは、5 章で定義されている FileX ドライバーの要件に準拠している必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2819">The I/O driver must conform to FileX driver requirements defined in Chapter 5.</span></span>
- <span data-ttu-id="aa949-2820">**driver_info_ptr**: 指定された I/O ドライバーが使用できるオプション情報へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2820">**driver_info_ptr**: Pointer to optional information that the supplied I/O driver may utilize.</span></span>
- <span data-ttu-id="aa949-2821">**memory_ptr**: メディアの作業メモリへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2821">**memory_ptr**: Pointer to the working memory for the media.</span></span>
- <span data-ttu-id="aa949-2822">**memory_size**: 作業メディア メモリのサイズを指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2822">**memory_size**: Specifies the size of the working media memory.</span></span> <span data-ttu-id="aa949-2823">サイズはメディアのセクター サイズ (通常は 512 バイト) の大きさにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2823">The size must be as large as the media's sector size (typically 512 bytes).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2824">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2824">Return Values</span></span>

- <span data-ttu-id="aa949-2825">**FX_SUCCESS** (0x00) メディアのオープンに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2825">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="aa949-2826">**FX_BOOT_ERROR** (0x01) メディアのブート セクターの読み取り中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2826">**FX_BOOT_ERROR** (0x01) Error reading the media's boot sector.</span></span>
- <span data-ttu-id="aa949-2827">**FX_MEDIA_INVALID** (0x02) 指定されたメディアのブート セクターが破損しているか無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2827">**FX_MEDIA_INVALID** (0x02) Specified media's boot sector is corrupt or invalid.</span></span> <span data-ttu-id="aa949-2828">また、このリターン コードは、論理セクター キャッシュのサイズまたは FAT エントリのサイズのいずれかが 2 の累乗でないことを示すために使用されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-2828">In addition, this return code is used to indicate that either the logical sector cache size or the FAT entry size is not a power of 2.</span></span>
- <span data-ttu-id="aa949-2829">**FX_FAT_READ_ERROR** (0x03) メディア FAT の読み取り中にエラーが発生しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2829">**FX_FAT_READ_ERROR** (0x03) Error reading the media FAT.</span></span>
- <span data-ttu-id="aa949-2830">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2830">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2831">**FX_PTR_ERROR** (0x18) 1 つ以上のポインターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2831">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="aa949-2832">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2832">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2833">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2833">Allowed From</span></span>

<span data-ttu-id="aa949-2834">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2834">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2835">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2835">Example</span></span>

```c
FX_MEDIA         ram_disk,
UINT             status;
UCHAR             buffer[128];
/* Open a 32KByte RAM disk starting at the fixed address of 0x800000.
    Note that the total 32KByte media size and 128-byte sector size is defined inside of the driver. */

status = fx_media_open(&ram_disk, "RAM DISK", fx_ram_driver, 0, &buffer[0], sizeof(buffer));

/* If status equals FX_SUCCESS, the RAM disk has been successfully setup and is ready for file access! */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2836">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2836">See Also</span></span>

- <span data-ttu-id="aa949-2837">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2837">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2838">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2838">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2839">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2839">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2840">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2840">fx_media_check</span></span>
- <span data-ttu-id="aa949-2841">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2841">fx_media_close</span></span>
- <span data-ttu-id="aa949-2842">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2842">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2843">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2843">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2844">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2844">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2845">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2845">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2846">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2846">fx_media_format</span></span>
- <span data-ttu-id="aa949-2847">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2847">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2848">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2848">fx_media_read</span></span>
- <span data-ttu-id="aa949-2849">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2849">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2850">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2850">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2851">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2851">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2852">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2852">fx_media_write</span></span>
- <span data-ttu-id="aa949-2853">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2853">fx_system_initialize</span></span>

## <a name="fx_media_open_notify_set"></a><span data-ttu-id="aa949-2854">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2854">fx_media_open_notify_set</span></span>

<span data-ttu-id="aa949-2855">メディア オープン通知関数を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-2855">Sets the media open notify function</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2856">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2856">Prototype</span></span>

```c
UINT fx_media_open_notify_set(
    FX_MEDIA *media_ptr,
    VOID (*media_open_notify)(FX_MEDIA*));
```
### <a name="description"></a><span data-ttu-id="aa949-2857">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2857">Description</span></span>

<span data-ttu-id="aa949-2858">このサービスは、メディアのオープンに成功した後に呼び出される通知コールバック関数を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2858">This service sets a notify callback function which will be invoked after a media is successfully opened.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2859">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2859">Input Parameters</span></span>

- <span data-ttu-id="aa949-2860">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2860">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-2861">**media_open_notify**: インストールされるメディア オープン通知コールバック関数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2861">**media_open_notify**: Media open notify callback function to be installed.</span></span> <span data-ttu-id="aa949-2862">コールバック関数として NULL を渡すと、メディア オープン コールバックが無効になります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2862">Passing NULL as the callback function disables the media open callback.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2863">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2863">Return Values</span></span>


- <span data-ttu-id="aa949-2864">**FX_SUCCESS** (0x00) コールバック関数が正常にインストールされました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2864">**FX_SUCCESS** (0x00) Successfuly installed the callback function.</span></span>
- <span data-ttu-id="aa949-2865">**FX_PTR_ERROR** (0x18) media_ptr is が NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2865">**FX_PTR_ERROR** (0x18) media_ptr is NULL.</span></span>
- <span data-ttu-id="aa949-2866">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2866">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2867">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2867">Allowed From</span></span>

<span data-ttu-id="aa949-2868">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2868">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2869">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2869">Example</span></span>

```c
fx_media_open_notify_set(media_ptr, my_media_open_callback);

```

### <a name="see-also"></a><span data-ttu-id="aa949-2870">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2870">See Also</span></span>

- <span data-ttu-id="aa949-2871">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2871">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2872">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2872">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2873">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2873">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2874">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2874">fx_media_check</span></span>
- <span data-ttu-id="aa949-2875">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2875">fx_media_close</span></span>
- <span data-ttu-id="aa949-2876">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2876">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2877">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2877">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2878">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2878">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2879">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2879">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2880">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2880">fx_media_format</span></span>
- <span data-ttu-id="aa949-2881">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2881">fx_media_open</span></span>
- <span data-ttu-id="aa949-2882">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2882">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2883">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2883">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2884">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2884">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2885">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2885">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2886">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2886">fx_media_write</span></span>
- <span data-ttu-id="aa949-2887">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2887">fx_system_initialize</span></span>

## <a name="fx_media_read"></a><span data-ttu-id="aa949-2888">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2888">fx_media_read</span></span>

<span data-ttu-id="aa949-2889">メディアから論理セクターを読み取ります</span><span class="sxs-lookup"><span data-stu-id="aa949-2889">Reads logical sector from media</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2890">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2890">Prototype</span></span>

```c
UINT fx_media_read(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector, 
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-2891">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2891">Description</span></span>

<span data-ttu-id="aa949-2892">このサービスは、メディアから論理セクターを読み取り、指定されたバッファーに格納します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2892">This service reads a logical sector from the media and places it into the supplied buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2893">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2893">Input Parameters</span></span>

- <span data-ttu-id="aa949-2894">**media_ptr**: 以前に開いたメディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2894">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="aa949-2895">**logical_sector**: 読み取る論理セクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2895">**logical_sector**: Logical sector to read.</span></span>
- <span data-ttu-id="aa949-2896">**buffer_ptr**: 読み取る論理セクターの宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2896">**buffer_ptr**: Pointer to the destination for the logical sector read.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2897">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2897">Return Values</span></span>

- <span data-ttu-id="aa949-2898">**FX_SUCCESS** (0x00) メディアの読み取りに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2898">**FX_SUCCESS** (0x00) Successful media read.</span></span>
- <span data-ttu-id="aa949-2899">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2899">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2900">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2900">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2901">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2901">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-2902">**FX_PTR_ERROR** (0x18) 無効なメディアまたはバッファー ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2902">**FX_PTR_ERROR** (0x18) Invalid media or buffer pointer.</span></span>
- <span data-ttu-id="aa949-2903">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2903">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2904">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2904">Allowed From</span></span>

<span data-ttu-id="aa949-2905">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2905">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2906">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2906">Example</span></span>

```c
FX_MEDIA         my_media;
UCHAR             my_buffer[128];
UINT            STATUS;
/* Read logical sector 22 into "my_buffer" assuming the
    physical media has a sector size of 128. */
status = fx_media_read(&my_media, 22, my_buffer);
/* If status equals FX_SUCCESS, the contents of logical sector 22 are in "my_buffer". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-2907">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2907">See Also</span></span>

- <span data-ttu-id="aa949-2908">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2908">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2909">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2909">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2910">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2910">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2911">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2911">fx_media_check</span></span>
- <span data-ttu-id="aa949-2912">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2912">fx_media_close</span></span>
- <span data-ttu-id="aa949-2913">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2913">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2914">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2914">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2915">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2915">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2916">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2916">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2917">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2917">fx_media_format</span></span>
- <span data-ttu-id="aa949-2918">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2918">fx_media_open</span></span>
- <span data-ttu-id="aa949-2919">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2919">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2920">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2920">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2921">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2921">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2922">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2922">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2923">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2923">fx_media_write</span></span>
- <span data-ttu-id="aa949-2924">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2924">fx_system_initialize</span></span>

## <a name="fx_media_space_available"></a><span data-ttu-id="aa949-2925">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2925">fx_media_space_available</span></span>

<span data-ttu-id="aa949-2926">利用可能なメディア領域を返します</span><span class="sxs-lookup"><span data-stu-id="aa949-2926">Returns available media space</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2927">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2927">Prototype</span></span>

```c
UINT fx_media_space_available(
    FX_MEDIA *media_ptr,
    ULONG *available_bytes_ptr);
```

### <a name="description"></a><span data-ttu-id="aa949-2928">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2928">Description</span></span>

<span data-ttu-id="aa949-2929">このサービスは、メディアで使用可能なバイト数を返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2929">This service returns the number of bytes available in the media.</span></span>

<span data-ttu-id="aa949-2930">4 GB を超えるメディアを使用するには、アプリケーションでサービス *fx_media_extended_space_available* を使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-2930">To work with the media larger than 4GB, application shall use the service *fx_media_extended_space_available*.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2931">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2931">Input Parameters</span></span>

- <span data-ttu-id="aa949-2932">**media_ptr**: 以前に開いたメディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2932">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="aa949-2933">**available_bytes_ptr**: メディアに残っている使用可能なバイト数。</span><span class="sxs-lookup"><span data-stu-id="aa949-2933">**available_bytes_ptr**: Available bytes left in the media.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2934">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2934">Return Values</span></span>

- <span data-ttu-id="aa949-2935">**FX_SUCCESS** (0x00) メディア上の使用可能な領域を正常に返しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2935">**FX_SUCCESS** (0x00) Successfully returned available space on media.</span></span>
- <span data-ttu-id="aa949-2936">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2936">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2937">**FX_PTR_ERROR** (0x18) 無効なメディアポインターまたは使用可能なバイト ポインターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-2937">**FX_PTR_ERROR** (0x18) Invalid media pointer or available bytes pointer is NULL.</span></span>
- <span data-ttu-id="aa949-2938">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2938">**FX_CALLER_ERROR**    (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2939">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2939">Allowed From</span></span>

<span data-ttu-id="aa949-2940">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2940">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2941">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2941">Example</span></span>

```c
FX_MEDIA        my_media;
ULONG            available_bytes;
UINT            status;
/* Retrieve the available bytes in the media. */

status = fx_media_space_available(&my_media, &available_bytes);

/* If status equals FX_SUCCESS, the number of available bytes is in "available_bytes." */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2942">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2942">See Also</span></span>

- <span data-ttu-id="aa949-2943">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2943">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2944">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2944">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2945">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2945">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2946">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2946">fx_media_check</span></span>
- <span data-ttu-id="aa949-2947">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2947">fx_media_close</span></span>
- <span data-ttu-id="aa949-2948">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2948">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2949">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2949">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2950">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2950">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2951">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2951">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2952">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2952">fx_media_format</span></span>
- <span data-ttu-id="aa949-2953">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2953">fx_media_open</span></span>
- <span data-ttu-id="aa949-2954">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2954">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2955">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2955">fx_media_read</span></span>
- <span data-ttu-id="aa949-2956">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2956">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-2957">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2957">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2958">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2958">fx_media_write</span></span>
- <span data-ttu-id="aa949-2959">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-2959">fx_system_initialize</span></span>

## <a name="fx_media_volume_get"></a><span data-ttu-id="aa949-2960">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-2960">fx_media_volume_get</span></span>

<span data-ttu-id="aa949-2961">メディアのボリューム名を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-2961">Gets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-2962">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-2962">Prototype</span></span>

```c
UINT fx_media_volume_get(
    FX_MEDIA *media_ptr,
    CHAR *volume_name,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="aa949-2963">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-2963">Description</span></span>

<span data-ttu-id="aa949-2964">このサービスは、以前に開いたメディアのボリューム名を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2964">This service retrieves the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-2965">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-2965">Input Parameters</span></span>

- <span data-ttu-id="aa949-2966">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2966">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-2967">**volume_name**: ボリューム名の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2967">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="aa949-2968">宛先は、12 文字を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa949-2968">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="aa949-2969">**volume_source**: 名前を取得する場所を、ブート セクターまたはルート ディレクトリのいずれかから指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-2969">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="aa949-2970">このパラメーターの有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa949-2970">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="aa949-2971">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="aa949-2971">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="aa949-2972">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="aa949-2972">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-2973">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-2973">Return Values</span></span>

- <span data-ttu-id="aa949-2974">**FX_SUCCESS** (0x00) メディア ボリュームの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-2974">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="aa949-2975">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2975">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-2976">**FX_NOT_FOUND** (0x04) ボリュームが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2976">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="aa949-2977">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-2977">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-2978">**FX_PTR_ERROR** (0x18) 無効なメディアまたはボリュームの宛先ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-2978">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="aa949-2979">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-2979">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-2980">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-2980">Allowed From</span></span>

<span data-ttu-id="aa949-2981">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-2981">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-2982">例</span><span class="sxs-lookup"><span data-stu-id="aa949-2982">Example</span></span>

```c
FX_MEDIA        ram_disk;
UCHAR             volume_name[12];
/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name), FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */

```

### <a name="see-also"></a><span data-ttu-id="aa949-2983">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-2983">See Also</span></span>

- <span data-ttu-id="aa949-2984">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-2984">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-2985">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-2985">fx_media_abort</span></span>
- <span data-ttu-id="aa949-2986">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-2986">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-2987">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-2987">fx_media_check</span></span>
- <span data-ttu-id="aa949-2988">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-2988">fx_media_close</span></span>
- <span data-ttu-id="aa949-2989">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2989">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-2990">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2990">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-2991">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2991">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-2992">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-2992">fx_media_flush</span></span>
- <span data-ttu-id="aa949-2993">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-2993">fx_media_format</span></span>
- <span data-ttu-id="aa949-2994">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-2994">fx_media_open</span></span>
- <span data-ttu-id="aa949-2995">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2995">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-2996">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-2996">fx_media_read</span></span>
- <span data-ttu-id="aa949-2997">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-2997">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-2998">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-2998">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-2999">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-2999">fx_media_write</span></span>
- <span data-ttu-id="aa949-3000">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3000">fx_system_initialize</span></span>

## <a name="fx_media_volume_get_extended"></a><span data-ttu-id="aa949-3001">fx_media_volume_get_extended</span><span class="sxs-lookup"><span data-stu-id="aa949-3001">fx_media_volume_get_extended</span></span>

<span data-ttu-id="aa949-3002">以前に開いたメディアのメディア ボリューム名を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3002">Gets media volume name of previously opened media</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3003">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3003">Prototype</span></span>

```c
UINT fx_media_volume_get_extended(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name,
    UINT volume_name_buffer_length,
    UINT volume_source);
```
### <a name="description"></a><span data-ttu-id="aa949-3004">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3004">Description</span></span>

<span data-ttu-id="aa949-3005">このサービスは、以前に開いたメディアのボリューム名を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3005">This service retrieves the volume name of the previously opened media.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3006">このサービスは ***fx_media_volume_get ()** _ と同じですが、呼び出し元が _ *volume_name** バッファーのサイズを渡す点が異なります。</span><span class="sxs-lookup"><span data-stu-id="aa949-3006">This service is identical to ***fx_media_volume_get()** _ except the caller passes in the size of the _ *volume_name** buffer.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3007">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3007">Input Parameters</span></span>


- <span data-ttu-id="aa949-3008">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3008">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3009">**volume_name**: ボリューム名の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3009">**volume_name**: Pointer to destination for volume name.</span></span> <span data-ttu-id="aa949-3010">宛先は、12 文字を保持するのに十分な大きさである必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="aa949-3010">Note that the destination must be at least large enough to hold 12 characters.</span></span>
- <span data-ttu-id="aa949-3011">**volume_name_buffer_length**: volume_name バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3011">**volume_name_buffer_length**: Size of volume_name buffer.</span></span>
- <span data-ttu-id="aa949-3012">**volume_source**: 名前を取得する場所を、ブート セクターまたはルート ディレクトリのいずれかから指定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3012">**volume_source**: Designates where to retrieve the name, either from the boot sector or the root directory.</span></span> <span data-ttu-id="aa949-3013">このパラメーターの有効な値は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="aa949-3013">Valid values for this parameter are:</span></span>
  - <span data-ttu-id="aa949-3014">FX_BOOT_SECTOR</span><span class="sxs-lookup"><span data-stu-id="aa949-3014">FX_BOOT_SECTOR</span></span>
  - <span data-ttu-id="aa949-3015">FX_DIRECTORY_SECTOR</span><span class="sxs-lookup"><span data-stu-id="aa949-3015">FX_DIRECTORY_SECTOR</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3016">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3016">Return Values</span></span>

- <span data-ttu-id="aa949-3017">**FX_SUCCESS** (0x00) メディア ボリュームの取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3017">**FX_SUCCESS** (0x00) Successful media volume get.</span></span>
- <span data-ttu-id="aa949-3018">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3018">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3019">**FX_NOT_FOUND** (0x04) ボリュームが見つかりません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3019">**FX_NOT_FOUND** (0x04) Volume not found.</span></span>
- <span data-ttu-id="aa949-3020">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3020">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3021">**FX_PTR_ERROR** (0x18) 無効なメディアまたはボリュームの宛先ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3021">**FX_PTR_ERROR** (0x18) Invalid media or volume destination pointer.</span></span>
- <span data-ttu-id="aa949-3022">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3022">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3023">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3023">Allowed From</span></span>

<span data-ttu-id="aa949-3024">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3024">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3025">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3025">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             volume_name[12];

/* Retrieve the volume name of the RAM disk, from the boot sector. */

status = fx_media_volume_get_extended(&ram_disk, volume_name,
                                      sizeof(volume_name),
                                      FX_BOOT_SECTOR);

/* If status is FX_SUCCESS, the volume name was successfully retrieved. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3026">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3026">See Also</span></span>

- <span data-ttu-id="aa949-3027">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-3027">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-3028">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-3028">fx_media_abort</span></span>
- <span data-ttu-id="aa949-3029">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-3029">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-3030">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-3030">fx_media_check</span></span>
- <span data-ttu-id="aa949-3031">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3031">fx_media_close</span></span>
- <span data-ttu-id="aa949-3032">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3032">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-3033">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-3033">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-3034">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-3034">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-3035">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-3035">fx_media_flush</span></span>
- <span data-ttu-id="aa949-3036">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-3036">fx_media_format</span></span>
- <span data-ttu-id="aa949-3037">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3037">fx_media_open</span></span>
- <span data-ttu-id="aa949-3038">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3038">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-3039">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3039">fx_media_read</span></span>
- <span data-ttu-id="aa949-3040">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-3040">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-3041">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3041">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-3042">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3042">fx_media_write</span></span>
- <span data-ttu-id="aa949-3043">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3043">fx_system_initialize</span></span>

## <a name="fx_media_volume_set"></a><span data-ttu-id="aa949-3044">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3044">fx_media_volume_set</span></span>

<span data-ttu-id="aa949-3045">メディアのボリューム名を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-3045">Sets media volume name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3046">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3046">Prototype</span></span>

```c
UINT fx_media_volume_set(
    FX_MEDIA *media_ptr, 
    CHAR *volume_name);
```
### <a name="description"></a><span data-ttu-id="aa949-3047">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3047">Description</span></span>

<span data-ttu-id="aa949-3048">このサービスは、以前に開いたメディアのボリューム名を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3048">This service sets the volume name of the previously opened media.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3049">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3049">Input Parameters</span></span>

- <span data-ttu-id="aa949-3050">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3050">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3051">**volume_name**: ボリューム名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3051">**volume_name**: Pointer to the volume name.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3052">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3052">Return Values</span></span>

- <span data-ttu-id="aa949-3053">**FX_SUCCESS** (0x00) メディア ボリュームの設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3053">**FX_SUCCESS** (0x00) Successful media volume set.</span></span>
- <span data-ttu-id="aa949-3054">**FX_INVALID_NAME** (0x0C) Volume_name が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3054">**FX_INVALID_NAME** (0x0C) Volume_name is invalid.</span></span>
- <span data-ttu-id="aa949-3055">**FX_MEDIA_INVALID** (0x02) ボリューム名を設定できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3055">**FX_MEDIA_INVALID** (0x02) Unable to set volume name.</span></span>
- <span data-ttu-id="aa949-3056">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3056">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3057">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3057">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3058">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-3058">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-3059">**FX_PTR_ERROR** (0x18) 無効なメディアまたはボリューム名のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3059">**FX_PTR_ERROR** (0x18) Invalid media or volume name pointer.</span></span>
- <span data-ttu-id="aa949-3060">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3060">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3061">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3061">Allowed From</span></span>

<span data-ttu-id="aa949-3062">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3062">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3063">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3063">Example</span></span>

```c
FX_MEDIA ram_disk;

/* Set the volume name to "MY_VOLUME". */

status = fx_media_volume_set(&ram_disk, "MY_VOLUME");

/* If status is FX_SUCCESS, the volume name was successfully set. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3064">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3064">See Also</span></span>

- <span data-ttu-id="aa949-3065">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-3065">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-3066">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-3066">fx_media_abort</span></span>
- <span data-ttu-id="aa949-3067">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-3067">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-3068">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-3068">fx_media_check</span></span>
- <span data-ttu-id="aa949-3069">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3069">fx_media_close</span></span>
- <span data-ttu-id="aa949-3070">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3070">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-3071">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-3071">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-3072">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-3072">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-3073">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-3073">fx_media_flush</span></span>
- <span data-ttu-id="aa949-3074">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-3074">fx_media_format</span></span>
- <span data-ttu-id="aa949-3075">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3075">fx_media_open</span></span>
- <span data-ttu-id="aa949-3076">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3076">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-3077">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3077">fx_media_read</span></span>
- <span data-ttu-id="aa949-3078">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-3078">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-3079">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3079">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-3080">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3080">fx_media_write</span></span>
- <span data-ttu-id="aa949-3081">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3081">fx_system_initialize</span></span>

## <a name="fx_media_write"></a><span data-ttu-id="aa949-3082">fx_media_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3082">fx_media_write</span></span>

<span data-ttu-id="aa949-3083">論理セクターを書き込みます</span><span class="sxs-lookup"><span data-stu-id="aa949-3083">Writes logical sector</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3084">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3084">Prototype</span></span>

```c
UINT fx_media_write(
    FX_MEDIA *media_ptr, 
    ULONG logical_sector,
    VOID *buffer_ptr);
```
### <a name="description"></a><span data-ttu-id="aa949-3085">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3085">Description</span></span>

<span data-ttu-id="aa949-3086">このサービスは、指定されたバッファーを指定された論理セクターに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3086">This service writes the supplied buffer to the specified logical sector.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3087">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3087">Input Parameters</span></span>

- <span data-ttu-id="aa949-3088">**media_ptr**: 以前に開いたメディアへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3088">**media_ptr**: Pointer to a previously opened media.</span></span>
- <span data-ttu-id="aa949-3089">**logical_sector**: 書き込む論理セクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3089">**logical_sector**: Logical sector to write.</span></span>
- <span data-ttu-id="aa949-3090">**buffer_ptr**: 論理セクター書き込みのソースへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3090">**buffer_ptr**: Pointer to the source for the logical sector write.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3091">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3091">Return Values</span></span>

- <span data-ttu-id="aa949-3092">**FX_SUCCESS** (0x00) メディアの書き込みに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3092">**FX_SUCCESS** (0x00) Successful media write.</span></span>
- <span data-ttu-id="aa949-3093">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3093">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3094">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3094">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-3095">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3095">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3096">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-3096">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-3097">**FX_PTR_ERROR** (0x18) 無効なメディア ポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3097">**FX_PTR_ERROR** (0x18) Invalid media pointer.</span></span>
- <span data-ttu-id="aa949-3098">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3098">**FX_CALLER_ERROR**    (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3099">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3099">Allowed From</span></span>

<span data-ttu-id="aa949-3100">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3100">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3101">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3101">Example</span></span>

```c
FX_MEDIA             my_media;
UCHAR                 my_buffer[128];
UINT                 status;

/* Write logical sector 22 from "my_buffer" assuming
    the physical media has a sector size of 128. */

status = fx_media_write(&my_media, 22, my_buffer);

/* If status equals FX_SUCCESS, the contents of logical
    sector 22 are now the same as "my_buffer." */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3102">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3102">See Also</span></span>

- <span data-ttu-id="aa949-3103">fx_fault_tolerant_enable</span><span class="sxs-lookup"><span data-stu-id="aa949-3103">fx_fault_tolerant_enable</span></span>
- <span data-ttu-id="aa949-3104">fx_media_abort</span><span class="sxs-lookup"><span data-stu-id="aa949-3104">fx_media_abort</span></span>
- <span data-ttu-id="aa949-3105">fx_media_cache_invalidate</span><span class="sxs-lookup"><span data-stu-id="aa949-3105">fx_media_cache_invalidate</span></span>
- <span data-ttu-id="aa949-3106">fx_media_check</span><span class="sxs-lookup"><span data-stu-id="aa949-3106">fx_media_check</span></span>
- <span data-ttu-id="aa949-3107">fx_media_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3107">fx_media_close</span></span>
- <span data-ttu-id="aa949-3108">fx_media_close_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3108">fx_media_close_notify_set</span></span>
- <span data-ttu-id="aa949-3109">fx_media_exFAT_format</span><span class="sxs-lookup"><span data-stu-id="aa949-3109">fx_media_exFAT_format</span></span>
- <span data-ttu-id="aa949-3110">fx_media_extended_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-3110">fx_media_extended_space_available</span></span>
- <span data-ttu-id="aa949-3111">fx_media_flush</span><span class="sxs-lookup"><span data-stu-id="aa949-3111">fx_media_flush</span></span>
- <span data-ttu-id="aa949-3112">fx_media_format</span><span class="sxs-lookup"><span data-stu-id="aa949-3112">fx_media_format</span></span>
- <span data-ttu-id="aa949-3113">fx_media_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3113">fx_media_open</span></span>
- <span data-ttu-id="aa949-3114">fx_media_open_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3114">fx_media_open_notify_set</span></span>
- <span data-ttu-id="aa949-3115">fx_media_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3115">fx_media_read</span></span>
- <span data-ttu-id="aa949-3116">fx_media_space_available</span><span class="sxs-lookup"><span data-stu-id="aa949-3116">fx_media_space_available</span></span>
- <span data-ttu-id="aa949-3117">fx_media_volume_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3117">fx_media_volume_get</span></span>
- <span data-ttu-id="aa949-3118">fx_media_volume_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3118">fx_media_volume_set</span></span>
- <span data-ttu-id="aa949-3119">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3119">fx_system_initialize</span></span>

## <a name="fx_system_date_get"></a><span data-ttu-id="aa949-3120">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3120">fx_system_date_get</span></span>

<span data-ttu-id="aa949-3121">ファイル システム日付を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3121">Gets file system date</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3122">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3122">Prototype</span></span>

```c
UINT fx_system_date_get(
    UINT *year, 
    UINT *month, 
    UINT *day);
```
### <a name="description"></a><span data-ttu-id="aa949-3123">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3123">Description</span></span>

<span data-ttu-id="aa949-3124">このサービスは、現在のシステム日付を返します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3124">This service returns the current system date.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3125">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3125">Input Parameters</span></span>

- <span data-ttu-id="aa949-3126">**year**: 年の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3126">**year**: Pointer to destination for year.</span></span>
- <span data-ttu-id="aa949-3127">**month**: 月の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3127">**month**: Pointer to destination for month.</span></span>
- <span data-ttu-id="aa949-3128">**day**: 日の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3128">**day**: Pointer to destination for day.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3129">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3129">Return Values</span></span>

- <span data-ttu-id="aa949-3130">**FX_SUCCESS** (0x00) 日付の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3130">**FX_SUCCESS** (0x00) Successful date retrieval.</span></span>
- <span data-ttu-id="aa949-3131">**FX_PTR_ERROR** (0x18) 1 つ以上の入力パラメーターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3131">**FX_PTR_ERROR** (0x18) One or more of the input parameters are NULL.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3132">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3132">Allowed From</span></span>

<span data-ttu-id="aa949-3133">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3133">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3134">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3134">Example</span></span>

```c
UINT            status;
UINT            year;
UINT            month;
UINT            day;
/* Retrieve the current system date. */

status = fx_system_date_get(&year, &month, &day);

/* If status equals FX_SUCCESS, the year, month,
    and day parameters now have meaningful information. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3135">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3135">See Also</span></span>

- <span data-ttu-id="aa949-3136">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3136">fx_system_date_set</span></span>
- <span data-ttu-id="aa949-3137">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3137">fx_system_initialize</span></span>
- <span data-ttu-id="aa949-3138">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3138">fx_system_time_get</span></span>
- <span data-ttu-id="aa949-3139">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3139">fx_system_time_set</span></span>

## <a name="fx_system_date_set"></a><span data-ttu-id="aa949-3140">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3140">fx_system_date_set</span></span>

<span data-ttu-id="aa949-3141">システム日付を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-3141">Sets system date</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3142">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3142">Prototype</span></span>

```c
UINT fx_system_date_set(
    UINT year, 
    UINT month, 
    UINT day);
```

### <a name="description"></a><span data-ttu-id="aa949-3143">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3143">Description</span></span>

<span data-ttu-id="aa949-3144">このサービスは、指定されたシステム日付を設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3144">This service sets the system date as specified.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-3145">*このサービスは、最初のシステム日付を設定するために **fx_system_initialize** の直後に呼び出す必要があります。既定では、システム日付は最後の汎用 FileX リリースの日付です。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3145">*This service should be called shortly after **fx_system_initialize** to set the initial system date. By default, the system date is that of the last generic FileX release.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3146">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3146">Input Parameters</span></span>

- <span data-ttu-id="aa949-3147">**year**: 新しい年。</span><span class="sxs-lookup"><span data-stu-id="aa949-3147">**year**: New year.</span></span> <span data-ttu-id="aa949-3148">有効な範囲は 1980 年から 2107 年までです。</span><span class="sxs-lookup"><span data-stu-id="aa949-3148">The valid range is from 1980 through the year 2107.</span></span>
- <span data-ttu-id="aa949-3149">**month**: 新しい月。</span><span class="sxs-lookup"><span data-stu-id="aa949-3149">**month**: New month.</span></span> <span data-ttu-id="aa949-3150">有効な範囲は 1 から 12 までです。</span><span class="sxs-lookup"><span data-stu-id="aa949-3150">The valid range is from 1 through 12.</span></span>
- <span data-ttu-id="aa949-3151">**day**: 新しい日付。</span><span class="sxs-lookup"><span data-stu-id="aa949-3151">**day**: New day.</span></span> <span data-ttu-id="aa949-3152">有効な範囲は、月と閏年の条件に応じて 1 から 31 までです。</span><span class="sxs-lookup"><span data-stu-id="aa949-3152">The valid range is from 1 through 31, depending on month and leap year conditions.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3153">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3153">Return Values</span></span>

- <span data-ttu-id="aa949-3154">**FX_SUCCESS** (0x00) 日付の設定に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3154">**FX_SUCCESS** (0x00) Successful date setting.</span></span>
- <span data-ttu-id="aa949-3155">**FX_INVALID_YEAR** (0x12) 無効な年が指定されました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3155">**FX_INVALID_YEAR** (0x12) Invalid year specified.</span></span>
- <span data-ttu-id="aa949-3156">**FX_INVALID_MONTH** (0x13) 無効な月が指定されました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3156">**FX_INVALID_MONTH** (0x13) Invalid month specified.</span></span>
- <span data-ttu-id="aa949-3157">**FX_INVALID_DAY** (0x14) 無効な日付が指定されました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3157">**FX_INVALID_DAY** (0x14) Invalid day specified.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3158">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3158">Allowed From</span></span>

<span data-ttu-id="aa949-3159">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="aa949-3159">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3160">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3160">Example</span></span>

```c
 UINT             status;

/* Set the system date to December 12, 2005. */

status = fx_system_date_set(2005, 12, 12);

/* If status equals FX_SUCCESS, the file system date is now
    12-12-2005. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3161">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3161">See Also</span></span>

- <span data-ttu-id="aa949-3162">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3162">fx_system_date_get</span></span>
- <span data-ttu-id="aa949-3163">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3163">fx_system_initialize</span></span>
- <span data-ttu-id="aa949-3164">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3164">fx_system_time_get</span></span>
- <span data-ttu-id="aa949-3165">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3165">fx_system_time_set</span></span>

## <a name="fx_system_initialize"></a><span data-ttu-id="aa949-3166">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3166">fx_system_initialize</span></span>

<span data-ttu-id="aa949-3167">システム全体を初期化します</span><span class="sxs-lookup"><span data-stu-id="aa949-3167">Initializes entire system</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3168">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3168">Prototype</span></span>

```c
VOID fx_system_initialize(void);
```

### <a name="description"></a><span data-ttu-id="aa949-3169">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3169">Description</span></span>

<span data-ttu-id="aa949-3170">このサービスは、すべての主要な FileX データ構造を初期化します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3170">This service initializes all the major FileX data structures.</span></span> <span data-ttu-id="aa949-3171">これは ***tx_application_define*** または初期化スレッドから呼び出す必要があり、他の FileX サービスを使用する前に呼び出す必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-3171">It should be called either in ***tx_application_define*** or possibly from an initialization thread and must be called prior to using any other FileX service.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-3172">\* この呼び出しによって初期化されると、アプリケーションは正確なシステム日付と時刻で開始するために、***fx_system_date_set** _ および _ *fx_system_time_set** を呼び出す必要があります。\*</span><span class="sxs-lookup"><span data-stu-id="aa949-3172">*Once initialized by this call, the application should call ***fx_system_date_set** _ and _ *fx_system_time_set** to start with an accurate system date and time.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3173">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3173">Input Parameters</span></span>

<span data-ttu-id="aa949-3174">None</span><span class="sxs-lookup"><span data-stu-id="aa949-3174">None</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3175">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3175">Return Values</span></span>

<span data-ttu-id="aa949-3176">[なし] :</span><span class="sxs-lookup"><span data-stu-id="aa949-3176">None.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3177">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3177">Allowed From</span></span>

<span data-ttu-id="aa949-3178">初期化、スレッド</span><span class="sxs-lookup"><span data-stu-id="aa949-3178">Initialization, threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3179">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3179">Example</span></span>

```c
void tx_application_define(VOID *free_memory)
{
    UINT status;
    /* Initialize the FileX system. */
    fx_system_initialize();
    /* Set the file system date. */
    fx_system_date_set(my_year, my_month, my_day);

    /* Set the file system time. */
    fx_system_time_set(my_hour, my_minute, my_second);

    /* Now perform all other initialization and possibly FileX media
        open calls if the corresponding driver does not block on the boot sector read. */

    ...

}
```

### <a name="see-also"></a><span data-ttu-id="aa949-3180">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3180">See Also</span></span>

- <span data-ttu-id="aa949-3181">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3181">fx_system_date_get</span></span>
- <span data-ttu-id="aa949-3182">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3182">fx_system_date_set</span></span>
- <span data-ttu-id="aa949-3183">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3183">fx_system_time_get</span></span>
- <span data-ttu-id="aa949-3184">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3184">fx_system_time_set</span></span>

## <a name="fx_system_time_get"></a><span data-ttu-id="aa949-3185">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3185">fx_system_time_get</span></span>

<span data-ttu-id="aa949-3186">現在のシステム時刻を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3186">Gets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3187">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3187">Prototype</span></span>

```c
UINT fx_system_time_get(
    UINT *hour,
    UINT *minute,
    UINT *second);
```

### <a name="description"></a><span data-ttu-id="aa949-3188">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3188">Description</span></span>

<span data-ttu-id="aa949-3189">このサービスは、現在のシステム時刻を取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3189">This service retrieves the current system time.</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3190">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3190">Input Parameters</span></span>

- <span data-ttu-id="aa949-3191">**hour**: 時間の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3191">**hour**: Pointer to destination for hour.</span></span>
- <span data-ttu-id="aa949-3192">**minute**: 分の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3192">**minute**: Pointer to destination for minute.</span></span>
- <span data-ttu-id="aa949-3193">**second**: 秒の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3193">**second**: Pointer to destination for second.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3194">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3194">Return Values</span></span>

- <span data-ttu-id="aa949-3195">**FX_SUCCESS** (0x00) システム時刻の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3195">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="aa949-3196">**FX_PTR_ERROR** (0x18) 1 つ以上の入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3196">**FX_PTR_ERROR** (0x18) One or more of the input parameters</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3197">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3197">Allowed From</span></span>

<span data-ttu-id="aa949-3198">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3198">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3199">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3199">Example</span></span>

```c
UINT             status;
UINT             hour;
UINT             minute;
UINT             second;

/* Retrieve the current system time. */

status = fx_system_time_get(&hour, &minute, &second);

/* If status equals FX_SUCCESS, the current system time
    is in the hour, minute, and second variables. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3200">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3200">See Also</span></span>

- <span data-ttu-id="aa949-3201">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3201">fx_system_date_get</span></span>
- <span data-ttu-id="aa949-3202">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3202">fx_system_date_set</span></span>
- <span data-ttu-id="aa949-3203">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3203">fx_system_initialize</span></span>
- <span data-ttu-id="aa949-3204">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3204">fx_system_time_set</span></span>

## <a name="fx_system_time_set"></a><span data-ttu-id="aa949-3205">fx_system_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3205">fx_system_time_set</span></span>

<span data-ttu-id="aa949-3206">現在のシステム時刻を設定します</span><span class="sxs-lookup"><span data-stu-id="aa949-3206">Sets current system time</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3207">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3207">Prototype</span></span>

```c
UINT fx_system_time_set(UINT hour, UINT minute, UINT second);
```

### <a name="description"></a><span data-ttu-id="aa949-3208">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3208">Description</span></span>

<span data-ttu-id="aa949-3209">このサービスは、現在のシステム時刻を、入力パラメーターによって指定されたものに設定します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3209">This service sets the current system time to that specified by the input parameters.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-3210">*このサービスは、最初のシステム時刻を設定するために **fx_system_initialize** の直後に呼び出す必要があります。既定では、システム時刻は0:0:0 です。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3210">*This service should be called shortly after **fx_system_initialize** to set the initial system time. By default, the system time is 0:0:0.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3211">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3211">Input Parameters</span></span>

- <span data-ttu-id="aa949-3212">**hour**: 新しい時間 (0 から 23)。</span><span class="sxs-lookup"><span data-stu-id="aa949-3212">**hour**: New hour (0-23).</span></span>
- <span data-ttu-id="aa949-3213">**minute**: 新しい分 (0 から 59)。</span><span class="sxs-lookup"><span data-stu-id="aa949-3213">**minute**: New minute (0-59).</span></span>
- <span data-ttu-id="aa949-3214">**second**: 新しい秒 (0 から 59)。</span><span class="sxs-lookup"><span data-stu-id="aa949-3214">**second**: New second (0-59).</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3215">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3215">Return Values</span></span>

- <span data-ttu-id="aa949-3216">**FX_SUCCESS** (0x00) システム時刻の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3216">**FX_SUCCESS** (0x00) Successful system time retrieval.</span></span>
- <span data-ttu-id="aa949-3217">**FX_INVALID_HOUR** (0x15) 新しい時間が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3217">**FX_INVALID_HOUR**    (0x15) New hour is invalid.</span></span>
- <span data-ttu-id="aa949-3218">**FX_INVALID_MINUTE** (0x16) 新しい分が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3218">**FX_INVALID_MINUTE** (0x16) New minute is invalid.</span></span>
- <span data-ttu-id="aa949-3219">**FX_INVALID_SECOND** (0x17) 新しい秒が無効です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3219">**FX_INVALID_SECOND** (0x17) New second is invalid.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3220">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3220">Allowed From</span></span>

<span data-ttu-id="aa949-3221">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3221">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3222">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3222">Example</span></span>

```c
 UINT status;

/* Set the current system time to hour 23, minute 21, and second 20. */

status = fx_system_time_set(23, 21, 20);

/* If status is FX_SUCCESS, the current system time has been set. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3223">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3223">See Also</span></span>

- <span data-ttu-id="aa949-3224">fx_system_date_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3224">fx_system_date_get</span></span>
- <span data-ttu-id="aa949-3225">fx_system_date_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3225">fx_system_date_set</span></span>
- <span data-ttu-id="aa949-3226">fx_system_initialize</span><span class="sxs-lookup"><span data-stu-id="aa949-3226">fx_system_initialize</span></span>
- <span data-ttu-id="aa949-3227">fx_system_time_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3227">fx_system_time_get</span></span>

## <a name="fx_unicode_directory_create"></a><span data-ttu-id="aa949-3228">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3228">fx_unicode_directory_create</span></span>

<span data-ttu-id="aa949-3229">Unicode ディレクトリを作成します</span><span class="sxs-lookup"><span data-stu-id="aa949-3229">Creates a Unicode directory</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3230">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3230">Prototype</span></span>

```c
UINT fx_unicode_directory_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```
### <a name="description"></a><span data-ttu-id="aa949-3231">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3231">Description</span></span>

<span data-ttu-id="aa949-3232">このサービスでは、Unicode 名が付いたサブディレクトリが現在のデフォルト ディレクトリに作成されます。Unicode ソース名パラメーターではパス情報は使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3232">This service creates a Unicode-named subdirectory in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="aa949-3233">成功した場合は、新しく作成された Unicode サブディレクトリの短い名前 (8.3 形式) がサービスによって返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3233">If successful, the short name (8.3 format) of the newly created Unicode subdirectory is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-3234">*Unicode サブディレクトリに対するすべての操作 (デフォルト パスへの設定、削除など) は、返された短い名前 (8.3 形式) を標準の FileX ディレクトリ サービスに渡すことによって行う必要があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3234">*All operations on the Unicode subdirectory (making it the default path, deleting, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX directory services.*</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3235">*このサービスは、exFAT メディアではサポートされていません。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3235">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3236">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3236">Input Parameters</span></span>

- <span data-ttu-id="aa949-3237">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3237">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3238">**source_unicode_name**: 新しいサブディレクトリの Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3238">**source_unicode_name**: Pointer to the Unicode name for the new subdirectory.</span></span>
- <span data-ttu-id="aa949-3239">**source_unicode_length**: Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3239">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="aa949-3240">**short_name**: 新しい Unicode サブディレクトリの短い名前 (8.3 形式) の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3240">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode subdirectory.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3241">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3241">Return Values</span></span>

- <span data-ttu-id="aa949-3242">**FX_SUCCESS** (0x00) Unicode ディレクトリの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3242">**FX_SUCCESS** (0x00) Successful Unicode directory create.</span></span>
- <span data-ttu-id="aa949-3243">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3243">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3244">**FX_ALREADY_CREATED** (0x0B) 指定されたディレクトリは既に存在します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3244">**FX_ALREADY_CREATED** (0x0B) Specified directory already exists.</span></span>
- <span data-ttu-id="aa949-3245">**FX_NO_MORE_SPACE** (0x0A) 新しいディレクトリ エントリについて使用できるクラスターはメディア内にこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3245">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new directory entry.</span></span>
- <span data-ttu-id="aa949-3246">**FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3246">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="aa949-3247">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-3247">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-3248">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3248">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="aa949-3249">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3249">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="aa949-3250">**FX_IO_ERROR (0x90)** ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3250">**FX_IO_ERROR    (0x90)** Driver I/O error.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3251">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3251">Allowed From</span></span>

<span data-ttu-id="aa949-3252">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3252">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3253">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3253">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_short_name[13];
UCHAR                 my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                         0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                         0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                         0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                         0x63,0x00, 0x00,0x00};

/* Create a Unicode subdirectory with the name contained in "my_unicode_name". */

length = fx_unicode_directory_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode subdirectory is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3254">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3254">See Also</span></span>

- <span data-ttu-id="aa949-3255">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3255">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-3256">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3256">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-3257">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3257">fx_directory_create</span></span>
- <span data-ttu-id="aa949-3258">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3258">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-3259">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3259">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-3260">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3260">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-3261">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3261">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-3262">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3262">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-3263">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3263">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-3264">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-3264">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-3265">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3265">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-3266">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-3266">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-3267">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3267">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-3268">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3268">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-3269">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-3269">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-3270">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3270">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-3271">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3271">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-3272">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3272">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-3273">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3273">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-3274">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3274">fx_unicode_directory_rename</span></span>

## <a name="fx_unicode_directory_rename"></a><span data-ttu-id="aa949-3275">fx_unicode_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3275">fx_unicode_directory_rename</span></span>

<span data-ttu-id="aa949-3276">Unicode 文字列を使用してディレクトリの名前を変更します</span><span class="sxs-lookup"><span data-stu-id="aa949-3276">Renames directory using Unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3277">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3277">Prototype</span></span>

```c
UINT fx_unicode_directory_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length,
    CHAR *new_short_name);
```
### <a name="description"></a><span data-ttu-id="aa949-3278">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3278">Description</span></span>

<span data-ttu-id="aa949-3279">このサービスは、現在の作業ディレクトリ内で、Unicode 名が付いたサブディレクトリを指定された新しい Unicode 名に変更します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3279">This service changes a Unicode-named subdirectory to specified new Unicode name in current working directory.</span></span> <span data-ttu-id="aa949-3280">Unicode 名のパラメーターにパス情報を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3280">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3281">*このサービスは、exFAT メディアではサポートされていません。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3281">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3282">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3282">Input Parameters</span></span>

- <span data-ttu-id="aa949-3283">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3283">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3284">**old_unicode_name**: 現在のファイルの Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3284">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="aa949-3285">**old_unicode_name_length**: 現在の Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3285">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="aa949-3286">**new_unicode_name**: 新しい Unicode ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3286">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="aa949-3287">**old_unicode_name_length**: 新しい Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3287">**old_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="aa949-3288">**new_short_name**: 名前が変更された Unicode ファイルの短い名前 (8.3 形式) の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3288">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span> <span data-ttu-id="aa949-3289">Unicode でディレクトリ名を変更する</span><span class="sxs-lookup"><span data-stu-id="aa949-3289">Rename Directory with Unicode</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3290">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3290">Return Values</span></span>

- <span data-ttu-id="aa949-3291">**FX_SUCCESS** (0x00) メディアのオープンに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3291">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="aa949-3292">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3292">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3293">**FX_ALREADY_CREATED** (0x0B) 指定されたディレクトリ名は既に存在します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3293">**FX_ALREADY_CREATED** (0x0B) Specified directory name already exists.</span></span>
- <span data-ttu-id="aa949-3294">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3294">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3295">**FX_PTR_ERROR** (0x18) 1 つ以上のポインターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3295">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="aa949-3296">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3296">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>
- <span data-ttu-id="aa949-3297">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-3297">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3298">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3298">Allowed From</span></span>

<span data-ttu-id="aa949-3299">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3299">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3300">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3300">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_directory_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the directory was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3301">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3301">See Also</span></span>

- <span data-ttu-id="aa949-3302">fx_directory_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3302">fx_directory_attributes_read</span></span>
- <span data-ttu-id="aa949-3303">fx_directory_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3303">fx_directory_attributes_set</span></span>
- <span data-ttu-id="aa949-3304">fx_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3304">fx_directory_create</span></span>
- <span data-ttu-id="aa949-3305">fx_directory_default_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3305">fx_directory_default_get</span></span>
- <span data-ttu-id="aa949-3306">fx_directory_default_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3306">fx_directory_default_set</span></span>
- <span data-ttu-id="aa949-3307">fx_directory_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3307">fx_directory_delete</span></span>
- <span data-ttu-id="aa949-3308">fx_directory_first_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3308">fx_directory_first_entry_find</span></span>
- <span data-ttu-id="aa949-3309">fx_directory_first_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3309">fx_directory_first_full_entry_find</span></span>
- <span data-ttu-id="aa949-3310">fx_directory_information_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3310">fx_directory_information_get</span></span>
- <span data-ttu-id="aa949-3311">fx_directory_local_path_clear</span><span class="sxs-lookup"><span data-stu-id="aa949-3311">fx_directory_local_path_clear</span></span>
- <span data-ttu-id="aa949-3312">fx_directory_local_path_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3312">fx_directory_local_path_get</span></span>
- <span data-ttu-id="aa949-3313">fx_directory_local_path_restore</span><span class="sxs-lookup"><span data-stu-id="aa949-3313">fx_directory_local_path_restore</span></span>
- <span data-ttu-id="aa949-3314">fx_directory_local_path_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3314">fx_directory_local_path_set</span></span>
- <span data-ttu-id="aa949-3315">fx_directory_long_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3315">fx_directory_long_name_get</span></span>
- <span data-ttu-id="aa949-3316">fx_directory_name_test</span><span class="sxs-lookup"><span data-stu-id="aa949-3316">fx_directory_name_test</span></span>
- <span data-ttu-id="aa949-3317">fx_directory_next_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3317">fx_directory_next_entry_find</span></span>
- <span data-ttu-id="aa949-3318">fx_directory_next_full_entry_find</span><span class="sxs-lookup"><span data-stu-id="aa949-3318">fx_directory_next_full_entry_find</span></span>
- <span data-ttu-id="aa949-3319">fx_directory_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3319">fx_directory_rename</span></span>
- <span data-ttu-id="aa949-3320">fx_directory_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3320">fx_directory_short_name_get</span></span>
- <span data-ttu-id="aa949-3321">fx_unicode_directory_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3321">fx_unicode_directory_create</span></span>

## <a name="fx_unicode_file_create"></a><span data-ttu-id="aa949-3322">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3322">fx_unicode_file_create</span></span>

<span data-ttu-id="aa949-3323">Unicode ファイルを作成します</span><span class="sxs-lookup"><span data-stu-id="aa949-3323">Creates a Unicode file</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3324">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3324">Prototype</span></span>

```c
UINT fx_unicode_file_create(
    FX_MEDIA *media_ptr, 
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *short_name);
```

### <a name="description"></a><span data-ttu-id="aa949-3325">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3325">Description</span></span>

<span data-ttu-id="aa949-3326">このサービスでは、Unicode 名が付いたファイルが現在のデフォルト ディレクトリに作成されます。Unicode ソース名パラメーターではパス情報は使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3326">This service creates a Unicode-named file in the current default directory—no path information is allowed in the Unicode source name parameter.</span></span> <span data-ttu-id="aa949-3327">成功した場合は、新しく作成された Unicode ファイルの短い名前 (8.3 形式) がサービスによって返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3327">If successful, the short name (8.3 format) of the newly created Unicode file is returned by the service.</span></span>

> [!WARNING]
> <span data-ttu-id="aa949-3328">*Unicode ファイルに対するすべての操作 (開く、書き込み、読み取り、終了など) は、返された短い名前 (8.3 形式) を標準の FileX ファイル サービスに渡すことによって行う必要があります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3328">*All operations on the Unicode file (opening, writing, reading, closing, etc.) should be done by supplying the returned short name (8.3 format) to the standard FileX file services.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3329">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3329">Input Parameters</span></span>


- <span data-ttu-id="aa949-3330">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3330">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3331">**source_unicode_name**: 新しいファイルの Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3331">**source_unicode_name**: Pointer to the Unicode name for the new file.</span></span>
- <span data-ttu-id="aa949-3332">**source_unicode_length**: Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3332">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="aa949-3333">**short_name**: 新しい Unicode ファイルの短い名前 (8.3 形式) の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3333">**short_name**: Pointer to destination for short name (8.3 format) for the new Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3334">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3334">Return Values</span></span>

- <span data-ttu-id="aa949-3335">**FX_SUCCESS** (0x00) ファイルの作成に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3335">**FX_SUCCESS** (0x00) Successful file create.</span></span>
- <span data-ttu-id="aa949-3336">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3336">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3337">**FX_ALREADY_CREATED** (0x0B) 指定されたファイルは既に存在します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3337">**FX_ALREADY_CREATED** (0x0B) Specified file already exists.</span></span>
- <span data-ttu-id="aa949-3338">**FX_NO_MORE_SPACE** (0x0a) 新しいファイル エントリについて使用できるクラスターはメディア内にこれ以上ありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3338">**FX_NO_MORE_SPACE** (0x0A) No more clusters available in the media for the new file entry.</span></span>
- <span data-ttu-id="aa949-3339">**FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3339">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="aa949-3340">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3340">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3341">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-3341">**FX_WRITE_PROTECT** (0x23) Specified media is write protected.</span></span>
- <span data-ttu-id="aa949-3342">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3342">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="aa949-3343">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3343">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3344">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3344">Allowed From</span></span>

<span data-ttu-id="aa949-3345">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3345">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3346">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3346">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Create a Unicode file with the name contained in "my_unicode_name". */

length = fx_unicode_file_create(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the Unicode file is created and "my_short_name"
    contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3347">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3347">See Also</span></span>

- <span data-ttu-id="aa949-3348">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3348">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3349">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3349">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3350">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3350">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3351">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3351">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3352">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3352">fx_file_close</span></span>
- <span data-ttu-id="aa949-3353">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3353">fx_file_create</span></span>
- <span data-ttu-id="aa949-3354">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3354">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3355">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3355">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3356">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3356">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3357">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3357">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3358">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3358">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3359">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3359">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3360">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3360">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3361">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3361">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3362">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3362">fx_file_open</span></span>
- <span data-ttu-id="aa949-3363">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3363">fx_file_read</span></span>
- <span data-ttu-id="aa949-3364">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3364">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3365">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3365">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3366">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3366">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3367">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3367">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3368">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3368">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3369">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3369">fx_file_write</span></span>
- <span data-ttu-id="aa949-3370">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3370">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3371">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3371">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3372">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3372">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-3373">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3373">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_file_rename"></a><span data-ttu-id="aa949-3374">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3374">fx_unicode_file_rename</span></span>

<span data-ttu-id="aa949-3375">Unicode 文字列を使用してファイルの名前を変更します</span><span class="sxs-lookup"><span data-stu-id="aa949-3375">Renames a file using unicode string</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3376">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3376">Prototype</span></span>

```c
UINT fx_unicode_file_rename(
    FX_MEDIA *media_ptr, 
    UCHAR *old_unicode_name,
    ULONG old_unicode_length, 
    UCHAR *new_unicode_name,
    ULONG new_unicode_length, 
    CHAR *new_short_name);
```

### <a name="description"></a><span data-ttu-id="aa949-3377">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3377">Description</span></span>

<span data-ttu-id="aa949-3378">このサービスは、現在のデフォルト ディレクトリ内で、Unicode 名が付いたファイル名を、指定された新しい Unicode 名に変更します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3378">This service changes a Unicode-named file name to specified new Unicode name in current default directory.</span></span> <span data-ttu-id="aa949-3379">Unicode 名のパラメーターにパス情報を指定することはできません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3379">The Unicode name parameters must not have path information.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3380">*このサービスは、exFAT メディアではサポートされていません。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3380">*This service is not supported on exFAT media.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3381">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3381">Input Parameters</span></span>

- <span data-ttu-id="aa949-3382">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3382">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3383">**old_unicode_name**: 現在のファイルの Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3383">**old_unicode_name**: Pointer to the Unicode name for the current file.</span></span>
- <span data-ttu-id="aa949-3384">**old_unicode_name_length**: 現在の Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3384">**old_unicode_name_length**: Length of current Unicode name.</span></span>
- <span data-ttu-id="aa949-3385">**new_unicode_name**: 新しい Unicode ファイル名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3385">**new_unicode_name**: Pointer to the new Unicode file name.</span></span>
- <span data-ttu-id="aa949-3386">**new_unicode_name_length**: 新しい Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3386">**new_unicode_name_length**: Length of new Unicode name.</span></span>
- <span data-ttu-id="aa949-3387">**new_short_name**: 名前が変更された Unicode ファイルの短い名前 (8.3 形式) の宛先を指すポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3387">**new_short_name**: Pointer to destination for short name (8.3 format) for the renamed Unicode file.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3388">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3388">Return Values</span></span>


- <span data-ttu-id="aa949-3389">**FX_SUCCESS** (0x00) メディアのオープンに成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3389">**FX_SUCCESS** (0x00) Successful media open.</span></span>
- <span data-ttu-id="aa949-3390">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3390">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3391">**FX_ALREADY_CREATED** (0x0B) 指定されたファイル名は既に存在します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3391">**FX_ALREADY_CREATED** (0x0B) Specified file name already exists.</span></span>
- <span data-ttu-id="aa949-3392">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3392">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3393">**FX_PTR_ERROR** (0x18) 1 つ以上のポインターが NULL です。</span><span class="sxs-lookup"><span data-stu-id="aa949-3393">**FX_PTR_ERROR** (0x18) One or more pointers are NULL.</span></span>
- <span data-ttu-id="aa949-3394">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3394">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>
- <span data-ttu-id="aa949-3395">**FX_WRITE_PROTECT** (0x23) 指定されたメディアは書き込み保護されています。</span><span class="sxs-lookup"><span data-stu-id="aa949-3395">**FX_WRITE_PROTECT** (0x23) Specified media is write-protected.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3396">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3396">Allowed From</span></span>

<span data-ttu-id="aa949-3397">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3397">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3398">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3398">Example</span></span>

```c
FX_MEDIA             my_media;
UINT                 status;
UCHAR                 my_short_name[13];
UCHAR                 my_old_unicode_name[] = {'a', '\0', 'b', '\0', 'c', '\0', '\0', '\0'};
UCHAR                 my_new_unicode_name[] = {'d', '\0', 'e', '\0', 'f', '\0', '\0', '\0'};

/* Change the Unicode-named file "abc" to "def". */

status = fx_unicode_file_rename(&my_media, my_old_unicode_name,
    3, my_new_unicode_name, 3, my_short_name);

/* If status equals FX_SUCCESS, the file name was changed to "def" and
    "my_short_name" contains the 8.3 format name that can be used with other FileX services. */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3399">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3399">See Also</span></span>

- <span data-ttu-id="aa949-3400">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3400">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3401">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3401">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3402">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3402">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3403">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3403">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3404">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3404">fx_file_close</span></span>
- <span data-ttu-id="aa949-3405">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3405">fx_file_create</span></span>
- <span data-ttu-id="aa949-3406">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3406">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3407">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3407">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3408">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3408">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3409">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3409">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3410">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3410">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3411">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3411">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3412">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3412">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3413">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3413">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3414">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3414">fx_file_open</span></span>
- <span data-ttu-id="aa949-3415">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3415">fx_file_read</span></span>
- <span data-ttu-id="aa949-3416">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3416">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3417">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3417">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3418">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3418">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3419">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3419">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3420">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3420">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3421">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3421">fx_file_write</span></span>
- <span data-ttu-id="aa949-3422">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3422">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3423">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3423">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3424">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3424">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-3425">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3425">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get"></a><span data-ttu-id="aa949-3426">fx_unicode_length_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3426">fx_unicode_length_get</span></span>

<span data-ttu-id="aa949-3427">Unicode 名の長さを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3427">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3428">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3428">Prototype</span></span>

```c
ULONG fx_unicode_length_get(UCHAR *unicode_name);
```
### <a name="description"></a><span data-ttu-id="aa949-3429">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3429">Description</span></span>

<span data-ttu-id="aa949-3430">このサービスは、指定された Unicode 名の長さを判断します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3430">This service determines the length of the supplied Unicode name.</span></span> <span data-ttu-id="aa949-3431">Unicode 文字は 2 バイトで表されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3431">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="aa949-3432">Unicode 名は一連の 2 バイトの Unicode 文字で、2 つの NULL バイト (値 0 の 2 バイト) で終了します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3432">A Unicode name is a series of two byte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3433">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3433">Input Parameters</span></span>

<span data-ttu-id="aa949-3434">**unicode_name**: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3434">**unicode_name**: Pointer to Unicode name.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3435">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3435">Return Values</span></span>

<span data-ttu-id="aa949-3436">**length**: Unicode 名の長さ (名前に含まれる Unicode 文字の数)。</span><span class="sxs-lookup"><span data-stu-id="aa949-3436">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3437">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3437">Allowed From</span></span>

<span data-ttu-id="aa949-3438">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3438">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3439">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3439">Example</span></span>

```c
UCHAR     my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                           0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                           0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                           0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                           0x63,0x00, 0x00,0x00};

UINT     length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get(my_unicode_name);

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3440">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3440">See Also</span></span>

- <span data-ttu-id="aa949-3441">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3441">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3442">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3442">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3443">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3443">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3444">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3444">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3445">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3445">fx_file_close</span></span>
- <span data-ttu-id="aa949-3446">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3446">fx_file_create</span></span>
- <span data-ttu-id="aa949-3447">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3447">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3448">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3448">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3449">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3449">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3450">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3450">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3451">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3451">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3452">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3452">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3453">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3453">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3454">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3454">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3455">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3455">fx_file_open</span></span>
- <span data-ttu-id="aa949-3456">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3456">fx_file_read</span></span>
- <span data-ttu-id="aa949-3457">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3457">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3458">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3458">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3459">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3459">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3460">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3460">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3461">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3461">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3462">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3462">fx_file_write</span></span>
- <span data-ttu-id="aa949-3463">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3463">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3464">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3464">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3465">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3465">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3466">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3466">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-3467">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3467">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_length_get_extended"></a><span data-ttu-id="aa949-3468">fx_unicode_length_get_extended</span><span class="sxs-lookup"><span data-stu-id="aa949-3468">fx_unicode_length_get_extended</span></span>

<span data-ttu-id="aa949-3469">Unicode 名の長さを取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3469">Gets length of Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3470">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3470">Prototype</span></span>

```c
UINT fx_unicode_length_get_extended(
    UCHAR *unicode_name,
    UINT buffer_length);
```
### <a name="description"></a><span data-ttu-id="aa949-3471">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3471">Description</span></span>

<span data-ttu-id="aa949-3472">このサービスは、指定された Unicode 名の長さを取得します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3472">This service gets the length of the supplied Unicode name.</span></span> <span data-ttu-id="aa949-3473">Unicode 文字は 2 バイトで表されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3473">A Unicode character is represented by two bytes.</span></span> <span data-ttu-id="aa949-3474">Unicode 名は一連の 2 バイトの Unicode 文字で、2 つの NULL バイト (値 0 の 2 バイト) で終了します。</span><span class="sxs-lookup"><span data-stu-id="aa949-3474">A Unicode name is a series of twobyte Unicode characters terminated by two NULL bytes (two bytes of 0 value).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3475">*このサービスは **fx_unicode_length_get()** と同じですが、呼び出し元が、2 つの NULL 文字を含む **unicode_name** バッファーのサイズを渡す点が異なります。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3475">*This service is identical to **fx_unicode_length_get()** except the caller passes in the size of the **unicode_name** buffer, including the two NULL characters.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3476">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3476">Input Parameters</span></span>

- <span data-ttu-id="aa949-3477">**unicode_name**: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3477">**unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="aa949-3478">**buffer_length**: Unicode 名のバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3478">**buffer_length**: Size of Unicode name buffer.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3479">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3479">Return Values</span></span>

<span data-ttu-id="aa949-3480">**length**: Unicode 名の長さ (名前に含まれる Unicode 文字の数)。</span><span class="sxs-lookup"><span data-stu-id="aa949-3480">**length**: Length of Unicode name (number of Unicode characters in the name).</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3481">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3481">Allowed From</span></span>

<span data-ttu-id="aa949-3482">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3482">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3483">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3483">Example</span></span>

```c
UCHAR         my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                 0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                 0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                 0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                 0x63,0x00, 0x00,0x00};

UINT         length;

/* Get the length of "my_unicode_name". */

length = fx_unicode_length_get_extended(my_unicode_name, sizeof(my_unicode_name));

/* A value of 17 will be returned for the length of the "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3484">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3484">See Also</span></span>

- <span data-ttu-id="aa949-3485">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3485">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3486">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3486">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3487">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3487">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3488">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3488">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3489">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3489">fx_file_close</span></span>
- <span data-ttu-id="aa949-3490">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3490">fx_file_create</span></span>
- <span data-ttu-id="aa949-3491">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3491">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3492">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3492">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3493">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3493">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3494">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3494">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3495">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3495">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3496">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3496">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3497">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3497">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3498">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3498">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3499">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3499">fx_file_open</span></span>
- <span data-ttu-id="aa949-3500">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3500">fx_file_read</span></span>
- <span data-ttu-id="aa949-3501">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3501">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3502">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3502">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3503">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3503">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3504">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3504">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3505">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3505">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3506">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3506">fx_file_write</span></span>
- <span data-ttu-id="aa949-3507">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3507">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3508">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3508">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3509">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3509">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3510">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3510">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-3511">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3511">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get"></a><span data-ttu-id="aa949-3512">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3512">fx_unicode_name_get</span></span>

<span data-ttu-id="aa949-3513">短い名前から Unicode 名を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3513">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3514">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3514">Prototype</span></span>

```c
UINT fx_unicode_name_get(
    FX_MEDIA *media_ptr, 
    CHAR *source_short_name,
    UCHAR *destination_unicode_name, 
    ULONG *destination_unicode_length);
```

### <a name="description"></a><span data-ttu-id="aa949-3515">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3515">Description</span></span>

<span data-ttu-id="aa949-3516">このサービスは、現在のデフォルト ディレクトリ内の指定された短い名前 (8.3 形式) に関連付けられている Unicode 名を取得します。短い名前のパラメーターではパス情報は使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3516">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="aa949-3517">成功した場合、短い名前に関連付けられている Unicode 名がサービスによって返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3517">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3518">*このサービスを使用して、ファイルとサブディレクトリの両方の Unicode 名を取得できます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3518">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3519">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3519">Input Parameters</span></span>

- <span data-ttu-id="aa949-3520">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3520">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3521">**short_name**: 短い名前 (8.3 形式) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3521">**short_name** Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="aa949-3522">**destination_unicode_name**: 指定された短い名前に関連付けられている Unicode 名の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3522">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="aa949-3523">**destination_unicode_length**: 返された Unicode 名の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3523">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3524">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3524">Return Values</span></span>

- <span data-ttu-id="aa949-3525">**FX_SUCCESS** (0x00) Unicode 名の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3525">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="aa949-3526">**FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3526">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="aa949-3527">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-3527">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-3528">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3528">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3529">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3529">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3530">**FX_NOT_FOUND** (0x04) 短い名前が見つからなかったか、Unicode の宛先サイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3530">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="aa949-3531">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3531">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-3532">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3532">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="aa949-3533">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3533">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3534">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3534">Allowed From</span></span>

<span data-ttu-id="aa949-3535">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3535">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3536">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3536">Example</span></span>

```c
FX_MEDIA             ram_disk;
UCHAR                 my_unicode_name[256*2];
ULONG                 unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the
    number of maximum characters in the name. */

length = fx_unicode_name_get(&ram_disk, "ABC0~111.TXT", my_unicode_name, unicode_name_length);

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3537">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3537">See Also</span></span>

- <span data-ttu-id="aa949-3538">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3538">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3539">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3539">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3540">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3540">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3541">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3541">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3542">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3542">fx_file_close</span></span>
- <span data-ttu-id="aa949-3543">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3543">fx_file_create</span></span>
- <span data-ttu-id="aa949-3544">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3544">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3545">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3545">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3546">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3546">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3547">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3547">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3548">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3548">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3549">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3549">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3550">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3550">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3551">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3551">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3552">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3552">fx_file_open</span></span>
- <span data-ttu-id="aa949-3553">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3553">fx_file_read</span></span>
- <span data-ttu-id="aa949-3554">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3554">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3555">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3555">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3556">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3556">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3557">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3557">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3558">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3558">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3559">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3559">fx_file_write</span></span>
- <span data-ttu-id="aa949-3560">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3560">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3561">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3561">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3562">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3562">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3563">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3563">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_name_get_extended"></a><span data-ttu-id="aa949-3564">fx_unicode_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="aa949-3564">fx_unicode_name_get_extended</span></span>

<span data-ttu-id="aa949-3565">短い名前から Unicode 名を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3565">Gets Unicode name from short name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3566">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3566">Prototype</span></span>

```c
UINT fx_unicode_name_get_extended(
    FX_MEDIA *media_ptr,
    CHAR *source_short_name,
    UCHAR *destination_unicode_name,
    ULONG *destination_unicode_length,
    ULONG unicode_name_buffer_length);
```
### <a name="description"></a><span data-ttu-id="aa949-3567">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3567">Description</span></span>

<span data-ttu-id="aa949-3568">このサービスは、現在のデフォルト ディレクトリ内の指定された短い名前 (8.3 形式) に関連付けられている Unicode 名を取得します。短い名前のパラメーターではパス情報は使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3568">This service retrieves the Unicode-name associated with the supplied short name (8.3 format) within the current default directory—no path information is allowed in the short name parameter.</span></span> <span data-ttu-id="aa949-3569">成功した場合、短い名前に関連付けられている Unicode 名がサービスによって返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3569">If successful, the Unicode name associated with the short name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3570">\*このサービスは \***fx_unicode_name_get** _と同じですが、呼び出し元が入力引数として宛先の Unicode バッファーのサイズを指定する点が異なります。これにより、サービスでは宛先の Unicode バッファーが上書きされないことが保証されます_</span><span class="sxs-lookup"><span data-stu-id="aa949-3570">\*This service is identical to \***fx_unicode_name_get**_, except the caller supplies the size of the destination Unicode buffer as an input argument. This allows the service to guarantee that it will not overwrite the destination Unicode buffer_</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3571">*このサービスを使用して、ファイルとサブディレクトリの両方の Unicode 名を取得できます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3571">*This service can be used to get Unicode names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3572">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3572">Input Parameters</span></span>

- <span data-ttu-id="aa949-3573">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3573">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3574">**short_name**: 短い名前 (8.3 形式) へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3574">**short_name**: Pointer to short name (8.3 format).</span></span>
- <span data-ttu-id="aa949-3575">**destination_unicode_name**: 指定された短い名前に関連付けられている Unicode 名の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3575">**destination_unicode_name**: Pointer to the destination for the Unicode name associated with the supplied short name.</span></span>
- <span data-ttu-id="aa949-3576">**destination_unicode_length**: 返された Unicode 名の長さへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3576">**destination_unicode_length**: Pointer to returned Unicode name length.</span></span>
- <span data-ttu-id="aa949-3577">**unicode_name_buffer_length**: Unicode 名のバッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3577">**unicode_name_buffer_length**: Size of the Unicode name buffer.</span></span> <span data-ttu-id="aa949-3578">注: NULL 終端文字が必要です。これによって 1 バイトが追加されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3578">Note: A NULL terminator is required, which makes an extra byte.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3579">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3579">Return Values</span></span>

- <span data-ttu-id="aa949-3580">**FX_SUCCESS** (0x00) Unicode 名の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3580">**FX_SUCCESS** (0x00) Successful Unicode name retrieval.</span></span>
- <span data-ttu-id="aa949-3581">**FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3581">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="aa949-3582">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-3582">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-3583">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3583">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3584">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3584">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3585">**FX_NOT_FOUND** (0x04) 短い名前が見つからなかったか、Unicode の宛先サイズが小さすぎます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3585">**FX_NOT_FOUND** (0x04) Short name was not found or the Unicode destination size is too small.</span></span>
- <span data-ttu-id="aa949-3586">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3586">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-3587">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3587">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="aa949-3588">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3588">**FX_CALLER_ERROR** (0x20) Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3589">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3589">Allowed From</span></span>

<span data-ttu-id="aa949-3590">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3590">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3591">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3591">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_unicode_name[256*2];
ULONG             unicode_name_length;

/* Get the Unicode name associated with the short name "ABC0~111.TXT".
    Note that the Unicode destination must have 2 times the number of maximum characters in the name. */

length = fx_unicode_name_get_extended(&ram_disk, "ABC0~111.TXT",
    my_unicode_name,&unicode_name_length, sizeof(ny_unicode_name));

/* If successful, the Unicode name is returned in "my_unicode_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3592">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3592">See Also</span></span>

- <span data-ttu-id="aa949-3593">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3593">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3594">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3594">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3595">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3595">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3596">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3596">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3597">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3597">fx_file_close</span></span>
- <span data-ttu-id="aa949-3598">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3598">fx_file_create</span></span>
- <span data-ttu-id="aa949-3599">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3599">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3600">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3600">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3601">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3601">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3602">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3602">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3603">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3603">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3604">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3604">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3605">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3605">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3606">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3606">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3607">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3607">fx_file_open</span></span>
- <span data-ttu-id="aa949-3608">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3608">fx_file_read</span></span>
- <span data-ttu-id="aa949-3609">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3609">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3610">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3610">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3611">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3611">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3612">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3612">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3613">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3613">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3614">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3614">fx_file_write</span></span>
- <span data-ttu-id="aa949-3615">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3615">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3616">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3616">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3617">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3617">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3618">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3618">fx_unicode_short_name_get</span></span>

## <a name="fx_unicode_short_name_get"></a><span data-ttu-id="aa949-3619">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3619">fx_unicode_short_name_get</span></span>

<span data-ttu-id="aa949-3620">Unicode 名から短い名前を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3620">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3621">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3621">Prototype</span></span>

```c
UINT fx_unicode_short_name_get(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length,
    CHAR *destination_short_name);
```

<span data-ttu-id="aa949-3622">このサービスは、現在のデフォルト ディレクトリ内で Unicode 名に関連付けられている短い名前 (8.3 形式) を取得します。Unicode 名のパラメーターではパス情報は使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3622">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="aa949-3623">成功した場合、Unicode 名に関連付けられている短い名前がサービスによって返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3623">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3624">*このサービスを使用して、ファイルとサブディレクトリの両方の短い名前を取得できます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3624">*This service can be used to get short names for both files and subdirectories.*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3625">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3625">Input Parameters</span></span>

- <span data-ttu-id="aa949-3626">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3626">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3627">**source_unicode_name**: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3627">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="aa949-3628">**source_unicode_length**: Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3628">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="aa949-3629">**destination_short_name**: 短い名前 (8.3 形式) の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3629">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="aa949-3630">これは、少なくとも 13 バイトのサイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-3630">This must be at least 13 bytes in size.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3631">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3631">Return Values</span></span>

- <span data-ttu-id="aa949-3632">**FX_SUCCESS** (0x00) 短い名前の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3632">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="aa949-3633">**FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3633">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="aa949-3634">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-3634">**FX_FILE_CORRUPT** (0x08) File is corrupted</span></span>
- <span data-ttu-id="aa949-3635">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3635">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3636">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3636">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3637">**FX_NOT_FOUND** (0x04) Unicode 名が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-3637">**FX_NOT_FOUND** (0x04)    Unicode name was not found.</span></span>
- <span data-ttu-id="aa949-3638">**FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3638">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="aa949-3639">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3639">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-3640">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3640">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="aa949-3641">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3641">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3642">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3642">Allowed From</span></span>

<span data-ttu-id="aa949-3643">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3643">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3644">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3644">Example</span></span>

```c
FX_MEDIA         ram_disk;
UCHAR             my_short_name[13];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get(&ram_disk, my_unicode_name, 17, my_short_name);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3645">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3645">See Also</span></span>

- <span data-ttu-id="aa949-3646">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3646">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3647">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3647">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3648">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3648">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3649">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3649">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3650">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3650">fx_file_close</span></span>
- <span data-ttu-id="aa949-3651">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3651">fx_file_create</span></span>
- <span data-ttu-id="aa949-3652">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3652">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3653">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3653">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3654">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3654">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3655">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3655">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3656">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3656">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3657">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3657">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3658">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3658">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3659">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3659">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3660">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3660">fx_file_open</span></span>
- <span data-ttu-id="aa949-3661">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3661">fx_file_read</span></span>
- <span data-ttu-id="aa949-3662">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3662">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3663">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3663">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3664">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3664">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3665">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3665">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3666">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3666">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3667">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3667">fx_file_write</span></span>
- <span data-ttu-id="aa949-3668">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3668">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3669">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3669">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3670">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3670">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3671">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3671">fx_unicode_name_get</span></span>

## <a name="fx_unicode_short_name_get_extended"></a><span data-ttu-id="aa949-3672">fx_unicode_short_name_get_extended</span><span class="sxs-lookup"><span data-stu-id="aa949-3672">fx_unicode_short_name_get_extended</span></span>

<span data-ttu-id="aa949-3673">Unicode 名から短い名前を取得します</span><span class="sxs-lookup"><span data-stu-id="aa949-3673">Gets short name from Unicode name</span></span>

### <a name="prototype"></a><span data-ttu-id="aa949-3674">プロトタイプ</span><span class="sxs-lookup"><span data-stu-id="aa949-3674">Prototype</span></span>

```c
UINT fx_unicode_short_name_get_extended(
    FX_MEDIA *media_ptr,
    UCHAR *source_unicode_name,
    ULONG source_unicode_length, 
    CHAR *destination_short_name,
    ULONG short_name_buffer_length);
```

### <a name="description"></a><span data-ttu-id="aa949-3675">説明</span><span class="sxs-lookup"><span data-stu-id="aa949-3675">Description</span></span>

<span data-ttu-id="aa949-3676">このサービスは、現在のデフォルト ディレクトリ内で Unicode 名に関連付けられている短い名前 (8.3 形式) を取得します。Unicode 名のパラメーターではパス情報は使用できません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3676">This service retrieves the short name (8.3 format) associated with the Unicode-name within the current default directory—no path information is allowed in the Unicode name parameter.</span></span> <span data-ttu-id="aa949-3677">成功した場合、Unicode 名に関連付けられている短い名前がサービスによって返されます。</span><span class="sxs-lookup"><span data-stu-id="aa949-3677">If successful, the short name associated with the Unicode name is returned by the service.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="aa949-3678">*このサービスは **fx_unicode_short_name_get()** と同じですが、呼び出し元が入力引数として宛先バッファーのサイズを指定する点が異なります。これにより、サービスでは短い名前が宛先バッファーを超えないことが保証されます。*</span><span class="sxs-lookup"><span data-stu-id="aa949-3678">*This service is identical to **fx_unicode_short_name_get()**, except the caller supplies the size of the destination buffer as an input argument. This allows the service to guarantee the short name does not exceed the destination buffer.*</span></span>

<span data-ttu-id="aa949-3679">*このサービスを使用して、ファイルとサブディレクトリの両方の短い名前を取得できます*</span><span class="sxs-lookup"><span data-stu-id="aa949-3679">*This service can be used to get short names for both files and subdirectories*</span></span>

### <a name="input-parameters"></a><span data-ttu-id="aa949-3680">入力パラメーター</span><span class="sxs-lookup"><span data-stu-id="aa949-3680">Input Parameters</span></span>

- <span data-ttu-id="aa949-3681">**media_ptr**: メディア コントロール ブロックへのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3681">**media_ptr**: Pointer to media control block.</span></span>
- <span data-ttu-id="aa949-3682">**source_unicode_name**: Unicode 名へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3682">**source_unicode_name**: Pointer to Unicode name.</span></span>
- <span data-ttu-id="aa949-3683">**source_unicode_length**: Unicode 名の長さ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3683">**source_unicode_length**: Length of Unicode name.</span></span>
- <span data-ttu-id="aa949-3684">**destination_short_name**: 短い名前 (8.3 形式) の宛先へのポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3684">**destination_short_name**: Pointer to destination for the short name (8.3 format).</span></span> <span data-ttu-id="aa949-3685">これは、少なくとも 13 バイトのサイズである必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-3685">This must be at least 13 bytes in size.</span></span>
- <span data-ttu-id="aa949-3686">**short_name_buffer_length**: 宛先バッファーのサイズ。</span><span class="sxs-lookup"><span data-stu-id="aa949-3686">**short_name_buffer_length**: Size of the destination buffer.</span></span> <span data-ttu-id="aa949-3687">バッファー サイズは 14 バイト以上である必要があります。</span><span class="sxs-lookup"><span data-stu-id="aa949-3687">The buffer size must be at least 14 bytes.</span></span>

### <a name="return-values"></a><span data-ttu-id="aa949-3688">戻り値</span><span class="sxs-lookup"><span data-stu-id="aa949-3688">Return Values</span></span>

- <span data-ttu-id="aa949-3689">**FX_SUCCESS** (0x00) 短い名前の取得に成功しました。</span><span class="sxs-lookup"><span data-stu-id="aa949-3689">**FX_SUCCESS** (0x00) Successful short name retrieval.</span></span>
- <span data-ttu-id="aa949-3690">**FX_FAT_READ_ERROR** (0x03) FAT テーブルを読み取ることができません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3690">**FX_FAT_READ_ERROR** (0x03) Unable to read FAT table.</span></span>
- <span data-ttu-id="aa949-3691">**FX_FILE_CORRUPT** (0x08) ファイルが破損しています</span><span class="sxs-lookup"><span data-stu-id="aa949-3691">**FX_FILE_CORRUPT** (0x08)    File is corrupted</span></span>
- <span data-ttu-id="aa949-3692">**FX_IO_ERROR** (0x90) ドライバーの I/O エラー。</span><span class="sxs-lookup"><span data-stu-id="aa949-3692">**FX_IO_ERROR** (0x90) Driver I/O error.</span></span>
- <span data-ttu-id="aa949-3693">**FX_MEDIA_NOT_OPEN** (0x11) 指定されたメディアが開いていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3693">**FX_MEDIA_NOT_OPEN** (0x11) Specified media is not open.</span></span>
- <span data-ttu-id="aa949-3694">**FX_NOT_FOUND** (0x04) Unicode 名が見つかりませんでした。</span><span class="sxs-lookup"><span data-stu-id="aa949-3694">**FX_NOT_FOUND** (0x04) Unicode name was not found.</span></span>
- <span data-ttu-id="aa949-3695">**FX_NOT_IMPLEMENTED** (0x22) サービスは exFAT ファイル システム用に実装されていません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3695">**FX_NOT_IMPLEMENTED** (0x22) Service not implemented for exFAT file system.</span></span>
- <span data-ttu-id="aa949-3696">**FX_SECTOR_INVALID** (0x89) 無効なセクター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3696">**FX_SECTOR_INVALID** (0x89) Invalid sector.</span></span>
- <span data-ttu-id="aa949-3697">**FX_PTR_ERROR** (0x18) 無効なメディアまたは名前のポインター。</span><span class="sxs-lookup"><span data-stu-id="aa949-3697">**FX_PTR_ERROR** (0x18) Invalid media or name pointers.</span></span>
- <span data-ttu-id="aa949-3698">**FX_CALLER_ERROR** (0x20) 呼び出し元はスレッドではありません。</span><span class="sxs-lookup"><span data-stu-id="aa949-3698">**FX_CALLER_ERROR** (0x20)    Caller is not a thread.</span></span>

### <a name="allowed-from"></a><span data-ttu-id="aa949-3699">許可元</span><span class="sxs-lookup"><span data-stu-id="aa949-3699">Allowed From</span></span>

<span data-ttu-id="aa949-3700">Threads</span><span class="sxs-lookup"><span data-stu-id="aa949-3700">Threads</span></span>

### <a name="example"></a><span data-ttu-id="aa949-3701">例</span><span class="sxs-lookup"><span data-stu-id="aa949-3701">Example</span></span>

```c
#define         SHORT_NAME_BUFFER_SIZE 13
FX_MEDIA         ram_disk;
UCHAR             my_short_name[SHORT_NAME_BUFFER_SIZE];
UCHAR             my_unicode_name[] = {0x38,0xC1, 0x88,0xBC, 0xF8,0xC9, 0x20,0x00,
                                     0x54,0xD6, 0x7C,0xC7, 0x20,0x00, 0x74,0xC7,
                                     0x84,0xB9, 0x20,0x00, 0x85,0xC7, 0xC8,0xB2,
                                     0xE4,0xB2, 0x2E,0x00, 0x64,0x00, 0x6F,0x00,
                                     0x63,0x00, 0x00,0x00};

/* Get the short name associated with the Unicode name contained in the array "my_unicode_name". */

length = fx_unicode_short_name_get_extended(&ram_disk,
    my_unicode_name, 17, my_short_name,SHORT_NAME_BUFFER_SIZE);

/* If successful, the short name is returned in "my_short_name". */
```

### <a name="see-also"></a><span data-ttu-id="aa949-3702">参照</span><span class="sxs-lookup"><span data-stu-id="aa949-3702">See Also</span></span>

- <span data-ttu-id="aa949-3703">fx_file_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3703">fx_file_allocate</span></span>
- <span data-ttu-id="aa949-3704">fx_file_attributes_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3704">fx_file_attributes_read</span></span>
- <span data-ttu-id="aa949-3705">fx_file_attributes_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3705">fx_file_attributes_set</span></span>
- <span data-ttu-id="aa949-3706">fx_file_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3706">fx_file_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3707">fx_file_close</span><span class="sxs-lookup"><span data-stu-id="aa949-3707">fx_file_close</span></span>
- <span data-ttu-id="aa949-3708">fx_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3708">fx_file_create</span></span>
- <span data-ttu-id="aa949-3709">fx_file_date_time_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3709">fx_file_date_time_set</span></span>
- <span data-ttu-id="aa949-3710">fx_file_delete</span><span class="sxs-lookup"><span data-stu-id="aa949-3710">fx_file_delete</span></span>
- <span data-ttu-id="aa949-3711">fx_file_extended_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3711">fx_file_extended_allocate</span></span>
- <span data-ttu-id="aa949-3712">fx_file_extended_best_effort_allocate</span><span class="sxs-lookup"><span data-stu-id="aa949-3712">fx_file_extended_best_effort_allocate</span></span>
- <span data-ttu-id="aa949-3713">fx_file_extended_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3713">fx_file_extended_relative_seek</span></span>
- <span data-ttu-id="aa949-3714">fx_file_extended_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3714">fx_file_extended_seek</span></span>
- <span data-ttu-id="aa949-3715">fx_file_extended_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3715">fx_file_extended_truncate</span></span>
- <span data-ttu-id="aa949-3716">fx_file_extended_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3716">fx_file_extended_truncate_release</span></span>
- <span data-ttu-id="aa949-3717">fx_file_open</span><span class="sxs-lookup"><span data-stu-id="aa949-3717">fx_file_open</span></span>
- <span data-ttu-id="aa949-3718">fx_file_read</span><span class="sxs-lookup"><span data-stu-id="aa949-3718">fx_file_read</span></span>
- <span data-ttu-id="aa949-3719">fx_file_relative_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3719">fx_file_relative_seek</span></span>
- <span data-ttu-id="aa949-3720">fx_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3720">fx_file_rename</span></span>
- <span data-ttu-id="aa949-3721">fx_file_seek</span><span class="sxs-lookup"><span data-stu-id="aa949-3721">fx_file_seek</span></span>
- <span data-ttu-id="aa949-3722">fx_file_truncate</span><span class="sxs-lookup"><span data-stu-id="aa949-3722">fx_file_truncate</span></span>
- <span data-ttu-id="aa949-3723">fx_file_truncate_release</span><span class="sxs-lookup"><span data-stu-id="aa949-3723">fx_file_truncate_release</span></span>
- <span data-ttu-id="aa949-3724">fx_file_write</span><span class="sxs-lookup"><span data-stu-id="aa949-3724">fx_file_write</span></span>
- <span data-ttu-id="aa949-3725">fx_file_write_notify_set</span><span class="sxs-lookup"><span data-stu-id="aa949-3725">fx_file_write_notify_set</span></span>
- <span data-ttu-id="aa949-3726">fx_unicode_file_create</span><span class="sxs-lookup"><span data-stu-id="aa949-3726">fx_unicode_file_create</span></span>
- <span data-ttu-id="aa949-3727">fx_unicode_file_rename</span><span class="sxs-lookup"><span data-stu-id="aa949-3727">fx_unicode_file_rename</span></span>
- <span data-ttu-id="aa949-3728">fx_unicode_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3728">fx_unicode_name_get</span></span>
- <span data-ttu-id="aa949-3729">fx_unicode_short_name_get</span><span class="sxs-lookup"><span data-stu-id="aa949-3729">fx_unicode_short_name_get</span></span>
