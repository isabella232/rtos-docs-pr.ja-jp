---
title: チャプター 1 - Azure RTOS NetX Duo SNMP の概要
description: NetX Duo SNMP は SNMP エージェントにより実装されています。 エージェントによって SNMP マネージャーのコマンドに応答し、イベント トラップを送信します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 5760e35fdbe8d7b27e2ccc82abac37b1f6fb5118
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810598"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-snmp"></a><span data-ttu-id="4fbeb-104">チャプター 1 - Azure RTOS NetX Duo SNMP の概要</span><span class="sxs-lookup"><span data-stu-id="4fbeb-104">Chapter 1 - Introduction to Azure RTOS NetX Duo SNMP</span></span>

<span data-ttu-id="4fbeb-105">Simple Network Management Protocol (SNMP) は、インターネット上のデバイスを管理するために設計されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-105">The Simple Network Management Protocol (SNMP) is a protocol designed for managing devices on the internet.</span></span> <span data-ttu-id="4fbeb-106">SNMP は、コネクションレスのユーザー データグラム プロトコル (UDP) サービスを使用して管理機能を実行するプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-106">SNMP is a protocol that utilizes the connectionless User Datagram Protocol (UDP) services to perform its management function.</span></span> <span data-ttu-id="4fbeb-107">Azure RTOS NetX Duo SNMP は SNMP エージェントにより実装されています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-107">The Azure RTOS NetX Duo SNMP implementation is that of an SNMP Agent.</span></span> <span data-ttu-id="4fbeb-108">エージェントによって SNMP マネージャーのコマンドに応答し、イベント トラップを送信します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-108">An agent is responsible for responding to SNMP Manager’s commands and sending event driven traps.</span></span> 

<span data-ttu-id="4fbeb-109">NetX Duo SNMP は、SNMP マネージャーとの通信で IPv4 と IPv6 の両方をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-109">NetX Duo SNMP supports both IPv4 and IPv6 communication with SNMP Managers.</span></span> <span data-ttu-id="4fbeb-110">NetX SNMP アプリケーションは、NetX Duo SNMP でコンパイルして実行するべきです。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-110">NetX SNMP applications should compile and run in NetX Duo SNMP.</span></span> <span data-ttu-id="4fbeb-111">ただし、開発者の方には、既存の SNMP アプリケーションを、対応する “duo” サービスを使用できるように移植することを推奨します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-111">However, the developer is encouraged to port existing SNMP applications to using the equivalent “duo” services.</span></span> <span data-ttu-id="4fbeb-112">たとえば、SNMP トラップ メッセージを送信するときは、次の “duo” サービスで、対応する NetX サービスを置き換えます:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-112">For example, when sending SNMP trap messages, the following ‘duo’ services should replace their NetX equivalent:</span></span>

<span data-ttu-id="4fbeb-113">*nxd_snmp_object_trap_send*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-113">*nxd_snmp_object_trap_send*</span></span>

<span data-ttu-id="4fbeb-114">*nxd_snmp_object_trapv2_send*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-114">*nxd_snmp_object_trapv2_send*</span></span>

<span data-ttu-id="4fbeb-115">*nxd_snmp_object_trapv3_send*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-115">*nxd_snmp_object_trapv3_send*</span></span>

<span data-ttu-id="4fbeb-116">詳細は、このユーザー ガイドの「**SNMP エージェントのサービスの説明**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-116">For more details, see **Description of SNMP Agent Services** elsewhere in this User Guide for more details.</span></span>

## <a name="netx-duo-snmp-agent-requirements"></a><span data-ttu-id="4fbeb-117">NetX Duo SNMP エージェントの要件</span><span class="sxs-lookup"><span data-stu-id="4fbeb-117">NetX Duo SNMP Agent Requirements</span></span>

<span data-ttu-id="4fbeb-118">NetX Duo SNMP パッケージを使用するには、IP インスタンスを作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-118">The NetX Duo SNMP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="4fbeb-119">さらに、その IP インスタンスで UDP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-119">In addition, UDP must be enabled on that same IP instance.</span></span>

<span data-ttu-id="4fbeb-120">NetX Duo SNMP エージェントには、いくつかの追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-120">The NetX Duo SNMP Agent has several additional requirements.</span></span> <span data-ttu-id="4fbeb-121">まず、SNMP マネージャーのすべての要求を処理するために、ポート 161 へのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-121">First, it requires access to port 161 for handling all SNMP manager requests.</span></span> <span data-ttu-id="4fbeb-122">また、トラップ メッセージをマネージャーに送信するために、ポート 162 へのアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-122">It also requires access to port 162 for sending trap messages to the Manager.</span></span>

<span data-ttu-id="4fbeb-123">IPv6 で NetX Duo SNMP エージェントを使用して IPv6 オブジェクトを取得するには、NetX Duo で IPv6 を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-123">To use NetX Duo SNMP Agent with over IPv6 and to obtain IPv6 objects, IPv6 must be enabled in NetX Duo.</span></span> <span data-ttu-id="4fbeb-124">IPv6 サービスで IP インスタンスを有効にする方法の詳細は『***Netx Duo ユーザー ガイド***』をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-124">See the ***NetX Duo User Guide*** for details on enabling the IP instance for IPv6 services.</span></span>

## <a name="netx-duo-snmp-constraints"></a><span data-ttu-id="4fbeb-125">NetX Duo SNMP の制約</span><span class="sxs-lookup"><span data-stu-id="4fbeb-125">NetX Duo SNMP Constraints</span></span>

<span data-ttu-id="4fbeb-126">NetX Duo SNMP プロトコルでは、SNMP version 1、2、3 を実装しています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-126">The NetX Duo SNMP protocol implements SNMP Version 1, 2, and 3.</span></span> <span data-ttu-id="4fbeb-127">SNMPv3 の実装では、MD5 認証、SHA 認証、DES 暗号化をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-127">The SNMPv3 implementation supports MD5 and SHA authentication, and DES encryption.</span></span> <span data-ttu-id="4fbeb-128">このバージョンの NetX Duo SNMP エージェントには次の制約があります:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-128">This version of the NetX Duo SNMP Agent has the following constraints:</span></span>

