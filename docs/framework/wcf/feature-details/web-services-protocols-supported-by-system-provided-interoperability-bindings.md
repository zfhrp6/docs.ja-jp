---
title: "システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WS-プロトコル"
  - "Web サービス プロトコル"
  - "Windows Communication Foundation、Web サービス プロトコル"
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
caps.latest.revision: 39
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 39
---
# システム標準の相互運用性バインディングがサポートしている Web サービス プロトコル
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] は、Web サービス仕様と呼ばれる一連の仕様をサポートする Web サービスと相互運用できるように構築されています。 相互運用性のベスト プラクティスについては、サービスの構成を簡略化する[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]3 つの相互運用可能なシステム指定のバインディングが導入されています: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=fullName>、 <xref:System.ServiceModel.WSHttpBinding?displayProperty=fullName>、および<xref:System.ServiceModel.WSDualHttpBinding?displayProperty=fullName>します。 Advancement 構造化情報標準 (OASIS) 標準では、組織との相互運用性の[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]1 つの相互運用可能なシステム指定のバインディングが含まれています: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=fullName>します。 メタデータの公開の[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]2 つの相互運用可能なシステム指定のバインディングが含まれています: [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)と[ <> \</> \>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)します。 このトピックでは、システム指定の相互運用可能なバインディングがサポートする仕様を示します。  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>basicHttpBinding、wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding の各バインディングでサポートされる Web サービス プロトコル  
  
### <a name="all-bindings"></a>すべてのバインディング  
 The [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), and [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) bindings support the following protocols.  
  
