---
title: "&lt;namespaceTable&gt; の &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 394657abcebb42192fb7a8b57b0402bcacf37693
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltnamespacetablegt"></a>&lt;namespaceTable&gt; の &lt;add&gt;
名前空間とプレフィックスのマッピングを含む構成要素を表します。これは、ルーティングの XPath フィルターで使用されます。  
  
 \<system.serviceModel >  
\<ルーティング >  
\<namespaceTable >  
\<add>  
  
## <a name="syntax"></a>構文  
  
```xml  
   <routing>   <namespaceTable>  
     <add namespace="String" prefix="String" />    </namespaceTable></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|namespace|名前空間を示す文字列。|  
|prefix|この名前空間のプレフィックスを示す文字列。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<namespaceTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Routing.Configuration.NamespaceElement?displayProperty=nameWithType>    
