---
title: 第 3 章 - Azure RTOS NetX Crypto の機能の説明
description: この章では、NetX Crypto の機能について説明します。
author: philmea
ms.author: philmea
ms.date: 05/19/2020
ms.topic: article
ms.service: rtos
ms.openlocfilehash: 4ecdbfe99daa000d109908f834b139dcaf321491
ms.sourcegitcommit: e3d42e1f2920ec9cb002634b542bc20754f9544e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 03/22/2021
ms.locfileid: "104810409"
---
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a>第 3 章 - Azure RTOS NetX Crypto の機能の説明

## <a name="execution-overview"></a>実行の概要

この章では、Azure RTOS NetX Crypto の機能について説明します。 NetX Crypto アプリケーションには、初期化とアプリケーション インターフェイスの呼び出しという主に 2 種類のプログラム実行があります。

"*NetX Crypto は、スタンドアロンの暗号化ライブラリとして使用することも、ThreadX、NetX、NetX Secure と共に使用することもできます。* "

## <a name="aes"></a>AES

- **アルゴリズムの標準**: NetX Crypto は、NIST FIPS 197 ([http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf) を参照) に従って AES を実装しています。
- **サポートされているキーの長さ**: 128、192、256
- **サポートされているモード**:
  - CBC、CTR (キーの長さ: 128、192、256 ビット)
  - XCBC (キーの長さ: 128 ビットのみ)
  - CCM8 (キーの長さ: 128 ビットのみ)
- **メモリ要件**: アプリケーションでは、入力バッファーと出力バッファー、および AES 制御構造を指定します。 AES 制御構造により、API の呼び出し間で AES アルゴリズムの状態が維持されます。 入力バッファーには、暗号化または復号化するデータが格納され、任意のサイズを指定できます。 出力バッファーは、AES で処理されるデータを格納するために AES によって使用されます。 出力バッファー サイズは、入力バッファー サイズ以上である必要があり、AES ブロック サイズの 16 バイトの倍数である必要があります。 入力および出力バッファーは連続したメモリである必要があり、インプレース暗号化 (入力と出力に同じメモリを使用) という特殊なケースを除き、重複することはできません。 インプレース暗号化の場合、出力バッファーは入力バッファーとまったく同じ場所から開始されます。出力バッファーを入力バッファーより小さくすることはできません。 AES 暗号化操作をインプレースで実行する場合、追加のスクラッチ メモリは不要です。

## <a name="3des"></a>3DES

- **アルゴリズムの標準**: NetX Crypto は、NIST Special Publication 800-67 rev 2: "*トリプル データ暗号化アルゴリズム (TDES) ブロック暗号の推奨事項*" ([https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final) を参照) に従って、Tripple DES (TDES、3DES とも呼ばれます) を実装しています。
- **サポートされているキーの長さ**: 64 * 3 = 192
- **メモリ要件**: なし

NetX Crypto では、"3DES" という用語は "TDES" と同じ意味で使用されます。

## <a name="md5"></a>MD5

- **アルゴリズムの標準**: NetX Crypto は、RFC 1321: "*MD5 メッセージ ダイジェスト アルゴリズム*" に従って MD5 を実装しています。
- **メモリ要件**: アプリケーションでは、MD5 操作間で状態を維持するために使用される、MD5 制御ブロック構造を提供する必要があります。

## <a name="sha1-sha256512"></a>SHA1、SHA256/512

- **アルゴリズムの標準**: NetX Crypto は、NIST FIPS Publication 180-4: "*セキュア ハッシュ標準*" ([http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf) を参照) に従って、SHA1、SHA256、または SHA512 を実装しています。
- **ハッシュ ブロック サイズ**:
  - SHA1: 160 ビットのハッシュ値
  - SHA 224: 224 ビットのハッシュ値
  - SHA 256: 256 ビットのハッシュ値
  - SHA 384: 384 ビットのハッシュ値
  - SHA 512: 512 ビットのハッシュ値
  - SHA 512/224: 224 ビットのハッシュ値
  - SHA 512/256: 256 ビットのハッシュ値

  NetX Crypto では、SHA256 ルーチンを使用して、SHA256 と SHA224 が渡されます。 SHA512 ルーチンを使用して、SHA512、SHA384、SHA512/224、SHA512/256 が渡されます。
- **メモリ要件:** アプリケーションでは、操作間で状態を維持するために、SHA 制御ブロック構造を提供する必要があります。

## <a name="rsa"></a>RSA

- **標準:** NetX Crypto は、"*PKCS #1 v2.2: RSA 暗号標準*" に従って RSA を実装しています。この標準は、RFC 8017 として公開されており、[https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf) でも参照できます。
- **メモリ要件:** アプリケーションでは、操作間で状態を維持し、中間計算に必要な "スクラッチ" バッファー領域を提供するために、RSA 制御ブロック構造を提供する必要があります。

## <a name="hmac"></a>HMAC

- **標準:** NetX Crypto は、FIPS PUB 198-1: "*キー付きハッシュ メッセージ認証コード (HMAC)* " ([https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf) を参照) に従って HMAC を実装しています。
- **メモリ要件:** アプリケーションでは、操作間で状態を維持するために、HMAC 制御ブロック構造を提供する必要があります。 提供する実際の制御ブロックは、必要な基になるハッシュ操作 (SHA1、MD5 など) によって異なります。

## <a name="elliptic-curve"></a>楕円曲線

- **標準:** NetX Crypto は楕円曲線を実装しています。 サポートされている名前付き曲線は次のとおりです (プライム フィールドのみ)。
  - P-192
  - P-224
  - P-256
  - P-384
  - P-521

   > [!TIP]
   > 非圧縮形式がサポートされています。 SEC1-v1 のセクション 2.3.3 および 2.3.4 を参照してください ([http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf))。

- **メモリ要件:** なし

## <a name="ecdsa"></a>ECDSA

- **標準:** NetX Crypto は、FIPS PUB 186-4: "*デジタル署名標準 (DSS)* " ([https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf) を参照) に従って ECDSA を実装しています。
- **メモリ要件:** アプリケーションでは、操作間で状態を維持するために、ECDSA 制御ブロック構造を提供する必要があります。

## <a name="ecdh"></a>ECDH

> [!IMPORTANT]
> Azure RTOS 6.0 では、静的秘密キーを使用する ECDH は入力ポイントの検証をセキュリティで保護する必要があるため、ECDH ルーチンは ECDHE 暗号にのみ使用する必要があります。

- **標準:** NetX Crypto は、FIPS PUB 800-56Ar2: "離散対数暗号を使用したペアワイズ キー確立スキームの推奨事項" ([https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf) を参照) に従って ECDH を実装しています。
- **メモリ要件:** アプリケーションでは、操作間で状態を維持するために、ECDH 制御ブロック構造を提供する必要があります。

## <a name="drbg"></a>DRBG

- **標準:** NetX Crypto は、FIPS PUB 800-90Ar1: "決定論的ランダム ビット ジェネレーターを使用した乱数生成の推奨事項" ([https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf) を参照) に従って DRBG を実装しています。
- **メモリ要件:** アプリケーションでは、操作間で状態を維持するために、DRBG 制御ブロック構造を提供する必要があります。

## <a name="fips-compliant"></a>FIPS 準拠

NetX Crypto FIPS 140-2