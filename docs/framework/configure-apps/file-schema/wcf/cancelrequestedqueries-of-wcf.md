---
title: "WCF の &lt;cancelRequestedQueries&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a7cc7125-9ea3-4d3f-99c0-878cdeb1258a
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 48c89eef074ab76547838f02a7b8dd0f45373d19
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="ltcancelrequestedqueriesgt-of-wcf"></a>WCF の &lt;cancelRequestedQueries&gt;
親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用する、クエリのコレクションを表します。 追跡参加要素がキャンセル要求レコード オブジェクトを定期受信するには、このクエリが必要です。  
  
 追跡プロファイルのクエリの詳細については、次を参照してください[追跡プロファイル。](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)  
  
 \<system.serviceModel>  
\<tracking>  
\<trackingProfile>  
\<workflow>  
\<cancelRequestedQueries>  
  
## <a name="syntax"></a>構文  
  
```xml
<tracking>   <trackingProfile name="Name">       <workflow>          <cancelRequestQueries>             <cancelRequestQuery activityName="String"                 childActivityName="String"/>          </cancelRequestQueries>       </workflow>   </trackingProfile></tracking>  
```

## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<cancelRequestedQuery>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/cancelrequestedquery.md)|親アクティビティが子アクティビティを取り消すための要求を追跡するのに使用するクエリ。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<workflow>](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/workflow.md)|`a HYPERLINK "http://msdn.microsoft.com/library/system.servicemodel.activities.tracking.configuration.profileworkflowelement.activitydefinitionid(VS.100).aspx" ctivityDefinitionId` プロパティによって識別される特定のワークフローのすべてのクエリを格納する構成要素。|  
  
## <a name="see-also"></a>参照  
 <xref:System.Activities.Tracking.CancelRequestedQuery>  
 [ワークフローの追跡とトレース](../../../../../docs/framework/windows-workflow-foundation/workflow-tracking-and-tracing.md)  
 [追跡プロファイル](../../../../../docs/framework/windows-workflow-foundation/tracking-profiles.md)
