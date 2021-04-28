---
title: 第 1 章 - Azure RTOS NetX Duo TFTP の概要
description: 簡易ファイル転送プロトコル (TFTP) は、ファイル転送用に設計された軽量プロトコルです。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4431b23e143d05214090547e7f179a6f5def8217
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810526"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-duo-tftp"></a><span data-ttu-id="57503-103">第 1 章 - Azure RTOS NetX Duo TFTP の概要</span><span class="sxs-lookup"><span data-stu-id="57503-103">Chapter 1 - Introduction to Azure RTOS NetX Duo TFTP</span></span> 

<span data-ttu-id="57503-104">簡易ファイル転送プロトコル (TFTP) は、ファイル転送用に設計された軽量プロトコルです。</span><span class="sxs-lookup"><span data-stu-id="57503-104">The Trivial File Transfer Protocol (TFTP) is a lightweight protocol designed for file transfers.</span></span> <span data-ttu-id="57503-105">他の堅牢なプロトコルと異なり TFTP は細かなエラー チェックを行いません。また、stop-and-wait プロトコルであるためパフォーマンスに制約があります。</span><span class="sxs-lookup"><span data-stu-id="57503-105">Unlike more robust protocols, TFTP does not perform extensive error checking and can also have limited performance because it is a stop-and-wait protocol.</span></span> <span data-ttu-id="57503-106">TFTP データ パケットを送信した後、送信元は受信元から ACK が返されるまで待機します。</span><span class="sxs-lookup"><span data-stu-id="57503-106">After a TFTP data packet is sent, the sender waits for an ACK to be returned by the recipient.</span></span> <span data-ttu-id="57503-107">この方法はシンプルですが、TFTP の全体的なスループットが制約を受けます。</span><span class="sxs-lookup"><span data-stu-id="57503-107">Although this is simple, it does limit the overall TFTP throughput.</span></span> <span data-ttu-id="57503-108">TFTP パッケージを使用すると、ホストが IP ネットワークで TFTP プロトコルを使用できます。</span><span class="sxs-lookup"><span data-stu-id="57503-108">The TFTP package enables hosts to use the TFTP protocol over IP networks.</span></span>

## <a name="tftp-requirements"></a><span data-ttu-id="57503-109">TFTP の要件</span><span class="sxs-lookup"><span data-stu-id="57503-109">TFTP Requirements</span></span>

<span data-ttu-id="57503-110">NetX Duo TFTP パッケージの TFTP クライアント部分が正しく機能するためには、IP インスタンスを前もって作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="57503-110">In order to function properly, the TFTP Clients portion of the NetX Duo TFTP package requires that an IP instance has already been created.</span></span> <span data-ttu-id="57503-111">さらに、その IP インスタンスで UDP が有効になっている必要があります。</span><span class="sxs-lookup"><span data-stu-id="57503-111">In addition, UDP must be enabled on that same IP instance.</span></span> <span data-ttu-id="57503-112">NetX Duo TFTP パッケージのクライアント部分には、それ以上の要件はありません。</span><span class="sxs-lookup"><span data-stu-id="57503-112">The Client portion of the NetX Duo TFTP package has no further requirements.</span></span>

<span data-ttu-id="57503-113">NetX Duo TFTP パッケージの TFTP サーバー部分には、それ以外にもいくつか要件があります。</span><span class="sxs-lookup"><span data-stu-id="57503-113">The TFTP Server portion of the NetX Duo TFTP package has several additional requirements.</span></span> <span data-ttu-id="57503-114">まず、すべてのクライアント TFTP 要求を処理するために、*ウェルノウン ポートの UDP ポート 69* に対する完全なアクセスが必要です。</span><span class="sxs-lookup"><span data-stu-id="57503-114">First, it requires complete access to the UDP *well known port 69* for handling all client TFTP requests.</span></span> <span data-ttu-id="57503-115">また、TFTP サーバーは、組み込みファイル システムの FileX と合わせて使用するように設計されています。</span><span class="sxs-lookup"><span data-stu-id="57503-115">The TFTP Server is also designed for use with the FileX embedded file system.</span></span> <span data-ttu-id="57503-116">FileX が使用できない場合、ユーザーは、使用されている FileX の一部を自分自身の環境に移植することもできます。</span><span class="sxs-lookup"><span data-stu-id="57503-116">If FileX is not available, the user may port the portions of FileX used to their own environment.</span></span> <span data-ttu-id="57503-117">これについては、このガイドの後のセクションで説明します。</span><span class="sxs-lookup"><span data-stu-id="57503-117">This is discussed in later sections of this guide.</span></span>

