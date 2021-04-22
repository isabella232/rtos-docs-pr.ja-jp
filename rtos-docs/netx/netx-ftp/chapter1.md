---
title: 第 1 章 - Azure RTOS NetX FTP の概要
description: ファイル転送プロトコル (FTP) は、ファイル転送用に設計されたプロトコルです。 FTP では、信頼性の高い伝送制御プロトコル (TCP) サービスを使用してファイル転送機能を実行します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 86e132daf96f9039631234f10c8e239b61ad5126
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811549"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-ftp"></a><span data-ttu-id="70fd1-104">第 1 章 - Azure RTOS NetX FTP の概要</span><span class="sxs-lookup"><span data-stu-id="70fd1-104">Chapter 1 - Introduction to Azure RTOS NetX FTP</span></span>

<span data-ttu-id="70fd1-105">ファイル転送プロトコル (FTP) は、ファイル転送用に設計されたプロトコルです。</span><span class="sxs-lookup"><span data-stu-id="70fd1-105">The File Transfer Protocol (FTP) is a protocol designed for file transfers.</span></span> <span data-ttu-id="70fd1-106">FTP では、信頼性の高い伝送制御プロトコル (TCP) サービスを使用してファイル転送機能を実行します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-106">FTP utilizes reliable Transmission Control Protocol (TCP) services to perform its file transfer function.</span></span> <span data-ttu-id="70fd1-107">このため、FTP は、信頼性の高いファイル転送プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="70fd1-107">Because of this, FTP is a highly reliable file transfer protocol.</span></span> <span data-ttu-id="70fd1-108">また、高パフォーマンスでもあります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-108">FTP is also high-performance.</span></span> <span data-ttu-id="70fd1-109">実際の FTP ファイル転送は、専用の FTP 接続で実行されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-109">The actual FTP file transfer is performed on a dedicated FTP connection.</span></span>

## <a name="ftp-requirements"></a><span data-ttu-id="70fd1-110">FTP の要件</span><span class="sxs-lookup"><span data-stu-id="70fd1-110">FTP Requirements</span></span>

<span data-ttu-id="70fd1-111">Azure RTOS NetX FTP パッケージが正しく機能するには、NetX IP インスタンスが既に作成されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-111">In order to function properly, the Azure RTOS NetX FTP package requires that a NetX IP instance has already been created.</span></span> <span data-ttu-id="70fd1-112">さらに、その同じ IP インスタンス上で TCP が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-112">In addition, TCP must be enabled on that same IP instance.</span></span> <span data-ttu-id="70fd1-113">NetX FTP パッケージの FTP クライアント部分には、これ以外の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="70fd1-113">The FTP Client portion of the NetX FTP package has no further requirements.</span></span>

<span data-ttu-id="70fd1-114">NetX FTP パッケージの FTP サーバー部分には、追加要件がいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-114">The FTP Server portion of the NetX FTP package has several additional requirements.</span></span> <span data-ttu-id="70fd1-115">最も重要なのは、TCP の "*ウェルノウン ポート 21*" (すべてのクライアント FTP コマンド要求を処理) と、"*ウェルノウン ポート 20*" (すべてのクライアント FTP データ転送を処理) への完全なアクセス権が必要であることです。</span><span class="sxs-lookup"><span data-stu-id="70fd1-115">First, it requires complete access to TCP *well-known port 21* for handling all Client FTP command requests and *well-known port 20* for handling all Client FTP data transfers.</span></span> <span data-ttu-id="70fd1-116">また、FTP サーバーは、組み込みファイルシステムの FileX と合わせて使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="70fd1-116">The FTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="70fd1-117">FileX が使用できない場合、ユーザーは、使用されている FileX の一部を自分自身の環境に移植することもできます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-117">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="70fd1-118">これについては、このガイドの後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-118">This is discussed in later sections of this guide.</span></span>

## <a name="ftp-constraints"></a><span data-ttu-id="70fd1-119">FTP の制約</span><span class="sxs-lookup"><span data-stu-id="70fd1-119">FTP Constraints</span></span>

<span data-ttu-id="70fd1-120">FTP 標準には、ファイル データの表現に関する多くのオプションがあります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-120">The FTP standard has many options regarding the representation of file data.</span></span> <span data-ttu-id="70fd1-121">UNIX の実装と同様に、NetX FTP には次のファイル形式の制約があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-121">Similar to Unix implementations, NetX FTP assumes the following file format constraints:</span></span>

