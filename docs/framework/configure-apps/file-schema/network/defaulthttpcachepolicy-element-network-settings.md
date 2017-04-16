---
title: "&lt;defaultHttpCachePolicy&gt; 要素 (ネットワーク設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultHttpCachePolicy> 要素"
  - "defaultHttpCachePolicy 要素"
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;defaultHttpCachePolicy&gt; 要素 (ネットワーク設定)
HTTP キャッシュがアクティブであるかどうかを指定し、既定のキャッシュ ポリシーを記述します。  
  
## 構文  
  
```  
< defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss"|"minValue"  
  maximumAge  ="d.hh:mm:ss"|"maxValue"  
  maximumStale="d.hh:mm:ss"|"maxValue"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`maximumAge`|キャッシュされたオブジェクトを期限切れであるとマークするまでの最大時間間隔を指定します。|  
|`maximumStale`|キャッシュされたオブジェクトを期限切れであるとマークするまでの、計算されたフレッシュネス時間からの最大経過時間を指定します。|  
|`minimumFresh`|キャッシュされたオブジェクトをフレッシュであると判断する最小時間を指定します。|  
|`policyLevel`|キャッシュ ポリシーが自動であるか、またはキャッシュを迂回するかを指定します。  既定値は `BypassCache` です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|ネットワーク要求のキャッシュ機構を制御します。|  
  
## 解説  
 `policyLevel` 属性の値は、`BypassCache` または `Default` です。  
  
 `maximumAge`、`maximumStale`と `minimumFresh` 要素の値は *d*形式の明示的な時間間隔のいずれかです。*hh*:*mm*:*ss* \(日、時、分、秒\)、または適切 `minValue` 定数または `maxValue`。  
  
## 構成ファイル  
 この要素は、アプリケーション構成ファイルまたはマシン構成ファイル \(Machine.config\) で使用できます。  
  
## 使用例  
 次のコード例は、minimumFresh に 6 時間を指定し、maximumAge に 2 日間を指定し、maximumStale に 4 時間を指定する方法を示しています。  
  
```  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy>  
        <set minimumFresh="0.06:00:00" />  
        <set maximumAge  ="2.00:00:00" />  
        <set maximumStale="0.04:00:00" />  
      </defaultHttpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.Cache>   
 <xref:System.Net.WebRequest>   
 <xref:System.Net.Cache.RequestCacheLevel>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)