---
title: "&lt;scopedCertificates&gt; 要素"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c7b6fc35-d4b2-4c18-98bd-83e09591f1d3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 719a52fb1a0f558bda2b337e1402f8aecafc6b8d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ltscopedcertificatesgt-element"></a>&lt;scopedCertificates&gt; 要素
認証用の (範囲指定された) 特定のサービスにより提供される X.509 証明書のコレクションを表します。 このコレクションは一般に、フェデレーション シナリオでセキュリティ トークン サービスのサービス証明書を指定するために使用されます。  
  
 \<システムです。ServiceModel >  
\<ビヘイビアー >  
endpointBehaviors セクション  
\<動作 >  
\<clientCredentials >  
\<serviceCertificate >  
\<scopedCertificates > 要素  
\<追加 > 要素を\<scopedCertificates >  
  
## <a name="syntax"></a>構文  
  
```xml  
<scopedCertificates>  
      <add findValue="String"  
                storeLocation="CurrentUser/LocalMachine"  
                storeName=" CurrentUser/LocalMachine"  
                targetUri="string"  
            x509Type="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />   
</scopedCertificates>   
```  
  
## <a name="attributes-and-elements"></a>属性および要素  
 以降のセクションでは、属性、子要素、および親要素について説明します。  
  
### <a name="attributes"></a>属性  
 なし。  
  
### <a name="child-elements"></a>子要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)|範囲指定された証明書のコレクションに X.509 証明書を追加します。|  
  
### <a name="parent-elements"></a>親要素  
  
|要素|説明|  
|-------------|-----------------|  
|[\<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)|クライアントに対してサービスを認証する際に使用される証明書を指定します。|  
  
## <a name="remarks"></a>コメント  
 このコレクションを使用すると、クライアントは、通信するサービスの URL に基づいて、使用するサービス証明書を構成できます。 これは、クライアントが複数のサービス (エンド サービスと中間セキュリティ トークン サービス) と通信している可能性がある発行済みトークンのシナリオで特に便利です。 証明書に基づくメッセージ セキュリティを使用したバインドにおいて、この証明書を使用してサービスへのメッセージを暗号化します。サービスがクライアントへの応答に署名する際には、この証明書を使用することが要求されます。  
  
 バインディングにサービスの証明書が必要で、サービスの URL に対する特定の証明書が ScopedCertificates 内に存在しない場合は、既定の証明書が使用されます。  
  
 詳細についてを参照してください「証明書のスコープ」の[する方法: フェデレーション クライアントを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)です。  
  
## <a name="example"></a>例  
 ドメイン名が http://www.contoso.com であるエンドポイントと HTTP プロトコルを経由して通信するときに使用するクライアントのサービス証明書を指定する例を次に示します。  
  
```xml  
<serviceCertificate>  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
</serviceCertificate>  
```  
  
## <a name="see-also"></a>参照  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement.ScopedCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElementCollection>  
 <xref:System.ServiceModel.Configuration.X509ScopedServiceCertificateElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.ScopedCertificates%2A>  
 [証明書の使用](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [方法 : フェデレーション クライアントを作成する](../../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopedcertificates-element.md)  
 [クライアントのセキュリティ保護](../../../../../docs/framework/wcf/securing-clients.md)  
 [サービスおよびクライアントのセキュリティ保護](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