- <span data-ttu-id="70fd1-122">ファイルの種類: **バイナリ**</span><span class="sxs-lookup"><span data-stu-id="70fd1-122">File Type: **Binary**</span></span>
- <span data-ttu-id="70fd1-123">ファイル形式: **NONPRINT のみ**</span><span class="sxs-lookup"><span data-stu-id="70fd1-123">File Format: **Nonprint Only**</span></span>
- <span data-ttu-id="70fd1-124">ファイル構造: **ファイル構造のみ**</span><span class="sxs-lookup"><span data-stu-id="70fd1-124">File Structure: **File Structure Only**</span></span>
- <span data-ttu-id="70fd1-125">送信モード: **ストリーム モードのみ**</span><span class="sxs-lookup"><span data-stu-id="70fd1-125">Transmission Mode: **Stream Mode Only**</span></span>

## <a name="ftp-file-names"></a><span data-ttu-id="70fd1-126">FTP ファイル名</span><span class="sxs-lookup"><span data-stu-id="70fd1-126">FTP File Names</span></span>

<span data-ttu-id="70fd1-127">FTP ファイル名は、ターゲット ファイル システム (通常は FileX) の形式である必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-127">FTP file names should be in the format of the target file system (usually FileX).</span></span> <span data-ttu-id="70fd1-128">これらは、必要に応じて完全なパス情報を含む、NULL 終端 ASCII 文字列である必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-128">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="70fd1-129">NetX FTP 実装では、FTP ファイル名のサイズに特に制限はありません。</span><span class="sxs-lookup"><span data-stu-id="70fd1-129">There is no specified limit for the size of FTP file names in the NetX FTP implementation.</span></span> <span data-ttu-id="70fd1-130">ただし、パケット プールのペイロード サイズが、最大のパスやファイル名に対応できることが必要です。</span><span class="sxs-lookup"><span data-stu-id="70fd1-130">However, the packet pool payload size should be able to accommodate the maximum path and/or file name.</span></span>

## <a name="ftp-client-commands"></a><span data-ttu-id="70fd1-131">FTP クライアント コマンド</span><span class="sxs-lookup"><span data-stu-id="70fd1-131">FTP Client Commands</span></span>

<span data-ttu-id="70fd1-132">FTP には、接続を開き、ファイルおよびディレクトリ操作を実行するための単純なメカニズムがあります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-132">The FTP has a simple mechanism for opening connections and performing file and directory operations.</span></span> <span data-ttu-id="70fd1-133">基本的には、TCP の "*ウェルノウン ポート 21*" で接続が正常に確立された後に、クライアントによって発行される一連の標準の FTP コマンドがあります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-133">There is basically a set of standard FTP commands that are issued by the Client after a connection has been successfully established on the TCP *well-known port 21*.</span></span> <span data-ttu-id="70fd1-134">基本的な FTP コマンドの一部を次に示します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-134">The following shows some of the basic FTP commands:</span></span>

### <a name="ftp-command-and-meaning"></a><span data-ttu-id="70fd1-135">FTP コマンドおよび意味</span><span class="sxs-lookup"><span data-stu-id="70fd1-135">FTP Command and Meaning</span></span>

