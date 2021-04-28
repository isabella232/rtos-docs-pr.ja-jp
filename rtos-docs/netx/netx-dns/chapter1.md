---
title: 第 1 章 - Azure RTOS NetX DNS クライアントの概要
description: Azure RTOS NetX DNS は、ドメイン名と物理 IP アドレス間のマッピングを含む分散型データベースを提供します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3426b0895e259bd70e758aae8b56349082a3a95a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811591"
---
# <a name="chapter-1---introduction-to-the-azure-rtos-netx-dns-client"></a>第 1 章 - Azure RTOS NetX DNS クライアントの概要

Azure RTOS NetX DNS は、ドメイン名と物理 IP アドレス間のマッピングを含む分散型データベースを提供します。 インターネット上には完全なマッピングを含む単一のエンティティが存在しないため、このデータベースは "*分散型*" と呼ばれます。 マッピングの部分を管理するエンティティは、DNS サーバーと呼ばれます。 インターネットは多数の DNS サーバーで構成されており、それぞれにデータベースのサブセットが含まれています。 また、DNS サーバーは、要求されたマッピングがサーバーに存在する場合にのみ、ドメイン名マッピング情報に関する DNS クライアント要求に応答します。

NetX 用 DNS クライアント プロトコルは、1 つ以上の DNS サーバーにマッピング情報を要求するサービスをアプリケーションに提供します。

## <a name="dns-client-setup"></a>DNS クライアントのセットアップ

DNS クライアント パッケージを正しく機能させるには、NetX IP インスタンスが既に作成されている必要があります。

DNS クライアントの作成後、アプリケーションでは、DNS クライアントが管理するサーバー リストに 1 つ以上の DNS サーバーを追加する必要があります。 DNS サーバーを追加するには、アプリケーションで *nx_dns_server_add* サービスを使用します。

NX_DNS_IP_GATEWAY_SERVER オプションが有効になっており、IP インスタンスのゲートウェイ アドレスが 0 以外の場合は、IP インスタンスのゲートウェイがプライマリ DNS サーバーとして自動的に追加されます。 DNS サーバー情報が静的に認識されていない場合は、NetX の動的ホスト構成プロトコル (DHCP) を介して取得することもできます。 詳細については、NetX DHCP ユーザー ガイドをご覧ください。

DNS クライアントには、DNS メッセージを送信するためのパケット プールが必要です。 既定では、このパケット プールは、*nx_dns_create* サービスが呼び出されたときに DNS クライアントによって作成されます。 構成オプションの NX_DNS_PACKET_PAYLOAD と NX_DNS_PACKET_POOL_SIZE を使用すると、アプリケーションでこのパケット プールのパケット ペイロードとパケット プール サイズ (パケット数など) をそれぞれ指定できます。 これらのオプションについては、第 2 章の「構成オプション」セクションで説明しています。

DNS クライアントが独自のパケット プールを作成する代わりに、アプリケーションでパケット プールを作成し、*nx_dns_packet_pool_set* サービスを使用して DNS クライアントのパケット プールとして設定することもできます。 これを行うには、NX_DNS_CLIENT_USER_CREATE_PACKET_POOL オプションを定義する必要があります。 このオプションでは、*nx_dns_packet_pool_set* へのパケット プール ポインター入力として、*nx_packet_pool_create* を使用して以前に作成したパケット プールも必要となります。 NX_DNS_CLIENT_USER_CREATE_PACKET_POOL が有効になっている場合に、DNS クライアント インスタンスが削除されたとき、不要になった DNS クライアント パケット プールを削除するのはアプリケーションの役割です。

>[!NOTE] 
> アプリケーションで **NX_DNS_CLIENT_USER_CREATE_PACKET_POOL オプション** を使用して独自のパケット プールを提供する場合、パケット サイズは、DNS 最大メッセージ サイズ (512 バイト) に加えて、UDP ヘッダー、IPv4 ヘッダー、および MAC ヘッダー用のスペースを保持できる必要があります。

## <a name="dns-messages"></a>DNS メッセージ

DNS では、ホスト名と IP アドレス間のマッピングを取得するためのメカニズムは非常に簡単です。 マッピングを取得するために、DNS クライアントは、解決する必要がある名前または IP アドレスを含む DNS クエリ メッセージを準備します。 次に、サーバー リストの最初の DNS サーバーにこのメッセージが送信されます。 サーバーにマッピングが存在する場合、要求されたマッピング情報が含まれている DNS 応答メッセージを使用して DNS クライアントへの応答が行われます。 サーバーが応答しない場合、DNS クライアントはリストの次のサーバーに対してクエリを実行し、すべての DNS サーバーに照会するまでそれを続けます。 どの DNS サーバーからも応答がない場合、DNS クライアントには DNS メッセージを再送信する再試行ロジックがあります。 DNS クエリの再送信時には、再送信タイムアウトが 2 倍になります。 このプロセスは、最大送信タイムアウト (*nxd_dns.h* で NX_DNS_MAX_RETRANS_TIMEOUT として定義) に達するか、そのサーバーから正常な応答を受信するまで続行されます。

NetX DNS クライアントでは、*nx_dns_host_by_name_get* または *nx_dns_ipv4_address_by_name_get* を呼び出すことで、IPv4 アドレス検索 (A タイプ) を実行できます。 DNS クライアントでは、*nx_dns_host_by_address_get* を使用して、IP アドレスの逆引き参照 (PTR タイプのクエリ) を実行して Web ホスト名を取得できます。

