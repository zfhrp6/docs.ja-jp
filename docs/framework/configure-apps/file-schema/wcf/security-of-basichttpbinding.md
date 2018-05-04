---
title: '&lt;basicHttpBinding&gt; の &lt;security&gt;'
ms.date: 03/30/2017
ms.assetid: 6432708d-5465-4bd9-bfc2-466742db99cb
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: ddf120d5462c7fcb0774e29fa18e80b71727acd8
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/03/2018
---
# <a name="ltsecuritygt-of-ltbasichttpbindinggt"></a>&lt;basicHttpBinding&gt; の &lt;security&gt;
セキュリティ機能を定義、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。  
  
 \<system.ServiceModel >  
\<bindings>  
\<basicHttpBinding>  
\<binding>  
\<セキュリティ >  
  
## <a name="syntax"></a>構文  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">  
   <transport  
      clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"  
      proxyCredentialType="Basic/Digest/None/Ntlm/Windows"  
      realm="string" />  
   <message  
      algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />  
</security>  
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
  
|属性|説明|  
|---------------|-----------------|  
|モード|省略可能です。 使用されるセキュリティの種類を指定します。 既定値は、`None` です。 この属性は <xref:System.ServiceModel.BasicHttpSecurityMode> 型です。|  
  
## <a name="mode-attribute"></a>mode 属性  
  
|値|説明|  
|-----------|-----------------|  
|なし|メッセージの数は、転送中にセキュリティ保護されていません。|  
|Transport|セキュリティは、HTTPS トランスポートを使用して提供されます。 SOAP メッセージは、HTTPS を使用したセキュリティで保護されます。 サービスは、サービスの X.509 証明書を使用してクライアントに認証されます。 クライアントは、提供される ClientCredentialType を使用して認証されます。 参照してください、 [\<トランスポート >](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)です。|  
|メッセージ|セキュリティは、SOAP メッセージ セキュリティを使用して確保されます。 既定では、本文は暗号化および署名されます。 このバインディングの場合、サーバー証明書をクライアントの帯域外で提供するように要求されます。 このバインディングの唯一の有効な `ClientCredentialType` は、`Certificate` です。|  
|TransportWithMessageCredential|整合性、機密性、およびサーバー認証は、トランスポート セキュリティによって提供されます。 クライアント認証は、SOAP メッセージ セキュリティで提供されます。 このモードは、ユーザーがユーザー名およびパスワードを使用して認証し、メッセージ転送をセキュリティで保護するために既存の HTTP が配置されている場合に関連します。|  
|TransportCredentialOnly|このモードは、メッセージの整合性と機密性を提供しません。 http ベースのクライアント認証を提供します。 このモードを使用するときは、十分に注意する必要があります。 トランスポート セキュリティが他の方法 (IPSec など) で提供され、クライアント認証だけが [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] インフラストラクチャで提供されている環境で使用する必要があります。|  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-basichttpbinding.md)|基本 HTTP サービスのトランスポート セキュリティ設定を定義します。 この要素は、<xref:System.ServiceModel.HttpTransportSecurity> に対応しています。|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-of-basichttpbinding.md)|基本 HTTP サービスのメッセージ セキュリティ設定を定義します。 この要素は、<xref:System.ServiceModel.BasicHttpMessageSecurity> に対応しています。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|バインド|バインド要素、 [ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)です。|  
  
## <a name="remarks"></a>コメント  
 既定では、SOAP メッセージはセキュリティで保護されず、クライアントは認証されません。 この要素を使用すると、`basicHttpBinding` 要素に追加のセキュリティ設定を構成できます。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.ServiceModel.BasicHttpBinding.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpBindingElement.Security%2A>  
 <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement>  
 <xref:System.ServiceModel.BasicHttpSecurity>  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [資格情報の種類の選択](../../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [バインディング](../../../../../docs/framework/wcf/bindings.md)  
 [システムが提供するバインディングの構成](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [バインディングを使用して、Windows Communication Foundation サービスとクライアントを構成するには](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [\<binding>](../../../../../docs/framework/misc/binding.md)
