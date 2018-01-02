---
title: '&lt;nameClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 2c53886458b4c6e2867e1f9fddd4ab50b199c660
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltnameclaimtypegt"></a>&lt;nameClaimType&gt;
指定するクレームの種類を設定、<xref:System.Security.Principal.IIdentity.Name%2A>プロパティです。 要求の種類がの検索に使用される、<xref:System.Security.Claims.Claim>のコレクションで<xref:System.Security.Claims.ClaimsIdentity>によって返されるオブジェクト、<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>このトークン ハンドラーのメソッドです。 一致する要求の値がの名前として設定し、<xref:System.Security.Principal.IIdentity>このトークン ハンドラーから生成します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
\<samlSecurityTokenRequirement >  
\<nameClaimType >  
  
## <a name="syntax"></a>構文  
  
```xml  
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
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|value|使用する要求の要求の種類を表す URI を指定する文字列、<xref:System.Security.Principal.IIdentity.Name%2A>プロパティです。 必須。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|構成を提供、<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>クラス、<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>クラス、またはこれらのクラスのいずれかの派生クラス。|  
  
## <a name="remarks"></a>コメント  
 `<nameClaimType>`要素セット、<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>プロパティと、<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>構成からオブジェクトを初期化します。  
  
## <a name="example"></a>例  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
