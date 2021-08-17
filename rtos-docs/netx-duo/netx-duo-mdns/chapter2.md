---
title: 第 2 章 - mDNS のインストールと使用
description: この章では、NetX Duo mDNS モジュールのインストール、設定、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 07/09/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: b27671f82c100db4e6a70a568e8a68f14b3ab45e3a33f46dd1f2e1852010f500
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796431"
---
# <a name="chapter-2---installation-and-use-of-mdns"></a>第 2 章 - mDNS のインストールと使用

この章では、NetX Duo mDNS モジュールのインストール、設定、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品ディストリビューション

NetX Duo mDNS は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 このパッケージには、次のように、2 つのソース ファイルと、このドキュメントを含む PDF ファイルが含まれています。

- **nxd_mdns.h**: NetX Duo mDNS モジュールのヘッダー ファイル
- **nxd_mdns.c**: NetX Duo mDNS モジュールの C ソース ファイル
- **nxd_mdns.pdf**: NetX Duo 用 mDNS を説明する PDF
- **demo_netxduo_mdns.c**: mDNS に用意されているサービスを説明する簡単なデモンストレーション プログラム。

## <a name="netx-duo-mdns-installation"></a>NetX Duo mDNS のインストール

NetX Duo mDNS API シリーズを使用するには、前述のディストリビューション全体を、NetX Duo がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX Duo が "*c:\netxduo*" ディレクトリにインストールされている場合は、*nxd_mdns.h* と *nxd_mdns.c* をこのディレクトリにコピーする必要があります。

## <a name="using-netx-duo-mdns"></a>NetX Duo mDNS の使用

NetX Duo mDNS モジュールは簡単に使用できます。 基本的には、ThreadX と NetX Duo を使用するために、アプリケーション コードにそれぞれ *tx_api.h* と *nx_api.h* をインクルードした後に、*nxd_mdns.h* をインクルードする必要があります。 このビルド プロジェクトには、mDNS ソース コードとアプリケーション ファイルのほか、ThreadX および NetX ライブラリ ファイルを含める必要があります。 NetX Duo mDNS を使用するために必要なのはこれだけです。

## <a name="configuration-options"></a>構成オプション

NetX Duo mDNS モジュールを構築するための構成オプションはいくつかあります。 既定値が記載されていますが、各定義は、指定された NetX Duo mDNS ヘッダー ファイルをインクルードする前にアプリケーションによって設定できます。 次の一覧では、それぞれについて詳しく説明しています。

