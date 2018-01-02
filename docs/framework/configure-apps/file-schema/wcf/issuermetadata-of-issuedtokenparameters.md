---
title: "&lt;issuedTokenParameters&gt; の &lt;issuerMetadata&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1a85ca37-496d-4fa3-8d44-d6c9383d735c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ee0f6b2abe6ddfa81f236da47425ae586b56f0ca
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltissuermetadatagt-of-ltissuedtokenparametersgt"></a>&lt;issuedTokenParameters&gt; の &lt;issuerMetadata&gt;
\<system.serviceModel >  
\<バインド >  
\<customBinding >  
\<バインド >  
\<セキュリティ >  
\<issuedTokenParameters >  
\<issuerMetadata >  
  
## <a name="syntax"></a>構文  
  
```xml  
<issuerMetaData address=String"/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|address|必ず指定します。 エンドポイントのアドレスを指定する文字列。 アドレスは、絶対 URI にする必要があります。 既定値は空の文字列です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ヘッダー >](../../../../../docs/framework/configure-apps/file-schema/wcf/headers-element.md)|アドレス ヘッダーのコレクション。|  
|[\<id >](../../../../../docs/framework/configure-apps/file-schema/wcf/identity.md)|メッセージを交換する他のエンドポイントによるエンドポイントの認証を可能にする ID です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<issuedTokenParameters >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenparameters.md)|フェデレーション セキュリティのシナリオで発行されるセキュリティ トークンのパラメーターを指定します。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters>  
 <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [サービス ID と認証](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [カスタム バインドを使用したセキュリティ機能](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [フェデレーションと発行済みトークン](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [バインディングの拡張](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [カスタム バインディング](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [カスタム バインド セキュリティ](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
