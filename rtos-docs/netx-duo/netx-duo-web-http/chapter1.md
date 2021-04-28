---
title: 第 1 章 - HTTP と HTTPS の概要
description: この章では、Azure RTOS NetX Duo HTTP/HTTPS for Web モジュールの概要について説明します。
author: philmea
ms.author: philmea
ms.date: 07/24/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: c784843e4d3f11ee306e866223c0a19bfcba3b85
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811810"
---
# <a name="chapter-1---introduction-to-http-and-https"></a><span data-ttu-id="d912d-103">第 1 章 - HTTP と HTTPS の概要</span><span class="sxs-lookup"><span data-stu-id="d912d-103">Chapter 1 - Introduction to HTTP and HTTPS</span></span>

<span data-ttu-id="d912d-104">ハイパーテキスト転送プロトコル (HTTP) は、Web 上でコンテンツを転送するために設計されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="d912d-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="d912d-105">HTTP は、信頼性の高い伝送制御プロトコル (TCP) サービスを利用してコンテンツ転送機能を実行する単純なプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="d912d-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="d912d-106">そのため、HTTP は信頼性の高いコンテンツ転送プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="d912d-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="d912d-107">HTTP は、最も使用されているアプリケーション プロトコルの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="d912d-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="d912d-108">Web 上のすべての操作で HTTP プロトコルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-108">All operations on the Web utilize the HTTP protocol.</span></span>

<span data-ttu-id="d912d-109">HTTPS は、HTTP プロトコルのセキュリティで保護されたバージョンです。これは、基盤となる TCP 接続をセキュリティで保護するためにトランスポート層セキュリティ (TLS) を使用して HTTP を実装します。</span><span class="sxs-lookup"><span data-stu-id="d912d-109">HTTPS is the secure version of the HTTP protocol, which implements HTTP using Transport Layer Security (TLS) to secure the underlying TCP connection.</span></span> <span data-ttu-id="d912d-110">TLS のセットアップに必要な追加の構成を除き、HTTPS の使用方法は基本的に HTTP と同じです。</span><span class="sxs-lookup"><span data-stu-id="d912d-110">Other than the additional configuration required to set up TLS, HTTPS is basically identical to HTTP in use.</span></span>

## <a name="general-http-requirements"></a><span data-ttu-id="d912d-111">HTTP の一般的な要件</span><span class="sxs-lookup"><span data-stu-id="d912d-111">General HTTP Requirements</span></span>

<span data-ttu-id="d912d-112">NetX Web HTTP パッケージを正常に機能させるためには、NetX Duo (バージョン 5.10 以降) がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-112">In order to function properly, the NetX Web HTTP package requires that NetX Duo (version 5.10 or later) is installed.</span></span> <span data-ttu-id="d912d-113">また、IP インスタンスを作成する必要があり、その同じ IP インスタンスで TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-113">In addition, an IP instance must be created, and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="d912d-114">HTTPS をサポートするには、NetX Secure TLS (バージョン 5.11 以降) もインストールする必要があります (次のセクションを参照)。</span><span class="sxs-lookup"><span data-stu-id="d912d-114">For HTTPS support, NetX Secure TLS (version 5.11 or later) must also be installed (see next section).</span></span> <span data-ttu-id="d912d-115">**第 2 章** の「小規模システムの例」セクションのデモ ファイルでは、この方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-115">The demo file in section “Small Example System” in **Chapter 2** demonstrates how this is done.</span></span>

<span data-ttu-id="d912d-116">NetX Web HTTP パッケージの HTTP Client の部分には、その他の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-116">The HTTP Client portion of the NetX Web HTTP package has no further requirements.</span></span>

<span data-ttu-id="d912d-117">NetX Web HTTP パッケージの HTTP Server の部分には、いくつかの追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-117">The HTTP Server portion of the NetX Web HTTP package has several additional requirements.</span></span> <span data-ttu-id="d912d-118">まず、すべてのクライアント HTTP 要求を処理するために、TCP の "*ウェルノウンポート 80*" に完全にアクセスできる必要があります (これは、アプリケーションによって他の有効な TCP ポートに変更される可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="d912d-118">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests (this can be changed by the application to any other valid TCP port).</span></span> <span data-ttu-id="d912d-119">また、HTTP Server は、FileX 埋め込みファイル システムで使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-119">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="d912d-120">FileX を使用できない場合、ユーザーは、使用される FileX の部分を自分の環境に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="d912d-120">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="d912d-121">これについては、このガイドの後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="d912d-121">This is discussed in later sections of this guide.</span></span>

## <a name="https-requirements"></a><span data-ttu-id="d912d-122">HTTPS の要件</span><span class="sxs-lookup"><span data-stu-id="d912d-122">HTTPS Requirements</span></span>

