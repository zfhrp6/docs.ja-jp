---
title: "&lt;namespaceTable&gt; の &lt;add&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: cf7b5b75-63bd-49a6-abac-4bfdab377e36
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;namespaceTable&gt; の &lt;add&gt;
名前空間とプレフィックスのマッピングを含む構成要素を表します。これは、ルーティングの XPath フィルターで使用されます。  
  
## 構文  
  
```vb  
  
<routing>  
   <namespaceTable>  
     <add namespace="String" prefix="String" />   
   </namespaceTable>  
</routing>  
  
```  
  
```csharp  
  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|namespace|名前空間を示す文字列。|  
|prefix|この名前空間のプレフィックスを示す文字列。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<namespaceTable\>](../../../../../docs/framework/configure-apps/file-schema/wcf/namespacetable.md)|名前空間とプレフィックスのマッピングを含む要素セットを定義する構成セクションを表します。これは、ルーティングの XPath フィルターで使用されます。|  
  
## 参照  
 [System.ServiceModel.Routing.Configuration.NamespaceElement](assetId:///System.ServiceModel.Routing.Configuration.NamespaceElement?qualifyHint=False&amp;autoUpgrade=True)