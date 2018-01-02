---
title: "&lt;netPeerTcpBinding&gt; の &lt;transport&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c44d86d2-1160-44d7-9c7a-297b12eccc7f
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ed3e933e1c3468a09b1d6b089b4abf52dad85017
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="lttransportgt-of-ltnetpeertcpbindinggt"></a>&lt;netPeerTcpBinding&gt; の &lt;transport&gt;
使用する場合は、トランスポート レベルのセキュリティの設定を指定、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。  
  
 \<システムです。ServiceModel >  
\<バインド >  
\<netPeerTcpBinding >  
\<バインド >  
\<セキュリティ >  
\<トランスポート >  
  
## <a name="syntax"></a>構文  
  
```xml  
<netPeerTcpBinding>  
    <binding>  
        <security>  
            <transport credentialType="Certificate/Password" />  
        </security>         
    </binding>  
</netPeerTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|credentialType|省略可能です。 ピア トランスポートにより送信されるメッセージの検証に使用される資格情報の種類を指定します。 この属性は <xref:System.ServiceModel.PeerTransportCredentialType> 型です。|  
  
## <a name="credentialtype-attribute"></a>credentialType 属性  
  
|値|説明|  
|-----------|-----------------|  
|証明書|ピア チャネル トランスポートの認証には X 509 証明書が必要です。|  
|[Password]|ピア チャネル トランスポートの認証には正しいパスワードが必要です。|  
  
### <a name="child-elements"></a>子要素  
 なし  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<セキュリティ >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|セキュリティ設定を定義、 [ \<netPeerTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)です。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.PeerTransportSecurityElement>  
 <xref:System.ServiceModel.PeerSecuritySettings.Transport%2A>  
 <xref:System.ServiceModel.Configuration.PeerSecurityElement.Transport%2A>  
 <xref:System.ServiceModel.PeerTransportSecuritySettings>  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<バインド >](../../../../../docs/framework/misc/binding.md)
