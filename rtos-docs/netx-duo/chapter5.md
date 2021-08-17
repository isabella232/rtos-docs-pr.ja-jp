---
title: 第 5 章 - Azure RTOS NetX Duo のネットワーク ドライバー
description: この章では、Azure RTOS NetX Duo のネットワーク ドライバーについて説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a0d18929f33f15a342e8fb8b3d01d4ce934d6ec7dc287707f960adb36fb4f44b
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116788849"
---
# <a name="chapter-5---azure-rtos-netx-duo-network-drivers"></a>第 5 章 - Azure RTOS NetX Duo のネットワーク ドライバー

この章では、Azure RTOS NetX Duo のネットワーク ドライバーについて説明します。 開発者が特定のアプリケーション用に NetX Duo のネットワーク ドライバーを作成するのに役立つ情報を掲載しています。

## <a name="driver-introduction"></a>ドライバーの概要

NX_IP 構造体には、単一の IP インスタンスを管理するためのすべてが含まれています。 これには、一般的な TCP/IP プロトコル情報だけでなく、アプリケーション固有の物理ネットワーク ドライバーのエントリ ルーチンが含まれます。 ドライバーのエントリ ルーチンは ***nx_ip_create** サービス実行中に定義されます。 新しいデバイスを IP インスタンスに追加する場合は _ *_nx_ip_interface_attach_** サービスを使用します。

NetX Duo とアプリケーションのネットワーク ドライバーの通信は **NX_IP_DRIVER** 要求構造体を使用して行われます。 この構造体は、ほとんどの場合、呼び出し元のスタック上にローカルで定義されるため、ドライバーと呼び出し元の関数が返された後に解放されます。 構造体は、次のように定義されています。

```c
typedef struct NX_IP_DRIVER_STRUCT
{
      UINT           nx_ip_driver_command;
      UINT           nx_ip_driver_status;
      ULONG          nx_ip_driver_physical_address_msw;
      ULONG          nx_ip_driver_physical_address_lsw;
      NX_PACKET      *nx_ip_driver_packet;
      ULONG          *nx_ip_driver_return_ptr;
      NX_IP          *nx_ip_driver_ptr;
      NX_INTERFACE   *nx_ip_driver_interface;01
} NX_IP_DRIVER;
```
## <a name="driver-entry"></a>ドライバー エントリ 

NetX Duo では、ネットワーク ドライバー エントリ関数を呼び出すことで、ドライバーの初期化、パケットの送信、ネットワーク デバイスの初期化と有効化などのさまざまな制御や状態操作を行います。 NetX Duo では、_ *NX_IP_DRIVER** 要求構造体の ***nx_ip_driver_command** _ フィールドを設定することにより、ネットワーク ドライバーにコマンドを発行します。 ドライバー エントリ関数の形式は次のとおりです。

```c
VOID my_driver_entry(NX_IP_DRIVER *request);
```
## <a name="driver-requests"></a>ドライバー要求

NetX Duo は特定のコマンドでドライバー要求を作成し、そのコマンドを実行するためのドライバー エントリ関数を実行します。 各ネットワーク ドライバーには 1 つずつエントリ関数が用意されているので、NetX Duo では、あらゆる要求を行うのにドライバー要求データ構造体を使用します。 ドライバー要求データ構造体 ( _*NX_IP_DRIVER**) では ***nx_ip_driver_command** _ メンバーで要求を定義します。状態の情報は、**_nx_ip_driver_status_* メンバーに存在する呼び出し元に報告されます_。 このフィールドが _*NX_SUCCESS** になっている場合、ドライバー要求が完了したことを意味します。

NetX Duo では、ドライバーへのすべてのアクセスがシリアル化されます。 このため、ドライバーは、エントリ関数を呼び出している複数のスレッドを非同期に処理する必要がありません。 デバイス ドライバー関数は、IP ミューテックスがロックされた状態で実行されることに注意してください。 このため、デバイス ドライバーの内部関数が自身をブロックすることはできません。

通常、デバイス ドライバーは割り込みも処理します。 したがって、すべてのドライバー関数が、割り込みセーフである必要があります。

### <a name="driver-initialization"></a>ドライバーの初期化   
実際のドライバー初期化処理はアプリケーション固有ですが、通常、データ構造体と物理ハードウェアの初期化で構成されます。 ドライバー初期化のために NetX Duo で必要な情報は、IP 最大転送単位 (MTU。IPv4 または IPv6 ヘッダーを含めて IP 層のペイロードに使用できるバイト数) と、物理インターフェイスで論理から物理へのマッピングが必要かどうかという情報です。 ドライバーは ***nx_ip_interface_mtu_set*** を呼び出すことでインターフェイスの MTU を構成します。

デバイス ドライバーは ***nx_ip_interface_address_mapping_configure** _ を呼び出して、インターフェイスへのアドレスのマッピングが必要かどうかを NetX Duo に通知する必要があります。 アドレスのマッピングが必要な場合、ドライバーが有効な MAC アドレスを使用してインターフェイスを構成し、_*_nx_ip_interface_physical_address_set_** を通じてその MAC アドレスを NetX に渡します。

ネットワーク ドライバーは、NetX Duo から NX_LINK INITIALIZE 要求を受信するときに、上に示した NX_IP_DRIVER 要求制御ブロックの一部として IP 制御ブロックを指すポインターを受け取ります。

