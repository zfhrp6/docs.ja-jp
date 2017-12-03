---
title: '&lt;peerAuthentication&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ad545e6f-f06e-4549-ac92-09d758d5c636
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 103ee50e86a809ee4a5e36451fd9e6b99fc3bb2c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeerauthenticationgt"></a>&lt;peerAuthentication&gt;
ピア ノードで使用されるピア証明書の認証設定を指定します。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
\<serviceBehaviors >  
\<動作 >  
\<serviceCredentials >  
\<ピア >  
\<peerAuthentication >  
  
## <a name="syntax"></a>構文  
  
```xml  
<peerAuthentication  
      customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
      certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
      revocationMode="NoCheck/Online/Offline"  
      trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`certificateValidationMode`|省略可能な列挙体です。 資格情報の検証に使用される 3 つのモードのいずれかを指定します。 この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。 `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。|  
|`customCertificateValidatorType`|省略可能な文字列。 ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。 `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。 この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] には、信頼されたユーザーのストアに対してピア証明書を検証する既定のピア証明書検証が用意されており、 証明書が有効なルートまでつながっていることを検証します。 カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。|  
|`revocationMode`|省略可能な列挙体です。 証明書失効モードを指定します。 この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。 システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。 このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。 失効チェックは、この属性を NoCheck に設定することにより無効にできます。|  
|`trustedStoreLocation`|省略可能な列挙体です。 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] セキュリティ システムによりピア証明書を検証する、信頼されているユーザー ストアを指定します。 この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ピア >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|ピア ノードの現在の資格情報を指定します。|  
  
## <a name="remarks"></a>コメント  
 `<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。 この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。 新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。 リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。 メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.PeerAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [ピア ツー ピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [ピア チャネル メッセージの認証](http://msdn.microsoft.com/en-us/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [ピア チャネル カスタム認証](http://msdn.microsoft.com/en-us/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [ピア チャネル アプリケーションのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
