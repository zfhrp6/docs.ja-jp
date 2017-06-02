---
title: "&lt;namedCaches&gt; の &lt;add&gt; 要素 | Microsoft Docs"
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
  - "<namedCaches> の <add> 要素"
  - "<namedCaches> の add 要素"
ms.assetid: ce2a63a8-c829-4742-a6ea-72ee5d89f169
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;namedCaches&gt; の &lt;add&gt; 要素
メモリ キャッシュの `namedCaches` コレクションに `namedCache` エントリを追加します。  
  
## 構文  
  
```  
<namedCaches>  
    <add name="default" />  
      <!-- child elements -->  
 </namedCaches>  
```  
  
## 型  
 `None`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|||  
|-|-|  
|Attribute|説明|  
|`CacheMemoryLimitMegabytes`|<xref:System.Runtime.Caching.MemoryCache> のインスタンスについて許可される最大サイズ \(MB 単位\) を指定する整数値。  既定値は 0 です。これは、<xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ変更ヒューリスティックが既定で使用されることを意味します。|  
|`Name`|キャッシュの名前。|  
|`PhysicalMemoryLimitPercentage`|キャッシュで使用できる物理的にインストールされたコンピューター メモリの最大パーセンテージを指定する 0 ～ 100 の整数値。  既定値は 0 です。これは、<xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ変更ヒューリスティックが既定で使用されることを意味します。|  
|`PollingInterval`|キャッシュの実装が、現在のメモリ負荷を、キャッシュ インスタンスに設定されているメモリ制限の絶対値および割合と比較する時間間隔を示す値。  この値は "HH:MM:SS" の形式で入力されます。|  
  
### 子要素  
 `None`  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<namedCaches\>](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)|名前付き <xref:System.Runtime.Caching.MemoryCache> インスタンスの構成設定のコレクションが含まれます。|  
  
## 解説  
 `add` 要素は、メモリ キャッシュの `namedCaches` コレクションにエントリを追加します。  `add` 要素を使用する前に [clear](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md) 要素を使用すると、コレクション内に他の名前付きキャッシュがないことを確認できます。  この要素は、machine.config ファイルと Web.config ファイルで使用できます。  
  
## 使用例  
 メモリ キャッシュの `namedCaches`  コレクションに既定の `namedCache` エントリの設定を定義する方法を次の例に示します。  
  
```  
<configuration>  
  
  <system.runtime.caching>  
    <memoryCache>  
      <namedCaches>  
          <add name="default"   
               cacheMemoryLimitMegabytes="0"   
               physicalMemoryPercentage="0"  
               pollingInterval="00:02:00" />  
      </namedCaches>  
    </memoryCache>  
  </system.runtime.caching>  
  
</configuration>  
```  
  
## 参照  
 [\<namedCaches\> 要素 \(キャッシュ設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/namedcaches-element-cache-settings.md)