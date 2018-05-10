---
title: WSE 3.0 Web サービスの WCF への移行
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: fea56d5737b47dabd5632477b7daed23fcfaf249
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>WSE 3.0 Web サービスの WCF への移行
移行する WSE 3.0 Web サービスには、Windows Communication Foundation (WCF) の利点を示しますパフォーマンスの向上とサポートの追加のトランスポート、追加のセキュリティ シナリオ、および ws-* 仕様です。 WSE 3.0 から WCF に移行する Web サービスは、最大で 200 ~ 400% パフォーマンスが向上発生があります。 WCF でサポートされているトランスポートの詳細については、次を参照してください。[トランスポート選択](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)です。 WCF によりサポートされるシナリオの一覧は、次を参照してください。[一般的なセキュリティ シナリオ](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md)です。 WCF でサポートされている仕様の一覧は、次を参照してください。 [Web サービス プロトコルの相互運用性ガイド](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md)です。  
  
 次のセクションでは、WSE 3.0 Web サービスの特定の機能を WCF に移行する方法のガイダンスを提供します。  
  
## <a name="general"></a>全般  
 WSE 3.0 と WCF アプリケーションには、ネットワーク レベルの相互運用性と共通の用語セットが含まれます。 WSE 3.0 と WCF アプリケーションは、ネットワーク レベルで相互運用 ws-のセットに基づく *、両方をサポートする仕様。 WSE 3.0 または WCF アプリケーションの開発時に WSE モードおよび認証モードで、設定不要のセキュリティ アサーションの名前などの用語の共通セットがあります。  
  
 WCF と ASP.NET 間のような多くの側面がありますが、WSE 3.0 のプログラミング モデルが異なるです。 WCF プログラミング モデルについての詳細については、「[基本的なプログラミング ライフ サイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)です。  
  
> [!NOTE]
>  WSE Web サービスを WCF に移行する、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)ツールは、クライアントを生成するために使用できます。 ただし、このクライアントには、WCF サービスの開始点として使用できるインターフェイスとクラスも含まれます。 生成されるインターフェイスの <xref:System.ServiceModel.OperationContractAttribute> 属性は、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> プロパティが `*` に設定されたコントラクトのメンバーに適用されます。 WSE クライアントは、この設定では、Web サービスを呼び出して、次の例外がスローされます**Web.services3.responseprocessingexception:: WSE910:、応答メッセージの処理中にエラーが発生し、内側のエラーを見つけることができます。例外**です。 このエラーを軽減するには、<xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> 属性の <xref:System.ServiceModel.OperationContractAttribute> プロパティを `null` 以外の値 (`http://Microsoft.WCF.Documentation/ResponseToOCAMethod` など) に設定します。  
  
## <a name="security"></a>セキュリティ  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>ポリシー ファイルを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WCF サービスは、構成ファイルを使用してサービスをセキュリティで保護して、その機構は WSE 3.0 ポリシー ファイルに似ています。 WSE 3.0 でポリシー ファイルを使用して Web サービスをセキュリティ保護するときは、設定不要のセキュリティ アサーションまたはカスタム ポリシー アサーションを使用します。 設定不要のセキュリティ アサーションは、WCF のセキュリティ バインド要素の認証モードに厳密にマップします。 だけでなく、WCF 認証モードと WSE 3.0 の設定不要のセキュリティ アサーションの名前は同じまたは、同様に、同じ資格情報の種類を使用してメッセージを保護します。 インスタンス、 `usernameForCertificate` WSE 3.0 の設定不要のセキュリティ アサーションにマップ、 `UsernameForCertificate` WCF での認証モードです。 次のコード例は、方法を使用する最小ポリシーを示しています。、 `usernameForCertificate` WSE 3.0 の設定不要のセキュリティ アサーションにマップする`UsernameForCertificate`WCF での認証モード、カスタム バインドにします。  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 WCF へのポリシー ファイルで指定されている WSE 3.0 Web サービスのセキュリティ設定を移行するには、構成ファイルで、カスタム バインディングを作成し、設定不要のセキュリティ アサーションは、同等の認証モードを設定する必要があります。 さらに、WSE 3.0 クライアントがサービスと通信するときに 2004 年 8 月版の WS-Addressing 仕様を使用するように、カスタム バインドを構成する必要もあります。 移行済みの WCF サービスが WSE 3.0 クライアントとの通信は不要し、等価のセキュリティを管理する必要があります、カスタム バインドを作成する代わりに適切なセキュリティ設定で、WCF のシステム定義バインディングの使用を検討します。  
  
 次の表は、WSE 3.0 ポリシー ファイルと WCF で同等のカスタム バインディング間のマッピングを一覧表示します。  
  