- <span data-ttu-id="70fd1-136">**CWD パス**: *作業ディレクトリを変更する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-136">**CWD path**: *Change working directory*</span></span>
- <span data-ttu-id="70fd1-137">**DELE ファイル名**: *指定したファイル名を削除する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-137">**DELE filename**: *Delete specified file name*</span></span>
- <span data-ttu-id="70fd1-138">**LIST ディレクトリ**: *ディレクトリの一覧を取得する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-138">**LIST directory**: *Get directory listing*</span></span>
- <span data-ttu-id="70fd1-139">**MKD ディレクトリ**: *新しいディレクトリを作成する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-139">**MKD directory**: *Make new directory*</span></span>
- <span data-ttu-id="70fd1-140">**NLST ディレクトリ**: *ディレクトリの一覧を取得する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-140">**NLST directory**: *Get directory listing*</span></span>
- <span data-ttu-id="70fd1-141">**NOOP**: *操作なし、成功を返す*</span><span class="sxs-lookup"><span data-stu-id="70fd1-141">**NOOP**: *No operation, returns success*</span></span>
- <span data-ttu-id="70fd1-142">**PASS パスワード**: *ログインのパスワードを指定する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-142">**PASS password**: *Provide password for login*</span></span>
- <span data-ttu-id="70fd1-143">**PASV**: *パッシブ転送モードを要求する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-143">**PASV**: *Request passive transfer mode*</span></span>
- <span data-ttu-id="70fd1-144">**PWD パス**: *現在のディレクトリ パスを選択する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-144">**PWD path**: *Pickup current directory path*</span></span>
- <span data-ttu-id="70fd1-145">**QUIT**: *クライアント接続を終了する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-145">**QUIT**: *Terminate Client connection*</span></span>
- <span data-ttu-id="70fd1-146">**RETR ファイル名**: *指定したファイルを読み取る*</span><span class="sxs-lookup"><span data-stu-id="70fd1-146">**RETR filename**: *Read specified file*</span></span>
- <span data-ttu-id="70fd1-147">**RMD ディレクトリ**: *指定したディレクトリを削除する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-147">**RMD directory**: *Delete specified directory*</span></span>
- <span data-ttu-id="70fd1-148">**RNFR 古いファイル名**: *名前を変更するファイルを指定する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-148">**RNFR oldfilename**: *Specify file to rename*</span></span>
- <span data-ttu-id="70fd1-149">**RNTO 新しいファイル名**: *ファイル名を、指定したファイル名に変更する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-149">**RNTO newfilename**: *Rename file to supplied file name*</span></span>
- <span data-ttu-id="70fd1-150">**STOR ファイル名**: *指定したファイルを書き込む*</span><span class="sxs-lookup"><span data-stu-id="70fd1-150">**STOR filename**: *Write specified file*</span></span>
- <span data-ttu-id="70fd1-151">**TYPE I**: *バイナリ ファイル イメージを選択する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-151">**TYPE I**: *Select binary file image*</span></span>
- <span data-ttu-id="70fd1-152">**USER ユーザー名**: *ログインのユーザー名を指定する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-152">**USER username**: *Provide username for login*</span></span>
- <span data-ttu-id="70fd1-153">**PORT IP アドレス, ポート**: *IP アドレスとクライアント データ ポートを指定する*</span><span class="sxs-lookup"><span data-stu-id="70fd1-153">**PORT ip_address,port**: *Provide IP address and Client data port*</span></span>

<span data-ttu-id="70fd1-154">これらの ASCII コマンドは、FTP サーバーで FTP 操作を実行するために、NetX FTP クライアント ソフトウェアによって内部的に使用されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-154">These ASCII commands are used internally by the NetX FTP Client software to perform FTP operations with the FTP Server.</span></span>

## <a name="ftp-server-responses"></a><span data-ttu-id="70fd1-155">FTP サーバーの応答</span><span class="sxs-lookup"><span data-stu-id="70fd1-155">FTP Server Responses</span></span>

<span data-ttu-id="70fd1-156">FTP サーバーでは、"*ウェルノウン TCP ポート 21*" を使用してクライアント コマンド要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-156">The FTP Server utilizes the *well-known TCP port 21* to field Client command requests.</span></span> <span data-ttu-id="70fd1-157">FTP サーバーは、クライアントコマンドを処理した後、3 桁の数値応答を ASCII で返し、オプションの ASCII 文字列を返します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-157">Once the FTP Server processes the Client command, it returns a 3-digit numeric response in ASCII followed by an optional ASCII string.</span></span> <span data-ttu-id="70fd1-158">この数値の応答は、操作が成功したか、失敗したかを判断するために、FTP クライアント ソフトウェアによって使用されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-158">The numeric response is used by the FTP Client software to determine whether the operation succeeded or failed.</span></span> <span data-ttu-id="70fd1-159">クライアント要求に対するさまざまな FTP サーバー応答を次に示します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-159">The following lists various FTP Server responses to Client commands:</span></span>

### <a name="first-numeric-field-and-meaning"></a><span data-ttu-id="70fd1-160">最初の数値フィールドおよび意味</span><span class="sxs-lookup"><span data-stu-id="70fd1-160">First Numeric Field and Meaning</span></span>

