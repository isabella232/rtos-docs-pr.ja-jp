---
title: 第 1 章 - NetX HTTP の概要
description: このドキュメントでは、HTTP が Web 上でコンテンツを転送するために設計されたプロトコルであることについて説明します。
author: philmea
ms.author: philmea
ms.date: 06/08/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 6137cc0d8deb753d784be844d5abc7778dd62295
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811534"
---
# <a name="chapter-1---introduction-to-netx-http"></a><span data-ttu-id="e93d4-103">第 1 章 - NetX HTTP の概要</span><span class="sxs-lookup"><span data-stu-id="e93d4-103">Chapter 1 - Introduction to NetX HTTP</span></span>

<span data-ttu-id="e93d4-104">ハイパーテキスト転送プロトコル (HTTP) は、Web 上でコンテンツを転送するために設計されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-104">The Hypertext Transfer Protocol (HTTP) is a protocol designed for transferring content on the Web.</span></span> <span data-ttu-id="e93d4-105">HTTP は、信頼性の高い伝送制御プロトコル (TCP) サービスを利用してコンテンツ転送機能を実行する単純なプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-105">HTTP is a simple protocol that utilizes reliable Transmission Control Protocol (TCP) services to perform its content transfer function.</span></span> <span data-ttu-id="e93d4-106">そのため、HTTP は信頼性の高いコンテンツ転送プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-106">Because of this, HTTP is a highly reliable content transfer protocol.</span></span> <span data-ttu-id="e93d4-107">HTTP は、最も使用されているアプリケーション プロトコルの 1 つです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-107">HTTP is one of the most used application protocols.</span></span> <span data-ttu-id="e93d4-108">Web 上のすべての操作で HTTP プロトコルが使用されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-108">All operations on the Web utilize the HTTP protocol.</span></span>

## <a name="http-requirements"></a><span data-ttu-id="e93d4-109">HTTP の要件</span><span class="sxs-lookup"><span data-stu-id="e93d4-109">HTTP Requirements</span></span>

<span data-ttu-id="e93d4-110">NetX HTTP パッケージを正常に機能させるためには、NetX (バージョン 5.2 以降) がインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-110">In order to function properly, the NetX HTTP package requires that a NetX (version 5.2 or later) is installed.</span></span> <span data-ttu-id="e93d4-111">また、IP インスタンスが既に作成されている必要があり、その同じ IP インスタンスで TCP が有効にされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-111">In addition, an IP instance must already be created and TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="e93d4-112">**第 2 章** の「小規模のシステム例」セクションのデモ ファイルに、これを実行する方法が示されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-112">The demo file in section “Small Example System” in **Chapter 2** will demonstrate how this is done.</span></span>

<span data-ttu-id="e93d4-113">NetX Web HTTP パッケージの HTTP クライアント部分には、その他の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-113">The HTTP Client portion of the NetX HTTP package has no further requirements.</span></span>

<span data-ttu-id="e93d4-114">NetX HTTP パッケージの HTTP サーバー部分には、いくつかの追加要件があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-114">The HTTP Server portion of the NetX HTTP package has several additional requirements.</span></span> <span data-ttu-id="e93d4-115">まず、クライアントのすべての HTTP 要求を処理するために、TCP の "*ウェルノウン ポート 80*" に完全にアクセスできる必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-115">First, it requires complete access to TCP *well-known port 80* for handling all Client HTTP requests.</span></span> <span data-ttu-id="e93d4-116">また、HTTP サーバーは、FileX 埋め込みファイル システムで使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-116">The HTTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="e93d4-117">FileX を使用できない場合、ユーザーは、使用される FileX の部分を自分の環境に移植することができます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="e93d4-118">これについては、このガイドの後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-118">This is discussed in later sections of this guide.</span></span>

## <a name="http-constraints"></a><span data-ttu-id="e93d4-119">HTTP の制約</span><span class="sxs-lookup"><span data-stu-id="e93d4-119">HTTP Constraints</span></span> 

<span data-ttu-id="e93d4-120">NetX HTTP プロトコルでは、HTTP 1.0 標準が実装されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-120">The NetX HTTP protocol implements the HTTP 1.0 standard.</span></span> <span data-ttu-id="e93d4-121">ただし、次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-121">However, there are following constraints:</span></span>

1.  <span data-ttu-id="e93d4-122">永続的な接続はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-122">Persistent connections are not supported</span></span>

2.  <span data-ttu-id="e93d4-123">要求パイプライン処理はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-123">Request pipelining is not supported</span></span>

