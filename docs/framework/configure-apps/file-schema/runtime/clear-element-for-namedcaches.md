---
title: "&lt;namedCaches&gt; の &lt;clear&gt; 要素 | Microsoft Docs"
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
  - "<namedCaches> の <clear> 要素"
  - "<namedCaches> の clear 要素"
ms.assetid: ea01a858-65da-4348-800f-5e3df59d4d79
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;namedCaches&gt; の &lt;clear&gt; 要素
メモリ キャッシュの `namedCaches` コレクションのすべての `namedCache` エントリを消去します。  
  
## 構文  
  
```  
<namedCaches>  
    <clear name="default" />  
    <!-- child elements -->  
 </namedCaches>  
```  
  
## 型  
 `Type`  
  
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
 `clear` 要素は、メモリ キャッシュの名前付きキャッシュ コレクション内のすべての `namedCache` エントリを消去します。  `add` 要素を使用する前に `clear` 要素を使用すると、コレクション内に他の名前付きキャッシュがないことを確認するために、新しい名前付きキャッシュ エントリを追加できます。  
  
## 参照  
 [\<namedCaches\> 要素 \(キャッシュ設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)