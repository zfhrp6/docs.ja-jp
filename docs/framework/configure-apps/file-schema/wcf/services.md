---
title: "&lt;サービス&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 80d76ba9-2058-48ad-9b91-5e4be7e5c113
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 46a2e0d810068db6409bc7b0fd1443a41c3d3ec3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltservicesgt"></a>&lt;サービス&gt;
サービスは、設定ファイルの `services` セクションで定義されます。 各サービスには、独自の `service` 設定セクションがあります。  
  
 \<システムです。ServiceModel >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>  
        <services>  
        <service>  
        </service>  
        </services>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<サービス >](../../../../../docs/framework/configure-apps/file-schema/wcf/service.md)|サービス コントラクト、動作、および特定のサービスのエンドポイントを定義します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<system.serviceModel>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|すべての Windows Communication Foundation (WCF) 構成要素のルート要素です。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.ServicesSection>
