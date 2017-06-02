---
title: "&lt;federationConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: 9
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 9
---
# &lt;federationConfiguration&gt;
構成、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) と、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) を使用する場合の連合、Ws\-federation プロトコルを使って認証します。  構成、 <xref:System.Security.Claims.ClaimsAuthorizationManager>を使用すると、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>や、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クレーム ベースのアクセス制御を提供するクラス。  
  
## 構文  
  
```  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|name|このフェデレーションの構成要素の名前。  この属性は、主に将来のプロトコルの機能拡張ポイントを提供します。  省略可能です。|  
|identityConfigurationName|Id の構成セクションで指定した名前は、 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素を使用します。  この属性が指定されていない場合は、既定の id の構成セクションが使用されます。  省略可能です。|  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<cookieHandler\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|SAM によって使用される cookie のハンドラーを構成します。  省略可能です。|  
|[\<serviceCertificate\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|暗号化し、トークンを復号化するために使用する証明書を構成します。  省略可能です。|  
|[\<wsFederation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|WS フェデレーション認証モジュール \(WSFAM\) を構成します。  省略可能です。|  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<system.identityModel.services\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Ws\-federation プロトコルを使用して、認証用の構成セクション。|  
  
## 解説  
 \<federationConfiguration\> 要素に 2 つの異なるシナリオでの設定が用意されています。  
  
-   Ws\-federation のパッシブ Web アプリケーションで使用すると、要素には構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) と、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\)。  また、セキュリティ トークン ハンドラー、証明書、および要求の承認マネージャーやクレームの認証マネージャーのコンポーネントを構成するために使用する識別情報の構成を参照します。  
  
-   使用すると、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>や、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クラスのコード内でのクレーム ベースのアクセス コントロールを提供するために、要求承認マネージャー、承認決定を行うために使用するポリシーを構成、アイデンティティの構成要素を参照します。  これは、パッシブ Web シナリオでないシナリオにも当てはまります。 たとえば、Windows 通信基盤 \(WCF\) アプリケーションまたは Web ベースでないアプリケーション。  アプリケーションがパッシブの Web アプリケーションでない場合、 [\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素とその子ポリシー要素が存在する場合\) によって参照されている識別情報の構成の`<federationConfiguration>`要素が適用されるだけの設定します。  その他のメンバーはすべて無視されます。  
  
 シナリオに関係なく、ランタイムは既定のフェデレーション構成を読み込みます。  動作は、次のように定義されています。  
  
1.  ある場合ない`<federationConfiguration>`要素が、ランタイムはフェデレーションの構成を作成し、既定値が設定されます。  この既定のフェデレーションの構成は、既定のユーザー構成を参照します。  
  
2.  場合は 1 つの`<federationConfiguration>`要素が存在しない場合、という名前のないかにかかわらず、既定のフェデレーション構成です。  場合は、 `identityConfiguration`属性を指定すると、名前付きのアイデンティティ構成が参照されています。 それ以外の場合は、ユーザーの既定の構成を参照します。  
  
3.  場合は、名前のない`<federationConfiguration>`要素が存在しない場合、既定のフェデレーションの構成です。  場合は、 `identityConfiguration`属性を指定すると、名前付きのアイデンティティ構成が参照されています。 それ以外の場合は、ユーザーの既定の構成を参照します。  
  
4.  場合は、複数の名前付き`<federationConfiguration>`要素が存在しない無名`<federationConfiguration>`要素が存在しない場合、例外がスローされます。  
  
 通常、ひとつ`<federationConfiguration>`セクションを定義します。  このセクションでは、既定のフェデレーションの構成です。  複数を一意に名前を指定する可能性があります`<federationConfiguration>`の要素。 無名以外のフェデレーション構成をロードする場合は、ただし、この例では、ハンドラーを用意する必要があるがします。  <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>イベントとセット、 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=fullName>プロパティ内のハンドラーに、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトから適切な値に初期化`<federationConfiguration>`構成ファイル内の要素。  
  
 `<federationConfiguration>`要素で表される、 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>クラス。  構成オブジェクトによって表される、 <xref:System.IdentityModel.Services.Configuration.FederationConfiguration>クラス。  1 つの<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>インスタンスの設定には、 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>プロパティとフェデレーションの構成のアプリケーションが用意されています。  
  
## 使用例  
 次の XML に示す、 `<federationConfiguration>` 、WSFAM の設定が指定され、要素 cookie の既定のハンドラー \(インスタンスの<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス\) によって SAM を使用します。  
  
> [!WARNING]
>  この例では、cookie のハンドラーと WSFAM のどちらも必要な HTTPS を使用します。  これは、ためには、 `requireHttps`の属性、 `<wsFederation>`要素と、 `requireSsl`の属性、 `<cookieHandlerElement>`は`false`。  これらの設定は、セキュリティ上のリスクがあるとほとんどの運用環境では推奨されません。  
  
```  
<system.identityModel.services>  
  <federationConfiguration>  
    <wsFederation passiveRedirectEnabled="true"   
      issuer="http://localhost:15839/wsFederationSTS/Issue"   
      realm="http://localhost:50969/" reply="http://localhost:50969/"   
      requireHttps="false"   
      signOutReply="http://localhost:50969/SignedOutPage.html"   
      signOutQueryString="Param1=value2&Param2=value2"   
      persistentCookiesOnPassiveRedirects="true" />  
    <cookieHandler requireSsl="false" />  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## 参照  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>   
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>   
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=fullName>   
 [\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)