---
title: 第 1 章 - Azure RTOS NetX Crypto の概要
description: NetX Crypto は、データ暗号化および認証サービスを提供するように設計された、暗号アルゴリズムのハイパフォーマンス リアルタイム実装です。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 1b5ee0336ba9e867a628dc5db4f0c029f68ff45c81d68ceb6299e3469d5e2b49
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116796805"
---
# <a name="chapter-1---introduction-to-azure-rtos-netx-crypto"></a>第 1 章 - Azure RTOS NetX Crypto の概要

Azure RTOS NetX Crypto は、データ暗号化および認証サービスを提供するように設計された、暗号アルゴリズムのハイパフォーマンス リアルタイム実装です。 NetX Crypto は、NetX Secure TLS、DTLS、IPsec の各モジュールにプラグインするように設計されています。 アプリケーションでは、ネットワーク セキュリティの範囲外でスタンドアロンのモジュールとして NetX Crypto を使用することもできます。

## <a name="netx-crypto-unique-features"></a>NetX Crypto 独自の機能

NetX Crypto は標準 C 言語 (C99) で実装されており、ほぼすべての C/C++ コンパイラと互換性があります。 モジュール設計により、アプリケーションは、使用する必要がある暗号アルゴリズムにのみリンクできるため、最小限のコード サイズを実現できます。 この実装は、ほとんどの 32 ビット マイクロプロセッサで動作するように設計されており、基本的な算術演算 (加算、減算、乗算、除算、論理 AND、OR、NOR、およびビット シフト演算) のみが使用されます。 これらの操作はすべて 32 ビット量で使用されるので、ほとんどの 32 ビット マイクロプロセッサ間で NetX Crypto を移植できます。 この実装は、リソースに制約があるマイクロプロセッサで動作するように特別に最適化されており、深く組み込まれたアプリケーションを対象としています。

## <a name="algorithms-supported-by-netx-crypto"></a>NetX Crypto でサポートされているアルゴリズム

NetX Crypto では、次の暗号アルゴリズムがサポートされています。 NetX Crypto は、小さなメモリ占有領域と効率的な実行を必要とするリアルタイム オペレーティング システムおよびプラットフォームの制約の範囲内で、一般的な推奨事項と基本要件をすべて満たしています。

| アルゴリズム       | キーの長さ (ビット)      |
| --------------- | ---------------------- |
| AES (CBC、CTR)   | 128、192、256          |
| AES (XCBC)       | 128                    |
| AES-CCM 8       | 128                    |
| 3DES (CBC)       | 192                    |
| HMAC-SHA1       | 任意の長さ             |
| HMAC-SHA224     | 任意の長さ             |
| HMAC-SHA256     | 任意の長さ             |
| HMAC-SHA384     | 任意の長さ             |
| HMAC-SHA512     | 任意の長さ             |
| HMAC-SHA512/224 | 任意の長さ             |
| HMAC-SHA512/256 | 任意の長さ             |
| HMAC-MD5        | 任意の長さ             |
| RSA             | 1024、2048、3072、4096 |

| アルゴリズム       | ダイジェストの長さ (ビット) | ブロック サイズ (ビット) |
| --------------- | -------------------- | ----------------- |
| SHA1            | 160                  | 512               |
| SHA224          | 224                  | 512               |
| SHA256          | 256                  | 512               |
| SHA384          | 384                  | 1024              |
| SHA512          | 512                  | 1024              |
| MD5             | 128                  | 512               |
| HMAC-SHA1       | 160                  | 512               |
| HMAC-SHA224     | 224                  | 512               |
| HMAC-SHA256     | 256                  | 512               |
| HMAC-SHA384     | 384                  | 1024              |
| HMAC-SHA512     | 512                  | 1024              |
| HMAC-SHA512/224 | 224                  | 1024              |
| HMAC-SHA512/256 | 256                  | 1024              |
| HMAC-MD5        | 128                  | 512               |
| 楕円曲線  | P192/224/256/384/521 |                   |

## <a name="netx-crypto-requirements"></a>NetX Crypto の要件

TBD: メモリ要件。 割り込み/再入可能? ディスカッションが必要

## <a name="netx-crypto-constraints"></a>NetX Crypto の制約

[なし] :