## <a name="tftp-file-names"></a><span data-ttu-id="57503-118">TFTP ファイル名</span><span class="sxs-lookup"><span data-stu-id="57503-118">TFTP File Names</span></span> 

<span data-ttu-id="57503-119">TFTP ファイル名は、送信先のファイル システムに形式を合わせる必要があります。</span><span class="sxs-lookup"><span data-stu-id="57503-119">TFTP file names should be in the format of the target file system.</span></span> <span data-ttu-id="57503-120">また、NULL で終わる ASCII 文字列である必要があり、場合によっては絶対パスの情報も必要です。</span><span class="sxs-lookup"><span data-stu-id="57503-120">They should be NULL terminated ASCII strings, with full path information if necessary.</span></span> <span data-ttu-id="57503-121">NetX Duo TFTP の実装では、TFTP ファイル名のサイズに上限の指定はありません。</span><span class="sxs-lookup"><span data-stu-id="57503-121">There is no specified limit in the size of TFTP file names in the NetX Duo TFTP implementation.</span></span>

## <a name="tftp-messages"></a><span data-ttu-id="57503-122">TFTP メッセージ</span><span class="sxs-lookup"><span data-stu-id="57503-122">TFTP Messages</span></span>

<span data-ttu-id="57503-123">TFTP にはファイルの開閉、読み込み、書き込みを行うためのとてもシンプルな仕組みがあります。</span><span class="sxs-lookup"><span data-stu-id="57503-123">The TFTP has a very simple mechanism for opening, reading, writing, and closing files.</span></span> <span data-ttu-id="57503-124">UDP ヘッダーの下には、通常 2 ～ 4 バイトの TFTP ヘッダーがあります。</span><span class="sxs-lookup"><span data-stu-id="57503-124">There are basically 2-4 bytes of TFTP header underneath the UDP header.</span></span> <span data-ttu-id="57503-125">ファイルを開く TFTP メッセージは次の形式で定義されます:</span><span class="sxs-lookup"><span data-stu-id="57503-125">The definition of the TFTP file open messages has the following format:</span></span>

<span data-ttu-id="57503-126">**oooof…f0OCTET0**</span><span class="sxs-lookup"><span data-stu-id="57503-126">**oooof…f0OCTET0**</span></span>

<span data-ttu-id="57503-127">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="57503-127">Where:</span></span>

- <span data-ttu-id="57503-128">**oooo** 2 バイトのオペコード フィールド</span><span class="sxs-lookup"><span data-stu-id="57503-128">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="57503-129">0x0001 -> 読み込むために開く</span><span class="sxs-lookup"><span data-stu-id="57503-129">0x0001 -> Open for read</span></span>  
<span data-ttu-id="57503-130">0x0002 -> 書き込むために開く</span><span class="sxs-lookup"><span data-stu-id="57503-130">0x0002 -> Open for write</span></span>

- <span data-ttu-id="57503-131">**f…f** n バイトのファイル名フィールド</span><span class="sxs-lookup"><span data-stu-id="57503-131">**f…f** n-byte Filename field</span></span>

- <span data-ttu-id="57503-132">0  1 バイトの NULL 終端文字</span><span class="sxs-lookup"><span data-stu-id="57503-132">0  1-byte NULL termination character</span></span>

- <span data-ttu-id="57503-133">**OCTET** バイナリ転送を指定する ASCII 文字列 "OCTET"</span><span class="sxs-lookup"><span data-stu-id="57503-133">**OCTET** ASCII “OCTET” to specify binary transfer</span></span>

- <span data-ttu-id="57503-134">0  1 バイトの NULL 終端文字</span><span class="sxs-lookup"><span data-stu-id="57503-134">0  1-byte NULL termination character</span></span>

<span data-ttu-id="57503-135">TFTP 書き込み、ACK、エラー メッセージの定義は少し異なり、次のように定義されます:</span><span class="sxs-lookup"><span data-stu-id="57503-135">The definition of the TFTP write, ACK, and error messages are slightly different and are defined as follows:</span></span>

<span data-ttu-id="57503-136">**oooobbbbd…d**</span><span class="sxs-lookup"><span data-stu-id="57503-136">**oooobbbbd…d**</span></span>

<span data-ttu-id="57503-137">各値の説明:</span><span class="sxs-lookup"><span data-stu-id="57503-137">Where:</span></span>