3.  <span data-ttu-id="e93d4-124">HTTP サーバーでは、基本認証と MD5 ダイジェスト認証の両方がサポートされますが、MD5-sess はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-124">The HTTP Server supports both basic and MD5 digest authentication, but not MD5-sess.</span></span> <span data-ttu-id="e93d4-125">現時点では、HTTP クライアントでは、基本認証のみがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-125">At present, the HTTP Client supports only basic authentication.</span></span>

4.  <span data-ttu-id="e93d4-126">コンテンツの圧縮はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-126">No content compression is supported.</span></span>

5.  <span data-ttu-id="e93d4-127">TRACE、OPTIONS、CONNECT 要求はサポートされません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-127">TRACE, OPTIONS, and CONNECT requests are not supported.</span></span>

6.  <span data-ttu-id="e93d4-128">HTTP サーバーまたはクライアントに関連付けられるパケット プールは、完全な HTTP ヘッダーを保持するのに十分な大きさである必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-128">The packet pool associated with the HTTP Server or Client must be large enough to hold the complete HTTP header.</span></span>

7.  <span data-ttu-id="e93d4-129">HTTP クライアント サービスは、コンテンツの転送のみを対象としています。このパッケージでは、表示ユーティリティは提供されません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-129">HTTP Client services are for content transfer only—there are no display utilities provided in this package.</span></span>

## <a name="http-url-resource-names"></a><span data-ttu-id="e93d4-130">HTTP の URL (リソース名)</span><span class="sxs-lookup"><span data-stu-id="e93d4-130">HTTP URL (Resource Names)</span></span>

<span data-ttu-id="e93d4-131">HTTP プロトコルは、Web 上でコンテンツを転送するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-131">The HTTP protocol is designed to transfer content on Web.</span></span> <span data-ttu-id="e93d4-132">要求されるコンテンツは、ユニバーサル リソース ロケーター (URL) によって指定されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-132">The requested content is specified by the Universal Resource Locator (URL).</span></span> <span data-ttu-id="e93d4-133">これは、すべての HTTP 要求の主要なコンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-133">This is the primary component of every HTTP request.</span></span> <span data-ttu-id="e93d4-134">URL は必ず "/" 文字で始まり、通常は HTTP サーバー上のファイルに対応しています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-134">URLs always start with a “/” character and typically correspond to files on the HTTP Server.</span></span> <span data-ttu-id="e93d4-135">一般的な HTTP ファイルの拡張子を以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-135">Common HTTP file extensions are shown below:</span></span>

- <span data-ttu-id="e93d4-136">**.htm (または .html)** : ハイパーテキスト マークアップ言語 (HTML)</span><span class="sxs-lookup"><span data-stu-id="e93d4-136">**.htm (or .html)** Hypertext Markup Language (HTML)</span></span>
- <span data-ttu-id="e93d4-137">**.txt**: プレーン ASCII テキスト</span><span class="sxs-lookup"><span data-stu-id="e93d4-137">**.txt** Plain ASCII text</span></span>
- <span data-ttu-id="e93d4-138">**.gif**: バイナリ GIF 画像</span><span class="sxs-lookup"><span data-stu-id="e93d4-138">**.gif** Binary GIF image</span></span>
- <span data-ttu-id="e93d4-139">**.xbm**: バイナリ Xbitmap 画像</span><span class="sxs-lookup"><span data-stu-id="e93d4-139">**.xbm** Binary Xbitmap image</span></span>

## <a name="http-client-requests"></a><span data-ttu-id="e93d4-140">HTTP クライアントの要求</span><span class="sxs-lookup"><span data-stu-id="e93d4-140">HTTP Client Requests</span></span>

<span data-ttu-id="e93d4-141">HTTP には、Web コンテンツを要求するための単純なメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-141">The HTTP has a simple mechanism for requesting Web content.</span></span> <span data-ttu-id="e93d4-142">基本的には、TCP の "*ウェルノウン ポート 80*" で接続が正常に確立された後、クライアントによって発行される一連の標準の HTTP コマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-142">There is basically a set of standard HTTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 80*.</span></span> <span data-ttu-id="e93d4-143">基本的な HTTP コマンドの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-143">The following shows some of the basic HTTP commands:</span></span>