- <span data-ttu-id="70fd1-161">**1xx**: *肯定的な準備状態 - さらに別の応答が返されます*。</span><span class="sxs-lookup"><span data-stu-id="70fd1-161">**1xx**: *Positive preliminary status – another reply coming*.</span></span>
- <span data-ttu-id="70fd1-162">**2xx**: *肯定的な完了状態*。</span><span class="sxs-lookup"><span data-stu-id="70fd1-162">**2xx**: *Positive completion status*.</span></span>
- <span data-ttu-id="70fd1-163">**3xx**: *肯定的な準備状態 - 別のコマンドを送信する必要があります*。</span><span class="sxs-lookup"><span data-stu-id="70fd1-163">**3xx**: *Positive preliminary status – another command must be sent*.</span></span>
- <span data-ttu-id="70fd1-164">**4xx**: *一時的なエラー状態*。</span><span class="sxs-lookup"><span data-stu-id="70fd1-164">**4xx**: *Temporary error condition*.</span></span>
- <span data-ttu-id="70fd1-165">**5xx**: *エラー状態*。</span><span class="sxs-lookup"><span data-stu-id="70fd1-165">**5xx**: *Error condition.*</span></span>

### <a name="second-numeric-field-and-meaning"></a><span data-ttu-id="70fd1-166">2 番目の数値フィールドおよび意味</span><span class="sxs-lookup"><span data-stu-id="70fd1-166">Second Numeric Field and Meaning</span></span>

- <span data-ttu-id="70fd1-167">**x0x**: コマンドの構文エラー。</span><span class="sxs-lookup"><span data-stu-id="70fd1-167">**x0x**: Syntax error in command.</span></span>
- <span data-ttu-id="70fd1-168">**x1x**: 情報メッセージ。</span><span class="sxs-lookup"><span data-stu-id="70fd1-168">**x1x**: Informational message.</span></span>
- <span data-ttu-id="70fd1-169">**x2x**: 接続関連。</span><span class="sxs-lookup"><span data-stu-id="70fd1-169">**x2x**: Connection related.</span></span>
- <span data-ttu-id="70fd1-170">**x3x**: 認証関連。</span><span class="sxs-lookup"><span data-stu-id="70fd1-170">**x3x**: Authentication related.</span></span>
- <span data-ttu-id="70fd1-171">**x4x**: 未指定。</span><span class="sxs-lookup"><span data-stu-id="70fd1-171">**x4x**: Unspecified.</span></span>
- <span data-ttu-id="70fd1-172">**x5x**: ファイル システム関連。</span><span class="sxs-lookup"><span data-stu-id="70fd1-172">**x5x**: File system related.</span></span>

<span data-ttu-id="70fd1-173">たとえば、クライアントが QUIT コマンドで FTP 接続の切断を要求すると、通常はサーバーから "221" コードで応答が返されます (切断が成功した場合)。</span><span class="sxs-lookup"><span data-stu-id="70fd1-173">For example, a Client request to disconnect an FTP connection with the QUIT command will typically be responded with a "221" code from the Server – if the disconnect is successful.</span></span>

## <a name="ftp-passive-transfer-mode"></a><span data-ttu-id="70fd1-174">FTP パッシブ転送モード</span><span class="sxs-lookup"><span data-stu-id="70fd1-174">FTP Passive Transfer Mode</span></span>

<span data-ttu-id="70fd1-175">既定では、NetX FTP クライアントはアクティブ転送モードを使用して、データ ソケットを介して FTP サーバーとデータを交換します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-175">By default, the NetX FTP Client uses the active transport mode to exchange data over the data socket with the FTP server.</span></span> <span data-ttu-id="70fd1-176">この配置の問題は、FTP サーバーが接続する TCP サーバー ソケットを FTP クライアントが開く必要があることです。</span><span class="sxs-lookup"><span data-stu-id="70fd1-176">The problem with this arrangement is that it requires the FTP Client to open a TCP server socket for the FTP Server to connect to.</span></span> <span data-ttu-id="70fd1-177">これは、セキュリティ リスクとなる可能性があるため、クライアント ファイアウォールによってブロックされる場合があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-177">This represents a possible security risk and may be blocked by the Client firewall.</span></span> <span data-ttu-id="70fd1-178">パッシブ転送モードは、データ接続で FTP サーバーが TCP サーバー ソケットを作成するという点で、アクティブ転送モードとは異なります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-178">Passive transfer mode differs from active transport mode by having the FTP server create the TCP server socket on the data connection.</span></span> <span data-ttu-id="70fd1-179">これにより、(FTP クライアントの) セキュリティ リスクが排除されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-179">This eliminates the security risk (for the FTP Client).</span></span>