- <span data-ttu-id="57503-138">**oooo** 2 バイトのオペコード フィールド</span><span class="sxs-lookup"><span data-stu-id="57503-138">**oooo** 2-byte Opcode field</span></span>  
<span data-ttu-id="57503-139">0x0003 -> データ パケット</span><span class="sxs-lookup"><span data-stu-id="57503-139">0x0003 -> Data packet</span></span>  
<span data-ttu-id="57503-140">0x0004 -> 最後の読み込みに対する ACK</span><span class="sxs-lookup"><span data-stu-id="57503-140">0x0004 -> ACK for last read</span></span>  
<span data-ttu-id="57503-141">0x0005 -> Error 状態</span><span class="sxs-lookup"><span data-stu-id="57503-141">0x0005 -> Error condition</span></span>  

- <span data-ttu-id="57503-142">**bbbb** 2 バイトのブロック番号フィールド (1 - n)</span><span class="sxs-lookup"><span data-stu-id="57503-142">**bbbb** 2-byte Block Number field (1-n)</span></span>

- <span data-ttu-id="57503-143">**d…d** n バイトのデータ フィールド</span><span class="sxs-lookup"><span data-stu-id="57503-143">**d…d** n-byte Data field</span></span>


- <span data-ttu-id="57503-144">0x0001 (読み取り) ファイル名 0 オクテット 0</span><span class="sxs-lookup"><span data-stu-id="57503-144">0x0001 (read) File Name 0 OCTET 0</span></span>

- <span data-ttu-id="57503-145">0x0002 (書き込み) ファイル名 0 オクテット 0</span><span class="sxs-lookup"><span data-stu-id="57503-145">0x0002 (write) File Name 0 OCTET 0</span></span>

## <a name="tftp-communication"></a><span data-ttu-id="57503-146">TFTP 通信</span><span class="sxs-lookup"><span data-stu-id="57503-146">TFTP Communication</span></span>

<span data-ttu-id="57503-147">TFTP サーバーでは、既知の UDP ポート 69 を使用して、クライアントの要求をリッスンします。</span><span class="sxs-lookup"><span data-stu-id="57503-147">TFTP Servers utilize the well-known UDP port 69 to listen for Client requests.</span></span> <span data-ttu-id="57503-148">TFTP クライアントのソケットは、使用可能な任意の UDP ポートにバインドできます。</span><span class="sxs-lookup"><span data-stu-id="57503-148">TFTP Client sockets may bind to any available UDP port.</span></span> <span data-ttu-id="57503-149">アップロードまたはダウンロードするファイルの入ったデータ パケットのペイロードは、512 バイトのチャンクに分けて送信されます。ただし、最後のパケットは 512 バイト未満になります。</span><span class="sxs-lookup"><span data-stu-id="57503-149">Data packet payload containing the file to upload or download is sent in 512 byte chunks, until the last packet containing < 512 bytes.</span></span> <span data-ttu-id="57503-150">そのため、512 バイト未満のパケットがファイルの終わりの合図になります。</span><span class="sxs-lookup"><span data-stu-id="57503-150">Therefore a packet containing fewer than 512 bytes signals the end of file.</span></span> <span data-ttu-id="57503-151">イベントは一般に次の順序で進行します:</span><span class="sxs-lookup"><span data-stu-id="57503-151">The general sequence of events is as follows:</span></span>

<span data-ttu-id="57503-152">TFTP ファイル読み取り要求:</span><span class="sxs-lookup"><span data-stu-id="57503-152">TFTP Read File Requests:</span></span>

1.  <span data-ttu-id="57503-153">クライアントが "読むために開く" 要求をファイル名と合わせて発行し、サーバーの応答を待機します。</span><span class="sxs-lookup"><span data-stu-id="57503-153">The Client issues an “Open For Read” request with the file name and waits for a reply from the Server.</span></span>

2.  <span data-ttu-id="57503-154">サーバーからファイルの先頭の 512 バイトが送信されます。ただし、ファイルサイズが 512 バイト未満の場合は送信する量もそれ未満になります。</span><span class="sxs-lookup"><span data-stu-id="57503-154">The Server sends the first 512 bytes of the file or less if the file size is less than 512 bytes.</span></span>

3.  <span data-ttu-id="57503-155">ファイルの内容が 512 バイトを超える場合、クライアントはデータを受信し、ACK を送信し、サーバーからの次のパケットが届くのを待機します。</span><span class="sxs-lookup"><span data-stu-id="57503-155">The Client receives data, sends an ACK, and waits for the next packet from the Server for files containing more than 512 bytes.</span></span>

4.  <span data-ttu-id="57503-156">クライアントが 512 バイト未満のパケットを受信すると、この手順は終了します。</span><span class="sxs-lookup"><span data-stu-id="57503-156">The sequence ends when the Client receives a packet containing fewer than 512 bytes.</span></span>