- <span data-ttu-id="e93d4-144">GET resource HTTP/1.0: "*指定されたリソースを取得します*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-144">GET resource HTTP/1.0 *Get the specified resource*</span></span>
- <span data-ttu-id="e93d4-145">POST resource HTTP/1.0: "*指定されたリソースを取得し、添付された入力を HTTP サーバーに渡します*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-145">POST resource HTTP/1.0 *Get the specified resource and pass attached input to the HTTP Server*</span></span>
- <span data-ttu-id="e93d4-146">HEAD resource HTTP/1.0: "*GET のように扱われますが、コンテンツは HTTP サーバーによって返されません*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-146">HEAD resource HTTP/1.0 *Treated like a GET but not content is returned by the HTTP Server*</span></span>
- <span data-ttu-id="e93d4-147">PUT resource HTTP/1.0: "*HTTP サーバーにリソースを配置します*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-147">PUT resource HTTP/1.0 *Place resource on HTTP Server*</span></span>
- <span data-ttu-id="e93d4-148">DELETE resource HTTP/1.0: "*サーバー上のリソースを削除します*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-148">DELETE resource HTTP/1.0 *Delete resource on the Server*</span></span>

<span data-ttu-id="e93d4-149">これらの ASCII コマンドは、HTTP サーバーで HTTP 操作を実行するために、Web ブラウザーと NetX HTTP クライアント サービスによって内部的に生成されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-149">These ASCII commands are generated internally by Web browsers and the NetX HTTP Client services to perform HTTP operations with an HTTP Server.</span></span>

>[!NOTE] 
> <span data-ttu-id="e93d4-150">HTTP クライアント アプリケーションの既定の接続ポートは 80 です。</span><span class="sxs-lookup"><span data-stu-id="e93d4-150">The HTTP Client application default to the connect port of 80.</span></span> <span data-ttu-id="e93d4-151">ただし、*nx_http_client_set_connect_port* サービスを使用して、実行時に HTTP サーバーへの接続ポートを変更できます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-151">However, it can change the connect port to the HTTP Server at runtime using the *nx_http_client_set_connect_port* service.</span></span> <span data-ttu-id="e93d4-152">このサービスの詳細については、第 4 章を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e93d4-152">See Chapter 4 for more details of this service.</span></span> <span data-ttu-id="e93d4-153">これは、クライアント接続に代替ポートを使用する場合がある Web サーバーに対応するためのものです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-153">This is to accommodate web servers that occasionally use alternate ports for Client connections.</span></span>

## <a name="http-server-responses"></a><span data-ttu-id="e93d4-154">HTTP サーバーの応答</span><span class="sxs-lookup"><span data-stu-id="e93d4-154">HTTP Server Responses</span></span>

<span data-ttu-id="e93d4-155">HTTP サーバーでは、同じ "*ウェルノウン TCP ポート 80*" を使用して、クライアント コマンドの応答が送信されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-155">The HTTP Server utilizes the same *well-known TCP port 80* to send Client command responses.</span></span> <span data-ttu-id="e93d4-156">HTTP サーバーでクライアント コマンドが処理されると、3 桁の数値の状態コードを含む ASCII 応答文字列が返されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-156">Once the HTTP Server processes the Client command, it returns an ASCII response string that includes a 3-digit numeric status code.</span></span> <span data-ttu-id="e93d4-157">この数値の応答は、操作が成功したか失敗したかを判断するために、HTTP Client ソフトウェアによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-157">The numeric response is used by the HTTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="e93d4-158">クライアント コマンドに対するさまざまな HTTP サーバーの応答の一覧を次に示します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-158">Following is a list of various HTTP Server responses to Client commands:</span></span>

- <span data-ttu-id="e93d4-159">200: "*要求は成功しました*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-159">200 *Request was successful*</span></span>
- <span data-ttu-id="e93d4-160">400 "*要求の形式が正しくありませんでした*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-160">400 *Request was not formed properly*</span></span>
- <span data-ttu-id="e93d4-161">401 "*承認されていない要求。クライアントは認証を送信する必要があります*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-161">401 *Unauthorized request, client needs to send authentication*</span></span>
- <span data-ttu-id="e93d4-162">404 "*要求に指定されたリソースが見つかりませんでした*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-162">404 *Specified resource in request was not found*</span></span>
- <span data-ttu-id="e93d4-163">500 "*内部 HTTP サーバー エラー*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-163">500 *Internal HTTP Server error*</span></span>
- <span data-ttu-id="e93d4-164">501 "*HTTP サーバーによって要求が実装されていません*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-164">501 *Request not implemented by HTTP Server*</span></span>
- <span data-ttu-id="e93d4-165">502 "*サービスを利用できません*"</span><span class="sxs-lookup"><span data-stu-id="e93d4-165">502 *Service is not available*</span></span>

<span data-ttu-id="e93d4-166">たとえば、ファイル "test.htm" を PUT するクライアント要求が成功すると、"HTTP/1.0 200 OK" というメッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-166">For example, a successful Client request to PUT the file “test.htm” is responded with the message “HTTP/1.0 200 OK.”</span></span>

