---
title: "WSE 3.0 Web サービスの WCF への移行 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: 16
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 16
---
# WSE 3.0 Web サービスの WCF への移行
WSE 3.0 Web サービスを [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] に移行する利点には、パフォーマンスの向上と、追加のトランスポート、追加のセキュリティ シナリオ、および WS-* 仕様のサポートなどがあります。 WSE 3.0 から [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行した Web サービスでは、パフォーマンスが最大 200% から 400% 向上する可能性があります。 サポートされているトランスポートの詳細については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください[トランスポートの選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)します。 サポートされるシナリオの一覧については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)します。 サポートされている仕様の一覧については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください[Web サービス プロトコルの相互運用性ガイド](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)します。  
  
 以下の各セクションでは、WSE 3.0 Web サービスの特定の機能を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行する方法についてのガイドラインを示します。  
  
## <a name="general"></a>全般  
 WSE 3.0 アプリケーションと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションには、ネットワーク レベルの相互運用性と、共通の用語セットが含まれます。 WSE 3.0 アプリケーションと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションは、両方がサポートする WS-* 仕様セットに基づき、ネットワーク レベルで相互運用できます。 WSE 3.0 アプリケーションや [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションの展開時には、WSE の設定不要なセキュリティ アサーションの名前や認証モードなど、共通の用語セットが使用されます。  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と ASP.NET または WSE 3.0 のプログラミング モデルの間には、類似した側面が数多くありますが、同一ではありません。 詳細については、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]プログラミング モデルを参照してください[基本的なプログラミング ライフ サイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)します。  
  
> [!NOTE]
>  WSE Web サービスを WCF に移行する、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールは、クライアントを生成するために使用できます。 ただし、このクライアントには、WCF サービスの開始点として使用できるインターフェイスとクラスも含まれます。 生成されるインターフェイスが、 <xref:System.ServiceModel.OperationContractAttribute>されたコントラクトのメンバーに適用される属性、 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A>プロパティに設定`*`します。 WSE クライアントは、この設定では、Web サービスを呼び出して、次の例外がスローされます。 **Web.services3.responseprocessingexception:: WSE910: 応答メッセージの処理中に、エラーが発生したと内部例外で、エラーが見つかります**します。 これを防ぐには、設定、 <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A>のプロパティ、 <xref:System.ServiceModel.OperationContractAttribute>属性以外に`null`などの値`http://Microsoft.WCF.Documentation/ResponseToOCAMethod`です。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>ポリシー ファイルを使用してセキュリティ保護される WSE 3.0 Web サービス  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、構成ファイルを使用してサービスをセキュリティで保護できます。この機構は、WSE 3.0 ポリシー ファイルと似ています。 WSE 3.0 でポリシー ファイルを使用して Web サービスをセキュリティ保護するときは、設定不要のセキュリティ アサーションまたはカスタム ポリシー アサーションを使用します。 設定不要のセキュリティ アサーションは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] セキュリティ バインド要素の認証モードに厳密にマップされます。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 認証モードと WSE 3.0 の設定不要のセキュリティ アサーションには、同一または類似の名前が付けられているだけでなく、これらは同じ資格情報の種類を使用してメッセージをセキュリティ保護します。 たとえば、WSE 3.0 の設定不要の `usernameForCertificate` セキュリティ アサーションは、`UsernameForCertificate` の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 認証モードにマップされます。 WSE 3.0 の設定不要の `usernameForCertificate` セキュリティ アサーションを使用する最小ポリシーが、カスタム バインディングの `UsernameForCertificate` の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 認証モードにどのようにマップされるかを次のコード例に示します。  
  
 **WSE 3.0**  
  