<span data-ttu-id="57503-157">TFTP 書き込み要求:</span><span class="sxs-lookup"><span data-stu-id="57503-157">TFTP Write Requests:</span></span>

1.  <span data-ttu-id="57503-158">クライアントが "書き込むために開く" 要求をファイル名と合わせて発行し、ブロック番号が 0 の ACK がサーバーから届くのを待機します。</span><span class="sxs-lookup"><span data-stu-id="57503-158">The Client issues an “Open for Write” request with the file name and waits for an ACK with a block number of 0 from the Server.</span></span>

2.  <span data-ttu-id="57503-159">サーバーは、ファイルに書き込みを行う準備ができたら、ブロック番号が 0 の ACK を送信します。</span><span class="sxs-lookup"><span data-stu-id="57503-159">When the Server is ready to write the file, it sends an ACK with a block number of zero.</span></span>

3.  <span data-ttu-id="57503-160">クライアントからファイルの先頭の 512 バイト (ファイルが 512 バイト未満の場合はそれ未満) がサーバーに送信され、ACK が返されるのを待機します。</span><span class="sxs-lookup"><span data-stu-id="57503-160">The Client sends the first 512 bytes of the file (or less for files less than 512 bytes) to the Server and waits for an ACK back.</span></span>

4.  <span data-ttu-id="57503-161">サーバーは、バイトを書き込んでから ACK を送信します。</span><span class="sxs-lookup"><span data-stu-id="57503-161">The Server sends an ACK after the bytes are written.</span></span>

5.  <span data-ttu-id="57503-162">クライアントが 512 バイト未満のパケットの書き込みを完了すると、この手順は終了します。</span><span class="sxs-lookup"><span data-stu-id="57503-162">The sequence ends when the Client completes writing a packet containing fewer than 512 bytes.</span></span>
 

## <a name="tftp-server-session-timer"></a><span data-ttu-id="57503-163">TFTP サーバー セッション タイマー</span><span class="sxs-lookup"><span data-stu-id="57503-163">TFTP Server Session Timer</span></span>

<span data-ttu-id="57503-164">TFTP サーバーのクライアント要求スロットは数に制約があります。</span><span class="sxs-lookup"><span data-stu-id="57503-164">The TFTP Server has a limited number of client request slots.</span></span> <span data-ttu-id="57503-165">クライアント セッションが破棄されたように見える状態になっている場合、そのスロットは再使用できません。</span><span class="sxs-lookup"><span data-stu-id="57503-165">If a client session appears to be dropped, that slot cannot be available for re-use.</span></span> <span data-ttu-id="57503-166">ただし、NX_TFTP_SERVER_RETRANSMIT_ENABLE オプションが有効である場合、NetX Duo TFTP Server によって、各クライアント セッションのタイムアウトを監視するセッション タイマーが作成されます。</span><span class="sxs-lookup"><span data-stu-id="57503-166">However if the NX_TFTP_SERVER_RETRANSMIT_ENABLE option is enabled, the NetX Duo TFTP Server creates an session timer that monitors the timeout on each of its client sessions.</span></span> <span data-ttu-id="57503-167">タイムアウトするとセッションは終了し、開いているすべてのファイルが閉じられます。</span><span class="sxs-lookup"><span data-stu-id="57503-167">When a session timeout expires it is terminated and any open files are closed.</span></span> <span data-ttu-id="57503-168">こうしてその "スロット" は、別の TFTP クライアント要求に使用できるようになります。</span><span class="sxs-lookup"><span data-stu-id="57503-168">Thus the ‘slot’ becomes available for another TFTP Client request.</span></span>

<span data-ttu-id="57503-169">タイムアウトを設定するには、構成オプション NX_TFTP_SERVER_RETRANSMIT_TIMEOUT を調整します。既定値は 200 タイマー ティックです。</span><span class="sxs-lookup"><span data-stu-id="57503-169">To set the timeout, adjust the configuration option NX_TFTP_SERVER_RETRANSMIT_TIMEOUT which by default is 200 timer ticks.</span></span> <span data-ttu-id="57503-170">セッション タイムアウトを確認する間隔は NX_TFTP_SERVER_TIMEOUT_PERIOD で設定します。既定値は 20 タイマー ティックです。</span><span class="sxs-lookup"><span data-stu-id="57503-170">The interval between which session timeouts are checked is set by the NX_TFTP_SERVER_TIMEOUT_PERIOD which is 20 timer ticks by default.</span></span>

