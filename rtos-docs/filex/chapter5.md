---
title: 第 5 章 - Azure RTOS FileX 用 I/O ドライバー
description: この章は、Azure RTOS FileX 用 I/O ドライバーの説明であり、開発者がアプリケーション固有のドライバーを記述できるように作られています。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b44822b9d8f16208cf470a84013be5a5ff833325
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811354"
---
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a><span data-ttu-id="c4098-103">第 5 章 - Azure RTOS FileX 用 I/O ドライバー</span><span class="sxs-lookup"><span data-stu-id="c4098-103">Chapter 5 - I/O Drivers for Azure RTOS FileX</span></span>

<span data-ttu-id="c4098-104">この章は、Azure RTOS FileX 用 I/O ドライバーの説明であり、開発者がアプリケーション固有のドライバーを記述できるように作られています。</span><span class="sxs-lookup"><span data-stu-id="c4098-104">This chapter contains a description of I/O drivers for Azure RTOS FileX and is designed to help developers write application-specific drivers.</span></span>

## <a name="io-driver-introduction"></a><span data-ttu-id="c4098-105">I/O ドライバーの概要</span><span class="sxs-lookup"><span data-stu-id="c4098-105">I/O Driver Introduction</span></span>

<span data-ttu-id="c4098-106">FileX では、複数のメディア デバイスがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="c4098-106">FileX supports multiple media devices.</span></span> <span data-ttu-id="c4098-107">FX_MEDIA 構造体で、メディア デバイスを管理するために必要なすべての情報が定義されています。</span><span class="sxs-lookup"><span data-stu-id="c4098-107">The FX_MEDIA structure defines everything required to manage a media device.</span></span> <span data-ttu-id="c4098-108">この構造体には、メディア固有の I/O ドライバーや、ドライバーと FileX の間で情報と状態を受け渡すための関連パラメーターなど、すべてのメディア情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="c4098-108">This structure contains all media information, including the media-specific I/O driver and associated parameters for passing information and status between the driver and FileX.</span></span> <span data-ttu-id="c4098-109">ほとんどのシステムでは、FileX メディア インスタンスごとに一意の I/O ドライバーがあります。</span><span class="sxs-lookup"><span data-stu-id="c4098-109">In most systems, there is a unique I/O driver for each FileX media instance.</span></span>

## <a name="io-driver-entry"></a><span data-ttu-id="c4098-110">I/O ドライバーのエントリ</span><span class="sxs-lookup"><span data-stu-id="c4098-110">I/O Driver Entry</span></span>

<span data-ttu-id="c4098-111">各 FileX I/O ドライバーには、***fx_media_open*** サービス呼び出しによって定義されている 1 つのエントリ関数があります。</span><span class="sxs-lookup"><span data-stu-id="c4098-111">Each FileX I/O driver has a single entry function that is defined by the ***fx_media_open*** service call.</span></span> <span data-ttu-id="c4098-112">ドライバー エントリ関数の形式は次のとおりです:</span><span class="sxs-lookup"><span data-stu-id="c4098-112">The driver entry function has the following format:</span></span>

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

<span data-ttu-id="c4098-113">FileX により、I/O ドライバーのエントリ関数が呼び出されて、すべての物理メディアへのアクセスが要求されます。これには、初期化とブート セクターの読み取りが含まれます。</span><span class="sxs-lookup"><span data-stu-id="c4098-113">FileX calls the I/O driver entry function to request all physical media access, including initialization and boot sector reading.</span></span> <span data-ttu-id="c4098-114">ドライバーに対する要求は順番に実行されます。つまり、FileX は、現在の要求が完了して、別の要求が送信されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="c4098-114">Requests made to the driver are done sequentially; i.e., FileX waits for the current request to complete before another request is sent.</span></span>

## <a name="io-driver-requests"></a><span data-ttu-id="c4098-115">I/O ドライバーの要求</span><span class="sxs-lookup"><span data-stu-id="c4098-115">I/O Driver Requests</span></span>

<span data-ttu-id="c4098-116">各 I/O ドライバーには単一のエントリ関数があるため、FileX による特定の要求はメディア制御ブロックを通じて行われます。</span><span class="sxs-lookup"><span data-stu-id="c4098-116">Because each I/O driver has a single entry function, FileX makes specific requests through the media control block.</span></span> <span data-ttu-id="c4098-117">具体的には、正確なドライバー要求を指定するには、**FX_MEDIA** の **fx_media_driver_request** メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-117">Specifically, the  **fx_media_driver_request** member of **FX_MEDIA** is used to specify the exact driver request.</span></span> <span data-ttu-id="c4098-118">I/O ドライバーによる要求の成功または失敗の通知は、**FX_MEDIA** の **fx_media_driver_status** メンバーを通じて行われます。</span><span class="sxs-lookup"><span data-stu-id="c4098-118">The I/O driver communicates the success or failure of the request through the **fx_media_driver_status** member of **FX_MEDIA**.</span></span> <span data-ttu-id="c4098-119">ドライバーの要求が成功した場合、ドライバーから制御が戻る前に、このフィールドに **FX_SUCCESS** が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-119">If the driver request was successful, **FX_SUCCESS** is placed in this field before the driver returns.</span></span> <span data-ttu-id="c4098-120">それ以外で、エラーが検出された場合は、このフィールドに FX_IO_ERROR が設定されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-120">Otherwise, if an error is detected, FX_IO_ERROR is placed in this field.</span></span>

