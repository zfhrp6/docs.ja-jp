---
title: "&lt;nameClaimType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;nameClaimType&gt;
<xref:System.Security.Principal.IIdentity.Name%2A> のプロパティを指定する要求タイプを設定します。  要求タイプがこのトークン ハンドラーの <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 方法によって返された <xref:System.Security.Claims.ClaimsIdentity> のオブジェクト コレクションの <xref:System.Security.Claims.Claim> の検索に使用されます。  一致の値は、たとえば、このハンドラーから生成される <xref:System.Security.Principal.IIdentity> の名前設定されます。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|value|<xref:System.Security.Principal.IIdentity.Name%2A> のプロパティに使用する要求タイプの要求を表す URI を指定する文字列。  必須。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|これらのクラスのいずれかの <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> クラス、または派生クラスにコンフィギュレーションを提供します。|  
  
## 解説  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> のオブジェクトを構成から開始されるときに `<nameClaimType>` の要素セット <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> のプロパティ。  
  
## 使用例  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## 参照  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>