アプリケーションが ***nx_ip_create*** を呼び出した後、IP ヘルパー スレッドは、NX_LINK_INITIALIZE に設定されたコマンドを使用して、ドライバー要求をドライバーに送信し、その物理ネットワーク インターフェイスを初期化します。 次の NX_IP_DRIVER メンバーは、初期化要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー | 意味    |
| ------------------------- | ----------------------------- |
| nx_ip_driver_command   | NX_LINK_INITIALIZE    |
| nx_ip_driver_ptr       | IP インスタンスへのポインター。 この値は、ドライバー関数が操作対象の IP インスタンスを検出できるように、ドライバーが保存する必要があります。    |
| nx_ip_driver_interface | IP インスタンス内のネットワーク インターフェイス構造へのポインター。 この情報は、ドライバーが保存する必要があります。 パケットを受信するとき、ドライバーは、スタックへのパケット送信時のインターフェイス構造情報を使用する必要があります。 このデータ構造体の nx_interface_index メンバーを読み取ることでインターフェイス インデックス (デバイス インデックス) を取得できます。 |
| nx_ip_driver_status    | 完了状態。 IP インスタンスの指定されたインターフェイスをドライバーが初期化できない場合は、0 以外のエラー状態が返されます。 |


> [!NOTE]  
> *実際には IP インスタンス用に作成された IP ヘルパー スレッドからドライバーが呼び出されます。そのため、ドライバー ルーチンでのブロック操作の実行を避ける必要があります。そうしないと、IP ヘルパー スレッドが停止し、その IP スレッドを必要とするアプリケーションで無期限の遅延が生じるおそれがあります*。

### <a name="enable-link"></a>リンクを有効にする   
次に、IP ヘルパー スレッドは、ドライバー要求内でドライバー コマンドを NX_LINK_ENABLE に設定し、その要求をネットワーク ドライバーに要求を送信することで、物理ネットワークを有効にします。 これは、IP ヘルパー スレッドが初期化要求を完了した直後に行われます。 リンクは、インターフェイス インスタンスの *nx_interface_link_up* フィールドを設定するだけで有効にできる場合もあります。 物理ハードウェアの操作が必要になる場合もあります。 次の NX_IP_DRIVER メンバーは、リンクの有効化要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー       | 意味                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_ENABLE   |
| nx_ip_driver_ptr       | IP インスタンスへのポインター  |
| nx_ip_driver_interface | インターフェイス インスタンスへのポインター |
| nx_ip_driver_status    | 完了状態。 指定されたインターフェイスをドライバーが有効にできない場合は、0 以外のエラー状態が返されます。 |

### <a name="disable-link"></a>リンクを無効にする   
***nx_ip_delete** _ サービスで IP インスタンスを削除するときに NetX Duo によってこの要求が行われます。 または、アプリケーションが、電源を節約するためにリンクを一時的に無効にする目的で、このコマンドを実行する場合があります。 このサービスは、IP インスタンス上の物理ネットワーク インターフェイスを無効にします。 リンクを無効にする処理は、インターフェイス インスタンス内の "_nx_interface_link_up*" フラグをオフにするのと同じくらい簡単ですが、物理ハードウェアの操作が必要になる場合もあります。通常、これは "***リンクを有効にする**_" 操作と逆の操作になります。 リンクが無効になった後、アプリケーションは "_ *_リンクを有効にする_**" 操作を要求して、インターフェイスを有効にします。

次の NX_IP_DRIVER メンバーは、リンクの無効化要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー     | 意味                      |
| ------------------------- | ---------------------------- |
| nx_ip_driver_command   | NX_LINK_DISABLE    |
| nx_ip_driver_ptr       | IP インスタンスへのポインター   |
| nx_ip_driver_interface | インターフェイス インスタンスへのポインター   |
| nx_ip_driver_status    | 完了状態。 IP インスタンス内の指定されたインターフェイスをドライバーが無効にできない場合は、0 以外のエラー状態が返されます。 |

### <a name="uninitialize-link"></a>リンクを初期化前の状態に戻す   
***nx_ip_delete** _ サービスで IP インスタンスを削除するときに NetX Duo によってこの要求が行われます。 この要求によってインターフェイスが初期化前の状態に戻り、初期化フェーズ中に作成されたすべてのリソースが解放されます。 これは通常 _ *_Initialize Link_** 操作の逆操作です。 インターフェイスが初期化前の状態に戻されたら、デバイスは、インターフェイスが再度初期化されるまで使用できません。

次の NX_IP_DRIVER メンバーは、リンクの無効化要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー    | 意味                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_UNINITIALZE      |
| nx_ip_driver_ptr       | IP インスタンスへのポインター   |
| nx_ip_driver_interface | インターフェイス インスタンスへのポインター |
| nx_ip_driver_status    | 完了状態。 IP インスタンスの指定されたインターフェイスをドライバーが初期前の状態に戻せない場合は、0 以外のエラー状態が返されます。 |

### <a name="packet-send"></a>パケット送信   
この要求は、内部的に IPv4 または IPv6 送信処理を行うときに行われます。NetX Duo のすべてのプロトコルは、この処理によってパケットを送信します (ARP と RARP を除く)。 パケット送信コマンドを受信すると、*nx_packet_prepend_ptr* が送信するパケットの先頭、つまり IPv4 または IPv6 ヘッダーの先頭を指定します。 *nx_packet_length* は、転送されるデータの合計サイズ (バイト単位) を示します。 *Nx_packet_next* が有効な場合、発信 IP データグラムは複数のパケットに格納されるため、ドライバーは、チェーンされたパケットに従ってフレーム全体を送信する必要があります。 各チェーン パケットの有効なデータ領域は、*nx_packet_prepend_ptr* と *nx_packet_append_ptr* の間に格納されていることに注意してください。

