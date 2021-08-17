---
title: 第 2 章 - Azure RTOS NetX LWM2M のインストールと使用
description: この章では、Azure RTOS NetX LWM2M コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 3ad8963c342e907201074559929f3a7a2d70c9f13e135cd95c9a2e9b224e17cf
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116791229"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a>第 2 章 - Azure RTOS NetX LWM2M のインストールと使用

この章では、Azure RTOS NetX LWM2M コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。

## <a name="product-distribution"></a>製品の配布

NetX LWM2M は [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。 パッケージには、次のような 3 つのソース ファイル、1 つのインクルード ファイル、およびこのドキュメントを含む PDF ファイルが含まれています。

- **nx_lwm2m_client.h**: NetX LWM2M クライアント用のヘッダー ファイル

- **nx_lwm2m_*.c/h**: NetX LWM2M の C/H ソース ファイル

- **demo_netx_lwm2m_client.c**: NetX LWM2M クライアント デモの C ソース ファイル

- **NetX_LWM2M_User_Guide.pdf**: NetX LWM2M 製品の PDF 説明書

## <a name="netx-lwm2m-installation"></a>NetX LWM2M のインストール

NetX LWM2M を使用するには、前述のディストリビューション全体を NetX がインストールされているのと同じディレクトリにコピーする必要があります。 たとえば、NetX がディレクトリ " *\\threadx\\arm7\\green*" にインストールされている場合は、*nx_lwm2m&#42;.&#42;* ファイルをこのディレクトリにコピーする必要があります。

## <a name="using-netx-lwm2m"></a>NetX LWM2M の使用

NetX LWM2M は簡単に使用できます。 基本的には、アプリケーション コードに ThreadX と NetX を使用するための *tx_api.h* と *nx_api.h* をインクルードしてから *nx_lwm2m_client.h* をインクルードする必要があります。 *nx_lwm2m_client.h* をインクルードすると、このガイドで後述する NetX LWM2M 関数呼び出しを、アプリケーション コードで実行できるようになります。 また、アプリケーションによって、*nx_lwm2m&#42;.&#42;* ファイルを NetX ライブラリにインポートする必要があります。

## <a name="configuration-options"></a>構成オプション

LWM2M クライアントを使用して LWM2M クライアント ライブラリとアプリケーションを構築する場合、構成オプションがいくつかあります。 構成オプションは、アプリケーション ソース内に定義できます。他に指定がない場合、コマンド ラインで指定できます。

### <a name="nx_lwm2m_client_disable_error_checking"></a>NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING

定義すると、基本的な LWM2M エラー チェック API が削除され、パフォーマンスが向上します。 エラー チェックを無効にしても影響を受けない API リターン コードは、API 定義内で太字で表示されます。

### <a name="nx_lwm2m_client_disable_float"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT

定義されている場合、浮動小数点数の値のサポートを削除します。 無効にした場合、LWM2M クライアントで、Float データ型のリソースをサポートできなくなります。

### <a name="nx_lwm2m_client_disable_float64"></a>NX_LWM2M_CLIENT_DISABLE_FLOAT64

定義されている場合、64 ビットの浮動小数点数の値のサポートを削除します。 LWM2M クライアントでは、64 ビットの浮動小数点数を含む TLV メッセージを受信できますが、値は 32 ビットの浮動小数点に変換されて処理されます。

### <a name="nx_lwm2m_client_priority"></a>NX_LWM2M_CLIENT_PRIORITY

LWM2M クライアント スレッドの優先順位を指定します。 既定では、この値は優先順位 16 を示す 16 に定義されます。

### <a name="nx_lwm2m_client_max_device_errors"></a>NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS

デバイス オブジェクトによって格納されるエラー コードの最大数を指定します。 既定値は 8 です。

### <a name="nx_lwm2m_client_max_security_instances"></a>NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES

セキュリティ オブジェクト インスタンスの最大数を指定します。 既定値は 2 であり、ブートストラップ サーバーと標準サーバーがサポートされます。

### <a name="nx_lwm2m_client_max_server_instances"></a>NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES

サーバー オブジェクト インスタンスの最大数を指定します。 既定値は 1 であり、1 台の標準サーバーがサポートされます。

### <a name="nx_lwm2m_client_max_server_uri"></a>NX_LWM2M_CLIENT_MAX_SERVER_URI

終端の nil 文字を含むサーバー URI の最大長を指定します。 既定値は 128 です。

### <a name="nx_lwm2m_client_max_access_control_instances"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES

アクセス制御インスタンスの最大数を指定します。 既定値は 0 です。これにより、アクセス制御は無効になります。 アプリケーションで複数の LWM2M サーバーがサポートされている場合は、アクセス制御インスタンスの最大数を、LWM2M クライアントがサポートするオブジェクト インスタンスの最大数に設定する必要があります。これは、オブジェクト インスタンスごとに 1 つのアクセス制御インスタンスを作成する必要があるためです (セキュリティ オブジェクト インスタンスは除きます)。

### <a name="nx_lwm2m_client_max_access_control_acls"></a>NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS

アクセス制御インスタンスあたりの ACL リソースの最大数を指定します。 既定値は 4 です。

### <a name="nx_lwm2m_client_max_notifications"></a>NX_LWM2M_CLIENT_MAX_NOTIFICATIONS

LWM2M クライアントでサポートする通知の最大数を指定します。 LWM2M サーバーでは、オブジェクト、オブジェクト インスタンス、およびリソースに関する通知を設定できます。 既定値は 8 です。

### <a name="nx_lwm2m_client_max_resources"></a>NX_LWM2M_CLIENT_MAX_RESOURCES

オブジェクトごとのリソースの最大数を指定します。 既定値は 32 です。

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a>NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER

ブートストラップ セッションが開始されたときに、セッションを中止するまでの最大待機時間を指定します。 既定値は 60 秒です。

### <a name="nx_lwm2m_client_dtls_start_timeout"></a>NX_LWM2M_CLIENT_DTLS_START_TIMEOUT

DTLS ハンドシェイクの完了を待機する最大時間を指定します。 既定値は 30 秒です。

### <a name="nx_lwm2m_client_dtls_end_timeout"></a>NX_LWM2M_CLIENT_DTLS_END_TIMEOUT

DTLS シャットダウンの完了を待機する最大時間を指定します。 既定値は 5 秒です。
