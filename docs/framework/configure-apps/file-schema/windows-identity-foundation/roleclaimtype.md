---
title: "&lt;roleClaimType&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
caps.latest.revision: 4
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 4
---
# &lt;roleClaimType&gt;
たとえば、ハンドラーの <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 方法によって返された <xref:System.Security.Claims.ClaimsIdentity> のオブジェクト コレクションの要求ロールのタイプを定義する要求タイプを指定します。  
  
## 構文  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
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
|value|ロールのタイプの要求を使用して要求の要求のタイプを表す URI を指定する文字列。|  
  
### 子要素  
 なし  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<samlSecurityTokenRequirement\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|これらのクラスのいずれかの <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> クラス、または派生クラスにコンフィギュレーションを提供します。|  
  
## 解説  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> のオブジェクトを構成から開始されるときに `<roleClaimType>` の要素セット <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> のプロパティ。  
  
## 使用例  
  
```  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## 参照  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>