## <a name="http-communication"></a><span data-ttu-id="e93d4-167">HTTP 通信</span><span class="sxs-lookup"><span data-stu-id="e93d4-167">HTTP Communication</span></span>

<span data-ttu-id="e93d4-168">前述のとおり、HTTP サーバーによるクライアント要求の処理には、*TCP のウェルノウン ポート 80* が使用されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-168">As mentioned previously, the HTTP Server utilizes the *well-known TCP port 80* to field Client requests.</span></span> <span data-ttu-id="e93d4-169">HTTP クライアントでは、使用可能な任意の TCP ポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-169">HTTP Clients may use any available TCP port.</span></span> <span data-ttu-id="e93d4-170">HTTP イベントの一般的な順序は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-170">The general sequence of HTTP events is as follows:</span></span>

<span data-ttu-id="e93d4-171">**HTTP GET 要求**:</span><span class="sxs-lookup"><span data-stu-id="e93d4-171">**HTTP GET Request**:</span></span>

1.  <span data-ttu-id="e93d4-172">クライアントによって、サーバー ポート 80 への TCP 接続が発行されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-172">Client issues TCP connect to Server port 80.</span></span>

2.  <span data-ttu-id="e93d4-173">クライアントによって、"**GET resource HTTP/1.0**" 要求が (他のヘッダー情報と共に) 送信されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-173">Client sends “**GET resource HTTP/1.0**” request (along with other header information).</span></span>

3.  <span data-ttu-id="e93d4-174">サーバーによって、"**HTTP/1.0 200 OK**" メッセージ、追加情報、およびその直後に続くリソース コンテンツ (存在する場合) が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-174">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content (if any).</span></span>

4.  <span data-ttu-id="e93d4-175">サーバーによって切断が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-175">Server performs a disconnection.</span></span>

5.  <span data-ttu-id="e93d4-176">クライアントによって切断が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-176">Client performs a disconnection.</span></span>

<span data-ttu-id="e93d4-177">**HTTP PUT 要求**:</span><span class="sxs-lookup"><span data-stu-id="e93d4-177">**HTTP PUT Request**:</span></span>

1. <span data-ttu-id="e93d4-178">クライアントによって、サーバー ポート 80 への TCP 接続が発行されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-178">Client issues TCP connect to Server port 80.</span></span>

2. <span data-ttu-id="e93d4-179">クライアントによって、"**PUT resource HTTP/1.0**" 要求、他のヘッダー情報、およびそれに続くリソース コンテンツが送信されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-179">Client sends “**PUT resource HTTP/1.0**” request, along with other header information, and followed by the resource content.</span></span>

3. <span data-ttu-id="e93d4-180">サーバーによって、"**HTTP/1.0 200 OK**" メッセージ、追加情報、およびその直後に続くリソース コンテンツが作成されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-180">Server builds an “**HTTP/1.0 200 OK**” message with additional information followed immediately by the resource content.</span></span>

4. <span data-ttu-id="e93d4-181">サーバーによって切断が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-181">Server performs a disconnection.</span></span>

5. <span data-ttu-id="e93d4-182">クライアントによって切断が実行されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-182">Client performs a disconnection.</span></span>

>[!NOTE] 
> <span data-ttu-id="e93d4-183">前に説明したように、HTTP クライアントでは、*nx_web_http_client_set_connect_port* を使用して、クライアントへの接続に別のポートを使用する Web サーバーのために既定の接続ポートを 80 から別のポートに変更できます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-183">As mentioned previously, the HTTP Client can change the default connect port from 80 to another port using the *nx_http_client_set_connect_port* for web servers that use alternate ports to connect to clients.</span></span>

## <a name="http-authentication"></a><span data-ttu-id="e93d4-184">HTTP 認証</span><span class="sxs-lookup"><span data-stu-id="e93d4-184">HTTP Authentication</span></span>

