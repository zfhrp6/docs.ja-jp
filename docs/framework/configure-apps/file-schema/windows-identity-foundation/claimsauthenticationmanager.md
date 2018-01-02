---
title: '&lt;claimsAuthenticationManager&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6d30a450-6d13-4671-81a8-77e0204500c5
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: b7d68c2fe89b5ca56319df2f24fadd51f329f5ab
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimsauthenticationmanagergt"></a>&lt;claimsAuthenticationManager&gt;
入力方向の要求の要求認証マネージャーに登録します。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<claimsAuthenticationManager >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthenticationManager type=xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthenticationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|派生するカスタム型を指定します、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラスです。 指定する方法について、`type`属性 [カスタム型の参照] を参照してください。|  
  
### <a name="child-elements"></a>子要素  
 ある場合ありません`type`属性、または、`type`属性参照、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthenticationManager>`要素が子要素を受け取らないです。 ただし、から派生したクラス<xref:System.Security.Claims.ClaimsAuthenticationManager>子の構成要素を定義できます。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id 設定を指定します。|  
  
## <a name="remarks"></a>コメント  
 によって提供される既定の動作、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラスには、入力方向の要求がエコーされます。 ない場合は`type`属性が指定されて場合、または、`type`属性を指定、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthenticationManager>`要素は子要素を取りません。 指定することができます、`type`から派生した型を登録する属性、<xref:System.Security.Claims.ClaimsAuthenticationManager>カスタム動作を実装するクラス。 派生クラスの子要素から構成をサポートできる、`<claimsAuthenticationManager>`要素をオーバーライドすることで、<xref:System.Security.Claims.ClaimsAuthenticationManager.LoadCustomConfiguration%2A>これらの要素を処理するメソッド。 子要素に定義されたスキーマは、クラスの設計者の責任です。  
  
 `<claimsAuthenticationManager>`要素セット、<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthenticationManager%2A?displayProperty=nameWithType>プロパティです。  
  
## <a name="example"></a>例  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="MyIdentity">  
      <claimsAuthenticationManager type="MyNamespace.CustomClaimsAuthenticationManager, MyAssembly"/>          
    </identityConfiguration>  
</microsoft.identityModel>  
```