1. <span data-ttu-id="4fbeb-129">NetX IP インスタンス 1 つにつき SNMP エージェントは 1 つだけです</span><span class="sxs-lookup"><span data-stu-id="4fbeb-129">One SNMP Agent per NetX IP Instance</span></span>
2. <span data-ttu-id="4fbeb-130">RMON をサポートしていません</span><span class="sxs-lookup"><span data-stu-id="4fbeb-130">No support for RMON</span></span>
3. <span data-ttu-id="4fbeb-131">SNMPv3 の Inform メッセージをサポートしていません</span><span class="sxs-lookup"><span data-stu-id="4fbeb-131">SNMP v3 Inform messages are not supported</span></span>
4. <span data-ttu-id="4fbeb-132">OPAQUE と NSAP のデータ型をサポートしていません</span><span class="sxs-lookup"><span data-stu-id="4fbeb-132">OPAQUE and NSAP data types are not supported</span></span>
5. <span data-ttu-id="4fbeb-133">IPv6 アドレスをオクテット文字列で指定し、形式のチェックはアプリケーションに任されています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-133">IPv6 addresses are defined as octet strings, and format checking is left to the application.</span></span>

## <a name="snmp-object-names"></a><span data-ttu-id="4fbeb-134">SNMP オブジェクトの名前</span><span class="sxs-lookup"><span data-stu-id="4fbeb-134">SNMP Object Names</span></span>

<span data-ttu-id="4fbeb-135">SNMP プロトコルはインターネット上のデバイスを管理するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-135">The SNMP protocol is designed to manage devices on the internet.</span></span> <span data-ttu-id="4fbeb-136">この目的のために、SNMP で管理するデバイスにはそれぞれ、RFC 1155 で定義されている管理情報構造 (SMI) で定義するオブジェクトのセットが存在します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-136">To accomplish this, each SNMP managed device has a set of objects that are defined by the Structure of Management Information (SMI) as defined by RFC 1155.</span></span> <span data-ttu-id="4fbeb-137">管理情報構造は、次のような階層ツリー型の構造です:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-137">The structure is a hierarchical tree type of structure that looks like the following:</span></span>

![管理情報構造の図。](media/image3.png)

<span data-ttu-id="4fbeb-139">ツリーの各ノードはオブジェクトです。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-139">Each node in the tree is an object.</span></span> <span data-ttu-id="4fbeb-140">ツリーの “dod” オブジェクトは 1.3.6 の標識によって、“internet” オブジェクトは 1.3.6.1 の標識によって識別されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-140">The “dod” object in the tree is identified by the notation 1.3.6, while the “internet” object in the tree is identified by the notation 1.3.6.1.</span></span> <span data-ttu-id="4fbeb-141">SNMP オブジェクトの名前はすべて 1.3.6 で始まります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-141">All SNMP object names begin with the notation 1.3.6.</span></span>

<span data-ttu-id="4fbeb-142">SNMP マネージャーは、このオブジェクト命名法を使用して、取得または設定するデバイス上のオブジェクトを指定します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-142">An SNMP Manager uses this object notation to specify what object in the device it wishes to get or set.</span></span> <span data-ttu-id="4fbeb-143">NetX Duo SNMP エージェントはマネージャーのそうした要求を解釈し、要求された操作をアプリケーションで実行する仕組みを提供します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-143">The NetX Duo SNMP Agent interprets such manager requests and provides mechanisms for the application to perform the requested operation.</span></span>

## <a name="snmp-manager-requests"></a><span data-ttu-id="4fbeb-144">SNMP マネージャーの要求</span><span class="sxs-lookup"><span data-stu-id="4fbeb-144">SNMP Manager Requests</span></span>

<span data-ttu-id="4fbeb-145">SNMP には、デバイスを管理するシンプルな仕組みがあります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-145">The SNMP has a simple mechanism for managing devices.</span></span> <span data-ttu-id="4fbeb-146">SNMP には、SNMP マネージャーが *ポート 161* を使用して SNMP デバイスに発行する、標準 SNMP コマンドのセットが存在します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-146">There is a set of standard SNMP commands that are issued by the SNMP Manager to the SNMP device on *port 161*.</span></span> <span data-ttu-id="4fbeb-147">SNMP マネージャーの基本的なコマンドの一部を次に挙げます:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-147">The following shows some of the basic SNMP Manager commands:</span></span>

| <span data-ttu-id="4fbeb-148">SNMP コマンド</span><span class="sxs-lookup"><span data-stu-id="4fbeb-148">SNMP Command</span></span> | <span data-ttu-id="4fbeb-149">意味</span><span class="sxs-lookup"><span data-stu-id="4fbeb-149">Meaning</span></span>                                                        |
|--------------|----------------------------------------------------------------|
| <span data-ttu-id="4fbeb-150">GET</span><span class="sxs-lookup"><span data-stu-id="4fbeb-150">GET</span></span>          | <span data-ttu-id="4fbeb-151">*指定したオブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-151">*Get the specified object*</span></span>                                       |
| <span data-ttu-id="4fbeb-152">GETNEXT</span><span class="sxs-lookup"><span data-stu-id="4fbeb-152">GETNEXT</span></span>      | <span data-ttu-id="4fbeb-153">*指定したオブジェクト ID の次の論理オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-153">*Get the next logical object after the specified object ID*</span></span>      |
| <span data-ttu-id="4fbeb-154">GETBULK</span><span class="sxs-lookup"><span data-stu-id="4fbeb-154">GETBULK</span></span>      | <span data-ttu-id="4fbeb-155">*指定したオブジェクト ID より後にある複数の論理オブジェクトを取得します*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-155">*Get the multiple logical objects after the specified object ID*</span></span> |
| <span data-ttu-id="4fbeb-156">SET</span><span class="sxs-lookup"><span data-stu-id="4fbeb-156">SET</span></span>          | <span data-ttu-id="4fbeb-157">*指定したオブジェクトを設定します*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-157">*Set the specified object*</span></span>                                       |

<span data-ttu-id="4fbeb-158">これらのコマンドは抽象構文記法 1 (ASN.1) 形式でエンコードされ、SNMP マネージャーから送信される UDP パケットのペイロードに存在します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-158">These commands are encoded in the Abstract Syntax Notation One (ASN.1) format and reside in the payload of the UDP packet sent by the SNMP Manager.</span></span> <span data-ttu-id="4fbeb-159">NetX Duo SNMP エージェント は、要求を処理してから、***nx_snmp_agent_create*** の呼び出しで指定された、対応する処理ルーチンを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-159">The NetX Duo SNMP Agent processes the request and then calls the corresponding handling routine specified in the ***nx_snmp_agent_create*** call.</span></span>

