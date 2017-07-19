---
title: "&lt;defaultFtpCachePolicy&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultFtpCachePolicy> 要素"
  - "defaultFtpCachePolicy 要素"
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;defaultFtpCachePolicy&gt; 要素 (ネットワーク設定)
FTP キャッシュがアクティブであるかどうかを指定し、既定のキャッシュ ポリシーを記述します。  
  
## 構文  
  
```  
< defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`policyLevel`|FTP キャッシュ ポリシーを指定します。  既定値は `Default` です。|  
  
## policyLevel 属性  
  
|値|説明|  
|-------|--------|  
|`Default`|キャッシュされているリソースが最新であり、content length が正しく、expiration 属性、modification 属性、および content length 属性が指定されている場合、キャッシュされているリソースを返します。|  
|`BypassCache`|サーバーからリソースを返します。|  
|`CacheOnly`|content length が指定されており、エントリのサイズに一致する場合、キャッシュされているリソースを返します。|  
|`CacheIfAvailable`|content length が指定されており、エントリのサイズに一致する場合には、キャッシュされているリソースを返します。その他の場合には、対象のリソースをサーバーからダウンロードした上で、呼び出し元に返します。|  
|`Revalidate`|キャッシュされているリソースのタイムスタンプが、サーバー上のリソースのタイムスタンプと等しい場合には、キャッシュされているリソースを返します。その他の場合には、対象のリソースをサーバーからダウンロードし、キャッシュに格納し、呼び出し元に返します。|  
|`Reload`|対象のリソースをサーバーからダウンロードし、キャッシュに格納した上で、呼び出し元に返します。|  
|`NoCacheNoStore`|キャッシュされたリソースが存在する場合は削除されます。  サーバーからリソースをダウンロードし、呼び出し元に返します。|  
|`Revalidate`|タイムスタンプがサーバーのリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して要求に応じます。それ以外の場合は、リソースがサーバーからダウンロードされ、呼び出し元に提示され、キャッシュに格納されます。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|ネットワーク要求のキャッシュ機構を制御します。|  
  
## 解説  
  
## 使用例  
 次のコード例は、`NoCacheNoStore` の FTP キャッシュ ポリシーを指定する方法を示しています。  
  
```  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        Level="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.Cache>   
 <xref:System.Net.WebRequest>   
 <xref:System.Net.Cache.RequestCacheLevel>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)