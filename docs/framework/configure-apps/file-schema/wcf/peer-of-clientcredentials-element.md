---
title: "&lt;clientCredentials&gt; 要素の &lt;peer&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 505bd987-0042-4622-b68e-94f439729d53
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: accd6c261a393da3ffcffd261d6603d20b8fcb3d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltpeergt-of-ltclientcredentialsgt-element"></a>&lt;clientCredentials&gt; 要素の &lt;peer&gt;
ピアツーピア クライアントの認証時に使用される資格情報を指定します。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors >  
\<動作 >  
\<clientCredentials >  
\<ピア >  
  
## <a name="syntax"></a>構文  
  
```xml  
<peer>  
  <certificate/>  
  <peerAuthentication/>  
  <messageSenderAuthentication/>  
</peer>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<証明書 >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md)|ピアツーピア クライアントのメッセージの署名と暗号化に使用する X.509 証明書を指定します。 である必要があります。|  
|[\<peerAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/peerauthentication-element.md)|ピア クライアントの認証オプションを指定します。|  
|[\<messageSenderAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/messagesenderauthentication-element.md)|メッセージ送信者の認証オプションを指定します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## <a name="remarks"></a>コメント  
 この構成要素は、ピア ノードがメッシュ内の他のノードに対して自身を認証するために使用する資格情報と、ピア ノードが他のピア ノードを認証するために使用する認証設定を指定します。 詳細については、次を参照してください。[ピア チャネル メッセージ認証](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)と[ピア チャネル アプリケーションのセキュリティで保護する](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)です。  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Peer%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>  
 <xref:System.ServiceModel.Security.PeerCredential>  
 [ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)  
 [ピア チャネル メッセージの認証](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [ピア チャネル カスタム認証](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [セキュリティによるピア チャネル アプリケーションの保護](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