<span data-ttu-id="70fd1-180">パッシブ データ転送を有効にするには、以前に作成された FTP クライアントに対して、2 番目の引数を NX_TRUE に設定した *nx_ftp_client_passive_mode_set* をアプリケーションで呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-180">To enable passive data transfer, the application calls *nx_ftp_client_passive_mode_set* on a previously created FTP Client with the second argument set to NX_TRUE.</span></span> <span data-ttu-id="70fd1-181">その後、データを転送するための後続の NetX FTP クライアント サービス (NLST、RETR、STOR) は、すべてパッシブ転送モードで試行されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-181">Thereafter, all subsequent NetX FTP Client services for transferring data (NLST, RETR, STOR) are attempted in the passive transport mode.</span></span>

<span data-ttu-id="70fd1-182">FTP クライアントは、最初に PASV コマンド (引数なし) を送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-182">The FTP Client first sends the PASV command (no arguments).</span></span> <span data-ttu-id="70fd1-183">FTP サーバーがこの要求をサポートしている場合は、227 の "OK" 応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-183">If the FTP server supports this request it will return the 227 "OK" response.</span></span> <span data-ttu-id="70fd1-184">次に、クライアントが、RETR などの要求を送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-184">Then the Client sends the request e.g. RETR.</span></span> <span data-ttu-id="70fd1-185">サーバーがパッシブ転送モードを拒否した場合、NetX FTP クライアント サービスはエラー状態を返します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-185">If the server refuses passive transfer mode, the NetX FTP Client service returns an error status.</span></span>

<span data-ttu-id="70fd1-186">パッシブ転送モードを無効にし、アクティブ転送モードに戻すには、2 番目の引数を NX_FALSE に設定した *nx_ftp_client_passive_mode_set* をアプリケーションで呼び出します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-186">To disable passive transport mode and return to active transport mode, the application calls *nx_ftp_client_passive_mode_set* with the second argument set to NX_FALSE.</span></span>

## <a name="ftp-communication"></a><span data-ttu-id="70fd1-187">FTP 通信</span><span class="sxs-lookup"><span data-stu-id="70fd1-187">FTP Communication</span></span>

<span data-ttu-id="70fd1-188">FTP サーバーでは、"*ウェルノウン TCP ポート 21*" を使用してクライアント要求を処理します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-188">The FTP Server utilizes the *well-known TCP port 21* to field Client requests.</span></span> <span data-ttu-id="70fd1-189">FTP クライアントは、使用可能な任意の TCP ポートを使用できます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-189">FTP Clients may use any available TCP port.</span></span> <span data-ttu-id="70fd1-190">FTP イベントの一般的なシーケンスは次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="70fd1-190">The general sequence of FTP events is as follows:</span></span>

### <a name="ftp-read-file-requests"></a><span data-ttu-id="70fd1-191">FTP ファイル読み取り要求</span><span class="sxs-lookup"><span data-stu-id="70fd1-191">FTP Read File Requests</span></span>

1. <span data-ttu-id="70fd1-192">クライアントがサーバー ポート 21 への TCP 接続を発行します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-192">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="70fd1-193">サーバーが "220" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-193">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-194">クライアントが、"ユーザー名" を含む "USER" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-194">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="70fd1-195">サーバーが "331" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-195">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-196">クライアントが、"パスワード" を含む "PASS" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-196">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="70fd1-197">サーバーが "230" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-197">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-198">クライアントが、バイナリ転送用の "TYPE I" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-198">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="70fd1-199">サーバーが "200" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-199">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-200">クライアントが、IP アドレスとポートを含む "PORT" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-200">Client sends "PORT" message with IP address and port.</span></span>
1. <span data-ttu-id="70fd1-201">サーバーが "200" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-201">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-202">クライアントが、読み取るファイル名を含む "RETR" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-202">Client sends "RETR" message with file name to read.</span></span>
1. <span data-ttu-id="70fd1-203">サーバーがデータ ソケットを作成し、"PORT" コマンドで指定されたクライアント データ ポートに接続します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-203">Server creates data socket and connects with client data port specified in the "PORT" command.</span></span>
1. <span data-ttu-id="70fd1-204">サーバーが "125" 応答を送信して、ファイルの読み取りが開始されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-204">Server sends "125" response to signal file read has started.</span></span>
1. <span data-ttu-id="70fd1-205">サーバーが、データ接続を介してファイルの内容を送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-205">Server sends contents of file through the data connection.</span></span> <span data-ttu-id="70fd1-206">ファイルが完全に転送されるまで、このプロセスが続行されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-206">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="70fd1-207">完了すると、サーバーはデータ接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-207">When finished, Server disconnects data connection.</span></span>
1. <span data-ttu-id="70fd1-208">サーバーが "250" 応答を送信して、ファイルの読み取りが成功したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-208">Server sends "250" response to signal file read is successful.</span></span>
1. <span data-ttu-id="70fd1-209">クライアントが "QUIT" を送信して FTP 接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-209">Clients sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="70fd1-210">サーバーが "221" 応答を送信して、切断が成功したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-210">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="70fd1-211">サーバーが FTP 接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-211">Server disconnects FTP connection.</span></span>

