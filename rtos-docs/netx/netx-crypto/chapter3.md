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
# <a name="chapter-3---functional-description-of-azure-rtos-netx-crypto"></a><span data-ttu-id="a1044-103">第 3 章 - Azure RTOS NetX Crypto の機能の説明</span><span class="sxs-lookup"><span data-stu-id="a1044-103">Chapter 3 - Functional description of Azure RTOS NetX Crypto</span></span>

## <a name="execution-overview"></a><span data-ttu-id="a1044-104">実行の概要</span><span class="sxs-lookup"><span data-stu-id="a1044-104">Execution Overview</span></span>

<span data-ttu-id="a1044-105">この章では、Azure RTOS NetX Crypto の機能について説明します。</span><span class="sxs-lookup"><span data-stu-id="a1044-105">This chapter contains a functional description of Azure RTOS NetX Crypto.</span></span> <span data-ttu-id="a1044-106">NetX Crypto アプリケーションには、初期化とアプリケーション インターフェイスの呼び出しという主に 2 種類のプログラム実行があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-106">There are two primary types of program execution in a NetX Crypto application: initialization and application interface calls.</span></span>

<span data-ttu-id="a1044-107">"*NetX Crypto は、スタンドアロンの暗号化ライブラリとして使用することも、ThreadX、NetX、NetX Secure と共に使用することもできます。* "</span><span class="sxs-lookup"><span data-stu-id="a1044-107">*NetX Crypto can be used as a standalone cryptographic library, or can be used with ThreadX, NetX, and/or NetX Secure.*</span></span>

## <a name="aes"></a><span data-ttu-id="a1044-108">AES</span><span class="sxs-lookup"><span data-stu-id="a1044-108">AES</span></span>

- <span data-ttu-id="a1044-109">**アルゴリズムの標準**: NetX Crypto は、NIST FIPS 197 ([http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf) を参照) に従って AES を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-109">**Algorithm Standard:**:  NetX Crypto implements AES according to NIST FIPS 197, which can be found at: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.197.pdf)</span></span>
- <span data-ttu-id="a1044-110">**サポートされているキーの長さ**: 128、192、256</span><span class="sxs-lookup"><span data-stu-id="a1044-110">**Key Lengths Supported**: 128, 192, 256</span></span>
- <span data-ttu-id="a1044-111">**サポートされているモード**:</span><span class="sxs-lookup"><span data-stu-id="a1044-111">**Modes Supported**:</span></span>
  - <span data-ttu-id="a1044-112">CBC、CTR (キーの長さ: 128、192、256 ビット)</span><span class="sxs-lookup"><span data-stu-id="a1044-112">CBC, CTR, (Key length 128-, 192-, 256-bit)</span></span>
  - <span data-ttu-id="a1044-113">XCBC (キーの長さ: 128 ビットのみ)</span><span class="sxs-lookup"><span data-stu-id="a1044-113">XCBC (key length 128-bit only),</span></span>
  - <span data-ttu-id="a1044-114">CCM8 (キーの長さ: 128 ビットのみ)</span><span class="sxs-lookup"><span data-stu-id="a1044-114">CCM8 (key length 128-bit only)</span></span>
