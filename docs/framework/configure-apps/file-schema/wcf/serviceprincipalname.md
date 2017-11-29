---
title: "&lt;サービス プリンシパル名&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3f3b85d3-20f2-4cd8-8a6a-ee18befbd165
caps.latest.revision: "6"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e472c7fcfd57341074489a75f7954be38291523b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="ltserviceprincipalnamegt"></a>&lt;サービス プリンシパル名&gt;
サービスの ID をサービス プリンシパル名 (SPN) により指定します。  
  
 SPN を設定の詳細については、次を参照してください。[サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)です。  
  
 \<id >  
\<サービス プリンシパル名 >  
  
## <a name="syntax"></a>構文  
  
```xml  
<servicePrincipalName value = "String" />  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|value|クライアントがサービスのインスタンスを一意に識別する名前です。 フォレストの複数のコンピューターに 1 つのサービスの複数のインスタンスをインストールする場合、各インスタンスには独自の SPN が必要です。 クライアントが認証に使用できる複数の名前がある場合は、指定したサービス インスタンスに複数の SPN を設定できます。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|クライアントで認証するサービスの ID を指定します。|  
  
## <a name="remarks"></a>コメント  
 この ID を持つエンドポイントに接続するセキュリティで保護された [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] クライアントは、エンドポイントの SSPI 認証を実行するときに SPN を使用します。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.IdentityElement>  
 <xref:System.ServiceModel.EndpointAddress>  
 <xref:System.ServiceModel.EndpointAddress.Identity%2A>  
 <xref:System.ServiceModel.SpnEndpointIdentity>  
 [サービス Id と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)
