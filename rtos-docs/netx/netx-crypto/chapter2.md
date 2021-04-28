---
title: 第 2 章 - Azure RTOS NetX Crypto のインストールと使用
description: この章では、NetX Crypto コンポーネントのインストール、セットアップ、使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1616667c5efd73229ed69bcd4e5de5f80e5826f9
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811633"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-crypto"></a>第 2 章 - Azure RTOS NetX Crypto のインストールと使用

この章では、Azure RTOS NetX Crypto コンポーネントのインストール、設定、使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS NetX Crypto は [https://github.com/azure-rtos/netxduo](https://github.com/azure-rtos/netxduo) で入手できます。 パッケージに含まれているソース ファイル、インクルード ファイル、このドキュメントを含む PDF ファイルを以下に示します。

- **nx_crypto.h**: NetX Crypto モジュールのパブリック API ヘッダー ファイル
- **nx_crypto_*.c/h**: NetX Crypto の C/H ソース ファイル
- **nx_crypto_port.h**: 開発ツールおよびターゲットに固有のデータ定義と構造体のすべてが含まれる C ヘッダー ファイル。
- **NetX_Crypto_User_Guide.pdf**: NetX Crypto モジュールについての PDF の説明。

## <a name="netx-crypto-installation"></a>NetX Crypto のインストール

前述したディストリビューション全体が、**crypto_libraries** ディレクトリに収録されています。このディレクトリは、NetX Duo リポジトリのルート レベルにあります。

NetX Crypto を使用するためには、前述のディストリビューション全体を、NetX がインストールされているのと同じディレクトリ レベルにコピーする必要があります。 たとえば、NetX がディレクトリ "\threadx\arm7\NetX" にインストールされている場合は、nx_crypto *.* ディレクトリを "\threadx\arm7\NetXCrypto" にコピーする必要があります。

NetX Crypto をスタンドアロン モードで使用するには、前述したディストリビューション全体をアプリケーション プロジェクトにコピーする必要があります。 たとえば、**crypto_libraries** ディレクトリをアプリケーション プロジェクトにコピーするか、**crypto_libraries** ディレクトリを含むライブラリ プロジェクトを作成して、アプリケーション プロジェクトにリンクする必要があります。 

## <a name="using-netx-crypto"></a>NetX Crypto の使用

NetX Crypto の使用は簡単です。 基本的に、アプリケーション コードで *nx_crypto.h* をインクルードする必要があります。  *nx_crypto.h* をインクルードすると、このガイドで後述する NetX Crypto 関数呼び出しを、アプリケーション コードで行えるようになります。

## <a name="configuration-options"></a>構成オプション

NetX Crypto のビルド時にはいくつかの構成オプションがあります。 以下に、すべてのオプションの一覧と、それぞれの詳細な説明を示します。

- **NX_CRYPTO_MAX_RSA_MODULUS_SIZE**: このオプションが定義されている場合、予期される最大の RSA モジュラスがビット単位で示されます。 4096 ビット モジュラスの既定値は 4096 です。 その他の値として 3072、2048、1024 (非推奨) を指定できます。
- **NX_CRYPTO_FIPS**: このオプションが定義されている場合、FIPS に準拠した使用のために必要な追加のセキュリティ機能が有効になります。 このオプションは、FIPS でないビルドに対しては有効になりません。
- **NX_CRYPTO_STANDALONE_ENABLE**: 定義されている場合、NetX Crypto をスタンドアロン モード (Azure RTOS なし) で使用できるようになります。 既定では、このシンボルは定義されません。