<span data-ttu-id="d912d-123">HTTPS を正常に機能されるために、NetX Web HTTP パッケージでは NetX Duo (バージョン 5.10 以降) と NetX Secure TLS (バージョン 5.11 以降) の両方がインストールされていることが求められます。</span><span class="sxs-lookup"><span data-stu-id="d912d-123">For HTTPS to function properly, the NetX Web HTTP package requires that NetX Duo (version 5.10 or later) and NetX Secure TLS (version 5.11 or later) are both installed.</span></span> <span data-ttu-id="d912d-124">また、IP インスタンスを作成する必要があり、TLS で使用するために、その同じ IP インスタンスで TCP を有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-124">In addition, an IP instance must be created, and TCP must be enabled on that same IP instance for use with TLS.</span></span> <span data-ttu-id="d912d-125">TLS セッションは、適切な暗号化ルーチンと信頼された CA 証明書を使用して初期化する必要があります。また、TLS ハンドシェイク中にリモート サーバー ホストによって提供される証明書のための領域を割り当てる必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-125">The TLS session will need to be initialized with appropriate cryptographic routines, a trusted CA certificate, and space must be allocated for certificates that will be provided by remote server hosts during the TLS handshake.</span></span> <span data-ttu-id="d912d-126">**第 2 章** の「小さな HTTPS システムの例」セクションのデモ ファイルでは、この方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-126">The demo file in section “Small Example HTTPS System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="d912d-127">NetX Web HTTP パッケージの HTTPS Client の部分には、その他の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-127">The HTTPS Client portion of the NetX Web HTTP package has no further requirements.</span></span>

<span data-ttu-id="d912d-128">NetX Web HTTP パッケージの HTTPS Server の部分には、いくつかの追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-128">The HTTPS Server portion of the NetX Web HTTP package has several additional requirements.</span></span> <span data-ttu-id="d912d-129">まず、すべてのクライアント HTTPS 要求を処理するために、TCP の "*ウェルノウンポート 443*" に完全にアクセスできる必要があります (プレーンテキスト HTTP と同様に、このポートはアプリケーションによって変更される可能性があります)。</span><span class="sxs-lookup"><span data-stu-id="d912d-129">First, it requires complete access to TCP *well-known port 443* for handling all Client HTTPS requests (as with plaintext HTTP, this port can be changed by the application).</span></span> <span data-ttu-id="d912d-130">次に、TLS セッションは、適切な暗号化ルーチンとサーバー ID 証明書 (または事前共有キー) を使用して初期化する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-130">Second, the TLS session will need to be initialized with proper cryptographic routines and a server identity certificate (or Pre-Shared Key).</span></span> <span data-ttu-id="d912d-131">また、HTTPS Server は、FileX 埋め込みファイル システムで使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-131">The HTTPS Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="d912d-132">FileX を使用できない場合、ユーザーは、使用される FileX の部分を自分の環境に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="d912d-132">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="d912d-133">FileX の使用については、このガイドの後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="d912d-133">The use of FileX is discussed in later sections of this guide.</span></span>

<span data-ttu-id="d912d-134">TLS の構成オプションの詳細については、NetX Secure のドキュメントを参照してください。</span><span class="sxs-lookup"><span data-stu-id="d912d-134">Refer to the NetX Secure documentation for more information on configuration options for TLS.</span></span>

<span data-ttu-id="d912d-135">このドキュメントで説明されているすべての HTTP 機能は、特に記載のない限り、HTTPS にも適用されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-135">Unless noted, all HTTP functionality described in this document also applies to HTTPS.</span></span>

## <a name="http-and-https-constraints"></a><span data-ttu-id="d912d-136">HTTP および HTTPS の制約</span><span class="sxs-lookup"><span data-stu-id="d912d-136">HTTP and HTTPS Constraints</span></span>

<span data-ttu-id="d912d-137">NetX Web HTTP では、HTTP 1.1 標準が実装されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-137">NetX Web HTTP implements the HTTP 1.1 standard.</span></span> <span data-ttu-id="d912d-138">ただし、次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-138">However, here are following constraints:</span></span>