- <span data-ttu-id="a1044-115">**メモリ要件**: アプリケーションでは、入力バッファーと出力バッファー、および AES 制御構造を指定します。</span><span class="sxs-lookup"><span data-stu-id="a1044-115">**Memory Requirements**: Application specifies input buffer and output buffer and an AES control structure.</span></span> <span data-ttu-id="a1044-116">AES 制御構造により、API の呼び出し間で AES アルゴリズムの状態が維持されます。</span><span class="sxs-lookup"><span data-stu-id="a1044-116">The AES control structure maintains AES algorithm state between calls to the API.</span></span> <span data-ttu-id="a1044-117">入力バッファーには、暗号化または復号化するデータが格納され、任意のサイズを指定できます。</span><span class="sxs-lookup"><span data-stu-id="a1044-117">The input buffer contains data to be encrypted or decrypted, and can be arbitrary size.</span></span> <span data-ttu-id="a1044-118">出力バッファーは、AES で処理されるデータを格納するために AES によって使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1044-118">The output buffer is used by AES to store data being processed by AES.</span></span> <span data-ttu-id="a1044-119">出力バッファー サイズは、入力バッファー サイズ以上である必要があり、AES ブロック サイズの 16 バイトの倍数である必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-119">The output buffer size must be no smaller than the input buffer size, and must be a multiple of 16 bytes, the AES block size.</span></span> <span data-ttu-id="a1044-120">入力および出力バッファーは連続したメモリである必要があり、インプレース暗号化 (入力と出力に同じメモリを使用) という特殊なケースを除き、重複することはできません。</span><span class="sxs-lookup"><span data-stu-id="a1044-120">The input and output buffers must be contiguous memory and may not overlap, except in the special case of encrypting in-place (using the same memory for input and output).</span></span> <span data-ttu-id="a1044-121">インプレース暗号化の場合、出力バッファーは入力バッファーとまったく同じ場所から開始されます。出力バッファーを入力バッファーより小さくすることはできません。</span><span class="sxs-lookup"><span data-stu-id="a1044-121">When encrypting in-place, the output buffer starts at exactly the same location as the input buffer, and must be no smaller than the input buffer.</span></span> <span data-ttu-id="a1044-122">AES 暗号化操作をインプレースで実行する場合、追加のスクラッチ メモリは不要です。</span><span class="sxs-lookup"><span data-stu-id="a1044-122">When AES encryption operates in-place no extra scratch memory is required.</span></span>

## <a name="3des"></a><span data-ttu-id="a1044-123">3DES</span><span class="sxs-lookup"><span data-stu-id="a1044-123">3DES</span></span>

- <span data-ttu-id="a1044-124">**アルゴリズムの標準**: NetX Crypto は、NIST Special Publication 800-67 rev 2: "*トリプル データ暗号化アルゴリズム (TDES) ブロック暗号の推奨事項*" ([https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final) を参照) に従って、Tripple DES (TDES、3DES とも呼ばれます) を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-124">**Algorithm Standard**: NetX Crypto implements Tripple DES(TDES, also known as 3DES) according to NIST Special Publication 800-67 rev 2: *"Recommendataion for the Triple Data Encryption Algorithm (TDES) Block Cipher"*, which can be found at: [https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final](https://csrc.nist.gov/publications/detail/sp/800-67/rev-2/final)</span></span>
- <span data-ttu-id="a1044-125">**サポートされているキーの長さ**: 64 \* 3 = 192</span><span class="sxs-lookup"><span data-stu-id="a1044-125">**Key Length Supported**: 64 \* 3 = 192</span></span>
- <span data-ttu-id="a1044-126">**メモリ要件**: なし</span><span class="sxs-lookup"><span data-stu-id="a1044-126">**Memory Requreiment:**: None</span></span>

<span data-ttu-id="a1044-127">NetX Crypto では、"3DES" という用語は "TDES" と同じ意味で使用されます。</span><span class="sxs-lookup"><span data-stu-id="a1044-127">In NetX Crypto, the term "3DES" is used interchangeably with "TDES".</span></span>

## <a name="md5"></a><span data-ttu-id="a1044-128">MD5</span><span class="sxs-lookup"><span data-stu-id="a1044-128">MD5</span></span>

- <span data-ttu-id="a1044-129">**アルゴリズムの標準**: NetX Crypto は、RFC 1321: "*MD5 メッセージ ダイジェスト アルゴリズム*" に従って MD5 を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-129">**Algorithm Standard**: NetX Crypto implements MD5 according to RFC 1321: *"The MD5 Message-Digest Algorithm"*</span></span>
- <span data-ttu-id="a1044-130">**メモリ要件**: アプリケーションでは、MD5 操作間で状態を維持するために使用される、MD5 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-130">**Memory Requirement**: The application must supply an MD5 control block structure, used to maintain state between MD5 operations.</span></span>

