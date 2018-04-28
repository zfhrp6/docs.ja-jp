---
title: システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
caps.latest.revision: 39
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 754915d5ba596b5121c47be3533ee679b4f9594b
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/28/2018
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、Web サービス仕様と呼ばれる一連の仕様をサポートする Web サービスと相互運用できるように構築されています。 サービス構成を簡略化して相互運用性のベスト プラクティスを実現するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>、<xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>、および <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType> の 3 つの相互運用可能なシステム指定のバインディングが導入されています。 OASIS (Organization for the Advancement of Structured Information Standards) 標準との相互運用性を実現するために、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] には <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType> という相互運用可能なシステム指定のバインディングがあります。 メタデータの公開の[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]2 つの相互運用可能なシステム指定のバインディングが含まれています: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)と[ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)です。 このトピックでは、システム指定の相互運用可能なバインディングがサポートする仕様を示します。  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>basicHttpBinding、wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding の各バインディングでサポートされる Web サービス プロトコル  
  
### <a name="all-bindings"></a>すべてのバインディング  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、および[ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)バインディング サポート、次のプロトコルです。  
  
> [!NOTE]
>  メタデータの公開に使用するバインディングについては、このトピックで後述する「システム指定のメタデータ バインディング」を参照してください。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`、`WSHttpBinding`、および `WS2007HttpBinding` は、HTTP トランスポートおよび HTTPS トランスポートを使用します。|  
|メッセージング|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`、`wsHttpBinding`、および `ws2007HttpBinding` は、MTOM (Message Transmission Optimization Mechanism) をサポートしています。 既定では使用されません。 MTOM を使用するには、`messageEncoding` 属性を `"Mtom"` に設定します。<br /><br /> 例:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|メタデータ|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービスの記述に Web サービス記述言語 (WSDL) を使用します。|  
|メタデータ|WS-Policy|[WS-Policy](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ドメイン固有のアサーションと共に WS-Policy 仕様を使用して、サービス要件と機能を記述します。|  
|メタデータ|WS-Policy 1.5|[Ws-policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ドメイン固有のアサーションと共に WS-Policy 仕様を使用して、サービス要件と機能を記述します。|  
|メタデータ|WS-PolicyAttachment|[WS-PolicyAttachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、Web サービス記述言語 (WSDL) のさまざまなスコープでポリシー式を関連付けるために、WS-PolicyAttachment を実装しています。|  
|メタデータ|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Basic Profile 1.1 に従って、`basicHttpBinding` 要素は SOAP 1.1 メッセージ プロトコルを実装しています。|  
|セキュリティ|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Basic Security Profile に従って、`basicHttpBinding` 要素は、ユーザー名/パスワードおよび X.509 ベースのセキュリティを実現するために、WSS (Web Services Security) SOAP Message Security 1.0 仕様を実装しています。<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP メッセージ セキュリティ UsernameToken Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|セキュリティ|WSS SOAP メッセージ セキュリティ X.509 証明書トークン プロファイル 1.0|[WSS SOAP メッセージ セキュリティ X.509 証明書トークン プロファイル 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.2|[入門](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [メッセージング フレームワーク](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [(HTTP バインドを含む) に対する](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - コア](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`、`ws2007HttpBinding`、および `wsDualHttpBinding` は、非同期メッセージング、メッセージ相関、およびトランスポート中立のアドレス指定機構を有効にするために、W3C (World Wide Web Consortium) WS-Addressing 勧告を実装しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|メッセージング|WS-Addressing 1.0 - メタデータ|[Ws-addressing 1.0 メタデータ](http://www.w3.org/2007/05/addressing/metadata)policyversion 1.2 (既定) に設定と ServiceMetadata 動作 - ポリシーのバージョンを設定してこのプロトコルのサポートが有効になっている、wsdl 説明は、Ws-addressing の wsdl に準拠するいるとバージョン 1.5 設定 policyversion、wsdl 説明は、ws アドレス指定のメタデータに準拠しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|セキュリティ|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> `securityMode` 属性が "wsSecurityOverHttp" (既定) に設定され、`wsSecurity` 子要素を使用してパラメーターが構成されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP メッセージ セキュリティ UsernameToken Profile 1.1|[WSS SOAP メッセージ セキュリティ UsernameToken Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username" に設定されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP メッセージ セキュリティ X.509 証明書トークン プロファイル 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username"、"Certificate"、または "None" に設定されている場合に、メッセージを保護するために使用します。 また、`wsSecurity` 要素の `authenticationMode` 属性が "Certificate" に設定されている場合は、クライアント認証に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP メッセージ Security Kerberos Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Windows" に設定されている場合に、認証とメッセージの保護に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|セキュリティ|WS-SecureConversation|[WS-SecureConversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> `security/@mode` 属性が "Message" に設定され、`message/@establishSecurityContext` 属性が "true" (既定値) に設定されている場合に、セッションをセキュリティで保護するために使用します。|  
|セキュリティ|WS-Trust|[Ws-trust](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation で使用されます (上記を参照)。|  
|信頼できるメッセージ機能|WS-ReliableMessaging|[WS-ReliableMessaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> バインディングが `reliableSession` を使用するように構成されている場合に使用します。<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|トランザクション|WS-AtomicTransaction|[WS-AtomicTransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> トランザクション マネージャー間の通信に使用します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のクライアントとサービスは、常にローカル トランザクション マネージャーを使用します。|  
|トランザクション|WS-Coordination|[Ws-coordination 仕様](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> `flowTransactions` 属性が "Allowed" または "Required" に設定されている場合に、トランザクション コンテキストをフローするために使用します。<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding および ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)と[ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) 3 つ目のフェデレーション シナリオでは、サポートを提供する要素が導入されましたパーティは、クライアントの認証に使用されるトークンを発行します。 `wsHttpBinding` で使用されるプロトコルに加えて、`wsFederationHttpBinding` では次のものを使用します。  
  
-   トークンを発行するための `WS-Trust`  
  
-   最も一般的に発行されるトークンの形式のための WSS SAML (Security Assertions Markup Language) Token Profile 1.0 および 1.1  
  
 例:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"   
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =   
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 詳細については、次を参照してください。[フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)です。  
  
## <a name="system-provided-metadata-bindings"></a>システム指定のメタデータ バインディング  
 次の表に、<xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> クラスによって公開される、システム指定の相互運用可能なメタデータ バインディングによってサポートされるプロトコルを示します。  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)バインディングは、次のプロトコルをサポートします。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] このバインディングを使用して参照してください[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)です。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|メッセージング|SOAP 1.2|[入門](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [メッセージング フレームワーク](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [(HTTP バインドを含む) に対する](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - コア](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|メタデータ|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)次のプロトコルをサポートします。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)] このバインディングを使用して参照してください[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)です。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> トランスポート セキュリティは有効です。|  
|メッセージング|SOAP 1.2|[入門](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [メッセージング フレームワーク](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [(HTTP バインドを含む) に対する](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - コア](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|メタデータ|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
  
## <a name="see-also"></a>関連項目  
 [システム標準のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
