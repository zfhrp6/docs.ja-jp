---
title: "WIF 3.5 と WIF 4.5 間での名前空間マッピング | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a092d98c-444d-4336-a644-63c2e11e96c8
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# WIF 3.5 と WIF 4.5 間での名前空間マッピング
.NET 4.5 以降では、Windows ID Foundation \(WIF\) は、.NET Framework に完全に統合されています。  この統合には、WIF の名前空間と API サーフェイスの名前変更と連結を生成しました。  このトピックでは、WIF 3.5 の名前空間と WIF 4.5 の名前空間の間の一般的なガイダンスとマッピングを提供します。  を網羅したものではないはなく WIF 4.5 の使い慣れた WIF 3.5 のクラスの場所に関する一般的な情報を検索するか提供します。  WIF WIF 3.5 と 4.5 の違いに関する詳細については、[Windows Identity Foundation 4.5 の新機能](../../../docs/framework/security/whats-new-in-wif.md)を参照してください。  WIF WIF 3.5 ~ 4.5 を使用して作成されたアプリケーションを移行する方法については、[WIF 3.5 でビルドされたアプリケーションを WIF 4.5 に移行するためのガイドライン](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)を参照してください。  
  
## WIF WIF 3.5 ~ 4.5 の名前空間の割り当て  
 WIF 3.5 の `Microsoft.IdentityModel` の名前空間の下で収集された WIF のクラスは名前空間間で配布されます: WIF 4.5 の `System.Security.Claims`、`System.ServiceModel.Security`と `System.IdentityModel` の名前空間。  WIF さらに 3.5 の名前空間は WIF 4.5 に統合されているか、完全にドロップします。  
  
> [!IMPORTANT]
>  `System.IdentityModel` に次の名前空間は、WCF クレームベース ID モデルを実装するクラスが含まれています: <xref:System.IdentityModel.Claims?displayProperty=fullName>、<xref:System.IdentityModel.Policy?displayProperty=fullName>と <xref:System.IdentityModel.Selectors?displayProperty=fullName>。  WCF クレームベース ID モデルは WIF に置き換えられました。  WIF に基づいてソリューションをビルドする場合は、この 3 は、名前空間のクラスを使用する必要があります。  
  
 次の表は、に関する WIF 3.5 のクラスが WIF 4.5 である、情報を示します。  
  
