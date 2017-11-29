---
title: "&lt;issuerChannelBehaviors&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 50710506-e28f-45dd-ab7e-bff6f44173db
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7dca60a5bf1b3dd81502f9fd48d2881c3a9b71dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltaddgt-of-ltissuerchannelbehaviorsgt"></a>&lt;issuerChannelBehaviors&gt; の &lt;add&gt;
STS と通信するときに使用されるエンドポイントの動作を追加します。  
  
> [!NOTE]
>  すべてのエンドポイント動作が含まれている場合、 [ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)要素、例外がスローされます。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
endpointBehaviors セクション  
\<動作 >  
\<clientCredentials >  
\<issuedToken >  
\<issuerChannelBehaviors > 要素  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
<add issuerAddress="string"  
     behaviorConfiguraton="string" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|issuerAddress|通信するためのセキュリティ トークン発行者の URI。|  
|behaviorConfiguration|同じ構成ファイルに定義されたエンドポイントの動作の名前。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)|指定されたセキュリティ トークン サービスと通信するときに使用される [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアント エンドポイントの動作のコレクションが含まれています。|  
  
## <a name="remarks"></a>コメント  
 `issuerAddress` には、クライアントの通信相手となるセキュリティ トークン サービスの URI が含まれます。 `behaviorConfiguration` は、アプリケーションが使用するエンドポイント動作を表します。アプリケーションは、セキュリティ トークン サービスから発行されたトークンを取得するために、[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] によって作成されたチャネルでこの動作を使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientElement.IssuerChannelBehaviors%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElement>  
 <xref:System.ServiceModel.Configuration.IssuedTokenClientBehaviorsElementCollection>  
 <xref:System.ServiceModel.Security.IssuedTokenClientCredential.IssuerChannelBehaviors%2A>  
 [サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [セキュリティ動作](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [サービスとクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)  
 [方法: フェデレーション クライアントを作成します。](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [方法: ローカル発行者を構成します。](../../../../../docs/framework/wcf/feature-details/how-to-configure-a-local-issuer.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [\<issuerChannelBehaviors >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuerchannelbehaviors-element.md)
