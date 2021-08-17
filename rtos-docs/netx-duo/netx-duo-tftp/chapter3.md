---
title: 第 3 章 - Azure RTOS NetX Duo TFTP サービスの説明
description: この章では、すべての NetX Duo TFTP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: db7b7469bda02597db6428ecbf080b37a095413411eef2abefb1c4804d7bb1d3
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799065"
---
# <a name="chapter-3---description-of-azure-rtos-netx-duo-tftp-services"></a>第 3 章 - Azure RTOS NetX Duo TFTP サービスの説明

この章では、すべての NetX Duo TFTP サービス (以下に記載) をアルファベット順に説明します。 特に指定がない限り、すべてのサービスで IPv6 および IPv4 の通信がサポートされます。

以下の API の説明の「戻り値」セクションでは、**太字** の値は、API エラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nxd_tftp_client_file_open**: "*TFTP クライアント ファイルを開く*"

- **nxd_tftp_client_create**: "*TFTP クライアント インスタンスを作成する*"

- **nxd_tftp_client_delete**: "*TFTP クライアント インスタンスを削除する*"

- **nxd_tftp_client_error_info_get**: "*クライアントのエラー情報を取得する*"

- **nxd_tftp_client_file_close**: "*クライアント ファイルを閉じる*"

- **nxd_tftp_client_file_open**: "*クライアント ファイルを開く*"

- **nxd_tftp_client_file_read**: "*クライアント ファイルからブロックを読み取る*"

- **nxd_tftp_client_file_write**: "*クライアント ファイルにブロックを書き込む*"

- **nxd_tftp_client_packet_allocate**: "*クライアント ファイル書き込み用にパケットを割り当てる*"

- **nxd_tftp_client_set_interface**: "*TFTP 要求の物理インターフェイスを設定する*"

- **nxd_tftp_server_create**: "*TFTP サーバーを作成する*"

- **nxd_tftp_server_delete**: "*TFTP サーバーを削除する*"

- **nxd_tftp_server_start**: "*TFTP サーバーを起動する*"

- **nxd_tftp_server_stop**: "*TFTP サーバーを停止する*"

> [!NOTE] 
> 上記のすべてのサービスの IPv4 に相当するものは、NetX Duo TFTP クライアントとサーバー (*nx_tftp_server_create* や *nx_tftp_client_file_open* など) で利用できます。 以下のページでは、"Duo" API の説明 (*nxd_* で始まるサービスなど) のみを提供しています。 NXD_ADDRESS \* 入力が指定されている場合、IPv4 に相当する API は ULONG 入力を呼び出します。 それ以外の場合、API の使用に違いはありません。

## <a name="nxd_tftp_client_create"></a>nxd_tftp_client_create