||||  
|-|-|-|  
|**WIF 3.5 の名前空間**|**WIF 4.5 の名前空間**|**コメント**|  
|`Microsoft.IdentityModel`|<xref:System.IdentityModel?displayProperty=fullName>|-   定数を表すクラスのほとんどは実行されません。<br />-   セキュリティ トークン サービスのビルドに使用されるクラスは `Microsoft.IdentityModel.SecurityTokenService` から <xref:System.IdentityModel?displayProperty=fullName>に移動されています。<br />-   `Microsoft.IdentityModel.Threading` のクラスは <xref:System.IdentityModel?displayProperty=fullName>に移動されました。<br />-   `ExceptionMapper` と `MruSecurityTokenCache` のクラスは実行されません。|  
|`Microsoft.IdentityModel.Claims`|<xref:System.Security.Claims?displayProperty=fullName>|-   `IClaimsPrincipal` と `IClaimsIdentity` のインターフェイスは WIF 4.5 では実装されません。  代わりに、現在は <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> と <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> は、ほとんどの .NET プリンシパル オブジェクトと ID のクラスの派生元となる基本クラスです。  これは、特殊な要求プリンシパルおよび WIF 4.5、使用中 <xref:System.Security.Principal.WindowsPrincipal?displayProperty=fullName> と <xref:System.Security.Principal.WindowsIdentity?displayProperty=fullName> の `Microsoft.IdentityModel.Claims.WindowsClaimsPrincipal` と `Microsoft.IdentityModel.Claims.WindowsClaimsIdentity` などの ID クラスの代わりに必要ないことを意味します。  同じ WIF には 3.5 の ID クラスなどの特殊な要求プリンシパルの他にも当てはまります。<br />-   `Microsoft.IdentityModel.Claims.ClaimsCollection` のクラスは WIF 4.5 では実装されません。  代わりに、要求のコレクションは型 <xref:System.Security.Claims.Claim?displayProperty=fullName>の列挙可能なコレクションとして公開されます。<br />-   <xref:System.Security.Claims.ClaimsPrincipal?displayProperty=fullName> と <xref:System.Security.Claims.ClaimsIdentity?displayProperty=fullName> は、完全に LINQ をサポートするメソッドを提供します。|  
|`Microsoft.IdentityModel.Configuration`|<xref:System.IdentityModel.Configuration?displayProperty=fullName>|ある要素とクラスは、変更が行われます。このとき、ユーザーは WIF 4.5 にドロップ; これで、たとえば `Microsoft.IdentityModel.Configuraiton.ServiceConfiguration` は <xref:System.IdentityModel.Configuration.IdentityConfiguration?displayProperty=fullName>です。|  
|`Microsoft.IdentityModel.Protocols`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSFederation`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSFederation.Metadata`|<xref:System.IdentityModel.Metadata?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Protocols.WSIdentity`|WIF 4.5 に実装されていません|WIF 3.5 ではクラスを WIF 4.5 で実行されなかった場合、CardSpace をサポートするために含まれています。|  
|`Microsoft.IdentityModel.Protocols.WSTrust`|<xref:System.ServiceModel.Security?displayProperty=fullName> の <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> と名前空間の間のされました。|クラスは <xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName> の名前空間に WS\-Trust 項目を表す;あります。たとえば、<xref:System.IdentityModel.Protocols.WSTrust.RequestSecurityToken> のクラス。  WS\-Trust プロトコルを使用して通信するための WCF サービスを有効にする WCF サービス コントラクト、ホスト サービスとチャネルを表すクラスは <xref:System.ServiceModel.Security?displayProperty=fullName> の名前空間に含まれています; たとえば、<xref:System.ServiceModel.Security.WSTrustServiceHost> のクラス。|  
|`Microsoft.IdentityModel.Protocols.WSTrust.Bindings`|WIF 4.5 に実装されていません|\-|  
|`Microsoft.IdentityModel.Protocols.XmlEncryption`|WIF 4.5 に実装されていません|WIF 3.5 の XML 暗号化の定数を表す含まれるクラス。  これらの定数は WIF 4.5 では実装されません。|  
|`Microsoft.IdentityModel.Protocols.XmlSignature`|<xref:System.IdentityModel?displayProperty=fullName>|定数を表すクラスおよび `EnvelopingSignature` のクラスは実行されません。|  
|`Microsoft.IdentityModel.SecurityTokenService`|<xref:System.IdentityModel?displayProperty=fullName>、<xref:System.IdentityModel.Protocols.WSTrust?displayProperty=fullName>と <xref:System.IdentityModel.Tokens?displayProperty=fullName> の名前空間に分割します。|\-|  
|`Microsoft.IdentityModel.Threading`|<xref:System.IdentityModel?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens.Saml11`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Tokens.Saml2`|<xref:System.IdentityModel.Tokens?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Web`|<xref:System.IdentityModel.Services?displayProperty=fullName>|\-|  
|`Microsoft.IdentityModel.Web.Configuration`|<xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>|受動的な \(WS\-Federation\) のシナリオに構成を提供するクラスには <xref:System.IdentityModel.Services.Configuration?displayProperty=fullName>主として実行されていました; ただし、これらのクラスには、<xref:System.IdentityModel.Services?displayProperty=fullName>にあります。|  
|`Microsoft.IdentityModel.Web.Controls`|WIF 4.5 に実装されていません|`Microsoft.IdentityModel.Web.Controls` のクラスは WIF 4.5 に存在しないフェデレーションな受動的な署名のコントロールを実装します。|  
|`Microsoft.IdentityModel.WindowsTokenService`|WIF 4.5 に実装されていません|\-|  
  
## 参照  
 [Windows Identity Foundation 4.5 の新機能](../../../docs/framework/security/whats-new-in-wif.md)   
 [WIF 3.5 でビルドされたアプリケーションを WIF 4.5 に移行するためのガイドライン](../../../docs/framework/security/guidelines-for-migrating-an-application-built-using-wif-3-5-to-wif-4-5.md)