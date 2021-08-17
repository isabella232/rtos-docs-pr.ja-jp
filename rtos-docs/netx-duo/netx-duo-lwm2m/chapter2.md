---
title: 第 2 章 - RTOS NetX Duo LWM2M クライアントのインストールと使用
description: この章では、RTOS NetX Duo LWM2M クライアントをインストールして使用する方法について説明します。
author: v-condav
ms.author: v-condav
ms.date: 01/22/2021
ms.topic: article
ms.service: rtos
ms.openlocfilehash: f804ae59dd639ca05d1b8f5251cf8b878e78bb9ad2575e08c21d43b14e727a19
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796516"
---
# <a name="chapter-2--installation-and-use-of-lwm2m-client"></a>第 2 章 - LWM2M クライアントのインストールと使用

この章では、LWM2M クライアント コンポーネントのインストール、セットアップ、および使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

Azure RTOS LWM2M クライアントは、[https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m](https://github.com/azure-rtos/netxduo/tree/master/addons/lwm2m/) のパブリック ソース コード リポジトリから入手できます。 パッケージには、次のような 3 つのソース ファイルとインクルード ファイルが含まれています。

* **nx\_lwm2m\_client.h**: LWM2M クライアント用のヘッダー ファイル

* **nx\_lwm2m\_client.c**: LWM2M クライアントの C ソース ファイル

* **demo\_netx\_lwm2m\_client.c**: LWM2M クライアント デモの C ソース ファイル

## <a name="lwm2m-client-installation"></a>LWM2M クライアントのインストール

LWM2M クライアントは NetX Duo の一部です。 このため、NetX Duo を GitHub リポジトリから複製した後、***netxduo/addons/lwm2m*** で LWM2M クライアントのソースを見つけることができます。

## <a name="using-lwm2m_client"></a>LWM2M\_Client の使用

LWM2M クライアントの使用は簡単です。 基本的には、アプリケーション コードに ThreadX と NetX を使用するための ****_* _tx\_api.h_ *_ と _* _nx\_api.h_ *_ をインクルードしてから nx\_lwm2m\_client.h*_ をインクルードする必要があります。_* _nx\_lwm2m\_client.h_ *_ がインクルードされると、このガイドの後半に記載されている LWM2M クライアント関数呼び出しをアプリケーション コードで実行できるようになります。また、アプリケーションによって _* _nx\_lwm2m\_client\_.\**** ファイルを NetX ライブラリにインポートする必要があります。

## <a name="configuration-options"></a>構成オプション

LWM2M クライアントを使用して LWM2M クライアント ライブラリとアプリケーションを構築する場合、構成オプションがいくつかあります。 構成オプションは、アプリケーション ソース内に定義できます。他に指定がない場合、コマンド ラインで指定できます。

| 構成&nbsp;オプション | 説明 |
| --- | --- |
| **NX\_LWM2M\_CLIENT\_MTU** | CoAP のメッセージの最大サイズを指定します (IP ヘッダーと UDP ヘッダーを含みます)。 既定値は 1280 です。 |
| **NX\_LWM2M\_CLIENT\_SOCKET\_TOS** | LwM2M UDP に必要なサービスの種類。 既定では、この値は通常の IP パケット サービスを示す NX\_IP\_NORMAL と定義されます。 |
| **NX\_LWM2M\_CLIENT\_SOCKET\_TTL** | このパケットが通過できるルーターの数を指定します。この数を超えるとパケットは破棄されます。 既定値は 0x80 に設定されます。 |
| **NX\_LWM2M\_CLIENT\_SOCKET\_QUEUE\_MAX** | 受信キューの最大深度数を指定します。 既定値は 4 に設定されています。 |
| **NX\_LWM2M\_CLIENT\_MAX\_COAP\_URI\_PATH** | CoAP Uri-Path オプションの最大長を指定します。 既定値は 32 に設定されます。 |
| **NX\_LWM2M\_CLIENT\_MAX\_DEVICE\_ERRORS** | デバイス オブジェクトによって格納されるエラー コードの最大数を指定します。 既定値は 8 です。 |
| **NX\_LWM2M\_CLIENT\_MAX\_SECURITY\_INSTANCES** | セキュリティ オブジェクト インスタンスの最大数を指定します。 既定値は 2 であり、ブートストラップ サーバーと標準サーバーがサポートされます。 |
| **NX\_LWM2M\_CLIENT\_MAX\_SERVER\_INSTANCES** | サーバー オブジェクト インスタンスの最大数を指定します。 既定値は 1 であり、1 台の標準サーバーがサポートされます。 |
| **NX\_LWM2M\_CLIENT\_MAX\_ACCESS\_CONTROL\_INSTANCES** | アクセス制御インスタンスの最大数を指定します。 既定値は 0 です。これにより、アクセス制御は無効になります。 アプリケーションで複数の LWM2M サーバーがサポートされている場合は、アクセス制御インスタンスの最大数を、LWM2M クライアントがサポートするオブジェクト インスタンスの最大数に設定する必要があります。これは、オブジェクト インスタンスごとに 1 つのアクセス制御インスタンスを作成する必要があるためです (セキュリティ オブジェクト インスタンスは除きます)。 |
| **NX\_LWM2M\_CLIENT\_MAX\_ACCESS\_CONTROL\_ACLS** | アクセス制御インスタンスあたりの ACL リソースの最大数を指定します。 既定値は 4 です。 |
| **NX\_LWM2M\_CLIENT\_MAX\_NOTIFICATIONS** | LWM2M クライアントでサポートする通知の最大数を指定します。 LWM2M サーバーでは、オブジェクト、オブジェクト インスタンス、およびリソースに関する通知を設定できます。 既定値は 8 です。 |
| **NX\_LWM2M\_CLIENT\_MAX\_RESOURCES** | オブジェクトごとのリソースの最大数を指定します。 既定値は 32 です。 |
| **NX\_LWM2M\_CLIENT\_MAX\_MULTIPLE\_RESOURCES** | 複数のリソースのリソース インスタンスの最大数を指定します。 既定値は 8 です。 |
| **NX\_LWM2M\_CLIENT\_BOOTSTRAP\_IDLE\_TIMER** | ブートストラップ セッションが開始されたときに、セッションを中止するまでの最大待機時間を指定します。 既定値は 60 秒です。 |
| **NX\_LWM2M\_CLIENT\_DTLS\_START\_TIMEOUT** | DTLS ハンドシェイクの完了を待機する最大時間を指定します。 既定値は 30 秒です。 |
| **NX\_LWM2M\_CLIENT\_DTLS\_END\_TIMEOUT** | DTLS シャットダウンの完了を待機する最大時間を指定します。 既定値は 5 秒です。 |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SERVER\_URI** | 終端の null 文字を含むサーバー URI の最大長を指定します。 既定値は 128 です。 |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_PUBLIC\_KEY\_OR\_IDENTITY** | DTLS の公開キーまたは ID の最大長を指定します。 既定値は 128 です。 |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SERVER\_PUBLIC\_KEY** | DTLS のサーバー公開キーの最大長を指定します。 既定値は 128 です。 |
| **NX\_LWM2M\_CLIENT\_SECURITY\_MAX\_SECRET\_KEY** | DTLS のシークレット キーの最大長を指定します。 既定値は 128 です。 |
| **NX\_LWM2M\_CLIENT\_HOLD\_OFF** | ブートストラップを開始する前に待機する秒数を指定します。 既定値は 1 秒です。 |
| **NX\_LWM2M\_CLIENT\_LIFE\_TIME** | 登録の有効期間の秒数を指定します。 既定値は 600 秒です。 |