## <a name="sha1-sha256512"></a><span data-ttu-id="a1044-131">SHA1、SHA256/512</span><span class="sxs-lookup"><span data-stu-id="a1044-131">SHA1, SHA256/512</span></span>

- <span data-ttu-id="a1044-132">**アルゴリズムの標準**: NetX Crypto は、NIST FIPS Publication 180-4: "*セキュア ハッシュ標準*" ([http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf) を参照) に従って、SHA1、SHA256、または SHA512 を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-132">**Algorithm Standard:** NetX Crypto implements SHA1/256/512 according to NIST FIPS publication 180-4: "*Secure Hash Standard*", which can be found at: [http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf](http://nvlpubs.nist.gov/nistpubs/FIPS/NIST.FIPS.180-4.pdf)</span></span>
- <span data-ttu-id="a1044-133">**ハッシュ ブロック サイズ**:</span><span class="sxs-lookup"><span data-stu-id="a1044-133">**Hash block size:**:</span></span>
  - <span data-ttu-id="a1044-134">SHA1: 160 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-134">SHA1: 160 bits hash value</span></span>
  - <span data-ttu-id="a1044-135">SHA 224: 224 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-135">SHA 224: 224 bits hash value</span></span>
  - <span data-ttu-id="a1044-136">SHA 256: 256 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-136">SHA 256: 256 bits hash value</span></span>
  - <span data-ttu-id="a1044-137">SHA 384: 384 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-137">SHA 384: 384 bits hash value</span></span>
  - <span data-ttu-id="a1044-138">SHA 512: 512 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-138">SHA 512: 512 bits hash value</span></span>
  - <span data-ttu-id="a1044-139">SHA 512/224: 224 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-139">SHA 512/224: 224 bits hash value</span></span>
  - <span data-ttu-id="a1044-140">SHA 512/256: 256 ビットのハッシュ値</span><span class="sxs-lookup"><span data-stu-id="a1044-140">SHA 512/256: 256 bits hash value</span></span>

  <span data-ttu-id="a1044-141">NetX Crypto では、SHA256 ルーチンを使用して、SHA256 と SHA224 が渡されます。</span><span class="sxs-lookup"><span data-stu-id="a1044-141">In NetX Crypto, SHA256 routines are used to hadn SHA256 and SHA224.</span></span> <span data-ttu-id="a1044-142">SHA512 ルーチンを使用して、SHA512、SHA384、SHA512/224、SHA512/256 が渡されます。</span><span class="sxs-lookup"><span data-stu-id="a1044-142">SHA512 routines are used to hand SHA512, SHA384, SHA512/224 and SHA512/256.</span></span>
- <span data-ttu-id="a1044-143">**メモリ要件:** アプリケーションでは、操作間で状態を維持するために、SHA 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-143">**Memory Requirement:** The application must provide a SHA control block structure for maintaining state between operations.</span></span>

## <a name="rsa"></a><span data-ttu-id="a1044-144">RSA</span><span class="sxs-lookup"><span data-stu-id="a1044-144">RSA</span></span>