- **NX_MDNS_DISABLE_SERVER**: mDNS または DNS-SD サーバー機能を無効にします。 サーバー機能がない場合、mDNS または DNS-SD モジュールは、ローカル ホストが提供するサービスをアナウンスせず、mDNS 照会にも応答しません。 このシンボルは、既定では定義されていません。
- **NX_MDNS_DISABLE_CLIENT**: mDNS または DNS-SD クライアント機能を無効にします。 クライアント機能がない場合、mDNS または DNS-SD は、クエリを送信せず、ネットワーク経由で受信した mDNS クエリ応答も保持しません。
- **NX_MDNS_ENABLE_ADDRESS_CHECK**: 定義済み。mDNS モジュールは、受信した mDNS メッセージに含まれるアドレス (送信元アドレス、送信先アドレス、ポート番号) を検証します。 このシンボルは、既定で定義されています。
- **NX_MDNS_ENABLE_CLIENT_POOF**: 定義済み。mDNS モジュールは、障害のパッシブ監視を実行し、mDNS または DNS_SD クライアント (クエリ送信元) は、ネットワーク上の他のホストが発行したマルチキャスト クエリを監視します。 このシンボルは、既定で定義されています。
- **NX_MDNS_ENABLE_SERVER_NEGATIVE_RESPONSES**: 定義済み。mDNS または DNS-SD サーバー (レスポンダー) は、正当な所有権のあるクエリに対して否定応答を生成します。 このシンボルは、既定で定義されています。
- **NX_MDNS_ENABLE_IPV6**: 定義済み。mDNS または DNS-SD は、IPv6 アドレス経由で mDNS メッセージを送信または処理します。 このシンボルは、既定では定義されていません。
- **NX_MDNS_IPV6_ADDRESS_COUNT**: ホストの IPv6 アドレスの最大数。 既定値は 2 です。
- **NX_MDNS_HOST_NAME_MAX**: ホスト名の文字列の最大サイズ。 既定値は 64 です。 NULL 終端記号は含めないでください。
- **NX_MDNS_SERVICE_NAME_MAX**: サービス名の文字列の最大サイズ。 既定値は 64 です。 NULL 終端記号は含めないでください。
- **NX_MDNS_DOMAIN_NAME_MAX**: ドメイン名の文字列の最大サイズ。 既定値は 16 です。 NULL 終端記号は含めないでください。
- **NX_MDNS_CONFLICT_COUNT**: ホスト名またはサービス名の競合の最大数。 既定値は 8 です。
- **NX_MDNS_RR_TTL_HOST**: ホスト名を含むリソース レコードの TTL 値 (秒単位)。 既定値は 120 (120 秒) です。
- **NX_MDNS_RR_TTL_OTHER**: 他のリソース レコードの TTL 値 (秒単位)。 既定値は 4,500 (75 分) です。
- **NX_MDNS_PROBING_TIMER_COUNT**: mDNS のプローブ メッセージ間の時間間隔 (ティック数)。 既定値は 25 ティック (250 ミリ秒) です。
- **NX_MDNS_ANNOUNCING_TIMER_COUNT**: mDNS のアナウンス メッセージ間の時間間隔 (ティック数)。 既定値は 25 ティック (250 ミリ秒) です。
- **NX_MDNS_GOODBYE_TIMER_COUNT**: 繰り返される "goodbye" メッセージ間の時間間隔 (ティック数)。 既定値は 25 ティック (250 ミリ秒) です。
- **NX_MDNS_QUERY_MIN_TIMER_COUNT**: 2 件のクエリ間の最小時間間隔 (ティック数)。 既定値は 100 ティック (1 秒) です。
- **NX_MDNS_QUERY_MAX_TIMER_COUNT**: 2 件のクエリ間の最大時間間隔 (ティック数)。 既定値は 360,000 (60 秒) です。
- **NX_MDNS_QUERY_DELAY_MIN**: 最初のクエリを送信する際の最小待ち時間 (ティック数)。 既定値は 2 ティック (20 ミリ秒) です。
- **NX_MDNS_QUERY_DELAY_RANGE**: 最初のクエリを送信する際の遅延時間の範囲 (ティック数)。 既定値は 10 ティック (100 ミリ秒) です。
- **NX_MDNS_RESPONSE_INTERVAL**: レコードが最後にマルチキャストされてから少なくとも 1 秒の間隔を確保するために、クエリに応答する際の時間間隔 (ティック数)。 既定値は 100 ティックです。
- **NX_MDNS_RESPONSE_PROBING_TIMER_OUT**: レコードが最後にマルチキャストされてから少なくとも 250 ミリ秒の間隔を確保するために、プローブ クエリに応答する際の時間間隔 (ティック数)。 既定値は 25 ティックです。
- **NX_MDNS_RESPONSE_UNIQUE_DELAY**: ローカル ネットワークに固有のサービスに対するクエリに応答する際の遅延時間 (ティック数)。 既定値は 1 ティック (10 ミリ秒) です。
- **NX_MDNS_RESPONSE_SHARED_DELAY_MIN**: 共有リソースに対するクエリに応答する際の最小遅延時間 (ティック数)。 既定値は 2 ティック (20 ミリ秒) です。
- **NX_MDNS_RESPONSE_SHARED_DELAY_RANGE**: 共有リソースに対するクエリに応答する際の遅延時間の範囲 (ティック数)。 既定値は 10 ティック (100 ミリ秒) です。
- **NX_MDNS_RESPONSE_TC_DELAY_MIN**: TC ビットを使用してクエリに応答する際の遅延時間 (ティック数)。 既定値は 40 ティック (400 ミリ秒) です。
- **NX_MDNS_RESPONSE_TC_DELAY_RANGE**: TC ビットを使用してクエリに応答する際の遅延時間の範囲 (ティック数)。 既定値は 10 ティック (100 ミリ秒) です。
- **NX_MDNS_TIMER_COUNT_RANGE**: mDNS 応答を送信する際、パケットには、このタイマー カウンター範囲内で送信される応答が含まれます。 タイマー カウント範囲はティック数で表します。 既定値は 12 (120 ミリ秒) です。 この値を使用すると、各ティックが 10 ミリ秒の場合に、次の 120 ミリ秒の範囲内で送信されるメッセージを応答に含めることができます。
- **NX_MDNS_PROBING_RETRANSMIT_COUNT**: 再送信されるプローブ メッセージの数。 既定値は、3 です。
- **NX_MDNS_GOODBYE_RETRANSMIT_COUNT**: 再送信される "goodbye" メッセージの数。 既定値は 1 です。
- **NX_MDNS_POOF_MIN_COUNT**: マルチキャスト応答がないクエリの数。ホストは、これを、レコードが無効になった可能性があることを示していると見なす場合があります。 既定値は 2 です。
- **NX_MDNS_POOF_TIME_COUNT**: これらのクエリのうち 2 つ以上が表示され、期待される回答を含むマルチキャスト応答が表示されない場合にキャッシュからレコードを削除する際の時間間隔 (ティック数)。 既定値は 1,000 ティック (10 秒) です。
- **NX_MDNS_RR_DELETE_DELAY_TIMER_COUNT**: このレコードの TTL が 0 のときにリソース レコードを削除する際の遅延時間 (ティック数)。既定値は 100 ティック (1 秒) です。