### <a name="driver-initialization"></a><span data-ttu-id="c4098-121">ドライバーの初期化</span><span class="sxs-lookup"><span data-stu-id="c4098-121">Driver Initialization</span></span>

<span data-ttu-id="c4098-122">実際のドライバー初期化処理はアプリケーションごとに異なりますが、通常は、データ構造体の初期化と、必要に応じた、ハードウェアのいくつかの事前初期化で構成されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-122">Although the actual driver initialization processing is application specific, it usually consists of data structure initialization and possibly some preliminary hardware initialization.</span></span> <span data-ttu-id="c4098-123">この要求は、最初に FileX によって行われ、fx_media_open サービス内から実行されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-123">This request is the first made by FileX and is done from within the fx_media_open service.</span></span>

<span data-ttu-id="c4098-124">メディア書き込み保護が検出された場合は、ドライバーの FX_MEDIA の fx_media_driver_write_protect メンバーが FX_TRUE に設定されているはずです。</span><span class="sxs-lookup"><span data-stu-id="c4098-124">If media write protection is detected, the driver fx_media_driver_write_protect member of FX_MEDIA should be set to FX_TRUE.</span></span>

<span data-ttu-id="c4098-125">I/O ドライバーの初期化要求には、次の FX_MEDIA メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-125">The following FX_MEDIA members are used for the I/O driver initialization request:</span></span>

|<span data-ttu-id="c4098-126">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-126">FX_MEDIA member</span></span>|<span data-ttu-id="c4098-127">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-127">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-128">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-128">fx_media_driver_request</span></span>|<span data-ttu-id="c4098-129">FX_DRIVER_INIT</span><span class="sxs-lookup"><span data-stu-id="c4098-129">FX_DRIVER_INIT</span></span>|

<span data-ttu-id="c4098-130">FileX には、セクターが使用されなくなったときにアプリケーション ドライバーに通知するメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="c4098-130">FileX provides a mechanism to inform the application driver when sectors are no longer being used.</span></span> <span data-ttu-id="c4098-131">これは、FLASH にマップされているすべての使用中論理セクターを管理する必要がある FLASH メモリ マネージャーに特に便利です。</span><span class="sxs-lookup"><span data-stu-id="c4098-131">This is especially useful for FLASH memory managers that must manage all in-use logical sectors mapped to the FLASH.</span></span>

<span data-ttu-id="c4098-132">空きセクターのそのような通知が必要な場合は、アプリケーション ドライバーで単に、関連付けられた **FX_MEDIA** 構造体の *fx_media_driver_free_sector_update* フィールドを **FX_TRUE** に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4098-132">If such notification of free sectors is required, the application driver simply sets the *fx_media_driver_free_sector_update* field in the associated **FX_MEDIA** structure to **FX_TRUE**.</span></span> <span data-ttu-id="c4098-133">設定した後、FileX により、1 つ以上の連続するセクターが空きセクターになったことを示す **_FX_DRIVER_RELEASE_SECTORS_** I/O ドライバー呼び出しが行われます。</span><span class="sxs-lookup"><span data-stu-id="c4098-133">After set, FileX makes a **_FX_DRIVER_RELEASE_SECTORS_** I/O driver call indicating when one or more consecutive sectors becomes free.</span></span>

### <a name="boot-sector-read"></a><span data-ttu-id="c4098-134">ブート セクターの読み取り</span><span class="sxs-lookup"><span data-stu-id="c4098-134">Boot Sector Read</span></span>

<span data-ttu-id="c4098-135">標準の読み取り要求を使用する代わりに、メディアのブート セクターを読み取る特定の要求が FileX によって行われます。</span><span class="sxs-lookup"><span data-stu-id="c4098-135">Instead of using a standard read request, FileX makes a specific request to read the media's boot sector.</span></span> <span data-ttu-id="c4098-136">I/O ドライバーのブート セクター読み取り要求には、次の **FX_MEDIA** メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-136">The following **FX_MEDIA** members are used for the I/O driver boot sector read request:</span></span>