<span data-ttu-id="70fd1-212">前述のように、IPv4 で実行される FTP と、IPv6 で実行される FTP の違いは、IPv6 では PORT コマンドの代わりに EPRT コマンドが使用されることのみです。</span><span class="sxs-lookup"><span data-stu-id="70fd1-212">As mentioned previously, the only difference between FTP running over IPv4 and IPv6 is the PORT command is replaced with the EPRT command for IPv6</span></span>

<span data-ttu-id="70fd1-213">FTP クライアントがパッシブ転送モードで読み取り要求を行う場合、コマンド シーケンスは次のようになります (**太字** の行は、アクティブ転送モードとは異なる手順を示しています)。</span><span class="sxs-lookup"><span data-stu-id="70fd1-213">If the FTP Client makes a read request in the passive transfer mode, the command sequence is as follows (**bolded** lines indicates a different step from active transfer mode):</span></span>

1. <span data-ttu-id="70fd1-214">クライアントがサーバー ポート 21 への TCP 接続を発行します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-214">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="70fd1-215">サーバーが "220" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-215">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-216">クライアントが、"ユーザー名" を含む "USER" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-216">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="70fd1-217">サーバーが "331" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-217">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-218">クライアントが、"パスワード" を含む "PASS" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-218">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="70fd1-219">サーバーが "230" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-219">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-220">クライアントが、バイナリ転送用の "TYPE I" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-220">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="70fd1-221">サーバーが "200" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-221">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-222">**クライアントが "PASV" メッセージを送信します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-222">**Client sends "PASV" message.**</span></span>
1. <span data-ttu-id="70fd1-223">**"227" 応答と、クライアントの接続先となる IP アドレスとポートをサーバーが送信して成功を通知します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-223">**Server sends "227" response, and IP address and port for the Client to connect to, to signal success.**</span></span>
1. <span data-ttu-id="70fd1-224">クライアントが、読み取るファイル名を含む "RETR" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-224">Client sends "RETR" message with file name to read.</span></span>
1. <span data-ttu-id="70fd1-225">**サーバーがデータ サーバー ソケットを作成し、"227" 応答で指定されたポートを使用して、このソケットでクライアント接続要求をリッスンします。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-225">**Server creates data server socket and listens for the Client connect request on this socket using the port specified in the "227" response.**</span></span>
1. <span data-ttu-id="70fd1-226">**サーバーが制御ソケットで "150" 応答を送信して、ファイルの読み取りが開始されたことを通知します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-226">**Server sends "150" response on the control socket to signal file read has started.**</span></span>
1. <span data-ttu-id="70fd1-227">サーバーが、データ接続を介してファイルの内容を送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-227">Server sends contents of file through the data connection.</span></span> <span data-ttu-id="70fd1-228">ファイルが完全に転送されるまで、このプロセスが続行されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-228">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="70fd1-229">完了すると、サーバーはデータ接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-229">When finished, Server disconnects data connection.</span></span>
1. <span data-ttu-id="70fd1-230">**サーバーが制御ソケットで "226" 応答を送信して、ファイルの読み取りが成功したことを通知します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-230">**Server sends "226" response on the control socket to signal file read is successful.**</span></span>
1. <span data-ttu-id="70fd1-231">クライアントが "QUIT" を送信して FTP 接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-231">Client sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="70fd1-232">サーバーが "221" 応答を送信して、切断が成功したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-232">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="70fd1-233">サーバーが FTP 接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-233">Server disconnects FTP connection.</span></span>

### <a name="ftp-write-requests"></a><span data-ttu-id="70fd1-234">FTP 書き込み要求</span><span class="sxs-lookup"><span data-stu-id="70fd1-234">FTP Write Requests</span></span>