1. <span data-ttu-id="d912d-139">要求パイプライン処理はサポートされません</span><span class="sxs-lookup"><span data-stu-id="d912d-139">Request pipelining is not supported</span></span>
1. <span data-ttu-id="d912d-140">HTTP Server では、基本認証と MD5 ダイジェスト認証の両方がサポートされますが、MD5-sess はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d912d-140">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="d912d-141">現時点では、HTTP Client では基本認証のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d912d-141">At present, the HTTP Client supports only basic authentication.</span></span> <span data-ttu-id="d912d-142">HTTPS のために TLS を使用する場合でも、HTTP 認証を使用できます。</span><span class="sxs-lookup"><span data-stu-id="d912d-142">When using TLS for HTTPS, HTTP authentication may still be used.</span></span>
1. <span data-ttu-id="d912d-143">コンテンツの圧縮はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d912d-143">No content compression is supported.</span></span>
1. <span data-ttu-id="d912d-144">TRACE、OPTIONS、CONNECT 要求はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="d912d-144">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>
1. <span data-ttu-id="d912d-145">HTTP Server またはクライアントに関連付けられるパケット プールは、完全な HTTP ヘッダーを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-145">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>
1. <span data-ttu-id="d912d-146">HTTP Client サービスは、コンテンツの転送のみを対象としています。このパッケージでは、表示ユーティリティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="d912d-146">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="d912d-147">HTTP の URL (リソース名)</span><span class="sxs-lookup"><span data-stu-id="d912d-147">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="d912d-148">HTTP プロトコルは、Web 上でコンテンツを転送するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-148">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="d912d-149">要求されるコンテンツは、ユニバーサル リソース ロケーター (URL) によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-149">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="d912d-150">これは、すべての HTTP 要求の主要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="d912d-150">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="d912d-151">URL は必ず "/" 文字で始まり、通常は HTTP Server 上のファイルに対応しています。</span><span class="sxs-lookup"><span data-stu-id="d912d-151">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="d912d-152">一般的な HTTP ファイルの拡張子を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="d912d-152">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="d912d-153">**.htm** (または **.html**) ハイパーテキスト マークアップ言語 (HTML)</span><span class="sxs-lookup"><span data-stu-id="d912d-153">**.htm** (or **.html**) Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="d912d-154">**.txt** プレーン ASCII テキスト</span><span class="sxs-lookup"><span data-stu-id="d912d-154">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="d912d-155">**.gif** バイナリ GIF イメージ</span><span class="sxs-lookup"><span data-stu-id="d912d-155">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="d912d-156">**.xbm** バイナリ Xbitmap イメージ</span><span class="sxs-lookup"><span data-stu-id="d912d-156">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="d912d-157">HTTP Client の要求</span><span class="sxs-lookup"><span data-stu-id="d912d-157">HTTP Client Requests</span></span>

<span data-ttu-id="d912d-158">HTTP には、Web コンテンツを要求するための単純なメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="d912d-158">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="d912d-159">TCP の "*ウェルノウン ポート 80 (HTTPS の場合はポート 443)* " で接続が正常に確立された後に、クライアントによって発行される標準の一連の HTTP コマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="d912d-159">There is a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80 (port 443 for HTTPS)*.</span></span> <span data-ttu-id="d912d-160">基本的な HTTP コマンドの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d912d-160">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="d912d-161">**GET *resource* HTTP/1.1** 指定されたリソースを取得します</span><span class="sxs-lookup"><span data-stu-id="d912d-161">**GET *resource* HTTP/1.1** Get the specified resource</span></span>
- <span data-ttu-id="d912d-162">**POST *resource* HTTP/1.1** 指定されたリソースを取得し、添付された入力を HTTP Server に渡します</span><span class="sxs-lookup"><span data-stu-id="d912d-162">**POST *resource* HTTP/1.1** Get the specified resource and pass attached input to the HTTP Server</span></span>
- <span data-ttu-id="d912d-163">**HEAD *resource* HTTP/1.1** GET のように扱われますが、コンテンツは HTTP Server によって返されません</span><span class="sxs-lookup"><span data-stu-id="d912d-163">**HEAD *resource* HTTP/1.1** Treated like a GET but not content is returned by the HTTP Server</span></span>
- <span data-ttu-id="d912d-164">**PUT *resource* HTTP/1.1** HTTP Server にリソースを配置します</span><span class="sxs-lookup"><span data-stu-id="d912d-164">**PUT *resource* HTTP/1.1** Place resource on HTTP Server</span></span>
- <span data-ttu-id="d912d-165">**DELETE *resource* HTTP/1.1** HTTP Server 上のリソースを削除します</span><span class="sxs-lookup"><span data-stu-id="d912d-165">**DELETE *resource* HTTP/1.1** Delete resource on the Server</span></span>

<span data-ttu-id="d912d-166">これらの ASCII コマンドは、HTTP Server で HTTP 操作を実行するために、Web ブラウザーと NetX Web HTTP Client サービスによって内部的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-166">These ASCII commands are generated internally by Web browsers and the NetX Web HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

<span data-ttu-id="d912d-167">HTTP Client アプリケーションでは、ポート 80 (HTTPS を使用する場合は、ポート 443) を使用する必要があることに注意してください。</span><span class="sxs-lookup"><span data-stu-id="d912d-167">Note that the HTTP Client application should use port 80, or port 443 if HTTPS is used.</span></span> <span data-ttu-id="d912d-168">クライアントとサーバーの両方の HTTP API では、パラメーターとしてポートを受け取ります。マクロ NX_WEB_HTTP_SERVER_PORT (ポート 80) と NX_WEB_HTTPS_SERVER_PORT (ポート 443) は、利便性のために定義されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-168">Both the Client and Server HTTP APIs take the port as a parameter – the macros NX_WEB_HTTP_SERVER_PORT (port 80) and NX_WEB_HTTPS_SERVER_PORT (port 443) are defined for convenience.</span></span> <span data-ttu-id="d912d-169">HTTP Server のポートは、*nx_web_http_client_set_connect_port()* サービスを使用して実行時に変更することもできます。</span><span class="sxs-lookup"><span data-stu-id="d912d-169">The HTTP Server port can also be changed at runtime using the *nx_web_http_client_set_connect_port()* service.</span></span> <span data-ttu-id="d912d-170">このサービスの詳細については、第 4 章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d912d-170">See Chapter 4 for more details on this service.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="d912d-171">HTTP Server の応答</span><span class="sxs-lookup"><span data-stu-id="d912d-171">HTTP Server Responses</span></span>

