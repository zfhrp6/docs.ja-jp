---
title: "&lt;synchronousReceive&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cc070387-3d11-4b02-a952-bc08ad2df05a
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 63923121ae96b85bd192899a8d8ad285a3ad5b2d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsynchronousreceivegt-element"></a>&lt;synchronousReceive&gt; 要素
この構成要素は、サービスまたはクライアント アプリケーションでメッセージを受信する場合のランタイム動作を指定するために使用されます。 属性や子要素はありません。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors >  
\<動作 >  
\<synchronousReceive >  
  
## <a name="syntax"></a>構文  
  
```xml  
<synchronousReceive />  
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
|[\<動作 >](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|エンドポイントの動作を指定します。|  
  
## <a name="remarks"></a>コメント  
 この動作を使用して、既定の非同期受信ではなく同期受信を使用するようにチャネル リスナーに指示します。 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] は、受け入れた各チャネルに対して新しい処理スレッドを発行します。 チャネルが多数ある場合は、スレッドが不足する可能性があります。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.SynchronousReceiveElement>  
 <xref:System.ServiceModel.Description.SynchronousReceiveBehavior>
