---
title: "&lt;messageSenderAuthentication&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: ea62fc06-55fb-42e0-aa2b-8867bdf4b415
caps.latest.revision: 10
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 10
---
# &lt;messageSenderAuthentication&gt;
メッセージ送信者により使用されるピア証明書の認証設定を指定します。  
  
## 構文  
  
```  
  
<messageSenderAuthentication  
   customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
   certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
   revocationMode="NoCheck/Online/Offline"  
   trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## 属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### 属性  
  
|属性|説明|  
|--------|--------|  
|`certificateValidationMode`|省略可能な列挙体です。  資格情報の検証に使用される 5 つのモードのいずれかを指定します。  この属性は <xref:System.ServiceModel.Security.X509CertificateValidationMode> 型です。  `Custom` に設定されている場合、`customCertificateValidator` も指定する必要があります。|  
|`customCertificateValidatorType`|省略可能な文字列。  ユーザー設定タイプの検証に使用されるタイプおよびアセンブリを指定します。  `certificateValidationMode` が `Custom` に設定されている場合は、この属性を設定する必要があります。  この属性は <xref:System.IdentityModel.Selectors.X509CertificateValidator> 型です。  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] には、信頼されたユーザーのストアに対してピア証明書を検証する既定のピア証明書検証が用意されており、  証明書が有効なルートまでつながっていることを検証します。  カスタム検証を実装して別の動作を指定したり、この属性を使用してカスタム検証を指定することができます。|  
|`revocationMode`|省略可能な列挙体です。  証明書失効モードを指定します。  この属性は <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> 型です。  システムは、ピア証明書を失効証明書リストで検索して、それが失効していないことを検証します。  このチェックは、オンラインで、またはキャッシュされた失効リストをチェックする方法で実行されます。  失効チェックは、この属性を NoCheck に設定することにより無効にできます。|  
|`trustedStoreLocation`|省略可能な列挙体です。  [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] セキュリティ システムによりピア証明書を検証する、信頼されているユーザー ストアを指定します。  この属性は <xref:System.Security.Cryptography.X509Certificates.StoreLocation> 型です。|  
  
### 子要素  
 なし。  
  
### 親要素  
  
|要素|説明|  
|--------|--------|  
|[\<peer\>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-servicecredentials.md)|ピア ノードの現在の資格情報を指定します。|  
  
## 解説  
 メッセージ認証を選択した場合は、この要素を構成する必要があります。  出力チャネルでは、各メッセージは、[\<certificate\>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md) が提供する認証を使用して署名されます。  すべてのメッセージは、アプリケーションに配信される前に、この要素の `customCertificateValidatorType` 属性で指定した検証を使用してメッセージ資格情報がチェックされます。  検証は、資格情報を受け入れることも拒否することもできます。  
  
## 参照  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>   
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>   
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>   
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>   
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [ピアツーピア ネットワーク](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)   
 [Peer Channel Message Authentication](http://msdn.microsoft.com/ja-jp/80e73386-514e-4c30-9e4a-b9ca8c173a95)   
 [Peer Channel Custom Authentication](http://msdn.microsoft.com/ja-jp/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)   
 [セキュリティによるピア チャネル アプリケーションの保護](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)