|WSE 3.0 の設定不要のセキュリティ アサーション|WCF のカスタム バインド構成|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 WCF でのカスタム バインドの作成の詳細については、次を参照してください。[カスタム バインド](../../../../docs/framework/wcf/extending/custom-bindings.md)です。  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>アプリケーション コードを使用してセキュリティ保護される WSE 3.0 Web サービス  
 WSE 3.0 または WCF を使用するかどうかは、構成ではなく、アプリケーション コードでセキュリティ要件を指定できます。 WSE 3.0 でこれを行うには、`Policy` クラスの派生クラスを作成してから、`Add` メソッドを呼び出して要件を追加します。 セキュリティ要件を指定するコードの詳細については、次を参照してください。[する方法: セキュリティで保護された Web サービスなしを使用して、ポリシー ファイル](http://go.microsoft.com/fwlink/?LinkId=73747)です。 WCF では、コードでセキュリティ要件を指定するのインスタンスを作成、<xref:System.ServiceModel.Channels.BindingElementCollection>クラスおよびインスタンスの追加、<xref:System.ServiceModel.Channels.SecurityBindingElement>を<xref:System.ServiceModel.Channels.BindingElementCollection>です。 セキュリティ アサーション要件は、<xref:System.ServiceModel.Channels.SecurityBindingElement> クラスの静的認証モード ヘルパー メソッドを使用して設定します。 WCF を使用してコードでセキュリティ要件を指定する方法の詳細については、次を参照してください[する方法: SecurityBindingElement 作成するカスタム バインドを使用して、](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)と[する方法: は指定されたため、SecurityBindingElement を作成します。認証モード](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)です。  
  
### <a name="wse-30-custom-policy-assertion"></a>WSE 3.0 カスタム ポリシー アサーション  
 WSE 3.0 には、2 種類のカスタム ポリシー アサーションがあります。一方は SOAP メッセージをセキュリティで保護し、もう一方は SOAP メッセージをセキュリティで保護しません。 WSE 3.0 から派生して、SOAP メッセージをセキュリティで保護するポリシー アサーション`SecurityPolicyAssertion`クラスと、WCF の概念と同じでは、<xref:System.ServiceModel.Channels.SecurityBindingElement>クラスです。  
  
 重要な注意点は、WSE 3.0 の設定不要のセキュリティ アサーション WCF 認証モードのサブセットであることです。 WSE 3.0 カスタム ポリシー アサーションを作成した場合と同等の WCF 認証モードである可能性があります。 たとえば、WSE 3.0 は、設定不要の `UsernameOverTransport` セキュリティ アサーションと等価な CertificateOverTransport セキュリティ アサーションを提供しませんが、クライアントを認証するために X.509 証明書を使用します。 このシナリオでは、独自のカスタム ポリシー アサーションを定義した場合は、WCF によって移行が容易です。 利用する静的認証モード ヘルパー メソッドを WCF を構成するために、WCF がこのシナリオでは、認証モードを定義<xref:System.ServiceModel.Channels.SecurityBindingElement>です。  
  
 SOAP メッセージを保護するカスタム ポリシー アサーションと等価である WCF 認証モードがない場合、派生クラスを<xref:System.ServiceModel.Channels.TransportSecurityBindingElement>、<xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>または<xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF クラスし、等価なバインド要素を指定します。 詳細については、次を参照してください。[する方法: SecurityBindingElement 作成するカスタム バインドを使用して、](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)です。  
  
 SOAP メッセージ セキュリティで保護するカスタム ポリシー アサーションを変換するには、次を参照してください。 [Filtering](../../../../docs/framework/wcf/feature-details/filtering.md)サンプルとサンプル[カスタム メッセージ インターセプター](../../../../docs/framework/wcf/samples/custom-message-interceptor.md)です。  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 カスタム セキュリティ トークン  
 カスタム トークンを作成するための WCF プログラミング モデルは、WSE 3.0 とは異なるです。 WSE でカスタム トークンを作成する方法については、次を参照してください。[カスタム セキュリティ トークンの作成](http://go.microsoft.com/fwlink/?LinkID=73750)です。 WCF では、カスタム トークンを作成する方法については、次を参照してください。[する方法: カスタム トークンを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 カスタム トークン マネージャー  
 カスタム トークン マネージャーを作成するためのプログラミング モデルは、WSE 3.0 と WCF で異なるです。 カスタム トークン マネージャーとカスタム セキュリティ トークンに必要なその他のコンポーネントを作成する方法の詳細については、次を参照してください。[する方法: カスタム トークンを作成する](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md)です。  
  
> [!NOTE]
>  カスタムを作成した場合`UsernameToken`セキュリティ トークン マネージャーは、WCF には、カスタム セキュリティ トークン マネージャーを作成するよりも認証ロジックを指定するを容易に行えるが用意されています。 詳細については、次を参照してください。[する方法: カスタム ユーザー名およびパスワード検証を使用して](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md)です。  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>MTOM エンコードされた SOAP メッセージを使用する WSE 3.0 Web サービス  
 WSE 3 アプリケーションのように、WCF アプリケーションは、MTOM メッセージの構成でのエンコードを指定できます。 この設定を移行するには追加、 [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md)サービスのバインドにします。 次のコード例では、MTOM エンコーディングを指定する方法 WSE 3.0 の WCF で同等であるサービスを示します。  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>メッセージング  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE メッセージング API を使用する WSE 3.0 アプリケーション  
 クライアントと Web サービス間でやり取りされる XML に直接アクセスするために WSE メッセージング API が使用されている場合は、"Plain Old XML" (POX) を使用するようにアプリケーションを変換できます。 POX の詳細については、次を参照してください。 [POX アプリケーションとの相互運用](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md)です。 WSE メッセージング API の詳細については、次を参照してください。[送信および受信 SOAP メッセージを使用する WSE メッセージング API](http://go.microsoft.com/fwlink/?LinkID=73755)です。  
  
## <a name="transports"></a>トランスポート  
  
### <a name="tcp"></a>TCP  
 既定では、WSE 3.0 クライアントおよび TCP トランスポートを使用して SOAP メッセージを送信する Web サービス相互運用不可能 WCF クライアントと Web サービスを使用します。 このような非互換性は、TCP プロトコルで使用されるフレームの違いとパフォーマンス上の理由に起因します。 ただし、WCF サンプルでは、WSE 3.0 と相互運用するカスタム TCP セッションを実装する方法について説明します。 このサンプルに関する詳細については、次を参照してください。[トランスポート: WSE 3.0 TCP 相互運用性](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md)です。  
  
 WCF アプリケーションが TCP トランスポートを使用することを指定するには、使用、 [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)です。  
  
### <a name="custom-transport"></a>カスタム トランスポート  
 WCF での WSE 3.0 カスタム トランスポートの該当するショートカットは、チャネル拡張です。 チャネル拡張機能の作成に関する詳細については、「 [、チャネル レイヤの拡張](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md)です。  
  
## <a name="see-also"></a>関連項目  
 [基本的なプログラミング ライフサイクル](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [カスタム バインディング](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [方法 : SecurityBindingElement を使用してカスタム バインディングを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [方法 : 指定した認証モード用の SecurityBindingElement を作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
