---
title: "&lt;entries&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1583ec3cab3ed43556dc066c1e4753ddf9845ef5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltentriesgt"></a>&lt;entries&gt; の &lt;add&gt;
以前に定義されたクライアント エンドポイントにフィルターをマップするルーティング エントリを表します。 このフィルターに一致するメッセージは、この宛先に送信されます。  
  
 \<system.serviceModel >  
\<ルーティング >  
\<routingTables >  
\<テーブル >  
\<エントリ >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|backupList|エンドポイントのバックアップ リストへの参照を指定する文字列。|  
|エンドポイント|`filterName` 属性で指定されたフィルターに一致するメッセージを受信するクライアント エンドポイントへの参照を指定する文字列。|  
|filterName|フィルター要素への参照を指定する文字列。|  
|priority|このエントリの優先順位を指定する整数。<br /><br /> ルーティング テーブルのエントリは、優先順位に基づいて評価されます。0 が最下位の優先順位です。 特定の優先順位について、すべてのエントリが同時に評価されます。現在の優先順位について一致するエントリが見つからない場合は、次の優先順位が評価されます。<br /><br /> この値はオプションです。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ルーティング >](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|ルーティング マッピング エントリを含む構成セクション。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
