---
title: ".NET Framework の新機能 | Microsoft Docs"
ms.custom: ""
ms.date: "04/07/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "新機能 [.NET Framework]"
ms.assetid: 1d971dd7-10fc-4692-8dac-30ca308fc0fa
caps.latest.revision: 292
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 287
---
# .NET Framework の新機能
<a name="introduction"></a>この記事では、主な新機能や強化された次のバージョン、.NET Framework の概要を示します。  
  
 [.NET framework 4.6.2](#v462)   
 [.NET framework 4.6.1](#v461)   
 [.NET 2015年、.NET Framework 4.6](#v46)   
 [.NET framework 4.5.2](#v452)   
 [.NET framework 4.5.1](#v451)   
 [.NET framework 4.5](#core)  
  
 この記事は、各新機能の包括的な情報を説明するものではありません。また、この内容は変更される可能性があります。 .NET Framework の概要については、次を参照してください。[概要](../../../docs/framework/get-started/index.md)します。 サポートされるプラットフォームは、次を参照してください。[システム要件](../../../docs/framework/get-started/system-requirements.md)します。 ダウンロード リンクとインストール手順については、次を参照してください。[インストール ガイド](../../../docs/framework/install/guide-for-developers.md)します。  
  
> [!NOTE]
>  .NET Framework チームは、アウトオブ バンドで NuGet プラットフォームのサポートを拡張し、変更できないコレクションおよび SIMD が有効なベクター型などの新機能を実装する機能も解放します。 詳細については、次を参照してください。[するその他のクラス ライブラリと Api](../../../ml/index.xml)と[.NET Framework および特別のリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)します。 参照してください、 [NuGet パッケージの完全な一覧](http://blogs.msdn.com/b/dotnet/p/nugetpackages.aspx)、.NET framework やサブスクライブを[フィード](https://nuget.org/api/v2/curated-feeds/dotnetframework/Packages/)します。  
  
<a name="v462"></a>   
## <a name="introducing-the-net-framework-462"></a>.NET Framework 4.6.2 の概要  
 この [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] は、.NET Framework 4.6 と 4.6.1 を基に、多数の新しい修正といくつかの新機能を追加したものであり、これまでと同様に非常に安定した製品です。  
  
### <a name="downloading-and-installing-the-net-framework-462"></a>.NET Framework 4.6.2 のダウンロードおよびインストール  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] は、次の場所からダウンロードできます。  
  
-   [.NET framework 4.6.2 Web インストーラー](http://go.microsoft.com/fwlink/?LinkId=780597)  
  
-   [NET Framework 4.6.2 のオフライン インストーラー](http://go.microsoft.com/fwlink/?LinkId=780601)  
  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] は、Windows 10、Windows 8.1、Windows 7、および Windows Server 2008 R2 SP1 以降に相当するサーバー プラットフォームにインストールできます。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] は、Web インストーラーまたはオフライン インストーラーを使用してインストールできます。 ほとんどのユーザーにお勧めする方法は、Web インストーラーの使用です。  
  
 対象にすることができます、 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] Visual Studio 2012、または後でインストールすることによって、 [.NET Framework 4.6.2 Developer Pack](http://go.microsoft.com/fwlink/?LinkId=780617)します。  
  
### <a name="whats-new-in-the-net-framework-462"></a>.NET Framework 4.6.2 の新機能  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] には、次の領域における新機能が含まれています。  
  
-   [ASP.NET](#ASPNET462)  
  
-   [文字カテゴリ](#Strings)  
  
-   [暗号化](#Crypto462)  
  
-   [SqlClient](#SQLClient)  
  
-   [Windows Communication Foundation](#WCF)  
  
-   [Windows Presentation Foundation (WPF)](#WPF462)  
  
-   [Windows Workflow Foundation (WF)](#WF462)  
  
-   [ClickOnce](#ClickOnce)  
  
-   [Windows フォームと WPF アプリ UWP アプリを変換します。](#UWPConvert)  
  
-   [デバッグの機能強化](#Debug462)  
  
 追加された新しい Api の一覧の場合、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]を参照してください[API の変更を .NET Framework 4.6.2](https://github.com/Microsoft/dotnet/blob/master/releases/net462/dotnet462-api-changes.md) GitHub にします。 機能の改善とにおけるバグ修正の一覧については、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]を参照してください[API の変更を .NET Framework 4.6.2](http://go.microsoft.com/fwlink/?LinkId=708778) github します。  詳細については、次を参照してください。 [4.6.2 の .NET Framework の発表](https://blogs.msdn.microsoft.com/dotnet/2016/08/02/announcing-net-framework-4-6-2/)、.NET ブログです。  
  
<a name="ASPNET462"></a>   
### <a name="aspnet"></a>ASP.NET  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、ASP.NET の機能が次のように強化されています。  
  
 **データ注釈の検証コントロールのローカライズされたエラー メッセージのサポートの強化**  
 データ注釈検証コントロールを使用して、1 つ以上の属性をクラス プロパティに追加して検証を行うことができます。 属性の<xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName>要素は、検証が失敗した場合にエラー メッセージのテキストを定義します。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降では、ASP.NET でエラー メッセージを簡単にローカライズできます。 エラー メッセージは次のような場合にローカライズされます。  
  
1.  <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName>検証属性で提供されています。  
  
2.  リソース ファイルが App_LocalResources フォルダーに格納されている。  
  
3.  ローカライズされたリソース ファイル名の形式`DataAnnotation.Localization.{`*名*`}.resx`ここで、*名*形式のカルチャ名は、*言語コード*`-`*国または地域番号*または*言語コード*します。  
  
4.  リソースのキーの名前は、文字列に割り当てられている、 <xref:System.ComponentModel.DataAnnotations.ValidationAttribute.ErrorMessage%2A?displayProperty=fullName>属性、およびその値は、ローカライズされたエラー メッセージ。  
  
 たとえば、次のデータ注釈属性は、無効なレベルの既定のカルチャのエラー メッセージを定義します。  
  
```csharp  
  
public class RatingInfo  
{  
   [Required(ErrorMessage = "The rating must be between 1 and 10.")]  
   [Display(Name = "Your Rating")]  
   public int Rating { get; set; }  
}  
  
```  
  
```vb  
  
Public Class RatingInfo  
   <Required(ErrorMessage = "The rating must be between 1 and 10.")>  
   <Display(Name = "Your Rating")>  
   Public Property Rating As Integer = 1  
End Class  
  
```  
  
 リソース ファイル、DataAnnotation.Localization.fr.resx、キーを持つエラー メッセージ文字列は、値がローカライズされたエラー メッセージを作成できます。 ファイルを検索する、`App.LocalResources`フォルダーです。 たとえば、次は、キーと、値は、ローカライズされたフランス語 (fr) 言語のエラー メッセージです。  
  
|名前|値|  
|----------|-----------|  
|評価は、1 ~ 10 でする必要があります。|Doit être メニュー 1 を構成する la 注 et 10 です。|  
  
 このファイルをこともできます。  
  
 また、データ注釈ローカリゼーションを拡張することができます。 開発者が実装することによって文字列ローカライザー プロバイダーに接続できます、 <xref:System.Web.Globalization.IStringLocalizerProvider>以外の場所に、ローカライズ文字列をリソース ファイルに格納するインターフェイスです。  
  
 **セッション状態ストアのプロバイダーとの非同期サポート**  
 ASP.NET では、セッション状態ストア プロバイダーでタスクを返すメソッドを使用できるようになりました。これにより、ASP.NET アプリで非同期のスケーラビリティのメリットが得られます。 非同期操作のセッション状態とストア プロバイダーをサポートする、ASP.NET には、新しいインターフェイスが含まれています。 <xref:System.Web.SessionState.ISessionStateModule?displayProperty=fullName>、から継承される<xref:System.Web.IHttpModule>により、開発者は、独自のセッション状態モジュールと async セッション ストア プロバイダーを実装するとします。 このインターフェイスは次のように定義されます。  
  
```csharp  
  
public interface ISessionStateModule : IHttpModule {  
    void ReleaseSessionState(HttpContext context);  
    Task ReleaseSessionStateAsync(HttpContext context);  
}  
  
```  
  
 さらに、 <xref:System.Web.SessionState.SessionStateUtility>クラスには、2 つの新しいメソッドが含まれています。 <xref:System.Web.SessionState.SessionStateUtility.IsSessionStateReadOnly%2A>と<xref:System.Web.SessionState.SessionStateUtility.IsSessionStateRequired%2A>、非同期操作をサポートするために使用できます。  
  
 **出力キャッシュ プロバイダーの非同期サポート**  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] 以降では、タスクを返すメソッドを出力キャッシュ プロバイダーで使用して、非同期のスケーラビリティのメリットを得ることができます。  これらのメソッドを実装するプロバイダーは、Web サーバー上のスレッド ブロックを減らし、ASP.NET サービスのスケーラビリティを向上させます。  
  
 非同期出力キャッシュ プロバイダーをサポートするために、次の API が追加されました。  
  
-   <xref:System.Web.Caching.OutputCacheProviderAsync?displayProperty=fullName>から継承されるクラスが<xref:System.Web.Caching.OutputCacheProvider?displayProperty=fullName>により、開発者が非同期の出力キャッシュ プロバイダーを実装するとします。  
  
-   <xref:System.Web.Caching.OutputCacheUtility>クラスで、出力キャッシュを構成するためのヘルパー メソッドを提供します。  
  
-   18 の新しいメソッドで、 <xref:System.Web.HttpCachePolicy?displayProperty=fullName>クラスです。 以下の<xref:System.Web.HttpCachePolicy.GetCacheability%2A>、 <xref:System.Web.HttpCachePolicy.GetCacheExtensions%2A>、 <xref:System.Web.HttpCachePolicy.GetETag%2A>、 <xref:System.Web.HttpCachePolicy.GetETagFromFileDependencies%2A>、 <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>、 <xref:System.Web.HttpCachePolicy.GetMaxAge%2A>、 <xref:System.Web.HttpCachePolicy.GetNoStore%2A>、 <xref:System.Web.HttpCachePolicy.GetNoTransforms%2A>、 <xref:System.Web.HttpCachePolicy.GetOmitVaryStar%2A>、 <xref:System.Web.HttpCachePolicy.GetProxyMaxAge%2A>、 <xref:System.Web.HttpCachePolicy.GetRevalidation%2A>、 <xref:System.Web.HttpCachePolicy.GetUtcLastModified%2A>、 <xref:System.Web.HttpCachePolicy.GetVaryByCustom%2A>、 <xref:System.Web.HttpCachePolicy.HasSlidingExpiration%2A>、および<xref:System.Web.HttpCachePolicy.IsValidUntilExpires%2A>します。  
  
-   2 つの新しい方法で、 <xref:System.Web.HttpCacheVaryByContentEncodings?displayProperty=fullName>クラス: <xref:System.Web.HttpCacheVaryByContentEncodings.GetContentEncodings%2A>と<xref:System.Web.HttpCacheVaryByContentEncodings.SetContentEncodings%2A>します。  
  
-   2 つの新しい方法で、 <xref:System.Web.HttpCacheVaryByHeaders?displayProperty=fullName>クラス: <xref:System.Web.HttpCacheVaryByHeaders.GetHeaders%2A>と<xref:System.Web.HttpCacheVaryByHeaders.SetHeaders%2A>します。  
  
-   2 つの新しい方法で、 <xref:System.Web.HttpCacheVaryByParams?displayProperty=fullName>クラス: <xref:System.Web.HttpCacheVaryByParams.GetParams%2A>と<xref:System.Web.HttpCacheVaryByParams.SetParams%2A>します。  
  
-   <xref:System.Web.Caching.AggregateCacheDependency?displayProperty=fullName> 、クラス、 <xref:System.Web.Caching.AggregateCacheDependency.GetFileDependencies%2A>メソッドです。  
  
-   <xref:System.Web.Caching.CacheDependency>、 <xref:System.Web.Caching.CacheDependency.GetFileDependencies%2A>メソッドです。  
  
<a name="Strings"></a>   
### <a name="character-categories"></a>文字カテゴリ  
 内の文字、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]に基づいて分類は、 [Unicode 標準のバージョン 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/)します。 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] と [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] では、文字は Unicode 6.3 文字のカテゴリに基づいて分類されました。  
  
 Unicode 8.0 のサポートは、文字の分類を制限、 <xref:System.Globalization.CharUnicodeInfo>クラスし、それに依存する型およびメソッドにします。 含まれます、 <xref:System.Globalization.StringInfo>クラスをオーバー ロードされた<xref:System.Char.GetUnicodeCategory%2A?displayProperty=fullName>メソッド、および[文字クラス](../../../docs/standard/base-types/character-classes-in-regular-expressions.md).NET Framework 正規表現エンジンによって認識されます。  文字や文字列の比較と並べ替えは、この変更の影響を受けることなく、引き続き基となるオペレーティング システムに依存します (Windows 7 システムの場合は、.NET Framework で提供される文字データに依存)。  
  
 Unicode 6.0 から 7.0 の Unicode の文字のカテゴリが変更されたのため、次を参照してください。 [Unicode 標準を、バージョン 7.0.0](http://www.unicode.org/versions/Unicode7.0.0/) Unicode Consortium の web サイトに掲載します。 変更は Unicode 7.0 Unicode 8.0 を次を参照してください。 [Unicode 標準を、バージョン 8.0.0](http://www.unicode.org/versions/Unicode8.0.0/) Unicode Consortium の web サイトに掲載します。  
  
<a name="Crypto462"></a>   
### <a name="cryptography"></a>暗号  
 **証明書を含む FIPS 186 3 DSA の X509 のサポート**  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] には、FIPS 186-2 の 1024 ビットという制限を超えるキーを持つ、DSA (Digital Signature Algorithm) X509 証明書のサポートが追加されています。  
  
 より大きな FIPS 186-3 のキー サイズのサポートに加えて、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、SHA-2 ファミリのハッシュ アルゴリズム (SHA256、SHA384、SHA512) によるシグネチャ計算も可能です。 FIPS 186 3 のサポートはによって提供される新しい<xref:System.Security.Cryptography.DSACng?displayProperty=fullName>クラスです。  
  
 最新の変更に合わせて、 <xref:System.Security.Cryptography.RSA> .NET Framework 4.6 のクラスと<xref:System.Security.Cryptography.ECDsa> 4.6.1、.NET Framework クラスに、 <xref:System.Security.Cryptography.DSA>抽象基本クラスで[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]キャストせずには、この機能を使用して呼び出し元を許可するその他の方法があります。 呼び出すことができます、 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPrivateKey%2A?displayProperty=fullName>拡張メソッドを次の例のように、データに署名します。  
  
```csharp  
  
public static byte[] SignDataDsaSha384(byte[] data, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPrivateKey())  
    {  
        return dsa.SignData(data, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function SignDataDsaSha384(data As Byte(), cert As X509Certificate2) As Byte()  
    Using DSA As DSA = cert.GetDSAPrivateKey()  
        Return DSA.SignData(data, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 呼び出すことができます、 <xref:System.Security.Cryptography.X509Certificates.DSACertificateExtensions.GetDSAPublicKey%2A?displayProperty=fullName>拡張メソッドを次の例のように、符号付きのデータを確認します。  
  
```csharp  
  
public static bool VerifyDataDsaSha384(byte[] data, byte[] signature, X509Certificate2 cert)  
{  
    using (DSA dsa = cert.GetDSAPublicKey())  
    {  
        return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384);  
    }  
}  
  
```  
  
```  
  
 Public Shared Function VerifyDataDsaSha384(data As Byte(), signature As Byte(), cert As X509Certificate2) As Boolean  
    Using dsa As DSA = cert.GetDSAPublicKey()  
        Return dsa.VerifyData(data, signature, HashAlgorithmName.SHA384)  
    End Using  
End Function  
  
```  
  
 **ECDiffieHellman キー派生ルーチンへの入力に明瞭さを向上**  
 .NET Framework 3.5 では、3 種類の KDF (キー派生関数) ルーチンによる Elliptic Curve Diffie-Hellman キー承諾のサポートが追加されました。 プロパティを使用して構成されていた、ルーチン、およびルーチン自体への入力、 <xref:System.Security.Cryptography.ECDiffieHellmanCng>オブジェクトです。 しかし、すべてのルーチンですべての入力プロパティが読み取られるわけではないため、これまで開発者がよく混乱することがありました。  
  
 これに対処する、 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]、次の&3; つのメソッドに追加された、 <xref:System.Security.Cryptography.ECDiffieHellman>基本 KDF ルーチンと、入力値をより明確に表すクラス。  
  
|ECDiffieHellman メソッド|説明|  
|----------------------------|-----------------|  
|[DeriveKeyFromHash (ECDiffieHellmanPublicKey HashAlgorithmName、バイト\[\]、バイト\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHash%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|次の式を使用してキー マテリアルを派生させます。<br /><br /> HASH(secretPrepend ||*x* | | secretAppend)<br /><br /> ハッシュ (secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> ここで*x* EC Diffie-hellman アルゴリズムの計算結果を示します。|  
|[DeriveKeyFromHmac (ECDiffieHellmanPublicKey HashAlgorithmName、バイト\[\]、バイト\[\]、バイト\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyFromHmac%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Security.Cryptography.HashAlgorithmName%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|次の式を使用してキー マテリアルを派生させます。<br /><br /> HMAC (hmacKey secretPrepend | |*x* | | secretAppend)<br /><br /> HMAC (hmacKey secretPrepend OrElse *x* OrElse secretAppend)<br /><br /> ここで*x* EC Diffie-hellman アルゴリズムの計算結果を示します。|  
|[DeriveKeyTls (ECDiffieHellmanPublicKey、バイト\[\]、バイト\<xref:System.Security.Cryptography.ECDiffieHellman.DeriveKeyTls%28System.Security.Cryptography.ECDiffieHellmanPublicKey%2CSystem.Byte%5B%5D%2CSystem.Byte%5B%5D%29>|TLS 擬似乱数関数 (PRF) 派生アルゴリズムを使用して、キー マテリアルを派生させます。|  
  
 **永続化キー対称暗号化のサポート**  
 Windows の暗号化ライブラリ (CNG) では、永続化された対称キーの格納とハードウェアに格納された対称キーの使用のサポートが追加され、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] で開発者はこの機能を利用できるようになりました。  キー名とキー プロバイダーの概念が実装に固有であるため、この機能を使用するには、推奨されるファクトリ手法 (`Aes.Create` の呼び出しなど) ではなく、具象実装型のコンストラクターを利用する必要があります。  
  
 AES の永続化キー対称暗号化のサポートが存在する (<xref:System.Security.Cryptography.AesCng>) および 3 des (<xref:System.Security.Cryptography.TripleDESCng>) アルゴリズム。 例:  
  
```csharp  
  
public static byte[] EncryptDataWithPersistedKey(byte[] data, byte[] iv)  
{  
    using (Aes aes = new AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider))  
    {  
        aes.IV = iv;  
  
        // Using the zero-argument overload is required to make use of the persisted key  
        using (ICryptoTransform encryptor = aes.CreateEncryptor())  
        {  
            if (!encryptor.CanTransformMultipleBlocks)  
            {  
                throw new InvalidOperationException("This is a sample, this case wasn’t handled...");  
            }  
  
            return encryptor.TransformFinalBlock(data, 0, data.Length);  
        }  
    }  
}  
  
```  
  
```vb  
  
Public Shared Function EncryptDataWithPersistedKey(data As Byte(), iv As Byte()) As Byte()  
    Using Aes As Aes = New AesCng("AesDemoKey", CngProvider.MicrosoftSoftwareKeyStorageProvider)  
        Aes.IV = iv  
  
        ' Using the zero-argument overload Is required to make use of the persisted key  
        Using encryptor As ICryptoTransform = Aes.CreateEncryptor()  
            If Not encryptor.CanTransformMultipleBlocks Then  
                Throw New InvalidOperationException("This is a sample, this case wasn’t handled...")  
            End If  
            Return encryptor.TransformFinalBlock(data, 0, data.Length)  
        End Using  
    End Using  
End Function  
  
```  
  
 **Sha-2 ハッシュの SignedXml サポート**  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]にサポートが追加されて、 <xref:System.Security.Cryptography.Xml.SignedXml>ダイジェスト アルゴリズムを rsa-sha256、RSA SHA384、SHA512 RSA PKCS&#1; の署名方法と、SHA256、SHA384、SHA512 リファレンス クラスです。  
  
 URI の定数がすべてで公開されている<xref:System.Security.Cryptography.Xml.SignedXml>:  
  
|SignedXml フィールド|定数|  
|---------------------|--------------|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA256Url>|"http://www.w3.org/2001/04/xmlenc#sha256"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA256Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha256"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#sha384"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA384Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha384"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigSHA512Url>|"http://www.w3.org/2001/04/xmlenc#sha512"|  
|<xref:System.Security.Cryptography.Xml.SignedXml.XmlDsigRSASHA512Url>|"http://www.w3.org/2001/04/xmldsig-more#rsa-sha512"|  
  
 カスタムを登録するすべてのプログラム<xref:System.Security.Cryptography.SignatureDescription>にハンドラー <xref:System.Security.Cryptography.CryptoConfig>これらのアルゴリズムは引き続き、過去に行ったことがあるのでここでのプラットフォームの既定値 としての機能をサポートするため、 <xref:System.Security.Cryptography.CryptoConfig>登録は必要なくなりました。  
  
<a name="SQLClient"></a>   
### <a name="sqlclient"></a>SqlClient  
 .NET framework Data Provider for SQL Server (<xref:System.Data.SqlClient?displayProperty=fullName>) で次の新機能が含まれています、 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]:  
  
 **接続プールと Azure SQL データベースとタイムアウト**  
 接続プールが有効な状態で、タイムアウトまたは他のログイン エラーが発生した場合は、例外がキャッシュされ、キャッシュされた例外は次の 5 秒から 1 分の間の後続の接続試行時にすべてスローされます。  詳細については、次を参照してください。 [SQL サーバー接続プール (ADO.NET)](../../../docs/framework/data/adonet/sql-server-connection-pooling.md)します。  
  
 通常は迅速に復旧される一時的なエラーで接続試行が失敗する可能性があるため、Azure SQL Database への接続時のこの動作は望ましくありません。 接続試行操作をより最適化するため、Azure SQL Database への接続が失敗した場合は、接続プールのブロック期間の動作は削除されます。  
  
 新しい `PoolBlockingPeriod` キーワードを追加することで、使用しているアプリに最適なブロック期間を選択できます。 次の値が含まれます。  
  
 `Auto`  
 Azure SQL Database に接続しているアプリケーションの接続プールのブロック期間は無効になり、他のすべての SQL Server インスタンスに接続しているアプリケーションの接続プールのブロック期間が有効になります。 これが既定値です。 サーバー エンドポイント名の末尾が以下のいずれかである場合は、Azure SQL Database と見なされます。  
  
-   .database.windows.net  
  
-   .database.chinacloudapi.cn  
  
-   .database.usgovcloudapi.net  
  
-   .database.cloudapi.de  
  
 `AlwaysBlock`  
 接続プールのブロック期間は常に有効になります。  
  
 `NeverBlock`  
 接続プールのブロック期間は常に無効になります。  
  
 **拡張機能は常に暗号化の**  
 SQLClient では、Always Encrypted の以下の&2; つの機能が強化されました。  
  
-   暗号化されたデータベースの列に対するパラメーター クエリのパフォーマンスを向上させるために、クエリ パラメーターの暗号化メタデータがキャッシュされるようになりました。 <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionQueryMetadataCacheEnabled%2A?displayProperty=fullName>プロパティに設定`true`(既定値は、)、同じクエリを複数回呼び出すと、クライアント パラメーターのメタデータ サーバーから&1; 回だけ取得します。  
  
-   キーのキャッシュ内の列暗号化キーのエントリが設定を使用して、構成可能な時間間隔後に解放されるようになりました、 <xref:System.Data.SqlClient.SqlConnection.ColumnEncryptionKeyCacheTtl%2A?displayProperty=fullName>プロパティです。  
  
<a name="WCF"></a>   
### <a name="windows-communication-foundation"></a>Windows Communication Foundation  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、Windows Communication Foundation の次の領域の機能が強化されています。  
  
 **CNG を使用して格納されている証明書を WCF トランスポート セキュリティのサポート**  
 WCF トランスポート セキュリティでは、Windows 暗号化ライブラリ (CNG) を使用して格納される証明書がサポートされます。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、このサポートは、指数の長さが 32 ビット以下の公開キーを持つ証明書を使用する場合に限定されます。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] を対象とするアプリケーションでは、この機能は既定で有効になります。  
  
 対象とするアプリケーションの[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]以前ですが実行していると、 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)]、次の行を追加することで、この機能を有効にすることができます、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config または web.config ファイルのセクションです。  
  
```xml  
  
<AppContextSwitchOverrides  
    value="Switch.System.ServiceModel.DisableCngCertificates=false"  
/>  
  
```  
  
 以下のようなコードを使用してプログラムで行うこともできます。  
  
```csharp  
  
private const string DisableCngCertificates = @"Switch.System.ServiceModel.DisableCngCertificates";  
AppContext.SetSwitch(disableCngCertificates, false);  
  
```  
  
```vb  
  
Const DisableCngCertificates As String = "Switch.System.ServiceModel.DisableCngCertificates"  
AppContext.SetSwitch(disableCngCertificates, False)  
  
```  
  
 **DataContractJsonSerializer クラスによって夏時間調整規則が複数のサポートの強化**  
 お客様は、決定をアプリケーション構成の設定を使用しているかどうか、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>クラスは、1 つのタイム ゾーンの複数の調整規則をサポートしています。 これはオプトイン機能です。 これを有効にするには、app.config ファイルに次の設定を追加します。  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides value="Switch.System.Runtime.Serialization.DoNotUseTimeZoneInfo=false" />  
</runtime>  
  
```  
  
 この機能が有効にすると、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>オブジェクトが使用、 <xref:System.TimeZoneInfo>型の代わりに、<xref:System.TimeZone>日付と時刻のデータを逆シリアル化する型。 <xref:System.TimeZoneInfo>履歴のタイム ゾーンのデータを使用することが複数の調整規則をサポートしています  <xref:System.TimeZone>しません。  
  
 詳細については、 <xref:System.TimeZoneInfo>構造とタイム ゾーン調整を参照してください[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)します。  
  
 **時刻、UTC を保持するためのサポートおよび XMLSerializer クラスを使用して逆シリアル化**  
 通常、ときに、 <xref:System.Xml.Serialization.XmlSerializer>クラスは、UTC をシリアル化に使用<xref:System.DateTime>値、日付と時刻を保持しますが、時間がローカルでと想定するシリアル化されたタイム文字列を作成します。  たとえば、次のコードを呼び出して UTC 日時をインスタンス化するとします。  
  
```csharp  
DateTime utc = new DateTime(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc);  
```  
  
```vb  
Dim utc As New Date(2016, 11, 07, 3, 0, 0, DateTimeKind.Utc)  
```  
  
 この場合、システムのシリアル化された時刻文字列は、UTC より&8; 時間遅れの "03:00:00.0000000-08:00" となります。  シリアル化された値は常に、現地日時の値として逆シリアル化されます。  
  
 アプリケーション構成の設定を使用するを判断するかどうか、 <xref:System.Xml.Serialization.XmlSerializer>シリアル化とシリアル化するときに、UTC タイム ゾーン情報が保持されます<xref:System.DateTime>値。  
  
```xml  
  
<runtime>  
     <AppContextSwitchOverrides   
          value="Switch.System.Runtime.Serialization.DisableSerializeUTCDateTimeToTimeAndDeserializeUTCTimeToUTCDateTime=false" />  
</runtime>  
  
```  
  
 この機能が有効にすると、 <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>オブジェクトが使用、 <xref:System.TimeZoneInfo>型の代わりに、<xref:System.TimeZone>日付と時刻のデータを逆シリアル化する型。 <xref:System.TimeZoneInfo>履歴のタイム ゾーンのデータを使用することが複数の調整規則をサポートしています  <xref:System.TimeZone>しません。  
  
 詳細については、 <xref:System.TimeZoneInfo>構造とタイム ゾーン調整を参照してください[タイム ゾーンの概要](../../../docs/standard/datetime/time-zone-overview.md)します。  
  
 **NetNamedPipeBinding 最適な一致**  
 WCF には、クライアント アプリケーションで設定できる新しいアプリ設定があります。これにより、クライアント アプリケーションは常に、要求したものと最も一致する URI でリッスンしているサービスに接続できます。 このアプリケーション設定`false`(既定値) を使用してクライアントは<xref:System.ServiceModel.NetNamedPipeBinding>要求された URI の部分文字列である URI をリッスンするサービスに接続しようとします。  
  
 たとえば、クライアントが `net.pipe://localhost/Service1` でリッスンしているサービスに接続しようとしているときに、管理者特権で実行しているコンピューター上の別のサービスが `net.pipe://localhost` でリッスンしているとします。 このアプリ設定が `false` に設定されている場合、クライアントは間違ったサービスに接続しようとします。 アプリ設定を `true` に設定すれば、クライアントは常に最も一致するサービスに接続するようになります。  
  
> [!NOTE]
>  使用してクライアント<xref:System.ServiceModel.NetNamedPipeBinding>完全なエンドポイント アドレスではなく (ある場合) をサービスのベース アドレスに基づくサービスを検索します。 この設定が常に機能するようにするには、サービスは一意のベース アドレスを使用する必要があります。  
  
 この変更を有効にするには、以下のアプリ設定をクライアント アプリケーションの App.config ファイルまたは Web.config ファイルに追加します。  
  
```xml  
  
<configuration>  
    <appSettings>  
        <add key="wcf:useBestMatchNamedPipeUri" value="true" />  
    </appSettings>  
</configuration>  
  
```  
  
 **SSL 3.0 が既定のプロトコルではありません。**  
 トランスポート セキュリティで NetTcp を使用し、証明書の資格情報の種類を使用する場合、SSL 3.0 は、安全な接続のネゴシエーションに使用される既定のプロトコルではなくなりました。 TLS 1.0 が NetTcp のプロトコル一覧に含まれているため、ほとんどの場合、既存のアプリには影響はないと考えられます。 既存のすべてのクライアントは TLS 1.0 以降を使用して接続をネゴシエートできるようになりました。      Ssl3 が必要な場合は、以下の構成メカニズムのいずれかを使用して、ネゴシエートされたプロトコルの一覧に追加します。  
  
-   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement.SslProtocols%2A?displayProperty=fullName>プロパティ  
  
-   <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A?displayProperty=fullName>プロパティ  
  
-   The [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md) section of the [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) section  
  
-   The [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) section of the [<>\>](../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) section  
  
<a name="WPF462"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、Windows Presentation Foundation の次の領域の機能が強化されています。  
  
 **グループの並べ替え**  
 使用するアプリケーション、 <xref:System.Windows.Data.CollectionView>データをグループ化するオブジェクトは、グループを並べ替える方法を明示的に宣言できますようになりました。 明示的な並べ替えにより、アプリがグループを動的に追加または削除する場合や、グループ化に関連する項目のプロパティの値を変更する場合に発生する非直感的な順序付けの問題が解決されます。 また、グループ化プロパティの比較がコレクション全体の並べ替えからグループの並べ替えに変更されるため、グループ作成プロセスのパフォーマンスを向上させることができます。  
  
 グループの並べ替えをサポートするために、新しい<xref:System.ComponentModel.GroupDescription.SortDescriptions%2A?displayProperty=fullName>と<xref:System.ComponentModel.GroupDescription.CustomSort%2A?displayProperty=fullName>プロパティによって生成されるグループのコレクションを並べ替える方法を説明する、 <xref:System.ComponentModel.GroupDescription>オブジェクトです。 これは同じ名前を持つ方法に似ています<xref:System.Windows.Data.ListCollectionView>プロパティは、データ項目を並べ替える方法を説明します。  
  
 2 つの新しい静的なプロパティ、 <xref:System.Windows.Data.PropertyGroupDescription>クラス、 <xref:System.Windows.Data.PropertyGroupDescription.CompareNameAscending%2A>と<xref:System.Windows.Data.PropertyGroupDescription.CompareNameDescending%2A>、最も一般的な場合に使用できます。  
  
 たとえば、次の XAML ではデータを年齢でグループ化し、年齢グループを昇順に並べ替え、各年齢グループ内の項目を姓でグループ化します。  
  
```xaml  
  
<GroupDescriptions>  
     <PropertyGroupDescription   
         PropertyName=”Age”   
         CustomSort=   
              ”{x:Static PropertyGroupDescription.CompareNamesAscending}”/>  
     </PropertyGroupDescription>  
</GroupDescriptions>  
  
<SortDescriptions>  
     <SortDescription PropertyName=”LastName”/>  
</SortDescriptions>  
  
```  
  
 **ソフト キーボードのサポート**  
 ソフト キーボードのサポートにより、WPF アプリケーションでのフォーカス追跡が可能になります。テキスト入力が可能なコントロールによりタッチ入力を受信すると、Windows 10 の新しいソフト キーボードが自動的に起動および終了します。  
  
 .NET Framework の以前のバージョンでは、WPF アプリケーションは、WPF のペン/タッチ ジェスチャ サポートを無効にしないとフォーカス追跡を選択できません。  そのため、WPF アプリケーションは完全な WPF タッチのフル サポートを選ぶか、Windows のマウス プロモーションに依存する必要があります。  
  
 **モニターごとの DPI**  
 WPF アプリ用の高 DPI とハイブリッド DPI 環境の最近の急激な増加に対応するために、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)] の WPF でモニターごとに対応できるようになりました。 参照してください、[サンプルと開発者ガイド](https://github.com/Microsoft/WPF-Samples/tree/master/PerMonitorDPI)モニターごとの DPI 対応になる WPF アプリを有効にする方法の詳細についての GitHub のです。  
  
 .NET Framework の以前のバージョンでは、WPF アプリはシステム DPI 対応です。 つまり、アプリケーションの UI は、アプリがレンダリングされるモニターの DPI に基づき、必要に応じて OS でスケーリングされます。 ,  
  
 実行するアプリケーションの[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]、構成のステートメントを追加することで WPF アプリでは、モニターごとの DPI の変更を無効にすることができます、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)アプリケーション構成のセクションでファイルの次のようにします。  
  
```xml  
  
<runtime>  
   <AppContextSwitchOverrides value=”Switch.System.Windows.DoNotScaleForDpiChanges=false”/>  
</runtime>  
  
```  
  
<a name="WF462"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] では、Windows Workflow Foundation の次領域の機能が強化されています。  
  
 **C# の式と Re-hosted WF デザイナーでは、IntelliSense のサポート**  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] 以降では、WF によって、Visual Studio デザイナーとコード ワークフローの両方で C# 式がサポートされます。 再ホストされたワークフロー デザイナーは WF の主な機能です。これにより、ワークフロー デザイナーを Visual Studio の外部のアプリケーション (WPF など) で使用できるようになります。  Windows Workflow Foundation は、再ホストされたワークフロー デザイナーで C# 式と IntelliSense をサポートできるようにします。 詳細については、次を参照してください。、 [Windows Workflow Foundation ブログ](http://go.microsoft.com/fwlink/?LinkID=809042&clcid=0x409)します。  
  
 `Availability of IntelliSense when a customer rebuilds a workflow project from Visual Studio`  
 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] より前のバージョンの .NET Framework で、お客様が Visual Studio からワークフロー プロジェクトを再ビルドした場合、WF Designer IntelliSense は破損してしまいます。 プロジェクトのビルドが成功した、ワークフローの種類は、デザイナー上に存在しないおよびで不足しているワークフローの種類の IntelliSense からの警告が表示される間、**エラー一覧**ウィンドウです。 [!INCLUDE[net_v462](../../../includes/net-v462-md.md)] はこの問題に対処し、IntelliSense を使用できるようにします。  
  
 **ここでのワークフローの追跡とワークフロー V1 アプリケーション FIPS モードで実行します。**  
 FIPS コンプライアンス モードが有効なコンピューターで、ワークフロー追跡が有効なワークフロー バージョン 1 スタイルのアプリケーションを正常に実行できるようになりました。 このシナリオを有効にするには、app.config ファイルを以下のように変更する必要があります。  
  
```xml  
<add key="microsoft:WorkflowRuntime:FIPSRequired" value="true" />  
```  
  
 このシナリオが有効でない場合、アプリケーションを実行すると、引き続き例外が生成され、"この実装は Windows プラットフォーム FIPS 検証暗号化アルゴリズムの一部ではありません" というメッセージが表示されます。  
  
 **Visual Studio ワークフロー デザイナーで動的更新を使用する場合のワークフローの強化**  
 ワークフロー デザイナー、フローチャート アクティビティ デザイナー、およびその他のワークフロー アクティビティ デザイナーこれで正常に読み込んで表示呼び出した後に保存されているワークフロー、 <xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName>メソッドです。 前に .NET Framework のバージョンで、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]を呼び出した後に保存されているワークフローの Visual Studio で XAML ファイルの読み込み<xref:System.Activities.DynamicUpdate.DynamicUpdateServices.PrepareForUpdate%2A?displayProperty=fullName>次の問題が発生することができます。  
  
-   ワークフロー デザイナーでは、XAML ファイルを正しく読み込めませんでした (ときに、 <xref:System.Activities.Presentation.ViewState.ViewStateData.Id%2A?displayProperty=fullName>行の末尾にある)。  
  
-   フローチャート アクティビティ デザイナーまたは他のワークフロー アクティビティ デザイナーで、アタッチされるプロパティの値ではなく既定の場所にすべてのオブジェクトが表示される場合がある。  
  
<a name="ClickOnce"></a>   
### <a name="clickonce"></a>ClickOnce  
 ClickOnce が更新され、既にサポートされている 1.0 プロトコルに加え、TLS 1.1 と TLS 1.2 がサポートがサポートされるようになりました。 ClickOnce が必要なプロトコルを自動的に検出するため、TLS 1.1 と 1.2 のサポートを有効にするために、ClickOnce アプリケーション内での追加の手順は不要です。  
  
<a name="UWPConvert"></a>   
### <a name="converting-windows-forms-and-wpf-apps-to--uwp-apps"></a>Windows フォームおよび WPF アプリの UWP アプリへの変換  
 Windows では、WPF および Windows フォーム アプリを含む、既存の Windows デスクトップ アプリを UWP (ユニバーサル Windows プラットフォーム) で使用できるようになりました。 このテクノロジはブリッジとして機能し、既存のコード ベースを段階的に UWP に移行し、アプリをすべての Windows 10 デバイスで使用できるようにします。  
  
 変換後のデスクトップ アプリは UWP アプリのアプリ ID のようなアプリ ID を取得し、UWP API をアクセス可能にして、ライブ タイルや通知などの機能を有効にすることができます。 アプリは引き続き従来どおり動作し、完全信頼アプリとして実行されます。 アプリが変換されたら、アプリ コンテナー プロセスを既存の完全信頼プロセスに追加し、適応ユーザー インターフェイスを追加できます。 すべての機能がアプリ コンテナー プロセスに移行されたら、完全信頼プロセスを削除し、新しい UWP アプリをすべての Windows 10 デバイスで有効にすることができます。  
  
<a name="Debug462"></a>   
### <a name="debugging-improvements"></a>デバッグの機能強化  
 *アンマネージ デバッグ API*で強化されています、[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]詳細な分析を実行するときに、 <xref:System.NullReferenceException>をソース コードの単一の行には、どの変数が特定されるようにスローされる`null`します。   このシナリオをサポートするために、次の API がアンマネージ デバッグ API に追加されました。  
  
-   [ICorDebugCode4](../../../ocs/framework/unmanaged-api/debugging/icordebugcode4-interface.md)、 [ICorDebugVariableHome](../../../ocs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)、および[ICorDebugVariableHomeEnum](../../../ocs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)インターフェイスで、マネージ変数のネイティブの家を公開します。 これにより、デバッガーはコード フロー分析を実行するときに、 <xref:System.NullReferenceException>が発生したと判断されたネイティブの位置に対応する管理対象の変数に旧バージョンと作業`null`します。  
  
-   [ICorDebugType2::GetTypeID](../Topic/ICorDebugType2::GetTypeID%20Method.md)メソッドでは、マッピングを提供する ICorDebugType の[COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md)、これを使用すると、デバッガーは、取得、 [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md) ICorDebugType のインスタンスなし。 既存の Api [COR_TYPEID](../../../ocs/framework/unmanaged-api/debugging/cor-typeid-structure.md)型のクラス レイアウトを決定し、使用できます。  
  
<a name="v461"></a>   
## <a name="whats-new-in-the-net-framework-461"></a>.NET Framework 4.6.1 の新機能  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] には、次の領域における新機能が含まれています。  
  
-   [暗号化](#Crypto)  
  
-   [ADO.NET](#ADO.NET461)  
  
-   [Windows Presentation Foundation (WPF)](#WPF461)  
  
-   [Windows Workflow Foundation](#WWF461)  
  
-   [プロファイリング](#Profile461)  
  
-   [NGen](#NGEN461)  
  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] の詳細については、次のトピックを参照してください。  
  
-   [変更の .NET Framework 4.6.1 一覧](http://go.microsoft.com/fwlink/?LinkId=622964)  
  
-   [4.6.1 アプリケーションの互換性](../../../docs/framework/migration-guide/application-compatibility-in-the-net-framework-4-6-1.md)  
  
-   [.NET Framework API の相違](http://go.microsoft.com/fwlink/?LinkId=622989)(GitHub) に  
  
<a name="Crypto"></a>   
### <a name="cryptography-support-for-x509-certificates-containing-ecdsa"></a>暗号化: ECDSA を含む X509 証明書のサポート  
 .NET Framework 4.6 では、X509 証明書の RSACng サポートが追加されました。 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] では、ECDSA (Elliptic Curve Digital Signature Algorithm: 楕円曲線デジタル署名アルゴリズム) X509 証明書のサポートが追加されました。  
  
 ECDSA は、RSA よりも安全な暗号化アルゴリズムで、パフォーマンスも向上するため、トランスポート層セキュリティ (TLS) のパフォーマンスとスケーラビリティが問題になる場合に最適な選択肢です。 .NET Framework の実装では、既存の Windows 機能の呼び出しがラップされます。  
  
 次のサンプル コードでは、[!INCLUDE[net_v461](../../../includes/net-v461-md.md)] での新しい ECDSA X509 証明書のサポートを使用してバイト ストリームの署名が簡単に生成できることを示しています。  
  
 [!code-csharp[whatsnew.461.crypto#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#1)]
 [!code-vb[whatsnew.461.crypto#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code461.vb#1)]  
  
 このコードは、.NET Framework 4.6 での署名の生成に必要な次のコードとは大きく異なっています。  
  
 [!code-csharp[whatsnew.461.crypto#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.461.crypto/cs/Code46.cs#2)]
 [!code-vb[whatsnew.461.crypto#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.461.crypto/vb/Code46.vb#2)]  
  
<a name="ADO.NET461"></a>   
### <a name="adonet"></a>ADO.NET  
 次のものが ADO.NET に追加されました。  
  
 ハードウェア保護キーに対する Always Encrypted のサポート  
 ADO.NET では、Always Encrypted 列 (常に暗号化される列) のマスター キーをハードウェア セキュリティ モジュール (HSM) に格納することが、ネイティブでサポートされるようになりました。 このサポートによって、ユーザーは、HSM に格納された非対称キーを利用できます。カスタムの列マスター キー ストア プロバイダーを作成してからアプリケーションに登録する必要はありません。  
  
 HSM に格納された列マスター キーで保護された Always Encrypted データにアクセスするには、HSM ベンダー提供の CSP プロバイダーまたは CNG キー ストア プロバイダーをアプリ サーバーまたはクライアント コンピューターにインストールする必要があります。  
  
 向上<xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A> AlwaysOn の接続の動作  
 SqlClient で、AlwaysOn 可用性グループ (AG) へのより高速な接続が自動的に提供されるようになりました。 SqlClient では、アプリケーションが別のサブネット上の AlwaysOn 可用性グループ (AG) に接続しているかどうかを自動的に検出し、現在のアクティブなサーバーを迅速に探索し、そのサーバーへの接続を提供します。 このリリースよりも前は、アプリケーションで接続文字列を設定し、`“MultisubnetFailover=true”` を含め、AlwaysOn 可用性グループに接続されていることを示す必要がありました。 `true` への接続キーワードを設定しないと、アプリケーションで AlwaysOn 可用性グループに接続中にタイムアウトが発生する可能性がありました。 アプリケーションではこのリリースで*いない*を設定する必要がある<xref:System.Data.SqlClient.SqlConnectionStringBuilder.MultiSubnetFailover%2A>に`true`できなくなります。 Always On 可用性グループに対する SqlClient サポートの詳細については、次を参照してください。[高可用性、災害復旧のための SqlClient サポート](../../../docs/framework/data/adonet/sql/sqlclient-support-for-high-availability-disaster-recovery.md)します。  
  
<a name="WPF461"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 Windows Presentation Foundation には、さまざまな改善と変更が含まれています。  
  
 パフォーマンスの向上  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] で、タッチ イベントの開始の遅延が修正されました。 さらに、入力、 <xref:System.Windows.Controls.RichTextBox>コントロールが不要になった高速の入力時にレンダリング スレッドを占有します。  
  
 スペル チェック機能の改善  
 WPF のスペル チェック機能が、追加の言語のスペル チェックのためにオペレーティング システムのサポートを利用するように、Windows 8.1 以降のバージョンで更新されました。  Windows 8.1 よりも前の Windows バージョンの機能の変更はありません。  
  
 以前のバージョンの .NET Framework の言語と同様に、 <xref:System.Windows.Controls.TextBox>かを制御<xref:System.Windows.Controls.RichTextBox>ブロックが次の順序で情報を探すことによって検出されました。  
  
-   `xml:lang` (存在する場合)。  
  
-   現在の入力言語。  
  
-   現在のスレッド カルチャ。  
  
 WPF でサポートされる言語の詳細については、次を参照してください。、 [WPF のブログ投稿については、.NET Framework 4.6.1 機能](http://go.microsoft.com/fwlink/?LinkID=691819)です。  
  
 ユーザーごとのユーザー辞書の追加サポート  
 [!INCLUDE[net_v461](../../../includes/net-v461-md.md)] では、WPF で、グローバルに登録されているユーザー辞書が認識されます。 この機能は、ユーザー辞書をコントロールごとに登録する機能に加えて使用できます。  
  
 以前のバージョンの WPF では、ユーザー辞書で除外された単語とオートコレクト リストが認識されませんでした。 `%AppData%\Microsoft\Spelling\<language tag>` ディレクトリに配置できるファイルの使用によって、これらが Windows 8.1 と Windows 10 でサポートされます。  これらのファイルには、次の規則が適用されます。  
  
-   これらのファイルには、拡張子の .dic (追加された単語の場合)、.exc (除外された単語の場合)、または .acl (オートコレクトの場合) が付いている必要があります。  
  
-   これらのファイルは、バイト オーダー マーク (BOM) で始まる UTF-16 LE プレーン テキストである必要があります。  
  
-   各行があります (追加と除外された単語のリストにある) に含まれる単語または、縦棒で区切られた単語と、オート コレクトの組み合わせ ("|")で、自動修正候補の一覧)。  
  
-   これらのファイルは読み取り専用と見なされ、システムによって変更されることはありません。  
  
> [!NOTE]
>  これらの新しいファイル形式は、WPF スペル チェック API で直接サポートされるわけではありません。また、アプリケーションで WPF に提供されるユーザー辞書では以前と同様に .lex ファイルを使用する必要があります。  
  
 サンプル  
 数がある[WPF サンプル](https://msdn.microsoft.com/library/ms771633.aspx)MSDN にします。 移動されます (その使用法に基づく) 最も人気のあるサンプルの 200 を超える、[オープン ソースの GitHub リポジトリ](https://github.com/Microsoft/WPF-Samples)します。 プル要求またはオープンを送信することで、サンプルの改善にご協力を[GitHub 問題](https://github.com/Microsoft/WPF-Samples/issues)します。  
  
 DirectX の拡張機能  
 WPF には、 [NuGet パッケージ](http://go.microsoft.com/fwlink/?LinkID=691342)の新しい実装を提供する<xref:System.Windows.Interop.D3DImage>をやすく DX10 および Dx11 と相互運用するためのコンテンツ。 コードは、このパッケージが開かれているために発生する場所し、が利用可能な[github](https://github.com/Microsoft/WPFDXInterop)します。  
  
<a name="WWF461"></a>   
### <a name="windows-workflow-foundation-transactions"></a>Windows Workflow Foundation: トランザクション  
 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName>メソッドに、トランザクションを昇格させる MSDTC 以外の分散トランザクション マネージャーを使用できます。 新しい GUID トランザクション プロモーター識別子を指定して、これを行う<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName>オーバー ロードします。 この操作が成功すると、そのトランザクションの機能に制限が加えられます。 次のメソッドがスローする非 MSDTC トランザクション プロモーターが参加すると、 <xref:System.Transactions.TransactionPromotionException>これらのメソッドは、MSDTC への昇格を必要とするため。  
  
-   <xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetDtcTransaction%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetExportCookie%2A?displayProperty=fullName>  
  
-   <xref:System.Transactions.TransactionInterop.GetTransmitterPropagationToken%2A?displayProperty=fullName>  
  
 MSDTC 以外のトランザクション プロモーターが登録されると、そのプロモーターで定義するプロトコルを使用することで、そのプロモーターをその後の永続参加リストに使用する必要があります。 <xref:System.Guid>を使用して、トランザクションのプロモーターを取得できます、 <xref:System.Transactions.Transaction.PromoterType%2A>プロパティです。 ときに、トランザクションを促進、トランザクション プロモーター提供、<xref:System.Byte>昇格したトークンを表す配列。 アプリケーションでの非 MSDTC 昇格されたトランザクションの昇格したトークンを取得する、 <xref:System.Transactions.Transaction.GetPromotedToken%2A>メソッドです。  
  
 新しいユーザー <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%28System.Transactions.IPromotableSinglePhaseNotification%2CSystem.Guid%29?displayProperty=fullName>オーバー ロードが、昇格操作が正常に完了するために特定の呼び出し順序に従う必要があります。 これらの規則は、メソッドのドキュメントに記載されています。  
  
<a name="Profile461"></a>   
### <a name="profiling"></a>プロファイル  
 アンマネージ プロファイル API が、次のように拡張されました。  
  
 Pdb へのアクセスのサポートの強化、 [ICorProfilerInfo7](../../../ocs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)インターフェイス  
 ASP.NET 5 では、アセンブリがメモリ内で Roslyn によってコンパイルされることがよりいっそう一般的になっています。 プロファイル ツールを作成する開発者にとって、これは従来ディスクにシリアル化されていた PDB が存在しなくなる可能性があることを意味しています。 プロファイル ツールでは、多くの場合 PDB を使用して、コード カバレッジや&1; 行単位のパフォーマンス分析などのタスクのソース行に、コードをマップし戻します。 [ICorProfilerInfo7](../../../ocs/framework/unmanaged-api/profiling/icorprofilerinfo7-interface.md)インターフェイスは、2 つの新しいメソッド[ICorProfilerInfo7::GetInMemorySymbolsLength](../Topic/ICorProfilerInfo7::GetInMemorySymbolsLength%20Method.md)と[ICorProfilerInfo7::ReadInMemorySymbols](../Topic/ICorProfilerInfo7::ReadInMemorySymbols.md)メモリ内の PDB データへのアクセスにこれらのプロファイラー ツールを提供する新しい Api を使用すると、プロファイラーことができますをバイト配列として、メモリ内の pdb ファイルの内容を取得し、それを処理またはディスクにシリアル化します。  
  
 ICorProfiler インターフェイスを使用したインストルメンテーションの改良  
 動的インストルメンテーションに `ICorProfiler` API の ReJit 機能を使用しているプロファイラーで、いくつかのメタデータを変更できるようになりました。 従来、このようなツールでは、いつでも IL をインストルメント化できましたが、メタデータを変更できるのはモジュールを読み込む時だけでした。 IL はメタデータを参照するため、実行できるインストルメンテーションの種類が限られています。 追加することでこれらの制限の一部の廃止して、 [ICorProfilerInfo7::ApplyMetaData](../Topic/ICorProfilerInfo7::ApplyMetaData%20Method.md)モジュールが読み込まれた後、具体的には新規に追加して、メタデータの編集のサブセットをサポートするためにメソッド`AssemblyRef`、 `TypeRef`、 `TypeSpec`、 `MemberRef`、 `MemberSpec`、および`UserString`レコードです。 この変更により、はるかに広範な実行時インストルメンテーションが可能になります。  
  
<a name="NGEN461"></a>   
### <a name="native-image-generator-ngen-pdbs"></a>ネイティブ イメージ ジェネレーター (NGEN) PDB  
 マシン間のイベント トレースを使用すれば、ユーザーはマシン A 上でプログラムのプロファイリングを行い、マシン B 上でソース行のマッピングを使用して、プロファイリング データを確認できます。以前のバージョンの.NET Framework を使用する場合、ソースからネイティブへのマッピングを作成するには、ユーザーは、プロファイルされたコンピューターにあるすべてのモジュールとネイティブ イメージを、IL PDB が含まれた分析用コンピューターにコピーする必要がありました。 この処理は、Phone アプリケーションなどファイル サイズが比較的小さい場合には高速に実行されますが、これらのファイルのサイズがデスクトップ システム上で非常に大きくなる可能性があり、その場合コピーにかなりの時間を要する可能性があります。  
  
 NGen PDB を使用すれば、IL PDB に依存することなく、NGen で IL からネイティブへのマッピングが含まれた PDB を作成できます。 コンピューター B にコンピューター A によって生成される PDB のネイティブ イメージをコピーし、使用するには必要なは、シナリオでは、コンピューター間のイベント トレース、[インターフェイス Api へのアクセスでデバッグ](https://msdn.microsoft.com/en-us/library/ee8x173s.aspx)IL PDB のソースの IL のマッピングとネイティブ イメージ PDB の IL からネイティブへのマッピングを読み取れません。 両方のマッピングを組み合わせることで、ソースからネイティブへのマッピングが実現します。 ネイティブ イメージの PDB は、どのモジュールとネイティブ イメージよりもはるかにサイズが小さいため、コンピューター A からコンピューター B へのコピーの処理は非常に高速になります。  
  
<a name="v46"></a>   
## <a name="whats-new-in-net-2015"></a>.NET 2015 の新機能  
 .NET 2015 では、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)] と .NET Core が導入されています。 一部の新機能はその両方に適用され、その他の機能は [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] または [!INCLUDE[net_core](../../../includes/net-core-md.md)] に固有です。  
  
-   **ASP.NET 5**  
  
     .NET 2015 には、ASP.NET 5 が含まれています。これは、最新のクラウド ベースのアプリを構築するのに非常に効率の良い .NET プラットフォームです。 このプラットフォームはモジュール形式であるため、アプリケーションで必要な機能のみを含めることができます。 IIS でホストすることも、カスタムのプロセスでセルフホストすることもできます。さらに同じサーバー上のさまざまなバージョンの .NET Framework でアプリを実行することも可能です。 クラウド展開用に設計されている新たな環境構成システムが含まれています。  
  
     MVC、Web API、および Web ページは、MVC 6 と呼ばれる 1 つのフレームワークに統合されています。 Visual Studio 2015 の新しいツールで ASP.NET 5 アプリをビルドします。 既存のアプリケーションは、この新しい .NET Framework で動作しますが、MVC 6 または SignalR 3 を使用するアプリケーションをビルドするには Visual Studio 2015 のプロジェクト システムを使用する必要があります。  
  
     詳細については、次を参照してください。 [ASP.NET 5](http://go.microsoft.com/fwlink/?LinkId=518238)します。  
  
-   **ASP.NET の更新プログラム**  
  
    -   **非同期応答のフラッシュのタスクベースの API**  
  
         ASP.NET では、非同期応答をフラッシュする簡単なタスクベースの API ようになりましたが用意されています<xref:System.Web.HttpResponse.FlushAsync%2A?displayProperty=fullName>、言語を使用して非同期的にフラッシュするへの応答を許可する`async/await`をサポートします。  
  
    -   `Model binding supports task-returning methods`  
  
         [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、Web フォーム ページやユーザー コントロールでの CRUD ベースのデータ操作に対して拡張可能なコード中心のアプローチを可能にするモデル バインド機能が ASP.NET に追加されました。 モデル バインド システムになりました<xref:System.Threading.Tasks.Task>-モデル バインディングのメソッドを取得します。 この機能により、Web フォーム開発者は Entity Framework などの ORM の新しいバージョンを使用するときに、データ バインド システムのように簡単に非同期のスケーラビリティ上のメリットを得ることができます。  
  
         非同期モデル バインドは、`aspnet:EnableAsyncModelBinding` 構成設定によって制御されます。  
  
        ```  
  
        <appSettings>  
           <add key=" aspnet:EnableAsyncModelBinding" value="true|false" />  
        </appSettings>  
  
        ```  
  
         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] を対象とするアプリでは、既定で `true` になります。 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] で実行され、.NET Framework の以前のバージョンを対象とするアプリでは、既定で `false` になります。 有効にするには、この構成設定を `true` に設定します。  
  
    -   **Http/2 のサポート (Windows 10)**  
  
         [Http/2](http://www.wikipedia.org/wiki/HTTP/2)程度接続使用率の向上 (より少ない、ラウンドト リップ クライアントとサーバー間) を提供する HTTP プロトコルの新しいバージョンの下の待機時間 web ページを読み込むときのユーザーに結果ができます。  このプロトコルは単一のエクスペリエンスの一部として要求さる複数の成果物のために最適化されているので、HTTP/2 が最も役立つのは (サービスではなく) web ページです。 .NET Framework 4.6 では、HTTP/2 のサポートが ASP.NET に追加されました。 ネットワーク機能は複数のレイヤーで存在するので、HTTP/2 を有効にするために、Windows、IIS、および ASP.NET で新機能が必要とされていました。 ASP.NET で HTTP/2 を使用するには、Windows 10 を実行している必要があります。  
  
         Http/2 がサポートされてに既定で windows 10 ユニバーサル Windows プラットフォーム (UWP) アプリを使用する、 <xref:System.Net.Http.HttpClient?displayProperty=fullName> API です。  
  
         使用する方法を提供するために、 [PUSH_PROMISE](http://http2.github.io/http2-spec/#PUSH_PROMISE)機能の ASP.NET アプリケーションでは、2 つのオーバー ロードを持つ新しいメソッドで<xref:System.Web.HttpResponse.PushPromise%28System.String%29>と<xref:System.Web.HttpResponse.PushPromise%28System.String%2CSystem.String%2CSystem.Collections.Specialized.NameValueCollection%29>に追加されて、 <xref:System.Web.HttpResponse>クラスです。  
  
        > [!NOTE]
        >  ASP.NET 5 では HTTP/2 がサポートされましたが、PUSH PROMISE 機能のサポートはまだ追加されていません。  
  
         ブラウザーと web サーバー (Windows 上の IIS) がすべての処理を実行します。 ユーザーの側で複雑な操作を実行する必要はありません。  
  
         ほとんどの[主なブラウザーは http/2 をサポート](http://www.wikipedia.org/wiki/HTTP/2)できると考え、ユーザーは http/2 のサポートの場合は、サーバーでサポートされているので、します。  
  
    -   **トークン バインディング プロトコルのサポート**  
  
         Microsoft と Google と呼ばれる、認証のための新しい手法に取り組んできました、[トークン バインディング プロトコル](https://github.com/TokenBinding/Internet-Drafts)します。 (ブラウザー キャッシュ) 内の認証トークンの盗難にあったし、パスワードやその他の特別な情報を必要とせず、それ以外の場合にセキュリティで保護されたリソース (銀行口座など) にアクセスする犯罪者が使用されることはできます。 新しいプロトコルは、この問題を軽減することを目指しています。  
  
         トークン バインディング プロトコルは、Windows 10 でブラウザーの機能として実装されます。 ASP.NET アプリは、認証トークンの正当性が検証されるように、このプロトコルに参加します。 クライアントとサーバーの実装は、プロトコルによって指定されるエンド ツー エンドの保護を確立します。  
  
    -   **ランダム化された文字列のハッシュ アルゴリズム**  
  
         導入された .NET Framework 4.5、[ランダム化された文字列のハッシュ アルゴリズム](https://msdn.microsoft.com/library/jj152924.aspx)します。 しかし、ASP.NET の一部の機能は安定したハッシュ コードに依存していたため、この機能は ASP.NET ではサポートされませんでした。 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] では、ランダムな文字列のハッシュ アルゴリズムがサポートされるようになりました。 この機能を有効にするには、`aspnet:UseRandomizedStringHashAlgorithm` 構成設定を使用します。  
  
        ```  
  
        <appSettings>  
           <add key="aspnet:UseRandomizedStringHashAlgorithm" value="true|false" />  
        </appSettings>  
  
        ```  
  
-   **ADO.NET**  
  
     ADO .NET では、SQL Server 2016 Community Technology Preview 2 (CTP2) で使用できる Always Encrypted 機能がサポートされました。 SQL Server は、Always Encrypted 機能を使用して、暗号化されたデータに対して操作を実行できます。特に、サーバー上ではなく、ユーザーが信頼している環境内にアプリケーションと共に暗号化キーを保存できるようになりました。 Always Encrypted でユーザー データが保護されるので、DBA はプレーン テキスト データにアクセスできません。 データの暗号化と復号化は、ドライバー レベルで透過的に行われるので、既存のアプリケーションに対する変更が最小限に抑えられます。 詳細については、「 [(データベース エンジン) を常に暗号化](https://msdn.microsoft.com/library/mt163865\(v=sql.130\).aspx)と[(クライアント開発) 常に暗号化](https://msdn.microsoft.com/library/mt147923\(v=sql.130\).aspx)します。  
  
-   **マネージ コードの&64; ビット JIT コンパイラ**  
  
     .NET Framework 4.6 の特徴の 1 つとして、新しいバージョンの 64 ビット JIT コンパイラ (RyuJIT というコードネームで呼ばれていたもの) があります。 この新しい 64 ビット コンパイラは、これまでの 64 ビット JIT コンパイラよりもパフォーマンスが大幅に向上しています。 新しい 64 ビット コンパイラは、.NET Framework 4.6 上で実行される 64 ビット プロセスで有効になります。 64 ビットまたは AnyCPU としてコンパイルされ、64 ビット オペレーティング システム上で実行されるアプリは、64 ビットで動作します。 新しいコンパイラへの移行をできる限り透過的に行うように注意を払いましたが、動作の変更が発生する可能性があります。 新しい JIT コンパイラの使用中に発生した問題については、直接お聞かせいただければと思います。 お問い合わせください[Microsoft Connect](http://connect.microsoft.com/)新しい 64 ビット JIT コンパイラに関連する可能性のある問題が発生した場合。  
  
     新しい 64 ビット JIT コンパイラが SIMD が有効な型と組み合わせると、ハードウェア SIMD アクセラレータ機能にはも含まれています、 <xref:System.Numerics>名前空間は、良好なパフォーマンス向上をもたらすことができます。  
  
-   **アセンブリ ローダーの機能強化**  
  
     アセンブリ ローダーで、対応する NGEN イメージの読み込み後に IL アセンブリをアンロードすることにより、メモリがより効率的に使用されるようになりました。 この変更は、仮想メモリが減少するため、特に大規模な 32 ビット アプリ (Visual Studio など) で有益であり、物理メモリの節約にもなります。  
  
-   **基本クラス ライブラリの変更点**  
  
     主なシナリオを利用できるようにするため、多くの新しい API が [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] に関連して追加されました。 変更点と追加点を以下に示します。  
  
    -   **IReadOnlyCollection<> \</> \>の実装**  
  
         追加のコレクションを実装<xref:System.Collections.Generic.IReadOnlyCollection%601>など<xref:System.Collections.Generic.Queue%601>と<xref:System.Collections.Generic.Stack%601>します。  
  
    -   **CultureInfo.CurrentCulture と CultureInfo.CurrentUICulture**  
  
         <xref:System.Globalization.CultureInfo.CurrentCulture%2A?displayProperty=fullName>と<xref:System.Globalization.CultureInfo.CurrentUICulture%2A?displayProperty=fullName>プロパティが読み取り/書き込みではなく読み取り専用になりました。 新しいを割り当てる場合<xref:System.Globalization.CultureInfo>オブジェクトで定義されている現在のスレッド カルチャのこれらのプロパティを`Thread.CurrentThread.CurrentCulture`プロパティと現在の UI スレッド カルチャによって定義された、`Thread.CurrentThread.CurrentUICulture`プロパティも変更します。  
  
    -   **ガベージ コレクション (GC) の機能強化**  
  
         <xref:System.GC>クラスが含まれています<xref:System.GC.TryStartNoGCRegion%2A>と<xref:System.GC.EndNoGCRegion%2A>メソッドがクリティカル パスの実行中にガベージ コレクションを不許可にできます。  
  
         新しいオーバー ロード、 <xref:System.GC.Collect%28System.Int32%2CSystem.GCCollectionMode%2CSystem.Boolean%2CSystem.Boolean%29?displayProperty=fullName>メソッドを制御できる小さなオブジェクト ヒープと大きなオブジェクト ヒープの両方に関して、スイープし圧縮、スイープのみを行うかどうか。  
  
    -   **SIMD が有効な型**  
  
         <xref:System.Numerics>名前空間は、さまざまな種類の SIMD が有効ななど<xref:System.Numerics.Matrix3x2>、 <xref:System.Numerics.Matrix4x4>、<xref:System.Numerics.Plane>、<xref:System.Numerics.Quaternion>、 <xref:System.Numerics.Vector2>、 <xref:System.Numerics.Vector3>、および<xref:System.Numerics.Vector4>します。  
  
         新しい 64 ビット JIT コンパイラにはハードウェア SIMD アクセラレータ機能も含まれているため、新しい 64 ビット JIT コンパイラで SIMD 対応の型を使用すると、パフォーマンスが大幅に向上します。  
  
    -   **暗号の更新**  
  
         <xref:System.Security.Cryptography?displayProperty=fullName> API がサポートするために更新される、 [Windows CNG 暗号化 Api](https://msdn.microsoft.com/library/windows/desktop/aa376214.aspx)します。 .NET Framework の以前のバージョンを完全に利用して、[以前のバージョンの Windows 暗号化 Api](https://msdn.microsoft.com/library/windows/desktop/aa380255.aspx)を基準として、 <xref:System.Security.Cryptography?displayProperty=fullName>実装します。 サポートしているので、CNG API をサポートするためにリクエスト[近代暗号アルゴリズム](https://msdn.microsoft.com/library/windows/desktop/bb204775.aspx#suite_b_support)、特定のカテゴリのアプリケーションにとって重要であります。  
  
         .NET Framework 4.6 には、Windows CNG 暗号化 API をサポートするために、次の新しい機能強化が含まれています。  
  
        -   可能な場合に CAPI ベースの実装ではなく CNG ベースの実装を返す X509 証明書用の一連の拡張メソッド `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPublicKey(System.Security.Cryptography.X509Certificates.X509Certificate2)` および `System.Security.Cryptography.X509Certificates.RSACertificateExtensions.GetRSAPrivateKey(System.Security.Cryptography.X509Certificates.X509Certificate2)`  (一部のスマート カードなどでは現在も CAPI が必要であり、API がフォールバックを処理します)。  
  
        -   <xref:System.Security.Cryptography.RSACng?displayProperty=fullName>クラスで、RSA アルゴリズムの CNG の実装を提供します。  
  
        -   一般的な操作でキャストを不要にする RSA API の機能強化。 たとえばを使用してデータの暗号化、 <xref:System.Security.Cryptography.X509Certificates.X509Certificate2>オブジェクトには、.NET Framework の以前のバージョンでは、次のようなコードが必要です。  
  
             [!code-csharp[WhatsNew.Casting#1](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#1)]
             [!code-vb[WhatsNew.Casting#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#1)]  
  
             .NET Framework 4.6 で新しい暗号化を使用するコードは、次のように書き換えてキャストを回避することができます。  
  
             [!code-csharp[WhatsNew.Casting#2](../../../samples/snippets/csharp/VS_Snippets_CLR/whatsnew.casting/cs/program.cs#2)]
             [!code-vb[WhatsNew.Casting#2](../../../samples/snippets/visualbasic/VS_Snippets_CLR/whatsnew.casting/vb/module1.vb#2)]  
  
    -   **日付と時刻の変換と Unix 時間の間のサポート**  
  
         次のメソッドに追加された、 <xref:System.DateTimeOffset>と Unix 時間の間に、日付と時刻の値を変換をサポートする構造体。  
  
        -   <xref:System.DateTimeOffset.FromUnixTimeSeconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.FromUnixTimeMilliseconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.ToUnixTimeSeconds%2A?displayProperty=fullName>  
  
        -   <xref:System.DateTimeOffset.ToUnixTimeMilliseconds%2A?displayProperty=fullName>  
  
    -   **互換性スイッチ**  
  
         新しい<xref:System.AppContext>クラス ライブラリの作成者のユーザーの新機能の統一されたオプトアウト メカニズムを提供するようにする新しい互換性機能を追加します。 これは、オプトアウト要求を伝達するために、コンポーネント間に疎結合のコントラクトを確立します。 通常、この機能は既存の機能が変更されるときに重要となります。 それに対して、新しい機能には暗黙のオプトインが既に存在しています。  
  
         <xref:System.AppContext>ライブラリは、定義、およびそれらに依存するコードの中に、公開の互換性スイッチがライブラリの動作に影響するこれらのスイッチを設定できます。 ライブラリは、既定では新しい機能を提供し、スイッチが設定されている場合のみそれを変更する (つまり以前の機能を提供する) ことができます。  
  
         アプリケーション (またはライブラリ) は、スイッチの値を宣言できます (これは常に、<xref:System.Boolean>値)、依存するライブラリを定義します。 スイッチは常に暗黙的に `false` です。 スイッチを `true` に設定すると、それが有効になります。 スイッチを明示的に `false` に設定すると、新しい動作が提供されます。  
  
        ```csharp  
        AppContext.SetSwitch("Switch.AmazingLib.ThrowOnException", true);  
        ```  
  
         ライブラリは、コンシューマーがスイッチの値を宣言したことを確認してから、それを適切に実行する必要があります。  
  
        ```  
  
        if (!AppContext.TryGetSwitch("Switch.AmazingLib.ThrowOnException", out shouldThrow))   
        {  
           // This is the case where the switch value was not set by the application.   
           // The library can choose to get the value of shouldThrow by other means.   
           // If no overrides nor default values are specified, the value should be 'false'.   
           // A false value implies the latest behavior.  
        }  
  
           // The library can use the value of shouldThrow to throw exceptions or not.  
           if (shouldThrow)   
           {  
              // old code  
           }  
           else {  
              // new code  
           }  
        }  
  
        ```  
  
         スイッチは、ライブラリによって公開される正式なコントラクトであるため、一貫性のある形式を使用することをお勧めします。 2 つの明確な形式を次に示します。  
  
        -   *Switch*.*名前空間*.*switchname*  
  
        -   *Switch*.*library*.*switchname*  
  
    -   **タスク ベースの非同期パターン (TAP) への変更**  
  
         対象とするアプリに対して、 [!INCLUDE[net_v46](../../../includes/net-v46-md.md)]、<xref:System.Threading.Tasks.Task>と<xref:System.Threading.Tasks.Task%601>オブジェクトのカルチャと、呼び出し元スレッドの UI カルチャを継承します。 以前のバージョンの .NET Framework をターゲットするとアプリまたは特定のバージョンの .NET Framework をターゲットとしないアプリの動作には影響を及ぼしません。 詳細については、の「カルチャとタスク ベースの非同期操作」セクションを参照して、 <xref:System.Globalization.CultureInfo>クラスに関するトピック。  
  
         <xref:System.Threading.AsyncLocal%601?displayProperty=fullName>クラスを使用するなど、特定の非同期制御フローに対してローカルなアンビエント データを表すため、`async`メソッドです。 これは、スレッド間でデータを保持するために使用できます。 アンビエント データではいずれかが変更されるためされるたびに通知されるコールバック メソッドを定義することも、 <xref:System.Threading.AsyncLocal%601.Value%2A?displayProperty=fullName>プロパティが明示的に変更された、またはスレッドにコンテキストの遷移が発生したためです。  
  
         次の&3; つの便利なメソッド<xref:System.Threading.Tasks.Task.CompletedTask%2A?displayProperty=fullName>、 <xref:System.Threading.Tasks.Task.FromCanceled%2A?displayProperty=fullName>、および<xref:System.Threading.Tasks.Task.FromException%2A?displayProperty=fullName>、タスクベースの非同期パターン (TAP) を特定の状態で完了したタスクを返すに追加されました。  
  
         <xref:System.IO.Pipes.NamedPipeClientStream>クラスは、今すぐとその新しいの非同期通信をサポートしています<xref:System.IO.Pipes.NamedPipeClientStream.ConnectAsync%2A>します。 メソッドをオーバーライドします。  
  
    -   **EventSource は、イベント ログへの書き込みをサポートします。**  
  
         今すぐ使用できる、 <xref:System.Diagnostics.Tracing.EventSource>をコンピューターに作成、既存の ETW セッションにさらに、管理や運用ログにクラスがメッセージをイベント ログです。 以前は、この機能のために Microsoft.Diagnostics.Tracing.EventSource NuGet パッケージを使用する必要がありました。 この機能は .NET Framework 4.6 に組み込まれました。  
  
         NuGet パッケージと .NET Framework 4.6 は、どちらも次の機能によって更新されています。  
  
        -   **動的イベント**  
  
             イベント メソッドを作成せずに、実行時にイベントを定義できます。  
  
        -   **リッチ ペイロード**  
  
             特別な属性が指定されたクラスや配列に加えて、プリミティブ型もペイロードとして渡すことができます。  
  
        -   **動作状況の追跡**  
  
             Start イベントと Stop イベントの間のイベントに、現在アクティブなすべてのアクティビティを表す ID が付けられます。  
  
         これらをサポートする機能が、オーバー ロードされた<xref:System.Diagnostics.Tracing.EventSource.Write%2A>にメソッドが追加されて、 <xref:System.Diagnostics.Tracing.EventSource>クラスです。  
  
-   **Windows Presentation Foundation (WPF)**  
  
    -   **HDPI 機能強化**  
  
         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] では、WPF での HDPI サポートが強化されました。 境界があるコントロールでのクリッピングの発生を減らすため、レイアウトの丸め処理が変更されました。 既定では、この機能が有効になっている場合にのみ、 <xref:System.Runtime.Versioning.TargetFrameworkAttribute> .NET 4.6 に設定されています。  以前のバージョンの framework を対象と、上で実行されているアプリケーション、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]次の行を追加することで、新しい動作をオプトインできます、 [ <> \> ](../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md) app.config ファイルのセクション。  
  
        ```  
  
        <AppContextSwitchOverrides  
        value="Switch.MS.Internal.DoNotApplyLayoutRoundingToMarginsAndBorderThickness=false"  
        />  
  
        ```  
  
         異なる DPI 設定を持つ (マルチ DPI セットアップの) 複数のモニターにまたがる WPF ウィンドウは、ブラック アウト領域なしで完全にレンダリングされるようになりました。 この動作の選択を解除するには、app.config ファイルの `<appSettings>` セクションに次の行を追加して、この新しい動作を無効にします。  
  
        ```  
  
        <add key="EnableMultiMonitorDisplayClipping" value="true"/>  
  
        ```  
  
         DPI 設定に基づいた正しいカーソルを自動的に読み込むに追加されたサポート<xref:System.Windows.Input.Cursor?displayProperty=fullName>します。  
  
    -   **タッチをお勧め**  
  
         お客様からの報告[接続](https://connect.microsoft.com/VisualStudio/feedback/details/903760/)で予期しない動作が処理された生成をタッチする、[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]です。 Windows 8.1 以降では、Windows ストア アプリケーションと WPF アプリケーションのダブルタップのしきい値が同じになりました。  
  
    -   **透過的な子ウィンドウのサポート**  
  
         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] の WPF では、Windows 8.1 以降の透過的な子ウィンドウがサポートされます。 これにより、最上位レベルのウィンドウ内に四角形でない透過的な子ウィンドウを作成できます。 この機能を有効に設定することができます、 <xref:System.Windows.Interop.HwndSourceParameters.UsesPerPixelTransparency%2A?displayProperty=fullName>プロパティを`true`します。  
  
-   **Windows Communication Foundation (WCF)**  
  
    -   **SSL のサポート**  
  
         WCF で、NetTcp をトランスポート セキュリティおよびクライアント認証と共に使用する場合に、SSL のバージョンとして SSL 3.0 および TLS 1.0 に加えて TLS 1.1 および TLS 1.2 がサポートされるようになりました。 使用するプロトコルを選択することも、安全性の低い古いプロトコルを無効化することもできるようになりました。 これを行う設定するか、 <xref:System.ServiceModel.TcpTransportSecurity.SslProtocols%2A>プロパティまたは構成ファイルに、次を追加します。  
  
        ```  
        <netTcpBinding>  
           <binding>  
              <security mode= "None|Transport|Message|TransportWithMessageCredential" >  
                 <transport clientCredentialType="None|Windows|Certificate"  
                            protectionLevel="None|Sign|EncryptAndSign"  
                            sslProtocols="Ssl3|Tls1|Tls11|Tls12">  
                    </transport>  
              </security>  
           </binding>  
        </netTcpBinding>  
  
        ```  
  
    -   **別の HTTP 接続を使用してメッセージを送信します。**  
  
         WCF で、ユーザーが別の基になる HTTP 接続を使用して特定のメッセージを送信できるようになりました。 これには、2 つの方法があります。  
  
        -   **接続グループ名のプレフィックスを使用します。**  
  
             ユーザーは、WCF で接続グループ名のプレフィックスとして使用される文字列を指定できます。 異なるプレフィックスを持つ&2; つのメッセージは、別の基になる HTTP 接続を使用して送信されます。 メッセージのキー/値ペアを追加することで、プレフィックスを設定する<xref:System.ServiceModel.Channels.Message.Properties%2A?displayProperty=fullName>プロパティです。 キーは、"HttpTransportConnectionGroupNamePrefix"です。値は、目的のプレフィックスです。  
  
        -   **異なる種類のチャネル ファクトリを使用します。**  
  
             ユーザーは、異なるチャネル ファクトリによって作成されたチャネルを使用して送信されるメッセージで別の基になる HTTP 接続を使用する機能を有効にすることもできます。 この機能を有効にするには、ユーザーが次の `appSetting` を `true` に設定する必要があります。  
  
            ```  
  
            <appSettings>  
               <add key="wcf:httpTransportBinding:useUniqueConnectionPoolPerFactory" value="true" />  
            </appSettings>  
  
            ```  
  
-   **Windows Workflow Foundation (WWF)**  
  
     順序不定の操作要求がタイムアウトする前に未処理の「非プロトコル」ブックマークが存在する場合に、ワークフロー サービスが要求を保持する秒数を指定できるようになりました。 「非プロトコル」ブックマークとは、未処理の Receive アクティビティに関連付けられていないブックマークです。 一部のアクティビティはその実装内で非プロトコル ブックマークを作成するため、必ずしも非プロトコル ブックマークの存在が明らかにわかるとは限りません。 例として State や Pick などがあります。 ステート マシンを使用して実装されたワークフロー サービスや、Pick アクティビティを含むワークフロー サービスがある場合は、非プロトコル ブックマークが存在する可能性が高くなります。 この間隔を指定するには、app.config ファイルの `appSettings` セクションに次のような行を追加します。  
  
    ```  
    <add key="microsoft:WorkflowServices:FilterResumeTimeoutInSeconds" value="60"/>  
    ```  
  
     既定値は 60 秒です。 `value` を 0 に設定すると、順序不定の要求はただちに拒否され、次のようなテキストを含むエラーが返されます。  
  
    ```Output  
    Operation 'Request3|{http://tempuri.org/}IService' on service instance with identifier '2b0667b6-09c8-4093-9d02-f6c67d534292' cannot be performed at this time. Please ensure that the operations are performed in the correct order and that the binding in use provides ordered delivery guarantees.   
    ```  
  
     これは、順序不定の操作メッセージを受信し、非プロトコル ブックマークが存在しない場合に受信するメッセージと同じです。  
  
     `FilterResumeTimeoutInSeconds` 要素の値がゼロ以外で、非プロトコル ブックマークが存在し、タイムアウト間隔が終了した場合、その操作は失敗し、タイムアウト メッセージが発生します。  
  
-   **トランザクション**  
  
     派生した例外を発生させたトランザクションの現在の分散トランザクションの識別子を含めることができます<xref:System.Transactions.TransactionException>がスローされます。 これを行うには、次のキーを app.config ファイルの `appSettings` セクションに追加します。  
  
    ```  
    <add key="Transactions:IncludeDistributedTransactionIdInExceptionMessage" value="true"/>   
    ```  
  
     既定値は `false` です。  
  
-   **ネットワーク接続**  
  
    -   **ソケットの再利用**  
  
         Windows 10 には、送信 TCP 接続のローカル ポートを再利用してコンピューターのリソースを効率的に使用する新しいスケーラビリティの高いネットワーク アルゴリズムが含まれています。 .NET Framework 4.6 では、この新しいアルゴリズムがサポートされ、.NET アプリで新しい動作を利用できます。 以前のバージョンの Windows では、人工的な同時接続の制限 (通常は動的なポート範囲の既定のサイズである 16,384) があったため、負荷がかかったときにポートが使い尽くされ、サービスのスケーラビリティが制限されることがありました。  
  
         [!INCLUDE[net_v46](../../../includes/net-v46-md.md)] では、ポートの再利用を有効にする次の 2 つの新しい API が追加され、同時接続に対する 64K の制限が実質的になくなりました。  
  
        -   <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>列挙値。  
  
        -   <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName>プロパティです。  
  
         既定では、 <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName>プロパティは、`false`しない限り、`HWRPortReuseOnSocketBind`の値、`HKLM\SOFTWARE\Microsoft\.NETFramework\v4.0.30319`レジストリ キーが 0x1 に設定します。 HTTP 接続でのローカル ポートの再利用を有効にするには設定、 <xref:System.Net.ServicePointManager.ReusePort%2A?displayProperty=fullName>プロパティを`true`します。 これにより、すべての発信 TCP ソケット接続から<xref:System.Net.Http.HttpClient>と<xref:System.Net.HttpWebRequest>新しい Windows 10 ソケット オプションを使用する[SO_REUSE_UNICASTPORT](https://msdn.microsoft.com/library/windows/desktop/ms740532.aspx)、ローカル ポートを再利用できるようにします。  
  
         ソケット専用のアプリケーションを作成する開発者を指定できます、 <xref:System.Net.Sockets.SocketOptionName?displayProperty=fullName>オプションなどのメソッドを呼び出すことと<xref:System.Net.Sockets.Socket.SetSocketOption%2A?displayProperty=fullName>アウト バウンド ソケットのバインド中にローカル ポートを再利用できるようにします。  
  
    -   **国際ドメイン名と PunyCode のサポート**  
  
         新しいプロパティ<xref:System.Uri.IdnHost%2A>に追加されて、 <xref:System.Uri>サポートを強化する国際ドメイン名と PunyCode クラスです。  
  
-   **Windows フォーム コントロールにおけるサイズ変更します。**  
  
     この機能が拡張されました[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]に含める、 <xref:System.Windows.Forms.DomainUpDown>、 <xref:System.Windows.Forms.NumericUpDown>、 <xref:System.Windows.Forms.DataGridViewComboBoxColumn>、 <xref:System.Windows.Forms.DataGridViewColumn>と<xref:System.Windows.Forms.ToolStripSplitButton>型と指定された四角形、<xref:System.Drawing.Design.PaintValueEventArgs.Bounds%2A>描画するときに使用されるプロパティ、 <xref:System.Drawing.Design.UITypeEditor>します。  
  
     これはオプトイン機能です。 この機能を有効にするには、アプリケーション構成 (app.config) ファイルで `EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。  
  
    ```  
  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
  
    ```  
  
-   **コード ページ エンコーディングのサポート**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)] は、本来 Unicode エンコードをサポートし、既定ではコード ページ エンコーディングに関するサポートは限定的です。 サポートされていないが、.NET Framework で使用できるコード ページ エンコーディングのサポートを追加する[!INCLUDE[net_core](../../../includes/net-core-md.md)]使用してコード ページ エンコーディングを登録することによって、 <xref:System.Text.Encoding.RegisterProvider%2A?displayProperty=fullName>メソッドです。 詳細については、次を参照してください。 [System.Text.CodePagesEncodingProvider](https://msdn.microsoft.com/en-us/library/system.text.codepagesencodingprovider.aspx)します。  
  
-   **.NET ネイティブ**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)] をターゲットとし、c# または Visual Basic で作成されている Windows 10 用の Windows アプリは、IL ではなくネイティブ コードにアプリをコンパイルする新しい技術を活用できます。 これで、起動時間と実行時間がより速いアプリを生成できます。 詳細については、次を参照してください。 [.NET ネイティブによるアプリのコンパイル](../../../docs/framework/net-native/index.md)します。 .NET ネイティブ JIT コンパイルと NGEN による違い、およびどのようなことの概要については、コードの意味を参照してください[.NET ネイティブとコンパイル](../../../docs/framework/net-native/net-native-and-compilation.md)します。  
  
     アプリは、Visual Studio 2015 でコンパイルするときに、既定でネイティブ コードにコンパイルされます。 詳細については、次を参照してください。 [.NET ネイティブの概要](../../../docs/framework/net-native/getting-started-with-net-native.md)します。  
  
     .NET ネイティブ アプリのデバッグをサポートするため、アンマネージ デバッグ APIに対して数多くの新しいインターフェイスと列挙型が追加されました。 詳細については、次を参照してください。、[デバッグ (アンマネージ API リファレンス)](../../../ml/index.xml)トピックです。  
  
-   **オープン ソースの .NET Framework パッケージ**  
  
     [!INCLUDE[net_core](../../../includes/net-core-md.md)]変更できないコレクションなどのパッケージ[SIMD Api](http://go.microsoft.com/fwlink/?LinkID=518639)、については、ネットワークなどの Api と、 <xref:System.Net.Http>にオープン ソース パッケージとして利用できる名前空間が[GitHub](https://github.com/)します。 コードにアクセスするを参照してください。 [GitHub の NetFx](http://go.microsoft.com/fwlink/?LinkID=518634)します。 これらのパッケージに投稿する方法と詳細については、次を参照してください。 [.NET Core とオープン ソース](../../../docs/framework/get-started/net-core-and-open-source.md)、 [GitHub の .NET ホーム ページ](http://go.microsoft.com/fwlink/?LinkID=518635)します。  
  
 [ページのトップへ](#introduction)  
  
<a name="v452"></a>   
## <a name="whats-new-in-the-net-framework-452"></a>.NET Framework 4.5.2 の新機能  
  
-   **ASP.NET アプリ用の新しい Api です。** 新しい<xref:System.Web.HttpResponse.AddOnSendingHeaders%2A?displayProperty=fullName>と<xref:System.Web.HttpResponseBase.AddOnSendingHeaders%2A?displayProperty=fullName>メソッドを検査し、応答がクライアント アプリにフラッシュされる際に、応答ヘッダー、ステータス コードを変更することができます。 これらのメソッドの代わりに使用を検討、 <xref:System.Web.HttpApplication.PreSendRequestHeaders>と<xref:System.Web.HttpApplication.PreSendRequestContent>イベントより効率的で信頼性の高い。  
  
     <xref:System.Web.Hosting.HostingEnvironment.QueueBackgroundWorkItem%2A?displayProperty=fullName>メソッドを使用して、小さなバック グラウンド作業項目をスケジュールできます。 ASP.NET はこれらの項目を追跡し、すべてのバックグラウンド作業項目が完了するまで IIS が突然ワーカー プロセスを終了しないようにします。 このメソッドは、ASP.NET マネージ アプリ ドメインの外部で呼び出すことはできません。  
  
     新しい<xref:System.Web.HttpResponse.HeadersWritten?displayProperty=fullName>と<xref:System.Web.HttpResponseBase.HeadersWritten?displayProperty=fullName>プロパティは、応答ヘッダーが書き込まれたかどうかを示すブール値を返します。 これらのプロパティを確認するなどの Api を呼び出している<xref:System.Web.HttpResponse.StatusCode%2A?displayProperty=fullName> (例外をスロー ヘッダーが書き込まれた場合) は成功します。  
  
-   **Windows フォーム コントロールにおけるサイズ変更します。** この機能が拡張されました。 これにより、システム DPI 設定を使用して、次の追加コントロールのコンポーネント (例: コンボ ボックスのドロップダウン矢印) をサイズ変更できます。  
  
     <xref:System.Windows.Forms.ComboBox>   
     <xref:System.Windows.Forms.ToolStripComboBox>   
     <xref:System.Windows.Forms.ToolStripMenuItem>   
     <xref:System.Windows.Forms.Cursor>   
     <xref:System.Windows.Forms.DataGridView>   
     <xref:System.Windows.Forms.DataGridViewComboBoxColumn>  
  
     これはオプトイン機能です。 この機能を有効にするには、アプリケーション構成 (app.config) ファイルで `EnableWindowsFormsHighDpiAutoResizing` 要素を `true` に設定します。  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
-   **新しいワークフロー機能。** リソース マネージャーを使用している、 <xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A>メソッド (したがってを実装して、 <xref:System.Transactions.IPromotableSinglePhaseNotification>インターフェイス)、新しい使用<xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName>メソッドを次の要求。  
  
    -   トランザクションを Microsoft 分散トランザクション コーディネーター (MSDTC) トランザクションに昇格します。  
  
    -   置換<xref:System.Transactions.IPromotableSinglePhaseNotification>で、 <xref:System.Transactions.ISinglePhaseNotification>、単一フェーズ コミットをサポートする永続参加リストがあります。  
  
     これは同じアプリ ドメイン内で実行でき、MSDTC とやり取りして昇格を実行するためにアンマネージ コードを追加する必要はありません。 未処理の呼び出しがある場合にのみ、新しいメソッドを呼び出すことができる<xref:System.Transactions?displayProperty=fullName>に、 <xref:System.Transactions.IPromotableSinglePhaseNotification> `Promote`昇格可能参加リストによって実装されるメソッドです。  
  
-   **プロファイリングの機能強化** 次の新しいアンマネージ プロファイリング API により、さらに信頼性の高いプロファイリングを提供します。  
  
     [COR_PRF_ASSEMBLY_REFERENCE_INFO 構造体](../../../ocs/framework/unmanaged-api/profiling/cor-prf-assembly-reference-info-structure.md)   
     [COR_PRF_HIGH_MONITOR 列挙型](../../../ocs/framework/unmanaged-api/profiling/cor-prf-high-monitor-enumeration.md)   
     [GetAssemblyReferences メソッド](../Topic/ICorProfilerCallback6::GetAssemblyReferences%20Method.md)   
     [GetEventMask2 メソッド](../Topic/ICorProfilerInfo5::GetEventMask2%20Method.md)   
     [SetEventMask2 メソッド](../Topic/ICorProfilerInfo5::SetEventMask2%20Method.md)   
     [AddAssemblyReference メソッド](../Topic/ICorProfilerAssemblyReferenceProvider::AddAssemblyReference%20Method.md)  
  
     以前の `ICorProfiler` の実装は、依存アセンブリの遅延読み込みをサポートしていました。 新しいプロファイリング API では、プロファイラーにより挿入される依存アセンブリを、アプリの完全な初期化後に読み込むのではなく、すぐに読み込む必要があります。 この変更は、既存の `ICorProfiler` API のユーザーには影響しません。  
  
-   **デバッグの機能強化。** 次の新しいアンマネージド デバッグ API により、プロファイラーとの統合性が向上しました。 これにより、ダンプのデバッグ時にコンパイラ ReJIT 要求により作成されたローカル変数やコードだけでなく、プロファイラーにより挿入されたメタデータにアクセスできます。  
  
     [SetWriteableMetadataUpdateMode メソッド](../Topic/ICorDebugProcess7::SetWriteableMetadataUpdateMode%20Method.md)   
     [EnumerateLocalVariablesEx メソッド](../Topic/ICorDebugILFrame4::EnumerateLocalVariablesEx%20Method.md)   
     [GetLocalVariableEx メソッド](../Topic/ICorDebugILFrame4::GetLocalVariableEx%20Method.md)   
     [GetCodeEx メソッド](../Topic/ICorDebugILFrame4::GetCodeEx%20Method.md)   
     [GetActiveReJitRequestILCode メソッド](../Topic/ICorDebugFunction3::GetActiveReJitRequestILCode%20Method.md)   
     [GetInstrumentedILMap メソッド](../Topic/ICorDebugILCode2::GetInstrumentedILMap%20Method.md)  
  
-   **イベント トレーシングの変更です。** .NET Framework 4.5.2 では、より大きなサーフェイス領域において、アウトプロセスの Windows イベント トレーシング (ETW) に基づくアクティビティ トレーシングができるようになりました。 これにより、アドバンスト パワー マネージメント (APM) ベンダーは、スレッドを越えた個々の要求とアクティビティのコストを正確に追跡する軽量ツールを提供できます。  これらのイベントは、ETW コントローラーで有効にされた場合にのみ発生します。したがって、変更は以前に記述された ETW コードや ETW が無効な状態で実行されるコードには影響しません。  
  
-   **トランザクションを昇格して、永続参加リストに変換します。**  
  
     <xref:System.Transactions.Transaction.PromoteAndEnlistDurable%2A?displayProperty=fullName>は新しい API に追加、.NET Framework 4.5.2 と 4.6。  
  
    ```  
  
    [System.Security.Permissions.PermissionSetAttribute(System.Security.Permissions.SecurityAction.LinkDemand, Name = "FullTrust")]  
    public Enlistment PromoteAndEnlistDurable(Guid resourceManagerIdentifier,  
                                              IPromotableSinglePhaseNotification promotableNotification,  
                                              ISinglePhaseNotification enlistmentNotification,  
                                              EnlistmentOptions enlistmentOptions)  
  
    ```  
  
     によって既に作成済みの登録リストにより、メソッドを使用する可能性があります<xref:System.Transactions.Transaction.EnlistPromotableSinglePhase%2A?displayProperty=fullName>に応えて、 <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName>メソッドです。 これは、`System.Transactions` に対して、トランザクションを MSDTC トランザクションに昇格させ、昇格可能参加リストを永続参加リストに「変換」するように要求します。 このメソッドは正常に完了した後、 <xref:System.Transactions.IPromotableSinglePhaseNotification>インターフェイスはによって参照されなくなった`System.Transactions`、将来通知が表示されているに到着して<xref:System.Transactions.ISinglePhaseNotification>インターフェイスです。 問題の参加リストは、永続参加リストとして機能し、トランザクションのログ記録と復旧をサポートする必要があります。 参照してください<xref:System.Transactions.Transaction.EnlistDurable%2A?displayProperty=fullName>詳細です。 さらに、参加がサポートする必要があります<xref:System.Transactions.ISinglePhaseNotification>します。  このメソッドは*のみ*処理中に呼び出される、 <xref:System.Transactions.ITransactionPromoter.Promote%2A?displayProperty=fullName>呼び出します。 この場合、それがない場合、 <xref:System.Transactions.TransactionException>例外がスローされます。  
  
 [ページのトップへ](#introduction)  
  
<a name="v451"></a>   
## <a name="whats-new-in-the-net-framework-451"></a>.NET Framework 4.5.1 の新機能  
 **2014 年 4 月の更新**:  
  
-   [Visual Studio 2013 Update 2](http://go.microsoft.com/fwlink/p/?LinkId=393658)をこれらのシナリオをサポートするポータブル クラス ライブラリ テンプレートの更新プログラムが含まれています。  
  
    -   Windows 8.1、Windows Phone 8.1、および Windows Phone Silverlight 8.1 を対象とするポータブル ライブラリで Windows ランタイム API を使用できます。  
  
    -   Windows 8.1 または Windows Phone 8.1 を対象とする場合、ポータブル ライブラリに XAML (Windows.UI.XAML 型) を含めることができます。 次の XAML テンプレートがサポートされています。空白のページ、リソース ディクショナリ、テンプレート コントロール、およびユーザー コントロール。  
  
    -   Windows 8.1 および Windows Phone 8.1 を対象とするストア アプリで使用するためにポータブル Windows ラインタイム コンポーネント (.winmd ファイル) を作成できます。  
  
    -   ポータブル クラス ライブラリのような Windows ストアまたは Windows Phone ストア クラス ライブラリを再ターゲットできます。  
  
     これらの変更の詳細については、次を参照してください。[ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)します。  
  
-   .NET Framework のコンテンツ セットには、Windows アプリをビルドして配置するためのプリコンパイル テクノロジである [!INCLUDE[net_native](../../../includes/net-native-md.md)] のドキュメントが含まれます。 [!INCLUDE[net_native](../../../includes/net-native-md.md)] は、中間言語 (IL) ではなくネイティブ コードへアプリを直接コンパイルすることにより、パフォーマンスを向上させます。 詳細については、「 [.NET ネイティブによるアプリのコンパイル](../../../docs/framework/net-native/index.md)します。  
  
-   [.NET Framework Reference Source](http://referencesource.microsoft.com/)新しい参照エクスペリエンスと強化された機能を提供します。 .NET Framework ソース コードをオンラインで表示できるようになりました[リファレンスをダウンロード](http://referencesource.microsoft.com/download.html)のデバッグ中にソース (パッチや更新プログラムを含む) をステップ実行してオフラインで表示します。 詳細については、ブログ記事を参照してください。 [.NET Reference Source の新しいデザイン](http://blogs.msdn.com/b/dotnet/archive/2014/02/24/a-new-look-for-net-reference-source.aspx)します。  
  
 .NET Framework 4.5.1 のコア機能の新機能と機能強化には次が含まれます。  
  
-   アセンブリの自動バインディング リダイレクト。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 以降では、アプリまたはそのコンポーネントが同じアセンブリの複数バージョンを参照している場合、[!INCLUDE[net_v451](../../../includes/net-v451-md.md)] を対象とするアプリのコンパイル時に、バインディング リダイレクトをアプリ構成ファイルに追加できます。 また、.NET Framework の以前のバージョンを対象とするプロジェクトで、この機能を有効にすることもできます。 詳細については、次を参照してください。[方法: 有効化と自動バインディング リダイレクトを無効にする](../../../docs/framework/configure-apps/how-to-enable-and-disable-automatic-binding-redirection.md)です。  
  
-   開発者がサーバーおよびクラウド アプリケーションのパフォーマンスを向上するために役立つ診断情報を収集する機能。 詳細については、次を参照してください。、 <xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityId%2A>と<xref:System.Diagnostics.Tracing.EventSource.WriteEventWithRelatedActivityIdCore%2A>内のメソッド、 <xref:System.Diagnostics.Tracing.EventSource>クラスです。  
  
-   ガベージ コレクション中に大きなオブジェクト ヒープ (LOH) を圧縮する機能。 詳細については、次を参照してください。、 <xref:System.Runtime.GCSettings.LargeObjectHeapCompactionMode%2A?displayProperty=fullName>プロパティです。  
  
-   その他のパフォーマンス向上 (ASP.NET アプリの中断、マルチコア JIT の改良、.NET Framework 更新後のアプリ起動時間の短縮など)。 詳細については、「、 [.NET Framework 4.5.1 のお知らせ](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)と[ASP.NET アプリの中断](http://blogs.msdn.com/b/dotnet/archive/2013/10/09/asp-net-app-suspend-responsive-shared-net-web-hosting.aspx)ブログの投稿です。  
  
 Windows フォームの機能強化には次が含まれます。  
  
-   Windows フォーム コントロールでのサイズ変更。 アプリのアプリケーション構成ファイル (app.config) 内のエントリで有効にすることにより、システム DIP 設定を使用してコントロールのコンポーネント (例: プロパティ グリッドに表示されるアイコン) をサイズ変更できます。 現在、この機能は次の Windows フォーム コントロールでサポートされています。  
  
     <xref:System.Windows.Forms.PropertyGrid>   
     <xref:System.Windows.Forms.TreeView>   
     一部の機能、 <xref:System.Windows.Forms.DataGridView> (を参照してください[4.5.2 の新機能](#v452)サポートされているその他のコントロールの)  
  
     この機能を有効にするには、新しい追加<>\>要素に構成ファイル (app.config) を設定し、`EnableWindowsFormsHighDpiAutoResizing`要素を`true`:  
  
    ```  
    <appSettings>  
       <add key="EnableWindowsFormsHighDpiAutoResizing" value="true" />  
    </appSettings>  
    ```  
  
 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] で .NET Framework アプリをデバッグするときの改善点は次のとおりです。  
  
-   Visual Studio デバッガーの戻り値。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] でマネージ アプリをデバッグする場合、メソッドの戻り値の型と値が [自動変数] ウィンドウに表示されます。 デスクトップ アプリ、Windows ストア アプリ、Windows Phone アプリについて、この情報を使用できます。 詳細については、次を参照してください。[メソッド呼び出しの戻り値を調べて](http://msdn.microsoft.com/library/e3245b37-8e2e-4200-ba84-133726e95f1f\(v=vs.120\).aspx)、MSDN ライブラリです。  
  
-   64 ビット アプリのエディット コンティニュ。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] では、デスクトップ、Windows ストア、Windows Phone 用の 64 ビット マネージ アプリについて、エディット コンティニュ機能がサポートされています。 32 ビットと 64 ビットの両方のアプリケーションの既存の制限を有効になります (の最後のセクションを参照してください、[サポートされているコード変更 (c#)](http://msdn.microsoft.com/library/ms164927\(v=vs.120\).aspx)記事)。  
  
-   非同期対応のデバッグ。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] で非同期アプリを簡単にデバッグするために、呼び出し履歴には、非同期プログラミングをサポートするためにコンパイラに用意されているインフラストラクチャ コード、および論理上の親フレーム内のチェーンが表示されません。これにより、論理的なプログラムの実行をよりわかりやすく行うことができます。 [タスク] ウィンドウが [並列タスク] ウィンドウに代わって使用され、特定のブレークポイントに関連するタスクが表示されます。また、現在アクティブなタスクやアプリでスケジュールされているタスクなども表示されます。 「非同期対応のデバッグ」セクションでは、この機能に関する記事を参照する、 [.NET Framework 4.5.1 のお知らせ](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)します。  
  
-   Windows ランタイム コンポーネント向けのより適切な例外処理のサポート。 [!INCLUDE[win81](../../../includes/win81-md.md)] では、言語の種類に関係なく、Windows ストア アプリから発生する例外には、例外を発生させたエラーに関する情報が保持されます。 「Windows ストア アプリの開発」セクションでは、この機能に関する記事を参照する、 [.NET Framework 4.5.1 のお知らせ](http://blogs.msdn.com/b/dotnet/archive/2013/06/26/announcing-the-net-framework-4-5-1-preview.aspx)します。  
  
 以降で[!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)]、使用することができます、[マネージ プロファイル ガイド付き最適化ツール (Mpgo.exe)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)を最適化する[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)]アプリとデスクトップ アプリ。  
  
 ASP.NET 4.5.1 の新機能は、次を参照してください。 [ASP.NET 4.5.1 および Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) ASP.NET サイトです。  
  
 [ページのトップへ](#introduction)  
  
<a name="core"></a>   
## <a name="whats-new-in-the-net-framework-45"></a>.NET Framework 4.5 の新機能  
  
### <a name="core-new-features-and-improvements"></a>コア機能の新機能と機能強化  
  
-   配置時に .NET Framework 4 アプリケーションを検出して終了することにより、システムの再起動を減らす機能。 参照してください[システム再起動の削減 .NET Framework 4.5 のインストール中に](../../../docs/framework/deployment/reducing-system-restarts.md)します。  
  
-   64 ビット プラットフォームでの 2 ギガバイト (GB) を超える配列のサポート。 この機能は、アプリケーション構成ファイルで有効にすることができます。 参照してください、 [ <> \>要素](../../../docs/framework/configure-apps/file-schema/runtime/gcallowverylargeobjects-element.md)、オブジェクトのサイズと配列サイズに関するその他の制限も記載します。  
  
-   サーバーのガベージ コレクションをバックグラウンドで行うことにより、パフォーマンスを改善します。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] でサーバーのガベージ コレクションを使用すると、バックグラウンド ガベージ コレクションが自動的に有効になります。 バック グラウンド サーバー ガベージ コレクションを参照してください、[ガベージ コレクションの基礎](../../../docs/standard/garbage-collection/fundamentals.md)トピックです。  
  
-   マルチコア プロセッサでオプションで使用できるバックグラウンドの Just-in-time (JIT) コンパイルを使用すると、アプリケーションのパフォーマンスが向上します。 参照してください<xref:System.Runtime.ProfileOptimization>します。  
  
-   正規表現エンジンがタイムアウトする前に、正規表現の解決を試みる時間に制限を設ける機能。 参照してください、 <xref:System.Text.RegularExpressions.Regex.MatchTimeout%2A?displayProperty=fullName>プロパティです。  
  
-   アプリケーション ドメインの既定のカルチャを定義する機能。 参照してください、 <xref:System.Globalization.CultureInfo>クラスです。  
  
-   Unicode UTF-16 エンコードのコンソール サポート。 参照してください、<xref:System.Console>クラスです。  
  
-   カルチャに従った文字列の順序のバージョン指定と比較データのサポート。 参照してください、 <xref:System.Globalization.SortVersion>クラスです。  
  
-   リソースを取得するときのパフォーマンスを改善します。 参照してください[のパッケージ化とリソースをデプロイする](../../../docs/framework/resources/packaging-and-deploying-resources-in-desktop-apps.md)です。  
  
-   Zip 圧縮の機能強化により、圧縮ファイルのサイズが小さくなりました。 参照してください、 <xref:System.IO.Compression?displayProperty=fullName>名前空間。  
  
-   既定のリフレクションの動作をオーバーライドするリフレクション コンテキストをカスタマイズする機能、 <xref:System.Reflection.Context.CustomReflectionContext>クラスです。  
  
-   国際化ドメイン名のアプリケーション (IDNA) の 2008年バージョンのサポートされる標準的な場合に、 <xref:System.Globalization.IdnMapping?displayProperty=fullName>クラスは、使用[!INCLUDE[win8](../../../includes/win8-md.md)]します。  
  
-   オペレーティング システムへの文字列比較の処理代行。.NET Framework を [!INCLUDE[win8](../../../includes/win8-md.md)] で使用したときに、Unicode 6.0 が実装されます。 他のプラットフォームで実行されている場合、.NET Framework には、Unicode 5.x. を実装する独自の文字列比較データが含まれています。 参照してください、<xref:System.String>クラスとの「解説」セクション、 <xref:System.Globalization.SortVersion>クラスです。  
  
-   アプリケーション ドメインごとに文字列のハッシュ コードを計算する機能。 See [<>\> Element](../../../docs/framework/configure-apps/file-schema/runtime/userandomizedstringhashalgorithm-element.md).  
  
-   タイプ リフレクションのサポートが分割<xref:System.Type>と<xref:System.Reflection.TypeInfo>クラスです。 参照してください[Windows ストア アプリ用 .NET Framework のリフレクション](../../../docs/framework/reflection-and-codedom/reflection-for-windows-store-apps.md)します。  
  
### <a name="managed-extensibility-framework-mef"></a>MEF (Managed Extensibility Framework)  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、MEF (Managed Extensibility Framework) に次の新機能が用意されています。  
  
-   ジェネリック型のサポート。  
  
-   属性ではなく命名規則に基づいてパーツを作成できるようにする、規則ベースのプログラミング モデル。  
  
-   複数のスコープ。  
  
-   [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリを作成するときに使用できる MEF のサブセット。 このサブセットは、[ダウンロード可能なパッケージ](http://go.microsoft.com/fwlink/?LinkId=256238)NuGet ギャラリーからです。 パッケージをインストールするには、Visual Studio でプロジェクトを開きます、選択**NuGet パッケージの管理**から、**プロジェクト**メニューのおよびオンラインで検索、`Microsoft.Composition`パッケージです。  
  
 詳細については、次を参照してください。 [Managed Extensibility Framework (MEF)](../../../docs/framework/mef/index.md)します。  
  
### <a name="asynchronous-file-operations"></a>非同期のファイル操作  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、新しい非同期機能が C# および Visual Basic 言語に追加されました。 これらの機能は、非同期操作を実行するためのタスク ベースのモデルを追加します。 この新しいモデルを使用するには、I/O クラスで非同期メソッドを使用します。 参照してください[非同期ファイル I/O](../../../docs/standard/io/非同期ファイル-i-o.md)します。  
  
<a name="tools"></a>   
### <a name="tools"></a>ツール  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、リソース ファイル ジェネレーター (Resgen.exe) を使用すると、.NET Framework アセンブリに埋め込まれた .resources ファイルから [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリ用の .resw ファイルを作成することができます。 詳細については、次を参照してください。 [Resgen.exe (リソース ファイル ジェネレーター)](../../../docs/framework/tools/resgen-exe-resource-file-generator.md)します。  
  
 マネージ プロファイル ガイド付き最適化ツール (Mpgo.exe) を使用すると、ネイティブ イメージ アセンブリを最適化することによって、アプリケーションの起動時間、メモリの使用率 (ワーキング セットのサイズ)、およびスループットを向上させることができます。 このコマンド ライン ツールは、ネイティブ イメージ アプリケーション アセンブリ用のプロファイル データを生成します。 参照してください[Mpgo.exe (マネージ プロファイル ガイド付き最適化ツール)](../../../docs/framework/tools/mpgo-exe-managed-profile-guided-optimization-tool.md)します。 [!INCLUDE[vs_dev12](../../../includes/vs-dev12-md.md)] 以降では、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] アプリおよびデスクトップ アプリを最適化するために、Mpgo.exe を使用できます。  
  
<a name="parallel"></a>   
### <a name="parallel-computing"></a>並列コンピューティング  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、並列計算用にいくつかの新機能と機能強化が提供されています。 パフォーマンスの向上、コントロールの強化、非同期プログラミングのサポートの改善、新しいデータフロー ライブラリ、並列デバッグとパフォーマンス分析のためのサポートの強化などが挙げられます。 エントリを参照してください[.NET 4.5 における並列処理の新](http://go.microsoft.com/fwlink/?LinkId=235061).NET ブログでの並列プログラミングにします。  
  
<a name="web"></a>   
### <a name="web"></a>Web  
 ASP.NET 4.5 および 4.5.1 では、Web フォーム モデルのバインディング、WebSocket のサポート、非同期ハンドラー、パフォーマンスの向上などの多くの機能が追加されています。 詳細については、次のリソースを参照してください。  
  
-   [ASP.NET 4.5 と Visual Studio 2012](../Topic/ASP.NET%20Core%20and%20Visual%20Studio%202015.md) MSDN ライブラリです。  
  
-   [ASP.NET 4.5.1 および Visual Studio 2013](http://go.microsoft.com/fwlink/?LinkID=309094) ASP.NET サイトです。  
  
<a name="networking"></a>   
### <a name="networking"></a>ネットワーク  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] は、HTTP アプリケーションに新しいプログラミング インターフェイスを提供します。 詳細については、表示、新しい<xref:System.Net.Http?displayProperty=fullName>と<xref:System.Net.Http.Headers?displayProperty=fullName>名前空間。  
  
 サポートも受け入れ、既存を使用して WebSocket 接続をやり取りするための新しいプログラミング インターフェイスに含まれて<xref:System.Net.HttpListener>および関連クラスです。 詳細については、表示、新しい<xref:System.Net.WebSockets>名前空間および<xref:System.Net.HttpListener>クラスです。  
  
 また [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] には、次のネットワークの機能強化が含まれています。  
  
-   RFC 準拠の URI サポート。 詳細については、次を参照してください。 <xref:System.Uri>および関連クラスです。  
  
-   国際化ドメイン名 (IDN: Internationalized Domain Name) による解析のサポート。 詳細については、次を参照してください。 <xref:System.Uri>および関連クラスです。  
  
-   電子メール アドレスの国際化 (EAI) のサポート。 詳細については、次を参照してください。、 <xref:System.Net.Mail>名前空間。  
  
-   強化された IPv6 サポート。 詳細については、次を参照してください。、 <xref:System.Net.NetworkInformation>名前空間。  
  
-   デュアル モードのソケットのサポート。 詳細については、次を参照してください。、<xref:System.Net.Sockets.Socket>と<xref:System.Net.Sockets.TcpListener>クラスです。  
  
<a name="client"></a>   
### <a name="windows-presentation-foundation-wpf"></a>Windows Presentation Foundation (WPF)  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、WPF (Windows Presentation Foundation) の次の領域の機能が変更および強化されています。  
  
-   新しい<xref:System.Windows.Controls.Ribbon.Ribbon>コントロールで、クイック アクセス ツールバー、アプリケーション メニューおよびタブをホストするリボン ユーザー インターフェイスを実装することができます。  
  
-   新しい<xref:System.ComponentModel.INotifyDataErrorInfo>インターフェイスで、同期および非同期のデータの検証をサポートします。  
  
-   新機能、 <xref:System.Windows.Controls.VirtualizingPanel>と<xref:System.Windows.Threading.Dispatcher>クラスです。  
  
-   グループ化された大量のデータを表示するときに、非 UI スレッドのコレクションにアクセスすることによってパフォーマンスを向上。  
  
-   静的プロパティへのバインド データをカスタム型データ バインディングを実装する、 <xref:System.Reflection.ICustomTypeProvider>インターフェイス、およびバインディング式からのデータ バインディング情報を取得します。  
  
-   値の変更に伴うデータの再配置 (ライブ形成)。  
  
-   項目コンテナーのデータ コンテキストを切断するかどうかをチェックする機能。  
  
-   プロパティの変更とデータ ソースの更新までの経過時間を設定する機能。  
  
-   弱いイベント パターン実装時のサポートの強化。 また、イベントでマークアップ拡張機能を使用することもできるようになりました。  
  
<a name="windows_communication_foundation"></a>   
### <a name="windows-communication-foundation-wcf"></a>Windows Communication Foundation (WCF)  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]では、Windows Communication Foundation (WCF) アプリケーションの記述と保守を簡単にするため、次の機能が追加されました。  
  
-   生成された構成ファイルの簡略化。  
  
-   コントラクト優先開発のサポート。  
  
-   ASP.NET 互換モードをより簡単に構成できる機能。  
  
-   既定のトランスポート プロパティ値に変更を加え、設定しなければならない可能性を低減しました。  
  
-   更新プログラムを<xref:System.Xml.XmlDictionaryReaderQuotas>クラス XML ディクショナリ リーダーのクォータを手動で構成する必要がある可能性を低減します。  
  
-   ビルド処理の一部として Visual Studio による WCF 構成ファイルを検証することで、アプリケーションを実行する前に構成エラーを検出できます。  
  
-   新しい非同期ストリーミングのサポート。  
  
-   Internet Information Services (IIS) での HTTPS 上のエンドポイントを公開しやすくする新しい HTTPS プロトコル マッピング。  
  
-   `?singleWSDL` をサービス URL に追加して&1; つの WSDL ドキュメントのメタデータを生成する機能。  
  
-   TCP トランスポートと同様のパフォーマンス特性を持つポート 80 と 443 で真の双方向通信を可能にする Websockets のサポート。  
  
-   コード内の構成サービスのサポート。  
  
-   XML エディターのツール ヒント。  
  
-   <xref:System.ServiceModel.ChannelFactory>キャッシュのサポート。  
  
-   バイナリ エンコーダーの圧縮サポート。  
  
-   開発者が「ファイア アンド フォーゲット (撃ち放し)」メッセージングを使用するサービスを作成できるようにする UDP トランスポートのサポート。 クライアントは、サービスにメッセージを送信しますが、サービスからの応答を期待しません。  
  
-   HTTP トランスポートとトランスポート セキュリティを使用したときに、単一の WCF エンドポイントで複数の認証モードをサポートする機能。  
  
-   国際化ドメイン名 (IDN: Internationalized Domain Name) を使用する WCF サービスのサポート。  
  
 詳細については、次を参照してください。 [Windows Communication Foundation の新](http://go.microsoft.com/fwlink/?LinkId=228173)します。  
  
<a name="windows_workflow_foundation"></a>   
### <a name="windows-workflow-foundation-wf"></a>Windows Workflow Foundation (WF)  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、次に示すようないくつかの新しい機能が Windows Workflow Foundation (WF) に追加されました。  
  
-   ステート マシン ワークフローは、最初に .NET Framework 4.0.1 の一部として導入された ([.NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092))。 この更新プログラムには、開発者がステート マシン ワークフローを作成できるようにする新しいクラスとアクティビティが複数含まれていました。 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] では、これらのクラスとアクティビティが、次を含むように更新されました。  
  
    -   状態でブレークポイントを設定する機能。  
  
    -   ワークフロー デザイナーで遷移をコピーして貼り付ける機能。  
  
    -   共有されるトリガーの遷移作成のデザイナー サポート。  
  
    -   含む、ステート マシン ワークフローを作成する: <xref:System.Activities.Statements.StateMachine>、<xref:System.Activities.Statements.State>、および<xref:System.Activities.Statements.Transition>します。  
  
-   次のようなワークフロー デザイナーの機能が強化されました。  
  
    -   強化された Visual Studio で、ワークフロー検索機能を含む**クイック検索**と**ファイル内の検索**します。  
  
    -   2 番目の子アクティビティがコンテナー アクティビティに追加されたときに、自動的にシーケンス アクティビティを作成し、両方のアクティビティをシーケンス アクティビティに含める機能。  
  
    -   スクロール バーを使用せずに変更されるワークフローの表示部分を変更できるようにするパン サポート。  
  
    -   新しい**ドキュメント アウトライン**ツリー スタイルのアウトライン ビューで、ワークフローのコンポーネントを表示するビューでコンポーネントを選択して、 **ドキュメント アウトライン**表示します。  
  
    -   アクティビティに注釈を追加できる機能。  
  
    -   ワークフロー デザイナーでアクティビティ デリゲートを定義および使用する機能。  
  
    -   ステート マシンのアクティビティと遷移、およびフローチャート ワークフローの自動接続と自動挿入。  
  
-   ワークフローのビュー状態情報を XAML ファイルの&1; つの要素に保管して、ビュー状態情報を簡単に見つけ、編集できるようにします。  
  
-   子アクティビティの永続化を防ぐ NoPersistScope コンテナー アクティビティ。  
  
-   C# 式のサポート:   
  
    -   Visual Basic を使用するワークフロー プロジェクトは、Visual Basic 式を使用し、C# ワークフロー プロジェクトは C# 式を使用します。  
  
    -   Visual Studio 2010 で作成され、Visual Basic 式が使用されている C# ワークフロー プロジェクトは、C# 式を使用する C# ワークフロー プロジェクトと互換性があります。  
  
-   バージョン管理機能の強化  
  
    -   新しい<xref:System.Activities.WorkflowIdentity>永続化されたワークフロー インスタンスとワークフロー定義間のマッピングを提供するクラス。  
  
    -   を含む同じホスト内の複数のワークフロー バージョンのサイド バイ サイド実行<xref:System.ServiceModel.Activities.WorkflowServiceHost>します。  
  
    -   動的更新プログラムで、永続化されたワークフロー インスタンスの定義を変更する機能。  
  
-   既存のサービス コントラクトに合わせて自動的にアクティビティを生成するサポートが提供されるコントラクト優先のワークフロー サービス開発。  
  
 詳細については、次を参照してください。 [Windows Workflow Foundation の新](http://go.microsoft.com/fwlink/?LinkId=228176)します。  
  
<a name="tailored"></a>   
### [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]  
 [!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] のアプリは、特定のフォーム ファクターに合わせて設計されており、Windows オペレーティング システムの機能を利用します。 C# または Visual Basic を使用して Windows 用の [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] アプリをビルドするために、[!INCLUDE[win8_appname_long](../../../includes/win8-appname-long-md.md)] または 4.5.1 のサブセットを使用できます。 このような操作が呼び出されます[!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]で説明されている場合は、[概要](http://go.microsoft.com/fwlink/?LinkId=228491)Windows デベロッパー センターでします。  
  
<a name="portable"></a>   
### <a name="portable-class-libraries"></a>ポータブル クラス ライブラリ  
 [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)] (および以降のバージョン) のポータブル クラス ライブラリ プロジェクトを使用すると、複数の .NET Framework プラットフォームで動作するマネージ アセンブリを作成してビルドできます。 ポータブル クラス ライブラリ プロジェクトを使用して、対象とするプラットフォーム (Windows Phone や [!INCLUDE[net_win8_profile](../../../includes/net-win8-profile-md.md)]など) を選択します。 プロジェクトで使用できる型およびメンバーは、自動的にこれらのプラットフォーム間で共通の型とメンバーに制限されます。 詳細については、次を参照してください。[ポータブル クラス ライブラリ](../../../docs/standard/cross-platform/cross-platform-development-with-the-portable-class-library.md)します。  
  
## <a name="see-also"></a>関連項目  
 [.NET Framework および特別のリリース](../../../docs/framework/get-started/the-net-framework-and-out-of-band-releases.md)   
 [Visual Studio 2013 の新機能します。](http://msdn.microsoft.com/library/bb386063\(v=vs.120\).aspx)   
 [ASP.NET 4.5.1 および Visual Studio 2013 用 Web ツール](http://go.microsoft.com/fwlink/?LinkID=309094)   
 [ASP.NET および Web 対応の Visual Studio](../Topic/ASP.NET%20and%20Visual%20Studio%20for%20Web.md)   
 [Windows Communication Foundation の新機能します。](http://go.microsoft.com/fwlink/?LinkId=228173)   
 [Windows Workflow Foundation の新機能します。](http://go.microsoft.com/fwlink/?LinkId=228176)   
 [Visual C の新機能します。](http://msdn.microsoft.com/library/hh409293\(v=vs.120\).aspx)