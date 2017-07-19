---
title: "&lt;system.runtime.caching&gt; 要素 (キャッシュ設定) | Microsoft Docs"
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
  - "<system.runtime.caching> 要素"
  - "キャッシュ [.NET Framework], 構成"
  - "system.runtime.caching 要素"
ms.assetid: 9b44daee-874a-4bd1-954e-83bf53565590
caps.latest.revision: 10
author: "rpetrusha"
ms.author: "ronpet"
manager: "wpickett"
caps.handback.revision: 10
---
# &lt;system.runtime.caching&gt; 要素 (キャッシュ設定)
構成ファイル内の `memoryCache` エントリを使用して既定のメモリ内の <xref:System.Runtime.Caching.ObjectCache> の実装の構成を提供します。  
  
 \<configuration\>  
\<system.runtime.caching\>  
  
## 構文  
  
```  
<system.runtime.caching >  
   <!-- child elements -->  
</system.runtime.caching >  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
 `None`  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[\<memoryCache\>](../../../../../docs/framework/configure-apps/file-schema/runtime/memorycache-element-cache-settings.md)|<xref:System.Runtime.Caching.MemoryCache> クラスに基づくキャッシュを構成するために使用される要素を定義します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|共通言語ランタイムおよび [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] アプリケーションで使用されるすべての構成ファイルのルート要素です。|  
  
## 解説  
 この名前空間のクラスは、ASP.NET のキャッシュ機能と同様のキャッシュ機能を使用する方法を提供しますが、`System.Web` アセンブリに依存しません。 詳細については、「[.NET Framework アプリケーションでのキャッシュ](../../../../../docs/framework/performance/caching-in-net-framework-applications.md)」を参照してください。  
  
> [!NOTE]
>  <xref:System.Runtime.Caching> 名前空間の出力キャッシュ機能と型は、[!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)] の新機能です。  
  
## 使用例  
 次の例では、<xref:System.Runtime.Caching.MemoryCache> クラスを元にしたキャッシュの構成方法を紹介します。 この例では、メモリ キャッシュ用の `namedCaches` エントリのインスタンスの構成を方法を示します。 キャッシュの名前は、`name` 属性を "default" に設定することによって、既定のキャッシュ エントリ名に設定されます。  
  
 `cacheMemoryLimitMegabytes` 属性および `physicalMemoryPercentage` 属性はゼロに設定されます。 これらの属性をゼロに設定すると、<xref:System.Runtime.Caching.MemoryCache> の自動サイズ調整ヒューリスティックが既定で使用されることになります。 キャッシュの実装では、現在のメモリ負荷と絶対およびパーセントのメモリ制限を 2 分ごとに比較する必要があります。  
  
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