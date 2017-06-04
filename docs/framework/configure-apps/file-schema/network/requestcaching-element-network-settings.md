---
title: "&lt;requestCaching&gt; 要素 (ネットワーク設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<requestCaching> 要素"
  - "requestCaching 要素"
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;requestCaching&gt; 要素 (ネットワーク設定)
ネットワーク要求のキャッシュ機構を制御します。  
  
## 構文  
  
```  
  
      <requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss""  
  <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
  <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|Attribute|説明|  
|---------------|--------|  
|`isPrivateCache`|キャッシュが、異なるユーザーの情報間で分離を提供するかどうかを指定します。  既定値は `true` です。  この値は、中間層アプリケーションの場合は `false` です。|  
|`disableAllCaching`|キャッシュがすべての Web 応答に対して無効になっているため、プログラムでオーバーライドできないことを指定します。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列挙値のいずれか。  既定値は `BypassCache` です。|  
|`unspecifiedMaximumAge`|コンテンツを期限切れであるとマークするまでの、既定の時間を指定します。|  
  
## policyLevel 属性  
  
|値|説明|  
|-------|--------|  
|`Default`|キャッシュされているリソースが最新であり、content length が正しく、expiration 属性、modification 属性、および content length 属性が指定されている場合、キャッシュされているリソースを返します。|  
|`BypassCache`|サーバーからリソースを返します。|  
|`CacheOnly`|content length が指定されており、エントリのサイズに一致する場合、キャッシュされているリソースを返します。|  
|`CacheIfAvailable`|content length が指定されており、エントリのサイズに一致する場合には、キャッシュされているリソースを返します。その他の場合には、対象のリソースをサーバーからダウンロードした上で、呼び出し元に返します。|  
|`Revalidate`|キャッシュされているリソースのタイムスタンプが、サーバー上のリソースのタイムスタンプと等しい場合には、キャッシュされているリソースを返します。その他の場合には、対象のリソースをサーバーからダウンロードし、キャッシュに格納した上で、呼び出し元に戻します。|  
|`Reload`|対象のリソースをサーバーからダウンロードし、キャッシュに格納した上で、呼び出し元に返します。|  
|`NoCacheNoStore`|キャッシュされたリソースが存在する場合は削除されます。  サーバーからリソースをダウンロードし、呼び出し元に返します。|  
|`Revalidate`|キャッシュされているリソースのタイムスタンプが、サーバー上のリソースのタイムスタンプと一致する場合には、キャッシュされているリソースのコピーを返して、要求を満たします。その他の場合には、対象のリソースをサーバーからダウンロードして呼び出し元に返し、キャッシュに格納します。|  
  
### 子要素  
  
|要素|説明|  
|--------|--------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|省略可能な要素です。<br /><br /> HTTP キャッシュがアクティブであるかどうかを指定し、既定のキャッシュ ポリシーを記述します。|  
|[\<defaultFtpCachePolicy\> 要素 \(ネットワーク設定\)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|省略可能な要素です。<br /><br /> FTP キャッシュがアクティブであるかどうかを指定し、既定のキャッシュ ポリシーを記述します。|  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## 使用例  
 すべてのキャッシュを無効にする方法を次のコード例に示します。  
  
```  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## 参照  
 <xref:System.Net.Cache?displayProperty=fullName>   
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)