TFTP クライアント インスタンスを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_create(NX_TFTP_CLIENT *tftp_client_ptr,  
     CHAR *tftp_client_name, NX_IP *ip_ptr, NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された IP インスタンスの TFTP クライアント インスタンスが作成されます。

> [!IMPORTANT]
> アプリケーションでは、指定された IP およびパケット プールが既に作成されていることを確認する必要があります。 さらに、このサービスを呼び出す前に、IP インスタンスに対して UDP を有効にする必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** TFTP クライアントの制御ブロックへのポインター。

- **tftp_client_name** この TFTP クライアント インスタンスの名前

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

- **pool_ptr** パケット プール TFTP クライアント インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TFTP が正常に作成されました。

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効またはサポートされていません

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 無効なサーバー IP アドレスを受信しました

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバー ACK を受信しませんでした

- NX_PTR_ERROR (0x16) IP、プール、または TFTP ポインターが無効です。

- NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Create a TFTP Client instance. */
status =  nxd_tftp_client_create(&my_tftp_client, “My TFTP Client”, 
                                                    &my_ip, &pool_ptr);

/* If status is NX_SUCCESS a TFTP Client instance was successfully
   created. */
```

## <a name="nxd_tftp_client_delete"></a>nxd_tftp_client_delete

TFTP クライアント インスタンスを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_delete(NX_TFTP_CLIENT *tftp_client_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された TFTP クライアント インスタンスが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** 以前に作成した TFTP クライアント インスタンスへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TFTP クライアントが正常に削除されました。

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete a TFTP Client instance. */
status =  nxd_tftp_client_delete(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP Client instance was successfully
   deleted. */
```

## <a name="nxd_tftp_client_error_info_get"></a>nxd_tftp_client_error_info_get

クライアントのエラー情報を取得する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_error_info_get(NX_TFTP_CLIENT *tftp_client_ptr,
                        UINT *error_code, CHAR **error_string);
```

### <a name="description"></a>説明

このサービスでは、最後のエラー コードを返し、クライアントの内部エラー文字列へのポインターを設定します。 エラー状態では、ユーザーはサーバーによって最後に送信されたエラーを表示できます。 null 値のエラー文字列は、エラーが存在しないことを示します。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** 以前に作成した TFTP クライアント インスタンスへのポインター。

- **error_code** エラー コードの送信先領域へのポインター

- **error_string** エラー文字列の送信先へのポインター

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) TFTP エラー情報を正常に取得しました。  

- NX_PTR_ERROR (0x16) TFTP クライアント ポインターが無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Get error information for client. */
status =  nxd_tftp_client_error_info_get(&my_tftp_client, &error_code,
                    &error_string_ptr);

/* If status is NX_SUCCESS the error code and error string are available. */
```

## <a name="nxd_tftp_client_file_close"></a>nxd_tftp_client_file_close

クライアント ファイルを閉じる

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_file_close(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT ip_type);
```

### <a name="description"></a>説明

このサービスにより、この TFTP クライアント インスタンスによって以前に開かれたファイルが閉じます。 TFTP クライアント インスタンスで一度に開くことができるファイルは 1 つだけです。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** 以前に作成した TFTP クライアント インスタンスへのポインター。

- **ip_type** 使用する IP プロトコルを指定します。 有効なオプションは、IPv4 (4) または IPv6 (6) です。

### <a name="return-values"></a>戻り値

- **FX_SUCCESS** (0x00) TFTP ファイルが閉じられました。

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です。

- NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Close the previously opened file associated with “my_client”. */
status =  nxd_tftp_client_file_close(&my_tftp_client);

/* If status is NX_SUCCESS the TFTP file is closed. */
```

## <a name="nx_tftp_client_file_open"></a>nx_tftp_client_file_open

TFTP クライアント ファイルを開く

### <a name="prototype"></a>プロトタイプ

```C
UINT nx_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr, 
            CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
            open_type, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスでは、指定された IP アドレスで、TFTP サーバー上の指定されたファイルを開こうとします。 読み取りまたは書き込みのいずれかでファイルが開かれます。 

> [!NOTE] 
> これは IPv4 パケットに限定され、NetX TFTP アプリケーションのサポートを目的としています。 開発者は、同等の "duo" サービス *nxd_tftp_client_file_open* を使用するようにアプリケーションを移植することをお勧め します。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** TFTP 制御ブロックへのポインター。

- **file_name** ASCII ファイル名で、NULL で終了し、かつ適切なパス情報を持ちます。

- **server_ip_address** サーバーの TFTP アドレス。

- **open_type** オープン要求の種類。次のいずれかになります。

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** サービスで、TFTP クライアントのファイルが開くまで待機する時間を定義します。 この待機オプションは次のように定義されます。

  **タイムアウト値** (0x00000001 から 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF) 
  
  TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。 
  
  数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

- **ip_type** 使用する IP プロトコルを指定します。 有効なオプションは、IPv4 (4) または IPv6 (6) です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアント ファイルのオープンに成功しました

- **NX_TFTP_NOT_CLOSED** (0xC3) クライアントで既にファイルが開かれています

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 無効なサーバー IP を受信しました

- **NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_IP_ADDRESS_ERROR (0x21) サーバー IP アドレスが無効です

- NX_OPTION_ERROR (0x0A) オープン型が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
        & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_open"></a>nxd_tftp_client_file_open

TFTP クライアント ファイルを開く

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_file_open(NX_TFTP_CLIENT *tftp_client_ptr,
        CHAR *file_name, NXD_ADDRESS *server_ip_address, UINT 
        open_type, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>説明

このサービスでは、指定された IPv6 アドレスで、TFTP サーバー上の指定されたファイルを開こうとします。 読み取りまたは書き込みのいずれかでファイルが開かれます。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** TFTP 制御ブロックへのポインター。

- **file_name** ASCII ファイル名で、NULL で終了し、かつ適切なパス情報を持ちます。

- **server_ip_address** サーバーの TFTP アドレス。

- **open_type** オープン要求の種類。次のいずれかになります。

  **NX_TFTP_OPEN_FOR_READ** (0x01)

  **NX_TFTP_OPEN_FOR_WRITE** (0x02)

- **wait_option** サービスで、TFTP クライアントのファイルが開くまで待機する時間を定義します。 この待機オプションは次のように定義されます。

  **タイムアウト値** (0x00000001 から 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。

  数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

- **ip_type** 使用する IP プロトコルを指定します。 有効なオプションは、IPv4 (4) または IPv6 (6) です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアント ファイルのオープンに成功しました

- **NX_TFTP_NOT_CLOSED** (0xC3) クライアントで既にファイルが開かれています

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効です

- **NX_TFTP_INVALID_SERVER_ADDRESS** (0x08) 無効なサーバー IP を受信しました

- **NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_IP_ADDRESS_ERROR (0x21) サーバー IP アドレスが無効です

- NX_OPTION_ERROR (0x0A) オープン型が無効です

- NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Define the TFTP server address. */
NXD_ADDRESS server_ip_address;

server_ip_address.nxd_ip_version = NX_IP_VERSION_V6;
server _ip_address.nxd_ip_address.v6[0] = 0x20010db8;
server _ip_address.nxd_ip_address.v6[1] = 0xf101;
server _ip_address.nxd_ip_address.v6[2] = 0;
server _ip_address.nxd_ip_address.v6[3] = 0x101;

/* Open file “test.txt” for reading on the TFTP Server. */
status =  nxd_tftp_client_file_open(&my_tftp_client, “test.txt”,
                & server_ip_address, NX_TFTP_OPEN_FOR_READ, 200);

/* If status is NX_SUCCESS the “test.txt” file is now open for reading. */
```

## <a name="nxd_tftp_client_file_read"></a>nxd_tftp_client_file_read

クライアント ファイルからブロックを読み取る

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_file_read(NX_TFTP_CLIENT *tftp_client_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>説明

このサービスでは、以前に開いた TFTP クライアント ファイルから 512 バイトのブロックを読み取ります。 512 バイト未満のブロックではファイルの終わりの合図があります。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** TFTP クライアントの制御ブロックへのポインター。

- **packet_ptr** ファイルから読み取られたブロックを格納しているパケットの宛先。

- **wait_option** サービスで読み取りの完了を待機する時間を定義します。 この待機オプションは次のように定義されます。

  **タイムアウト値** (0x00000001 から 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。

  数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーによるファイルのブロックの送信を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

- **ip_type** 使用する IP プロトコルを指定します。 有効なオプションは、IPv4 (4) または IPv6 (6) です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアント ブロックが正常に読み取られました

- **NX_TFTP_NOT_OPEN** (0xC3) 指定されたクライアント ファイルは読み取り用に開かれていません

- **NX_NO_PACKET** (0x01) サーバーからパケットを受信していません。

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません

- **NX_TFTP_END_OF_FILE** (0xC5) ファイルの終わりが検出されました (エラーではありません)。

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効です

- **NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました

- **NX_TFTP_FAILED** (0xC2) 不明な TFTP コードを受信しました

- **NX_TFTP_INVALID_BLOCK_NUMBER** (0x0A) 無効なブロック番号を受信しました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Read a block from a previously opened file of “my_client”. */
status =  nxd_tftp_client_file_read(&my_tftp_client, &return_packet_ptr, 200);

/* If status is NX_SUCCESS a block of the TFTP file is in the payload of
   “return_packet_ptr”. */
```

## <a name="nxd_tftp_client_file_write"></a>nxd_tftp_client_file_write

クライアント ファイルにブロックを書き込む

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_file_write(NX_TFTP_CLIENT *tftp_client_ptr,
            NX_PACKET *packet_ptr, ULONG wait_option, UINT ip_type);
```

### <a name="description"></a>説明

このサービスでは、前に開いていた TFTP クライアント ファイルに 512 バイトのブロックを書き込みます。 512 バイト未満のブロックを指定すると、ファイルの終わりの合図があります。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** TFTP クライアントの制御ブロックへのポインター。

- **packet_ptr** ファイルに書き込むブロックを格納しているパケット。

- **wait_option** サービスで書き込みの完了を待機する時間を定義します。 この待機オプションは次のように定義されます。

  **タイムアウト値** (0x00000001 から 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER を選択すると、TFTP サーバーが要求に応答するまで、呼び出し元のスレッドが無期限に一時停止になります。
 
  数値 (1 から 0xFFFFFFFE) を選択すると、TFTP サーバーで書き込み要求に対する ACK の送信を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

- **ip_type** 使用する IP プロトコルを指定します。 有効なオプションは、IPv4 (4) または IPv6 (6) です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) クライアント ブロックが正常に書き込まれました

- **NX_TFTP_NOT_OPEN** (0xC3) 指定されたクライアント ファイルは書き込み用に開かれていません

- **NX_TFTP_TIMEOUT** (0xC1) サーバーの ACK を待機中にタイムアウトになりました

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました

- **NX_TFTP_NO_ACK_RECEIVED** (0x09) サーバーから ACK を受信していません

- **NX_TFTP_INVALID_IP_VERSION** (0x0C) IP バージョンが無効です

- **NX_INVALID_TFTP_SERVER_ADDRESS** (0x08) 無効なサーバー アドレスを受信しました

- **NX_TFTP_CODE_ERROR** (0x05) エラー コードを受信しました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Write a block to the previously opened file of “my_client”. */
status =  nxd_tftp_client_file_write(&my_tftp_client, packet_ptr, 200);

/* If status is NX_SUCCESS the block in the payload of “packet_ptr” was 
   written to the TFTP file opened by “my_client”. */
```

## <a name="nxd_tftp_client_packet_allocate"></a>nxd_tftp_client_packet_allocate

クライアント ファイル書き込み用のパケットを割り当てる

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_packet_allocate(NX_PACKET_POOL *pool_ptr,
                        NX_PACKET **packet_ptr, ULONG wait_option,
                        UINT ip_type);
```

### <a name="description"></a>説明

このサービスでは、指定されたパケット プールから UDP パケットを割り当て、パケットが呼び出し元に返される前に 4 バイトの TFTP ヘッダー用の領域を確保します。 その後、呼び出し元では、クライアント ファイルに書き込むためのバッファーを作成できます。

### <a name="input-parameters"></a>入力パラメーター

- **pool_ptr** パケット プールへのポインター。

- **packet_ptr** 割り当てられたパケットへのポインターの宛先。

- **wait_option** パケットの割り当てが完了するまでサービスが待機する時間を定義します。 この待機オプションは次のように定義されます。

  **タイムアウト値** (0x00000001 から 0xFFFFFFFE)

  **TX_WAIT_FOREVER** (0xFFFFFFFF)

  TX_WAIT_FOREVER を選択すると、呼び出し元のスレッドは、割り当てが完了するまで無期限に一時停止になります。

  数値 (1 から 0xFFFFFFFE) を選択すると、パケットの割り当てを待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

- **ip_type** 使用する IP プロトコルを指定します。 有効なオプションは、IPv4 (4) または IPv6 (6) です。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) パケットが正常に割り当てられました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_INVALID_PARAMETERS (0x4D) 無効な非ポインター入力です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Allocate a packet for TFTP file write. */
status =  nxd_tftp_client_packet_allocate(&my_pool, &packet_ptr, 200);

/* If status is NX_SUCCESS “packet_ptr” contains the new packet. */
```

## <a name="nxd_tftp_client_set_interface"></a>nxd_tftp_client_set_interface

TFTP 要求の物理インターフェイスを設定する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_client_set_interface(NX_TFTP_CLIENT *tftp_client_ptr,
                                    UINT if_index);
```

### <a name="description"></a>説明

このサービスでは、入力インターフェイス インデックスを使用して、TFTP パケットを送受信する TFTP クライアントの物理インターフェイスを設定します。 プライマリ インターフェイスの既定値は 0 です。

> [!NOTE]
> NetX Duo では、このサービスを使用するために、マルチホーム アドレス指定 (v5.6 以降) をサポートしている必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_client_ptr** TFTP クライアント インスタンスへのポインター

- **if_index** 使用する物理インターフェイスのインデックス

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) インターフェイスが正常に設定されました (0x0B) インターフェイス入力が無効です

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

- NX_TFTP_INVALID_INTERFACE (0x0B) インターフェイス入力が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Specify the primary interface for TFTP requests. */
status =  nxd_tftp_client_set_interface(&client, 0);

/* If status is NX_SUCCESS the primary interface will be use for TFTP communications. */
```

## <a name="nxd_tftp_server_create"></a>nxd_tftp_server_create

TFTP サーバーを作成する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_server_create(NX_TFTP_SERVER *tftp_server_ptr,
            CHAR *tftp_server_name, NX_IP *ip_ptr, FX_MEDIA *media_ptr, 
            VOID *stack_ptr, ULONG stack_size,
            NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>説明

このサービスでは、ポート 69 で TFTP クライアント要求に応答する TFTP サーバーを作成します。 サーバーは、*nxd_tftp_server_start* の後続の呼び出しによって開始される必要があります。

> [!IMPORTANT]
> アプリケーションでは、指定された IP インスタンス、パケット プール、および FileX メディア インスタンスが既に作成されていることを確認する必要があります。 さらに、このサービスを呼び出す前に、IP インスタンスに対して UDP を有効にする必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。

- **tftp_server_name** この TFTP サーバー インスタンスの名前

- **ip_ptr** 以前に作成された IP インスタンスへのポインター。

- **media_ptr** FileX メディア インスタンスへのポインター。

- **stack_ptr** TFTP サーバーのスタック領域へのポインター。

- **stack_size** TFTP サーバー スタック内のバイト数。

- **pool_ptr** TFTP パケット プールへのポインター。 

> [!NOTE]
> 指定されたプールには、サイズが 580 バイト以上のパケット ペイロードが必要です。<sup>1</sup>

<sup>1</sup> パケットのデータ部分はちょうど 512 バイトですが、パケット ペイロードのサイズは 572 バイト以上である必要があります。 残りのバイト数は、UDP、IPv6、イーサネット ヘッダー、およびドライバーがアラインメントに必要とする可能性のある後続バイトに使用されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に作成されました

- **NX_TFTP_POOL_ERROR** (0xC6) パケット プールのパケット サイズが 560 バイト未満です

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Create a TFTP Server called “my_server”. */
status =  nxd_tftp_server_create(&my_server, “My TFTP Server”, &server_ip, 
                &ram_disk, stack_ptr, 2048, pool_ptr);

/* If status is NX_SUCCESS the TFTP Server is created. */
```

## <a name="nxd_tftp_server_delete"></a>nxd_tftp_server_delete

TFTP サーバーを削除する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_server_delete(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成された TFTP サーバーが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に削除されました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Delete the TFTP Server called “my_server”. */
status =  nxd_tftp_server_delete(&my_server);

/* If status is NX_SUCCESS the TFTP Server is deleted. */
```

## <a name="nxd_tftp_server_start"></a>nxd_tftp_server_start

TFTP サーバーを起動する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_server_start(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成した TFTP サーバーを起動します。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に起動しました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。
 
### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```C
/* Start the TFTP Server called “my_server”. */
status =  nxd_tftp_server_start(&my_server);

/* If status is NX_SUCCESS the TFTP Server is started. */
```

## <a name="nxd_tftp_server_stop"></a>nxd_tftp_server_stop

TFTP サーバーを停止する

### <a name="prototype"></a>プロトタイプ

```C
UINT nxd_tftp_server_stop(NX_TFTP_SERVER *tftp_server_ptr);
```

### <a name="description"></a>説明

このサービスでは、以前に作成した TFTP サーバーを停止します。

### <a name="input-parameters"></a>入力パラメーター

- **tftp_server_ptr** TFTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS** (0x00) サーバーが正常に停止しました

- NX_PTR_ERROR (0x16) ポインターの入力が無効です。

- NX_CALLER_ERROR (0x11) このサービスの呼び出し元が無効です

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```C
/* Stop the TFTP Server called “my_server”. */
status =  nxd_tftp_server_stop(&my_server);

/* If status is NX_SUCCESS the TFTP Server is stopped. */
```