|<span data-ttu-id="c4098-137">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-137">FX_MEDIA member</span></span>|<span data-ttu-id="c4098-138">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-138">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-139">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-139">fx_media_driver_request</span></span>| <span data-ttu-id="c4098-140">FX_DRIVER_BOOT_READ</span><span class="sxs-lookup"><span data-stu-id="c4098-140">FX_DRIVER_BOOT_READ</span></span>|
|<span data-ttu-id="c4098-141">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="c4098-141">fx_media_driver_buffer</span></span>| <span data-ttu-id="c4098-142">ブート セクターの読み取り先のアドレス。</span><span class="sxs-lookup"><span data-stu-id="c4098-142">Address of destination for boot sector.</span></span>|

### <a name="boot-sector-write"></a><span data-ttu-id="c4098-143">ブート セクターの書き込み</span><span class="sxs-lookup"><span data-stu-id="c4098-143">Boot Sector Write</span></span>

<span data-ttu-id="c4098-144">標準の書き込み要求を使用する代わりに、メディアのブート セクターを書き込む特定の要求が FileX によって行われます。</span><span class="sxs-lookup"><span data-stu-id="c4098-144">Instead of using a standard write request, FileX makes a specific request to write the media's boot sector.</span></span> <span data-ttu-id="c4098-145">I/O ドライバーのブート セクター書き込み要求には、次の **FX_MEDIA** メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-145">The following **FX_MEDIA** members are used for the I/O driver boot sector write request:</span></span>

|<span data-ttu-id="c4098-146">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-146">FX_MEDIA member</span></span>|<span data-ttu-id="c4098-147">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-147">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-148">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-148">fx_media_driver_request</span></span>| <span data-ttu-id="c4098-149">FX_DRIVER_BOOT_WRITE</span><span class="sxs-lookup"><span data-stu-id="c4098-149">FX_DRIVER_BOOT_WRITE</span></span>|
|<span data-ttu-id="c4098-150">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="c4098-150">fx_media_driver_buffer</span></span>| <span data-ttu-id="c4098-151">ブート セクターの書き込み元のアドレス。</span><span class="sxs-lookup"><span data-stu-id="c4098-151">Address of source for boot sector.</span></span>|

### <a name="sector-read"></a><span data-ttu-id="c4098-152">セクターの読み取り</span><span class="sxs-lookup"><span data-stu-id="c4098-152">Sector Read</span></span>

<span data-ttu-id="c4098-153">FileX により、I/O ドライバーに読み取り要求を発行することにより、1 つ以上のセクターがメモリに読み取られます。</span><span class="sxs-lookup"><span data-stu-id="c4098-153">FileX reads one or more sectors into memory by issuing a read request to the I/O driver.</span></span> <span data-ttu-id="c4098-154">I/O ドライバーの読み取り要求には、次の **FX_MEDIA** メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-154">The following **FX_MEDIA** members are used for the I/O driver read request:</span></span>

|<span data-ttu-id="c4098-155">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-155">FX_MEDIA member</span></span>|<span data-ttu-id="c4098-156">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-156">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-157">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-157">fx_media_driver_request</span></span>| <span data-ttu-id="c4098-158">FX_DRIVER_READ</span><span class="sxs-lookup"><span data-stu-id="c4098-158">FX_DRIVER_READ</span></span>|
|<span data-ttu-id="c4098-159">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="c4098-159">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="c4098-160">読み取る論理セクター</span><span class="sxs-lookup"><span data-stu-id="c4098-160">Logical sector to read</span></span>|
|<span data-ttu-id="c4098-161">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="c4098-161">fx_media_driver_sectors</span></span>|<span data-ttu-id="c4098-162">読み取るセクターの数</span><span class="sxs-lookup"><span data-stu-id="c4098-162">Number of sectors to read</span></span>|
|<span data-ttu-id="c4098-163">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="c4098-163">fx_media_driver_buffer</span></span>|<span data-ttu-id="c4098-164">セクターの読み取り先バッファー</span><span class="sxs-lookup"><span data-stu-id="c4098-164">Destination buffer for sector(s) read</span></span>|
|<span data-ttu-id="c4098-165">fx_media_driver_data_sector_read</span><span class="sxs-lookup"><span data-stu-id="c4098-165">fx_media_driver_data_sector_read</span></span>|<span data-ttu-id="c4098-166">ファイル データ セクターを要求する場合は FX_TRUE に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4098-166">Set to FX_TRUE if a file data sector is requested.</span></span> <span data-ttu-id="c4098-167">それ以外で、システム セクター (FAT またはディレクトリ セクター) を要する場合は、FX_FALSE に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4098-167">Otherwise, FX_FALSE if a system sector (FAT or directory sector) is requested.</span></span>|
|<span data-ttu-id="c4098-168">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="c4098-168">fx_media_driver_sector_type</span></span>|<span data-ttu-id="c4098-169">要求するセクターの明示的な種類を次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="c4098-169">Defines the explicit type of sector requested, as follows:</span></span><br /><span data-ttu-id="c4098-170">FX_FAT_SECTOR (2)</span><span class="sxs-lookup"><span data-stu-id="c4098-170">FX_FAT_SECTOR (2)</span></span><br /><span data-ttu-id="c4098-171">FX_DIRECTORY_SECTOR (3)</span><span class="sxs-lookup"><span data-stu-id="c4098-171">FX_DIRECTORY_SECTOR (3)</span></span><br /><span data-ttu-id="c4098-172">FX_DATA_SECTOR (4)</span><span class="sxs-lookup"><span data-stu-id="c4098-172">FX_DATA_SECTOR (4)</span></span>|

