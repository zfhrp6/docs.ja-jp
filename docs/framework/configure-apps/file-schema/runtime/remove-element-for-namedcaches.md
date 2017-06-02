---
title: "&lt;namedCaches&gt; の &lt;remove&gt; 要素 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "namedCaches の <remove> 要素"
  - "namedCaches の remove 要素"
ms.assetid: 24211ea5-163e-4fe5-aed8-004d8499760c
caps.latest.revision: 10
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 10
---
# &lt;namedCaches&gt; の &lt;remove&gt; 要素
メモリ キャッシュの `namedCaches` コレクションから、名前付きキャッシュ エントリを削除します。  
  
## 構文  
  
```  
<namedCaches>  
    <remove name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## 型  
 `None`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 `None`  
  
### 子要素  
 `None`  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|名前付き <xref:System.Runtime.Caching.MemoryCache> インスタンスの構成設定のコレクションが含まれます。|  
  
## 解説  
 `remove` 要素は、メモリ キャッシュの名前付きキャッシュ コレクションから `namedCache` エントリを削除します。  
  
## 参照  
 [\<namedCaches\> 要素 \(キャッシュ設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)