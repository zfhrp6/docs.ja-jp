---
title: CBC モード対称復号化の埋め込みを使用してタイミング脆弱性
description: 検出して暗号ブロック チェーン (CBC) モードで埋め込みを使用して暗号化解除の対称でタイミングの脆弱性を軽減する方法を説明します。
ms.date: 06/12/2018
author: blowdart
ms.author: mairaw
ms.openlocfilehash: 26f4d19f591ac02d792bebbd648e90b07d84de56
ms.sourcegitcommit: 6bc4efca63e526ce6f2d257fa870f01f8c459ae4
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 06/19/2018
ms.locfileid: "36208688"
---
# <a name="timing-vulnerabilities-with-cbc-mode-symmetric-decryption-using-padding"></a>CBC モード対称復号化の埋め込みを使用してタイミング脆弱性

Microsoft では、安全を除き、暗号化テキストの整合性を確認せずに検証可能な埋め込みが適用されたときに、対称暗号化の暗号ブロック チェーン (CBC) モードで暗号化されたデータを復号化には不要になったと見なす非常に限定ような場合にします。 この判断は、現在認識されている暗号研究は常に基づいています。 

## <a name="introduction"></a>はじめに

パディング oracle 攻撃は、キーがわからなくても、データの内容の暗号化を解除する攻撃者は、暗号化されたデータに対する攻撃の一種です。

Oracle は、「を確認する」、攻撃者について説明するかどうかが実行しているアクションが正しいかどうを参照します。 ボードの再生を想像してくださいまたはカード ゲームの子にします。 ときに顔点灯笑顔と彼女が彼女と思われるため、oracle である、適切な移動を行うためについてです。 、、対戦相手としてこの oracle をする際、次の操作を適切に計画します。

余白は、特定の暗号用語です。 データの暗号化に使用するアルゴリズムであり、一部の暗号は、各ブロックが固定サイズのデータのブロックで機能します。 暗号化するデータがない場合、ブロックを入力する適切なサイズ、終了する前に、データが埋め込まれます。 埋め込みの多くの形式では、常に存在する場合でも、元の入力が適切なサイズがそのパディングが必要です。 これにより、余白を常に復号化時に削除しても問題ありません。

次の 2 つを一緒に配置するには、埋め込み oracle ソフトウェアの実装は復号化されたデータに有効な埋め込みがあるかどうかが表示されます。 Oracle には、「無効な埋め込み」と表示されている値を返すように単純なもの、または多少異なるにかかる時間が無効なブロックではなく有効なブロックの処理と同様より複雑なものがあります。

ブロック ベースの暗号は、2 番目のブロック内のデータに最初のブロック内のデータの関係を決定すると、モードと呼ばれる別のプロパティを持ちなど。 CBC は、最もよく使用されるモードのいずれか。 CBC として、初期化ベクター (IV)、既知の初期乱数ブロックを導入し、同じ暗号化された出力を常に生成しない、同じキーで、同じメッセージを暗号化するように静的な暗号化の結果と、前のブロックを結合します。

攻撃者は、CBC データ構造と組み合わせてのパディング oracle を使用することができます、データが正しく、oracle を公開するコードを少し変更したメッセージを送信し、oracle のかを示しますまでデータの送信を続けます。 この応答から攻撃者は、バイトごとのメッセージを暗号化解除できます。

最近のコンピューターのネットワークはこのような高品質の攻撃者がリモート システムにかかる時間 (0.1 ミリ秒未満) を実行中の違いが非常に小さいで検出できることです。 データが改ざんされていない場合にのみ成功した復号化が行われると仮定しているアプリケーションは、成功と失敗の暗号化解除の違いを観察するよう設計されているツールからの攻撃に対して脆弱可能性があります。 このタイミングの違いは、さらに重要な一部の言語またはライブラリで他のものより可能性がありますが、今すぐと思われますであるすべての言語とライブラリの実践的な脅威の障害に対するアプリケーションの応答がアカウントになったときにします。

このような攻撃は、暗号化されたデータを変更し、oracle では結果をテストする機能に依存しています。 暗号化されたデータへの変更を検出し、実行できるすべてのアクションを拒否するのには完全に攻撃を軽減するためにしかありません。 これを行う標準的な方法では、データの署名を作成し、操作を実行する前に、その署名を検証します。 署名は検証可能である必要があります、攻撃者が作成することはできませんは、暗号化されたデータを変更し、変更されたデータに基づく新しい署名の計算のそれ以外の場合。 1 つの一般的な種類の適切なシグネチャは、キー付きハッシュ メッセージ認証コード (HMAC) と呼ばれます。 HMAC は、既知の HMAC を生成した人にのみ、および検証するユーザーに秘密キーを受け取るというチェックサムと異なります。 キーを所有している、せずには、正しい HMAC を生成することはできません。 データを受信するときに、暗号化されたデータとして、個別に計算 HMAC を秘密キーを使用して、送信者共有し、比較が送信されるとき、いずれかに対して、HMAC を計算します。 この比較は、一定の時間をする必要があります、それ以外の場合追加した別の検出可能な oracle では、異なる種類の攻撃を許可します。