ドライバーは、物理ヘッダーを構築する役割を担います。 IP アドレスへの物理アドレスのマッピングが必要な場合 (イーサネットなど)、IP レイヤーによって、既に MAC アドレスは解決されています。 送信先の MAC アドレスは、IP インスタンスから渡されて *nx_ip_driver_physical_address_msw と nx_ip_driver_physical_address_lsw* に保存されます。

物理ヘッダーを追加すると、パケット送信処理によってドライバーの出力関数が呼び出され、パケットが送信されます。

次の NX_IP_DRIVER メンバーは、パケット送信要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー              | 意味                               |
| -----------------------------------| --------------------------------------|
| nx_ip_driver_command            | NX_LINK_PACKET_SEND                |
| nx_ip_driver_ptr                | IP インスタンスへのポインター                |
| nx_ip_driver_packet             | 送信するパケットへのポインター         |
| nx_ip_driver_interface          | インターフェイス インスタンスへのポインター    |
| nx_ip_driver_physical_address_msw | 最上位 32 ビットの物理アドレス (物理マッピングが必要な場合のみ) |
| nx_ip_driver_physical_address_lsw | 最下位 32 ビットの物理アドレス (物理マッピングが必要な場合のみ) |
| nx_ip_driver_status             | 完了状態。 ドライバーがパケットを送信できない場合は、0 以外のエラー状態が返されます。 |

### <a name="packet-broadcastipv4-packets-only"></a>パケット ブロードキャスト (IPv4 パケットのみ)  
この要求は、送信パケット要求とほぼ同じです。 唯一の違いは、ブロードキャスト先の物理アドレス フィールドがイーサネットのブロードキャスト MAC アドレスに設定されていることです。 次の NX_IP_DRIVER メンバーは、パケット ブロードキャスト要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー                | 意味                                                                                                  |
|------------------------------------|----------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_PACKET_BROADCAST                                                                                 |
| nx_ip_driver_ptr                   | IP インスタンスへのポインター                                                                                   |
| nx_ip_driver_packet                | 送信するパケットへのポインター                                                                            |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (ブロードキャスト)                                                                                   |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (ブロードキャスト)                                                                                   |
| nx_ip_driver_interface             | インターフェイス インスタンスへのポインター                                                                       |
| nx_ip_driver_status                | 完了状態。 ドライバーがパケットを送信できない場合は、0 以外のエラー状態が返されます。 |

### <a name="arp-send"></a>ARP 送信  
この要求も、IP パケット送信要求に似ています。 唯一の違いは、イーサネット ヘッダーによって指定されるのが IP パケットではなく ARP パケットであること、そして送信先の物理アドレス フィールドが MAC ブロードキャスト アドレスに設定されていることです。 次の NX_IP_DRIVER メンバーは、ARP 送信要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー                | 意味                                                                                                      |
|------------------------------------|--------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_ARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | IP インスタンスへのポインター                                                                                       |
| nx_ip_driver_packet                | 送信するパケットへのポインター                                                                                |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (ブロードキャスト)                                                                                       |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (ブロードキャスト)                                                                                       |
| nx_ip_driver_interface             | インターフェイス インスタンスへのポインター                                                                           |
| nx_ip_driver_status                | 完了状態。 ドライバーが ARP パケットを送信できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *物理マッピングが必要ない場合、この要求の実装は必要ありません*。

*ARP は IPv6 で近隣探索プロトコルとルーター探索プロトコルに置き換えられましたが、イーサネット ネットワーク ドライバーには現在も IPv4 のピアおよびルーターとの互換性が必要です。そのため、現在でもドライバーで ARP パケットを処理する必要があります*。

### <a name="arp-response-send"></a>ARP 応答送信  
この要求は、ARP 送信パケット要求とほぼ同じです。 唯一の違いは、送信先の物理アドレス フィールドが IP インスタンスから渡されることです。 次の NX_IP_DRIVER メンバーは、ARP 応答送信要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー                  | 意味                                  |
| -------------------------------------- | -----------------------------------------|
| nx_ip_driver_command                | NX_LINK_ARP_RESPONSE_SEND            |
| nx_ip_driver_ptr                    | IP インスタンスへのポインター   |
| nx_ip_driver_packet                 | 送信するパケットへのポインター          |
| nx_ip_driver_physical_address_msw | 最上位 32 ビットの物理アドレス |
| nx_ip_driver_physical_address_lsw | 最下位 32 ビットの物理アドレス |
| nx_ip_driver_interface              | インターフェイス インスタンスへのポインター |
| nx_ip_driver_status                 | 完了状態。 ドライバーが ARP パケットを送信できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *物理マッピングが必要ない場合、この要求の実装は必要ありません*。

### <a name="rarp-send"></a>RARP 送信   
この要求は、ARP 送信パケット要求とほぼ同じです。 唯一の違いは、パケット ヘッダーの種類と、物理アドレス フィールドが不要であることです。これは、物理的な送信先が常にブロードキャスト アドレスであるためです。

次の NX_IP_DRIVER メンバーは、RARP 送信要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー                | 意味                                                                                                       |
|------------------------------------|---------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command               | NX_LINK_RARP_SEND                                                                                             |
| nx_ip_driver_ptr                   | IP インスタンスへのポインター                                                                                        |
| nx_ip_driver_packet                | 送信するパケットへのポインター                                                                                 |
| nx_ip_driver_physical_address_ms w | 0x0000FFFF (ブロードキャスト)                                                                                        |
| nx_ip_driver_physical_address_lsw  | 0xFFFFFFFF (ブロードキャスト)                                                                                        |
| nx_ip_driver_interface             | インターフェイス インスタンスへのポインター                                                                            |
| nx_ip_driver_status                | 完了状態。 ドライバーが RARP パケットを送信できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *RARP サービスが必要なアプリケーションではこのコマンドを実装する必要があります*。

