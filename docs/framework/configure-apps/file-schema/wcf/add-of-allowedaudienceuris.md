---
title: "&lt;allowedAudienceUris&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4e7b7637-e0ea-4a91-988f-6b6ef28d9fc3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8b10a0ef5718197464ffa40126f0a013d82256dc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltallowedaudienceurisgt"></a>&lt;allowedAudienceUris&gt; の &lt;add&gt;
<xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI を追加します。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
\<serviceBehaviors >  
\<動作 >  
\<serviceCredentials >  
\<issuedTokenAuthentication >  
\<allowedAudienceUris >  
\<追加 > 要素を\<allowedAudienceUris >  
  
## <a name="syntax"></a>構文  
  
```xml  
<allowedAudienceUris>   
   <add allowedAudienceUri="String"/>  
</allowedAudienceUris>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|allowedAudienceUri|<xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI を含む文字列です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)|<xref:System.IdentityModel.Tokens.SamlSecurityToken> インスタンスにより有効と見なされるように、<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> セキュリティ トークンのターゲットとなる URI のコレクションを表します。|  
  
## <a name="remarks"></a>コメント  
 このコレクションは、<xref:System.IdentityModel.Tokens.SamlSecurityToken> セキュリティ トークンを発行するセキュリティ トークン サービス (STS) を利用するフェデレーション アプリケーションで使用する必要があります。 STS がセキュリティ トークンを発行する場合、このセキュリティ トークンに <xref:System.IdentityModel.Tokens.SamlAudienceRestrictionCondition> を追加して、セキュリティ トークンの提供先となる Web サービスの URI を指定できます。 これにより、受け取り側 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator> Web サービスは、次のようにしてこのチェックが行われるように指定することで、発行されたセキュリティ トークンがこの Web サービスを対象としていることを確認できます。  
  
-   `audienceUriMode` の `<issuedTokenAuthentication>` 属性を <xref:System.IdentityModel.Selectors.AudienceUriMode.Always> または <xref:System.IdentityModel.Selectors.AudienceUriMode.BearerKeyOnly> に設定します。  
  
-   このコレクションに URI を追加して、有効な URI のセットを指定します。  
  
 詳細については、「<xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>」を参照してください。  
  
 この構成要素を使用する方法については、次を参照してください。[する方法: フェデレーション サービスの資格情報の構成](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.AllowedAudienceUris%2A>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElementCollection>  
 <xref:System.ServiceModel.Configuration.AllowedAudienceUriElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.AllowedAudienceUris%2A>  
 [\<allowedAudienceUris >](../../../../../docs/framework/configure-apps/file-schema/wcf/allowedaudienceuris.md)  
 [\<issuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [方法 : フェデレーション サービスで資格情報を設定する](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