DNS メッセージングでは、UDP プロトコルを利用して要求を送信し、応答を処理します。 DNS サーバーは、クライアントからのクエリをポート番号 53 でリッスンします。 そのため、以前に作成した IP インスタンス (_*_nx_ip_create_**) で ***nx_udp_enable** _ サービスを使用して、NetX で UDP サービスを有効にする必要があります。

この時点で、DNS クライアントがアプリケーションからの要求を受け入れ、DNS クエリを送信する準備ができました。

## <a name="extended-dns-resource-record-types"></a>拡張 DNS リソース レコードの種類

NX_DNS_ENABLE_EXTENDED_RR_TYPES が有効になっている場合、NetX DNS クライアントでは、次のレコードの種類のクエリもサポートされます。

- **CNAME**: エイリアスの正規名が含まれています

- **TXT**: テキスト文字列が含まれています

- **NS**: 権威ネーム サーバーが含まれています

- **SOA**: 権威のゾーンの開始が含まれています

- **MX**: メール交換に使用されます

- **SRV**: ドメインによって提供されるサービスに関する情報が含まれています

種類が CNAME と TXT のレコードを除き、アプリケーションでは、DNS データ レコードを受信するために 4 バイト アラインされたバッファーを提供する必要があります。

NetX DNS クライアントでは、レコード データはバッファー領域を最も効率的に使用できるように格納されます。

ホスト名が可変長である NS レコードのように、レコードの種類で可変データ長が使用されるクエリの場合、NetX DNS クライアントは次のようにデータを保存します。 DNS クライアント クエリで指定されたバッファーは、固定長データの領域と非構造化メモリの領域に編成されます。 メモリ バッファーの先頭は、4 バイト アラインされたレコード エントリに編成されます。 各レコード エントリには、IP アドレスとその IP アドレスの可変長データへのポインターが含まれます。 各 IP アドレスの可変長データは、メモリ バッファーの末尾から始まる非構造化領域のメモリに格納されます。 連続する各レコード エントリの可変長データは、前のレコード エントリの可変データに隣接する次の領域のメモリに保存されます。 そのため、別のレコード エントリと可変データを格納するためのメモリが不足するまで、レコード エントリを格納する構造化されたメモリ領域に向かって可変データが "増大" していきます。

これを次の図に示します。

![D N S ドメイン名 (N S) データの格納の例を示す図](media/image1.png)

DNS ドメイン名 (NS) データの格納の例を上に示します。

このレコード格納形式を使用する NetX DNS クライアント クエリは、レコード バッファーに保存されたレコードの数を返します。 この情報を使用して、アプリケーションはレコード バッファーから NS レコードを抽出できます。

このレコード格納形式を使用して可変長の DNS データを格納する DNS クライアント クエリの例を次に示します。

```c
UINT     _nx_dns_domain_name_server_get(NX_DNS *dns_ptr, UCHAR  *host_name, 
                                        VOID *record_buffer, UINT buffer_size, 
                                        UINT *record_count, ULONG wait_option);
```

詳細については、第 3 章の DNS クライアント サービスの説明をご覧ください。

## <a name="dns-cache"></a>DNS キャッシュ

NX_DNS_CACHE_ENABLE が有効になっている場合、NetX DNS クライアントで DNS キャッシュ機能がサポートされます。 DNS クライアントの作成後、アプリケーションで *nx_dns_cache_initialize()* API を呼び出して、特別な DNS キャッシュを設定できます。 DNS キャッシュ機能を有効にすると、DNS クライアントは DNS クエリの送信を開始する前に、DNS キャッシュから使用可能な応答を検索します。使用可能な応答が見つかった場合は、その応答を直接アプリケーションに返します。それ以外の場合、DNS クライアントは DNS サーバーにクエリ メッセージを送信し、応答を待ちます。 DNS クライアントが応答メッセージを取得したときに使用可能な空きキャッシュがある場合、DNS クライアントはアプリケーションに応答を返し、その応答をリソース レコードとして DNS キャッシュにも追加します。

各応答は、キャッシュ内の *NX_DNS_RR* データ構造体 (リソース レコード) に格納されます。 レコード内の文字列 (リソース レコード名とデータ) は可変長であるため、NX_DNS_RR 構造体には格納されません。 レコードには、文字列が格納されている実際のメモリ位置へのポインターが含まれています。 文字列テーブルとレコードはキャッシュを共有します。 レコードはキャッシュの先頭から格納され、キャッシュの末尾に向かって増加していきます。 文字列テーブルはキャッシュの末尾から開始され、キャッシュの先頭に向かって拡大していきます。 文字列テーブル内の各文字列には、長さフィールドとカウンター フィールドがあります。 文字列が文字列テーブルに追加されたときに、同じ文字列が既にそのテーブルに存在する場合は、カウンター値が増分され、その文字列にはメモリが割り当てられません。 リソース レコードまたは新しい文字列をこれ以上キャッシュに追加できない場合、キャッシュはいっぱいであると見なされます。

## <a name="dns-client-limitations"></a>DNS クライアントの制限事項

DNS クライアントは、一度に 1 つの DNS 要求をサポートします。 別の DNS 要求を実行しようとしているスレッドは、前の DNS 要求が完了するまで一時的にブロックされます。

NetX DNS クライアントでは、権威のある応答からのデータを使用して他の DNS サーバーに追加の DNS クエリを転送することはありません。

## <a name="dns-rfcs"></a>DNS RFC

NetX DNS は次の RFC に準拠しています。

- RFC 1034 ドメイン名 - 概念と機能
- RFC 1035 ドメイン名 - 実装と仕様
- RFC 1480 US ドメイン
- RFC 2782 サービスの場所を指定するための DNS RR (DNS SRV)