## <a name="netx-duo-snmp-agent-traps"></a><span data-ttu-id="4fbeb-160">NetX Duo SNMP エージェント トラップ</span><span class="sxs-lookup"><span data-stu-id="4fbeb-160">NetX Duo SNMP Agent Traps</span></span>

<span data-ttu-id="4fbeb-161">NetX Duo SNMP エージェント によって、SNMP マネージャーに非同期でイベントのアラートを送ることができます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-161">The NetX Duo SNMP Agent provides the ability to also alert an SNMP Manager of events asynchronously.</span></span> <span data-ttu-id="4fbeb-162">これは SNMP トラップ コマンドで実行します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-162">This is done via an SNMP trap command.</span></span> <span data-ttu-id="4fbeb-163">SNMP マネージャーにトラップを送信するために、SNMP の各バージョンには固有の API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-163">There is a unique API for each version of SNMP for sending traps to an SNMP Manager.</span></span> <span data-ttu-id="4fbeb-164">既定では、トラップはSNMP マネージャーのポート 162 に送信されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-164">By default, the traps are sent to the SNMP Manager on port 162.</span></span>

<span data-ttu-id="4fbeb-165">NetX Duo SNMP エージェント では、SNMPv3 のトラップ メッセージに個別のセキュリティ キーを使用します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-165">The NetX Duo SNMP Agent provides separate security keys for SNMPv3 trap messages.</span></span> <span data-ttu-id="4fbeb-166">そのため、SNMP アプリケーションでは、マネージャーの要求への応答に使用するもキーとは別に、キーのセットを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-166">To do so, the SNMP application must create a separate set of keys from those applied to responses to Manager requests.</span></span> <span data-ttu-id="4fbeb-167">トラップのセキュリティにより、SNMP エージェントでは、認証用とプライバシー用で同じパスワードと異なるパスワードのどちらも使用できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-167">Trap security enables the SNMP Agent to use the same or different passwords for authentication and privacy.</span></span> <span data-ttu-id="4fbeb-168">セキュリティ キー作成の詳しい情報は、次のセクションの「**Netx Duo SNMP 認証および暗号化**」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-168">For more information on creating security keys, see **NetX Duo SNMP Authentication and Encryption** in the next section.</span></span>

<span data-ttu-id="4fbeb-169">標準の SNMP トラップ変数は *nxd_snmp.h* の冒頭に列挙されています:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-169">A list of standard SNMP trap variables is enumerated at the top of *nxd_snmp.h:*</span></span>

| <span data-ttu-id="4fbeb-170">変数</span><span class="sxs-lookup"><span data-stu-id="4fbeb-170">Variables</span></span>                                 | <span data-ttu-id="4fbeb-171">値</span><span class="sxs-lookup"><span data-stu-id="4fbeb-171">Value</span></span>  |
|-------------------------------------------|---|
| <span data-ttu-id="4fbeb-172">#NX_SNMP_TRAP_COLDSTART を有効</span><span class="sxs-lookup"><span data-stu-id="4fbeb-172">#define NX_SNMP_TRAP_COLDSTART</span></span>            | <span data-ttu-id="4fbeb-173">0</span><span class="sxs-lookup"><span data-stu-id="4fbeb-173">0</span></span> |
| <span data-ttu-id="4fbeb-174">#NX_SNMP_TRAP_WARMSTART を有効化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-174">#define NX_SNMP_TRAP_WARMSTART</span></span>            | <span data-ttu-id="4fbeb-175">1</span><span class="sxs-lookup"><span data-stu-id="4fbeb-175">1</span></span> |
| <span data-ttu-id="4fbeb-176">#NX_SNMP_TRAP_LINKDOWN を有効化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-176">#define NX_SNMP_TRAP_LINKDOWN</span></span>             | <span data-ttu-id="4fbeb-177">2</span><span class="sxs-lookup"><span data-stu-id="4fbeb-177">2</span></span> |
| <span data-ttu-id="4fbeb-178">#NX_SNMP_TRAP_LINKUP を有効化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-178">#define NX_SNMP_TRAP_LINKUP</span></span>               | <span data-ttu-id="4fbeb-179">3</span><span class="sxs-lookup"><span data-stu-id="4fbeb-179">3</span></span> |
| <span data-ttu-id="4fbeb-180">#NX_SNMP_TRAP_AUTHENTICATE_FAILURE を有効化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-180">#define NX_SNMP_TRAP_AUTHENTICATE_FAILURE</span></span> | <span data-ttu-id="4fbeb-181">4</span><span class="sxs-lookup"><span data-stu-id="4fbeb-181">4</span></span> |
| <span data-ttu-id="4fbeb-182">#NX_SNMP_TRAP_EGPNEIGHBORLOSS を有効化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-182">#define NX_SNMP_TRAP_EGPNEIGHBORLOSS</span></span>      | <span data-ttu-id="4fbeb-183">5</span><span class="sxs-lookup"><span data-stu-id="4fbeb-183">5</span></span> |
| <span data-ttu-id="4fbeb-184">#NX_SNMP_TRAP_ENTERPRISESPECIFIC を有効化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-184">#define NX_SNMP_TRAP_ENTERPRISESPECIFIC</span></span>   | <span data-ttu-id="4fbeb-185">6</span><span class="sxs-lookup"><span data-stu-id="4fbeb-185">6</span></span> |

<span data-ttu-id="4fbeb-186">これらの変数をトラップ メッセージに含めるには、ここに列挙されている値を、各変数に対応する値として、*nx_snmp_agent_trapv2_send* (SNMPv2) または *nx_snmp_agent_trapv3_send* (SNMPv3) の trap_type 引数に入力します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-186">To include these variables in the trap message, the trap_type input argument in *nx_snmp_agent_trapv2_send* (SNMPv2) or *nx_snmp_agent_trapv3_send* (SNMPv3) is set to the enumerated value of these variables.</span></span> <span data-ttu-id="4fbeb-187">下に示すのは、SNMPv2 で SNMP マネージャーにコールド スタートのイベントを通知する例です:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-187">An example is shown below for SNMPv2 to notify the SNMP Manager of a cold start event:</span></span>

