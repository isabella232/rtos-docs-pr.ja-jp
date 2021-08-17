---
title: 別表 D - Azure RTOS NetX Duo BSD-Compatible Socket API
description: IPv4 および IPv6 用の BSD-Compatible Socket API について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: cd43c3efa18dd76f6eb996c84091024f48ad65aa5839958066161080dc02127e
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116789750"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a>別表 D - Azure RTOS NetX Duo BSD-Compatible Socket API

## <a name="bsd-compatible-socket-api"></a>BSD 互換ソケット API 
BSD-Compatible Socket API は、NetX Duo&reg; の基本操作を実際の処理に利用することで、BSD Sockets API 呼び出しの一部をサポートしています (ある程度の制約があります)。 IPv6 と IPv4 両方のプロトコルとネットワーク アドレス指定をサポートしています。 この BSD-Compatible Sockets API 互換レイヤーでは NetX Duo の基本操作を利用し、NetX の基本的なエラー チェックを行わないため、通常の BSD 実装と同等か、それよりも少し高速です。  

構成可能なオプションにより、ホスト アプリケーションでソケットの最大数、TCP の最大ウィンドウ サイズ、リッスン キューの深さを指定できます。

パフォーマンスとアーキテクチャの制約により、この BSD 互換ソケット API は、必ずしもすべての BSD ソケット呼び出しをサポートしているとは限りません。 また、BSD サービスではすべての BSD オプションを使用できるわけではありません。具体的には次のオプションが使用できません:

  - ***select** _ 呼び出しは必ず fd_set \_readfds と合わせて使用します。この呼び出しでは writefds、exceptfds などの他の引数はサポートしていません。
  - int flags 引数は、***send** _、_*_recv_*_、_*_sendto_*_、_ *_recvfrom_** 呼び出しでサポートされていません。 
  - BSD-Compatible Socket API では、BSD Sockets 呼び出しの一部だけをサポートしています。

ソース コードはシンプルであることを重視しており、***nxd_bsd.c** _ と _*_nxd_bsd.h_*_ の 2 ファイルのみで構成されています。 インストールするには、これら 2 つのファイルを (NetX ライブラリではなく) ビルド プロジェクトに追加し、BSD Socket サービス呼び出しを使用するホスト アプリケーションを作成する必要があります。 _ *_nxd_bsd.h_** ファイルもアプリケーションのソースでインクルードする必要があります。 NetX Duo 用に自由に入手できる配布パッケージに、IPv4 と IPv6 用のアプリケーションのサンプル デモ ファイルが含まれています。 詳細は、BSD-Compatible Socket API のパッケージに付属するヘルプと Readme ファイルをご覧ください。

BSD-Compatible Sockets API は、次の BSD Sockets API 呼び出しをサポートしています:

```c
INT     bsd_initialize (NX_IP *default_ip, NX_PACKET_POOL *default_pool, CHAR
        *bsd_memory_not_used);
```
```c
INT     getpeername( INT sockID, struct sockaddr *remoteAddress, INT
        *addressLength);
```
```c
INT     getsockname( INT sockID, struct sockaddr *localAddress, INT *addressLength);
```
```c
INT     recvfrom(INT sockID, CHAR *buffer, INT buffersize, INT flags,struct sockaddr
        *fromAddr, INT *fromAddrLen);
```
```c        
INT     recv(INT sockID, VOID *rcvBuffer, INT bufferLength, INT flags);
```
```c
INT     sendto(INT sockID, CHAR *msg, INT msgLength, INT flags, struct sockaddr
        *destAddr, INT destAddrLen);
```
```c        
INT     send(INT sockID, const CHAR *msg, INT msgLength, INT flags);
```
```c
INT     accept(INT sockID, struct sockaddr *ClientAddress, INT *addressLength);
```
```c
INT     listen(INT sockID, INT backlog);
```
```c
INT     bind (INT sockID, struct sockaddr *localAddress, INT addressLength);
```
```c
INT     connect(INT sockID, struct sockaddr *remoteAddress, INT addressLength);
```
```c
INT     socket( INT protocolFamily, INT type, INT protocol);
```
```c
INT     soc_close ( INT sockID);
```
```c
INT     select(INT nfds, fd_set *readfds, fd_set *writefds, fd_set *exceptfds, struct
        timeval *timeout);
```
```c
VOID    FD_SET(INT fd, fd_set *fdset);
```
```c
VOID    FD_CLR(INT fd, fd_set *fdset);
```
```c
INT     FD_ISSET(INT fd, fd_set *fdset);
```
```c
VOID    FD_ZERO(fd_set *fdset);
```