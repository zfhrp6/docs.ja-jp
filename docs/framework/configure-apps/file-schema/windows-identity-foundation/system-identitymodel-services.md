---
title: "&lt;system.identityModel.services&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: 6
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 6
---
# &lt;system.identityModel.services&gt;
Ws\-federation プロトコルを使用して、認証用の構成セクション。  
  
 \<system.identityModel.services\>  
  
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
 なし  
  
### 子要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定を含む、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> \(WSFAM\) と、 <xref:System.IdentityModel.Services.SessionAuthenticationModule> \(SAM\) の HTTP モジュール。|  
  
### 親要素  
 なし  
  
## 解説  
 追加、 `<system.identityModel.services>` SAM および WSFAM の設定を提供するために、アプリケーションの構成ファイルを追加します。  
  
> [!IMPORTANT]
>  使用すると、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>や、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コード、要求の承認マネージャー内のクレームに基づくアクセス制御を提供するクラス \(<xref:System.Security.Claims.ClaimsAuthorizationManager>\) と承認を決定するために使用するポリシーを構成、 `<identityConfiguration>`から暗黙的または明示的に参照される要素が`<federationConfiguration>`このセクション内の要素。  詳細についてを参照してください、 **備考**で、 [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。  
  
 `<system.identityModel.services>`セクションで表される、 <xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>クラス。  コレクションの子`<federationConfiguration>` 、セクション内の構成要素で表される、 <xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>クラス。  
  
## 使用例  
 次の XML を追加する方法を示しています、 `<system.identityModel.services>`するには、構成ファイルのセクション。  最初セクション宣言の両方を追加する必要があります、 `<system.identityModel.services>`セクションと、 `<system.identityModel>`セクション。  \(を追加したとき、 `<system.identityModel.services>`セクションでは、する必要がありますも追加すると、宣言を`<system.identityModel>`デフォルトようにするセクション`<identityConfiguration>`セクション必要がある場合は、ランタイムで作成できます\)。宣言セクションを追加した後は、統合認証の設定\] を構成できます、 `<system.identityModel.services>`要素。  
  
```  
<configuration>  
  <configSections>  
    <section name="system.identityModel" type="System.IdentityModel.Configuration.SystemIdentityModelSection, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
    <section name="system.identityModel.services" type="System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=B77A5C561934E089" />  
  </configSections>  
  
  <!-- Additional elements (not shown) -->  
  
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
  
</configuration>  
```