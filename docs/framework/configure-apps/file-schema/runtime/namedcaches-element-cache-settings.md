---
title: "&lt;namedCaches&gt; 要素 (キャッシュ設定) | Microsoft Docs"
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
  - "<namedCaches> 要素"
  - "キャッシュ [.NET Framework], 構成"
  - "namedCaches 要素"
ms.assetid: 6bd4fbc5-55a6-4dc4-998b-cdcc7e023330
caps.latest.revision: 14
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 14
---
# &lt;namedCaches&gt; 要素 (キャッシュ設定)
名前付き <xref:System.Runtime.Caching.MemoryCache> インスタンスの構成設定のコレクションを指定します。  <xref:System.Runtime.Caching.Configuration.MemoryCacheSection.NamedCaches%2A> プロパティは、構成ファイルの 1 つ以上の `namedCaches` 要素の構成設定のコレクションを参照します。  
  
## 構文  
  
```  
<namedCaches>  
  <add name="default"   
</namedCaches>  
```  
  
## 型  
 `None`  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`CacheMemoryLimitMegabytes`|<xref:System.Runtime.Caching.MemoryCache> のインスタンスについて許可される最大サイズ \(MB 単位\) を指定する整数値。  既定値は 0 です。これは、<xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ変更ヒューリスティックが既定で使用されることを意味します。|  
|`Name`|キャッシュの名前。|  
|`PhysicalMemoryLimitPercentage`|キャッシュで使用できる物理的にインストールされたコンピューター メモリの最大パーセンテージを指定する 0 ～ 100 の整数値。  既定値は 0 です。これは、<xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ変更ヒューリスティックが既定で使用されることを意味します。|  
|`PollingInterval`|キャッシュの実装が、現在のメモリ負荷を、キャッシュ インスタンスに設定されているメモリ制限の絶対値および割合と比較する時間間隔を示す値。  この値は "HH:MM:SS" の形式で入力されます。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/runtime/add-element-for-namedcaches.md)|名前付きキャッシュをメモリ キャッシュの `namedCaches` コレクションに追加します。|  
|[\<&#91;clear&#93;\>](../../../../../docs/framework/configure-apps/file-schema/runtime/clear-element-for-namedcaches.md)|メモリ キャッシュの `namedCaches` コレクションを削除します。|  
|[\<削除\>](../../../../../docs/framework/configure-apps/file-schema/runtime/remove-element-for-namedcaches.md)|メモリ キャッシュの `namedCaches` コレクションから、名前付きキャッシュ エントリを削除します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<memoryCache\>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づいたキャッシュの構成に使用される要素を定義します。|  
  
## 解説  
 Web.config ファイルのメモリ キャッシュ構成セクションには、`namedCaches` コレクションの `add`、`remove`、および `clear` 属性を含めることができます。  各 `namedCaches` エントリは、`name` 属性によって一意に識別されます。  
  
 アプリケーション構成ファイル内の情報を参照することにより、メモリ キャッシュ エントリのインスタンスを取得できます。  既定では、既定のキャッシュ インスタンスのみが構成ファイルにエントリを持ちます。  既定のキャッシュ インスタンスは、<xref:System.Runtime.Caching.MemoryCache.Default%2A> プロパティから返されるインスタンスです。  
  
 名前属性を "default" に設定した場合、要素では既定のメモリ キャッシュ インスタンスが使用されます。  
  
## 使用例  
 `name` 属性を "default" に設定して、キャッシュの名前を既定のキャッシュ エントリ名に設定する方法を次の例に示します。  
  
 `cacheMemoryLimitMegabytes` 属性と `physicalMemoryPercentage` 属性は 0 に設定されています。  これらの属性を 0 に設定すると、<xref:System.Runtime.Caching.MemoryCache> クラスの自動サイズ変更ヒューリスティックが使用されます。  キャッシュの実装は、現在のメモリ負荷を、メモリ制限の絶対値および割合と 2 分ごとに比較します。  
  
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
 [\<memoryCache\> 要素 \(キャッシュ設定\)](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)