### <a name="sector-write"></a><span data-ttu-id="c4098-173">セクターの書き込み</span><span class="sxs-lookup"><span data-stu-id="c4098-173">Sector Write</span></span>

<span data-ttu-id="c4098-174">FileX により、I/O ドライバーへの書き込み要求を発行することで、物理メディアに 1 つ以上のセクターが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="c4098-174">FileX writes one or more sectors to the physical media by issuing a write request to the I/O driver.</span></span> <span data-ttu-id="c4098-175">I/O ドライバーの書き込み要求には、次の FX_MEDIA メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-175">The following FX_MEDIA members are used for the I/O driver write request:</span></span>

|<span data-ttu-id="c4098-176">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-176">FX_MEDIA member</span></span>| <span data-ttu-id="c4098-177">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-177">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-178">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-178">fx_media_driver_request</span></span>|<span data-ttu-id="c4098-179">FX_DRIVER_WRITE</span><span class="sxs-lookup"><span data-stu-id="c4098-179">FX_DRIVER_WRITE</span></span>|
|<span data-ttu-id="c4098-180">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="c4098-180">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="c4098-181">書き込む論理セクター</span><span class="sxs-lookup"><span data-stu-id="c4098-181">Logical sector to write</span></span>|
|<span data-ttu-id="c4098-182">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="c4098-182">fx_media_driver_sectors</span></span>|<span data-ttu-id="c4098-183">書き込むセクターの数</span><span class="sxs-lookup"><span data-stu-id="c4098-183">Number of sectors to write</span></span>|
|<span data-ttu-id="c4098-184">fx_media_driver_buffer</span><span class="sxs-lookup"><span data-stu-id="c4098-184">fx_media_driver_buffer</span></span>|<span data-ttu-id="c4098-185">書き込むセクターの書き込み元バッファー</span><span class="sxs-lookup"><span data-stu-id="c4098-185">Source buffer for sector(s) to write</span></span>|
|<span data-ttu-id="c4098-186">fx_media_driver_system_write</span><span class="sxs-lookup"><span data-stu-id="c4098-186">fx_media_driver_system_write</span></span>| <span data-ttu-id="c4098-187">システム セクター (FAT またはディレクトリ セクター) を要求する場合は、FX_TRUE に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4098-187">Set to FX_TRUE if a system sector is requested (FAT or directory sector).</span></span> <span data-ttu-id="c4098-188">それ以外で、ファイル データ セクターを要求する場合は、FX_FALSE に設定します。</span><span class="sxs-lookup"><span data-stu-id="c4098-188">Otherwise, FX_FALSE if a file data sector is requested.</span></span>|
|<span data-ttu-id="c4098-189">fx_media_driver_sector_type</span><span class="sxs-lookup"><span data-stu-id="c4098-189">fx_media_driver_sector_type</span></span>|<span data-ttu-id="c4098-190">要求するセクターの明示的な種類を次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="c4098-190">Defines the explicit type of sector requested, as follows:</span></span>
<span data-ttu-id="c4098-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span><span class="sxs-lookup"><span data-stu-id="c4098-191">FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|</span></span>

### <a name="driver-flush"></a><span data-ttu-id="c4098-192">ドライバーのフラッシュ</span><span class="sxs-lookup"><span data-stu-id="c4098-192">Driver Flush</span></span>

<span data-ttu-id="c4098-193">FileX によって、I/O ドライバーへのフラッシュ要求を発行することで、現在ドライバーのセクター キャッシュにあるすべてのセクターが物理メディアにフラッシュされます。</span><span class="sxs-lookup"><span data-stu-id="c4098-193">FileX flushes all sectors currently in the driver's sector cache to the physical media by issuing a flush request to the I/O driver.</span></span> <span data-ttu-id="c4098-194">もちろん、ドライバーでセクターがキャッシュされていない場合、この要求にドライバーの処理は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="c4098-194">Of course, if the driver is not caching sectors, this request requires no driver processing.</span></span> <span data-ttu-id="c4098-195">I/O ドライバーのフラッシュ要求には、次の FX_MEDIA メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-195">The following FX_MEDIA members are used for the I/O driver flush request:</span></span>

|<span data-ttu-id="c4098-196">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-196">FX_MEDIA member</span></span>| <span data-ttu-id="c4098-197">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-197">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-198">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-198">fx_media_driver_request</span></span>|<span data-ttu-id="c4098-199">FX_DRIVER_FLUSH</span><span class="sxs-lookup"><span data-stu-id="c4098-199">FX_DRIVER_FLUSH</span></span>|

