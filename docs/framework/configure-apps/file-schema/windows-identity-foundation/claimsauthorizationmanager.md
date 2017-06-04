---
title: "&lt;claimsAuthorizationManager&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;claimsAuthorizationManager&gt;
要求の承認マネージャーは、入力方向の要求を登録します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|Description|  
|--------|-----------------|  
|type|派生するカスタム型は<xref:System.Security.Claims.ClaimsAuthorizationManager>クラス。  指定する方法の詳細については、 `type`属性は、 [Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子要素  
 ある場合は、ない`type`属性、または、 `type`属性への参照、 <xref:System.Security.Claims.ClaimsAuthenticationManager>クラスは、 `<claimsAuthorizationManager>`要素に子要素。 ただし、クラスを派生してから<xref:System.Security.Claims.ClaimsAuthorizationManager>子の構成要素を定義することができます。  
  
### 親要素  
  
|要素|Description|  
|--------|-----------------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス ・ レベルの id の設定を指定します。|  
  
## 解説  
 によって提供される既定の動作は<xref:System.Security.Claims.ClaimsAuthorizationManager>クラスは、常に入力方向の要求を承認します。  ない場合`type`属性が指定されて場合、 `type`属性を指定します、 <xref:System.Security.Claims.ClaimsAuthorizationManager>クラス、 `<claimsAuthorizationManager>`要素には子要素があります。  指定することができます、 `type`から派生する属性は、タイプを登録するのには、 <xref:System.Security.Claims.ClaimsAuthorizationManager>カスタム動作を実装するクラス。  派生クラスは、構成要素の子要素をサポートできる、 `<claimsAuthorizationManager>`要素をオーバーライドすることで、 <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>これらの要素を処理するメソッド。  子要素を定義するスキーマ クラスのデザイナーです。  
  
> [!IMPORTANT]
>  使用すると、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission>や、 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クラスをコードで参照されている識別情報構成でクレーム ベースのアクセス制御を提供するために、 `<federationConfiguration>`要素は、要求承認マネージャー、承認決定を行うために使用するポリシーを構成します。  パッシブ Web シナリオ、たとえば、Windows 通信基盤 \(WCF\) アプリケーションまたは Web ベースでないアプリケーションではない場合も同様です。  アプリケーションがパッシブの Web アプリケーションでない場合、 `<claimsAuthorizationManager>`要素とその子ポリシー要素が存在する場合\) 参照の id の構成をされるだけの設定を適用します。  これ以外の設定は、すべて無視されます。  詳細については、[\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 要素を参照してください。  
  
 この要素を設定する、 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=fullName>プロパティ。  
  
## 使用例  
 次の XML 要求の承認の構成マネージャー リソースとアクションのペアの構成のポリシーの各リソースに対してアクションを実行するのには、リクエスターを持つ必要があります要求の論理的な組み合わせを指定しますを実装を示しています。  このポリシーを使用できるクレームの承認マネージャーを実装するコードにあります、 `ClaimsBasedAuthorization`サンプル。  
  
```  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```