```c
UINT trap_type = NX_SNMP_TRAP_COLDSTART;

status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                  (UCHAR *)"public", trap_type,
                                  tx_time_get(), NX_NULL);

```

<span data-ttu-id="4fbeb-188">独自の変数をトラップ メッセージに含めるには、trap_type 引数を NX_SNMP_TRAP_CUSTOM に設定して、トラップ リストの引数に独自のデータを入力します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-188">To include proprietary variables in the trap message, the trap_type input argument is set to NX_SNMP_TRAP_CUSTOM and the trap list input argument contains the proprietary data.</span></span> <span data-ttu-id="4fbeb-189">トラップ メッセージにはシステムのアップタイム (1.3.6.1.6.3.1.1.4.1.0) が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-189">Note that the trap message will contain as the system up time (1.3.6.1.6.3.1.1.4.1.0).</span></span> <span data-ttu-id="4fbeb-190">次に SNMPv2 の例を示します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-190">An example is shown below for SNMPv2:</span></span>

```c
NX_SNMP_TRAP_OBJECT trap_list[3];
NX_SNMP_OBJECT_DATA trap_data0;

    /* Load the data into the OBJECT. */
    nx_snmp_object_id_get((void*)"1.3.6.1.4.1.7428.1.3.2.0", &trap_data0);

    /* Update the Trap Object with the object and OID. */
    trap_list[0].nx_snmp_object_string_ptr = (UCHAR *)"1.3.6.1.6.3.1.1.4.0";
    trap_list[0].nx_snmp_object_data  = &trap_data0;

    /* Null terminate the trap list. */
    trap_list[1].nx_snmp_object_string_ptr = NX_NULL;

    status = nx_snmp_agent_trapv2_send(&my_agent, MIB_IP_ADDRESS,
                                      (UCHAR *)"trapduo",
                                      NX_SNMP_TRAP_CUSTOM,
                                      tx_time_get(), trap_list);
```

## <a name="netx-duo-snmp-authentication-and-encryption"></a><span data-ttu-id="4fbeb-191">NetX Duo SNMP 認証および暗号化</span><span class="sxs-lookup"><span data-stu-id="4fbeb-191">NetX Duo SNMP Authentication and Encryption</span></span>

<span data-ttu-id="4fbeb-192">認証には *Basic* と *Digest* の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-192">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="4fbeb-193">Basic 認証は、多くのプロトコルで使用される、プレーン テキストを用いた単純な *ユーザー名* 認証と同等の認証です。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-193">Basic authentication is equivalent to a simple plain text *username* authentication found in many protocols.</span></span> <span data-ttu-id="4fbeb-194">SNMP の Basic 認証では、渡されたユーザー名が SNMP 操作を実行するために有効であることを確認するだけです。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-194">In SNMP basic authentication, the user simply verifies that the supplied username is valid for performing SNMP operations.</span></span> <span data-ttu-id="4fbeb-195">SNMP バージョン 1 と 2 では、Basic 認証だけを使用できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-195">Basic authentication is the only option for SNMP versions 1 and 2.</span></span>

<span data-ttu-id="4fbeb-196">Basic 認証の主な欠点はユーザー名をプレーン テキストで送信することです。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-196">The main disadvantage of basic authentication is the username is transmitted in plain text.</span></span> <span data-ttu-id="4fbeb-197">SNMPv3 の Digest 認証では、ユーザー名をプレーン テキストで送信しないことによって、この問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-197">The SNMPv3 digest authentication addresses this problem by never transmitting the username in plain text.</span></span> <span data-ttu-id="4fbeb-198">代わりに、アルゴリズムを使用して、ユーザー名、コンテキスト エンジンなどの情報から 96 ビットの “ダイジェスト” を生成します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-198">Instead, an algorithm is used to derive a 96-bit ‘digest’ from the username, context engine, and other information.</span></span> <span data-ttu-id="4fbeb-199">NetX Duo SNMP エージェント は、MD5 と SHA のダイジェスト アルゴリズムを両方サポートしています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-199">The NetX Duo SNMP Agent supports both MD5 and SHA digest algorithms.</span></span>

<span data-ttu-id="4fbeb-200">認証を有効にするには、SNMP エージェントで *nx_snmp_agent_context_engine_set* サービスを使用してコンテキスト エンジン ID を設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-200">To enable authentication, the SNMP Agent must set its Context Engine ID using the *nx_snmp_agent_context_engine_set* service.</span></span> <span data-ttu-id="4fbeb-201">コンテキスト エンジン ID は、認証キーの作成に使用します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-201">The Context Engine ID is used in the creation of the authentication key.</span></span>

<span data-ttu-id="4fbeb-202">SNMPv3 のデータは DES アルゴリズムを使用して暗号化できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-202">Encryption of SNMPv3 data is available using the DES algorithm.</span></span> <span data-ttu-id="4fbeb-203">暗号化するには認証を有効にする必要があります (認証のパラメーターを設定しないとデータを暗号化できません)。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-203">Encryption requires that authentication be enabled (one cannot encrypt data without setting the authentication parameters).</span></span>

<span data-ttu-id="4fbeb-204">認証キーとプライバシー キーを作成するには次の API を使用します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-204">To create authentication and privacy keys, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_md5_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)

UINT  _nx_snmp_agent_sha_key_create(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *password, NX_SNMP_SECURITY_KEY
                                   *destination_key)