要約すると、使用する場合は、安全に CBC ブロック暗号を埋め込まれた、それらがデータの暗号化を解除する前に、定数時間の比較を使用して検証する HMAC (または別のデータの整合性チェック) で結合する必要があります。 変更後のすべてのメッセージには、応答を生成するために同じ量時間かかるため、攻撃が回避されます。

## <a name="who-is-vulnerable"></a>に対して脆弱であります。

この脆弱性は、独自の暗号化と復号化を実行しているマネージ コードとネイティブの両方のアプリケーションに適用されます。 これが含まれている例を示します。

- サーバー上の以降の暗号化解除用の cookie を暗号化するアプリケーション。
- 列を持つユーザーがテーブルにデータを挿入する機能を提供するデータベース アプリケーションは、後で復号化します。
- データは、転送中にデータを保護する共有キーを使用した暗号化に依存するアプリケーションを転送します。
- 暗号化し、「内部」の TLS トンネルのメッセージを復号化するアプリケーション。

単独で TLS を使用する可能性があります保護されないこれらのシナリオで注意してください。

影響を受けるアプリケーションの場合:

- CBC 暗号モードを PKCS #7 または ANSI X.923 など、検証可能なパディング モードを使用してデータを復号化します。
- (MAC または非対称のデジタル署名) 経由でデータの整合性チェックを実行せず、復号化を実行します。

