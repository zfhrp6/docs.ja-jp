---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 06824e20286f8905ad3a8ac9d2b4a30366a6ec10
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32757373"
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
入力方向の要求の要求の承認マネージャーを登録します。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|型|派生するカスタム型、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラスです。 指定する方法について、`type`属性は、「[カスタム型の参照](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)です。|  
  
### <a name="child-elements"></a>子要素  
 ある場合ありません`type`属性、または、`type`属性参照、<xref:System.Security.Claims.ClaimsAuthenticationManager>クラス、`<claimsAuthorizationManager>`要素が子要素を受け取らないです。 ただし、から派生したクラス<xref:System.Security.Claims.ClaimsAuthorizationManager>子の構成要素を定義できます。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|サービス レベルの id 設定を指定します。|  
  
## <a name="remarks"></a>コメント  
 によって提供される既定の動作、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラスは常に入力方向の要求を承認します。 ない場合は`type`属性が指定されて場合、または、`type`属性を指定、<xref:System.Security.Claims.ClaimsAuthorizationManager>クラス、`<claimsAuthorizationManager>`要素は子要素を取りません。 指定することができます、`type`から派生した型を登録する属性、<xref:System.Security.Claims.ClaimsAuthorizationManager>カスタム動作を実装するクラス。 派生クラスの子要素から構成をサポートできる、`<claimsAuthorizationManager>`要素をオーバーライドすることで、<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>これらの要素を処理するメソッド。 子要素に定義されたスキーマは、クラスの設計者の責任です。  
  
> [!IMPORTANT]
>  使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コードによって参照される id の構成でクレーム ベースのアクセス制御を提供するクラス、`<federationConfiguration>`要素は、要求承認マネージャーとを使用して、ポリシーを構成します。承認を決定します。 これは、true の場合、パッシブの Web シナリオ、たとえば、Windows Communication Foundation (WCF) アプリケーションや Web ベースではないアプリケーションではないシナリオであってもです。 アプリケーションが、パッシブ Web アプリケーションではない場合、`<claimsAuthorizationManager>`要素 (とその子ポリシー要素、存在する場合) のみに適用される設定は、参照される id の構成のです。 その他のすべての設定は無視されます。 詳細については、次を参照してください。、 [ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)要素。  
  
 この要素の設定、<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>プロパティです。  
  
## <a name="example"></a>例  
 次の XML では、それぞれ指定するブール型の組み合わせ申請元がリソースに対してアクションを実行する処理する必要をクレームのリソース操作のペアから成るポリシーを実装するマネージャー要求承認の構成を示します。 このポリシーを使用できる要求の承認マネージャーを実装するコードは含まれて、`ClaimsBasedAuthorization`サンプルです。  
  
```xml  
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
