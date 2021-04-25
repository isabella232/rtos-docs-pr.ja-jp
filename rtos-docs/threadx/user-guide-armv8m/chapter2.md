---
title: 第 2 章 - ARMv8-M 用 ThreadX サポートのインストール
description: この章では、ARMv8-M アーキテクチャ用の ThreadX ソース コードをインストールして使用する方法について説明します。
author: v-condav
ms.author: v-condav
ms.date: 03/04/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 303b83bcc92797314b764353b770965c0170fb99
ms.sourcegitcommit: d8edbb3207fe99f8afb431597dac063e73383e68
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/05/2021
ms.locfileid: "106377504"
---
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a><span data-ttu-id="e3a0c-103">第 2 章  ARMv8-M 用 ThreadX サポートのインストール</span><span class="sxs-lookup"><span data-stu-id="e3a0c-103">Chapter 2  Installing ThreadX support for ARMv8-M</span></span>

<span data-ttu-id="e3a0c-104">ARMv8-M アーキテクチャをサポートするための、追加の ThreadX ソース コード ファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-104">There are additional ThreadX source code files to support the ARMv8-M architecture.</span></span>

<span data-ttu-id="e3a0c-105">ThreadX をセキュア モードで実行する場合、これらの追加ファイルと API は必要ありません。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-105">If ThreadX is to be run in secure mode, these additional files and APIs are not needed.</span></span> <span data-ttu-id="e3a0c-106">ThreadX をセキュア モードで実行するには、**_tx_port.h_ *_ の先頭、コマンド ライン、またはプロジェクト設定のいずれかで、シンボル **TX_SECURE_EXECUTION** を定義します。すべての c ファイルおよびアセンブリ ファイルに対して、_* TX_SECURE_EXECUTION** が定義されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-106">To run ThreadX in secure mode, define the symbol **TX_SECURE_EXECUTION** at the top of **_tx_port.h_*_ or on the command line or project settings. Ensure _\* TX_SECURE_EXECUTION*\* is defined for all c and assembly files.</span></span> <span data-ttu-id="e3a0c-107">ThreadX とユーザー アプリケーションはセキュア モードで実行されます。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-107">ThreadX and the user application will execute in secure mode.</span></span>

<span data-ttu-id="e3a0c-108">ThreadX とユーザー アプリケーションを非セキュア モードで実行し、非セキュアで呼び出し可能なセキュア関数をサポートするには、次の操作を行ってください。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-108">To run ThreadX and the user application in non-secure mode and support non-secure callable secure functions, please do the following.</span></span>

<span data-ttu-id="e3a0c-109">セキュア アプリケーションにファイル ***tx_thread_secure_stack.c*** を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-109">The file ***tx_thread_secure_stack.c*** must be added to the secure application.</span></span>

<span data-ttu-id="e3a0c-110">ThreadX ライブラリに次のファイルを追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-110">The following files must be added to the ThreadX library.</span></span>

- <span data-ttu-id="e3a0c-111">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-111">***tx_secure_interface.h***</span></span>
- <span data-ttu-id="e3a0c-112">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-112">***txe_thread_secure_stack_allocate.c***</span></span>
- <span data-ttu-id="e3a0c-113">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-113">***txe_thread_secure_stack_free.c***</span></span>
- <span data-ttu-id="e3a0c-114">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-114">***tx_thread_secure_stack_allocate.s***</span></span>
- <span data-ttu-id="e3a0c-115">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-115">***tx_thread_secure_stack_free.s***</span></span>

<span data-ttu-id="e3a0c-116">次の 2 つのファイルは、ThreadX ライブラリ内の汎用ファイルに代わるものです。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-116">The following two files replace the generic files in the ThreadX library.</span></span>

- <span data-ttu-id="e3a0c-117">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-117">***tx_thread_stack_error_handler.c***</span></span>
- <span data-ttu-id="e3a0c-118">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-118">***tx_thread_stack_error_notify.c***</span></span>

## <a name="additional-threadx-sources-for-armv8-m"></a><span data-ttu-id="e3a0c-119">ARMv8-M 用 ThreadX の追加ソース</span><span class="sxs-lookup"><span data-stu-id="e3a0c-119">Additional ThreadX Sources for ARMv8-M</span></span>

<span data-ttu-id="e3a0c-120">ARMv8-M TrustZone アーキテクチャ用の ThreadX 追加ファイルを以下に示します。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-120">The additional ThreadX files for the ARMv8-M TrustZone architecture are described below.</span></span>

  | <span data-ttu-id="e3a0c-121">**[ファイル名]**</span><span class="sxs-lookup"><span data-stu-id="e3a0c-121">**File Name**</span></span>                            | <span data-ttu-id="e3a0c-122">**Contents**</span><span class="sxs-lookup"><span data-stu-id="e3a0c-122">**Contents**</span></span>                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | <span data-ttu-id="e3a0c-123">***tx_secure_interface.h***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-123">***tx_secure_interface.h***</span></span>              | <span data-ttu-id="e3a0c-124">ThreadX の非セキュアで呼び出し可能な関数を定義するインクルード ファイル。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-124">Include file that defines the ThreadX non-secure callable functions.</span></span> |
  | <span data-ttu-id="e3a0c-125">***txe_thread_secure_stack_allocate.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-125">***txe_thread_secure_stack_allocate.c***</span></span> |  <span data-ttu-id="e3a0c-126">セキュア スタック割り当て API のエラーチェック ファイル。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-126">Error-checking file for the secure stack allocate API.</span></span> |
  | <span data-ttu-id="e3a0c-127">***txe_thread_secure_stack_free.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-127">***txe_thread_secure_stack_free.c***</span></span>     |  <span data-ttu-id="e3a0c-128">セキュア スタック解放 API のエラーチェック ファイル。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-128">Error-checking file for the secure stack free API.</span></span> |
  | <span data-ttu-id="e3a0c-129">***tx_thread_secure_stack_allocate.s***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-129">***tx_thread_secure_stack_allocate.s***</span></span>  |  <span data-ttu-id="e3a0c-130">セキュア スタック割り当てサービスの非セキュア veneer。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-130">Non-secure veneer for the secure stack allocate service.</span></span> |
  | <span data-ttu-id="e3a0c-131">***tx_thread_secure_stack_free.s***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-131">***tx_thread_secure_stack_free.s***</span></span>      |  <span data-ttu-id="e3a0c-132">セキュア スタック解放サービスの非セキュア veneer。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-132">Non-secure veneer for the secure stack free service.</span></span> |
  | <span data-ttu-id="e3a0c-133">***tx_thread_stack_error_handler.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-133">***tx_thread_stack_error_handler.c***</span></span>    |  <span data-ttu-id="e3a0c-134">スレッド スタック エラーのハンドラー。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-134">Handler for thread stack errors.</span></span> |
  | <span data-ttu-id="e3a0c-135">***tx_thread_stack_error_notify.c***</span><span class="sxs-lookup"><span data-stu-id="e3a0c-135">***tx_thread_stack_error_notify.c***</span></span>     |  <span data-ttu-id="e3a0c-136">スレッド スタック エラー処理用のレジスタ通知コールバック。</span><span class="sxs-lookup"><span data-stu-id="e3a0c-136">Register notification callback for handling thread stack errors.</span></span> |
