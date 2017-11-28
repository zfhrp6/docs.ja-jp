---
title: '&lt;compositeDuplex&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 725004d1-ce88-4405-a220-78e89844f81f
caps.latest.revision: "14"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: f9f82d4b6ac69e0edc0a2ad2cddfd89ee6ac72db
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltcompositeduplexgt"></a>&lt;compositeDuplex&gt;
サービスがメッセージをクライアントに返送するためのエンドポイントをクライアントが公開する必要がある場合に使用される、バインド要素を定義します。  
  
 \<system.serviceModel >  
\<バインド >  
\<customBinding >  
\<バインド >  
\<compositeDuplex >  
  
## <a name="syntax"></a>構文  
  
```xml  
<compositeDuplex clientBaseAddress="URI" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|clientBaseAddress|二重モードのバック チャネルのアドレスを設定する URI。 サービスは、このアドレスを使用して、クライアントへのアクセス、接続の確立を行います。<br /><br /> この属性が設定されていないかどうか、既定のアドレス"`full qualified name+default port\TemporaryIndigoAddress\guid`"が生成されます。 既定値は、`null` です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/misc/binding.md)|カスタム バインドのすべてのバインド機能を定義します。|  
  
## <a name="remarks"></a>コメント  
 たとえば HTTP のように、この構成要素はネイティブでの二重通信を許可しないトランスポートで使用されます。 これとは対照的に、TCP では、二重通信がネイティブで許可されているので、クライアントにメッセージを返信するためにこのバインディング要素をサービスで使用する必要はありません。  
  
 クライアントは、サービスのアドレスを公開して、アクセスおよび接続の確立ができるようにする必要があります。 このクライアント アドレスは、`clientBaseAddress` 属性によって提供されます。 ClientBaseAddress がユーザーによって明示的に設定されていない場合は、WCF (Windows Communication Foundation) によって自動的に生成されます。  
  
## <a name="example"></a>例  
  
```xml  
<compositeDuplex clientBaseAddress="http://www.contoso.com" />  
```  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.CompositeDuplexElement>  
 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [カスタム バインド](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