### <a name="multicast-group-join"></a>マルチキャスト グループ参加   
この要求は、IPv4 では ***nx_igmp_multicast_interface join** _ および _*_nx_ipv4_multicast_interface_join_*_ サービス、IPv6 では _ *_nxd_ipv6_multicast_interface_join_** サービス、サービスおよび IPv6 で必要なさまざまな操作を使用して実行されます。 ネットワーク ドライバーは、指定されたマルチキャスト グループアドレスを受け取り、そのマルチキャスト グループ アドレスからの受信パケットを受け入れるように物理メディアを設定します。 ドライバーがマルチキャスト フィルターをサポートしていない場合は、ドライバー受信ロジックを、無作為検出モードにしなければならない可能性があります。 この場合、ドライバーが、送信先 MAC アドレスに基づいて、受信フレームをフィルター処理する必要が出てくることがあるため、IP インスタンスに渡されるトラフィック量が減少します。 次の NX_IP_DRIVER メンバーは、マルチキャスト グループ参加要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー                  | 意味                                 |
| -------------------------------------- | --------------------------------------- |
| nx_ip_driver_command                | NX_LINK_MULTICAST_JOIN               |
| nx_ip_driver_ptr                    | IP インスタンスへのポインター  |
| nx_ip_driver_physical_address_msw | 最上位 32 ビットの物理マルチキャスト アドレス |
| nx_ip_driver_physical_address_lsw | 最下位 32 ビットの物理マルチキャスト アドレス |
| nx_ip_driver_interface              | インターフェイス インスタンスへのポインター |
| nx_ip_driver_status                 | 完了状態。 ドライバーがマルチキャスト グループに参加できない場合は、0 以外のエラー状態が返されます。 |

> [!NOTE]  
> *アドレス構成などのために、IPv6 のアプリケーションでは、ICMPv6 ベースのプロトコル用のドライバーでマルチキャストを実装する必要があります。IPv4 のアプリケーションでは、マルチキャスト機能が必要ないのであれば、この要求を実装する必要はありません。*

> [!IMPORTANT]  
> *IPv6 が有効でなく、IPv4 でマルチキャスト機能が必要ない場合、この要求を実装する必要はありません*。

### <a name="multicast-group-leave"></a>マルチキャスト グループ脱退  
この要求を実行するには、***nx_igmp_multicast_interface_leave** _ サービス、IPv4 用の _*_nx_ipv4_multicast_interface_leave_*_ サービス、または IPv6 用の _ *_nxd_ipv6_multicast_interface_leave_** サービスを明示的に呼び出す方法と、IPv6 に必要なさまざまな NetX Duo 内部操作を使用する方法があります。 ドライバーは、指定されたイーサネット マルチキャスト アドレスをマルチキャスト リストから削除します。 ホストがマルチキャスト グループを脱退した後、この IP インスタンスは、このイーサネット マルチキャスト アドレスのネットワーク上のパケットを受信しなくなります。 次の NX_IP_DRIVER メンバーは、マルチキャスト グループ脱退要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー              | 意味                              |
| -----------------------------------| -------------------------------------|
| nx_ip_driver_command            | NX_LINK_MULTICAST_LEAVE           |
| nx_ip_driver_ptr                | IP インスタンスへのポインター   |
| nx_ip_driver_physical_address_msw | 物理マルチキャスト アドレスの最上位 32 ビット |
| nx_ip_driver_physical_address_lsw | 最下位 32 ビットの物理マルチキャスト アドレス |
| nx_ip_driver_interface              | インターフェイス インスタンスへのポインター |
| nx_ip_driver_status                 | 完了状態。 ドライバーがマルチキャスト グループを脱退できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *IPv4 でも IPv6 でも、マルチキャスト機能が必要ない場合この要求を実装する必要はありません*。

### <a name="attach-interface"></a>インターフェイスをアタッチする  
この要求は NetX Duo からデバイス ドライバーに対して行われます。この要求によりドライバーは、ドライバー インスタンスを、対応する IP インスタンスおよびその IP 内の物理インターフェイス インスタンスに関連付けることができます。 次の NX_IP_DRIVER メンバーは、インターフェイスのアタッチ要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー    | 意味                  |
|------------------------|--------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_ATTACH |
| nx_ip_driver_ptr       | IP インスタンスへのポインター   |
| nx_ip_driver_interface | インターフェイス インスタンスへのポインター|
| nx_ip_driver_status    | 完了状態。 IP インスタンスの指定されたインターフェイスをドライバーがデタッチできない場合は、0 以外のエラー状態が返されます。 |

### <a name="detach-interface"></a>インターフェイスをデタッチする    
この要求は NetX Duo からデバイス ドライバーに対して行われます。この要求によりドライバーは、ドライバー インスタンスと、対応する IP インスタンスおよびその IP 内の物理インターフェイス インスタンスとの関連付けを解除できます。 次の NX_IP_DRIVER メンバーは、インターフェイスのアタッチ要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー    | 意味                                                                                                                                    |
|------------------------|--------------------------------------------------------------------------------------------------------------------------------------------|
| nx_ip_driver_command   | NX_LINK_INTERFACE_DETACH                                                                                                                   |
| nx_ip_driver_ptr       | IP インスタンスへのポインター                                                                                                                     |
| nx_ip_driver_interface | インターフェイス インスタンスへのポインター                                                                                                         |
| nx_ip_driver_status    | 完了状態。 IP インスタンスの指定されたインターフェイスをドライバーがアタッチできない場合は、0 以外のエラー状態が返されます。 |

