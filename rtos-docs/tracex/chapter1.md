---
title: 第 1 章 - Azure RTOS TraceX の概要
description: Azure RTOS TraceX は、組み込みターゲット上で実行されている ThreadX によって収集されたシステム イベント情報を表示する、Microsoft のシステム分析ツールです。
author: philmea
ms.service: rtos
ms.topic: article
ms.date: 5/19/2020
ms.author: philmea
ms.openlocfilehash: 3009d13388b3b7e8eca041dc6ede569a5caf5e9b
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104812500"
---
# <a name="chapter-1---introduction-to-azure-rtos-tracex"></a><span data-ttu-id="f4708-103">第 1 章 - Azure RTOS TraceX の概要</span><span class="sxs-lookup"><span data-stu-id="f4708-103">Chapter 1 - Introduction to Azure RTOS TraceX</span></span>

<span data-ttu-id="f4708-104">Azure RTOS TraceX は、組み込みターゲット上で実行されている ThreadX によって収集されたシステム イベント情報を表示する、Microsoft のシステム分析ツールです。</span><span class="sxs-lookup"><span data-stu-id="f4708-104">Azure RTOS TraceX is a Microsoft system analysis tool that displays system event information gathered by ThreadX running on an embedded target.</span></span> <span data-ttu-id="f4708-105">ユーザーは、組み込みターゲットの RAM に格納されているトレース バッファーを、ホスト コンピューター上のバイナリ ファイルに転送する役割を担います。</span><span class="sxs-lookup"><span data-stu-id="f4708-105">The user is responsible for transferring the trace buffer stored in RAM in the embedded target to a binary file on the host computer.</span></span> <span data-ttu-id="f4708-106">次に、ユーザーはこのファイルを TraceX で開き、対象のイベントをグラフィカルに分析して、システムの問題を診断し、動作しているアプリケーションをチューニングしてパフォーマンスとリソース管理を向上させることができます。</span><span class="sxs-lookup"><span data-stu-id="f4708-106">The user can then open this file with TraceX and graphically analyze the target events, diagnosing system problems and tuning a working application to improve performance and resource management.</span></span>

## <a name="tracex-requirements"></a><span data-ttu-id="f4708-107">TraceX の要件</span><span class="sxs-lookup"><span data-stu-id="f4708-107">TraceX Requirements</span></span>

<span data-ttu-id="f4708-108">TraceX には Windows XP (またはそれ以降) が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4708-108">TraceX requires Windows XP (or above).</span></span> <span data-ttu-id="f4708-109">システムには、最低 192 MB の RAM、2 GB のハードディスク空き領域、および最低 256 色、1024x768 の表示が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4708-109">The system should have a minimum of 192 MB of RAM, 2 GB of available hard-disk space, and a minimum display of 1024x768 with 256 colors.</span></span> <span data-ttu-id="f4708-110">また、アプリケーションは ThreadX V5.0 以降で実行されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="f4708-110">In addition, the application must be running on ThreadX V5.0 or later.</span></span>

<span data-ttu-id="f4708-111">TraceX では、Microsoft .NET Framework をインストールする必要もあります。これは TraceX インストーラーによって自動的に行われます。</span><span class="sxs-lookup"><span data-stu-id="f4708-111">TraceX also requires the Microsoft .NET framework be installed, which the TraceX installer does automatically.</span></span>

## <a name="tracex-constraints"></a><span data-ttu-id="f4708-112">TraceX の制約</span><span class="sxs-lookup"><span data-stu-id="f4708-112">TraceX Constraints</span></span>

<span data-ttu-id="f4708-113">TraceX には次の制約があります。</span><span class="sxs-lookup"><span data-stu-id="f4708-113">TraceX has the following constraints:</span></span>

- <span data-ttu-id="f4708-114">TraceX のファイルは、最大 32,768 イベント (約 1 MB) に制限されています。</span><span class="sxs-lookup"><span data-stu-id="f4708-114">TraceX files are limited to a maximum of 32,768 events (roughly 1 MB ).</span></span>
- <span data-ttu-id="f4708-115">タイムスタンプ ソースには、適切な解像度が必要です。</span><span class="sxs-lookup"><span data-stu-id="f4708-115">The time-stamp source must have reasonable resolution.</span></span> <span data-ttu-id="f4708-116">解像度が低すぎると、イベントは重複します。</span><span class="sxs-lookup"><span data-stu-id="f4708-116">If the resolution is too low, the events will overlap.</span></span> <span data-ttu-id="f4708-117">解像度が高すぎると、イベント間に長時間のギャップが生じる可能性があります。</span><span class="sxs-lookup"><span data-stu-id="f4708-117">If the resolution is too high, there is potential for long gaps between events.</span></span>
- <span data-ttu-id="f4708-118">TraceX では、タイマー期間よりも長いイベント間の間隔を正確に測定することはできません。</span><span class="sxs-lookup"><span data-stu-id="f4708-118">TraceX cannot accurately measure intervals between events greater than the timer period.</span></span>