```

<span data-ttu-id="4fbeb-205">次に、これらのキーを使用するように SNMP エージェントを構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-205">Next, the SNMP agent must be configured to use these keys.</span></span> <span data-ttu-id="4fbeb-206">キーを SNMP エージェントに登録するには次の API を使用します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-206">To register a key with the SNMP agent, the following API are used:</span></span>

```c
UINT  _nx_snmp_agent_authenticate_key_use(NX_SNMP_AGENT *agent_ptr,
                                          NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_privacy_key_use(NX_SNMP_AGENT *agent_ptr,
                                    NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="4fbeb-207">トラップ メッセージには個別のキーを作成できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-207">Separate keys can be created for trap messages.</span></span> <span data-ttu-id="4fbeb-208">トラップ メッセージ用のキーを使用するには次の API を使用します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-208">To apply keys for trap messages the following API are available:</span></span>

```c
UINT  _nx_snmp_agent_auth_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)

UINT  _nx_snmp_agent_priv_trap_key_use(NX_SNMP_AGENT *agent_ptr,
                                       NX_SNMP_SECURITY_KEY *key)
```

<span data-ttu-id="4fbeb-209">応答メッセージとトラップ送信の認証または暗号化を無効にするには、キー ポインターの入力を NULL に設定してこれらのサービスを使用します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-209">To disable authentication or encryption for response messages and sending traps, use these services with the key pointer input set to NULL.</span></span>

## <a name="netx-duo-snmp-community-strings"></a><span data-ttu-id="4fbeb-210">NetX Duo SNMP コミュニティ文字列</span><span class="sxs-lookup"><span data-stu-id="4fbeb-210">NetX Duo SNMP Community Strings</span></span>

<span data-ttu-id="4fbeb-211">NetX Duo SNMP エージェント は、パブリックとプライベート両方のコミュニティ文字列をサポートしています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-211">The NetX Duo SNMP Agent supports both public and private community strings.</span></span> <span data-ttu-id="4fbeb-212">パブリック文字列は *nx_snmp_agent _public_string_set* サービスで設定します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-212">The public string is set with the *nx_snmp_agent _public_string_set* service.</span></span> <span data-ttu-id="4fbeb-213">NetX Duo SNMP エージェント のプライベート文字列は *nx_snmp_agent_private_string_set* サービスを使用して設定します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-213">The NetX Duo SNMP Agent private string is set using the *nx_snmp_agent_private_string_set* service.</span></span>

## <a name="netx-duo-snmp-username-callback"></a><span data-ttu-id="4fbeb-214">NetX Duo SNMP ユーザー名コールバック</span><span class="sxs-lookup"><span data-stu-id="4fbeb-214">NetX Duo SNMP Username Callback</span></span>

<span data-ttu-id="4fbeb-215">NetX Duo SNMP エージェント パッケージでは、アプリケーションで、SNMP クライアントの各要求の処理を開始するときに呼び出すユーザー名コールバックを指定できます (***nx_snmp_agent_create*** を呼び出すことで指定します)。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-215">The NetX Duo SNMP Agent package allows the application to specify (via the ***nx_snmp_agent_create*** call) a username callback  that is called at the beginning of handling each SNMP Client request.</span></span>

<span data-ttu-id="4fbeb-216">コールバック ルーチンで、NetX Duo SNMP エージェント にユーザー名を渡します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-216">The callback routine provides the NetX Duo SNMP Agent with the username.</span></span> <span data-ttu-id="4fbeb-217">渡されたユーザー名が有効である場合、または要求への応答にユーザー名の確認が必要ない場合は、ユーザー名コールバックから **NX_SUCCESS** の値が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-217">If the supplied username is valid or if no username check is necessary for the responding to the request, the username callback should return the value of **NX_SUCCESS**.</span></span> <span data-ttu-id="4fbeb-218">それ以外の場合は、ルーチンから **NX_SNMP_ERROR** が返され、指定されたユーザー名が無効であることを示します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-218">Otherwise, the routine should return **NX_SNMP_ERROR** to indicate the specified username is invalid.</span></span>

<span data-ttu-id="4fbeb-219">アプリケーションのユーザー名コールバック ルーチンの形式は次のとおりです:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-219">The format of the application username callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_username_process(NX_SNMP_AGENT *agent_ptr,
                                    UCHAR *username);
```

<span data-ttu-id="4fbeb-220">入力パラメーターは次のとおり定義されています:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-220">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="4fbeb-221">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-221">Parameter</span></span> | <span data-ttu-id="4fbeb-222">意味</span><span class="sxs-lookup"><span data-stu-id="4fbeb-222">Meaning</span></span>                                              |
|-----------|------------------------------------------------------|
| <span data-ttu-id="4fbeb-223">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-223">*agent_ptr*</span></span> | <span data-ttu-id="4fbeb-224">呼び出し元の SNMP エージェントへのポインター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-224">Pointer to calling SNMP agent</span></span>                        |
| <span data-ttu-id="4fbeb-225">username</span><span class="sxs-lookup"><span data-stu-id="4fbeb-225">username</span></span>  | <span data-ttu-id="4fbeb-226">必要なユーザー名へのポインターの保存先</span><span class="sxs-lookup"><span data-stu-id="4fbeb-226">Destination for the pointer to the required username</span></span> |

<span data-ttu-id="4fbeb-227">SNMPv1 および SNMPv2/v2C セッションンでは、アプリケーション使用時に、受信 SNMP 要求のコミュニティ文字列を調べてそれが有効かどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-227">For SNMPv1 and SNMPv2/v2C sessions, the application will want to examine the community string on an incoming SNMP request to determine if the SNMP request has a valid community string.</span></span> <span data-ttu-id="4fbeb-228">SNMP アプリケーションには、これを実行するためのサービスがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-228">There are several services for the SNMP application to do this.</span></span>

<span data-ttu-id="4fbeb-229">SNMP アプリケーションでは、処理中の SNMP マネージャーの要求が GET (GET、GETNEXT、GETBULKなど) と SET どちらのタイプの要求かを、次のサービスによって確認できます:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-229">The SNMP application can inquire if the current SNMP Manager request is a GET (e.g. GET, GETNEXT, or GETBULK) or SET type of request using this service:</span></span>

```c
UINT nx_snmp_agent_request_get_type_test(NX_SNMP_AGENT *agent_ptr,
                                         UINT *is_get_type);
```

<span data-ttu-id="4fbeb-230">GET タイプの要求である場合、アプリケーションでは、入力されたコミュニティ文字列を SNMP エージェントのパブリック文字列と比較します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-230">If the request is a GET type, the application will want to compare the input community string to the SNMP Agent’s public string:</span></span>

```c
UINT nx_snmp_agent_public_string_test(NX_SNMP_AGENT *agent_ptr,
                                      UCHAR *username,
                                      UINT *is_public);
```

<span data-ttu-id="4fbeb-231">SET タイプの要求である場合、アプリケーションでは、入力されたコミュニティ文字列を SNMP エージェントのプライベート文字列と比較します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-231">Similarly if the request is a SET type, the application will want to compare the input community string to the SNMP Agent’s private string:</span></span>

```c
UINT nx_snmp_agent_private_string_test(NX_SNMP_AGENT *agent_ptr,
                                       UCHAR *username,
                                       UINT *is_private);
```

<span data-ttu-id="4fbeb-232">is_public と is_private の戻り値はそれぞれ、入力されたコミュニティ文字列が有効なパブリック コミュニティ文字列、有効なプライベート コミュニティ文字列であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-232">The is_public and is_private return values indicate respectively if the input community string is a valid public or private community string.</span></span>

<span data-ttu-id="4fbeb-233">ユーザー名コールバック ルーチンの戻り値は、ユーザー名が有効であるかどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-233">The return value of the username callback routine indicates if the username is valid.</span></span> <span data-ttu-id="4fbeb-234">ユーザー名が有効である場合は **NX_SUCCESS** という値が、ユーザー名が無効である場合は **NX_SNMP_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-234">The value **NX_SUCCESS** is returned if the username is valid, or **NX_SNMP_ERROR** if the username is invalid.</span></span>

## <a name="netx-duo-snmp-agent-get-callback"></a><span data-ttu-id="4fbeb-235">NetX Duo SNMP エージェント GET コールバック</span><span class="sxs-lookup"><span data-stu-id="4fbeb-235">NetX Duo SNMP Agent GET Callback</span></span>

<span data-ttu-id="4fbeb-236">アプリケーションでは、SNMP マネージャーの GET オブジェクト要求を処理するコールバック ルーチンを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-236">The application must set a callback routine for handling GET object requests from the SNMP Manager.</span></span> <span data-ttu-id="4fbeb-237">そのコールバックにより、要求で指定されたオブジェクトの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-237">The callback retrieves the value of the object specified in the request.</span></span>

<span data-ttu-id="4fbeb-238">アプリケーションの GET 要求コールバック ルーチンは次のように定義されます:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-238">The application GET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_get_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="4fbeb-239">入力パラメーターは次のとおり定義されています:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-239">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="4fbeb-240">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-240">Parameter</span></span>        | <span data-ttu-id="4fbeb-241">意味</span><span class="sxs-lookup"><span data-stu-id="4fbeb-241">Meaning</span></span> |
|------------------|----------------------------------|
| <span data-ttu-id="4fbeb-242">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-242">*agent_ptr*</span></span>        | <span data-ttu-id="4fbeb-243">呼び出し元の SNMP エージェントへのポインター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-243">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="4fbeb-244">object_requested</span><span class="sxs-lookup"><span data-stu-id="4fbeb-244">object_requested</span></span> | <span data-ttu-id="4fbeb-245">GET 操作の対象のオブジェクト ID を表す ASCII 文字列。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-245">ASCII string representing the object ID the GET operation is for.</span></span> |
| <span data-ttu-id="4fbeb-246">object_data</span><span class="sxs-lookup"><span data-stu-id="4fbeb-246">object_data</span></span>      | <span data-ttu-id="4fbeb-247">コールバックで取得した値を保持するデータ構造体。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-247">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="4fbeb-248">これは、次に説明する一連の NetX Duo SNMP API で設定できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-248">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

> [!NOTE]
> <span data-ttu-id="4fbeb-249">*コールバック自体には長さの引数がないため、オクテット文字列を使用する場合は、オブジェクトに長さを割り当てて、内部の関数で長さを把握できるようにする必要があります:*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-249">*For octet strings, the object must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:*</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="4fbeb-250">GET コールバックではそのデータ型を扱わないため、データ型を確認する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-250">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="4fbeb-251">長さは、数値型または NULL 区切りの文字列には影響しません。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-251">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="4fbeb-252">次に内部の関数を呼び出します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-252">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="4fbeb-253">要求されたオブジェクトがコールバック関数で見つからない場合は **NX_SNMP_ERROR_NOSUCHNAME** エラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-253">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="4fbeb-254">他のエラーが検出された場合は **NX_SNMP_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-254">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-getnext-callback"></a><span data-ttu-id="4fbeb-255">NetX Duo SNMP エージェント の GETNEXT コールバック</span><span class="sxs-lookup"><span data-stu-id="4fbeb-255">NetX Duo SNMP Agent GETNEXT Callback</span></span>

<span data-ttu-id="4fbeb-256">アプリケーションでは、SNMP マネージャーによる GETNEXT オブジェクト要求のためのコールバック ルーチンも設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-256">The application must also set the callback routine for GETNEXT object requests from the SNMP Manager.</span></span> <span data-ttu-id="4fbeb-257">GETNEXT コールバックは、要求で指定された次のオブジェクトの値を取得します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-257">The GETNEXT callback retrieves the value of the next object specified by the request.</span></span>

<span data-ttu-id="4fbeb-258">アプリケーションの GETNEXT 要求コールバック ルーチンは次のように定義されます:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-258">The application GETNEXT request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_getnext_process(NX_SNMP_AGENT *agent_ptr,
                                   UCHAR *object_requested,
                                   NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="4fbeb-259">入力パラメーターは次のとおり定義されています:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-259">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="4fbeb-260">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-260">Parameter</span></span>        | <span data-ttu-id="4fbeb-261">意味</span><span class="sxs-lookup"><span data-stu-id="4fbeb-261">Meaning</span></span> |
|------------------|-------------------------------------------|
| <span data-ttu-id="4fbeb-262">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-262">*agent_ptr*</span></span>        | <span data-ttu-id="4fbeb-263">呼び出し元の SNMP エージェントへのポインター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-263">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="4fbeb-264">object_requested</span><span class="sxs-lookup"><span data-stu-id="4fbeb-264">object_requested</span></span> | <span data-ttu-id="4fbeb-265">GETNEXT 操作の対象のオブジェクト ID を表す ASCII 文字列。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-265">ASCII string representing the object ID the GETNEXT operation is for.</span></span> |
| <span data-ttu-id="4fbeb-266">object_data</span><span class="sxs-lookup"><span data-stu-id="4fbeb-266">object_data</span></span>      | <span data-ttu-id="4fbeb-267">コールバックで取得した値を保持するデータ構造体。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-267">Data structure to hold the value retrieved by the callback.</span></span> <span data-ttu-id="4fbeb-268">これは、次に説明する一連の NetX Duo SNMP API で設定できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-268">This can be set with a series of NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="4fbeb-269">コールバック自体には長さの引数がないため、GET コールバックと同様に、オクテット文字列のデータを含むオブジェクトには長さを割り当てて、内部関数で長さを把握できるようにする必要があります:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-269">Same as is true for GET callbacks, objects with octet string data must be assigned the length so that the internal function knows how long the length is since the callback itself does not have a length argument:</span></span>

```c
object_data -> nx_snmp_object_octet_string_size = mib2_mib[i].length;
```

<span data-ttu-id="4fbeb-270">GET コールバックではそのデータ型を扱わないため、データ型を確認する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-270">Since the type of data is not known to the GET callback, there is no need to check the data type.</span></span> <span data-ttu-id="4fbeb-271">長さは、数値型または NULL 区切りの文字列には影響しません。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-271">Length will not have any effect on numeric types or strings which are null delimited.</span></span>

<span data-ttu-id="4fbeb-272">次に内部の関数を呼び出します:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-272">Then call the internal function:</span></span>

```c
status = mib2_mib[i].object_get_callback)
                   (mib2_mib[i].object_value_ptr, object_data);
