---
title: '&lt;federationConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8b14054c-6d07-46ab-ab58-03f14beac0f2
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 9abe07c065dbea67c5ebc4a4490d9f88258130c8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltfederationconfigurationgt"></a>&lt;federationConfiguration&gt;
構成、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM) を使用する場合は、Ws-federation プロトコルを使用した認証をフェデレーションします。 構成、<xref:System.Security.Claims.ClaimsAuthorizationManager>を使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>クレームに基づくアクセス制御を提供するクラス。  
  
 \<system.identityModel.services >  
\<federationConfiguration >  
  
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
  
|属性|説明|  
|---------------|-----------------|  
|name|このフェデレーションの構成要素の名前。 この属性は、主の将来のプロトコル機能拡張ポイントを提供します。 省略可能です。|  
|identityConfigurationName|指定された id の構成セクションの名前、 [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)要素を使用します。 この属性が指定されていない場合、既定の id 構成セクションが表示されます。 省略可能です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cookieHandler >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/cookiehandler.md)|SAM によって使用されるクッキー ハンドラーを構成します。 省略可能です。|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicecertificate.md)|暗号化し、トークン暗号化解除に使用される証明書を構成します。 省略可能です。|  
|[\<wsFederation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/wsfederation.md)|Ws-federation 認証モジュール (WSFAM) を構成します。 省略可能です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.identityModel.services>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel-services.md)|Ws-federation プロトコルを使用して認証用の構成セクション。|  
  
## <a name="remarks"></a>コメント  
 \<FederationConfiguration > 要素が 2 つの異なるシナリオでの設定を提供します。  
  
-   要素に構成設定が含まれる WS フェデレーション パッシブ Web アプリケーションを使用する場合、 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule> (WSFAM) および<xref:System.IdentityModel.Services.SessionAuthenticationModule>(SAM)。 セキュリティ トークン ハンドラーと証明書、および要求の承認マネージャーと要求認証マネージャーなどのコンポーネントを構成するために使用される id の構成も参照します。  
  
-   使用する場合、<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>または<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>コード内のクレーム ベースのアクセス制御を提供するクラス、要素参照 id の構成要求承認マネージャーおよび承認に使用されるポリシーを構成します。決定します。 これが true の場合は受動的な Web シナリオ以外ではないシナリオであってもたとえば、Windows Communication Foundation (WCF) アプリケーションまたは Web ベースではないアプリケーションです。 アプリケーションが、パッシブ Web アプリケーションではない場合、 [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)要素 (とその子ポリシー要素、存在する場合) によって参照される id の構成の`<federationConfiguration>`要素唯一の設定が適用されます。 他の属性はすべて無視されます。  
  
 シナリオに関係なく、ランタイムは既定のフェデレーションの構成を読み込みます。 動作の定義は次のとおりです。  
  
1.  ある場合ありません`<federationConfiguration>`要素が存在、ランタイムは、フェデレーションの構成を作成し、既定値を設定します。 この既定のフェデレーションの構成では、既定の id 構成を参照します。  
  
2.  場合、1 つ`<federationConfiguration>`要素が存在、という名前または名前のないに関係なく、既定のフェデレーション構成します。 場合、`identityConfiguration`属性を指定すると、名前付きの id の構成が参照されている以外の場合は、既定の id 構成が参照されています。  
  
3.  場合は、名前のない`<federationConfiguration>`要素が、これは既定のフェデレーション構成します。 場合、`identityConfiguration`属性を指定すると、名前付きの id の構成が参照されている以外の場合は、既定の id 構成が参照されています。  
  
4.  複数の名前を付けて場合`<federationConfiguration>`要素が存在しない名前のない`<federationConfiguration>`要素が、例外がスローされます。  
  
 通常、1 つだけ`<federationConfiguration>`セクションを定義します。 このセクションでは、既定のフェデレーション構成です。 複数の一意な名前を指定することがあります`<federationConfiguration>`要素です。 ただし、この場合、名前のない別のフェデレーションの構成を読み込む場合は、する必要がありますハンドラーを提供します。 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfigurationCreated>イベントとセット、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationCreatedEventArgs.FederationConfiguration%2A?displayProperty=nameWithType>にハンドラー内のプロパティ、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>オブジェクトから、適切な値で初期化`<federationConfiguration>`構成ファイル内の要素。  
  
 `<federationConfiguration>`要素として表されます、<xref:System.IdentityModel.Services.Configuration.FederationConfigurationElement>クラスです。 構成オブジェクト自体がによって表される、<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>クラスです。 1 つ<xref:System.IdentityModel.Services.Configuration.FederationConfiguration>インスタンスに設定されて、<xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>プロパティし、フェデレーション アプリケーションの構成を提供します。  
  
## <a name="example"></a>例  
 次の XML に示します、 `<federationConfiguration>` 、WSFAM の設定を指定し、ことを指定する要素既定のクッキー ハンドラー (のインスタンス、<xref:System.IdentityModel.Services.ChunkedCookieHandler>クラス)、SAM で使用します。  
  
> [!WARNING]
>  この例では、HTTPS を使用するクッキー ハンドラーも WSFAM が必要です。 これは、ため、`requireHttps`属性を`<wsFederation>`要素および`requireSsl`属性を`<cookieHandlerElement>`は`false`します。 これらの設定は、セキュリティ上のリスクを伴うことがありますが、ほとんどの実稼働環境には推奨されません。  
  
```xml  
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
  
## <a name="see-also"></a>関連項目  
 <xref:System.IdentityModel.Services.WSFederationAuthenticationModule>  
 <xref:System.IdentityModel.Services.SessionAuthenticationModule>  
 <xref:System.IdentityModel.Services.FederatedAuthentication.FederationConfiguration%2A?displayProperty=nameWithType>  
 [\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)
