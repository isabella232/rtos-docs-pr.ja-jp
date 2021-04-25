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
#  <a name="chapter-2--installing-threadx-support-for-armv8-m"></a>第 2 章  ARMv8-M 用 ThreadX サポートのインストール

ARMv8-M アーキテクチャをサポートするための、追加の ThreadX ソース コード ファイルがあります。

ThreadX をセキュア モードで実行する場合、これらの追加ファイルと API は必要ありません。 ThreadX をセキュア モードで実行するには、**_tx_port.h_ *_ の先頭、コマンド ライン、またはプロジェクト設定のいずれかで、シンボル **TX_SECURE_EXECUTION** を定義します。すべての c ファイルおよびアセンブリ ファイルに対して、_* TX_SECURE_EXECUTION** が定義されていることを確認します。 ThreadX とユーザー アプリケーションはセキュア モードで実行されます。

ThreadX とユーザー アプリケーションを非セキュア モードで実行し、非セキュアで呼び出し可能なセキュア関数をサポートするには、次の操作を行ってください。

セキュア アプリケーションにファイル ***tx_thread_secure_stack.c*** を追加する必要があります。

ThreadX ライブラリに次のファイルを追加する必要があります。

- ***tx_secure_interface.h***
- ***txe_thread_secure_stack_allocate.c***
- ***txe_thread_secure_stack_free.c***
- ***tx_thread_secure_stack_allocate.s***
- ***tx_thread_secure_stack_free.s***

次の 2 つのファイルは、ThreadX ライブラリ内の汎用ファイルに代わるものです。

- ***tx_thread_stack_error_handler.c***
- ***tx_thread_stack_error_notify.c***

## <a name="additional-threadx-sources-for-armv8-m"></a>ARMv8-M 用 ThreadX の追加ソース

ARMv8-M TrustZone アーキテクチャ用の ThreadX 追加ファイルを以下に示します。

  | **[ファイル名]**                            | **Contents**                                                        |
  |------------------------------------------|---------------------------------------------------------------------|
  | ***tx_secure_interface.h***              | ThreadX の非セキュアで呼び出し可能な関数を定義するインクルード ファイル。 |
  | ***txe_thread_secure_stack_allocate.c*** |  セキュア スタック割り当て API のエラーチェック ファイル。 |
  | ***txe_thread_secure_stack_free.c***     |  セキュア スタック解放 API のエラーチェック ファイル。 |
  | ***tx_thread_secure_stack_allocate.s***  |  セキュア スタック割り当てサービスの非セキュア veneer。 |
  | ***tx_thread_secure_stack_free.s***      |  セキュア スタック解放サービスの非セキュア veneer。 |
  | ***tx_thread_stack_error_handler.c***    |  スレッド スタック エラーのハンドラー。 |
  | ***tx_thread_stack_error_notify.c***     |  スレッド スタック エラー処理用のレジスタ通知コールバック。 |
