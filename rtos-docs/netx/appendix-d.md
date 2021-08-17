---
title: 付録 D - Azure RTOS NetX BSD 互換ソケット API
description: IPv4 用の BSD 互換ソケット API について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: bd4a35c19cd794a5135f01abe5595456d39b5306ba25ce2966c3bb1aea14ea17
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116790090"
---
# <a name="appendix-d---azure-rtos-netx-bsd-compatible-socket-api"></a>付録 D - Azure RTOS NetX BSD 互換ソケット API

## <a name="bsd-compatible-socket-api"></a>BSD 互換ソケット API

BSD 互換ソケット API は、その下で Azure RTOS NetX プリミティブを利用することで、BSD ソケット API 呼び出しのサブセットをサポートしています （一部制限あり）。 IPv4 プロトコルとネットワーク アドレス指定がサポートされています。 この BSD 互換ソケット API は内部 NetX プリミティブを利用して、不要な NetX エラー チェックをバイパスするため、この API レイヤーの実行速度は、一般的な BSD 実装と同等か、わずかに高速です。

構成可能なオプションを使用すると、ホスト アプリケーションはソケットの最大数、TCP 最大ウィンドウ サイズ、およびリッスン キューの深度を定義できます。

パフォーマンスとアーキテクチャの制約により、この BSD 互換ソケット API は、必ずしもすべての BSD ソケット呼び出しをサポートしているとは限りません。 また、次のように、すべての BSD オプションを BSD サービスで使用できるわけではありません。

- ***select** _ 関数は _fd_set\*readfds* でのみ機能します。この呼び出し内の他の引数 （*writefds*、*exceptfds* など） はサポートされていません。
- *Int flags* 引数を、***send** _、_*_recv_*_、_*_sendto_*_、および _ *_recvfrom_* * 関数で使用することはできません。 BSD 互換ソケット API は、限られた一部の BSD ソケット呼び出しのみをサポートしています。

ソース コードはシンプルに設計されており、***nx_bsd. c** _ と _*_nx_bsd_*_ の 2 つのファイルのみで構成されています。 インストールするには、この 2 つのファイルを （NetX ライブラリではなく） ビルド プロジェクトに追加し、BSD ソケット サービス呼び出しを使用するホスト アプリケーションを作成する必要があります。 お使いのアプリケーション ソースには、_ *_nx_bsd.h_** ファイルを含める必要もあります。 サンプル デモ ファイルは、NetX で自由に利用できるディストリビューションに含まれています。 詳細については、BSD 互換ソケット API パッケージにバンドルされている BSD 互換ソケット API **417** ヘルプと Readme ファイルをご覧ください。

BSD 互換ソケット API は、次の BSD ソケット API 呼び出しをサポートしています。

```C
*INT bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool,
    CHAR *bsd_memory_not_used);*

*INT getpeername( INT sockID, struct sockaddr *remoteAddress, INT *addressLength);*

*INT getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);*

*INT recvfrom(INT sockID, CHAR *buffer, INT buffersize,
    INT flags,struct sockaddr *fromAddr, INT *fromAddrLen);*

*INT recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);*

*INT sendto(INT sockID, CHAR *msg, INT msgLength, INT flags,
    struct sockaddr *destAddr, INT destAddrLen);*

*INT send(INT sockID, const CHAR *msg, INT msgLength, INT flags);*

 *INT accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);*

*INT listen(INT sockID, INT backlog);*

*INT bind (INT sockID, struct sockaddr *localAddress, INT addressLength);*

*INT connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);*

*INT socket( INT protocolFamily, INT type, INT protocol);*

*INT soc_close ( INT sockID);*

*INT select(INT nfds, fd_set *readfds, fd_set *writefds,
    fd_set *exceptfds, struct timeval *timeout);*

*VOID FD_SET(INT fd, fd_set *fdset);*

*VOID FD_CLR(INT fd, fd_set *fdset);*

*INT FD_ISSET(INT fd, fd_set *fdset);*

*VOID FD_ZERO(fd_set *fdset);*

```