### <a name="get-link-status"></a>リンクの状態を取得する    
アプリケーションは NetX Duo の ***nx_ip_interface_status_check*** サービスを使用して、ホスト上のあらゆるインターフェイスのリンクの状態を問い合わせることができます。 これらのサービスの詳細は、第 4 章、149 ページ「NetX Duo サービスの説明」をご覧ください。

リンクの状態は *nx_ip_driver_interface* ポインターが指す NX_INTERFACE 構造体内の *nx_interface_link_up* フィールド内に含まれています。 次の NX_IP_DRIVER メンバーは、リンク状態要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー       | 意味                  |
| --------------------------- | -------------------------|
| nx_ip_driver_command     | NX_LINK_GET_STATUS    |
| nx_ip_driver_ptr         | IP インスタンスへのポインター   |
| nx_ip_driver_return_ptr | 状態の配置先へのポインター。 |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター   |
| nx_ip_driver_status      | 完了状態。 ドライバーが特定の状態を取得できない場合は、0 以外のエラー状態が返されます。 |

> [!NOTE]  
> ***nx_ip_status_check** _ は現在でもプライマリ インターフェイスの状態の確認に使用できます。 ですが、アプリケーション開発者は、インターフェイスごとに確認ができる _ *_nx_ip_interface_status_check_** サービスを使用することを推奨します。

### <a name="get-link-speed"></a>リンクの速度を取得する  
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 リンクの回線速度は、指定された宛先内にドライバーによって格納されます。 次の NX_IP_DRIVER メンバーは、リンク回線速度要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー   | 意味                   |
| ------------------------| ------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_SPEED          |
| nx_ip_driver_ptr         | IP インスタンスへのポインター                                                                                         |
| nx_ip_driver_return_ptr | 回線速度の配置先へのポインター                                                             |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター                                                                              |
| nx_ip_driver_status      | 完了状態。 ドライバーが速度情報を取得できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="get-duplex-type"></a>二重タイプを取得する   
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 リンクの二重タイプは、指定された宛先内にドライバーによって格納されます。 次の NX_IP_DRIVER メンバーは、二重タイプ要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー   | 意味                                                                                                    |
| --------------------------- | -------------------------------------------------------------------------------------------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_DUPLEX_TYPE                                                                                    |
| nx_ip_driver_ptr         | IP インスタンスへのポインター                                                                                         |
| nx_ip_driver_return_ptr | 二重タイプの配置先へのポインター                                                            |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター                                                                              |
| nx_ip_driver_status      | 完了状態。 ドライバーが二重情報を取得できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="get-error-count"></a>エラー数を取得する   
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 リンクのエラー数は、指定された宛先内にドライバーによって格納されます。 この機能をサポートするために、ドライバーは操作エラーを追跡する必要があります。 次の NX_IP_DRIVER メンバーは、リンク エラー数要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー   | 意味                   |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_ERROR_COUNT   |
| nx_ip_driver_ptr         | IP インスタンスへのポインター   |
| nx_ip_driver_return_ptr | エラー数の配置先へのポインター |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター|
| nx_ip_driver_status      | 完了状態。 ドライバーがエラー数を取得できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="get-receive-packet-count"></a>受信パケット数を取得する    
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 リンクの受信パケット数は、指定された宛先内にドライバーによって格納されます。 この機能をサポートするために、ドライバーは受信パケット数を追跡する必要があります。 次の NX_IP_DRIVER メンバーは、リンクの受信パケット数要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー       | 意味                        |
| --------------------------- | -------------------------------|
| nx_ip_driver_command     | NX_LINK_GET_RX_COUNT      |
| nx_ip_driver_ptr         | IP インスタンスへのポインター  |
| nx_ip_driver_return_ptr | 受信パケット数の配置先へのポインター   |
| nx_ip_driver_interface   | 物理ネットワーク インターフェイスへのポインター  |
| nx_ip_driver_status      | 完了状態。 ドライバーが受信数を取得できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="get-transmit-packet-count"></a>送信パケット数を取得する   
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 リンクの送信パケット数は、指定された宛先内にドライバーによって格納されます。 この機能をサポートするために、ドライバーは、各インターフェイス上で送信する各パケットを追跡する必要があります。 リンクの送信パケット数要求には、次の NX_IP_DRIVER メンバーを使用します。

| NX_IP_DRIVER&nbsp; メンバー   | 意味                   |
| ----------------------- | ------------------------- |
| nx_ip_driver_command | NX_LINK_GET_TX_COUNT  |
| nx_ip_driver_ptr     | IP インスタンスへのポインター    |
| nx_ip_driver_return_ptr | 送信パケット数の配置先へのポインター  |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター   |
| nx_ip_driver_status      | 完了状態。 ドライバーが送信数を取得できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="get-allocation-errors"></a>割り当てエラーを取得する   
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 リンクのパケット プール割り当てエラー数は、指定された宛先内にドライバーによって格納されます。 次の NX_IP_DRIVER メンバーは、リンクの割り当てエラー数要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー       | 意味                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_GET_ALLOC_ERRORS  |
| nx_ip_driver_ptr         | IP インスタンスへのポインター     |
| nx_ip_driver_return_ptr | 割り当てエラー数の配置先へのポインター  |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター  |
| nx_ip_driver_status      | 完了状態。 ドライバーが割り当てエラーを取得できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT]  
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="driver-deferred-processing"></a>ドライバー遅延処理    
この要求は、送信または受信 ISR による _***nx_ip_driver_deferred_processing**_ ルーチンのドライバー呼び出しに対する応答として、IP ヘルパー スレッドから送信されます。 これにより、ドライバー ISR はパケットの受信および送信処理を IP ヘルパー スレッドに任せて、ISR 内の処理量を減らすことができます。 *nx_ip_driver_interface* が指し示す NX_INTERFACE 構造体の _nx_interface_additional_link_info* フィールドは、IP ヘルパー スレッド コンテキストの遅延処理イベントに関する情報を保存するために、ドライバーで使用する場合があります。 遅延処理イベントには、次の NX_IP_DRIVER メンバーを使用します。