<span data-ttu-id="d912d-172">HTTP Server では、同じ "*ウェルノウン TCP ポート 80 (HTTPS の場合は 443)* " を使用して、クライアント コマンドの応答を送信します。</span><span class="sxs-lookup"><span data-stu-id="d912d-172">The HTTP Server utilizes the same *well-known TCP port 80 (443 for HTTPS)* to send Client command responses.</span></span> <span data-ttu-id="d912d-173">HTTP Server でクライアント コマンドが処理されると、3 桁の数値のステータス コードを含む ASCII 応答文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-173">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="d912d-174">この数値の応答は、操作が成功したかまたは失敗したかを判断するために、HTTP Client ソフトウェアによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-174">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="d912d-175">クライアント コマンドに対するさまざまな HTTP Server の応答の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="d912d-175">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="d912d-176">**200** 要求は成功しました</span><span class="sxs-lookup"><span data-stu-id="d912d-176">**200** Request was successful</span></span>
- <span data-ttu-id="d912d-177">**400** 要求の形式が正しくありませんでした</span><span class="sxs-lookup"><span data-stu-id="d912d-177">**400** Request was not formed properly</span></span>
- <span data-ttu-id="d912d-178">**401** 認可されていない要求。クライアントは認証を送信する必要があります</span><span class="sxs-lookup"><span data-stu-id="d912d-178">**401** Unauthorized request, client needs to send authentication</span></span>
- <span data-ttu-id="d912d-179">**404** 要求に指定されたリソースが見つかりませんでした</span><span class="sxs-lookup"><span data-stu-id="d912d-179">**404** Specified resource in request was not found</span></span>
- <span data-ttu-id="d912d-180">**500** 内部 HTTP Server エラー</span><span class="sxs-lookup"><span data-stu-id="d912d-180">**500** Internal HTTP Server error</span></span>
- <span data-ttu-id="d912d-181">**501** HTTP Server によって要求が実装されていません</span><span class="sxs-lookup"><span data-stu-id="d912d-181">**501** Request not implemented by HTTP Server</span></span>
- <span data-ttu-id="d912d-182">**502** サービスを利用できません</span><span class="sxs-lookup"><span data-stu-id="d912d-182">**502** Service is not available</span></span>

<span data-ttu-id="d912d-183">たとえば、ファイル "test.htm" を PUT するクライアント要求が成功すると、"HTTP/1.1 200 OK" というメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-183">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.1 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="d912d-184">HTTP 通信</span><span class="sxs-lookup"><span data-stu-id="d912d-184">HTTP Communication</span></span>

<span data-ttu-id="d912d-185">前述のように、HTTP Server では "*ウェルノウン TCP ポート 80 (HTTPS の場合は 443)* " を使用して、クライアント要求が処理されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-185">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80 (443 for HTTPS)* to field Client requests.</span></span> <span data-ttu-id="d912d-186">HTTP Client では、送信接続に使用可能な任意の TCP ポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="d912d-186">HTTP Clients may use any available TCP port for outgoing connections.</span></span> <span data-ttu-id="d912d-187">HTTP イベントの一般的な順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="d912d-187">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="d912d-188">**HTTP GET 要求**:</span><span class="sxs-lookup"><span data-stu-id="d912d-188">**HTTP GET Request**:</span></span>

1. <span data-ttu-id="d912d-189">クライアントによって、サーバー ポート 80 (HTTPS の場合は 443) に対して TCP 接続が発行されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-189">Client issues TCP connect to Server port 80 (or 443 for HTTPS).</span></span>
1. <span data-ttu-id="d912d-190">HTTPS が使用されている場合は、TCP 接続の後に TLS ハンドシェイクが行われ、サーバーが認証されて、セキュリティで保護されたチャネルが確立されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-190">If HTTPS is being used, the TCP connection is followed by a TLS handshake to authenticate the server and establish a secure channel.</span></span>
1. <span data-ttu-id="d912d-191">クライアントによって、"**GET *resource* HTTP/1.1**" 要求が (他のヘッダー情報と共に) 送信されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-191">Client sends “**GET *resource* HTTP/1.1**” request (along with other header information).</span></span>
1. <span data-ttu-id="d912d-192">サーバーによって、"**HTTP/1.1 200 OK**" メッセージが追加情報とその直後のリソース コンテンツ (存在する場合) と共に作成されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-192">Server builds an “**HTTP/1.1 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>
1. <span data-ttu-id="d912d-193">サーバーがクライアントから切断されます (HTTPS が使用されている場合は、TLS が停止されます)。</span><span class="sxs-lookup"><span data-stu-id="d912d-193">Server disconnects from the client (TLS is shut down if HTTPS is being used).</span></span>
1. <span data-ttu-id="d912d-194">クライアントがソケットから切断されます (サーバーからの切断アラートの後に、TLS が停止されます)。</span><span class="sxs-lookup"><span data-stu-id="d912d-194">Client disconnects from the socket (TLS is shut down following the disconnection alert from the server).</span></span>