```

<span data-ttu-id="4fbeb-273">要求されたオブジェクトがコールバック関数で見つからない場合は **NX_SNMP_ERROR_NOSUCHNAME** エラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-273">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span> <span data-ttu-id="4fbeb-274">他のエラーが検出された場合は **NX_SNMP_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-274">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

## <a name="netx-duo-snmp-agent-set-callback"></a><span data-ttu-id="4fbeb-275">NetX Duo SNMP エージェント SET コールバック</span><span class="sxs-lookup"><span data-stu-id="4fbeb-275">NetX Duo SNMP Agent SET Callback</span></span>

<span data-ttu-id="4fbeb-276">アプリケーションでは、SNMP マネージャーによる SET オブジェクト要求を処理するコールバック ルーチンを設定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-276">The application should set the callback routine for handling SET object requests from the SNMP Manager.</span></span> <span data-ttu-id="4fbeb-277">SET コールバックは、要求で指定されたオブジェクトの値を設定します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-277">The SET callback sets the value of the object specified by the request.</span></span>

<span data-ttu-id="4fbeb-278">アプリケーションの SET 要求コールバック ルーチンは次のように定義されます:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-278">The application SET request callback routine is defined below:</span></span>

```c
UINT nx_snmp_agent_set_process(NX_SNMP_AGENT *agent_ptr,
                               UCHAR *object_requested,
                               NX_SNMP_OBJECT_DATA *object_data);
