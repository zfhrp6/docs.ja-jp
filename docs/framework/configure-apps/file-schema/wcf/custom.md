---
title: "&lt;カスタム&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a6f65a00-bd1a-4d4a-955a-fe009ec02ab8
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5bccfc95313ae3ae4a692be2165dc694783a460e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcustomgt"></a>&lt;カスタム&gt;
ユーザー設定のピア リゾルバー サービスの設定を指定します。  
  
\<system.serviceModel >  
\<バインド >  
\<netPeerBinding >  
\<バインド >  
\<競合回避モジュール >  
\<カスタム >  
  
## <a name="syntax"></a>構文  
  
```xml
<custom address="Uri" 
        resolverType="String">  
  <headers/>  
  <identity/>  
</custom>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`address`|カスタム ピア リゾルバー サービスをホストするピア ノードのエンドポイント アドレスを指定する URI。|  
|`resolverType`|カスタム ピア リゾルバー サービスの種類を指定する文字列。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|この要素を使用して構成されたカスタム ピア リゾルバーの ID を指定します。 この要素は <xref:System.ServiceModel.Configuration.IdentityElement> 型です。|  
|[\<ヘッダー >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|カスタム ピア リゾルバーによって処理される SOAP メッセージに使用するアドレス ヘッダーのコレクション。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<競合回避モジュール >](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア ノード アドレスのセットを取得するために使用されるピア リゾルバー。|  
  
## <a name="remarks"></a>コメント  
 この要素は、サービスをホストするピアのエンドポイント アドレスや特定のバインディング設定など、カスタム ピア リゾルバー サービスの基本設定を定義します。 カスタム競合回避モジュールを作成する方法の詳細については、次を参照してください。 [PeerChannel アプリケーションにカスタム競合回避モジュールを追加する](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.PeerResolvers.CustomPeerResolverService>  
 <xref:System.ServiceModel.PeerResolvers.PeerCustomResolverSettings>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement.Custom%2A>  
 <xref:System.ServiceModel.Configuration.PeerCustomResolverElement>  
 [ピア リゾルバー](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [PeerChannel アプリケーションにカスタム競合回避モジュールを追加します。](http://msdn.microsoft.com/en-us/12aa3787-2962-439c-ad27-46523c8b0419)
