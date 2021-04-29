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
# <a name="chapter-5---io-drivers-for-azure-rtos-filex"></a>第 5 章 - Azure RTOS FileX 用 I/O ドライバー

この章は、Azure RTOS FileX 用 I/O ドライバーの説明であり、開発者がアプリケーション固有のドライバーを記述できるように作られています。

## <a name="io-driver-introduction"></a>I/O ドライバーの概要

FileX では、複数のメディア デバイスがサポートされています。 FX_MEDIA 構造体で、メディア デバイスを管理するために必要なすべての情報が定義されています。 この構造体には、メディア固有の I/O ドライバーや、ドライバーと FileX の間で情報と状態を受け渡すための関連パラメーターなど、すべてのメディア情報が含まれます。 ほとんどのシステムでは、FileX メディア インスタンスごとに一意の I/O ドライバーがあります。

## <a name="io-driver-entry"></a>I/O ドライバーのエントリ

各 FileX I/O ドライバーには、***fx_media_open*** サービス呼び出しによって定義されている 1 つのエントリ関数があります。 ドライバー エントリ関数の形式は次のとおりです:

```c
void my_driver_entry(FX_MEDIA *media_ptr);
```

FileX により、I/O ドライバーのエントリ関数が呼び出されて、すべての物理メディアへのアクセスが要求されます。これには、初期化とブート セクターの読み取りが含まれます。 ドライバーに対する要求は順番に実行されます。つまり、FileX は、現在の要求が完了して、別の要求が送信されるまで待機します。

## <a name="io-driver-requests"></a>I/O ドライバーの要求

各 I/O ドライバーには単一のエントリ関数があるため、FileX による特定の要求はメディア制御ブロックを通じて行われます。 具体的には、正確なドライバー要求を指定するには、**FX_MEDIA** の **fx_media_driver_request** メンバーが使用されます。 I/O ドライバーによる要求の成功または失敗の通知は、**FX_MEDIA** の **fx_media_driver_status** メンバーを通じて行われます。 ドライバーの要求が成功した場合、ドライバーから制御が戻る前に、このフィールドに **FX_SUCCESS** が設定されます。 それ以外で、エラーが検出された場合は、このフィールドに FX_IO_ERROR が設定されます。

### <a name="driver-initialization"></a>ドライバーの初期化

実際のドライバー初期化処理はアプリケーションごとに異なりますが、通常は、データ構造体の初期化と、必要に応じた、ハードウェアのいくつかの事前初期化で構成されます。 この要求は、最初に FileX によって行われ、fx_media_open サービス内から実行されます。

メディア書き込み保護が検出された場合は、ドライバーの FX_MEDIA の fx_media_driver_write_protect メンバーが FX_TRUE に設定されているはずです。

I/O ドライバーの初期化要求には、次の FX_MEDIA メンバーが使用されます。

|FX_MEDIA メンバー|意味|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_INIT|

FileX には、セクターが使用されなくなったときにアプリケーション ドライバーに通知するメカニズムがあります。 これは、FLASH にマップされているすべての使用中論理セクターを管理する必要がある FLASH メモリ マネージャーに特に便利です。

空きセクターのそのような通知が必要な場合は、アプリケーション ドライバーで単に、関連付けられた **FX_MEDIA** 構造体の *fx_media_driver_free_sector_update* フィールドを **FX_TRUE** に設定します。 設定した後、FileX により、1 つ以上の連続するセクターが空きセクターになったことを示す **_FX_DRIVER_RELEASE_SECTORS_** I/O ドライバー呼び出しが行われます。

### <a name="boot-sector-read"></a>ブート セクターの読み取り

標準の読み取り要求を使用する代わりに、メディアのブート セクターを読み取る特定の要求が FileX によって行われます。 I/O ドライバーのブート セクター読み取り要求には、次の **FX_MEDIA** メンバーが使用されます。

|FX_MEDIA メンバー|意味|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_READ|
|fx_media_driver_buffer| ブート セクターの読み取り先のアドレス。|

### <a name="boot-sector-write"></a>ブート セクターの書き込み

標準の書き込み要求を使用する代わりに、メディアのブート セクターを書き込む特定の要求が FileX によって行われます。 I/O ドライバーのブート セクター書き込み要求には、次の **FX_MEDIA** メンバーが使用されます。

|FX_MEDIA メンバー|意味|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_BOOT_WRITE|
|fx_media_driver_buffer| ブート セクターの書き込み元のアドレス。|

### <a name="sector-read"></a>セクターの読み取り

FileX により、I/O ドライバーに読み取り要求を発行することにより、1 つ以上のセクターがメモリに読み取られます。 I/O ドライバーの読み取り要求には、次の **FX_MEDIA** メンバーが使用されます。

|FX_MEDIA メンバー|意味|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_READ|
|fx_media_driver_logical_sector|読み取る論理セクター|
|fx_media_driver_sectors|読み取るセクターの数|
|fx_media_driver_buffer|セクターの読み取り先バッファー|
|fx_media_driver_data_sector_read|ファイル データ セクターを要求する場合は FX_TRUE に設定します。 それ以外で、システム セクター (FAT またはディレクトリ セクター) を要する場合は、FX_FALSE に設定します。|
|fx_media_driver_sector_type|要求するセクターの明示的な種類を次のように定義します。<br />FX_FAT_SECTOR (2)<br />FX_DIRECTORY_SECTOR (3)<br />FX_DATA_SECTOR (4)|