```

<span data-ttu-id="4fbeb-279">入力パラメーターは次のとおり定義されています:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-279">The input parameters are defined as follows:</span></span>

| <span data-ttu-id="4fbeb-280">パラメーター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-280">Parameter</span></span>        | <span data-ttu-id="4fbeb-281">意味</span><span class="sxs-lookup"><span data-stu-id="4fbeb-281">Meaning</span></span> |
|------------------|-------- |
| <span data-ttu-id="4fbeb-282">*agent_ptr*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-282">*agent_ptr*</span></span>      | <span data-ttu-id="4fbeb-283">呼び出し元の SNMP エージェントへのポインター</span><span class="sxs-lookup"><span data-stu-id="4fbeb-283">Pointer to calling SNMP agent</span></span> |
| <span data-ttu-id="4fbeb-284">object_requested</span><span class="sxs-lookup"><span data-stu-id="4fbeb-284">object_requested</span></span> | <span data-ttu-id="4fbeb-285">SET 操作の対象のオブジェクト ID を表す ASCII 文字列。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-285">ASCII string representing the object ID the SET operation is for.</span></span> |
| <span data-ttu-id="4fbeb-286">object_data</span><span class="sxs-lookup"><span data-stu-id="4fbeb-286">object_data</span></span>      | <span data-ttu-id="4fbeb-287">指定されたオブジェクトのための新しい値を保持するデータ構造体。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-287">Data structure that contains the new value for the specified object.</span></span> <span data-ttu-id="4fbeb-288">操作は、次に説明する NetX Duo SNMP API を使用して実行できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-288">The actual operation can be done using the NetX Duo SNMP API’s described below.</span></span> |

<span data-ttu-id="4fbeb-289">オクテット文字列については、SET コールバックで MIB テーブルの長さのデータを更新するべきです。これは、SNMP エージェントが前もってデータを解析して型と長さを把握しているからです:</span><span class="sxs-lookup"><span data-stu-id="4fbeb-289">Note that for octet strings, the SET callback should update the MIB table with the length of the data since the SNMP Agent has parsed the data and knows the type and length:</span></span>

```c
if (object_data -> nx_snmp_object_data_type ==
                           NX_SNMP_ANS1_OCTET_STRING)
{
    mib2_mib[i].length =
        object_data -> nx_snmp_object_octet_string_size;
}

object_data -> nx_snmp_object_octet_string_size =
                                 mib2_mib[i].length;
