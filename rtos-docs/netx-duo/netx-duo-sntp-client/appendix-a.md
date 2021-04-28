---
title: 付録 A - Azure RTOS NetX Duo SNTP の致命的なエラー コード
description: 次のエラー コードにより、Azure RTOS NetX Duo SNTP クライアントは、現在のサーバーとの間で時刻更新を中止します。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 065e7a3e65b3cf8d7fcfb34bb9568a673791609a
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810577"
---
# <a name="appendix-a---azure-rtos-netx-duo-sntp-fatal-error-codes"></a>付録 A - Azure RTOS NetX Duo SNTP の致命的なエラー コード

次のエラー コードにより、Azure RTOS NetX Duo SNTP クライアントは、現在のサーバーとの間で時刻更新を中止します。 アプリケーションにより、使用可能なサーバーの SNTP クライアント リストからサーバーを削除するか、リスト上にある次に使用可能なサーバーに切り替えるかが決まります。 各エラー状態は *nxd_sntp_client.h で定義されています。 *

SNTP クライアントからアプリケーションへ下のリストにあるエラーが返された場合は、サーバーを別のサーバーに置き換えることをお勧めします。 NX_SNTP_KOD_REMOVE_SERVER エラー状態の設定は、SNTP クライアントの致命的状態ハンドラー (コールバック関数) に委任されていることに注意してください。

- NX_SNTP_KOD_REMOVE_SERVER 0xD0C  
- NX_SNTP_SERVER_AUTH_FAIL 0xD0D  
- NX_SNTP_INVALID_NTP_VERSION 0xD11  
- NX_SNTP_INVALID_SERVER_MODE 0xD12  
- NX_SNTP_INVALID_SERVER_STRATUM 0xD15  

SNTP クライアントからアプリケーションへ下のリストにあるエラーが返された場合は、サーバーが有効な時刻更新を一時的に実行できていないだけであるため、削除する必要はありません。

- HNX_SNTP_NO_UNICAST_FROM_SERVER 0xD09  
- NX_SNTP_SERVER_CLOCK_NOT_SYNC 0xD0A  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD0B  
- NX_SNTP_OVER_BAD_UPDATE_LIMIT 0xD17  
- NX_SNTP_BAD_SERVER_ROOT_DISPERSION 0xD16  
- NX_SNTP_INVALID_RTT_TIME 0xD21  
- NX_SNTP_KOD_SERVER_NOT_AVAILABLE 0xD24