---
title: 第 1 章 - Azure RTOS NetX Secure DTLS の概要
description: Azure RTOS NetX Secure DTLS は、ThreadX ベースの埋め込みアプリケーション向けに設計されたデータグラム トランスポート層セキュリティ プロトコルのリアルタイムの実装です。
author: philmea
ms.author: philmea
ms.date: 06/04/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: a7fe51fd1e141c0c525a98986ca3058732b61843f8bd79bf24fc5ac986147501
ms.sourcegitcommit: 93d716cf7e3d735b18246d659ec9ec7f82c336de
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 08/07/2021
ms.locfileid: "116797043"
---
# <a name="chapter-1-introduction-to-azure-rtos-netx-secure-dtls"></a>第 1 章: Azure RTOS NetX Secure DTLS の概要

Azure RTOS NetX Secure DTLS は、ThreadX ベースの埋め込みアプリケーション専用に設計されたデータグラム トランスポート層セキュリティ プロトコルの高パフォーマンスでリアルタイムの実装です。 この章では、NetX Secure DTLS の概要と、そのアプリケーションおよび利点について説明します。

## <a name="netx-secure-unique-features"></a>NetX Secure 固有の機能

他のほとんどの TLS/DTLS の実装とは異なり、NetX Secure は、さまざまな埋め込みハードウェア プラットフォームがサポートされるようにゼロから設計されており、小さなマイクロコントローラー アプリケーションから、利用可能な最も強力な埋め込みプロセッサまで簡単に拡張できます。 コードは、埋め込みシステムの限られたリソースを考慮して記述されており、TLS または DTLS 経由のセキュリティで保護されたネットワーク通信を提供するために必要なメモリ占有領域を減らすための多くの構成オプションが用意されています。

## <a name="rfcs-supported-by-netx-secure"></a>NetX Secure でサポートされている RFC

NetX Secure では、TLS と DTLS に関連する次のプロトコルがサポートされます。 TLS/DTLS と暗号化に関連する RFC は多数あるため、この一覧は必ずしも包括的であるとは限りません。 NetX Secure は、リアルタイム オペレーティング システムの制約の中で、一般的な推奨事項と基本要件をすべて満たしており、メモリ専有領域が少なく、効率的に実行されます。


| RFC | 説明 |
| --- | ----------- |
| RFC 6347 | データグラム トランスポート層セキュリティ バージョン 1.2。 |
| RFC 2246 | TLS プロトコル バージョン 1.0|
| RFC 4346 | トランスポート層セキュリティ (TLS) プロトコル バージョン 1.1 |
| RFC 5246 | トランスポート層セキュリティ (TLS) プロトコル バージョン 1.2 |
| RFC 5280 | X.509 PKI 証明書 (v3) |
| RFC 3268 | トランスポート層セキュリティ (TLS) 用の Advanced Encryption Standard (AES) 暗号スイート |
| RFC 3447 | 公開キー暗号化標準 (PKCS) #1: RSA 暗号化仕様バージョン 2.1 |
| RFC 2104 | HMAC: メッセージ認証用のキー付きハッシング |
| RFC 6234 | 米国セキュア ハッシュ アルゴリズム (SHA および SHA ベースの HMAC および HKDF) |
| RFC 4279 | TLS 用の事前共有キー暗号スイート |

## <a name="netx-secure-dtls-requirements"></a>NetX Secure DTLS の要件

NetX Secure ランタイム ライブラリを正しく機能させるには、NetX IP インスタンスが既に作成されている必要があります。 さらに、アプリケーションによっては、1 つまたは複数の DER でエンコードされた X.509 デジタル証明書が必要になります。これは、TLS/DTLS インスタンスを識別したり、リモート ホストからの証明書を検証したりするためです。 NetX Secure パッケージに、その他の要件はありません。

## <a name="netx-secure-dtls-constraints"></a>NetX Secure DTLS の制約

NetX Secure DTLS プロトコルでは、DTLS 1.2 で RFC 6347 標準の要件が実装されています。 ただし、次の制約があります。

1. 埋め込みデバイスの性質上、アプリケーションによっては、TLS/DTLS レコードの最大サイズである 16 KB をサポートするためのリソースがない場合があります。 十分なリソースを持つデバイスでは、NetX Secure によって 16 KB のレコードを処理できます。
2. 最低限の証明書の検証。 NetX Secure では、証明書に対して基本的な X.509 チェーン検証が実行され、証明書が有効であり、信頼された証明機関によって署名されていることが確認されます。また、証明書の共通名が提供され、アプリケーションでリモート ホストの最上位のドメイン名と比較できます。 ただし、証明書拡張機能やその他のデータの検証は、アプリケーションの実装者が行う必要があります。
3. ソフトウェアベースの暗号化では、プロセッサが集中的に消費されます。 NetX Secure のソフトウェアベースの暗号化ルーチンは、パフォーマンスのために最適化されてきましたが、ターゲット プロセッサの性能によっては、そのパフォーマンスにより処理が非常に長くなることがあります。 ハードウェアベースの暗号化を使用できる場合は、NetX Secure DTLS を最適なパフォーマンスにするために使用してください。
