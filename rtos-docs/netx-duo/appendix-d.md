---
title: 別表 D - Azure RTOS NetX Duo BSD-Compatible Socket API
description: IPv4 および IPv6 用の BSD-Compatible Socket API について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 82439184d9facb6ddcc08ce81bc51182d7f34429
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811048"
---
# <a name="appendix-d---azure-rtos-netx-duo-bsd-compatible-socket-api"></a><span data-ttu-id="50eea-103">別表 D - Azure RTOS NetX Duo BSD-Compatible Socket API</span><span class="sxs-lookup"><span data-stu-id="50eea-103">Appendix D - Azure RTOS NetX Duo BSD-Compatible Socket API</span></span>

## <a name="bsd-compatible-socket-api"></a><span data-ttu-id="50eea-104">BSD 互換ソケット API</span><span class="sxs-lookup"><span data-stu-id="50eea-104">BSD-Compatible Socket API</span></span> 
<span data-ttu-id="50eea-105">BSD-Compatible Socket API は、NetX Duo&reg; の基本操作を実際の処理に利用することで、BSD Sockets API 呼び出しの一部をサポートしています (ある程度の制約があります)。</span><span class="sxs-lookup"><span data-stu-id="50eea-105">The BSD-Compatible Socket API supports a subset of the BSD Sockets API calls (with some limitations) by utilizing NetX Duo&reg; primitives underneath.</span></span> <span data-ttu-id="50eea-106">IPv6 と IPv4 両方のプロトコルとネットワーク アドレス指定をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="50eea-106">Both IPv6 and IPv4 protocols and network addressing are supported.</span></span> <span data-ttu-id="50eea-107">この BSD-Compatible Sockets API 互換レイヤーでは NetX Duo の基本操作を利用し、NetX の基本的なエラー チェックを行わないため、通常の BSD 実装と同等か、それよりも少し高速です。</span><span class="sxs-lookup"><span data-stu-id="50eea-107">This BSD-Compatible Sockets API layer should perform as fast or slightly faster than typical BSD implementations because this API utilizes internal NetX Duo primitives and bypasses unnecessary NetX error checking.</span></span>  

<span data-ttu-id="50eea-108">構成可能なオプションにより、ホスト アプリケーションでソケットの最大数、TCP の最大ウィンドウ サイズ、リッスン キューの深さを指定できます。</span><span class="sxs-lookup"><span data-stu-id="50eea-108">Configurable options allow the host application to define the maximum number of sockets, TCP maximum window size, and depth of listen queue.</span></span>

<span data-ttu-id="50eea-109">パフォーマンスとアーキテクチャの制約により、この BSD-Compatible Sockets API では、すべての BSD Sockets 呼び出しをサポートしてはいません。</span><span class="sxs-lookup"><span data-stu-id="50eea-109">Due to performance and architecture constraints, this BSD-Compatible Sockets API does not support all BSD Sockets calls.</span></span> <span data-ttu-id="50eea-110">また、BSD サービスではすべての BSD オプションを使用できるわけではありません。具体的には次のオプションが使用できません:</span><span class="sxs-lookup"><span data-stu-id="50eea-110">In addition, not all BSD options are available for the BSD services, specifically the following:</span></span>

  - <span data-ttu-id="50eea-111">\***select** _ 呼び出しは必ず fd_set \_readfds と合わせて使用します。この呼び出しでは writefds、exceptfds などの他の引数はサポートしていません。</span><span class="sxs-lookup"><span data-stu-id="50eea-111">\***select** _ call works with only fd_set \_readfds, other arguments in this call e.g., writefds, exceptfds are not supported.</span></span>
  - <span data-ttu-id="50eea-112">int flags 引数は、***send** _、_*_recv_*_、_*_sendto_*_、_ *_recvfrom_** 呼び出しでサポートされていません。</span><span class="sxs-lookup"><span data-stu-id="50eea-112">The "int flags" argument is not supported for ***send** _, _*_recv_*_, _*_sendto,_*_ and _ *_recvfrom_** calls.</span></span> 
  - <span data-ttu-id="50eea-113">BSD-Compatible Socket API では、BSD Sockets 呼び出しの一部だけをサポートしています。</span><span class="sxs-lookup"><span data-stu-id="50eea-113">The BSD-Compatible Socket API supports only limited set of BSD Sockets calls.</span></span>

<span data-ttu-id="50eea-114">ソース コードはシンプルであることを重視しており、***nxd_bsd.c** _ と _*_nxd_bsd.h_\*_ の 2 ファイルのみで構成されています。</span><span class="sxs-lookup"><span data-stu-id="50eea-114">The source code is designed for simplicity and is comprised of only two files, ***nxd_bsd.c** _ and _*_nxd_bsd.h_\*_.</span></span> <span data-ttu-id="50eea-115">インストールするには、これら 2 つのファイルを (NetX ライブラリではなく) ビルド プロジェクトに追加し、BSD Socket サービス呼び出しを使用するホスト アプリケーションを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="50eea-115">Installation requires adding these two files to the build project (not the NetX library) and creating the host application which will use BSD Socket service calls.</span></span> <span data-ttu-id="50eea-116">_ *_nxd_bsd.h_*\* ファイルもアプリケーションのソースでインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="50eea-116">The _ *_nxd_bsd.h_*\* file must also be included in your application source.</span></span> <span data-ttu-id="50eea-117">NetX Duo 用に自由に入手できる配布パッケージに、IPv4 と IPv6 用のアプリケーションのサンプル デモ ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="50eea-117">Sample demo files for both IPv4 and IPv6  based applications are included with the distribution which is freely available with NetX Duo.</span></span> <span data-ttu-id="50eea-118">詳細は、BSD-Compatible Socket API のパッケージに付属するヘルプと Readme ファイルをご覧ください。</span><span class="sxs-lookup"><span data-stu-id="50eea-118">Further details are available in the help and Readme files bundled with the BSDCompatible Socket API package.</span></span>

<span data-ttu-id="50eea-119">BSD-Compatible Sockets API は、次の BSD Sockets API 呼び出しをサポートしています:</span><span class="sxs-lookup"><span data-stu-id="50eea-119">The BSD-Compatible Sockets API supports the following BSD Sockets API calls:</span></span>

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