これは、Cryptographic Message Syntax (PKCS #7/CMS) EnvelopedData 構造など、これらのプリミティブの上に抽象化の上に構築されたアプリケーションにも適用されます。

## <a name="related-areas-of-concern"></a>関連する重要な領域

Research には、ISO 10126 に等しい場合、メッセージには、既知のまたは予測可能なフッター構造体は埋め込みで埋められます CBC メッセージの詳細関係するさらに Microsoft がますましています。 たとえば、W3C XML 暗号化の構文と処理の推奨事項 (xmlenc、EncryptedXml) の規則の下で準備のコンテンツ。 メッセージに署名し、暗号化には、W3C ガイダンスは、時に適切と見なされました、中に、マイクロソフトは常に暗号化、署名を行うようになりました推奨します。

アプリケーション開発者は常に考慮非対称署名キーの適用性を確認する非対称キーと任意のメッセージの本質的な信頼関係が存在しないためです。

## <a name="details"></a>説明

従来は、両方の暗号化および HMAC または RSA 署名などの手段を使用して、重要なデータを認証することが重要合意がありました。 ただし、以下を暗号化および認証の操作をシーケンス処理する方法に関して明確なガイダンスがありました。 この記事で詳しく説明脆弱性により Microsoft のガイダンスは常に「暗号化 then-署名」パラダイムを使用するようになりましたです。 つまり、最初に、対称キーを使用してデータを暗号化し、暗号化テキスト (暗号化されたデータ) を MAC または非対称署名を計算します。 データを復号化、逆を実行します。 最初に、MAC または暗号文の署名を確認し、復号化します。

上の脆弱性が 10 年以上にわたって存在する知られて「oracle 攻撃を埋め込み」と呼ばれるクラスです。 これらの脆弱性には、データのブロックあたり個 4096 の試行を使用する AES および 3 des などのブロックの対称アルゴリズムで暗号化されたデータの暗号化を解除する攻撃者が可能です。 これらの脆弱性のための暗号をブロックするファクトの使用が終了時に検証可能な埋め込みデータに最も頻繁に使用します。 これは、場合は、攻撃者は、暗号化テキストを改ざんし、末尾の余白の形式でエラーが発生改ざんが行われたかどうかを検出、攻撃者によって、データを解読できますが見つかりませんでした。

実用的な攻撃パディングが ASP.NET の脆弱性など、有効かどうかに基づいて別のエラー コードを返すサービスに基づいて最初に、 [MS10 070](https://technet.microsoft.com/library/security/ms10-070.aspx)です。 ただし、Microsoft 今すぐと見なすタイミング有効および無効な余白の処理の間の違いのみを使用するような攻撃を実施することは実用的であります。

任意の情報を出力せず、データの整合性を検証できます暗号化スキーム、署名を使用すると、(内容) に関係なくデータの指定した長さの固定のランタイムで、署名の検証が行われること、攻撃者によって、[側チャネル](https://en.wikipedia.org/wiki/Side-channel_attack)です。 整合性チェックは、改ざん、メッセージを拒否するため、パディング oracle 上の脅威が軽減されます。

## <a name="guidance"></a>ガイダンス

第一に、経由でトランスポート層セキュリティ (TLS)、セキュリティで保護された Sockets Layer (SSL) に後続必要がある機密性のあるすべてのデータに転送することをお勧めします。

次に、アプリケーションを分析します。

- どのような暗号化を実行しているし、プラットフォームと Api を使用しているによってどのような暗号化が提供されている正確に理解します。
- 各使用率、対称のそれぞれの層にあることがはっきり[ブロック暗号アルゴリズム](https://en.wikipedia.org/wiki/Block_cipher#Notable_block_ciphers)AES および 3 des、CBC モードでは、秘密キーとデータ整合性チェックの使用を組み込むなど、(、非対称署名した HMAC 値、またはする暗号モードを変更するには[認証暗号化](https://en.wikipedia.org/wiki/Authenticated_encryption)(AE) モード GCM、CCM など)。

現在の研究に基づき、通常と思われます認証と暗号化の手順は、暗号化のない AE モードに対する別に行う、ときに、暗号文の認証 (暗号化、-記号) がある、最適な一般的なオプションです。 ただし、暗号化に万能の公式の正しい解答がないと、この汎化されない professional 暗号からのアドバイスをほど有向。

メッセージングの形式の変更が、認証されていない CBC 暗号解読を実行することはないアプリケーションをなどの緩和策を組み込むしようとすることをお勧めします。

- 復号化、またはスペースを削除することを確認する復号化を許可しません。
  - 適用された埋め込みを削除するか、無視する必要がある、負荷をアプリケーションに移動します。
  - 利点は、その他のアプリケーション データの検証ロジックに組み込むことができます、パディングの検証と削除。 パディング検証とデータの検証は、定数時間で完了できます、脅威が減少します。
  - 余白の解釈は、見かけ上のメッセージの長さを変更後もありますこのアプローチにより、出力されるタイミング情報。
- ISO10126 を復号化する埋め込みモードを変更します。
  - ISO10126 復号化の余白は PKCS7 暗号化パディングと ANSIX923 暗号化パディングの両方と互換性のあります。
  - モードを変更すると、ブロック全体ではなく 1 バイトに埋め込み oracle ナレッジが減少します。 ただし、コンテンツに終わりの XML 要素などのよく知られているフッターがある場合は、関連する攻撃がメッセージの残りの部分を攻撃する続行できます。
  - これも防ぐ、攻撃者が、同じプレーン テキストをさまざまなメッセージの相対位置で複数回暗号化を強制するような状況で復旧にプレーン テキスト。
- ゲートするタイミングの信号を緩衝復号化の呼び出しの評価:
  - 余白を含む任意のデータ セグメントの暗号化解除の操作にかかる時間の最大の量を超えた最小の保持時間の計算が必要です。
  - ガイダンスに従って時間計算を行う必要があります[高解像度のタイムスタンプを取得する](https://msdn.microsoft.com/library/windows/desktop/dn55340.aspx)ではなく<xref:System.Environment.TickCount?displayProperty=nameWithType>(ロール オーバー/オーバーフロー) に従います (NTP 調整される可能性が 2 つのシステム タイムスタンプを減算またはエラーの場合)。
  - 時間計算する必要があります内のすべての潜在的な例外を含む、復号化操作を含めた管理または末尾に埋め込まれただけでなく、C++ アプリケーションです。
  - 成功または失敗をまだ決定されているが、有効期限が切れるときにエラーを返すタイミング ゲート必要があります。
- 認証されていない復号化を実行しているサービスは、大量の「無効」のメッセージが取得することを検出する監視が必要です。
  - このシグナルは偽陽性 (正当に破損したデータ) と (検出を回避するための十分に長い時間の経過と共に、攻撃を展開) 偽陰性の両方を実行することに注意してください。

## <a name="finding-vulnerable-code---native-applications"></a>脆弱なコードは、ネイティブ アプリケーションを検索します。

Windows Cryptography に対してビルドされたプログラム: Next Generation (CNG) ライブラリ。

- 暗号化解除の呼び出しが[BCryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa375391.aspx)を指定して、`BCRYPT_BLOCK_PADDING`フラグ。
- 呼び出してキー ハンドルが初期化されて[BCryptSetProperty](https://msdn.microsoft.com/library/windows/desktop/aa375504.aspx)で[BCRYPT_CHAINING_MODE](https://msdn.microsoft.com/library/windows/desktop/aa376211.aspx#BCRYPT_CHAINING_MODE) 'éý'`BCRYPT_CHAIN_MODE_CBC`です。
  - `BCRYPT_CHAIN_MODE_CBC`の影響を受ける、既定値は、コードが割り当てられていない任意の値の`BCRYPT_CHAINING_MODE`します。

以前の Windows 暗号化 API に対してビルドされたプログラム。

- 暗号化解除の呼び出しが[CryptDecrypt](https://msdn.microsoft.com/library/windows/desktop/aa379913.aspx)で`Final=TRUE`です。
- 呼び出してキー ハンドルが初期化されて[CryptSetKeyParam](https://msdn.microsoft.com/library/windows/desktop/aa380272.aspx)で[KP_MODE](https://msdn.microsoft.com/library/windows/desktop/aa379949.aspx#KP_MODE) 'éý'`CRYPT_MODE_CBC`です。
  - `CRYPT_MODE_CBC`の影響を受ける、既定値は、コードが割り当てられていない任意の値の`KP_MODE`します。

## <a name="finding-vulnerable-code---managed-applications"></a>検索の脆弱なコード、マネージ アプリケーション

- 暗号化解除の呼び出しが、<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor>または<xref:System.Security.Cryptography.SymmetricAlgorithm.CreateDecryptor(System.Byte[],System.Byte[])>メソッド<xref:System.Security.Cryptography.SymmetricAlgorithm?displayProperty=nameWithType>です。
  - これは、.NET 内で次の派生型が含まれていますが、サード パーティの型を含めることも。
    - <xref:System.Security.Cryptography.Aes>
    - <xref:System.Security.Cryptography.AesCng>
    - <xref:System.Security.Cryptography.AesCryptoServiceProvider>
    - <xref:System.Security.Cryptography.AesManaged>
    - <xref:System.Security.Cryptography.DES>
    - <xref:System.Security.Cryptography.DESCryptoServiceProvider>
    - <xref:System.Security.Cryptography.RC2>
    - <xref:System.Security.Cryptography.RC2CryptoServiceProvider>
    - <xref:System.Security.Cryptography.Rijndael>
    - <xref:System.Security.Cryptography.RijndaelManaged>
    - <xref:System.Security.Cryptography.TripleDES>
    - <xref:System.Security.Cryptography.TripleDESCng>
    - <xref:System.Security.Cryptography.TripleDESCryptoServiceProvider>
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>プロパティに設定された<xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>、 <xref:System.Security.Cryptography.PaddingMode.ANSIX923?displayProperty=nameWithType>、または<xref:System.Security.Cryptography.PaddingMode.ISO10126?displayProperty=nameWithType>です。
  - <xref:System.Security.Cryptography.PaddingMode.PKCS7?displayProperty=nameWithType>の影響を受ける、既定値は、コードが割り当てられませんが、<xref:System.Security.Cryptography.SymmetricAlgorithm.Padding?displayProperty=nameWithType>プロパティです。
- <xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>プロパティに設定されました <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>
  - <xref:System.Security.Cryptography.CipherMode.CBC?displayProperty=nameWithType>の影響を受ける、既定値は、コードが割り当てられませんが、<xref:System.Security.Cryptography.SymmetricAlgorithm.Mode?displayProperty=nameWithType>プロパティです。

## <a name="finding-vulnerable-code---cryptographic-message-syntax"></a>脆弱なコードは、暗号化メッセージ構文を検索します。

暗号化されたコンテンツを持つ、CBC モードの AES (2.16.840.1.101.3.4.1.2、2.16.840.1.101.3.4.1.22、2.16.840.1.101.3.4.1.42)、DES (1.3.14.3.2.7)、3 des を使用して認証されていない CMS EnvelopedData メッセージ (1.2.840.113549.3.7) または RC2 (1.2.840.113549.3.2) は脆弱なもとしてメッセージ CBC モードで他のブロック暗号アルゴリズムを使用します。

ストリーム暗号がこの特定の脆弱性を受けやすいでないときに、常に ContentEncryptionAlgorithm 値を調べることで、データの認証を行うことをお勧めします。

マネージ アプリケーションは、blob を指定できます CMS EnvelopedData 検出として任意の値に渡される<xref:System.Security.Cryptography.Pkcs.EnvelopedCms.Decode(System.Byte[])?displayProperty=fullName>です。

経由で CMS ハンドルを指定した値としてのネイティブ アプリケーションは、CMS EnvelopedData blob を検出できる[CryptMsgUpdate](https://msdn.microsoft.com/library/windows/desktop/aa380231.aspx)が結果として得られる[CMSG_TYPE_PARAM](https://msdn.microsoft.com/library/windows/desktop/aa380227.aspx)は`CMSG_ENVELOPED`CMS ハンドルやその後送信、`CMSG_CTRL_DECRYPT`を介して命令[CryptMsgControl](https://msdn.microsoft.com/library/windows/desktop/aa380220.aspx)です。

## <a name="vulnerable-code-example---managed"></a>脆弱なコードの例 - 管理

このメソッドが、cookie を読み取り、復号化し、データの整合性チェックが表示されません。 そのため、このメソッドによって読み取られる cookie の内容は、受信したユーザーまたは攻撃者は、暗号化された cookie の値を取得して攻撃があります。

```csharp
private byte[] DecryptCookie(string cookieName)
{
    HttpCookie cookie = Request.Cookies[cookieName];

    if (cookie == null)
    {
        return null;
    }

    using (ICryptoTransform decryptor = _aes.CreateDecryptor())
    using (MemoryStream memoryStream = new MemoryStream())
    using (CryptoStream cryptoStream =
        new CryptoStream(memoryStream, decryptor, CryptoStreamMode.Write))
    {
        byte[] readCookie = Convert.FromBase64String(cookie.Value);
        cryptoStream.Write(readCookie, 0, readCookie.Length);
        cryptoStream.FlushFinalBlock();
        return memoryStream.ToArray();
    }
}
```

## <a name="example-code-following-recommended-practices---managed"></a>例のコードの次の推奨されるプラクティス - 管理

次のサンプル コードの非標準のメッセージ形式を使用します。

`cipher_algorithm_id || hmac_algorithm_id || hmac_tag || iv || ciphertext`

ここで、`cipher_algorithm_id`と`hmac_algorithm_id`アルゴリズム識別子はそれらのアルゴリズムのアプリケーションのローカル (標準) 表現したものです。 これらの識別子が有意義の代わりに、既存のメッセージング プロトコルの他の部分でベア連結されたバイト ストリームとしてです。

また、この例では、単一のマスター _ キーを使用して、暗号化キーおよび HMAC キーの両方を抽出します。 これは提供便宜を図って両方デュアル キーとのアプリケーションに、さまざまな値の 2 つのキーを保持するように促すは、単独でキー指定されたアプリケーションを有効にします。 さらに、同期外 HMAC キーと暗号化キーを取得できませんを保証します。

このサンプルを受け取らず、<xref:System.IO.Stream>暗号化または復号化します。 現在のデータ形式が 1 回の暗号化難しいため、`hmac_tag`値で暗号化テキストの前にします。 ただし、この形式は、パーサーを簡素するには最初にそれ以降のすべての固定サイズの要素のために選ばれました。 このデータ形式に 1 回の復号化が必要な GetHashAndReset を呼び出すし、TransformFinalBlock を呼び出す前に、結果を確認する実装者は注意が必要です。 ストリーミングの暗号化が重要な場合、別の AE モード必要があります。

```csharp
// ==++==
//
//   Copyright (c) Microsoft Corporation.  All rights reserved.
//
//   Shared under the terms of the Microsoft Public License,
//   https://opensource.org/licenses/MS-PL
//
// ==--==

using System;
using System.Diagnostics;
using System.IO;
using System.Runtime.CompilerServices;
using System.Security.Cryptography;

namespace Microsoft.Examples.Cryptography
{
    public enum AeCipher : byte
    {
        Unknown,
        Aes256CbcPkcs7,
    }

    public enum AeMac : byte
    {
        Unknown,
        HMACSHA256,
        HMACSHA384,
    }

    /// <summary>
    /// Provides extension methods to make HashAlgorithm look like .NET Core's
    /// IncrementalHash
    /// </summary>
    internal static class IncrementalHashExtensions
    {
        public static void AppendData(this HashAlgorithm hash, byte[] data)
        {
            hash.TransformBlock(data, 0, data.Length, null, 0);
        }

        public static void AppendData(
            this HashAlgorithm hash,
            byte[] data,
            int offset,
            int length)
        {
            hash.TransformBlock(data, offset, length, null, 0);
        }

        public static byte[] GetHashAndReset(this HashAlgorithm hash)
        {
            hash.TransformFinalBlock(Array.Empty<byte>(), 0, 0);
            return hash.Hash;
        }
    }

    public static partial class AuthenticatedEncryption
    {
        /// <summary>
        /// Use <paramref name="masterKey"/> to derive two keys (one cipher, one HMAC)
        /// to provide authenticated encryption for <paramref name="message"/>.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="message">The message to encrypt</param>
        /// <returns>
        /// A concatenation of
        /// [cipher algorithm+chainmode+padding][mac algorithm][authtag][IV][ciphertext],
        /// suitable to be passed to <see cref="Decrypt"/>.
        /// </returns>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or bigger) value generated
        /// by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>.
        /// This implementation chooses to block deficient inputs by length, but does not
        /// make any attempt at discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase)
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Encrypt(byte[] masterKey, byte[] message)
        {
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (message == null)
                throw new ArgumentNullException(nameof(message));

            // First, choose an encryption scheme.
            AeCipher aeCipher = AeCipher.Aes256CbcPkcs7;

            // Second, choose an authentication (message integrity) scheme.
            //
            // In this example we use the master key length to change from HMACSHA256 to
            // HMACSHA384, but that is completely arbitrary. This mostly represents a
            // "cryptographic needs change over time" scenario.
            AeMac aeMac = masterKey.Length < 48 ? AeMac.HMACSHA256 : AeMac.HMACSHA384;

            // It's good to be able to identify what choices were made when a message was
            // encrypted, so that the message can later be decrypted. This allows for
            // future versions to add support for new encryption schemes, but still be
            // able to read old data. A practice known as "cryptographic agility".
            //
            // This is similar in practice to PKCS#7 messaging, but this uses a
            // private-scoped byte rather than a public-scoped Object IDentifier (OID).
            // Please note that the scheme in this example adheres to no particular
            // standard, and is unlikely to survive to a more complete implementation in
            // the .NET Framework.
            //
            // You may be well-served by prepending a version number byte to this
            // message, but may want to avoid the value 0x30 (the leading byte value for
            // DER-encoded structures such as X.509 certificates and PKCS#7 messages).
            byte[] algorithmChoices = { (byte)aeCipher, (byte)aeMac };
            byte[] iv;
            byte[] cipherText;
            byte[] tag;

            // Using our algorithm choices, open an HMAC (as an authentication tag
            // generator) and a SymmetricAlgorithm which use different keys each derived
            // from the same master key.
            //
            // A custom implementation may very well have distinctly managed secret keys
            // for the MAC and cipher, this example merely demonstrates the master to
            // derived key methodology to encourage key separation from the MAC and
            // cipher keys.
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
                using (ICryptoTransform encryptor = cipher.CreateEncryptor())
                {
                    // Since no IV was provided, a random one has been generated
                    // during the call to CreateEncryptor.
                    //
                    // But note that it only does the auto-generation once. If the cipher
                    // object were used again, a call to GenerateIV would have been
                    // required.
                    iv = cipher.IV;

                    cipherText = Transform(encryptor, message, 0, message.Length);
                }

                // The IV and ciphertest both need to be included in the MAC to prevent
                // tampering.
                //
                // By including the algorithm identifiers, we have technically moved from
                // simple Authenticated Encryption (AE) to Authenticated Encryption with
                // Additional Data (AEAD). By including the algorithm identifiers in the
                // MAC, it becomes harder for an attacker to change them as an attempt to
                // perform a downgrade attack.
                //
                // If you've added a data format version field, it can also be included
                // in the MAC to further inhibit an attacker's options for confusing the
                // data processor into believing the tampered message is valid.
                tagGenerator.AppendData(algorithmChoices);
                tagGenerator.AppendData(iv);
                tagGenerator.AppendData(cipherText);
                tag = tagGenerator.GetHashAndReset();
            }

            // Build the final result as the concatenation of everything except the keys.
            int totalLength =
                algorithmChoices.Length +
                tag.Length +
                iv.Length +
                cipherText.Length;

            byte[] output = new byte[totalLength];
            int outputOffset = 0;

            Append(algorithmChoices, output, ref outputOffset);
            Append(tag, output, ref outputOffset);
            Append(iv, output, ref outputOffset);
            Append(cipherText, output, ref outputOffset);

            Debug.Assert(outputOffset == output.Length);
            return output;
        }

        /// <summary>
        /// Reads a message produced by <see cref="Encrypt"/> after verifying it hasn't
        /// been tampered with.
        /// </summary>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <param name="cipherText">
        /// The output of <see cref="Encrypt"/>: a concatenation of a cipher ID, mac ID,
        /// authTag, IV, and cipherText.
        /// </param>
        /// <returns>The decrypted content.</returns>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="masterKey"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="ArgumentNullException">
        /// <paramref name="cipherText"/> is <c>null</c>.
        /// </exception>
        /// <exception cref="CryptographicException">
        /// <paramref name="cipherText"/> identifies unknown algorithms, is not long
        /// enough, fails a data integrity check, or fails to decrypt.
        /// </exception>
        /// <remarks>
        /// <paramref name="masterKey"/> should be a 128-bit (or larger) value
        /// generated by a secure random number generator, such as the one returned from
        /// <see cref="RandomNumberGenerator.Create()"/>. This implementation chooses to
        /// block deficient inputs by length, but doesn't make any attempt at
        /// discerning the randomness of the key.
        ///
        /// If the master key is being input by a prompt (like a password/passphrase),
        /// then it should be properly turned into keying material via a Key Derivation
        /// Function like PBKDF2, represented by Rfc2898DeriveBytes. A 'password' should
        /// never be simply turned to bytes via an Encoding class and used as a key.
        /// </remarks>
        public static byte[] Decrypt(byte[] masterKey, byte[] cipherText)
        {
            // This example continues the .NET practice of throwing exceptions for
            // failures. If you consider message tampering to be normal (and thus
            // "not exceptional") behavior, you may like the signature
            // bool Decrypt(byte[] messageKey, byte[] cipherText, out byte[] message)
            // better.
            if (masterKey == null)
                throw new ArgumentNullException(nameof(masterKey));
            if (masterKey.Length < 16)
                throw new ArgumentOutOfRangeException(
                    nameof(masterKey),
                    "Master Key must be at least 128 bits (16 bytes)");
            if (cipherText == null)
                throw new ArgumentNullException(nameof(cipherText));

            // The format of this message is assumed to be public, so there's no harm in
            // saying ahead of time that the message makes no sense.
            if (cipherText.Length < 2)
            {
                throw new CryptographicException();
            }

            // Use the message algorithm headers to determine what cipher algorithm and
            // MAC algorithm are going to be used. Since the same Key Derivation
            // Functions (KDFs) are being used in Decrypt as Encrypt, the keys are also
            // the same.
            AeCipher aeCipher = (AeCipher)cipherText[0];
            AeMac aeMac = (AeMac)cipherText[1];

            using (SymmetricAlgorithm cipher = GetCipher(aeCipher, masterKey))
            using (HMAC tagGenerator = GetMac(aeMac, masterKey))
            {
                int blockSizeInBytes = cipher.BlockSize / 8;
                int tagSizeInBytes = tagGenerator.HashSize / 8;
                int headerSizeInBytes = 2;
                int tagOffset = headerSizeInBytes;
                int ivOffset = tagOffset + tagSizeInBytes;
                int cipherTextOffset = ivOffset + blockSizeInBytes;
                int cipherTextLength = cipherText.Length - cipherTextOffset;
                int minLen = cipherTextOffset + blockSizeInBytes;

                // Again, the minimum length is still assumed to be public knowledge,
                // nothing has leaked out yet. The minimum length couldn't just be calculated
                // without reading the header.
                if (cipherText.Length < minLen)
                {
                    throw new CryptographicException();
                }

                // It's very important that the MAC be calculated and verified before
                // proceeding to decrypt the ciphertext, as this prevents any sort of
                // information leaking out to an attacker.
                //
                // Don't include the tag in the calculation, though.

                // First, everything before the tag (the cipher and MAC algorithm ids)
                tagGenerator.AppendData(cipherText, 0, tagOffset);

                // Skip the data before the tag and the tag, then read everything that
                // remains.
                tagGenerator.AppendData(
                    cipherText,
                    tagOffset + tagSizeInBytes,
                    cipherText.Length - tagSizeInBytes - tagOffset);

                byte[] generatedTag = tagGenerator.GetHashAndReset();

                // The time it took to get to this point has so far been a function only
                // of the length of the data, or of non-encrypted values (e.g. it could
                // take longer to prepare the *key* for the HMACSHA384 MAC than the
                // HMACSHA256 MAC, but the algorithm choice wasn't a secret).
                //
                // If the verification of the authentication tag aborts as soon as a
                // difference is found in the byte arrays then your program may be
                // acting as a timing oracle which helps an attacker to brute-force the
                // right answer for the MAC. So, it's very important that every possible
                // "no" (2^256-1 of them for HMACSHA256) be evaluated in as close to the
                // same amount of time as possible. For this, we call CryptographicEquals
                if (!CryptographicEquals(
                    generatedTag,
                    0,
                    cipherText,
                    tagOffset,
                    tagSizeInBytes))
                {
                    // Assuming every tampered message (of the same length) took the same
                    // amount of time to process, we can now safely say
                    // "this data makes no sense" without giving anything away.
                    throw new CryptographicException();
                }

                // Restore the IV into the symmetricAlgorithm instance.
                byte[] iv = new byte[blockSizeInBytes];
                Buffer.BlockCopy(cipherText, ivOffset, iv, 0, iv.Length);
                cipher.IV = iv;

                using (ICryptoTransform decryptor = cipher.CreateDecryptor())
                {
                    return Transform(
                        decryptor,
                        cipherText,
                        cipherTextOffset,
                        cipherTextLength);
                }
            }
        }

        private static byte[] Transform(
            ICryptoTransform transform,
            byte[] input,
            int inputOffset,
            int inputLength)
        {
            // Many of the implementations of ICryptoTransform report true for
            // CanTransformMultipleBlocks, and when the entire message is available in
            // one shot this saves on the allocation of the CryptoStream and the
            // intermediate structures it needs to properly chunk the message into blocks
            // (since the underlying stream won't always return the number of bytes
            // needed).
            if (transform.CanTransformMultipleBlocks)
            {
                return transform.TransformFinalBlock(input, inputOffset, inputLength);
            }

            // If our transform couldn't do multiple blocks at once, let CryptoStream
            // handle the chunking.
            using (MemoryStream messageStream = new MemoryStream())
            using (CryptoStream cryptoStream =
                new CryptoStream(messageStream, transform, CryptoStreamMode.Write))
            {
                cryptoStream.Write(input, inputOffset, inputLength);
                cryptoStream.FlushFinalBlock();
                return messageStream.ToArray();
            }
        }

        /// <summary>
        /// Open a properly configured <see cref="SymmetricAlgorithm"/> conforming to the
        /// scheme identified by <paramref name="aeCipher"/>.
        /// </summary>
        /// <param name="aeCipher">The cipher mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// A SymmetricAlgorithm object with the right key, cipher mode, and padding
        /// mode; or <c>null</c> on unknown algorithms.
        /// </returns>
        private static SymmetricAlgorithm GetCipher(AeCipher aeCipher, byte[] masterKey)
        {
            SymmetricAlgorithm symmetricAlgorithm;

            switch (aeCipher)
            {
                case AeCipher.Aes256CbcPkcs7:
                    symmetricAlgorithm = Aes.Create();
                    // While 256-bit, CBC, and PKCS7 are all the default values for these
                    // properties, being explicit helps comprehension more than it hurts
                    // performance.
                    symmetricAlgorithm.KeySize = 256;
                    symmetricAlgorithm.Mode = CipherMode.CBC;
                    symmetricAlgorithm.Padding = PaddingMode.PKCS7;
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            //
            // Since none of the symmetric encryption algorithms currently in .NET
            // support key sizes greater than 256-bit, we can use HMACSHA256 with
            // NIST SP 800-108 5.1 (Counter Mode KDF) to derive a value that is
            // no smaller than the key size, then Array.Resize to trim it down as
            // needed.

            using (HMAC hmac = new HMACSHA256(masterKey))
            {
                // i=1, Label=ASCII(cipher)
                byte[] cipherKey = hmac.ComputeHash(
                    new byte[] { 1, 99, 105, 112, 104, 101, 114 });

                // Resize the array to the desired keysize. KeySize is in bits,
                // and Array.Resize wants the length in bytes.
                Array.Resize(ref cipherKey, symmetricAlgorithm.KeySize / 8);

                symmetricAlgorithm.Key = cipherKey;
            }

            return symmetricAlgorithm;
        }

        /// <summary>
        /// Open a properly configured <see cref="HMAC"/> conforming to the scheme
        /// identified by <paramref name="aeMac"/>.
        /// </summary>
        /// <param name="aeMac">The message authentication mode to open.</param>
        /// <param name="masterKey">The master key from which other keys derive.</param>
        /// <returns>
        /// An HMAC object with the proper key, or <c>null</c> on unknown algorithms.
        /// </returns>
        private static HMAC GetMac(AeMac aeMac, byte[] masterKey)
        {
            HMAC hmac;

            switch (aeMac)
            {
                case AeMac.HMACSHA256:
                    hmac = new HMACSHA256();
                    break;
                case AeMac.HMACSHA384:
                    hmac = new HMACSHA384();
                    break;
                default:
                    // An algorithm we don't understand
                    throw new CryptographicException();
            }

            // Instead of using the master key directly, derive a key for our chosen
            // HMAC algorithm based upon the master key.
            // Since the output size of the HMAC is the same as the ideal key size for
            // the HMAC, we can use the master key over a fixed input once to perform
            // NIST SP 800-108 5.1 (Counter Mode KDF):
            hmac.Key = masterKey;

            // i=1, Context=ASCII(MAC)
            byte[] newKey = hmac.ComputeHash(new byte[] { 1, 77, 65, 67 });

            hmac.Key = newKey;
            return hmac;
        }

        // A simple helper method to ensure that the offset (writePos) always moves
        // forward with new data.
        private static void Append(byte[] newData, byte[] combinedData, ref int writePos)
        {
            Buffer.BlockCopy(newData, 0, combinedData, writePos, newData.Length);
            writePos += newData.Length;
        }

        /// <summary>
        /// Compare the contents of two arrays in an amount of time which is only
        /// dependent on <paramref name="length"/>.
        /// </summary>
        /// <param name="a">An array to compare to <paramref name="b"/>.</param>
        /// <param name="aOffset">
        /// The starting position within <paramref name="a"/> for comparison.
        /// </param>
        /// <param name="b">An array to compare to <paramref name="a"/>.</param>
        /// <param name="bOffset">
        /// The starting position within <paramref name="b"/> for comparison.
        /// </param>
        /// <param name="length">
        /// The number of bytes to compare between <paramref name="a"/> and
        /// <paramref name="b"/>.</param>
        /// <returns>
        /// <c>true</c> if both <paramref name="a"/> and <paramref name="b"/> have
        /// sufficient length for the comparison and all of the applicable values are the
        /// same in both arrays; <c>false</c> otherwise.
        /// </returns>
        /// <remarks>
        /// An "insufficient data" <c>false</c> response can happen early, but otherwise
        /// a <c>true</c> or <c>false</c> response take the same amount of time.
        /// </remarks>
        [MethodImpl(MethodImplOptions.NoInlining | MethodImplOptions.NoOptimization)]
        private static bool CryptographicEquals(
            byte[] a,
            int aOffset,
            byte[] b,
            int bOffset,
            int length)
        {
            Debug.Assert(a != null);
            Debug.Assert(b != null);
            Debug.Assert(length >= 0);

            int result = 0;

            if (a.Length - aOffset < length || b.Length - bOffset < length)
            {
                return false;
            }

            unchecked
            {
                for (int i = 0; i < length; i++)
                {
                    // Bitwise-OR of subtraction has been found to have the most
                    // stable execution time.
                    //
                    // This cannot overflow because bytes are 1 byte in length, and
                    // result is 4 bytes.
                    // The OR propagates all set bytes, so the differences are only
                    // present in the lowest byte.
                    result = result | (a[i + aOffset] - b[i + bOffset]);
                }
            }

            return result == 0;
        }
    }
}
```
