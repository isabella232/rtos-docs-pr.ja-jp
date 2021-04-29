---
title: 第 2 章 - Azure RTOS NetX LWM2M のインストールと使用
description: この章では、Azure RTOS NetX LWM2M コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 8c13d3b092d3a5b59bd0369f6ffc162509d02590
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104811516"
---
# <a name="chapter-2---installation-and-use-of-azure-rtos-netx-lwm2m"></a><span data-ttu-id="92288-103">第 2 章 - Azure RTOS NetX LWM2M のインストールと使用</span><span class="sxs-lookup"><span data-stu-id="92288-103">Chapter 2 - Installation and use of Azure RTOS NetX LWM2M</span></span>

<span data-ttu-id="92288-104">この章では、Azure RTOS NetX LWM2M コンポーネントのインストール、設定、および使用に関連するさまざまな問題について説明します。</span><span class="sxs-lookup"><span data-stu-id="92288-104">This chapter contains a description of various issues related to installation, setup, and usage of the Azure RTOS NetX LWM2M component.</span></span>

## <a name="product-distribution"></a><span data-ttu-id="92288-105">製品の配布</span><span class="sxs-lookup"><span data-stu-id="92288-105">Product Distribution</span></span>

<span data-ttu-id="92288-106">NetX LWM2M は [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx) で入手できます。</span><span class="sxs-lookup"><span data-stu-id="92288-106">NetX LWM2M is available at [https://github.com/azure-rtos/netx](https://github.com/azure-rtos/netx).</span></span> <span data-ttu-id="92288-107">パッケージには、次のような 3 つのソース ファイル、1 つのインクルード ファイル、およびこのドキュメントを含む PDF ファイルが含まれています。</span><span class="sxs-lookup"><span data-stu-id="92288-107">The package includes three source files, one include files, and a PDF file that contains this document, as follows:</span></span>

- <span data-ttu-id="92288-108">**nx_lwm2m_client.h**: NetX LWM2M クライアント用のヘッダー ファイル</span><span class="sxs-lookup"><span data-stu-id="92288-108">**nx_lwm2m_client.h**: Header file for the NetX LWM2M Client</span></span>

- <span data-ttu-id="92288-109">**nx_lwm2m_\*.c/h**: NetX LWM2M の C/H ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="92288-109">**nx_lwm2m_\*.c/h**: C/H Source files for NetX LWM2M</span></span>

- <span data-ttu-id="92288-110">**demo_netx_lwm2m_client.c**: NetX LWM2M クライアント デモの C ソース ファイル</span><span class="sxs-lookup"><span data-stu-id="92288-110">**demo_netx_lwm2m_client.c**: C Source file for NetX LWM2M Client Demo</span></span>

- <span data-ttu-id="92288-111">**NetX_LWM2M_User_Guide.pdf**: NetX LWM2M 製品の PDF 説明書</span><span class="sxs-lookup"><span data-stu-id="92288-111">**NetX_LWM2M_User_Guide.pdf**: PDF description of NetX LWM2M product</span></span>

## <a name="netx-lwm2m-installation"></a><span data-ttu-id="92288-112">NetX LWM2M のインストール</span><span class="sxs-lookup"><span data-stu-id="92288-112">NetX LWM2M Installation</span></span>

<span data-ttu-id="92288-113">NetX LWM2M を使用するには、前述のディストリビューション全体を NetX がインストールされているのと同じディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="92288-113">In order to use NetX LWM2M, the entire distribution mentioned previously should be copied to the same directory where NetX is installed.</span></span> <span data-ttu-id="92288-114">たとえば、NetX がディレクトリ " *\\threadx\\arm7\\green*" にインストールされている場合は、*nx_lwm2m&#42;.&#42;* ファイルをこのディレクトリにコピーする必要があります。</span><span class="sxs-lookup"><span data-stu-id="92288-114">For example, if NetX is installed in the directory "*\\threadx\\arm7\\green*" then the *nx_lwm2m&#42;.&#42;* files should be copied into this directory.</span></span>

## <a name="using-netx-lwm2m"></a><span data-ttu-id="92288-115">NetX LWM2M の使用</span><span class="sxs-lookup"><span data-stu-id="92288-115">Using NetX LWM2M</span></span>

<span data-ttu-id="92288-116">NetX LWM2M は簡単に使用できます。</span><span class="sxs-lookup"><span data-stu-id="92288-116">Using NetX LWM2M is easy.</span></span> <span data-ttu-id="92288-117">基本的には、アプリケーション コードに ThreadX と NetX を使用するための *tx_api.h* と *nx_api.h* をインクルードしてから *nx_lwm2m_client.h* をインクルードする必要があります。</span><span class="sxs-lookup"><span data-stu-id="92288-117">Basically, the application code must include *nx_lwm2m_client.h* after it includes *tx_api.h* and *nx_api.h*, in order to use ThreadX and NetX.</span></span> <span data-ttu-id="92288-118">*nx_lwm2m_client.h* をインクルードすると、このガイドで後述する NetX LWM2M 関数呼び出しを、アプリケーション コードで実行できるようになります。</span><span class="sxs-lookup"><span data-stu-id="92288-118">Once *nx_lwm2m_client.h* is included, the application code is then able to make the NetX LWM2M function calls specified later in this guide.</span></span> <span data-ttu-id="92288-119">また、アプリケーションによって、*nx_lwm2m&#42;.&#42;* ファイルを NetX ライブラリにインポートする必要があります。</span><span class="sxs-lookup"><span data-stu-id="92288-119">The application must also import the *nx_lwm2m&#42;.&#42;* files into the NetX library.</span></span>

## <a name="configuration-options"></a><span data-ttu-id="92288-120">構成オプション</span><span class="sxs-lookup"><span data-stu-id="92288-120">Configuration Options</span></span>

<span data-ttu-id="92288-121">LWM2M クライアントを使用して LWM2M クライアント ライブラリとアプリケーションを構築する場合、構成オプションがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="92288-121">There are several configuration options when building the LWM2M Client library and the application using the LWM2M Client.</span></span> <span data-ttu-id="92288-122">構成オプションは、アプリケーション ソース内に定義できます。他に指定がない場合、コマンド ラインで指定できます。</span><span class="sxs-lookup"><span data-stu-id="92288-122">The configuration options can be defined in the application source, on the command line, unless otherwise specified.</span></span>

### <a name="nx_lwm2m_client_disable_error_checking"></a><span data-ttu-id="92288-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span><span class="sxs-lookup"><span data-stu-id="92288-123">NX_LWM2M_CLIENT_DISABLE_ERROR_CHECKING</span></span>

<span data-ttu-id="92288-124">定義すると、基本的な LWM2M エラー チェック API が削除され、パフォーマンスが向上します。</span><span class="sxs-lookup"><span data-stu-id="92288-124">Defined, removes the basic LWM2M Client error checking API and improves performance.</span></span> <span data-ttu-id="92288-125">エラー チェックを無効にしても影響を受けない API リターン コードは、API 定義内で太字で表示されます。</span><span class="sxs-lookup"><span data-stu-id="92288-125">API return codes not affected by disabling error checking are listed in bold typeface in the API definition.</span></span>

### <a name="nx_lwm2m_client_disable_float"></a><span data-ttu-id="92288-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span><span class="sxs-lookup"><span data-stu-id="92288-126">NX_LWM2M_CLIENT_DISABLE_FLOAT</span></span>

<span data-ttu-id="92288-127">定義されている場合、浮動小数点数の値のサポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="92288-127">Defined, removes the support of floating point numbers values.</span></span> <span data-ttu-id="92288-128">無効にした場合、LWM2M クライアントで、Float データ型のリソースをサポートできなくなります。</span><span class="sxs-lookup"><span data-stu-id="92288-128">When disabled the LWM2M Client cannot support Resources with Float data type.</span></span>

### <a name="nx_lwm2m_client_disable_float64"></a><span data-ttu-id="92288-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span><span class="sxs-lookup"><span data-stu-id="92288-129">NX_LWM2M_CLIENT_DISABLE_FLOAT64</span></span>

<span data-ttu-id="92288-130">定義されている場合、64 ビットの浮動小数点数の値のサポートを削除します。</span><span class="sxs-lookup"><span data-stu-id="92288-130">Defined, removes the support of 64-bit floating point numbers values.</span></span> <span data-ttu-id="92288-131">LWM2M クライアントでは、64 ビットの浮動小数点数を含む TLV メッセージを受信できますが、値は 32 ビットの浮動小数点に変換されて処理されます。</span><span class="sxs-lookup"><span data-stu-id="92288-131">The LWM2M Client can still receive TLV messages containing 64-bit floating numbers, but the values are converted to 32-bit floating point for processing.</span></span>

### <a name="nx_lwm2m_client_priority"></a><span data-ttu-id="92288-132">NX_LWM2M_CLIENT_PRIORITY</span><span class="sxs-lookup"><span data-stu-id="92288-132">NX_LWM2M_CLIENT_PRIORITY</span></span>

<span data-ttu-id="92288-133">LWM2M クライアント スレッドの優先順位を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-133">Specifies the priority of the LWM2M Client thread.</span></span> <span data-ttu-id="92288-134">既定では、この値は優先順位 16 を示す 16 に定義されます。</span><span class="sxs-lookup"><span data-stu-id="92288-134">By default, this value is defined as 16 to specify priority 16.</span></span>

### <a name="nx_lwm2m_client_max_device_errors"></a><span data-ttu-id="92288-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span><span class="sxs-lookup"><span data-stu-id="92288-135">NX_LWM2M_CLIENT_MAX_DEVICE_ERRORS</span></span>

<span data-ttu-id="92288-136">デバイス オブジェクトによって格納されるエラー コードの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-136">Specifies the maximum number of error codes stored by the Device Object.</span></span> <span data-ttu-id="92288-137">既定値は 8 です。</span><span class="sxs-lookup"><span data-stu-id="92288-137">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_security_instances"></a><span data-ttu-id="92288-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="92288-138">NX_LWM2M_CLIENT_MAX_SECURITY_INSTANCES</span></span>

<span data-ttu-id="92288-139">セキュリティ オブジェクト インスタンスの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-139">Specifies the maximum number of Security Object Instances.</span></span> <span data-ttu-id="92288-140">既定値は 2 であり、ブートストラップ サーバーと標準サーバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="92288-140">The default value is 2 for supporting a Bootstrap Server and a standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_instances"></a><span data-ttu-id="92288-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="92288-141">NX_LWM2M_CLIENT_MAX_SERVER_INSTANCES</span></span>

<span data-ttu-id="92288-142">サーバー オブジェクト インスタンスの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-142">Specifies the maximum number of Server Object Instances.</span></span> <span data-ttu-id="92288-143">既定値は 1 であり、1 台の標準サーバーがサポートされます。</span><span class="sxs-lookup"><span data-stu-id="92288-143">The default value is 1 for supporting a single standard Server.</span></span>

### <a name="nx_lwm2m_client_max_server_uri"></a><span data-ttu-id="92288-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span><span class="sxs-lookup"><span data-stu-id="92288-144">NX_LWM2M_CLIENT_MAX_SERVER_URI</span></span>

<span data-ttu-id="92288-145">終端の nil 文字を含むサーバー URI の最大長を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-145">Specifies the maximum length of a server URI, including terminating nil character.</span></span> <span data-ttu-id="92288-146">既定値は 128 です。</span><span class="sxs-lookup"><span data-stu-id="92288-146">The default value is 128.</span></span>

### <a name="nx_lwm2m_client_max_access_control_instances"></a><span data-ttu-id="92288-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span><span class="sxs-lookup"><span data-stu-id="92288-147">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_INSTANCES</span></span>

<span data-ttu-id="92288-148">アクセス制御インスタンスの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-148">Specifies the maximum number of Access Control Instances.</span></span> <span data-ttu-id="92288-149">既定値は 0 です。これにより、アクセス制御は無効になります。</span><span class="sxs-lookup"><span data-stu-id="92288-149">The default value is 0, which disables access control.</span></span> <span data-ttu-id="92288-150">アプリケーションで複数の LWM2M サーバーがサポートされている場合は、アクセス制御インスタンスの最大数を、LWM2M クライアントがサポートするオブジェクト インスタンスの最大数に設定する必要があります。これは、オブジェクト インスタンスごとに 1 つのアクセス制御インスタンスを作成する必要があるためです (セキュリティ オブジェクト インスタンスは除きます)。</span><span class="sxs-lookup"><span data-stu-id="92288-150">If the application supports more than one LWM2M Server, the maximum number of Access Control Instances must be set to the maximum number of Object Instances that the LWM2M Client will support, as one Access Control Instance must be created for each Object Instance (except for the Security Object Instances).</span></span>

### <a name="nx_lwm2m_client_max_access_control_acls"></a><span data-ttu-id="92288-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span><span class="sxs-lookup"><span data-stu-id="92288-151">NX_LWM2M_CLIENT_MAX_ACCESS_CONTROL_ACLS</span></span>

<span data-ttu-id="92288-152">アクセス制御インスタンスあたりの ACL リソースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-152">Specifies the maximum number of ACL resources per Access Control Instance.</span></span> <span data-ttu-id="92288-153">既定値は 4 です。</span><span class="sxs-lookup"><span data-stu-id="92288-153">The default value is 4.</span></span>

### <a name="nx_lwm2m_client_max_notifications"></a><span data-ttu-id="92288-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span><span class="sxs-lookup"><span data-stu-id="92288-154">NX_LWM2M_CLIENT_MAX_NOTIFICATIONS</span></span>

<span data-ttu-id="92288-155">LWM2M クライアントでサポートする通知の最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-155">Specifies the maximum number of notifications that the LWM2M Client will support.</span></span> <span data-ttu-id="92288-156">LWM2M サーバーでは、オブジェクト、オブジェクト インスタンス、およびリソースに関する通知を設定できます。</span><span class="sxs-lookup"><span data-stu-id="92288-156">A LWM2M Server can set notifications on Objects, Object Instances, and Resources.</span></span> <span data-ttu-id="92288-157">既定値は 8 です。</span><span class="sxs-lookup"><span data-stu-id="92288-157">The default value is 8.</span></span>

### <a name="nx_lwm2m_client_max_resources"></a><span data-ttu-id="92288-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span><span class="sxs-lookup"><span data-stu-id="92288-158">NX_LWM2M_CLIENT_MAX_RESOURCES</span></span>

<span data-ttu-id="92288-159">オブジェクトごとのリソースの最大数を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-159">Specifies the maximum number of Resources per Object.</span></span> <span data-ttu-id="92288-160">既定値は 32 です。</span><span class="sxs-lookup"><span data-stu-id="92288-160">The default value is 32.</span></span>

### <a name="nx_lwm2m_client_bootstrap_idle_timer"></a><span data-ttu-id="92288-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span><span class="sxs-lookup"><span data-stu-id="92288-161">NX_LWM2M_CLIENT_BOOTSTRAP_IDLE_TIMER</span></span>

<span data-ttu-id="92288-162">ブートストラップ セッションが開始されたときに、セッションを中止するまでの最大待機時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-162">Specifies the maximum time to wait for bootstrap server requests when the bootstrap session is initiated before aborting the session.</span></span> <span data-ttu-id="92288-163">既定値は 60 秒です。</span><span class="sxs-lookup"><span data-stu-id="92288-163">The default value is 60 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_start_timeout"></a><span data-ttu-id="92288-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92288-164">NX_LWM2M_CLIENT_DTLS_START_TIMEOUT</span></span>

<span data-ttu-id="92288-165">DTLS ハンドシェイクの完了を待機する最大時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-165">Specifies the maximum time to wait for DTLS handshake completion.</span></span> <span data-ttu-id="92288-166">既定値は 30 秒です。</span><span class="sxs-lookup"><span data-stu-id="92288-166">The default value is 30 seconds.</span></span>

### <a name="nx_lwm2m_client_dtls_end_timeout"></a><span data-ttu-id="92288-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span><span class="sxs-lookup"><span data-stu-id="92288-167">NX_LWM2M_CLIENT_DTLS_END_TIMEOUT</span></span>

<span data-ttu-id="92288-168">DTLS シャットダウンの完了を待機する最大時間を指定します。</span><span class="sxs-lookup"><span data-stu-id="92288-168">Specifies the maximum time to wait for DTLS shutdown completion.</span></span> <span data-ttu-id="92288-169">既定値は 5 秒です。</span><span class="sxs-lookup"><span data-stu-id="92288-169">The default value is 5 seconds.</span></span>
