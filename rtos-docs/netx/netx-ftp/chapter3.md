---
title: 第 3 章 - Azure RTOS NetX FTP サービスの説明
description: この章では、すべての Azure RTOS NetX FTP サービス (以下に記載) をアルファベット順に説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b05d03c45607c45acf32474cf8e40861532c5fae
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811537"
---
# <a name="chapter-3---description-of-azure-rtos-netx-ftp-services"></a>第 3 章 - Azure RTOS NetX FTP サービスの説明

この章では、すべての Azure RTOS NetX FTP サービス (以下に記載) をアルファベット順に説明します。

以下の API の説明の「戻り値」セクションでは、**太字** の値は API のエラー チェックを無効にするために使用される **NX_DISABLE_ERROR_CHECKING** 定義の影響を受けませんが、太字以外の値は完全に無効になります。

- **nx_ftp_client_connect**: "*FTP サーバーに接続する*"
- **nx_ftp_client_create**: "*FTP クライアント インスタンスを作成する*"
- **nx_ftp_client_delete**: "*FTP クライアント インスタンスを削除する*"
- **nx_ftp_client_directory_create**: "*サーバーにディレクトリを作成する*"
- **nx_ftp_client_directory_default_set**: "*サーバーに既定のディレクトリを設定する*"
- **nx_ftp_client_directory_delete**: "*サーバー上のディレクトリを削除する*"
- **nx_ftp_client_directory_listing_get**: "*サーバーからディレクトリの一覧を取得する*"
- **nx_ftp_client_directory_listing_continue**: "*サーバーからのディレクトリの一覧を続行する*"
- **nx_ftp_client_disconnect**: "*FTP サーバーから切断する*"
- **nx_ftp_client_file_close**: "*クライアント ファイルを閉じる*"
- **nx_ftp_client_file_delete**: "*サーバー上のファイルを削除する*"
- **nx_ftp_client_file_open**: "*クライアント ファイルを開く*"
- **nx_ftp_client_file_read**: "*ファイルから読み取る*"
- **nx_ftp_client_file_rename**: "*サーバー上のファイルの名前を変更する*"
- **nx_ftp_client_file_write**: "*ファイルに書き込む*"
- **nx_ftp_server_create**: "*FTP サーバーを作成する*"
- **nx_ftp_server_delete**: "*FTP サーバーを削除する*"
- **nx_ftp_server_start**: "*FTP サーバーを開始する*"
- **nx_ftp_server_stop**: "*FTP サーバーを停止する*"

## <a name="nx_ftp_client_connect"></a>nx_ftp_client_connect