<span data-ttu-id="d912d-195">**HTTP PUT 要求**:</span><span class="sxs-lookup"><span data-stu-id="d912d-195">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="d912d-196">クライアントによって、サーバー ポート 80 (または 443) に対して TCP 接続が発行されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-196">Client issues TCP connect to Server port 80 (or 443).</span></span>
1. <span data-ttu-id="d912d-197">HTTPS が使用されている場合は、TCP 接続の後に TLS ハンドシェイクが行われ、サーバーが認証されて、セキュリティで保護されたチャネルが確立されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-197">If HTTPS is being used, the TCP connection is followed by a TLS handshake to authenticate the server and establish a secure channel.</span></span>
1. <span data-ttu-id="d912d-198">クライアントでは、"PUT resource HTTP/1.1" 要求を他のヘッダー情報とそれに続くリソース コンテンツと共に送信します。</span><span class="sxs-lookup"><span data-stu-id="d912d-198">Client sends “PUT resource HTTP/1.1” request, along with other header information, and followed by the resource content.</span></span>
1. <span data-ttu-id="d912d-199">サーバーでは、"HTTP/1.1 200 OK" メッセージを追加情報とその直後に続くリソース コンテンツと共に作成します。</span><span class="sxs-lookup"><span data-stu-id="d912d-199">Server builds an “HTTP/1.1 200 OK” message with additional information followed immediately by the resource content.</span></span>
1. <span data-ttu-id="d912d-200">サーバーによって切断が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-200">Server performs a disconnection.</span></span>
1. <span data-ttu-id="d912d-201">クライアントによって切断が実行されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-201">Client performs a disconnection.</span></span>

> [!NOTE]
> <span data-ttu-id="d912d-202">前に説明したように、HTTP Server では、別のポートを使用してクライアントに接続する Web サーバーのために、*nx_web_http_client_set_connect_port()* を使用して実行時に既定の接続ポート (80 または 443) を変更できます。</span><span class="sxs-lookup"><span data-stu-id="d912d-202">As mentioned previously, the HTTP Server can change the default connect port (80 or 443) at runtime another port using the *nx_web_http_client_set_connect_port()* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="d912d-203">HTTP 認証</span><span class="sxs-lookup"><span data-stu-id="d912d-203">HTTP Authentication</span></span>

<span data-ttu-id="d912d-204">HTTP 認証は省略可能であり、すべての Web 要求に必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-204">HTTP authentication is optional and is not required for all Web requests.</span></span> <span data-ttu-id="d912d-205">認証には、"*基本*" と "*ダイジェスト*" の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-205">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="d912d-206">基本認証は、多くのプロトコルで使用されている "*名前*" と "*パスワード*" の認証に相当します。</span><span class="sxs-lookup"><span data-stu-id="d912d-206">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="d912d-207">HTTP 基本認証では、名前とパスワードが連結されて base64 形式でエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="d912d-207">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="d912d-208">基本認証の主な短所は、名前とパスワードが要求でオープンに送信されることです。</span><span class="sxs-lookup"><span data-stu-id="d912d-208">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="d912d-209">これにより、名前とパスワードの傍受がいくらか簡単になります。</span><span class="sxs-lookup"><span data-stu-id="d912d-209">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="d912d-210">ダイジェスト認証では、要求で名前とパスワードを送信しないことによって、この問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="d912d-210">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="d912d-211">代わりに、アルゴリズムを使用して、名前、パスワード、およびその他の情報から 128 ビットのダイジェストを導出します。</span><span class="sxs-lookup"><span data-stu-id="d912d-211">Instead, an algorithm is used to derive a 128-bit digest from the name, password, and other information.</span></span> <span data-ttu-id="d912d-212">NetX Web HTTP Server では、標準の MD5 ダイジェスト アルゴリズムがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d912d-212">The NetX Web HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="d912d-213">認証はいつ必要になるのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="d912d-213">When is authentication required?</span></span> <span data-ttu-id="d912d-214">HTTP Server では、要求されたリソースで認証が必要とされるかどうかを判断します。</span><span class="sxs-lookup"><span data-stu-id="d912d-214">The HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="d912d-215">認証が必要で、クライアント要求に適切な認証が含まれていない場合は、"HTTP/1.1 401 未認可" の応答が必要な認証の種類と共にクライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-215">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.1 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="d912d-216">クライアントによって適切な認証を使用した新しい要求が作成されることが予期されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-216">The Client is then expected to form a new request with the proper authentication.</span></span>