### <a name="driver-abort"></a><span data-ttu-id="c4098-200">ドライバーの中止</span><span class="sxs-lookup"><span data-stu-id="c4098-200">Driver Abort</span></span>

<span data-ttu-id="c4098-201">FileX により、I/O ドライバーに中止要求を発行することで、物理メディアとのそれ以降のすべての物理 I/O アクティビティを中止するように、ドライバーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-201">FileX informs the driver to abort all further physical I/O activity with the physical media by issuing an abort request to the I/O driver.</span></span> <span data-ttu-id="c4098-202">ドライバーでは、再初期化されるまで、I/O を再度実行しないでください。</span><span class="sxs-lookup"><span data-stu-id="c4098-202">The driver should not perform any I/O again until it is re-initialized.</span></span> <span data-ttu-id="c4098-203">I/O ドライバーの中止要求には、次の FX_MEDIA メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-203">The following FX_MEDIA members are used for the I/O driver abort request:</span></span>

|<span data-ttu-id="c4098-204">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-204">FX_MEDIA member</span></span>| <span data-ttu-id="c4098-205">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-205">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-206">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-206">fx_media_driver_request</span></span>| <span data-ttu-id="c4098-207">FX_DRIVER_ABORT</span><span class="sxs-lookup"><span data-stu-id="c4098-207">FX_DRIVER_ABORT</span></span>|

### <a name="release-sectors"></a><span data-ttu-id="c4098-208">セクターの解放</span><span class="sxs-lookup"><span data-stu-id="c4098-208">Release Sectors</span></span>

<span data-ttu-id="c4098-209">前の初期化の間にドライバーによって選択された場合、FileX により、1 つ以上の連続するセクターが空くたびにドライバーに通知されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-209">If previously selected by the driver during initialization, FileX informs the driver whenever one or more consecutive sectors become free.</span></span> <span data-ttu-id="c4098-210">ドライバーが実際には FLASH マネージャーである場合、この情報を使用して、これらのセクターが不要になったことを FLASH マネージャーに通知できます。</span><span class="sxs-lookup"><span data-stu-id="c4098-210">If the driver is actually a FLASH manager, this information can be used to tell the FLASH manager that these sectors are no longer needed.</span></span> <span data-ttu-id="c4098-211">I/O ドライバーのセクター解放要求には、次の **FX_MEDIA** メンバーが使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-211">The following **FX_MEDIA** members are used for the I/O release sectors request:</span></span>

|<span data-ttu-id="c4098-212">FX_MEDIA メンバー</span><span class="sxs-lookup"><span data-stu-id="c4098-212">FX_MEDIA member</span></span>| <span data-ttu-id="c4098-213">意味</span><span class="sxs-lookup"><span data-stu-id="c4098-213">Meaning</span></span>|
|-----------|-----------|
|<span data-ttu-id="c4098-214">fx_media_driver_request</span><span class="sxs-lookup"><span data-stu-id="c4098-214">fx_media_driver_request</span></span>|<span data-ttu-id="c4098-215">FX_DRIVER_RELEASE_SECTORS</span><span class="sxs-lookup"><span data-stu-id="c4098-215">FX_DRIVER_RELEASE_SECTORS</span></span>|
|<span data-ttu-id="c4098-216">fx_media_driver_logical_sector</span><span class="sxs-lookup"><span data-stu-id="c4098-216">fx_media_driver_logical_sector</span></span>|<span data-ttu-id="c4098-217">空きセクターの開始</span><span class="sxs-lookup"><span data-stu-id="c4098-217">Start of free sector</span></span>|
|<span data-ttu-id="c4098-218">fx_media_driver_sectors</span><span class="sxs-lookup"><span data-stu-id="c4098-218">fx_media_driver_sectors</span></span>|<span data-ttu-id="c4098-219">空きセクター数</span><span class="sxs-lookup"><span data-stu-id="c4098-219">Number of free sectors</span></span>|

### <a name="driver-suspension"></a><span data-ttu-id="c4098-220">ドライバーの一時停止</span><span class="sxs-lookup"><span data-stu-id="c4098-220">Driver Suspension</span></span>

