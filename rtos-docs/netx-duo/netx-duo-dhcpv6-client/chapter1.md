---
title: 第 1 章 - Azure RTOS NetX Duo DHCPv6 クライアントの概要
description: IPv6 ネットワークでは、DHCPv6 サーバーからの動的なグローバル IP アドレスの割り当てに、DHCP ではなく DHCPv6 が使用され、ほとんどの同じ機能と、多くの拡張機能が提供されています。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3bf3b52c53bb26e2c9c2c736ae35817eb967f609
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810913"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-dhcpv6-client"></a>第 1 章 - Azure RTOS NetX Duo DHCPv6 クライアントの概要

IPv6 ネットワークでは、DHCPv6 サーバーからの動的なグローバル IP アドレスの割り当てに、DHCP ではなく DHCPv6 が使用され、ほとんどの同じ機能と、多くの拡張機能が提供されています。 このドキュメントでは、Azure RTOS NetX Duo DHCPv6 クライアント API を使用して IPv6 アドレスを取得する方法について詳しく説明します。

## <a name="dhcpv6-communication"></a>DHCPv6 の通信

DHCPv6 プロトコルでは UDP が使用されます。 DHCPv6 メッセージの交換のため、クライアントではポート 546 が使用され、サーバーではポート 547 が使用されます。 クライアントで使用可能な DHCPv6 サーバーへの DHCPv6 要求を開始するには、送信元アドレスとしてリンク ローカル アドレスが使用されます。 クライアントにより、ネットワーク上のすべての DHCPv6 サーバーを対象としたメッセージが送信されるときは、*All_DHCP_Relay_Agents_and_Servers* のマルチキャスト アドレス *FF02::01:02* が使用されます。 これは、予約されているリンク スコープのマルチキャスト アドレスです。

## <a name="dhcpv6-process-of-requesting-an-ipv6-address"></a>IPv6 アドレスを要求する DHCPv6 のプロセス

クライアントにより、グローバル IPv6 アドレスの割り当てを要求するプロセスが開始されるときは、最初に *nx_dhcpv6_send_solicit* サービスを使用して SOLICIT メッセージが送信されます。

**UINT nx_dhcpv6_request_solicit(NX_DHCPV6 \*dhcpv6_ptr)**

このメッセージは、*All_DHCP_Relay_Agents_and_Servers* のアドレスを使用してすべてのサーバーに送信されます。 SOLICIT 要求において、クライアントは、サーバーへのヒントとして、特定の IPv6 アドレスの割り当てを要求できます。 また、SOLICIT メッセージのオプション要求では、DNS サーバー、NTP サーバー、その他のオプションなど、他のネットワーク構成情報をサーバーに要求することもできます。

クライアントの要求に対応できる DHCPv6 サーバーは、クライアントに割り当てることができる IPv6 アドレス、IPv6 アドレスのリース時間、およびクライアントによって要求された追加情報が含まれる ADVERTISE メッセージで応答します。 DHCPv6 クライアント プロトコルの場合、クライアントは、ネットワーク上のすべての DHCPv6 サーバーから ADVERTISE メッセージを受信するまで、待機する必要があります。 各 ADVERTISE メッセージが有効なメッセージとして前処理され、さまざまな DHCPv6 パラメーターのオプション データがスキャンされます。 また、サーバーによって指定されている場合は、優先設定オプションの設定値も確認されます。 複数の ADVERTISE メッセージを受信した場合は、NetX DHCPv6 クライアントによって、待機期間の終了までに受信したサーバーの中で優先順位の値が最も高いものが選択されます。

ただし、優先順位の値が 255 の ADVERTISE メッセージをクライアントが受信した場合は例外です。 そのメッセージはすぐに受け入れられて、それ以降のすべての ADVERTISE メッセージは破棄されます。

