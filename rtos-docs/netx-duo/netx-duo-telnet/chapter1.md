---
title: チャプター 1 -Azure RTOS NetX Duo Telnet の概要
description: Azure RTOS NetX Duo Telnet は、コマンドと応答をインターネット上の 2 つのノード間で転送するためのプロトコルです。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 50a2c4d8726863f4e609debadd9ddf2455cfd540219a476970756d3d250ec562
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116799032"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-duo-telnet"></a>チャプター 1 -Azure RTOS NetX Duo Telnet の概要

Azure RTOS NetX Duo Telnet は、コマンドと応答をインターネット上の 2 つのノード間で転送するためのプロトコルです。 Telnet は、信頼性の高い伝送制御プロトコル (TCP) サービスを使用して転送処理を実行する単純なプロトコルです。 そのため、Telnet は信頼性の高い転送プロトコルとなっています。 Telnet は、最も多く使用されているアプリケーション プロトコルの 1 つでもあります。

## <a name="telnet-requirements"></a>Telnet の要件

NetX Duo Telnet パッケージが正常に機能するためには、NetX IP インスタンスを前もって作成しておく必要があります。 また、その IP インスタンスで TCP を有効にする必要があります。 NetX Duo Telnet パッケージに含まれる Telnet クライアントには、それ以上の要件はありません。

NetX Duo Telnet パッケージに含まれる Telnet サーバーには、1 つ追加要件があります。 Telnet サーバーでは、クライアントのすべての Telnet 要求を処理するために、ウェルノウン ポートである TCP *ポート 23* への完全なアクセスが必要です。

## <a name="telnet-constraints"></a>Telnet の制約 

NetX Duo Telnet プロトコルでは Telnet 標準を実装しています。 ただし、255 の値を持つバイトで示される Telnet コマンドを解釈してそれに応答するのは、アプリケーションの役割です。 さまざまな Telnet コマンドおよびコマンドのパラメーターは、*nxd_telnet_client.h および nxd_telnet_server.h* ファイルで定義されています。

## <a name="telnet-communication"></a>Telnet 通信

前述のとおり、Telnet サーバーでは、ウェルノウン ポートである *TCP ポート 23* を使用してクライアントの要求を処理します。 Telnet クライアントでは、任意の空き TCP ポートを使用できます。

## <a name="telnet-authentication"></a>Telnet 認証

Telnet 認証は、アプリケーションの Telnet サーバーのコールバック関数で行います。 アプリケーションの Telnet サーバーの “新規接続”コールバックでは通常、名前やパスワードの入力を求めるメッセージをクライアントに表示します。 そして、クライアントがその情報を渡します。 それから、サーバーが “データ受信” コールバックで情報を処理します。 その際、アプリケーションのサーバー コードにより情報を認証して有効性を判断することもできます。

## <a name="telnet-new-connection-callback"></a>Telnet 新規接続コールバック

NetX Duo Telnet サーバーでは、Telnet クライアントから新たな要求を受信するたびに、アプリケーションで指定するコールバック関数を呼び出します。 このコールバック関数は、アプリケーションで ***nx_telnet_server_create*** 関数を使用して Telnet サーバーを作成するときに指定します。 “新規接続” コールバックでは通常、クライアントにバナーまたはプロンプトを送信します。 ログイン情報の入力を求めるプロンプトをここに含める場合も多いです。

### <a name="prototype"></a>プロトタイプ

```c
void  telnet_new_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: 呼び出し元の Telnet サーバーへのポインター。
- **logical_connection**: Telnet サーバーで使用する、内部の論理的な接続。 この接続は、各クライアント接続に固有のバッファーおよびデータ構造体のインデックスとしてアプリケーションで使用できます。 取り得る値の範囲は 0 から NX_TELNET_MAX_CLIENTS - 1 です。

## <a name="telnet-receive-data-callback"></a>Telnet データ受信コールバック

NetX Duo Telnet サーバーでは、Telnet クライアントの新たなデータを受信するたびに、アプリケーションで指定したコールバック関数を呼び出します。 このコールバック関数は、アプリケーションで ***nx_telnet_server_create*** 関数を使用して Telnet サーバーを作成するときに指定します。 “新規接続” コールバックでは通常、データのエコー バックや解析を行い、クライアントのコマンドを解釈して得られたデータを返します。

このコールバック ルーチンでは、受け取ったパケットを解放する必要もあります。

### <a name="prototype"></a>プロトタイプ

```c
void  telnet_receive_data(NX_TELNET_SERVER *server_ptr, 
                          UINT logical_connection, NX_PACKET *packet_ptr);