| NX_IP_DRIVER&nbsp; メンバー     | 意味                           |
| ------------------------- | --------------------------------- |
| nx_ip_driver_command   | NX_LINK_DEFERRED_PROCESSING    |
| nx_ip_driver_ptr       | IP インスタンスへのポインター            |
| nx_ip_driver_interface | インターフェイス インスタンスへのポインター |

### <a name="set-physical-address"></a>物理アドレス設定  
この要求は ***nx_ip_interface_physical_address_set** _ サービスの内部から送信されます。 このサービスにより、アプリケーションの実行中にインターフェイスの物理アドレスを変更できます。 このコマンドを受け取ったドライバーは、ネットワーク インターフェイスのハードウェア アドレスを指定された物理アドレスに再構成する必要があります。 IP インスタンスには既に新しいアドレスが存在するため、このコマンドで _ *_nx_ip_interface_address_set_** サービスを呼び出す必要はありません。

次の NX_IP_DRIVER メンバーは、ユーザー コマンド要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー      | 意味                      |
| -------------------------- | ---------------------------- |
| nx_ip_driver_command    | NX_LINK_SET_PHYSICAL_ADDRESS  |
| nx_ip_driver_ptr        | IP インスタンスへのポインター  |
| nx_ip_driver_interface  | インターフェイス インスタンスへのポインター   |
| nx_ip_driver_physical_ad dress_msw | 新しい物理アドレスの最上位 32 ビット  |
| nx_ip_driver_physical_ad dress_lsw | 新しい物理アドレスの最下位 32 ビット  |
| nx_ip_driver_status                  | 完了状態。 ドライバーで物理アドレスを再構成できない場合、0 以外のエラー ステータスが返されます。 |

### <a name="user-commands"></a>ユーザー コマンド    
この要求は、***nx_ip_driver_direct_command*** サービス内から行われます。 ドライバーは、アプリケーション固有のユーザーコマンドを処理します。 次の NX_IP_DRIVER メンバーは、ユーザー コマンド要求に使用されます。

| NX_IP_DRIVER&nbsp; メンバー       | 意味                       |
| --------------------------- | ----------------------------- |
| nx_ip_driver_command     | NX_LINK_USER_COMMAND       |
| nx_ip_driver_ptr         | IP インスタンスへのポインター        |
| nx_ip_driver_return_ptr | ユーザー定義       |
| nx_ip_driver_interface   | インターフェイス インスタンスへのポインター    |
| nx_ip_driver_status      | 完了状態。 ドライバーがユーザー コマンドを実行できない場合は、0 以外のエラー状態が返されます。 |

> [!IMPORTANT] 
> *この要求は NetX Duo 内では使用しないため実装は任意です*。

### <a name="unimplemented-commands"></a>実装されていないコマンド  
ネットワーク ドライバーによって実装されていないコマンドのリターン状態フィールドは、NX_UNHANDLED_COMMAND に設定する必要があります。

## <a name="driver-capability"></a>ドライバーの機能

一部のネットワーク インターフェイスはチェックサム オフロード機能を備えています。 デバイス ドライバーは、ハードウェア アクセラレータを利用して、さまざまなチェックサムの計算にかかる CPU 時間をなくします。

ハードウェアでサポートされるハードウェア チェックサムの程度に応じて、ハードウェアのどの機能が有効であるかを、デバイス ドライバーから IP インスタンスに通知する必要があります。 これにより、IP インスタンスはハードウェア機能を認識し、できる限り多くの計算をハードウェアに任せます。 ドライバーでは ***nx_ip_interface_capability_set*** API を使用して、物理インターフェイスで処理できるすべての機能を設定する必要があります。

次の機能を使用できます:

- NX_INTERFACE_CAPABILITY_IPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_TCP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_UDP_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV4_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_ICMPV6_RX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_TX_CHECKSUM
- NX_INTERFACE_CAPABILITY_IGMP_RX_CHECKSUM

ハードウェアで実行できるチェックサム計算については、ドライバーでハードウェア記述子またはバッファー記述子を正しく設定し、ハードウェアで送信パケットのチェックサムを生成してヘッダーに埋め込めるようにする必要があります。 パケットを受信したときに、ハードウェアのチェックサム ロジックでチェックサム値を検証できる必要があります。 チェックサムの値が間違っている場合は受信したフレームを破棄します。

ハードウェアでチェックサムを計算する機能がある場合も、IP インスタンスのチェックサム機能は維持されます。 たとえば IPsec で保護された UDP データグラムを送信する場合など、特定の状況では、UDP チェックサムをソフトウェアで計算してから UDP フレームをスタック下部へ送る必要があります。 ほとんどのハードウェア チェックサム機能では、IPsec で保護されたデータセグメントのチェックサム計算をサポートしていません。 UDP または ICMP フレームのフラグメント化が必要な場合、UDP または ICMP チェックサムをソフトウェアで計算する必要があります。 ほとんどのハードウェア チェックサム ロジックは、データを複数のフレームに分割する処理に対応できません。

## <a name="driver-output"></a>ドライバーの出力  

