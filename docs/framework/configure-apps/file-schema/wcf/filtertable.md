---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8cf87cc74c7bb5d495584407c803dacc7b94f195
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltfiltertablegt"></a>&lt;filterTable&gt;
True に評価されると、フィルターに対してメッセージと、クライアント エンドポイントにメッセージをルーティングを評価するフィルターの一覧を含むルーティング テーブルを表します。  
  
 \<system.serviceModel >  
\<ルーティング >  
\<routingTables >  
\<テーブル >  
  
## <a name="syntax"></a>構文  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|要素|説明|  
|-------------|-----------------|  
|name|この構成要素の一意の名前を示す文字列。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<フィルター >](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|ルーティング フィルターとターゲット エンドポイントとのマッピング。フィルターが一致したときにメッセージを送信するために使用されます。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|ルーティング テーブルを含む構成セクション。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
