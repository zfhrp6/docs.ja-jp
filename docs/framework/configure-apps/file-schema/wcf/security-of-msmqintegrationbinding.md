---
title: "&lt;msmqIntegrationBinding&gt; の &lt;security&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ae5c68a8-14a2-4c6e-b9e0-3e94e3e9135e
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 92b496833cebbefbb97dd576ef3549d15b489aae
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltsecuritygt-of-ltmsmqintegrationbindinggt"></a>&lt;msmqIntegrationBinding&gt; の &lt;security&gt;
メッセージ キュー (MSMQ) 統合チャネルのトランスポート セキュリティ設定を定義します。  
  
 \<システムです。ServiceModel >  
\<バインド >  
msmqIntegrationBinding  
\<バインド >  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<msmqIntegrationBinding>  
   <binding>   
       <security mode="None/Transport">  
         <transport msmqAuthenticationMode="None/Windows/Certificate"  
            msmqEncryptionAlgorithm="RC4Stream/AES"  
            msmqProtectionLevel="None/Sign/EncryptAndSign"  
            msmqSecureHashAlgorithm="MD5/SHA1/SHA256/SHA512" />  
          <message  algorithmSuite="Aes128/Aes192/Aes256/Rsa15Aes128/ Rsa15Aes256/TripleDes"  
                        clientCredentialType="None/Windows/UserName/Certificate/CardSpace"  
            defaultProtectionLevel="None/Sign/EncryptAndSign" />  
       </security>  
   </binding>  
</msmqIntegrationBinding>   
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|モード|メッセージ キュー統合チャネルの整合性、機密性、および認証を制御するセキュリティの種類を指定します。 以下の値が有効です。<br /><br /> -なし: 無効になりますセキュリティ。<br />-Transport: 保護と認証は、トランスポートによって提供されます。 これは、2 つのキュー マネージャー間のメッセージ セキュリティに適用されます。 アプリケーションとキュー マネージャーとの間にセキュリティは提供されません。 既存の Msmq アプリケーションは、この種類のセキュリティ モードと機能的に等価です。<br /><br /> 既定値は `Transport` です。 この属性は <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurityMode> 型です。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<トランスポート >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-msmqintegrationbinding.md)|メッセージ キュー統合トランスポートのセキュリティ設定を定義します。 この要素は <xref:System.ServiceModel.Configuration.MsmqTransportSecurityElement> 型です。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<バインド >](../../../../../docs/framework/misc/binding.md)|バインド要素、 [ \<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)です。|  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationSecurityElement>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.MsmqIntegrationBindingElement.Security%2A>  
 <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationSecurity>  
 [WCF のキュー](../../../../../docs/framework/wcf/feature-details/queues-in-wcf.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<バインド >](../../../../../docs/framework/misc/binding.md)  
 [\<msmqIntegrationBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)
