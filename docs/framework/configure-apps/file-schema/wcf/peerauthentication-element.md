---
title: "&lt;peerAuthentication&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 09a8a9ff-e395-42f6-8ceb-9d44bdc1cbe1
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ddcb8b5199fc46cf3e5058650168131bb457545d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ltpeerauthenticationgt-element"></a>&lt;peerAuthentication&gt; 要素
ピアツーピア クライアントの認証オプションを指定します。  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]ピア ツー ピア プログラミングを参照してください[ピア ツー ピア ネットワー キング](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)です。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
\<endpointBehaviors >  
\<動作 >  
\<clientCredentials >  
\<ピア >  
\<PeerAuthentication >  
  
## <a name="syntax"></a>構文  
  
```xml  
<peerAuthentication  
customCertificateValidatorType = "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|`customCertificateValidatorType`|省略可能な文字列。 カスタム型の検証に使用される型およびアセンブリです。 `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。|  
|`certifcateValidationMode`|省略可能な列挙体です。 資格情報の検証に使用される 3 つのモードのいずれかを指定します。 `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。 既定値は、`ChainTrust` です。|  
|`revocationMode`|省略可能な列挙体です。 証明書失効リスト (CRL) のチェックに使用されるモードのいずれかです。 既定値は、`Online` です。|  
|`trustedStoreLocation`|省略可能な列挙体です。 2 つのシステム格納場所 (`LocalMachine` または `CurrentUser`) のいずれかです。 この値は、サービス証明書がクライアントにネゴシエートされるときに使用されます。 に対して検証が実行、**信頼されたユーザー**指定されたストアの場所に格納します。 既定値は、`CurrentUser` です。|  
  
## <a name="customcertificatevalidatortype-attribute"></a>customCertificateValidatorType 属性  
  
|値|説明|  
|-----------|-----------------|  
|String|タイプ名およびアセンブリと、タイプの検索に使用される他のデータを指定します。 少なくとも、名前空間とタイプ名が必要です。 省略可能な情報は、アセンブリ名、バージョン番号、カルチャ、および公開キー トークンです。|  
  
## <a name="certificatevalidationmode-attribute"></a>certificateValidationMode 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|`None`、`PeerTrust`、`ChainTrust`、`PeerOrChainTrust`、`Custom` のいずれかの値にします。 既定値は、`ChainTrust` です。<br /><br /> 詳細については、次を参照してください。[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。|  
  
## <a name="revocationmode-attribute"></a>revocationMode 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|`NoCheck`、`Online`、`Offline` のいずれかの値にします。 既定値は、`Online` です。<br /><br /> 詳細については、次を参照してください。[証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)です。|  
  
## <a name="trustedstorelocation-attribute"></a>trustedStoreLocation 属性  
  
|値|説明|  
|-----------|-----------------|  
|列挙型|`LocalMachine` または `CurrentUser` のいずれかの値にします。 既定値は、`CurrentUser` です。 クライアント アプリケーションがシステム アカウントで実行されている場合、証明書は通常 `LocalMachine` の下にあります。 クライアント アプリケーションがユーザー アカウントで実行されている場合、証明書は通常 `CurrentUser` の下にあります。|  
  
### <a name="child-elements"></a>子要素  
 なし。  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<ピア >](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|ピア サービスに対するクライアントの認証に使用される資格情報を指定します。|  
  
## <a name="remarks"></a>コメント  
 `<authentication>` 要素は、<xref:System.ServiceModel.Security.X509PeerCertificateAuthentication> クラスに対応します。 この要素は、メッシュ内の近隣ノード間の認証時に呼び出される検証コントロールを指定します。 新しいピアが近隣ノードとの接続を確立しようとするとき、自身の資格情報を応答側のピアに渡します。 リモート パーティの資格情報を検証するために、応答側の検証が呼び出されます。 メッシュ内でピア接続が確立されるたびに、両方のピアが相互に認証されます。つまり、双方の検証が呼び出されます。  
  
## <a name="example"></a>例  
 次のコードは、証明書検証モードを `PeerOrChainTrust` に設定します。  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
     <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
     <peerAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
     <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
</endpointBehaviors>  
```  
  
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