```
### <a name="input-parameters"></a>入力パラメーター

- **server_ptr**: 呼び出し元の Telnet サーバーへのポインター。
- **logical_connection**: Telnet サーバーで使用する、内部の論理的な接続。 この接続は、各クライアント接続に固有のバッファーおよびデータ構造体のインデックスとしてアプリケーションで使用できます。 取り得る値の範囲は 0 から NX_TELNET_MAX_CLIENTS - 1 です。
- **packet_ptr**: クライアントから受け取ったデータを保持するパケットへのポインター。

## <a name="telnet-end-connection-callback"></a>Telnet 接続終了コールバック

NetX Duo Telnet サーバーでは、Telnet クライアントが接続を終了するたびに、アプリケーションで指定したコールバック関数を呼び出します。 このコールバック関数は、アプリケーションで ***nx_telnet_server_create*** 関数を使用して Telnet サーバーを作成するときに指定します。 “終了接続” コールバックでは通常、論理的な接続に関連付けられた各クライアント固有のデータ構造体をすべて消去します。

### <a name="prototype"></a>プロトタイプ
```c
void  telnet_end_connection(NX_TELNET_SERVER *server_ptr, 
                            UINT logical_connection);
```

### <a name="input-parameters"></a>入力パラメーター

- **server_ptr** 呼び出し元の Telnet サーバーへのポインター。
- **logical_connection** Telnet サーバーで使用する、内部の論理的な接続。 この接続は、各クライアント接続に固有のバッファーおよびデータ構造体のインデックスとしてアプリケーションで使用できます。 取り得る値の範囲は 0 から NX_TELNET_MAX_CLIENTS - 1 です。

## <a name="telnet-option-negotiation"></a>Telnet オプションのネゴシエーション

NetX Duo Telnet サーバーは Telnet オプションの一部、Echo と Supress Go Ahead をサポートしています。

この機能を有効にするには NX_TELNET_SERVER_OPTION_DISABLE を無効にする必要があります。 これは既定では有効になっていません。 Telnet サーバーでは、Telnet オプション要求をクライアントに送信するためのパケットを、*nx_telnet_server_create* サービスで作成したパケット プールから割り当てます。 このパケット プールのパケットのペイロードのサイズ (NX_TELNET_SERVER_PACKET_PAYLOAD) とパケット プールそのもののサイズ (NX_TELNET_SERVER_PACKET_POOL_SIZE) の設定については「構成オプション」をご覧ください。 *nx_telnet_server_delete* サービスをび出すと、このパケット プールは削除されます。

Telnet クライアントからのオプション要求を受信していない状態で Telnet サーバーがこのクライアントに接続すると、次の Telnet オプションをクライアントに送信します:

- エコーする
- エコーしない
- SGA を行う

クライアントから Telnet データを受信すると、Telnet サーバーは最初のバイトが “IAC” コードであるかどうかを確認します。 “IAC” コードである場合は、クライアント パケットにあるすべてのオプションを処理します。 上のリストにないオプションは無視します。

既定では、NX_TELNET_SERVER_OPTION_DISABLE が有効になっていない状態で Telnet オプションのコマンドを送信する必要がある場合、Telnet サーバーは自身専用のパケット プールを作成します。 Telnet サーバーのパケット プールの設定は NX_TELNET_SERVER_PACKET_PAYLOAD と NX_TELNET_SERVER_PACKET_POOLSIZE で行います。 ただし、NX_TELNET_SERVER_USER_CREATE_PACKET_POOL が有効である場合は、アプリケーションで Telnet サーバー用にパケット プールを作成し、 *_nx_telnet_server_packet_pool_set* を呼び出してそれを Telnet サーバーのパケット プールに設定する必要があります。 この関数の詳細は、チャプター 3「Telnet サービスの説明」をご覧ください。

NetX Duo Telnet サーバーと異なり、NetX Duo Telnet クライアントのタスク スレッドでは、Telnet サーバーから受信したオプションに対して自動で応答しません。 これは Telnet クライアント アプリケーションで行う必要があります。

## <a name="telnet-multi-thread-support"></a>Telnet のマルチスレッド サポート

NetX Duo Telnet クライアントのサービスは複数のスレッドから同時に呼び出せます。 ただし、特定の Telnet クライアント インスタンスに対する読み取り、書き込み要求は、1 つずつ同じスレッドから実行する必要があります。

## <a name="telnet-rfcs"></a>Telnet に関連する RFC

NetX Duo Telnet は、RFC 854 とその他の関連 RFC に準拠しています。
