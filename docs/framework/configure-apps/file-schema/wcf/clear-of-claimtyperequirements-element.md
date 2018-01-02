---
title: "&lt;claimTypeRequirements&gt; 要素の &lt;clear&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ef42fde7-f292-4610-9111-9fea382c3b5f
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 71cc4516362691484408ae2f81dfee462bd560d9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltcleargt-of-ltclaimtyperequirementsgt-element"></a>&lt;claimTypeRequirements&gt; 要素の &lt;clear&gt;
すべてのクレームの種類をフェデレーション資格情報から削除するように指定します。 これにより、コレクションの初期値を確実に空にできます。  
  
 \<システムです。ServiceModel >  
\<バインド >  
\<wsFederatedBinding >  
\<バインド >  
\<セキュリティ >  
\<メッセージ >  
\<claimTypeRequirements >  
  
## <a name="syntax"></a>構文  
  
```xml  
<claimTypeRequirements>  
      <clear />  
</claimTypeRequirements>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<claimTypeRequirements >](../../../../../docs/framework/configure-apps/file-schema/wcf/claimtyperequirements-for-message.md)|必須のクレームの種類のコレクションを指定します。 各要素は <xref:System.ServiceModel.Configuration.ClaimTypeElement> 型です。<br /><br /> フェデレーション シナリオでは、サービスが受信資格情報についての要件を記述します。 たとえば、受信資格情報は、特定のクレーム タイプのセットを処理する必要があります。 このコレクションの要素はそれぞれ、フェデレーション資格情報に表示されると予想される必須の要求および省略可能な要求の種類を指定します。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