前述のすべてのパケット送信要求には、ドライバー内で実装された出力関数が必要です。 特別な送信ロジックはハードウェア固有ですが、通常は、パケットを直ちに送信できるハードウェア容量を確認することで構成されます。 できる場合、パケットのペイロード (および一続きになったパケット中に存在する追加ペイロード) が 1 つまたは複数のハードウェア送信バッファーに読み込まれ、送信操作が開始されます。 使用可能な送信バッファーに収まらないパケットは、キューに登録され、送信バッファーが使用可能になったときに送信されます。

送信キューには、先頭と末尾にポインターがある単方向リストを推奨します。 新しいパケットがキューの最後に追加され、最も古いパケットが先頭で保持されます。 *nx_packet_queue_next* フィールドは、キュー内のパケットの次のリンクとして使用されます。 送信キューの先頭および末尾のポインターをドライバーで指定します。

> [!CAUTION]  
> *このキューはドライバーのスレッドと割り込み部分からアクセスを受けるため、キューの操作を割り込みから保護する必要があります*。

物理ハードウェア実装のほとんどによって、パケット送信の完了時に割り込みが発生します。 ドライバーは、このような割り込みを受け取ると、通常は、送信中のパケットに関連付けられているリソースを解放します。 送信ロジックが NX_PACKET バッファーから直接データを読み取る場合、ドライバーは、 ***nx_packet_transmit_release*** サービスを使用して、送信完了割り込みに関連付けられているパケットを解放し、使用可能なパケット プールに戻します。 次に、ドライバーは、送信キューに、送信待ちの追加パケットがないかどうかを調べます。 キュー登録された送信パケットのうち、ハードウェア送信バッファーに適合するものが、キューから取り出され、バッファーに読み込まれます。 その後、別の送信操作が開始されます。

NX_PACKET のデータを送信 FIFO に移すとすぐに (ドライバーでゼロ コピー操作がサポートされている場合は、NX_PACKET のデータが送信されるとすぐに)、ドライバーによって *nx_packet_prepend_ptr* が IP ヘッダーの先頭に配置し、それから ***nx_packet_transmit_release** を呼び出す必要があります。それに合わせて _nx_packet_length* フィールドを調整することを忘れないでください。 IP フレームが複数のパケットで構成されている場合は、パケット チェーンの先頭のみを解放する必要があります。

## <a name="driver-input"></a>ドライバーの入力

受信パケット割り込みを受けると、ネットワーク ドライバーは物理ハードウェアの受信バッファーからパケットを取得し、有効な NetX Duo パケットを構築します。 受信パケットのサイズがパケットのペイロード 1 つ分よりも大きい場合、有効な NetX Duo パケットを構築するには、長さフィールドを適切に設定して複数のパケットを連結する必要があります。 正しく構築すると *prepend_ptr* が物理層ヘッダーの後ろに置かれ、受信パケットが NetX Duo に配置されます。

NetX Duo では、IP (IPv4 および IPv6) ヘッダーと ARP ヘッダーが **ULONG** 型の境界にアラインしてあることを前提にしています。 そのため、NetX Duo のドライバーは、アライメントがこの方法で行われるようにする必要があります。 イーサネット環境内でこの処理を実行するには、パケットの先頭から 2 バイトのところでイーサネット ヘッダーを開始します。 *nx_packet_prepend_ptr* がイーサネット ヘッダーの先に移されると、下層の IP ヘッダー (IPv4 と IPv6) または ARP ヘッダーが 4 バイトでアラインされます。

> [!WARNING] 
> *IPv6 と IPv6 イーサネット ヘッダーの重要な違いは、下の「イーサネット ヘッダー」セクションをご覧ください*。

NetX Duo ではいくつかの受信パケット関数を使用できます。 受信パケットが ARP パケットの場合は、 _***nx_arp_packet_deferred_receive**_ が呼び出されます。 受信パケットが RARP パケットの場合は、_*_nx_arp_packet_deferred_receive_*_ が呼び出されます。 受信 IP パケットの処理オプションは複数あり、 IP パケットを最速で処理する場合は、_ _*_nx_ip_packet_receive_*_ が呼び出されます。 この方法の場合、オーバーヘッドは最も少なくて済みますが、ドライバーの受信割り込みサービス ハンドラー (ISR) 内で必要な処理が増えます。 最小 ISR 処理の場合は、__ *_nx_ip_packet_deferred_receive_** が呼び出されます。

新しい受信パケットが適切に構築された後、物理ハードウェアの受信バッファーは、さらに多くのデータを受信するように設定されます。 そのためには、ハードウェアの受信バッファーに NetX Duo パケットを割り振ってペイロードのアドレスを指定するか、または単純にハードウェアの受信バッファーの設定を変更する必要があります。 オーバーランの可能性を最小限に抑えるために重要なのは、パケットを受信した後、ハードウェアの受信バッファーにできるだけ早く使用可能なバッファーを確保することです。

> [!IMPORTANT] 
> *初期受信バッファーはドライバーの初期化中に用意されます*。

### <a name="deferred-receive-packet-handling"></a>遅延受信パケット処理  
ドライバーは、NetX Duo の IP ヘルパー スレッドの受信パケット処理を遅延させる場合があります。 一部のアプリケーションについては、これは ISR の処理とパケット破棄を最小限に抑えるうえで必要な場合があります。 

遅延パケット処理を行うには、***NX_DRIVER_DEFERRED_PROCESSING** _ を定義した上で、最初に NetX Duo ライブラリをコンパイルする必要があります。 これで、遅延パケット ロジックを NetX Duo IP ヘルパー スレッドに追加できます。 次に、データ パケットの受信時に、ドライバーが __nx_ip_packet_deferred_receive()* を呼び出す必要があります。

