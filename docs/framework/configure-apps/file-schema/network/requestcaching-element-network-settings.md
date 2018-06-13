---
title: '&lt;requestCaching&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 9c0c8d80182931f9ac14e687a337b7be55a5a9a5
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743434"
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching&gt;要素 (ネットワーク設定)
ネットワーク要求のキャッシュ メカニズムを制御します。  
  
 \<configuration>  
\<system.net>  
\<requestCaching >  
  
## <a name="syntax"></a>構文  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`isPrivateCache`|キャッシュはさまざまなユーザーの情報との間の分離を提供するかどうかを指定します。 既定値は `true` です。 この値は、`false`中間層アプリケーションです。|  
|`disableAllCaching`|キャッシュとが無効にすべての Web 応答のプログラムではオーバーライドできませんを指定します。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列挙値の値の 1 つ。 既定値は `BypassCache` です。|  
|`unspecifiedMaximumAge`|その後、コンテンツを期限切れとマークは、既定の時間を指定します。|  
  
## <a name="policylevel-attribute"></a>policyLevel 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`Default`|リソースが新しい場合は、コンテンツの長さが、精度は有効期限、変更、およびコンテンツの長さの属性が存在は、キャッシュされたリソースを返します。|  
|`BypassCache`|サーバーからリソースを返します。|  
|`CacheOnly`|コンテンツの長さが存在し、エントリのサイズと一致する場合は、キャッシュされたリソースを返します。|  
|`CacheIfAvailable`|コンテンツの長さが指定されたエントリのサイズと一致する場合は、キャッシュされたリソースを返しますそれ以外の場合、リソースは、サーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|キャッシュされたリソースのタイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返しますそれ以外の場合、リソースは、キャッシュに格納されている、サーバーからダウンロードされ、呼び出し元に返されます。|  
|`Reload`|サーバーからリソースをダウンロード、キャッシュに格納し、呼び出し元にリソースを返します。|  
|`NoCacheNoStore`|キャッシュされたリソースが存在する場合は削除されます。 リソースは、サーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|タイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して、要求に応じます。それ以外の場合、リソースは、呼び出し元に表示される、サーバーからダウンロードされ、キャッシュに格納されます。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|省略可能な要素です。<br /><br /> かどうか HTTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。|  
|[\<defaultFtpCachePolicy > 要素 (ネットワーク設定)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|省略可能な要素です。<br /><br /> かどうか FTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|.NET Framework がネットワークに接続する方法を指定するための設定が含まれています。|  
  
## <a name="example"></a>例  
 次の例では、すべてのキャッシュを無効にする方法を示します。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
