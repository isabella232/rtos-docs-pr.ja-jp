---
title: GUIX Studio ユーザー ガイド
description: このガイドでは GUIX Studio に関する総合的な情報を提供します。これは、Microsoft の GUIX ランタイム ライブラリ用に設計された、Microsoft Windows ベースの高速 UI 開発環境です。
author: philmea
ms.author: philmea
ms.date: 5/19/2020
ms.service: rtos
ms.topic: article
ms.openlocfilehash: 6a5d628581d4c6b44ff093bac45790d6e2755349
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811987"
---
# <a name="chapter-1-introduction-to-azure-rtos-guix-studio"></a>第 1 章: Azure RTOS GUIX Studio の概要

Azure RTOS GUIX Studio は、Microsoft の GUIX ランタイム ライブラリ専用に設計された、Microsoft Windows ベースの高速 UI 開発環境です。

埋め込み UI の開発者は、GUIX Studio WYSIWYG 画面デザイナーを利用し、GUIX ランタイム環境を使用して埋め込み UI をすばやく作成および更新できます。 GUIX Studio のデザインは、拡張子が .gxp の GUIX Studio プロジェクト ファイルに保存され、メンテナンスされます。 ターゲット上でデザインを実行する準備が整うと、GUIX Studio によって、必要なすべての UI 情報とコードを含む C コードが生成されます。

## <a name="guix-studio-requirements"></a>GUIX Studio の要件

Microsoft の GUIX Studio が正常に機能するためには、*Windows XP* (またはそれ以降) が必要です。 システムには、最低 200 MB の RAM、2 GB のハードディスク空き領域、および 256 色で 1024x768 の最小表示が必要です。 また、埋め込みアプリケーションは、*ThreadX/GUIX V6.0* 以降で実行されている必要があります。

埋め込み UI アプリケーションをスタンドアロンの Microsoft Windows 実行可能ファイルとしてビルドして実行できるようにする場合は、Microsoft Windows の実行可能ファイルを生成するために C ソース コードをコンパイルできるコンパイラまたはビルド環境も必要になります。 GUIX Studio に含まれる評価パッケージには、Visual Studio 2019 と互換性のあるプロジェクト ファイルと、提供されている各サンプル アプリケーションのソリューションも含まれています。 別のコンパイラを使用している場合は、独自のプロジェクト ファイルを作成するか、サンプル アプリケーションをビルドするためにファイルを作成するか、 https://aka.ms/azrtos-support でサポートにお問い合わせください。

## <a name="guix-studio-constraints"></a>GUIX Studio の制約

GUIX Studio UI デザイン ツールには、次のようないくつかの制約があります。

- プロジェクトあたり最大 4 つの表示。
- GUIX Studio プロジェクトあたり最大 10 万のウィジェット。
- 最大 10 万の異なるリソース (色、フォント、ピクセルマップ、文字列など)。