### <a name="sector-write"></a>セクターの書き込み

FileX により、I/O ドライバーへの書き込み要求を発行することで、物理メディアに 1 つ以上のセクターが書き込まれます。 I/O ドライバーの書き込み要求には、次の FX_MEDIA メンバーが使用されます。

|FX_MEDIA メンバー| 意味|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_WRITE|
|fx_media_driver_logical_sector|書き込む論理セクター|
|fx_media_driver_sectors|書き込むセクターの数|
|fx_media_driver_buffer|書き込むセクターの書き込み元バッファー|
|fx_media_driver_system_write| システム セクター (FAT またはディレクトリ セクター) を要求する場合は、FX_TRUE に設定します。 それ以外で、ファイル データ セクターを要求する場合は、FX_FALSE に設定します。|
|fx_media_driver_sector_type|要求するセクターの明示的な種類を次のように定義します。
FX_FAT_SECTOR (2) FX_DIRECTORY_SECTOR (3) FX_DATA_SECTOR (4)|

### <a name="driver-flush"></a>ドライバーのフラッシュ

FileX によって、I/O ドライバーへのフラッシュ要求を発行することで、現在ドライバーのセクター キャッシュにあるすべてのセクターが物理メディアにフラッシュされます。 もちろん、ドライバーでセクターがキャッシュされていない場合、この要求にドライバーの処理は必要ありません。 I/O ドライバーのフラッシュ要求には、次の FX_MEDIA メンバーが使用されます。

|FX_MEDIA メンバー| 意味|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_FLUSH|

### <a name="driver-abort"></a>ドライバーの中止

FileX により、I/O ドライバーに中止要求を発行することで、物理メディアとのそれ以降のすべての物理 I/O アクティビティを中止するように、ドライバーに通知されます。 ドライバーでは、再初期化されるまで、I/O を再度実行しないでください。 I/O ドライバーの中止要求には、次の FX_MEDIA メンバーが使用されます。

|FX_MEDIA メンバー| 意味|
|-----------|-----------|
|fx_media_driver_request| FX_DRIVER_ABORT|

### <a name="release-sectors"></a>セクターの解放

前の初期化の間にドライバーによって選択された場合、FileX により、1 つ以上の連続するセクターが空くたびにドライバーに通知されます。 ドライバーが実際には FLASH マネージャーである場合、この情報を使用して、これらのセクターが不要になったことを FLASH マネージャーに通知できます。 I/O ドライバーのセクター解放要求には、次の **FX_MEDIA** メンバーが使用されます。

|FX_MEDIA メンバー| 意味|
|-----------|-----------|
|fx_media_driver_request|FX_DRIVER_RELEASE_SECTORS|
|fx_media_driver_logical_sector|空きセクターの開始|
|fx_media_driver_sectors|空きセクター数|

### <a name="driver-suspension"></a>ドライバーの一時停止

物理メディアとの I/O には時間がかかることがあるため、呼び出し元スレッドを一時停止するのが好ましいことがよくあります。 もちろん、これは基になる I/O 操作の完了が割り込み駆動であることを前提としています。 その場合、スレッドの一時停止は ThreadX セマフォで簡単に実装できます。 入力または出力操作を開始した後、I/O ドライバーにより、独自の内部 I/O セマフォ (ドライバーの初期化の間に初期カウント ゼロで作成されたもの) が一時停止されます。 ドライバーの I/O 完了割り込み処理の一部として、同じ I/O セマフォが設定され、それにより一時停止されているスレッドが起動されます。

### <a name="sector-translation"></a>セクターの変換

メディアは FileX により線形論理セクターとして認識されるため、I/O ドライバーに対して行われる I/O 要求は論理セクターで行われます。 論理セクターとメディアの物理ジオメトリ (ヘッド、トラック、物理セクターが含まれル場合があります) の間の変換は、ドライバーで行う必要があります。 FLASH および RAM ディスク メディアの場合は、通常、論理セクターによってディレクトリが物理セクターにマップされます。 どのような場合でも、I/O ドライバーによる論理セクターと物理セクターのマッピングの実行には、次の一般的な式が使用されます。

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

物理セクターは 1 から始まり、論理セクターは 0 から始まることに注意してください。

### <a name="hidden-sectors"></a>隠しセクター

隠しセクターはメディアのブート レコードより前に存在します。 それらは実際に FAT ファイル システムのレイアウトの範囲外にあるため、ドライバーによって実行される論理セクタ操作のたびに考慮される必要があります。

### <a name="media-write-protect"></a>メディア書き込み保護

FileX ドライバーで、メディア制御ブロックの fx_media_driver_write_protect フィールドを設定することにより、書き込み保護を有効にすることができます。 これにより、メディアへの書き込みを試行する FileX の呼び出しが行われた場合、エラーが返されます。

## <a name="sample-ram-driver"></a>RAM ドライバーのサンプル

FileX のデモンストレーション システムには小さい RAM ディスク ドライバーが付属しており、fx_ram_driver.c ファイルで定義されています。 そのドライバーでは、32K のメモリ領域が想定され、256 個の 128 バイト セクター用のブート レコードが作成されます。 このファイルは、アプリケーション固有の FileX I/O ドライバーを実装する方法の好例です。

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