<span data-ttu-id="e93d4-185">HTTP 認証は省略可能であり、すべての Web 要求に必須ではありません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-185">HTTP authentication is optional and isn’t required for all Web requests.</span></span> <span data-ttu-id="e93d4-186">認証には、"*基本*" と "*ダイジェスト*" の 2 種類があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-186">There are two flavors of authentication, namely *basic* and *digest*.</span></span> <span data-ttu-id="e93d4-187">基本認証は、多くのプロトコルで使用されている "*名前*" と "*パスワード*" の認証に相当します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-187">Basic authentication is equivalent to the *name* and *password* authentication found in many protocols.</span></span> <span data-ttu-id="e93d4-188">HTTP 基本認証では、名前とパスワードが連結されて base64 形式でエンコードされます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-188">In HTTP basic authentication, the name and passwords are concatenated and encoded in the base64 format.</span></span> <span data-ttu-id="e93d4-189">基本認証の主な短所は、名前とパスワードが要求でオープンに送信されることです。</span><span class="sxs-lookup"><span data-stu-id="e93d4-189">The main disadvantage of basic authentication is the name and password are transmitted openly in the request.</span></span> <span data-ttu-id="e93d4-190">これにより、名前とパスワードの傍受がいくらか簡単になります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-190">This makes it somewhat easy for the name and password to be stolen.</span></span> <span data-ttu-id="e93d4-191">ダイジェスト認証では、要求で名前とパスワードを送信しないことによって、この問題に対処しています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-191">Digest authentication addresses this problem by never transmitting the name and password in the request.</span></span> <span data-ttu-id="e93d4-192">代わりに、アルゴリズムを使用して、名前、パスワード、およびその他の情報から 128 ビットのキー (ダイジェスト) が導出されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-192">Instead, an algorithm is used to derive a 128-bit key or digest from the name, password, and other information.</span></span> <span data-ttu-id="e93d4-193">NetX HTTP サーバーでは、標準の MD5 ダイジェスト アルゴリズムがサポートされています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-193">The NetX HTTP Server supports the standard MD5 digest algorithm.</span></span>

<span data-ttu-id="e93d4-194">認証はいつ必要になるのでしょうか。</span><span class="sxs-lookup"><span data-stu-id="e93d4-194">When is authentication required?</span></span> <span data-ttu-id="e93d4-195">基本的に、要求されたリソースに認証が必要かどうかは、HTTP サーバーが判断します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-195">Basically, the HTTP Server decides if a requested resource requires authentication.</span></span> <span data-ttu-id="e93d4-196">認証が必要なときに、クライアント要求に適切な認証が含まれていなかった場合、"HTTP/1.0 401 未承認" という応答と必要な認証の種類が、クライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-196">If authentication is required and the Client request did not include the proper authentication, a “HTTP/1.0 401 Unauthorized” response with the type of authentication required is sent to the Client.</span></span> <span data-ttu-id="e93d4-197">クライアントによって適切な認証を使用した新しい要求が作成されることが期待されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-197">The Client is then expected to form a new request with the proper authentication.</span></span>

## <a name="http-authentication-callback"></a><span data-ttu-id="e93d4-198">HTTP 認証コールバック</span><span class="sxs-lookup"><span data-stu-id="e93d4-198">HTTP Authentication Callback</span></span>

<span data-ttu-id="e93d4-199">前述のように、HTTP 認証は省略可能であり、すべての Web 転送で必要とされるわけではありません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-199">As mentioned before, HTTP authentication is optional and isn’t required on all Web transfers.</span></span> <span data-ttu-id="e93d4-200">また、通常、認証はリソースに依存します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-200">In addition, authentication is typically resource dependent.</span></span> <span data-ttu-id="e93d4-201">サーバー上の一部のリソースに対するアクセスでは認証が必要となりますが、他のリソースでは必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-201">Access of some resources on the Server require authentication, while others do not.</span></span> <span data-ttu-id="e93d4-202">NetX HTTP サーバー パッケージを使用すると、アプリケーションで、各 HTTP クライアント要求の処理の開始時に呼び出される認証コールバック ルーチンを (***nx_http_server_create*** 呼び出しを使用して) 指定できます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-202">The NetX HTTP Server package allows the application to specify (via the ***nx_http_server_create*** call) an authentication callback routine that is called at the beginning of handling each HTTP Client request.</span></span>

<span data-ttu-id="e93d4-203">このコールバック ルーチンによって、リソースに関連付けられているユーザー名、パスワード、および領域の文字列が NetX HTTP サーバーに提供され、必要な認証の種類が返されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-203">The callback routine provides the NetX HTTP Server with the username, password, and realm strings associated with the resource and return the type of authentication necessary.</span></span> <span data-ttu-id="e93d4-204">リソースに認証が必要ない場合は、認証コールバックによって値 **NX_HTTP_DONT_AUTHENTICATE** が返されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-204">If no authentication is necessary for the resource, the authentication callback should return the value of **NX_HTTP_DONT_AUTHENTICATE**.</span></span> <span data-ttu-id="e93d4-205">それ以外の場合で、指定されたリソースに基本認証が必要な場合は、このルーチンから **NX_HTTP_BASIC_AUTHENTICATE** が返されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-205">Otherwise, if basic authentication is required for the specified resource, the routine should return **NX_HTTP_BASIC_AUTHENTICATE**.</span></span> <span data-ttu-id="e93d4-206">最後に、MD5 ダイジェスト認証が必要な場合は、コールバック ルーチンから **NX_HTTP_DIGEST_AUTHENTICATE** が返されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-206">And finally, if MD5 digest authentication is required, the callback routine should return **NX_HTTP_DIGEST_AUTHENTICATE**.</span></span> <span data-ttu-id="e93d4-207">HTTP サーバーによって提供されるリソースに認証が不要な場合、このコールバックは必要なく、HTTP サーバーの作成呼び出しに NULL ポインターを渡すことができます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-207">If no authentication is required for any resource provided by the HTTP Server, the callback is not needed and a NULL pointer can be provided to the HTTP Server create call.</span></span>