待機時間は、DHCPv6 クライアントがどのサーバーからも応答を受信しない場合に、別の SOLICIT メッセージを送信する前に待機する再送信期間として定義されます。 SOLICIT 状態の最初の再送信タイムアウトは、DHCPv6 プロトコルに関する RFC 3315 の説明で 1 秒に定義されています。 DHCPv6 クライアントで有効なサーバー応答が受信されない場合、その後の再送信間隔は、最大 120 秒になるまで倍々に増えていきます。

サーバーが選択されると、クライアントにより、ADVERTISE メッセージからデータが抽出され、割り当てられたアドレス情報とリース時間を受け取るために、REQUEST メッセージがサーバーに送り返されます。 サーバーからは、クライアントの IPv6 アドレスがクライアントに割り当て済みとしてサーバーに登録されたことを確認する REPLY メッセージが応答されます。

DHCPv6 クライアントにより、割り当てられた IPv6 アドレスが IP インスタンス (NetX Duo など) に登録されます。 重複アドレス検出 (DAD) プロトコル用に構成されている場合 (既定で有効)、NetX Duo により Neighbor Solicit メッセージが自動的に送信され、割り当てられたアドレスがネットワーク上で一意であることが確認されます。 その場合、割り当てられた各アドレスが TENTATIVE から VALID に昇格されると、DHCPv6 クライアントに通知されます。 DHCPv6 クライアントは BOUND 状態に昇格され、デバイスはその IPv6 アドレスを使用してメッセージの送受信を行うことができます。 DAD プロトコルが失敗した場合は、NetX Duo から DHCPv6 クライアントに通知され、DHCPv6 クライアントにより、IPv6 アドレスの割り当てをサーバーに戻す DECLINE メッセージが送信されて、DHCPv6 クライアントの状態は INIT 状態にリセットされます。

### <a name="notification-of-successful-address-assignment-and-validation"></a>アドレスの割り当てと検証の成功通知

DHCPv6 クライアントに *nx_dhcpv6_client_create* サービスで状態変更コールバックが構成されている場合は、アプリケーションで、状態の変化から DHCPv6 クライアントによるアドレス要求の結果を判断できます。 サーバーから応答が返されない場合、観察された状態変化は SOLICIT から INIT です。 サーバーから応答を受信したが、サーバーでアドレスを割り当てられない場合は、DHCPv6 クライアントのサーバー エラー コールバックによって (*nx_dhcpv6_client_create* で構成されている場合)、アプリケーションに通知されます。 クライアントが BOUND 状態に達しても、DAD チェックで失敗した場合は、状態が BOUND から INIT に変更されます。 DAD が有効になっているアプリケーションでは、要求プロセス開始後に、DAD チェックの時間的余裕を設ける必要があることに注意してください。 通常、これは約 400 から 500 ティックです (ほとんどの場合、4 から 5 秒)。

### <a name="relinquishing-an-ipv6-address"></a>IPv6 アドレスの破棄

割り当てられた IPv6 アドレスをクライアントで解放する必要がある場合は、*nx_dhcpv6_request_release* サービスを呼び出して DHCPv6 サーバーに通知します。

### <a name="uint-nx_dhcpv6_request_releasenx_dhcpv6-dhcpv6_ptr"></a>UINT nx_dhcpv6_request_release(NX_DHCPV6 \*dhcpv6_ptr)

DHCPv6 クライアントにより、割り当てられたアドレスが含まれるユニキャスト RELEASE メッセージが、アドレスを割り当てたサーバーに送信され、メッセージの受信を確認するサーバーからの REPLY が待機されます。

注: 割り当てられた IPv6 アドレスを、電源を切ってから再起動時したときも引き続き使用することを計画しているクライアントには、異なるプロセスがあります。 電源を入れるときに新しいアドレスを要求しない場合、電源を切るときに RELEASE メッセージを送信しません。 この状況の説明については、「不揮発性メモリの要件」を参照してください。