<span data-ttu-id="c4098-221">物理メディアとの I/O には時間がかかることがあるため、呼び出し元スレッドを一時停止するのが好ましいことがよくあります。</span><span class="sxs-lookup"><span data-stu-id="c4098-221">Because I/O with physical media may take some time, suspending the calling thread is often desirable.</span></span> <span data-ttu-id="c4098-222">もちろん、これは基になる I/O 操作の完了が割り込み駆動であることを前提としています。</span><span class="sxs-lookup"><span data-stu-id="c4098-222">Of course, this assumes completion of the underlying I/O operation is interrupt driven.</span></span> <span data-ttu-id="c4098-223">その場合、スレッドの一時停止は ThreadX セマフォで簡単に実装できます。</span><span class="sxs-lookup"><span data-stu-id="c4098-223">If so, thread suspension is easily implemented with a ThreadX semaphore.</span></span> <span data-ttu-id="c4098-224">入力または出力操作を開始した後、I/O ドライバーにより、独自の内部 I/O セマフォ (ドライバーの初期化の間に初期カウント ゼロで作成されたもの) が一時停止されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-224">After starting the input or output operation, the I/O driver suspends on its own internal I/O semaphore (created with an initial count of zero during driver initialization).</span></span> <span data-ttu-id="c4098-225">ドライバーの I/O 完了割り込み処理の一部として、同じ I/O セマフォが設定され、それにより一時停止されているスレッドが起動されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-225">As part of the driver I/O completion interrupt processing, the same I/O semaphore is set, which in turn wakes up the suspended thread.</span></span>

### <a name="sector-translation"></a><span data-ttu-id="c4098-226">セクターの変換</span><span class="sxs-lookup"><span data-stu-id="c4098-226">Sector Translation</span></span>

<span data-ttu-id="c4098-227">メディアは FileX により線形論理セクターとして認識されるため、I/O ドライバーに対して行われる I/O 要求は論理セクターで行われます。</span><span class="sxs-lookup"><span data-stu-id="c4098-227">Because FileX views the media as linear logical sectors, I/O requests made to the I/O driver are made with logical sectors.</span></span> <span data-ttu-id="c4098-228">論理セクターとメディアの物理ジオメトリ (ヘッド、トラック、物理セクターが含まれル場合があります) の間の変換は、ドライバーで行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4098-228">It is the driver's responsibility to translate between logical sectors and the physical geometry of the media, which may include heads, tracks, and physical sectors.</span></span> <span data-ttu-id="c4098-229">FLASH および RAM ディスク メディアの場合は、通常、論理セクターによってディレクトリが物理セクターにマップされます。</span><span class="sxs-lookup"><span data-stu-id="c4098-229">For FLASH and RAM disk media, the logical sectors typically map directory to physical sectors.</span></span> <span data-ttu-id="c4098-230">どのような場合でも、I/O ドライバーによる論理セクターと物理セクターのマッピングの実行には、次の一般的な式が使用されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-230">In any case, here are the typical formulas to perform the logical to physical sector mapping in the I/O driver:</span></span>

```c
media_ptr -> fx_media_driver_physical_sector =
    (media_ptr -> fx_media_driver_logical_sector % media_ptr -> fx_media_sectors_per_track) + 1;

media_ptr -> fx_media_driver_physical_head =
    (media_ptr -> fx_media_driver_logical_sector/ media_ptr ->
    fx_media_sectors_per_track) % media_ptr -> fx_media_heads;

media_ptr -> fx_media_driver_physical_track =(media_ptr ->
    fx_media_driver_logical_sector/ (media_ptr -> fx_media_sectors_per_track *
    media_ptr -> fx_media_heads)));
```

<span data-ttu-id="c4098-231">物理セクターは 1 から始まり、論理セクターは 0 から始まることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="c4098-231">Note that physical sectors start at one, while logical sectors start at zero.</span></span>

### <a name="hidden-sectors"></a><span data-ttu-id="c4098-232">隠しセクター</span><span class="sxs-lookup"><span data-stu-id="c4098-232">Hidden Sectors</span></span>

<span data-ttu-id="c4098-233">隠しセクターはメディアのブート レコードより前に存在します。</span><span class="sxs-lookup"><span data-stu-id="c4098-233">Hidden sectors resided prior to the boot record on the media.</span></span> <span data-ttu-id="c4098-234">それらは実際に FAT ファイル システムのレイアウトの範囲外にあるため、ドライバーによって実行される論理セクタ操作のたびに考慮される必要があります。</span><span class="sxs-lookup"><span data-stu-id="c4098-234">Because they are really outside the scope of the FAT file system layout, they must be accounted for in each logical sector operation the driver does.</span></span>

### <a name="media-write-protect"></a><span data-ttu-id="c4098-235">メディア書き込み保護</span><span class="sxs-lookup"><span data-stu-id="c4098-235">Media Write Protect</span></span>

<span data-ttu-id="c4098-236">FileX ドライバーで、メディア制御ブロックの fx_media_driver_write_protect フィールドを設定することにより、書き込み保護を有効にすることができます。</span><span class="sxs-lookup"><span data-stu-id="c4098-236">The FileX driver can turn on write protect by setting the fx_media_driver_write_protect field in the media control block.</span></span> <span data-ttu-id="c4098-237">これにより、メディアへの書き込みを試行する FileX の呼び出しが行われた場合、エラーが返されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-237">This will cause an error to be returned if any FileX calls are made in an attempt to write to the media.</span></span>

## <a name="sample-ram-driver"></a><span data-ttu-id="c4098-238">RAM ドライバーのサンプル</span><span class="sxs-lookup"><span data-stu-id="c4098-238">Sample RAM Driver</span></span>

