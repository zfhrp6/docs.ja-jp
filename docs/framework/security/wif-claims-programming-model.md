---
title: "WIF 要求プログラミング モデル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 149cb875-9b1c-4695-b88a-fbf1725a02f9
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 8
---
# WIF 要求プログラミング モデル
ASP。NET と Windows 通信基盤 \(WCF\) の開発者は、IIdentity と IPrincipal インターフェイスを使用して、ユーザーの id 情報を使用通常。  します。NET 4.5、たんだ Windows アイデンティティ基盤 \(ぜ） が統合されています要求が常に存在を次の図に示すように、プリンシパルが。  
  
 ![WIF 要求プログラミング モデル](../../../docs/framework/security/media/wifclaimsprogrammingmodel.png "WIFClaimsProgrammingModel")  
  
 します。NET の 4.5 には System.Security.Claims に \(上の図を参照\)、新しい ClaimsPrincipal と ClaimsIdentity のクラスが含まれています。  すべてのプリンシパル。今すぐ NET から ClaimsPrincipal を派生します。  組み込みアイデンティティのすべてのクラスと FormsIdentity ASP。今すぐ NET と WindowsIdentity を ClaimsIdentity を派生します。  同様に、組み込みのすべてのプリンシパル クラス GenericPrincipal および WindowsPrincipal ClaimsPrincipal から派生します。  
  
 要求によって表される<xref:System.Security.Claims.Claim>クラス。  このクラスには、次の重要なプロパティがあります。  
  
-   <xref:System.Security.Claims.Claim.Type%2A>クレームの種類を表すし、URI は通常です。  たとえば、として電子メール アドレスの要求が表示されます`http://schemas.microsoft.com/ws/2008/06/identity/claims/email`。  
  
-   <xref:System.Security.Claims.Claim.Value%2A>要求の値が含まれているし、文字列として表されます。  たとえば、電子メール アドレス"someone@contoso.com"として表されます。  
  
-   <xref:System.Security.Claims.Claim.ValueType%2A>要求の値の型を表すし、URI は通常です。  例えば、string 型として表されます`http://www.w3.org/2001/XMLSchema#string`。  値型は、QName に XML スキーマに従って必要があります。  形式を指定する必要があります`namespace#format`は有効な QName 値を出力するには、たんだぜを有効にします。  名前空間を明確に定義された名前空間ではない場合、されませんので、公開されている XSD ファイルをその名前空間も、生成された XML スキーマの検証、おそらくすることはできません。  既定値の型は`http://www.w3.org/2001/XMLSchema#string`。  参照してください[http:\/\/www.w3.org\/2001\/XMLSchema](http://go.microsoft.com/fwlink/?LinkId=209155)既知の値の型の安全に使用できます。  
  
-   <xref:System.Security.Claims.Claim.Issuer%2A>要求を発行するセキュリティ トークン サービス \(STS\) の識別子です。  これは、STS のように、STS を表す名前 URL として表すことができます`https://sts1.contoso.com/sts`。  
  
-   <xref:System.Security.Claims.Claim.OriginalIssuer%2A>STSs の数に関係なく、要求が最初にリリース、STS の識別子は、チェーン内です。  これと同じように表されます<xref:System.Security.Claims.Claim.Issuer%2A>。  
  
-   <xref:System.Security.Claims.Claim.Subject%2A>id を調べている主題です。  これには、<xref:System.Security.Claims.ClaimsIdentity> が含まれます。  
  
-   <xref:System.Security.Claims.Claim.Properties%2A>開発することができますは、辞書と他のプロパティでは、ワイヤの転送するアプリケーション固有のデータを提供し、カスタムの検証に使用できます。  
  
## Id の委任  
 重要なプロパティの<xref:System.Security.Claims.ClaimsIdentity>です<xref:System.Security.Claims.ClaimsIdentity.Actor%2A>。  このプロパティで、バックエンド サービスに要求を作成するのには、クライアントと中間層を動作する多層システムで資格情報の委任を有効になります。  
  
### Thread.CurrentPrincipal からクレームへのアクセス  
 使用して、現在のユーザーの一連のクレームを RP のアプリケーションにアクセスするには、 `Thread.CurrentPrincipal`。  
  
 次のコード例は、System.Security.Claims.ClaimsIdentity を取得するには、このメソッドの使用方法を示しています。  
  
```  
ClaimsPrincipal claimsPrincipal = Thread.CurrentPrincipal as ClaimsPrincipal;  
  
```  
  
 詳細については、「<xref:System.Security.Claims>」を参照してください。  
  
### 役割要求の種類  
 RP アプリケーションの構成の一部であるどのような役割を決定する要求の種類をする必要があります。  この要求の種類は、System.Security.Claims.ClaimsPrincipal.IsInRole\(System.String\) が使用されます。  既定の要求の種類は`http://schemas.microsoft.com/ws/2008/06/identity/claims/role`。  
  
### クレームの Windows アイデンティティの基盤のトークンの種類からを抽出します。  
 たんだぜ、ボックスの外の認証メカニズムのいくつかの組み合わせをサポートしています。  たんだぜのさまざまな種類のトークンを抽出し、要求を次に示します。  
  
||||  
|-|-|-|  
|トークンの種類|請求書の生成|マップする Windows アクセス トークン|  
|SAML 1.1|1.  System.IdentityModel.SecurityTokenService.GetOutputClaimsIdentity\(System.Security.Claims.ClaimsPrincipal,System.IdentityModel.Protocols.WSTrust.RequestSecurityToken,System.IdentityModel.Scope\) からのすべての要求。<br />2.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/confirmationkey`トークン、証明トークンが含まれている場合は、確認キーの XML シリアル化を含む請求します。<br />3.  `http://schemas.microsoft.com/ws/2008/06/identity/claims/samlissuername`から発行者要素を要求します。<br />4.  トークンは、認証のステートメントが含まれている場合は、AuthenticationMethod と AuthenticationInstant 請求。|要求するだけでなく表示「SAML」型に 1.1、請求を除く`http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`、Windows 認証に関連するクレームを追加すると、id WindowsClaimsIdentity で表されます。|  
|SAML 2.0|「SAML 1.1」と同じです。|「SAML 1.1 の Windows アカウントにマップされている」と同じです。|  
|X509|1.  主張に、x500 識別名、使用、dnsName、SimpleName、UpnName、UrlName、拇印 \(このできますされる抽出、RSACryptoServiceProvider.ExportParameters メソッドは、X509Certificate2.PublicKey.Key プロパティを使用して\) RsaKey、\(このできますされる抽出、DSACryptoServiceProvider.ExportParameters メソッドは、X509Certificate2.PublicKey.Key プロパティを使用して\)、DsaKey、SerialNumber プロパティが x509 証明書。<br />2.  AuthenticationMethod 要求値`http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/x509`。  AuthenticationInstant を主張する XmlSchema DateTime 形式で証明書を検証した場合、時間の値を使用します。|1.  Windows アカウントの完全修飾ドメイン名としてを使用して、 `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name`値を要求します。  .<br />2.  X509 証明書が Windows には、マップされていないからのクレームとクレーム Windows に証明書をマップすることによって取得した windows アカウントから。|  
|UPN|1.  クレームは、Windows 認証での要求のようです。<br />2.  AuthenticationMethod 要求値`http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/password`。  AuthenticationInstant 要求 XmlSchema DateTime 形式でパスワードを検証した場合、時間の値を使用します。||  
|Windows \(Kerberos または NTLM\)|1.  などからのアクセス トークンを生成するクレーム： PrimarySID、DenyOnlyPrimarySID、PrimaryGroupSID、DenyOnlyPrimaryGroupSID、GroupSID、DenyOnlySID、および名前<br />2.  AuthenticationMethod 値`http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/windows`。  AuthenticationInstant、Windows トークンをアクセスするとき、時刻の値が、XMLSchema を DateTime 形式でが作成されました。||  
|RSA キー ペア|1.  `http://schemas.xmlsoap.org/ws/2005/05/identity/claims/rsa` 、RSAKeyValue の値を要求します。<br />2.  AuthenticationMethod 要求値`http://schemas.microsoft.com/ws/2008/06/identity/authenticationmethod/signature`。  AuthenticationInstant 要求と RSA キーは認証されて、時間の値 \(つまり、署名が検証された\) XMLSchema DateTime 形式で。||  
  
|||  
|-|-|  
|認証の種類|「AuthenticationMethod」要求で放射される URI|  
|パスワード|`urn:oasis:names:tc:SAML:1.0:am:password`|  
|Kerberos|`urn:ietf:rfc:1510`|  
|SecureRemotePassword|`urn:ietf:rfc:2945`|  
|TLSClient|`urn:ietf:rfc:2246`|  
|X509|`urn:oasis:names:tc:SAML:1.0:am:X509-PKI`|  
|PGP|`urn:oasis:names:tc:SAML:1.0:am:PGP`|  
|Spki|`urn:oasis:names:tc:SAML:1.0:am:SPKI`|  
|XmlDSig|`urn:ietf:rfc:3075`|  
|Unspecified|`urn:oasis:names:tc:SAML:1.0:am:unspecified`|