1. <span data-ttu-id="70fd1-235">クライアントがサーバー ポート 21 への TCP 接続を発行します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-235">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="70fd1-236">サーバーが "220" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-236">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-237">クライアントが、"ユーザー名" を含む "USER" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-237">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="70fd1-238">サーバーが "331" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-238">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-239">クライアントが、"パスワード" を含む "PASS" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-239">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="70fd1-240">サーバーが "230" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-240">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-241">クライアントが、バイナリ転送用の "TYPE I" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-241">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="70fd1-242">サーバーが "200" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-242">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-243">クライアントが、IP アドレスとポートを含む "PORT" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-243">Client sends "PORT" message with IP address and port.</span></span>
1. <span data-ttu-id="70fd1-244">サーバーが "200" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-244">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-245">クライアントが、書き込むファイル名を含む "STOR" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-245">Client sends "STOR" message with file name to write.</span></span>
1. <span data-ttu-id="70fd1-246">サーバーがデータ ソケットを作成し、"PORT" コマンドで指定されたクライアント データ ポートに接続します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-246">Server creates data socket and connects with client data port specified in the "PORT" command.</span></span>
1. <span data-ttu-id="70fd1-247">サーバーが "125" 応答を送信して、ファイルの書き込みが開始されたことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-247">Server sends "125" response to signal file write has started.</span></span>
1. <span data-ttu-id="70fd1-248">クライアントが、データ接続を介してファイルの内容を送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-248">Client sends contents of file through the data connection.</span></span> <span data-ttu-id="70fd1-249">ファイルが完全に転送されるまで、このプロセスが続行されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-249">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="70fd1-250">完了すると、クライアントはデータ接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-250">When finished, Client disconnects data connection.</span></span>
1. <span data-ttu-id="70fd1-251">サーバーが "250" 応答を送信して、ファイルの書き込みが成功したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-251">Server sends "250" response to signal file write is successful.</span></span>
1. <span data-ttu-id="70fd1-252">クライアントが "QUIT" を送信して FTP 接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-252">Clients sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="70fd1-253">サーバーが "221" 応答を送信して、切断が成功したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-253">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="70fd1-254">サーバーが FTP 接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-254">Server disconnects FTP connection.</span></span>

<span data-ttu-id="70fd1-255">FTP クライアントがパッシブ転送モードで書き込み要求を行う場合、コマンド シーケンスは次のようになります (**太字** の行は、アクティブ転送モードとは異なる手順を示しています)。</span><span class="sxs-lookup"><span data-stu-id="70fd1-255">If the FTP Client makes a write request in the passive transfer mode, the command sequence is as follows (**bolded** lines indicates a different step from active transfer mode):</span></span>

1. <span data-ttu-id="70fd1-256">クライアントがサーバー ポート 21 への TCP 接続を発行します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-256">Client issues TCP connect to Server port 21.</span></span>
1. <span data-ttu-id="70fd1-257">サーバーが "220" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-257">Server sends "220" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-258">クライアントが、"ユーザー名" を含む "USER" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-258">Client sends "USER" message with "username."</span></span>
1. <span data-ttu-id="70fd1-259">サーバーが "331" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-259">Server sends "331" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-260">クライアントが、"パスワード" を含む "PASS" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-260">Client sends "PASS" message with "password."</span></span>
1. <span data-ttu-id="70fd1-261">サーバーが "230" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-261">Server sends "230" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-262">クライアントが、バイナリ転送用の "TYPE I" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-262">Client sends "TYPE I" message for binary transfer.</span></span>
1. <span data-ttu-id="70fd1-263">サーバーが "200" 応答を送信して成功を通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-263">Server sends "200" response to signal success.</span></span>
1. <span data-ttu-id="70fd1-264">**クライアントが "PASV" メッセージを送信します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-264">**Client sends "PASV" message.**</span></span>
1. <span data-ttu-id="70fd1-265">**"227" 応答と、クライアントの接続先となる IP アドレスとポートをサーバーが送信して成功を通知します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-265">**Server sends "227" response, and IP address and port for the Client to connect to, to signal success.**</span></span>
1. <span data-ttu-id="70fd1-266">クライアントが、書き込むファイル名を含む "STOR" メッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-266">Client sends "STOR" message with file name to write.</span></span>
1. <span data-ttu-id="70fd1-267">**サーバーがデータ サーバー ソケットを作成し、"227" 応答で指定されたポートを使用して、このソケットでクライアント接続要求をリッスンします。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-267">**Server creates data server socket and listens for the Client connect request on this socket using the port specified in the "227" response.**</span></span>
1. <span data-ttu-id="70fd1-268">**サーバーが制御ソケットで "150" 応答を送信して、ファイルの書き込みが開始されたことを通知します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-268">**Server sends "150" response on the control socket to signal file write has started.**</span></span>
1. <span data-ttu-id="70fd1-269">クライアントが、データ接続を介してファイルの内容を送信します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-269">Client sends contents of file through the data connection.</span></span> <span data-ttu-id="70fd1-270">ファイルが完全に転送されるまで、このプロセスが続行されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-270">This process continues until file is completely transferred.</span></span>
1. <span data-ttu-id="70fd1-271">完了すると、クライアントはデータ接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-271">When finished, Client disconnects data connection.</span></span>
1. <span data-ttu-id="70fd1-272">**サーバーが制御ソケットで "226" 応答を送信して、ファイルの書き込みが成功したことを通知します。**</span><span class="sxs-lookup"><span data-stu-id="70fd1-272">**Server sends "226" response on the control socket to signal file write is successful.**</span></span>
1. <span data-ttu-id="70fd1-273">クライアントが "QUIT" を送信して FTP 接続を終了します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-273">Client sends "QUIT" to terminate FTP connection.</span></span>
1. <span data-ttu-id="70fd1-274">サーバーが "221" 応答を送信して、切断が成功したことを通知します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-274">Server sends "221" response to signal disconnect is successful.</span></span>
1. <span data-ttu-id="70fd1-275">サーバーが FTP 接続を切断します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-275">Server disconnects FTP connection.</span></span>