> [!NOTE]
>  メタデータの公開に使用するバインディングについては、このトピックで後述する「システム指定のメタデータ バインディング」を参照してください。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`、`WSHttpBinding`、および `WS2007HttpBinding` は、HTTP トランスポートおよび HTTPS トランスポートを使用します。|  
|メッセージング|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`、`wsHttpBinding`、および `ws2007HttpBinding` は、MTOM (Message Transmission Optimization Mechanism) をサポートしています。 既定では使用されません。 MTOM を使用するには、`messageEncoding` 属性を `"Mtom"` に設定します。<br /><br /> 例:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|メタデータ|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、サービスの記述に Web サービス記述言語 (WSDL) を使用します。|  
|メタデータ|WS-Policy|[Ws-policy](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ドメイン固有のアサーションと共に WS-Policy 仕様を使用して、サービス要件と機能を記述します。|  
|メタデータ|WS-Policy 1.5|[Ws-policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、ドメイン固有のアサーションと共に WS-Policy 仕様を使用して、サービス要件と機能を記述します。|  
|メタデータ|WS-PolicyAttachment|[Ws-policyattachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、Web サービス記述言語 (WSDL) のさまざまなスコープでポリシー式を関連付けるために、WS-PolicyAttachment を実装しています。|  
|メタデータ|WS-MetadataExchange|[Ws-metadataexchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> Basic Profile 1.1 に従って、`basicHttpBinding` 要素は SOAP 1.1 メッセージ プロトコルを実装しています。|  
|セキュリティ|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Basic Security Profile に従って、`basicHttpBinding` 要素は、ユーザー名/パスワードおよび X.509 ベースのセキュリティを実現するために、WSS (Web Services Security) SOAP Message Security 1.0 仕様を実装しています。<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security UsernameToken Profile 1.0|[WSS SOAP Message Security UsernameToken Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security X.509 証明書 Token Profile 1.0|[WSS SOAP Message Security X.509 証明書 Token Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding、ws2007HttpBinding、および wsDualHttpBinding  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|メッセージング|SOAP 1.2|[入門](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [メッセージング フレームワーク](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP バインディングを含む)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - コア](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`、`ws2007HttpBinding`、および `wsDualHttpBinding` は、非同期メッセージング、メッセージ相関、およびトランスポート中立のアドレス指定機構を有効にするために、W3C (World Wide Web Consortium) WS-Addressing 勧告を実装しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|メッセージング|WS-Addressing 1.0 - メタデータ|[Ws-addressing 1.0 メタデータ](http://www.w3.org/2007/05/addressing/metadata)1.2 (既定値) に設定されると ServiceMetadata 動作のポリシーのバージョンを設定してこのプロトコルのサポートが有効になっている、1.5 に設定されると、wsdl 記述は Ws-addressing の wsdl に準拠して、wsdl 記述は ws-addressing メタデータに準拠しています。<br /><br /> WCF は WS-Addressing ヘッダーの暗号化をサポートしていませんが、これは WS-* 仕様によって許可されています。|  
|セキュリティ|WSS SOAP Message Security 1.0|[WSS SOAP Message Security 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> `securityMode` 属性が "wsSecurityOverHttp" (既定) に設定され、`wsSecurity` 子要素を使用してパラメーターが構成されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security UsernameToken Profile 1.1|[WSS SOAP Message Security UsernameToken Profile 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username" に設定されている場合に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security X.509 Certificate Token Profile 1.1|[WSS SOAP Message Security X.509 証明書トークン Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Username"、"Certificate"、または "None" に設定されている場合に、メッセージを保護するために使用します。 また、`wsSecurity` 要素の `authenticationMode` 属性が "Certificate" に設定されている場合は、クライアント認証に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|セキュリティ|WSS SOAP Message Security Kerberos Token Profile 1.1|[WSS SOAP Message Security Kerberos トークン Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> `wsSecurity` 要素の `authenticationMode` 属性が "Windows" に設定されている場合に、認証とメッセージの保護に使用します。<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|セキュリティ|WS-SecureConversation|[Ws-secureconversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> `security/@mode` 属性が "Message" に設定され、`message/@establishSecurityContext` 属性が "true" (既定値) に設定されている場合に、セッションをセキュリティで保護するために使用します。|  
|セキュリティ|WS-Trust|[WS 信頼](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> WS-SecureConversation で使用されます (上記を参照)。|  
|信頼できるメッセージ機能|WS-ReliableMessaging|[Ws-reliablemessaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> バインディングが `reliableSession` を使用するように構成されている場合に使用します。<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|トランザクション|WS-AtomicTransaction|[Ws-atomictransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> トランザクション マネージャー間の通信に使用します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のクライアントとサービスは、常にローカル トランザクション マネージャーを使用します。|  
|トランザクション|WS-Coordination|[Ws-coordination 仕様](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> `flowTransactions` 属性が "Allowed" または "Required" に設定されている場合に、トランザクション コンテキストをフローするために使用します。<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding および ws2007FederationHttpBinding  
 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)と[ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)サード パーティがクライアントの認証に使用されるトークンを発行、フェデレーション シナリオをサポートする要素が導入されています。 `wsHttpBinding` で使用されるプロトコルに加えて、`wsFederationHttpBinding` では次のものを使用します。  
  
-   トークンを発行するための `WS-Trust`  
  
-   最も一般的に発行されるトークンの形式のための WSS SAML (Security Assertions Markup Language) Token Profile 1.0 および 1.1  
  
 例:  
  
```  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][フェデレーション](../../../../docs/framework/wcf/feature-details/federation.md)します。  
  
## <a name="system-provided-metadata-bindings"></a>システム指定のメタデータ バインディング  
 次の表に、によって公開されているシステム指定の相互運用可能なメタデータ バインディングによってサポートされるプロトコル、 <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=fullName>クラスです。  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)バインディングは、次のプロトコルをサポートします。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]このバインディングを使用して表示[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)します。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|メッセージング|SOAP 1.2|[入門](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [メッセージング フレームワーク](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP バインディングを含む)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - コア](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|メタデータ|WS-MetadataExchange|[Ws-metadataexchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)次のプロトコルをサポートしています。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]このバインディングを使用して表示[メタデータの公開](../../../../docs/framework/wcf/feature-details/publishing-metadata.md)します。  
  
|カテゴリ|プロトコル|仕様と用途|  
|--------------|--------------|-----------------------------|  
|Transport|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> トランスポート セキュリティは有効です。|  
|メッセージング|SOAP 1.2|[入門](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [メッセージング フレームワーク](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (HTTP バインディングを含む)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|メッセージング|Ws-addressing 2005/08|[Web Services Addressing 1.0 - コア](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Web Services Addressing 1.0 - SOAP](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|メタデータ|WS-MetadataExchange|[Ws-metadataexchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、XML スキーマ、WSDL、WS-Policy を取得するために WS-MetadataExchange が実装されています。|  
  
## <a name="see-also"></a>関連項目  
 [システム指定のバインディング](../../../../docs/framework/wcf/system-provided-bindings.md)   
 [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)   
 [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)   
 [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)   
 [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)   
 [<>\>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)