### <a name="dhcpv6-lease-timeouts"></a>DHCPv6 リースのタイムアウト

サーバーによって割り当てられた IPv6 リースには、ID 関連付け – 非一時的アドレス (IANA) ブロックごとに、2 つのタイムアウト パラメーター T1 と T2 が含まれています。 IANA については、このユーザー ガイドの他の場所で説明されています。 割り当てられた IPv6 アドレスに DHCPv6 クライアントがバインドされてからの経過時間が T1 の場合、DHCPv6 クライアントにより、RENEW メッセージを送信することによって、IPv6 アドレスの更新が自動的に開始されます。 経過時間が T2 の場合、RENEW 要求への応答を受信していない場合は、DHCPv6 クライアントによって REBIND メッセージが自動的に送信されます。

他に 2 つの IPv6 リース パラメーター (優先および有効な有効期間) が、IANA ブロックに含まれる各 ID 関連付け (IA) ブロックに割り当てられます。 優先および有効な有効期間は、それぞれ、割り当てられた IPv6 アドレスが非推奨または無効になるまでの期間です。 T1 は、優先される有効期間より短くする必要があります。 T2 は、有効な有効期間より短くする必要があります。

### <a name="ip-thread-task-requirements"></a>IP スレッド タスクの要件

NetX Duo DHCPv6 クライアントでは、DHCPv6 クライアント サービスを使用する DHCPv6 クライアントを作成する前に、NetX Duo IP インスタンスを作成する必要があります。

DHCPv6 クライアントを使用する前に、IP インスタンスで UDP、IPv6、ICMPv6 を有効にする必要があります。

  - *nx_udp_enable*

  - *nxd_ipv6_enable*

  - *nxd_icmp_enable*

### <a name="packet-pool-requirements"></a>パケット プールの要件

NetX Duo DHCPv6 クライアントを作成するには、DHCPv6 メッセージを送信するために以前に作成したパケット プールが必要です。 パケット プールのサイズは、パケット ペイロードと使用可能なパケットの数に関してユーザーが構成可能であり、DHCPv6 メッセージとアプリケーションによる他の送信の予想される量によって異なります。

一般的な DHCPv6 メッセージは約 200 バイトであり、クライアントで必要な IA アドレスと DHCPv6 オプションの数に依存します。

### <a name="network-requirements"></a>ネットワークの要件

NetX Duo DHCPv6 クライアントでは、ポート 546 にバインドされた UDP ソケットを作成する必要があります。 ソケットは、DHCPv6 クライアント タスクが作成されるときに作成されます。

### <a name="non-volatile-memory-requirements"></a>不揮発性メモリの要件

DHCPv6 クライアントで、電源切断時に DHCPv6 サーバーとの IPv6 リースを解放し、再起動時に新しい IPv6 アドレスを要求する場合、不揮発性メモリ記憶域は必要ありません。 クライアントで割り当てられたリースを引き続き使用したい場合は、DHCPv6 クライアントに関する特定の情報を、再起動の間、不揮発性メモリに格納する必要があります。

不揮発性メモリの要件と DHCPv6 クライアント API については、第 2 章の「**NetX Duo DHCPv6 クライアントの使用**」で詳しく説明されています。

### <a name="netx-duo-dhcpv6-client-limitations"></a>NetX Duo DHCPv6 クライアントの制限事項

NetX Duo DHCPv6 クライアントの現在のリリースには、次の制限があります。

  - NetX Duo DHCPv6 クライアントでは、DHCPv6 サーバーにユニキャスト DHCPv6 メッセージを送信するためのサーバー ユニキャスト オプションが、サーバーで許可されている場合でも、サポートされていません。

  - NetX Duo DHCPv6 クライアントでは、サーバーによりネットワーク上のクライアントへの IPv6 アドレスの変更が開始される再構成要求は、サポートされていません。

  - NetX Duo DHCPv6 クライアントでは、DHCPv6 の一意識別子制御ブロックに対するエンタープライズ形式は、サポートされていません。 リンク レイヤーおよびリンクレイヤーと時間の形式のみがサポートされます。

  - NetX Duo DHCPv6 クライアントでは、一時的関連付け (TA) アドレス要求はサポートされていませんが、非一時的 (IANA) オプション要求はサポートされています。