## <a name="ftp-authentication"></a><span data-ttu-id="70fd1-276">FTP Authentication</span><span class="sxs-lookup"><span data-stu-id="70fd1-276">FTP Authentication</span></span>

<span data-ttu-id="70fd1-277">FTP 接続が行われるたびにクライアントは、*ユーザー名* と *パスワード* をサーバーに提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-277">Whenever an FTP connection takes place, the Client must provide the Server with a *username* and *password*.</span></span> <span data-ttu-id="70fd1-278">一部の FTP サイトでは、特定のユーザー名およびパスワードなしで FTP アクセスを許可する、"*匿名 FTP*" と呼ばれるものを使用できます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-278">Some FTP sites allow what is called *Anonymous FTP*, which allows FTP access without a specific username and password.</span></span> <span data-ttu-id="70fd1-279">この種類の接続では、"anonymous" をユーザー名として、完全な電子メール アドレスをパスワードとして指定します。</span><span class="sxs-lookup"><span data-stu-id="70fd1-279">For this type of connection, "anonymous" should be supplied for username and the password should be a complete e-mail address.</span></span>

<span data-ttu-id="70fd1-280">ログインおよびログアウト認証ルーチンは、ユーザーが NetX FTP に提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-280">The user is responsible for supplying NetX FTP with login and logout authentication routines.</span></span> <span data-ttu-id="70fd1-281">これらは、\***nx_ftp_server_create** _ 関数内で提供され、パスワード処理から呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-281">These are supplied during the \***nx_ftp_server_create** _ function and called from the password processing.</span></span> <span data-ttu-id="70fd1-282">login\* 関数により NX_SUCCESS が返された場合は、接続が認証され、FTP 操作が許可されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-282">If the _login\* function returns NX_SUCCESS, the connection is authenticated and FTP operations are allowed.</span></span> <span data-ttu-id="70fd1-283">*login* 関数により NX_SUCCESS 以外のものが返された場合は、接続が拒否されます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-283">Otherwise, if the *login* function returns something other than NX_SUCCESS, the connection attempt is rejected.</span></span>

## <a name="ftp-multi-thread-support"></a><span data-ttu-id="70fd1-284">FTP マルチスレッドのサポート</span><span class="sxs-lookup"><span data-stu-id="70fd1-284">FTP Multi-Thread Support</span></span>

<span data-ttu-id="70fd1-285">NetX FTP クライアント サービスは、複数のスレッドから同時に呼び出すことができます。</span><span class="sxs-lookup"><span data-stu-id="70fd1-285">The NetX FTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="70fd1-286">ただし、特定の FTP クライアント インスタンスの読み取りまたは書き込み要求は、同じスレッドから順番に実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="70fd1-286">However, read or write requests for a particular FTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="ftp-rfcs"></a><span data-ttu-id="70fd1-287">FTP RFC</span><span class="sxs-lookup"><span data-stu-id="70fd1-287">FTP RFCs</span></span>

<span data-ttu-id="70fd1-288">NetX FTP は、RFC959 および関連する RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="70fd1-288">NetX FTP is compliant with RFC959 and related RFCs.</span></span>