```

<span data-ttu-id="4fbeb-290">要求されたオブジェクトがコールバック関数で見つからない場合は **NX_SNMP_ERROR_NOSUCHNAME** エラー コードが返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-290">If the callback function cannot find the requested object, the **NX_SNMP_ERROR_NOSUCHNAME** error code should be returned.</span></span>

<span data-ttu-id="4fbeb-291">NetX Duo SNMP ホストでプライベート　コミュニティ文字列が既に作成されていて、SNMP の SET 要求の送信元にそれに一致するプライベート文字列がない場合、**NX_SNMP_ERROR_NOACCESS** エラーが返されることがあります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-291">If the NetX Duo SNMP host has created private community strings, and the SNMP sender of the SET request does not have the matching private string, it may return an **NX_SNMP_ERROR_NOACCESS** error.</span></span> <span data-ttu-id="4fbeb-292">他のエラーが検出された場合は **NX_SNMP_ERROR** が返されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-292">If any other error is detected, the **NX_SNMP_ERROR** should be returned.</span></span>

> [!NOTE]
> <span data-ttu-id="4fbeb-293">*NetX Duo SNMP エージェント の配布パッケージには SNMP MIB データベースが付いて来ますが、それは主にテストおよび開発用です。開発者がプロフェッショナル向けの SNMP アプリケーションを使用するためには、恐らく、独自の MIB データベースが必要になるでしょう。*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-293">*Although NetX Duo SNMP Agent supplies an SNMP MIB database with the distribution, it is primarily for testing and development purposes. The developer will likely require a proprietary MIB database for a professional SNMP application.*</span></span>

## <a name="changing-snmp-version-at-run-time"></a><span data-ttu-id="4fbeb-294">実行時に SNMP のバージョンを変更する</span><span class="sxs-lookup"><span data-stu-id="4fbeb-294">Changing SNMP Version at Run Time</span></span>

<span data-ttu-id="4fbeb-295">SNMP エージェント ホストは、実行時に *nx_snmp_agent_set_version* サービスを使用して、3 つの SNMP バージョンのうち好きなものにバージョンを変更できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-295">The SNMP Agent host can change SNMP version for each of the three versions at run time using the *nx_snmp_agent_set_version* service.</span></span> <span data-ttu-id="4fbeb-296">*nx_snmp_agent_create* で SNMP エージェントを作成すると、3 つのバージョンすべてに対して SNMP エージェントは既定で有効になります。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-296">The SNMP Agent is by default enabled for all three versions when the SNMP Agent is created in *nx_snmp_agent_create*.</span></span> <span data-ttu-id="4fbeb-297">ですが、アプリケーションでそれを一部のバージョンに限定することもできます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-297">However, the application can limit that to a subset of all versions.</span></span>

> [!NOTE]
> <span data-ttu-id="4fbeb-298">*構成オプションの NX_SNMP_DISABLE_V1、 NX_SNMP_DISABLE_V2 または NX_SNMP_DISABLE_V3 を有効にしている場合、そのオプションの対象となるバージョンに対して、この関数で SNMP エージェントを有効にすることはできません。*</span><span class="sxs-lookup"><span data-stu-id="4fbeb-298">*If the configuration options NX_SNMP_DISABLE_V1, NX_SNMP_DISABLE_V2 and/or NX_SNMP_DISABLE_V3 are defined, this function will have no effect enabling the effected versions.*</span></span>

<span data-ttu-id="4fbeb-299">SNMP エージェントでは *nx_snmp_agent_get_current_version* サービスを使用して、最後に受信した SNMP パケットの SNMP バージョンを取得できます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-299">The SNMP Agent can retrieve the SNMP version of the latest SNMP packet received using the *nx_snmp_agent_get_current_version* service.</span></span>

## <a name="snmpv3-discovery"></a><span data-ttu-id="4fbeb-300">SNMPv3 検出</span><span class="sxs-lookup"><span data-stu-id="4fbeb-300">SNMPv3 Discovery</span></span>

<span data-ttu-id="4fbeb-301">SNMPv3 に対して SNMP エージェントが有効にあっている場合、このエージェントは SNMP マネージャーの検出要求に応答します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-301">The SNMP Agent, if enabled for SNMPv3, will respond to discovery requests from the SNMP Manager.</span></span> <span data-ttu-id="4fbeb-302">この種の要求のセキュリティ パラメーターのデータでは、認証エンジン ID、ユーザー名、ブート回数、ブート時間の値が NULL になっています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-302">Such a request contains security parameter data with null values for Authoritative Engine ID, user name, boot count and boot time.</span></span> <span data-ttu-id="4fbeb-303">認証パラメーターは DISCOVERY メッセージには適用されません。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-303">Authentication parameters are not applied to the DISCOVERY message.</span></span> <span data-ttu-id="4fbeb-304">要求の変数バインド リストは空です (リストには 1 つも項目がありません)。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-304">The variable binding list in the request is empty (contains zero items).</span></span> <span data-ttu-id="4fbeb-305">SNMP エージェントは、値が 0 のブート時間とブート回数、項目 1 つを含む変数バインド リスト *usmStatsUnknownEngineIDs* で応答します。これは、エンジン ID が不明 (NULL) の要求を受信した回数を表します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-305">The SNMP agent responds with a zero boot time and count, and the variable binding list containing 1 item, *usmStatsUnknownEngineIDs*, which is the count of requests received with an unknown (null) engine ID.</span></span> <span data-ttu-id="4fbeb-306">それに続いて GETNEXT 要求をブラウザー/マネージャーから受け取ると、セキュリティが有効である場合に限り、ブートのデータとセキュリティ パラメーターが用意されます。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-306">On the subsequent GETNEXT request from the Browser/Manager, the boot data and security parameters are filled in only if security is enabled.</span></span> <span data-ttu-id="4fbeb-307">その場合、最新の NotInTime データもPDU に入れて送信します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-307">If so it will also send a NotInTime data update in the PDU.</span></span> <span data-ttu-id="4fbeb-308">認証などのセキュリティ パラメーターにより、エージェントの ID をマネージャーに証明します。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-308">The security parameters, e.g. authentication prove the identity of the Agent to the Manager.</span></span>

<span data-ttu-id="4fbeb-309">SNMPv3 認証の詳しい情報は、RFC 3414 の「User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)」(SNMPv3 のユーザー ベース セキュリティ モデル (USM))をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-309">More detailed information on SNMPv3 authentication is available in RFC 3414 “User-based Security Model (USM) for version 3 of the Simple Network Management Protocol (SNMPv3)”.</span></span>

## <a name="netx-duo-snmp-rfcs"></a><span data-ttu-id="4fbeb-310">NetX Duo SNMP に関連する RFC</span><span class="sxs-lookup"><span data-stu-id="4fbeb-310">NetX Duo SNMP RFCs</span></span>

<span data-ttu-id="4fbeb-311">NetX Duo SNMP は、RFC1155、RFC1157、RFC1215、RFC1901、RFC1905、RFC1906、RFC1907、RFC1908、RFC2571、RFC2572、RFC2574、RFC2575、RFC 3414、および関連するその他の RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="4fbeb-311">NetX Duo SNMP is compliant with RFC1155, RFC1157, RFC1215, RFC1901, RFC1905, RFC1906, RFC1907, RFC1908, RFC2571, RFC2572, RFC2574, RFC2575, RFC 3414 and related RFCs.</span></span>