## <a name="multihome-and-multiple-address-support"></a>マルチホームと複数アドレスのサポート

DHCPv6 クライアントでは、インターフェイスごとに複数のインターフェイスと複数のアドレスがサポートされています。 DHCPv6 クライアント サービスの *nx_dhcpv6_client_set_interface* を使用することにより、クライアント アプリケーションで、アプリケーションが DHCPv6 サーバーと通信するネットワーク インターフェイスを設定できます。 DHCPv6 クライアントは既定でプライマリ インターフェイス (インデックス 0) に設定されます。

インターフェイスごとに複数のアドレスを使用する場合、DHCPv6 クライアントによって、インデックス 0 から始まるアドレスの内部リストが保持されます。 DHCPv6 クライアントに登録されている同じアドレスでも、インターフェイス アドレスの IP テーブル内の同じインデックスに必ずしも存在しない場合があることに注意してください。

DHCPv6 クライアント サービスでクライアント IPv6 アドレス リースに関する情報を取得する場合、アドレス インデックスの指定が必要になる場合があります。 優先と有効の有効期間を取得する例を次に示します。

```C
UINT nx_dhcpv6_get_valid_ip_address_lease_time(NX_DHCPV6 *dhcpv6_ptr, 
                                              UINT address_index, 
                                              NXD_ADDRESS *ip_address,
                                              ULONG preferred_lifetime, 
                                              ULONG *valid_lifetime)
```

*nx_dhcpv6_get_valid_ip_address_count* サービスから割り当てられた有効な IPv6 アドレスの数を、クライアント アプリケーションで取得することもできます。

```C
UINT nx_dhcpv6_get_valid_ip_address_count(NX_DHCPV6 *dhcpv6_ptr, 
                                          UINT *address_count)
```

NetX Duo で複数のアドレスがサポートされるようになる前に作成された従来の DHCPv6 クライアント サービスは、アドレス インデックスを受け取りません。 そのため、このようなサービスの場合は、クライアントに割り当てられている IA アドレスの数に関係なく、要求されたデータはプライマリ グローバル IA アドレスから取得されます。 例を次に示します。

```C
UINT nx_dhcpv6_get_IP_address(NX_DHCPV6 *dhcpv6_ptr, 
                              NXD_ADDRESS *ip_address)
```

## <a name="netx-duo-dhcpv6-client-callback-functions"></a>NetX Duo DHCPv6 クライアントのコールバック関数

*nx_dhcpv6_state_change_callback*

DHCPv6 要求の処理の結果として、DHCPv6 クライアントが新しい DHCPv6 状態に変化すると、このコールバック関数によってアプリケーションに通知されます。

*nx_dhcpv6_server_error_handler*

DHCPv6 クライアントで、0 以外 (成功しなかった) の状態の "*状態*" オプションが含まれるサーバー応答が受信されると、サーバー エラー状態コードが含まれるこのコールバックによってアプリケーションに通知されます。

注: これらのコールバック関数は、DHCPv6 クライアント スレッド タスクから呼び出されるため、DHCPv6 クライアントのミューテックス制御を必要とする NetX Duo DHCPv6 クライアント サービス (*nx_dhcpv6_start、nx_dhcpv6_stop,* など) や、コールバックから直接メッセージを送信する API (*nx_dhcpv6_request_release* など) を、クライアント アプリケーションから呼び出すことはできません。

## <a name="dhcpv6-rfcs"></a>DHCPv6 の RFC

NetX Duo DHCP は、RFC3315、RFC3646、および関連する RFC に準拠しています。