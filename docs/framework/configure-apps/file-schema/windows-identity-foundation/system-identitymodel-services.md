---
title: '&lt;system.identityModel.services&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fa1624dd-2d74-4ae3-942e-498cee261ac5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 03c2fa7fe65650b760937ef06b848152893e023b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsystemidentitymodelservicesgt"></a>&lt;system.identityModel.services&gt;
Ws-federation プロトコルを使用して認証用の構成セクション。  
  
 \<system.identityModel.services >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel.services>  
  <federationConfiguration name=xs:string identityConfigurationName=xs:string>  
  </federationConfiguration>  
</system.identityModel.services>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<federationConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)|構成設定が含まれています、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) HTTP モジュールです。|  
  
### <a name="parent-elements"></a>親要素  
 なし  
  
## <a name="remarks"></a>コメント  
 追加、 `<system.identityModel.services>` SAM と WSFAM 用の設定を提供するアプリケーションの構成ファイルにセクションです。  
  
> [!IMPORTANT]
>  使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>、コードでは、要求の承認マネージャー内のクレーム ベースのアクセス制御を提供するクラス (<xref:System.Security.Claims.ClaimsAuthorizationManager>) を通じて承認決定を行うために使用するポリシーが構成されていると、 `<identityConfiguration>`暗黙的または明示的に参照される要素、`<federationConfiguration>`このセクションの要素。 詳細については、次を参照してください。、**解説**下にある、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。  
  
 `<system.identityModel.services>`セクションで表される、<xref:System.IdentityModel.Services.Configuration.SystemIdentityModelServicesSection>クラスです。 子のコレクション`<federationConfiguration>`セクションで構成されている要素がによって表される、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElementCollection>クラスです。  
  
## <a name="example"></a>例  
 次の XML を追加する方法を示しています、`<system.identityModel.services>`構成ファイルにセクションです。 最初に、両方のセクションの宣言を追加する必要があります、`<system.identityModel.services>`セクションおよび`<system.identityModel>`セクションです。 (追加すると、 `<system.identityModel.services>`  セクションの宣言も追加する必要があります、`<system.identityModel>`セクションで、既定値を確実に`<identityConfiguration>`セクションは、必要な場合、ランタイムによって作成できます)。セクション宣言が追加した後は、下にあるフェデレーション認証設定を構成することができます、`<system.identityModel.services>`要素。  
  
```xml  
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
