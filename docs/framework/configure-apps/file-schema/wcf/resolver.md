---
title: '&lt;resolver&gt;'
ms.date: 03/30/2017
ms.assetid: 0c00200c-f135-4e5c-a024-76b72bcbc021
ms.openlocfilehash: f29c34f53a8bdaee4b30c72bb5d764ae3935fe7a
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32749024"
---
# <a name="ltresolvergt"></a>&lt;resolver&gt;
ピア メッシュ ID を解決してメッシュに参加する複数ノードを表すピア アドレス セットを取得するためにピア リゾルバーを指定します。  
  
 \<system.ServiceModel >  
\<bindings>  
\<netPeerBinding>  
\<binding>  
\<resolver>  
  
## <a name="syntax"></a>構文  
  
```xml  
<resolver mode="Auto/Custom/Pnrp"  
   referralPolicy="DoNotShare/Service/Share">  
</resolver>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`mode`|このサービスに関連付けられるピア リゾルバー インスタンスが PNRP 固有、カスタム リゾルバー、自動的に決定されるのいずれであるかを指定する文字列。 この属性は <xref:System.ServiceModel.PeerResolvers.PeerResolverMode> 型です。|  
|`referralPolicy`|ピア間で参照を共有する方法を指定する文字列。 この属性は <xref:System.ServiceModel.PeerResolvers.PeerReferralPolicy> 型です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<headers>](../../../../../docs/framework/configure-apps/file-schema/wcf/headers.md)|ユーザー設定のピア リゾルバー サービスの設定を指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|すべてのバインド機能を定義、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。|  
  
## <a name="remarks"></a>コメント  
 ピア名リゾルバーは、ピア メッシュに参加するピア ノードを検索するためにピア チャネルにより使用される探索サービスです。 またピア名リゾルバーは、ノードをピア メッシュに登録するために使用されます。ピア メッシュは、ピア メッシュからピア ノードを認識し、使用可能にするための機構です。 ピア リゾルバーの詳細については、次を参照してください。[ピア リゾルバー](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)です。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.PeerResolver>  
 <xref:System.ServiceModel.PeerResolvers.PeerResolverSettings>  
 <xref:System.ServiceModel.NetPeerTcpBinding.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement.Resolver%2A>  
 <xref:System.ServiceModel.Configuration.PeerResolverElement>  
 [ピア リゾルバー](../../../../../docs/framework/wcf/feature-details/peer-resolvers.md)  
 [PeerChannel アプリケーションにカスタム競合回避モジュールを追加します。](http://msdn.microsoft.com/library/12aa3787-2962-439c-ad27-46523c8b0419)
