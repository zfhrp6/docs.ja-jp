---
title: '&lt;dns&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 81819dae-4825-43b7-bccd-f16d2d3d2f06
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4c7585cfa85d805a3d1454b0c16e38eee297280a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltdnsgt"></a>&lt;dns&gt;
予想されるサーバーの ID を指定します。 この ID は、同じ値を持つ DNS がサーバーの証明書に含まれていれば、X509 証明書の認証モードで有効です。 さらに、SPN に同じ値があれば、Windows 認証モードでも有効です。  
  
 要素の値の設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。  
  
 \<id >  
\<dns >  
  
## <a name="syntax"></a>構文  
  
```xml  
<dns value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|value|証明書の DNS です。 DNS は、IP ベースのネットワーク上でコンピューターを特定するために使用される業界標準のプロトコルです。 ユーザーが表示名をなど覚え[http://go.microsoft.com/fwlink/?prd=10929](http://go.microsoft.com/fwlink/?prd=10929)または[http://go.microsoft.com/fwlink/?LinkID=96165](http://go.microsoft.com/fwlink/?LinkID=96165)、207.46.131.137 などの数値ベースのアドレスよりも簡単です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|クライアントで認証するサービスの ID を指定します。|  
  
## <a name="example"></a>例  
 次の構成コードは、サーバーの認証に使用される X.509 証明書の DNS を指定します。  
  
```xml  
<identity>  
  <dns value = "www.cohowinery.com" />  
</identity>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.DnsEndpointIdentity>  
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