<span data-ttu-id="e93d4-208">アプリケーション認証のコールバック ルーチンの形式は非常に単純で、以下のように定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-208">The format of the application authenticate callback routine is very simple and is defined below:</span></span>

```c
UINT nx_http_server_authentication_check (NX_HTTP_SERVER *server_ptr,
                                         UINT request_type, CHAR *resource,
                                         CHAR **name, CHAR **password,
                                         CHAR **realm);
```

<span data-ttu-id="e93d4-209">入力パラメーターは次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-209">The input parameters are defined as follows:</span></span>

- <span data-ttu-id="e93d4-210">*request_type*: HTTP クライアント要求を指定します。有効な要求は次のように定義されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-210">*request_type* Specifies the HTTP Client request, valid requests are defined as:</span></span>
  - <span data-ttu-id="e93d4-211">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-211">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
  - <span data-ttu-id="e93d4-212">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-212">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
  - <span data-ttu-id="e93d4-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-213">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
  - <span data-ttu-id="e93d4-214">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-214">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
  - <span data-ttu-id="e93d4-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-215">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>
- <span data-ttu-id="e93d4-216">*resource*: 要求された特定のリソース。</span><span class="sxs-lookup"><span data-stu-id="e93d4-216">*resource* Specific resource requested.</span></span>
- <span data-ttu-id="e93d4-217">*name*: 必要なユーザー名へのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="e93d4-217">*name* Destination for the pointer to the required username.</span></span>
- <span data-ttu-id="e93d4-218">*password*: 必要なパスワードへのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="e93d4-218">*password* Destination for the pointer to the required password.</span></span>
- <span data-ttu-id="e93d4-219">*realm*: この認証の領域へのポインターの宛先。</span><span class="sxs-lookup"><span data-stu-id="e93d4-219">*realm* Destination for the pointer to the realm for this authentication.</span></span>

<span data-ttu-id="e93d4-220">認証ルーチンの戻り値は、認証が必要かどうかを示します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-220">The return value of the authentication routine specifies if authentication is required.</span></span> <span data-ttu-id="e93d4-221">認証コールバック ルーチンによって **NX_HTTP_DONT_AUTHENTICATE** が返される場合、name、password、および realm ポインターは使用されません。</span><span class="sxs-lookup"><span data-stu-id="e93d4-221">name, password, and realm pointers are not used if **NX_HTTP_DONT_AUTHENTICATE** is returned by the authentication callback routine.</span></span> <span data-ttu-id="e93d4-222">それ以外の場合、HTTP サーバー開発者は、*nxd_http_server.h* で定義されている **NX_HTTP_MAX_USERNAME** と **NX_HTTP_MAX_PASSWORD** が、認証コールバックで指定されるユーザー名とパスワードに十分な大きさであることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-222">Otherwise the HTTP server developer must ensure that **NX_HTTP_MAX_USERNAME** and **NX_HTTP_MAX_PASSWORD** defined in *nx_http_server.h* are large enough for the username and password specified in the authentication callback.</span></span> <span data-ttu-id="e93d4-223">どちらも、既定のサイズは 20 文字です。</span><span class="sxs-lookup"><span data-stu-id="e93d4-223">These are both defaulted to size 20 chars.</span></span>

## <a name="http-invalid-usernamepassword-callback"></a><span data-ttu-id="e93d4-224">HTTP の無効なユーザー名とパスワードのコールバック</span><span class="sxs-lookup"><span data-stu-id="e93d4-224">HTTP Invalid Username/Password Callback</span></span>