<span data-ttu-id="57503-171">TFTP クライアントから (書き込みを行った) ファイルを TFTP FileX メディアにアップロードした後は、メディアをフラッシュして、TFTP サーバーの RAM ディスクから裏で処理を実行するメディア (TFTP クライアントのディスクのメモリ) にデータを書き込めるようにする必要があります。</span><span class="sxs-lookup"><span data-stu-id="57503-171">When the TFTP Client has uploaded (written) files to the TFTP FileX media, the media needs to be flushed so that data can be written from the TFTP server ram disk to the underlying media (TFTP Client disk memory).</span></span> <span data-ttu-id="57503-172">アプリケーションの使用中に TFTP サーバーを終了したくない場合は、fx_media_flush サービスを使用してこれを実行できます。</span><span class="sxs-lookup"><span data-stu-id="57503-172">This can be done using the fx_media_flush service if the application does not wish to close the TFTP Server.</span></span>

<span data-ttu-id="57503-173">ただし、TFTP サーバーを終了した後、アプリケーションで FileX メディアをそれ以上使用しない場合は、fx_media_close サービスを使用してメディアを終了する必要があります。</span><span class="sxs-lookup"><span data-stu-id="57503-173">However, after closing the TFTP server, the application should, if it has no further use for the FileX media, then close the media using the fx_media_close service.</span></span> <span data-ttu-id="57503-174">そうすることで、ファイル データをフラッシュして TFTP クライアントのディスクに戻し、開いているファイル閉じ、ディレクトリの情報をメディアで更新できます。</span><span class="sxs-lookup"><span data-stu-id="57503-174">This will flush the file data back to the TFTP Client disk, close open files, and update the directory information to the media.</span></span>

<span data-ttu-id="57503-175">この章の「簡単な例」セクションでこの操作を例示しています。</span><span class="sxs-lookup"><span data-stu-id="57503-175">The “Small Example” section in this chapter demonstrates this.</span></span>

<span data-ttu-id="57503-176">FileX メディアを更新する 3 つ目の方法として、FileX サービスを明示的に使用する代わりに、FX_FAULT_TOLERANT または FX_FAULT_TOLERANT_DATA オプションを使用して FileX ライブラリをコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="57503-176">A third option for updating the FileX media is to compile the FileX library with the FX_FAULT_TOLERANT or the FX_FAULT_TOLERANT_DATA options instead of using FileX services explicitly.</span></span> <span data-ttu-id="57503-177">そのように定義すれば、FileX から書き込み要求が自動的にメディア ドライバーに渡されます。</span><span class="sxs-lookup"><span data-stu-id="57503-177">If defined, FileX automatically passes write requests to the media driver.</span></span> <span data-ttu-id="57503-178">これらのオプションを使用するとパフォーマンスが落ちる場合もありますが、ファイル データやクラスターの損失防止に大きな効果があります。</span><span class="sxs-lookup"><span data-stu-id="57503-178">These options may limit performance but offer greater protection from lost file data or lost clusters.</span></span> <span data-ttu-id="57503-179">これに関する詳しい情報と FileX 一般に関する情報は「Express Logic FileX ユーザー ガイド」をご覧ください。</span><span class="sxs-lookup"><span data-stu-id="57503-179">For more information about this and FileX in general, please see the Express Logic FileX User Guide.</span></span>

## <a name="tftp-multi-thread-support"></a><span data-ttu-id="57503-180">TFTP のマルチスレッド サポート</span><span class="sxs-lookup"><span data-stu-id="57503-180">TFTP Multi-Thread Support</span></span>

<span data-ttu-id="57503-181">NetX Duo TFTP Client のサービスは、複数のスレッドから同時に呼び出せます。</span><span class="sxs-lookup"><span data-stu-id="57503-181">The NetX Duo TFTP Client services can be called from multiple threads simultaneously.</span></span> <span data-ttu-id="57503-182">ただし、特定の TFTP クライアント インスタンスに対する読み取りまたは書き込み要求は、同じスレッドによって 1 つずつ順番に行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="57503-182">However, read or write requests for a particular TFTP Client instance should be done in sequence from the same thread.</span></span>

## <a name="tftp-rfcs"></a><span data-ttu-id="57503-183">TFTP RFC</span><span class="sxs-lookup"><span data-stu-id="57503-183">TFTP RFCs</span></span>

<span data-ttu-id="57503-184">NetX Duo TFTP は RFC1350 およびその関連 RFC に準拠しています。</span><span class="sxs-lookup"><span data-stu-id="57503-184">NetX Duo TFTP is compliant with RFC1350 and related RFCs.</span></span>

