---
title: "&lt;ホスト&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: be566d55-9d50-4b2e-985d-52a5cc26cbbb
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bded8d718259bf4fc84bfe790db069a77fc2a703
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="lthostgt"></a>&lt;ホスト&gt;
サービス ホストの設定を指定します。  
  
 \<システムです。ServiceModel >  
\<サービス >  
\<サービス >  
\<ホスト >  
  
## <a name="syntax"></a>構文  
  
```xml  
<host>  
      <baseAddresses>  
         <baseAddress baseAddress="string" />  
      </baseAddresses>  
      <timeOuts closeTimeout="TimeSpan"  
         openTimeout="TimeSpan" >  
</host>  
```  
  
## <a name="type"></a>型  
 `Type`  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<baseAddresses >](../../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)|サービス ホストによって使用されるベース アドレスを指定する `baseAddress` 要素のコレクション。|  
|[\<タイムアウト >](../../../../../docs/framework/configure-apps/file-schema/wcf/timeouts.md)|サービス ホストを開くまたは閉じるまでに待機できる期間を指定する構成要素。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<サービス >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|[!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] サービスの設定を指定します。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [ホスティング](../../../../../docs/framework/wcf/feature-details/hosting.md)