<span data-ttu-id="e93d4-225">HTTP サーバーがクライアント要求で無効なユーザー名とパスワードの組み合わせを受け取った場合、NetX HTTP サーバーでオプションの無効なユーザー名とパスワードのコールバックが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-225">The optional invalid username/password callback in NetX HTTP Server is invoked if HTTP server receives an invalid username and password combination in a Client request.</span></span> <span data-ttu-id="e93d4-226">HTTP サーバー アプリケーションによってコールバックが HTTP サーバーに登録されている場合、基本認証またはダイジェスト認証のいずれかが *nx_http_server_get_process*、*nx_http_server_put_process*、または *nx_http_server_delete_process* で失敗すると、それが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-226">If the HTTP server application registers a callback with HTTP server it will be invoked if either basic or digest authentication fails *in nx_http_server_get_process*, in *nx_http_server_put_process,* or *in nx_http_server_delete_process.*</span></span>

<span data-ttu-id="e93d4-227">HTTP サーバーにコールバックを登録するには、NetX HTTP サーバーに次のサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-227">To register a callback with the HTTP server, the following service is defined in NetX HTTP Server.</span></span>

```c
UINT nx_http_server_invalid_userpassword_notify_set (NX_HTTP_SERVER *http_server_ptr,
                                                    UINT *invalid_username_password_callback)
                                                    (CHAR *resource,
                                                    ULONG *client_nx_address,
                                                    UINT request_type));
```
<span data-ttu-id="e93d4-228">要求の種類を、次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-228">The request types are defined as follows:</span></span>

- <span data-ttu-id="e93d4-229">**NX_HTTP_SERVER_GET_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-229">**NX_HTTP_SERVER_GET_REQUEST**</span></span>
- <span data-ttu-id="e93d4-230">**NX_HTTP_SERVER_POST_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-230">**NX_HTTP_SERVER_POST_REQUEST**</span></span>
- <span data-ttu-id="e93d4-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-231">**NX_HTTP_SERVER_HEAD_REQUEST**</span></span>
- <span data-ttu-id="e93d4-232">**NX_HTTP_SERVER_PUT_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-232">**NX_HTTP_SERVER_PUT_REQUEST**</span></span>
- <span data-ttu-id="e93d4-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span><span class="sxs-lookup"><span data-stu-id="e93d4-233">**NX_HTTP_SERVER_DELETE_REQUEST**</span></span>

## <a name="http-insert-gmt-date-header-callback"></a><span data-ttu-id="e93d4-234">HTTP GMT 日付ヘッダー挿入コールバック</span><span class="sxs-lookup"><span data-stu-id="e93d4-234">HTTP Insert GMT Date Header Callback</span></span>

<span data-ttu-id="e93d4-235">NetX HTTP サーバーには、応答メッセージに日付ヘッダーを挿入するためのオプションのコールバックがあります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-235">There is an optional callback in NetX HTTP Server to insert a date header in its response messages.</span></span> <span data-ttu-id="e93d4-236">このコールバックは、HTTP サーバーで put または get 要求に応答しているときに呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-236">This callback is invoked when the HTTP Server is responding to a put or get request</span></span>

<span data-ttu-id="e93d4-237">HTTP サーバーに GMT 日付コールバックを登録するには、NetX HTTP サーバーに次のサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-237">To register a GMT date callback with the HTTP server, the following service is defined in the NetX HTTP Server.</span></span>

```c
UINT _nx_http_server_gmt_callback_set(NX_HTTP_SERVER *server_ptr,
                                     VOID (*gmt_get)(NX_HTTP_SERVER_DATE *date);
```

<span data-ttu-id="e93d4-238">NX_HTTP_SERVER_DATE データ型を、次のように定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-238">The NX_HTTP_SERVER_DATE data type is defined as follows:</span></span>

```c
typedef struct NX_HTTP_SERVER_DATE_STRUCT
{
    USHORT     nx_http_server_year;         /* Year        */
    UCHAR      nx_http_server_month;        /* Month       */
    UCHAR      nx_http_server_day;          /* Day         */
    UCHAR      nx_http_server_hour;         /* Hour        */
    UCHAR      nx_http_server_minute;       /* Minute      */
    UCHAR      nx_http_server_second;       /* Second      */
    UCHAR      nx_http_server_weekday;      /* Weekday     */
} NX_HTTP_SERVER_DATE;
```

## <a name="http-cache-info-get-callback"></a><span data-ttu-id="e93d4-239">HTTP キャッシュ情報取得コールバック</span><span class="sxs-lookup"><span data-stu-id="e93d4-239">HTTP Cache Info Get Callback</span></span>