<span data-ttu-id="c4098-239">FileX のデモンストレーション システムには小さい RAM ディスク ドライバーが付属しており、fx_ram_driver.c ファイルで定義されています。</span><span class="sxs-lookup"><span data-stu-id="c4098-239">The FileX demonstration system is delivered with a small RAM disk driver, which is defined in the file fx_ram_driver.c.</span></span> <span data-ttu-id="c4098-240">そのドライバーでは、32K のメモリ領域が想定され、256 個の 128 バイト セクター用のブート レコードが作成されます。</span><span class="sxs-lookup"><span data-stu-id="c4098-240">The driver assumes a 32K memory space and creates a boot record for 256 128-byte sectors.</span></span> <span data-ttu-id="c4098-241">このファイルは、アプリケーション固有の FileX I/O ドライバーを実装する方法の好例です。</span><span class="sxs-lookup"><span data-stu-id="c4098-241">This file provides a good example of how to implement application specific FileX I/O drivers.</span></span>

```c
/*FUNCTION: _fx_ram_driver
RELEASE: PORTABLE C 5.7
AUTHOR: William E. Lamie, Microsoft, Inc.
DESCRIPTION: This function is the entry point to the generic
    RAM disk driver that is delivered with all versions of FileX.
    The format of the RAM disk is easily modified by calling fx_media_format prior to opening the media.

    This driver also serves as a template for developing FileX drivers
    for actual devices. Simply replace the read/write sector logic
    with calls to read/write from the appropriate physical device.

FileX RAM/FLASH structures look like the following:
Physical Sector             Contents
    0                         Boot record
    1                         FAT Area Start
    +FAT Sectors             Root Directory Start
    +Directory Sectors         Data Sector Start

INPUT: media_ptr Media control block pointer
OUTPUT: None
CALLS:     _fx_utility_memory_copy Copy sector memory
        _fx_utility_16_unsigned_read Read 16-bit unsigned
CALLED BY: FileX System Functions
RELEASE HISTORY:

    DATE         NAME         DESCRIPTION
    12-12-2005     William E.     Lamie Initial Version 5.0
    07-18-2007     William E.     Lamie Modified comment(s),
                                resulting in version 5.1
    03-01-2009     William E.     Lamie Modified comment(s),
                                resulting in version 5.2
    11-01-2015     William E.     Lamie Modified comment(s),
                                resulting in version 5.3
    04-15-2016     William E.     Lamie Modified comment(s),
                                resulting in version 5.4
    04-03-2017     William E.     Lamie Modified comment(s),
                                fixed compiler warnings,
                                resulting in version 5.5
    12-01-2018     William E.     Lamie Modified comment(s),
                                checked buffer overflow,
                                resulting in version 5.6
    08-15-2019     William E.     Lamie Modified comment(s),
                                resulting in version 5.7
*/

VOID _fx_ram_driver(FX_MEDIA *media_ptr) { UCHAR *source_buffer;
                                           UCHAR *destination_buffer;
                                           UINT bytes_per_sector;

    /* There are several useful/important pieces of information contained
        in the media structure, some of which are supplied by FileX and
        others are for the driver to setup. The following
        is a summary of the necessary FX_MEDIA structure members:
    FX_MEDIA Member                     Meaning

    fx_media_driver_request             FileX request type.
        Valid requests from FileX are as follows:
        FX_DRIVER_READ
        FX_DRIVER_WRITE
        FX_DRIVER_FLUSH
        FX_DRIVER_ABORT
        FX_DRIVER_INIT
        FX_DRIVER_BOOT_READ
        FX_DRIVER_RELEASE_SECTORS
        FX_DRIVER_BOOT_WRITE FX_DRIVER_UNINIT

    fx_media_driver_status              This value is RETURNED by the driver.
        If the operation is successful, this field should be set to FX_SUCCESS
        for before returning. Otherwise, if an error occurred, this field should be set to FX_IO_ERROR.

    fx_media_driver_buffer              Pointer to buffer to read or write sector data. This is supplied by FileX.

    fx_media_driver_logical_sector      Logical sector FileX is requesting.
    fx_media_driver_sectors             Number of sectors FileX is requesting.

    The following is a summary of the optional FX_MEDIA structure members: FX_MEDIA Member Meaning

    fx_media_driver_info                Pointer to any additional information or memory.
        This is optional for the driver use and is setup from the fx_media_open call.
        The RAM disk uses this pointer for the RAM disk memory itself.

    fx_media_driver_write_protect       The DRIVER sets this to FX_TRUE when media is write protected.
        This is typically done in initialization, but can be done anytime.

    fx_media_driver_free_sector_update  The DRIVER sets this to FX_TRUE when it needs
        to know when clusters are released. This is important for FLASH wear-leveling drivers.

    fx_media_driver_system_write        FileX sets this flag to FX_TRUE if the sector
        being written is a system sector, e.g., a boot, FAT, or directory sector.
        The driver may choose to use this to initiate error recovery logic for greater fault
        tolerance. fx_media_driver_data_sector_read FileX sets this flag to FX_TRUE
        if the sector(s) being read are file data sectors, i.e., NOT system sectors.

    fx_media_driver_sector_type         FileX sets this variable to the specific type of
        sector being read or written. The following sector types are identified:
            FX_UNKNOWN_SECTOR
            FX_BOOT_SECTOR
            FX_FAT_SECTOR
            FX_DIRECTORY_SECTOR
            FX_DATA_SECTOR */

    /* Process the driver request specified in the media control block. */

    switch (media_ptr -> fx_media_driver_request){

        case FX_DRIVER_READ: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
            is pointed to by the fx_media_driver_info pointer, which is supplied
            by the application in the call to fx_media_open. */

            source_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the RAM sector into the destination. */

             _fx_utility_memory_copy(source_buffer,
                media_ptr -> fx_media_driver_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_WRITE: {

            /* Calculate the RAM disk sector offset. Note the RAM disk memory
                is pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */

            destination_buffer = ((UCHAR *)media_ptr -> fx_media_driver_info) +
                ((media_ptr -> fx_media_driver_logical_sector +
                media_ptr -> fx_media_hidden_sectors) * media_ptr -> fx_media_bytes_per_sector);

            /* Copy the source to the RAM sector. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_driver_sectors *
                media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_FLUSH: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_ABORT: {
            /* Return driver success. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_INIT: {

            /* FLASH drivers are responsible for setting several fields
                in the media structure, as follows:
                media_ptr -> fx_media_driver_free_sector_update media_ptr ->
                fx_media_driver_write_protect
                The fx_media_driver_free_sector_update flag is used to instruct
                FileX to inform the driver whenever sectors are not being used.
                This is especially useful for FLASH managers so they don't have
                maintain mapping for sectors no longer in use.
                The fx_media_driver_write_protect flag can be set anytime by
                the driver to indicate the media is not writable. Write attempts
                made when this flag is set are returned as errors. */
            /* Perform basic initialization here... since the boot record is going
                to be read subsequently and again for volume name requests. */
            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

         case FX_DRIVER_UNINIT: {

            /* There is nothing to do in this case for the RAM driver.
                For actual devices some shutdown processing may be necessary. */

            /* Successful driver request. */
            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_READ: {
            /* Read the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is pointed
                to by the fx_media_driver_info pointer, which is supplied by the
                application in the call to fx_media_open. */

            source_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* For RAM driver, determine if the boot record is valid. */

            if ((source_buffer[0] != (UCHAR)0xEB) ||

            ((source_buffer[1] != (UCHAR)0x34) &&

            (source_buffer[1] != (UCHAR)0x76)) || /* exFAT jump code. */

            (source_buffer[2] != (UCHAR)0x90)) {

            /* Invalid boot record, return an error! */
            media_ptr -> fx_media_driver_status = FX_MEDIA_INVALID; return; }

            /* For RAM disk only, pickup the bytes per sector. */

            bytes_per_sector =
                _fx_utility_16_unsigned_read(&source_buffer[FX_BYTES_SECTOR]); #ifdef FX_ENABLE_EXFAT

            /* if byte per sector is zero, then treat it as exFAT volume. */

            if (bytes_per_sector == 0 && (source_buffer[1] == (UCHAR)0x76)) {

            /* Pickup the byte per sector shift, and calculate byte per sector. */ 
            bytes_per_sector = (UINT)(1 << source_buffer[FX_EF_BYTE_PER_SECTOR_SHIFT]);

            }

            #endif /* FX_ENABLE_EXFAT */

            /* Ensure this is less than the media memory size. */
            if (bytes_per_sector \media_ptr -> fx_media_memory_size) {

            media_ptr -> fx_media_driver_status = FX_BUFFER_ERROR; break; }

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(source_buffer, media_ptr -> fx_media_driver_buffer, bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        case FX_DRIVER_BOOT_WRITE: {

            /* Write the boot record and return to the caller. */

            /* Calculate the RAM disk boot sector offset, which is at the
                very beginning of the RAM disk. Note the RAM disk memory is
                pointed to by the fx_media_driver_info pointer, which is supplied
                by the application in the call to fx_media_open. */ 
            destination_buffer = (UCHAR *)media_ptr -> fx_media_driver_info;

            /* Copy the RAM boot sector into the destination. */

            _fx_utility_memory_copy(media_ptr -> fx_media_driver_buffer,
                destination_buffer, media_ptr -> fx_media_bytes_per_sector);

            /* Successful driver request. */

            media_ptr -> fx_media_driver_status = FX_SUCCESS; break; }

        default: {
            /* Invalid driver request. */
            media_ptr -> fx_media_driver_status = FX_IO_ERROR; break;}
    }
}
```
