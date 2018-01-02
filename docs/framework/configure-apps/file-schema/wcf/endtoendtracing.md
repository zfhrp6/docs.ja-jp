---
title: '&lt;endToEndTracing&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5034f5de-bb60-4157-9ad4-58aaade094e0
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a43801f4c45d7ac518c3b24cadc58ffbec40adb4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltendtoendtracinggt"></a>&lt;endToEndTracing&gt;
サービス アプリケーションの実行中にエンドツーエンドのトレースのさまざまな側面を有効または無効にするための構成要素。  
  
 \<システムです。ServiceModel >  
\<診断 >  
\<endToEndTracing >  
  
## <a name="syntax"></a>構文  
  
```xml  
<system.serviceModel>  
   <diagnostics>  
       <endToEndTracing activityTracing="Boolean"  
          messageFlowTracing="Boolean"  
          propagateActivity="Boolean" />  
   </diagnostics>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`activityTracing`|アクティビティのトレースが有効かどうかを示すブール値。|  
|`messageFlowTracing`|メッセージ フローのトレースが有効かどうかを示すブール値。|  
|`propagateActivity`|伝達属性が true に設定されているかどうかを示すブール値。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<診断 >](../../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)|管理者が行うランタイムの検査と管理の WCF 設定を定義します。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.DiagnosticSection>  
 <xref:System.ServiceModel.Diagnostics>  
 <xref:System.ServiceModel.Configuration.DiagnosticSection.EndToEndTracing%2A>  
 <xref:System.ServiceModel.Configuration.EndToEndTracingElement>  
 [エンドツーエンドのトレース](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing.md)
