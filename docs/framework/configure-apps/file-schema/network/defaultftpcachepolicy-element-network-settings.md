---
title: '&lt;defaultFtpCachePolicy&gt;要素 (ネットワーク設定)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e4ea16c925114d4ad4054af5f340c764ed6fe4fd
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
ms.locfileid: "32743148"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultFtpCachePolicy&gt;要素 (ネットワーク設定)
かどうか FTP キャッシュがアクティブであり、既定のキャッシュ ポリシーの説明について説明します。  
  
 \<configuration>  
\<system.net>  
\<requestCaching >  
\<defaultFtpCachePolicy >  
  
## <a name="syntax"></a>構文  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`policyLevel`|FTP のキャッシュ ポリシーを指定します。 既定値は `Default` です。|  
  
## <a name="policylevel-attribute"></a>policyLevel 属性  
  
|[値]|説明|  
|-----------|-----------------|  
|`Default`|リソースが新しい場合は、コンテンツの長さが、精度は有効期限、変更、およびコンテンツの長さの属性が存在は、キャッシュされたリソースを返します。|  
|`BypassCache`|サーバーからリソースを返します。|  
|`CacheOnly`|コンテンツの長さが存在し、エントリのサイズと一致する場合は、キャッシュされたリソースを返します。|  
|`CacheIfAvailable`|コンテンツの長さが指定されたエントリのサイズと一致する場合は、キャッシュされたリソースを返しますそれ以外の場合、リソースは、サーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|キャッシュされたリソースのタイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースを返しますそれ以外の場合、リソース サーバーからダウンロード、キャッシュに格納されているを呼び出し元に返されます。|  
|`Reload`|サーバーからリソースをダウンロード、キャッシュに格納し、呼び出し元にリソースを返します。|  
|`NoCacheNoStore`|キャッシュされたリソースが存在する場合は削除されます。 リソースは、サーバーからダウンロードされ、呼び出し元に返されます。|  
|`Revalidate`|タイムスタンプは、サーバー上のリソースのタイムスタンプと同じ場合は、キャッシュされたリソースのコピーを使用して、要求に応じます。それ以外の場合、リソースはサーバーからダウンロード、呼び出し元に表示される、キャッシュに格納されています。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|ネットワーク要求のキャッシュ メカニズムを制御します。|  
  
## <a name="remarks"></a>コメント  
  
## <a name="example"></a>例  
 次の例は、FTP キャッシュのポリシーを指定する方法を示しています。`NoCacheNoStore`です。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [ネットワーク設定スキーマ](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