```  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 ポリシー ファイルで指定されている WSE 3.0 Web サービスのセキュリティ設定を [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] に移行するには、構成ファイルでカスタム バインディングを作成し、設定不要のセキュリティ アサーションを同等の認証モードに設定する必要があります。 さらに、WSE 3.0 クライアントがサービスと通信するときに 2004 年 8 月版の WS-Addressing 仕様を使用するように、カスタム バインディングを構成する必要もあります。 移行後の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが WSE 3.0 クライアントと通信する必要がなく、等価のセキュリティの保持のみが必要な場合は、カスタム バインディングを作成する代わりに [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] システム定義のバインディングと適切なセキュリティ設定を使用することを考慮してください。  
  
 WSE 3.0 ポリシー ファイルと [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] の同等のカスタム バインディングとの対応関係を次の表に示します。  
  
|WSE 3.0 の設定不要のセキュリティ アサーション|WCF のカスタム バインド構成|  
|----------------------------------------|--------------------------------------|  
|<usernameOverTransportSecurity></usernameOverTransportSecurity>\>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|<mutualCertificate10Security></mutualCertificate10Security>\>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|<usernameForCertificateSecurity></usernameForCertificateSecurity>\>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|<anonymousForCertificateSecurity></anonymousForCertificateSecurity>\>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|<kerberosSecurity></kerberosSecurity>\>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|<mutualCertificate11Security></mutualCertificate11Security>\>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF でカスタム バインディングの作成の詳細については、次を参照してください。[カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)します。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>アプリケーション コードを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WSE 3.0 と [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のいずれを使用する場合でも、構成ではなくアプリケーション コードでセキュリティ要件を指定できます。 WSE 3.0 でこれを行うには、`Policy` クラスの派生クラスを作成してから、`Add` メソッドを呼び出して要件を追加します。 セキュリティ要件を指定するコードの詳細については、次を参照してください。[方法: セキュリティで保護された Web サービスなしを使用して、ポリシー ファイル](http://go.microsoft.com/fwlink/?LinkId=73747)します。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]をコードでセキュリティ要件を指定してのインスタンスを作成する、 <xref:System.ServiceModel.Channels.BindingElementCollection>クラスし、インスタンスの追加、 <xref:System.ServiceModel.Channels.SecurityBindingElement>に、 <xref:System.ServiceModel.Channels.BindingElementCollection>します。 セキュリティ アサーション要件は、の静的認証モード ヘルパー メソッドを使用して設定された、 <xref:System.ServiceModel.Channels.SecurityBindingElement>クラスです。 使用してコードでのセキュリティ要件の指定の詳細については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください[方法: SecurityBindingElement を作成するカスタム バインディングを使用して、](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)と[方法: 指定の認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)します。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 カスタム ポリシー アサーション  
 WSE 3.0 には、2 種類のカスタム ポリシー アサーションがあります。一方は SOAP メッセージをセキュリティで保護し、もう一方は SOAP メッセージをセキュリティで保護しません。 SOAP メッセージをセキュリティで保護されたポリシー アサーションは WSE 3.0 から派生`SecurityPolicyAssertion`クラスと同等の概念[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]は、 <xref:System.ServiceModel.Channels.SecurityBindingElement>クラスです。  
  
 注意すべき重要な点は、WSE 3.0 の設定不要のセキュリティ アサーションは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 認証モードのサブセットであるということです。 WSE 3.0 でカスタム ポリシー アサーションを既に作成している場合は、同等の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 認証モードが存在する可能性があります。 たとえば、WSE 3.0 は、設定不要の `UsernameOverTransport` セキュリティ アサーションと等価な CertificateOverTransport セキュリティ アサーションを提供しませんが、クライアントを認証するために X.509 証明書を使用します。 このシナリオ用の独自のカスタム ポリシー アサーションを定義していれば、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] によって移行が容易になります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]静的認証モードの利点を構成するヘルパー メソッドを実行できるように、このシナリオでは、認証モードを定義、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Channels.SecurityBindingElement>します。  
  
 ない場合、 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 、SOAP メッセージをセキュリティで保護するカスタム ポリシー アサーションと等価な認証モードからクラスを派生する<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、 <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>または<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]クラスし、等価なバインド要素を指定します。 詳細については、次を参照してください。[方法: SecurityBindingElement を作成するカスタム バインディングを使用して、](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。  
  
 SOAP メッセージを保護していないカスタム ポリシー アサーションを変換するには、次を参照してください。[フィルタ リング](../../../../docs/framework/wcf/feature-details/filtering.md)サンプルとサンプル[カスタム メッセージ インターセプター](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)します。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 カスタム セキュリティ トークン  
 カスタム トークンを作成するための [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] プログラミング モデルは、WSE 3.0 と異なります。 WSE でカスタム トークンを作成する方法については、「[カスタム セキュリティ トークンの作成](http://go.microsoft.com/fwlink/?LinkID=73750)します。 カスタム トークンを作成する方法について[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]を参照してください[方法: カスタム トークンを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 カスタム トークン マネージャー  
 カスタム トークン マネージャーを作成するためのプログラミング モデルは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] と WSE 3.0 で異なります。 カスタム トークン マネージャーとカスタム セキュリティ トークンに必要な他のコンポーネントを作成する方法の詳細については、「[方法: カスタム トークンを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
> [!NOTE]
>  カスタムの `UsernameToken` セキュリティ トークン マネージャーを既に作成している場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、カスタム セキュリティ マネージャーを作成するよりも簡単に認証ロジックを指定する機構が提供されています。 詳細については、次を参照してください。[方法: カスタム ユーザー名およびパスワード検証を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)します。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM エンコードされた SOAP メッセージを使用する WSE 3.0 Web サービス  
 WSE 3.0 アプリケーションと同様に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションでは、MTOM メッセージ エンコードを構成で指定できます。 この設定を移行するには、追加、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) 、サービスのバインドにします。 WSE 3.0 での MTOM エンコードの指定方法と、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での等価な MTOM エンコードの指定方法を、次のコード例に示します。  
  
 **WSE 3.0**  
  
```  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE メッセージング API を使用する WSE 3.0 アプリケーション  
 クライアントと Web サービス間でやり取りされる XML に直接アクセスするために WSE メッセージング API が使用されている場合は、"Plain Old XML" (POX) を使用するようにアプリケーションを変換できます。 POX の詳細については、次を参照してください。 [POX アプリケーションとの相互運用](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)します。 WSE メッセージング API の詳細については、次を参照してください。[送信および受信 SOAP メッセージを使用して WSE メッセージング API](http://go.microsoft.com/fwlink/?LinkID=73755)します。  
  
## <a name="transports"></a>トランスポート  
  
### <a name="tcp"></a>TCP  
 既定では、TCP トランスポートを使用して SOAP メッセージを送信する WSE 3.0 クライアントおよび Web サービスは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のクライアントおよび Web サービスと相互運用できません。 このような非互換性は、TCP プロトコルで使用されるフレームの違いとパフォーマンス上の理由に起因します。 ただし、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサンプルでは、WSE 3.0 と相互運用するカスタム TCP セッションの実装方法を詳しく示しています。 詳細については、このサンプルは、次を参照してください。[トランスポート: WSE 3.0 TCP 相互運用性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)します。  
  
 指定する、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]アプリケーションは、TCP トランスポートを使用して、使用して、 [ <> \</> \>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)します。  
  
### <a name="custom-transport"></a>カスタム トランスポート  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] において WSE 3.0 カスタム トランスポートに相当するのは、チャネル拡張です。 チャネル拡張機能の作成に関する詳細については、「[チャネル レイヤーの拡張](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)します。  
  
## <a name="see-also"></a>関連項目  
 [基本的なプログラミング ライフ サイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)   
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)   
 [方法: SecurityBindingElement を使用してカスタム バインディングを作成します。](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)   
 [方法: 指定した認証モード用の SecurityBindingElement を作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)