<span data-ttu-id="d912d-217">HTTPS が使用される場合、HTTPS Server でも HTTP 認証を利用できます。</span><span class="sxs-lookup"><span data-stu-id="d912d-217">When HTTPS is used, the HTTPS Server can still utilize HTTP authentication.</span></span> <span data-ttu-id="d912d-218">この場合、TLS を使用してすべての HTTP トラフィックが暗号化されるため、HTTP の "*基本*" 認証を使用してもセキュリティ上のリスクはありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-218">In this case, TLS is used to encrypt all HTTP traffic so using *basic* HTTP authentication does not pose a security risk.</span></span> <span data-ttu-id="d912d-219">"*ダイジェスト*" 認証も使用できますが、TLS 経由の基本認証よりもセキュリティが大幅に向上することはありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-219">*Digest* authentication is also permitted but provides no significant security improvement over basic authentication over TLS.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="d912d-220">HTTP 認証コールバック</span><span class="sxs-lookup"><span data-stu-id="d912d-220">HTTP Authentication Callback</span></span>

<span data-ttu-id="d912d-221">前述のように、HTTP 認証は省略可能であり、すべての Web 転送で必要とされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-221">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="d912d-222">また、通常、認証はリソースに依存します。</span><span class="sxs-lookup"><span data-stu-id="d912d-222">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="d912d-223">サーバー上の一部のリソースに対するアクセスでは認証が必要となりますが、他のリソースでは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="d912d-223">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="d912d-224">NetX Web HTTP Server パッケージでは、アプリケーションで、各 HTTP Client 要求の処理の開始時に呼び出される認証コールバック ルーチンを (***nx_web_http_server_create*** 呼び出しを使用して) 指定できます。</span><span class="sxs-lookup"><span data-stu-id="d912d-224">The NetX Web HTTP Server package allows the application to specify (via the ***nx_web_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="d912d-225">このコールバック ルーチンによって、リソースに関連付けられているユーザー名、パスワード、領域の文字列が NetX Web HTTP Server に提供され、必要な認証の種類が返されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-225">The callback routine provides the NetX Web HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="d912d-226">リソースに対して認証が必要ない場合は、認証コールバックによって **NX_WEB_HTTP_DONT_AUTHENTICATE** が値として返されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-226">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_WEB_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="d912d-227">それ以外の場合で、指定されたリソースに対して基本認証が必要なときは、このルーチンによって **NX_WEB_HTTP_BASIC_AUTHENTICATE** が返されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-227">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_WEB_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="d912d-228">最後に、MD5 ダイジェスト認証が必要な場合は、このコールバック ルーチンによって **NX_WEB_HTTP_DIGEST_AUTHENTICATE** が返されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-228">And finally, if MD5 digest authentication is required, the callback routine should return **NX_WEB_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="d912d-229">HTTP Server によって提供されるリソースに対して認証が不要な場合、このコールバックは必要ありません。また、HTTP Server の作成呼び出しに NULL ポインターを渡すこともできます。</span><span class="sxs-lookup"><span data-stu-id="d912d-229">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed, and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="d912d-230">アプリケーション認証のコールバック ルーチンの形式は非常に単純で、以下のように定義します。</span><span class="sxs-lookup"><span data-stu-id="d912d-230">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```C
UINT nx_web_http_server_authentication_check(NX_WEB_HTTP_SERVER *server_ptr,
    UINT request_type, CHAR *resource,
    CHAR **name, CHAR **password,
    CHAR **realm);
```

<span data-ttu-id="d912d-231">入力パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="d912d-231">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="d912d-232">**request_type** HTTP Client 要求を指定します。有効な要求は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-232">**request_type** Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="d912d-233">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-233">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="d912d-234">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-234">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="d912d-235">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-235">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="d912d-236">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-236">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="d912d-237">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-237">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="d912d-238">**resource** 要求された特定のリソース。</span><span class="sxs-lookup"><span data-stu-id="d912d-238">**resource** Specific resource requested.</span></span>
- <span data-ttu-id="d912d-239">**name** 必要なユーザー名へのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="d912d-239">**name** Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="d912d-240">**password** 必要なパスワードへのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="d912d-240">**password** Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="d912d-241">**realm** この認証の領域へのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="d912d-241">**realm** Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="d912d-242">認証ルーチンの戻り値は、認証が必要かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="d912d-242">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="d912d-243">認証コールバックルーチンによって **NX_WEB_HTTP_DONT_AUTHENTICATE** が返される場合、name、password、realm のポインターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="d912d-243">name, password, and realm pointers are not used if **NX_WEB_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="d912d-244">それ以外の場合、HTTP Server の開発者は、*nx_web_http_server.h* で定義される **NX_WEB_HTTP_MAX_USERNAME** と **NX_WEB_HTTP_MAX_PASSWORD** が、認証コールバックに指定されるユーザー名とパスワードに対して十分な大きさであることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-244">Otherwise the HTTP server developer must ensure that **NX_WEB_HTTP_MAX_USERNAME** and **NX_WEB_HTTP_MAX_PASSWORD** defined in *nx_web_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="d912d-245">これらの両方の既定のサイズは 20 文字です。</span><span class="sxs-lookup"><span data-stu-id="d912d-245">These both have a default size of 20 characters.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="d912d-246">HTTP の無効なユーザー名/パスワードのコールバック</span><span class="sxs-lookup"><span data-stu-id="d912d-246">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="d912d-247">HTTP Server がクライアント要求で無効なユーザー名とパスワードの組み合わせを受け取った場合、NetX Web HTTP Server のオプションの無効なユーザー名/パスワードのコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-247">The optional invalid username/password callback in the NetX Web HTTP Server is invoked if the HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="d912d-248">HTTP Server アプリケーションでコールバックを HTTP Server に登録する場合は、基本認証またはダイジェスト認証のいずれかが *nx_web_http_server_get_process()* 、*nx_web_http_server_put_process()* 、または *nx_web_http_server_delete_process()* で失敗したときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-248">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_web_http_server_get_process()*, in *nx_web_http_server_put_process(),* or *in nx_web_http_server_delete_process().*</span></span>

<span data-ttu-id="d912d-249">HTTP Server にコールバックを登録するには、NetX Web HTTP Server に次のサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d912d-249">To register a callback with the HTTP server, the following service is defined for the NetX Web HTTP Server.</span></span>

```C
UINT nx_web_http_server_invalid_userpassword_notify_set(
    NX_WEB_HTTP_SERVER *http_server_ptr,
    UINT (*invalid_username_password_callback)
        (CHAR *resource, ULONG *client_nx_address,
        UINT request_type));