FTP サーバーに接続します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_connect(NX_FTP_CLIENT *ftp_client_ptr,
        ULONG server_ip, CHAR *username, CHAR *password,
        ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、以前に作成された FTP クライアント インスタンスが、指定された IP アドレスの FTP サーバーに接続されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **server_ip**: FTP サーバーの IP アドレス。
- **username**: 認証用のクライアント ユーザー名。
- **password**: 認証用のクライアント パスワード。
- **wait_option**: FTP クライント接続をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP 接続に成功しました。
- **NX_TFTP_EXPECTED_22X_CODE**: (0xDB) 22X (ok) 応答を取得しませんでした
- **NX_FTP_EXPECTED_23X_CODE**: (0xDC) 23X (ok) 応答を取得しませんでした
- **NX_FTP_EXPECTED_33X_CODE**: (0xDE) 33X (ok) 応答を取得しませんでした
- **NX_FTP_NOT_DISCONNECTED**: (0xD4) クライアントは既に接続されています。
- NX_PTR_ERROR: (0x07) ポインター入出力が無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。
- NX_IP_ADDRESS_ERROR: (0x21) IP アドレスが無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Connect the FTP Client instance "my_client" to the FTP Server at
    IP address 1.2.3.4. */
status = nx_ftp_client_connect(&my_client, IP_ADDRESS(1,2,3,4), NULL, NULL, 100);

/* If status is NX_SUCCESS an FTP Client instance was successfully  
connected to the FTP Server. */
```

## <a name="nx_ftp_client_create"></a>nx_ftp_client_create

FTP クライアント インスタンスを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_create(NX_FTP_CLIENT *ftp_client_ptr,
    CHAR *ftp_client_name, NX_IP *ip_ptr, ULONG window_size,
    NX_PACKET_POOL *pool_ptr);
```

### <a name="description"></a>説明

このサービスにより、FTP クライアント インスタンスが作成されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **ftp_client_name**: FTP クライアントの名前。
- **ip_ptr**: 以前に作成された IP インスタンスへのポインター。
- **window_size**: この FTP クライアントの TCP ソケットのアドバタイズされたウィンドウ サイズ。
- **pool_ptr**: この FTP クライアントの既定のパケット プールへのポインター。 最小パケット ペイロードは、完全なパスとファイルまたはディレクトリ名を保持するのに十分な大きさである必要があることに注意してください。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP クライアントが正常に作成されました。
- NX_PTR_ERROR: (0x16) FTP、IP ポインター、またはパケット プール ポインターが無効です。 パスワード ポインター。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create the FTP Client instance "my_client." */
status = nx_ftp_client_create(&my_client, "My Client", &client_ip,
                                2000, &client_pool);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
created. */
```

## <a name="nx_ftp_client_delete"></a>nx_ftp_client_delete

FTP クライアント インスタンスを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_delete(NX_FTP_CLIENT *ftp_client_ptr);
```

### <a name="description"></a>説明

このサービスにより、FTP クライアント インスタンスが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP クライアントが正常に削除されました。
- **NX_FTP_NOT_DISCONNECTED**: (0xD4) FTP クライアントの削除エラー。
- NX_PTR_ERROR: (0x16) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete the FTP Client instance "my_client." */
status = nx_ftp_client_delete(&my_client);

/* If status is NX_SUCCESS the FTP Client instance was successfully  
    deleted. */
```

## <a name="nx_ftp_client_directory_create"></a>nx_ftp_client_directory_create

FTP サーバーにディレクトリを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_directory_create(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上に、指定されたディレクトリが作成されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **directory_name**: 作成するディレクトリの名前。
- **wait_option**: FTP ディレクトリの作成をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に作成されました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした 
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。 
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Create the directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_create(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" was successfully  
    created. */
```

## <a name="nx_ftp_client_directory_default_set"></a>nx_ftp_client_directory_default_set

FTP サーバーに既定のディレクトリを設定します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_directory_default_set(NX_FTP_CLIENT *ftp_client_ptr,
                                CHAR *directory_path, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定された FTP クライアントに接続されている FTP サーバーに既定のディレクトリが設定されます。 この既定のディレクトリは、このクライアントの接続にのみ適用されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **directory_path**: 設定するディレクトリ パスの名前。
- **wait_option**: FTP の既定のディレクトリの設定をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP の既定の設定に成功しました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした 
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。 
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Set the default directory to "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_default_set(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is the default directory. */
```

## <a name="nx_ftp_client_directory_delete"></a>nx_ftp_client_directory_delete

FTP サーバー上のディレクトリを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_directory_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *directory_name, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上の指定されたディレクトリが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **directory_name**: 削除するディレクトリの名前。
- **wait_option**: FTP ディレクトリの削除をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に削除されました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした 
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。 
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_delete(&my_client, "my_dir", 200);

/* If status is NX_SUCCESS the directory "my_dir" is deleted. */
```

## <a name="nx_ftp_client_directory_listing_get"></a>nx_ftp_client_directory_listing_get

FTP サーバーからディレクトリの一覧を取得します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_directory_listing_get(NX_FTP_CLIENT *ftp_client_ptr,
                            CHAR *directory_name, NX_PACKET **packet_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上の指定されたディレクトリのコンテンツが取得されます。 指定されたパケット ポインターには、1 つ以上のディレクトリ エントリが含まれます。 それぞれのエントリは、&lt;cr/lf\ の組み合わせで区切られます。 ディレクトリの取得操作を完了するには、***nx_ftp_client_directory_listing_continue*** を呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **directory_name**: コンテンツを取得するディレクトリの名前。
- **packet_ptr**: 宛先パケット ポインターへのポインター。 成功した場合、パケット ペイロードには 1 つ以上のディレクトリ エントリが格納されます。
- **wait_option**: FTP ディレクトリの一覧をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に一覧されました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_NOT_ENABLED**: (0x14) サービス (IPv6) が有効になっていません
- **NX_FTP_EXPECTED_1XX_CODE**: (0xD9) 1XX (ok) 応答を取得しませんでした
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Get the contents of directory "my_dir" on the FTP Server connected to
    the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_get(&my_client, "my_dir", &my_packet,
                                            200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_directory_listing_continue"></a>nx_ftp_client_directory_listing_continue

FTP サーバーからのディレクトリの一覧取得を続行します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_directory_listing_continue(NX_FTP_CLIENT
                    *ftp_client_ptr, NX_PACKET **packet_ptr,
                    ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定された FTP クライアントに接続されている FTP サーバー上の指定されたディレクトリのコンテンツの取得が続行されます。 直前に ***nx_ftp_client_directory_listing_get*** の呼び出しが必要です。 成功した場合、指定されたパケット ポインターには、1 つ以上のディレクトリ エントリが含まれます。 このルーチンは、NX_FTP_END_OF_LISTING の状態を受信するまで呼び出す必要があります。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **packet_ptr**: 宛先パケット ポインターへのポインター。 成功した場合、パケット ペイロードには、&lt;cr/lf&gt; で区切られた 1 つ以上のディレクトリ エントリが格納されます。
- **wait_option**: FTP ディレクトリの一覧をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ディレクトリトが正常に一覧されました。
- **NX_FTP_END_OF_LISTING**: (0xD8) このディレクトリにはこれ以上エントリがありません。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_2XX_CODE** (0xDA) 2XX (ok) 応答を取得しませんでした
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Continue getting the contents of directory "my_dir" on the FTP Server
    connected to the FTP Client instance "my_client." */
status = nx_ftp_client_directory_listing_continue(&my_client, &my_packet,
                                                200);

/* If status is NX_SUCCESS, one or more entries of the directory "my_dir"
    can be found in "my_packet". */
```

## <a name="nx_ftp_client_disconnect"></a>nx_ftp_client_disconnect

FTP サーバーから切断します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_disconnect(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定された FTP クライアントとの間に以前に確立された FTP サーバー接続が切断されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **wait_option**: FTP クライントの切断をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP の切断に成功しました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Disconnect "my_client" from the FTP Server. */
status = nx_ftp_client_disconnect(&my_client, 200);

/* If status is NX_SUCCESS, "my_client" has been disconnected. */
```

## <a name="nx_ftp_client_file_close"></a>nx_ftp_client_file_close

クライアント ファイルを閉じます

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_file_close(NX_FTP_CLIENT *ftp_client_ptr,
                            ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、FTP サーバー上で既に開いているファイルが閉じられます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **wait_option**: FTP クライントのファイルが閉じられるのをこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ファイルが正常に閉じられました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_NOT_OPEN (0xD5)** : ファイルが開かれていません。閉じることができません
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Close previously opened file of client "my_client" on the FTP Server. */
status = nx_ftp_client_file_close(&my_client, 200);

/* If status is NX_SUCCESS, the file opened previously in the "my_client" FTP
    connection has been closed. */
```

## <a name="nx_ftp_client_file_delete"></a>nx_ftp_client_file_delete

FTP サーバー上のファイルを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_file_delete(NX_FTP_CLIENT *ftp_client_ptr,
                        CHAR *file_name, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、FTP サーバー上の指定したファイルが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **file_name**: 削除するファイルの名前。
- **wait_option**: FTP クライントのファイルの削除をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ファイルが正常に削除されました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete the file "my_file.txt" on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_delete(&my_client, "my_file.txt", 200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    deleted. */
```

## <a name="nx_ftp_client_file_open"></a>nx_ftp_client_file_open

FTP サーバー上のファイルを開きます

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_file_open(NX_FTP_CLIENT *ftp_client_ptr,
        CHAR *file_name, UINT open_type, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、指定したクライアント インスタンスに接続済みの FTP サーバー上の指定したファイルが (読み取りまたは書き込み用に) 開かれます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **file_name**: 開くファイルの名前。
- **open_type**: **NX_FTP_OPEN_FOR_READ** または **NX_FTP_OPEN_FOR_WRITE**。
- **wait_option**: FTP クライントのファイルが開かれるのをこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ファイルが正常に開かれました。
- **NX_OPTION_ERROR** :(0x0A) オープン型が無効です。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_NOT_CLOSED**: (0xD6) FTP クライアントは既に開かれています。
- **NX_NO_FREE_PORTS**: (0x45) 割り当てることのできる TCP ポートがありません
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Open the file "my_file.txt" for reading on the FTP Server using the previously
    connected client "my_client." */
status = nx_ftp_client_file_open(&my_client, "my_file.txt", NX_FTP_OPEN_FOR_READ,
                                200);

/* If status is NX_SUCCESS, the file "my_file.txt" on the FTP Server is
    open for reading. */
```

## <a name="nx_ftp_client_file_read"></a>nx_ftp_client_file_read

ファイルから読み取ります

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_file_read(NX_FTP_CLIENT *ftp_client_ptr,
                NX_PACKET **packet_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、以前に開かれたファイルからパケットが読み取られます。 NX_FTP_END_OF_FILE の状態が受信されるまで繰り返し呼び出す必要があります。

このサービスのパケットは呼び出し元によって割り当てられないことに注意してください。  指定する必要があるのはパケット ポインターへのポインターだけです。 このサービスにより、ソケット受信キューから取得されたパケットを指すようにそのパケット ポインターが更新されます。  正常状態が返された場合は、パケットが使用可能であったことを意味します。また、終了時にパケットを解放するのは呼び出し元の責任です。

0 以外の状態 (エラー状態または NX_FTP_END_OF_FILE) が返された場合、パケットは呼び出し元によって解放されません。 それ以外の場合は、パケット ポインターが NULL の場合にエラーが生成されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **packet_ptr**: キューから取得したデータ パケット ポインターの宛先へのポインター。 成功した場合、パケット データにはファイルの一部またはすべてが含まれます。
- **wait_option**: FTP クライントのファイルの読み取りをこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ファイルが正常に読み取られました。
- **NX_FTP_NOT_OPEN**: (0xD5) FTP クライアントが開かれていません。
- **NX_FTP_END_OF_FILE**: (0xD7) ファイルの終わりの条件。
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
       NX_PACKET   *my_packet;

/* Read a packet of data from the file "my_file.txt" that was previously opened
    from the client "my_client." */

status = nx_ftp_client_file_read(&my_client, &my_packet, 200);

        /* Check status.  */
        if (status != NX_SUCCESS)
        {
            error_counter++;
        }
        else
        {
            /* Release packet when done with it. */
            nx_packet_release(my_packet);
        }

/* If status is NX_SUCCESS, the packet pointer, "my_packet" points to the packet
that contains the next bytes from the file. If the file is completely
downloaded, an NX_FTP_END_OF_FILE status is returned (no packet retrieved). */
```

## <a name="nx_ftp_client_file_rename"></a>nx_ftp_client_file_rename

FTP サーバー上のファイルの名前を変更します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_file_rename(NX_FTP_CLIENT *ftp_ptr, CHAR *filename,
                                CHAR *new_filename, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、FTP サーバー上のファイルの名前が変更されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **filename**: ファイルの現在の名前。
- **new_filename**: ファイルの新しい名前。
- **wait_option**: FTP クライントのファイル名の変更をこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ファイルの名前が正常に変更されました。
- **NX_FTP_NOT_CONNECTED**: (0xD3) FTP クライアントが接続されていません。
- **NX_FTP_EXPECTED_3XX_CODE**: (0XDD) 3XX (ok) 応答を受信しませんでした
- **NX_FTP_EXPECTED_2XX_CODE**: (0xDA) 2XX (ok) 応答を取得しませんでした
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Rename file "my_file.txt" to "new_file.txt" on the previously connected
    Client instance "my_client." */

status = nx_ftp_client_file_rename(&my_client, "my_file.txt", "new_file.txt",
                                    200);

/* If status is NX_SUCCESS, the file has been renamed. */
```

## <a name="nx_ftp_client_file_write"></a>nx_ftp_client_file_write

ファイルに書き込みます

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_file_write(NX_FTP_CLIENT *ftp_client_ptr,
                    NX_PACKET *packet_ptr, ULONG wait_option);
```

### <a name="description"></a>説明

このサービスにより、FTP サーバー上の以前に開かれたファイルにデータのパケットが書き込まれます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **packet_ptr**: 書き込むデータが格納されているパケット ポインター。
- **wait_option**: FTP クライントのファイルの書き込みをこのサービスで待機する時間の長さを定義します。 この待機オプションは次のように定義されます。
  - **timeout value**: (0x00000001 から 0xFFFFFFFE)
  - **TX_WAIT_FOREVER**: (0xFFFFFFFF) TX_WAIT_FOREVER を選択すると、FTP サーバーが要求に応答するまで、呼び出しスレッドが無期限に中断されます。 数値 (1 から 0xFFFFFFFE) を選択すると、FTP サーバーの応答を待機している間に一時停止を続けるタイマーティックの最大数が指定されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP ファイルが正常に書き込まれました。
- **NX_FTP_NOT_OPEN**: (0xD5) FTP クライアントが開かれていません。
- NX_PTR_ERROR: (0x07) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Write the data contained in "my_packet" to the previously opened file
    "my_file.txt". */

status = nx_ftp_client_file_write(&my_client, my_packet, 200);

/* If status is NX_SUCCESS, the file has been written to. */
```

## <a name="nx_ftp_client_passive_mode_set"></a>nx_ftp_client_passive_mode_set

パッシブ転送モードを有効または無効にします

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_client_passive_mode_set(NX_FTP_CLIENT *ftp_client_ptr,
                                    UINT passive_mode_enabled);
```

### <a name="description"></a>説明

このサービスにより、以前に作成された FTP クライアント インスタンス上で passive_mode_enabled 入力が NX_TRUE に設定されている場合にパッシブ転送モードが有効化されます。これにより、ファイルの読み取りや書き込み (RETR、STOR) またはディレクトリ一覧のダウンロード (NLST) に対する後続の呼び出しは、転送モードで実行されます。 パッシブ モードの転送を無効にして、アクティブ転送モードの既定の動作に戻すには、passive_mode_enabled 入力を NX_FALSE に設定して、この関数を呼び出します。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_client_ptr**: FTP クライアントの制御ブロックへのポインター。
- **passive_mode_enabled**:
  - NX_TRUE に設定すると、パッシブ モードが有効になります。
  - NX_FALSE に設定すると、パッシブ モードが無効になります。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) パッシブ モードの設定に成功しました。
- NX_PTR_ERROR: (0x16) FTP ポインターが無効です。
- NX_INVALID_PARAMETERS: (0x4D) ポインターではない無効な入力

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Enable the FTP Client to exchange data with the FTP server in passive mode. */

status = nx_ftp_client_passive_mode_set(&my_client, NX_TRUE);

/* If status is NX_SUCCESS, the FTP client is in passive transfer mode. */
```

## <a name="nx_ftp_server_create"></a>nx_ftp_server_create

FTP サーバーを作成します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_server_create(NX_FTP_SERVER *ftp_server_ptr,
        CHAR *ftp_server_name, NX_IP *ip_ptr,
        FX_MEDIA *media_ptr, VOID *stack_ptr, ULONG stack_size,
        NX_PACKET_POOL *pool_ptr,
        UINT (*ftp_login)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info),
        UINT (*ftp_logout)(struct NX_FTP_SERVER_STRUCT
                *ftp_server_ptr, ULONG client_ip_address,
                UINT client_port, CHAR *name, CHAR *password,
                CHAR *extra_info));
```

### <a name="description"></a>説明

このサービスにより、指定した作成済みの NetX IP インスタンス上に FTP サーバー インスタンスが作成されます。 操作を開始するには、***nx_ftp_server_start*** の呼び出しを使用して FTP サーバーを開始する必要があることに注意してください。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。
- **ftp_server_name**: FTP サーバーの名前。
- **ip_ptr**: 関連付けられた NetX IP インスタンスへのポインター。 1 つの IP インスタンスにつき 1 つの FTP サーバーしか存在できないことに注意してください。
- **media_ptr**: 関連付けられた FileX メディア インスタンスへのポインター。
- **stack_ptr**: 内部 FTP サーバー スレッドのスタック領域のメモリへのポインター。
- **stack_size**: *stack_ptr* によって指定されたスタック領域のサイズ。
- **pool_ptr**: 既定の NetX パケット プールへのポインター。 プール内のパケットのペイロード サイズは、最大のファイル名またはパスを格納するのに十分な大きさである必要があることに注意してください。
- **ftp_login**: アプリケーションのログイン関数への関数ポインター。 この関数には、接続を要求しているクライアントからのユーザー名とパスワードが指定されます。 これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。
- **ftp_logout**: アプリケーションのログアウト関数への関数ポインター。 この関数には、切断を要求しているクライアントからのユーザー名とパスワードが指定されます。 これが有効な場合、アプリケーションのログイン関数から NX_SUCCESS が返されます。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP サーバーが正常に作成されました。
- NX_PTR_ERROR: (0x16) FTP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Create the FTP Server "my_server" on the IP instance "ip_0" using the
    "ram_disk" media. */

status = nx_ftp_server_create(&my_server, "My Server Name", &ip_0, &ram_disk,
                                stack_ptr, stack_size, &pool_0,
                                my_login, my_logout);

/* If status is NX_SUCCESS, the FTP Server has been created. */
```

## <a name="nx_ftp_server_delete"></a>nx_ftp_server_delete

FTP サーバーを削除します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_server_delete(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>説明

このサービスにより、以前に作成された FTP サーバー インスタンスが削除されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP サーバーが正常に削除されました。
- NX_PTR_ERROR: (0x16) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Delete the FTP Server "my_server". */

status = nx_ftp_server_delete(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been deleted. */
```

## <a name="nx_ftp_server_start"></a>nx_ftp_server_start

FTP サーバーを開始します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_server_start(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>説明

このサービスにより、作成済みの FTP サーバー インスタンスが開始されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP サーバーが正常に開始されました。
- NX_PTR_ERROR: (0x16) FTP ポインターが無効です。

### <a name="allowed-from"></a>許可元

初期化、スレッド

### <a name="example"></a>例

```c
/* Start the FTP Server "my_server". */

status = nx_ftp_server_start(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been started. */
```

## <a name="nx_ftp_server_stop"></a>nx_ftp_server_stop

FTP サーバーを停止します

### <a name="prototype"></a>プロトタイプ

```c
UINT nx_ftp_server_stop(NX_FTP_SERVER *ftp_server_ptr);
```

### <a name="description"></a>説明

このサービスにより、以前に作成され、開始された FTP サーバー インスタンスが停止されます。

### <a name="input-parameters"></a>入力パラメーター

- **ftp_server_ptr**: FTP サーバーの制御ブロックへのポインター。

### <a name="return-values"></a>戻り値

- **NX_SUCCESS**: (0x00) FTP サーバーが正常に停止されました。
- NX_PTR_ERROR: (0x16) FTP ポインターが無効です。
- NX_CALLER_ERROR: (0x11) このサービスの呼び出し元が無効です。

### <a name="allowed-from"></a>許可元

Threads

### <a name="example"></a>例

```c
/* Stop the FTP Server "my_server". */

status = nx_ftp_server_stop(&my_server);

/* If status is NX_SUCCESS, the FTP Server has been stopped. */
```