```c
_nx_ip_packet_deferred_receive(ip_ptr, packet_ptr);
```
遅延受信関数により、*packet_ptr* によって表される受信パケットが FIFO (リンクリスト) 上に配置され、IP ヘルパー スレッドに通知されます。 実行後、IP ヘルパーは遅延処理関数を繰り返し呼び出して、遅延パケットを処理します。 遅延ハンドラーの処理では通常、パケットの物理層ヘッダー (通常はイーサネット) を削除し、次の NetX Duo の受信関数のどれかにこのパケットを渡します:

- ***_nx_ip_packet_receive***
- ***_nx_arp_packet_deferred_receive***
- ***_nx_rarp_packet_deferred_receive***

## <a name="ethernet-headers"></a>イーサネット ヘッダー 

イーサネット ヘッダーに関する IPv6 と IPv4 の特に重要な違いの 1 つは、フレームの種類の設定です。 パケットを送信するときは、イーサネット ドライバーにより、送信パケットにイーサネット フレームの種類を設定します。 IPv6 パケットではフレームの種類を 0x86DD に、IPv4 パケットでは 0x0800 にします。

次に示すコードの抜粋で、この処理を例示します:

```c
NX_PACKET *packet_ptr;
packet_ptr = driver_req_ptr -> nx_ip_driver_packet;
if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V4)
{

   /* Set Ethernet frame type to IPv4 /*
   ethernet_frame_ptr -> frame_type = 0x0800;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else if (packet_ptr -> nx_packet_ip_version == NX_IP_VERSION_V6)
{

   /* Set Ethernet frame type to IPv6. /*
   ethernet_frame_ptr -> frame_type = 0x86DD;

   /* Swap endian-ness for little endian targets.*/
   NX_CHANGE_USHORT_ENDIAN(ethernet_frame_ptr -> frame_type);
}
else
{

   /* Unknown IP version. Free the packet we will not send. */
   nx_packet_transmit_release(packet_ptr);
}
```
同様に、受信パケットでは、イーサネット ドライバーにより、イーサネット フレームの種類からパケットの種類を判断します。 フレームの種類として IPv6 (0x86DD)、IPv4 (0x0800)、ARP (0x0806)、RARP (0x8035) を受け入れるように実装する必要があります。

## <a name="example-ram-ethernet-network-driver"></a>RAM イーサネット ネットワーク ドライバーの例

NetX Duo のデモ システムは、RAM ベースの簡単なネットワーク ドライバーと合わせて配布しています。このドライバーは ***nx_ram_network_driver.c*** に定義されています。 このドライバーは、IP インスタンスがすべて同じネットワーク上にあることを前提としており、仮想ハードウェア アドレス (MAC アドレス) を、各デバイス インスタンスに作成時に割り当てるだけです。 このファイルは、NetX Duo の物理ネットワーク ドライバーの基本構造の分かりやすい例になっています。 ユーザーは、この例に示されているドライバー フレームワークを使用して、独自のネットワーク ドライバーを開発できます。

ネットワーク ドライバーのエントリ関数は * **_nx_ram_network_driver()** であり、IP インスタンス作成呼び出しに渡されます。 追加のネットワーク インターフェイスのエントリ関数は _nx_ip_interface_attach()* サービスに渡すことができます。 IP インスタンスが立ち上がった後、ドライバー エントリ関数を実行し、デバイスを初期化、有効化します (**NX_LINK_INITIALIZE** と **NX_LINK_ENABLE** の事例を参考にしてください)。 **NX_LINK_ENABLE** コマンドの実行後は、デバイスをパケットの送受信が可能な状態にしておきます。 

IP インスタンスは、次のいずれかのコマンドを使用してネットワーク パケットを転送します。

| command                         |  説明                                                   |
| ------------------------------- | -------------------------------------------------------------- |
| ***NX_LINK_PACKET_SEND***    | IPv4 または IPv6 パケットを送信しています、                   |
| ***NX_LINK_ARP_SEND***       | ARP 要求または ARP 応答パケットが送信されています。    |
| ***NX_LINK_ARP_RARP_SEND*** | リバース ARP 要求または応答パケットが送信されています。 |

これらのコマンドの処理中、ネットワーク ドライバーは、適切なイーサネット フレーム ヘッダーを付加してから、基になるハードウェアに送信して、転送する必要があります。 転送処理中、ネットワーク ドライバーには、パケット バッファー領域の排他的な所有権があります。 そのため、データを送信したら (またはデータをドライバー内部の転送バッファーにコピーしたら)、ネットワーク ドライバーによってパケット バッファーを開放します。その際、先頭に付加したパケット バッファーをイーサネット ヘッダーの先にある IP ヘッダーに移動してから (パケットの長さもそれに合わせて調整します)、***nx_packet_transmit_release()*** サービスを呼び出してパケットを解放します。 データ転送後にパケットを解放しないと、パケットがリークします。

ネットワーク デバイス ドライバーは、受信データ パケットの処理も実行します。 RAM ドライバーの例では ***_nx_ram_network_driver_receive()*** 関数で受信パケットを処理します。 デバイスにイーサネット フレームを受信したときは、このドライバーによって NX_PACKET 構造体にそのデータを保存します。 NetX Duo では、4 バイトでアラインされた位置から IP ヘッダーが始まることを前提にしています。 イーサネット ヘッダーの長さは 14 バイトなので、ドライバーは、2 バイトでアラインされた位置に先頭が来るようにイーサネット ヘッダーを配置し、4 バイトでアラインされた位置から IP ヘッダーが始まることを保証する必要があります。