<span data-ttu-id="e93d4-240">HTTP サーバーには、特定のリソースについて HTTP アプリケーションから最大有効期間と日付を要求するためのコールバックがあります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-240">The HTTP Server has a callback to request the max age and date from the HTTP application for a specific resource.</span></span> <span data-ttu-id="e93d4-241">この情報は、クライアントの Get 要求に応答して、HTTP サーバーでページ全体を送信するかどうかを判断するために使用されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-241">This information is used to determine if the HTTP server sends the entire page in response to a Client Get request.</span></span> <span data-ttu-id="e93d4-242">クライアント要求に "if modified since" が見つからないか、キャッシュ取得コールバックによって返された "last modified" の日付と一致しない場合は、ページ全体が送信されます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-242">If the “if modified since” in the Client request is not found or does not match the “last modified” date returned by the get cache callback, the entire page is sent.</span></span>

<span data-ttu-id="e93d4-243">HTTP サーバーにこのコールバックを登録するには、次のサービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="e93d4-243">To register the callback with the HTTP server the following service is defined:</span></span>

```c
UINT _nx_http_server_cache_info_callback_set(NX_HTTP_SERVER *server_ptr,
                                            UINT (*cache_info_get)
                                            (CHAR *, UINT *, NX_HTTP_SERVER_DATE *));
```

## <a name="http-multipart-support"></a><span data-ttu-id="e93d4-244">HTTP マルチパートのサポート</span><span class="sxs-lookup"><span data-stu-id="e93d4-244">HTTP Multipart Support</span></span>

<span data-ttu-id="e93d4-245">Multipurpose Internet Mail Extensions (MIME) は当初は SMTP プロトコルを対象としていましたが、HTTP でも使用されるようになりました。</span><span class="sxs-lookup"><span data-stu-id="e93d4-245">Multipurpose Internet Mail Extensions (MIME) was originally intended for the SMTP protocol, but its use has spread to HTTP.</span></span> <span data-ttu-id="e93d4-246">MIME を使用すると、同じメッセージ内に混在したメッセージの種類 (image/jpg、text/plain など) を含めることができます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-246">MIME allows messages to contain mixed message types (e.g. image/jpg and text/plain) within the same message.</span></span> <span data-ttu-id="e93d4-247">NetX HTTP サーバーには、クライアントからの MIME を含む HTTP メッセージのコンテンツの種類を判別するサービスが追加されています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-247">NetX HTTP Server has added services to determine content type in HTTP messages containing MIME from the Client.</span></span> <span data-ttu-id="e93d4-248">HTTP マルチパートのサポートを有効にしてこれらのサービスを使用するには、構成オプション **NX_HTTP_MULTIPART_ENABLE** を定義する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-248">To enable HTTP multipart support and use these services, the configuration option **NX_HTTP_MULTIPART_ENABLE** must be defined.</span></span>

```c
UINT nx_http_server_get_entity_header(NX_HTTP_SERVER *server_ptr,
                                     NX_PACKET **packet_pptr,
                                     UCHAR *entity_header_buffer,
                                     ULONG buffer_size);

UINT nx_http_server_get_entity_content(NX_HTTP_SERVER *server_ptr,
                                      NX_PACKET **packet_pptr,
                                      ULONG *available_offset,
                                      ULONG *available_length);
```

<span data-ttu-id="e93d4-249">これらのサービスの使用方法の詳細については、第 3 章「HTTP サービスの説明」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="e93d4-249">For more details on the use of these services, see their description in Chapter 3 “Description of HTTP Services”.</span></span>

## <a name="http-multi-thread-support"></a><span data-ttu-id="e93d4-250">HTTP マルチスレッドのサポート</span><span class="sxs-lookup"><span data-stu-id="e93d4-250">HTTP Multi-Thread Support</span></span>

<span data-ttu-id="e93d4-251">NetX HTTP クライアント サービスは、複数のスレッドから同時に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="e93d4-251">The NetX HTTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="e93d4-252">ただし、特定の HTTP クライアント インスタンスの読み取り要求または書き込み要求は、同じスレッドから順番に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e93d4-252">However, read or write requests for a particular HTTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="http-rfcs"></a><span data-ttu-id="e93d4-253">HTTP の RFC</span><span class="sxs-lookup"><span data-stu-id="e93d4-253">HTTP RFCs</span></span>

<span data-ttu-id="e93d4-254">NetX HTTP は、RFC1945 "ハイパーテキスト転送プロトコル/1.0"、RFC 2581 "TCP の輻輳制御"、RFC 1122 "インターネット ホストの要件"、および関連する RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="e93d4-254">NetX HTTP is compliant with RFC1945 “Hypertext Transfer Protocol/1.0”, RFC 2581 “TCP Congestion Control”, RFC 1122 “Requirements for Internet Hosts”, and related RFCs.</span></span>