```

<span data-ttu-id="d912d-250">要求の種類は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="d912d-250">The request types are defined as follows:</span></span>

- <span data-ttu-id="d912d-251">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-251">**NX_WEB_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="d912d-252">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-252">**NX_WEB_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="d912d-253">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-253">**NX_WEB_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="d912d-254">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-254">**NX_WEB_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="d912d-255">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="d912d-255">**NX_WEB_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="d912d-256">HTTP GMT 日付ヘッダー挿入コールバック</span><span class="sxs-lookup"><span data-stu-id="d912d-256">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="d912d-257">NetX Web HTTP Server には、応答メッセージに日付ヘッダーを挿入するためのオプションのコールバックがあります。</span><span class="sxs-lookup"><span data-stu-id="d912d-257">There is an optional callback in the NetX Web HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="d912d-258">このコールバックは、HTTP Server で put または get 要求に応答しているときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-258">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="d912d-259">HTTP Server に GMT 日付コールバックを登録するには、次のサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d912d-259">To register a GMT date callback with the HTTP Server, the following service is defined.</span></span>

```C
UINT nx_web_http_server_gmt_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    VOID (*gmt_get)(NX_WEB_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="d912d-260">NX_WEB_HTTP_SERVER_DATE のデータ型は次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="d912d-260">The NX_WEB_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```C
typedef struct NX_WEB_HTTP_SERVER_DATE_STRUCT
{
    USHORT nx_web_http_server_year; /* Year */
    UCHAR nx_web_http_server_month; /* Month */
    UCHAR nx_web_http_server_day; /* Day */
    UCHAR nx_web_http_server_hour; /* Hour */
    UCHAR nx_web_http_server_minute; /* Minute */
    UCHAR nx_web_http_server_second; /* Second */
    UCHAR nx_web_http_server_weekday; /* Weekday */
} NX_WEB_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="d912d-261">HTTP キャッシュ情報取得コールバック</span><span class="sxs-lookup"><span data-stu-id="d912d-261">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="d912d-262">HTTP Server には、特定のリソースについて HTTP アプリケーションから最大有効期間と日付を要求するためのコールバックがあります。</span><span class="sxs-lookup"><span data-stu-id="d912d-262">The HTTP Server has a callback to request the maximum age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="d912d-263">この情報は、クライアントの Get 要求に応答して、HTTP Server でページ全体を送信するかどうかを判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-263">This information is used to determine if the HTTP server sends an entire page in response to a Client Get request.</span></span> <span data-ttu-id="d912d-264">クライアント要求に "if modified since" が見つからないか、キャッシュ取得コールバックによって返された "最終更新日" の日付と一致しない場合は、ページ全体が送信されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-264">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="d912d-265">HTTP Server にコールバックを登録するには、次のサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="d912d-265">To register the callback with the HTTP server the following service is defined:</span></span>

```C
UINT nx_web_http_server_cache_info_callback_set(
    NX_WEB_HTTP_SERVER *server_ptr,
    UINT (*cache_info_get)
    (CHAR *, UINT *, NX_WEB_HTTP_SERVER_DATE *));
```

## <a name="http-chunked-transfer-coding-support"></a><span data-ttu-id="d912d-266">HTTP チャンク転送コーディングのサポート</span><span class="sxs-lookup"><span data-stu-id="d912d-266">HTTP Chunked Transfer Coding Support</span></span>

<span data-ttu-id="d912d-267">送信する前に HTTP メッセージの合計長を判別できない場合は、チャンク転送コーディング機能を使用して、"Content-length" ヘッダー フィールドなしで一連のチャンクとしてメッセージを送信できます。</span><span class="sxs-lookup"><span data-stu-id="d912d-267">When the total length of HTTP message cannot be determined before sending it, the Chunked Transfer Coding feature can be used to send messages as series of chunks without the “Content-Length” header field.</span></span> <span data-ttu-id="d912d-268">この機能は、すべての HTTP 要求メッセージと応答メッセージでサポートされます。</span><span class="sxs-lookup"><span data-stu-id="d912d-268">This feature is supported in all HTTP request and response messages.</span></span> <span data-ttu-id="d912d-269">受信側では、この機能がサポートされており、チャンク ヘッダーは内部ロジックによって透過的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="d912d-269">As a receiver, this feature is supported, and the chunk header is processed transparently by internal logic.</span></span> <span data-ttu-id="d912d-270">送信側では、API *nx_web_http_client_request_chunked_set* と *nx_web_http_server_response_chunked_set* がクライアントとサーバーによってそれぞれ呼び出される必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-270">As a sender, the API *nx_web_http_client_request_chunked_set* and *nx_web_http_server_response_chunked_set* must be invoked by client and server respectively.</span></span>

```C
UINT nx_web_http_client_request_chunked_set(NX_WEB_HTTP_CLIENT *client_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);

UINT nx_web_http_server_response_chunked_set(NX_WEB_HTTP_SERVER *server_ptr,
    UINT chunk_size,
    NX_PACKET *packet_ptr);
```

<span data-ttu-id="d912d-271">これらのサービスの詳細については、第 3 章「HTTP サービスの説明」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d912d-271">For more details on these services, see their descriptions in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multipart-support"></a><span data-ttu-id="d912d-272">HTTP マルチパートのサポート</span><span class="sxs-lookup"><span data-stu-id="d912d-272">HTTP Multipart Support</span></span>

<span data-ttu-id="d912d-273">Multipurpose Internet Mail Extensions (MIME) は当初は SMTP プロトコルを対象としていましたが、HTTP でも使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="d912d-273">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="d912d-274">MIME を使用すると、同じメッセージ内に混在したメッセージの種類 (image/jpg、text/plain など) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="d912d-274">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="d912d-275">NetX Web HTTP Server には、クライアントからの MIME を含む HTTP メッセージのコンテンツの種類を判別するサービスがあります。</span><span class="sxs-lookup"><span data-stu-id="d912d-275">The NetX Web HTTP Server has services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="d912d-276">HTTP マルチパートのサポートを有効にしてこれらのサービスを使用するには、構成オプション **NX_WEB_HTTP_MULTIPART_ENABLE** を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-276">To enable HTTP multipart support and use these services, the configuration option **NX_WEB_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```C
UINT nx_web_http_server_get_entity_header(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    UCHAR *entity_header_buffer,
    ULONG buffer_size);

UINT nx_web_http_server_get_entity_content(NX_WEB_HTTP_SERVER *server_ptr,
    NX_PACKET **packet_pptr,
    ULONG *available_offset,
    ULONG *available_length);
```

<span data-ttu-id="d912d-277">これらのサービスの使用方法の詳細については、第 3 章「HTTP サービスの説明」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="d912d-277">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="d912d-278">HTTP マルチスレッドのサポート</span><span class="sxs-lookup"><span data-stu-id="d912d-278">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="d912d-279">NetX Web HTTP Client サービスは、複数のスレッドから同時に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="d912d-279">The NetX Web HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="d912d-280">ただし、特定の HTTP Client インスタンスの読み取り要求または書き込み要求は、同じスレッドから順番に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-280">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

<span data-ttu-id="d912d-281">HTTPS を使用する場合、複数のスレッドから NetX Web HTTP Client サービスを呼び出すことができますが、基になる TLS 機能が複雑になるため、各スレッドには独立した HTTP Client インスタンス (NX_WEB_HTTP_CLIENT 制御構造) が 1 つある必要があります。</span><span class="sxs-lookup"><span data-stu-id="d912d-281">If using HTTPS, NetX Web HTTP Client services may be called from multiple threads but due to the added complexity of the underlying TLS functionality each thread should have a single, independent HTTP Client instance (NX_WEB_HTTP_CLIENT control structure).</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="d912d-282">HTTP の RFC</span><span class="sxs-lookup"><span data-stu-id="d912d-282">HTTP RFCs</span></span>

<span data-ttu-id="d912d-283">NetX Web HTTP は、RFC1945 "ハイパーテキスト転送プロトコル/1.0"、RFC 2616 "ハイパーテキスト転送プロトコル – HTTP/1.1"、RFC 2581 "TCP の輻輳制御"、RFC 1122 "インターネット ホストの要件"、および関連する RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="d912d-283">NetX Web HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2616 “Hypertext Transfer Protocol – HTTP/1.1”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>

<span data-ttu-id="d912d-284">HTTPS の場合、NetX Web HTTP は RFC 2818 "HTTP over TLS" に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="d912d-284">For HTTPS, NetX Web HTTP is compliant with RFC 2818 “HTTP over TLS”.</span></span>