- <span data-ttu-id="a1044-145">**標準:** NetX Crypto は、"*PKCS #1 v2.2: RSA 暗号標準*" に従って RSA を実装しています。この標準は、RFC 8017 として公開されており、[https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf) でも参照できます。</span><span class="sxs-lookup"><span data-stu-id="a1044-145">**Standard:** NetX Crypto implements RSA according to the standard "*PKCS #1 v2.2: RSA Cryptography Standard*", which is published as RFC 8017 and can also be found at: [https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf](https://www.emc.com/collateral/white-papers/h11300-pkcs-1v2-2-rsa-cryptography-standard-wp.pdf)</span></span>
- <span data-ttu-id="a1044-146">**メモリ要件:** アプリケーションでは、操作間で状態を維持し、中間計算に必要な "スクラッチ" バッファー領域を提供するために、RSA 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-146">**Memory Requirement:** The application must provide an RSA control block structure for maintaining state between operations and to provide necessary "scratch" buffer space for intermediate calculations.</span></span>

## <a name="hmac"></a><span data-ttu-id="a1044-147">HMAC</span><span class="sxs-lookup"><span data-stu-id="a1044-147">HMAC</span></span>

- <span data-ttu-id="a1044-148">**標準:** NetX Crypto は、FIPS PUB 198-1: "*キー付きハッシュ メッセージ認証コード (HMAC)* " ([https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf) を参照) に従って HMAC を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-148">**Standard:** NetX Crypto implements HMAC according to FIPS PUB 198-1: "*The Keyed-Hash Message Authentication Code (HMAC)*", which can be found at: [https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf](https://csrc.nist.gov/csrc/media/publications/fips/198/1/final/documents/fips-198-1_final.pdf)</span></span>
- <span data-ttu-id="a1044-149">**メモリ要件:** アプリケーションでは、操作間で状態を維持するために、HMAC 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-149">**Memory Requirement:** The application must provide an HMAC control block structure for maintaining state between operations.</span></span> <span data-ttu-id="a1044-150">提供する実際の制御ブロックは、必要な基になるハッシュ操作 (SHA1、MD5 など) によって異なります。</span><span class="sxs-lookup"><span data-stu-id="a1044-150">The actual control block supplied depends on the desired underlying hash operation (e.g. SHA1, MD5).</span></span>

## <a name="elliptic-curve"></a><span data-ttu-id="a1044-151">楕円曲線</span><span class="sxs-lookup"><span data-stu-id="a1044-151">Elliptic Curve</span></span>

- <span data-ttu-id="a1044-152">**標準:** NetX Crypto は楕円曲線を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-152">**Standard:** NetX Crypto implements Elliptic Curve.</span></span> <span data-ttu-id="a1044-153">サポートされている名前付き曲線は次のとおりです (プライム フィールドのみ)。</span><span class="sxs-lookup"><span data-stu-id="a1044-153">The supported named curves are (prime field only):</span></span>
  - <span data-ttu-id="a1044-154">P-192</span><span class="sxs-lookup"><span data-stu-id="a1044-154">P-192</span></span>
  - <span data-ttu-id="a1044-155">P-224</span><span class="sxs-lookup"><span data-stu-id="a1044-155">P-224</span></span>
  - <span data-ttu-id="a1044-156">P-256</span><span class="sxs-lookup"><span data-stu-id="a1044-156">P-256</span></span>
  - <span data-ttu-id="a1044-157">P-384</span><span class="sxs-lookup"><span data-stu-id="a1044-157">P-384</span></span>
  - <span data-ttu-id="a1044-158">P-521</span><span class="sxs-lookup"><span data-stu-id="a1044-158">P-521</span></span>

   > [!TIP]
   > <span data-ttu-id="a1044-159">非圧縮形式がサポートされています。</span><span class="sxs-lookup"><span data-stu-id="a1044-159">Uncompressed format is supported.</span></span> <span data-ttu-id="a1044-160">SEC1-v1 のセクション 2.3.3 および 2.3.4 を参照してください ([http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf))。</span><span class="sxs-lookup"><span data-stu-id="a1044-160">See section 2.3.3 and 2.3.4 of SEC1-v1: [http://www.secg.org/sec1-v2.pdf](http://www.secg.org/sec1-v2.pdf)</span></span>

- <span data-ttu-id="a1044-161">**メモリ要件:** なし</span><span class="sxs-lookup"><span data-stu-id="a1044-161">**Memory Requirement:** None</span></span>

## <a name="ecdsa"></a><span data-ttu-id="a1044-162">ECDSA</span><span class="sxs-lookup"><span data-stu-id="a1044-162">ECDSA</span></span>

- <span data-ttu-id="a1044-163">**標準:** NetX Crypto は、FIPS PUB 186-4: "*デジタル署名標準 (DSS)* " ([https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf) を参照) に従って ECDSA を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-163">**Standard:** NetX Crypto implements ECDSA according to FIPS PUB 186-4: "*Digital Signature Standard (DSS)*", which can be found at: [https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf](https://nvlpubs.nist.gov/nistpubs/fips/nist.fips.186-4.pdf)</span></span>
- <span data-ttu-id="a1044-164">**メモリ要件:** アプリケーションでは、操作間で状態を維持するために、ECDSA 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-164">**Memory Requirement:** The application must provide an ECDSA control block structure for maintaining state between operations.</span></span>

## <a name="ecdh"></a><span data-ttu-id="a1044-165">ECDH</span><span class="sxs-lookup"><span data-stu-id="a1044-165">ECDH</span></span>

> [!IMPORTANT]
> <span data-ttu-id="a1044-166">Azure RTOS 6.0 では、静的秘密キーを使用する ECDH は入力ポイントの検証をセキュリティで保護する必要があるため、ECDH ルーチンは ECDHE 暗号にのみ使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-166">In Azure RTOS 6.0, ECDH routines should only be used for ECDHE cryptography as ECDH with a static private key requires input point validation to be secure.</span></span>

- <span data-ttu-id="a1044-167">**標準:** NetX Crypto は、FIPS PUB 800-56Ar2: "離散対数暗号を使用したペアワイズ キー確立スキームの推奨事項" ([https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf) を参照) に従って ECDH を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-167">**Standard:** NetX Crypto implements ECDH according to FIPS PUB 800-56Ar2: "Recommendation for Pair-Wise Key Establishment Schemes Using Discrete Logarithm Cryptography", which can be found at: [https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf](https://nvlpubs.nist.gov/nistpubs/specialpublications/nist.sp.800-56ar2.pdf)</span></span>
- <span data-ttu-id="a1044-168">**メモリ要件:** アプリケーションでは、操作間で状態を維持するために、ECDH 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-168">**Memory Requirement:** The application must provide an ECDH control block structure for maintaining state between operations.</span></span>

## <a name="drbg"></a><span data-ttu-id="a1044-169">DRBG</span><span class="sxs-lookup"><span data-stu-id="a1044-169">DRBG</span></span>

- <span data-ttu-id="a1044-170">**標準:** NetX Crypto は、FIPS PUB 800-90Ar1: "決定論的ランダム ビット ジェネレーターを使用した乱数生成の推奨事項" ([https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf) を参照) に従って DRBG を実装しています。</span><span class="sxs-lookup"><span data-stu-id="a1044-170">**Standard:** NetX Crypto implements DRBG according to FIPS PUB 800-90Ar1: "Recommendation for Random Number Generation Using Deterministic Random Bit Generators", which can be found at: [https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf](https://nvlpubs.nist.gov/nistpubs/SpecialPublications/NIST.SP.800-90Ar1.pdf)</span></span>
- <span data-ttu-id="a1044-171">**メモリ要件:** アプリケーションでは、操作間で状態を維持するために、DRBG 制御ブロック構造を提供する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a1044-171">**Memory Requirement:** The application must provide an DRBG control block structure for maintaining state between operations.</span></span>

## <a name="fips-compliant"></a><span data-ttu-id="a1044-172">FIPS 準拠</span><span class="sxs-lookup"><span data-stu-id="a1044-172">FIPS-Compliant</span></span>

<span data-ttu-id="a1044-173">NetX Crypto FIPS 140-2</span><span class="sxs-lookup"><span data-stu-id="a1044-173">NetX Crypto FIPS 140-2</span></span>