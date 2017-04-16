---
title: "トランスポート セキュリティの概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
caps.latest.revision: 23
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 23
---
# トランスポート セキュリティの概要
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] のトランスポート セキュリティ機構は、使用するバインディングとトランスポートによって異なります。 たとえばを使用する場合、 <xref:System.ServiceModel.WSHttpBinding>クラスで、トランスポートは HTTP であり、トランスポート セキュリティで保護するための主要機構 Secure Sockets Layer (SSL) over HTTP、HTTPS と呼ばします。 このトピックでは、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] システムに用意されたバインディングで使用する主要なトランスポート セキュリティ機構について説明します。  
  
> [!NOTE]
>  SSL セキュリティを .NET Framework 3.5 以降と共に使用すると、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントは、証明書ストア内の中間証明書と SSL ネゴシエーション中に受信した中間証明書の両方を使用して、サービスの証明書に対して証明書チェーンの検証を実行します。 .NET Framework 3.0 では、ローカルの証明書ストアにインストールされている中間証明書のみが使用されます。  
  
> [!WARNING]
>  トランスポート セキュリティを使用すると、 <xref:System.Treading.Thread.CurrentPrincipal%2A>プロパティが上書きされる可能性があります。 設定しないように、 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> "なし"にします。 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>はサービスの説明で設定できるサービス動作です。  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 既定では、 <xref:System.ServiceModel.BasicHttpBinding>クラスでは、セキュリティは提供されません。 このバインディングは、セキュリティを実装していない Web サービス プロバイダーとの相互運用性のためにデザインされています。 ただしを設定することでセキュリティに切り替えることができます、<xref:System.ServiceModel.BasicHttpSecurity.Mode%2A>プロパティ以外の値を<xref:System.ServiceModel.BasicHttpSecurityMode>します。 トランスポート セキュリティを有効にする、プロパティを設定<xref:System.ServiceModel.BasicHttpSecurityMode>します。  
  
### <a name="interoperation-with-iis"></a>IIS との相互運用性  
 <xref:System.ServiceModel.BasicHttpBinding>クラスは、既存の Web サービスと相互運用する、主に使用され、それらのサービスの多くでインターネット インフォメーション サービス (IIS) によってをホストします。 そのため、このバインディングのトランスポート セキュリティは、IIS サイトとシームレスに相互運用できるようにデザインされています。 これは、セキュリティ モードを設定することで<xref:System.ServiceModel.BasicHttpSecurityMode>し、クライアント資格情報の種類を設定します。 資格情報の種類の値は、IIS ディレクトリのセキュリティ機構に対応しています。 モードを設定し、資格情報の種類を Windows に設定するコードを次に示します。 この構成は、クライアントとサーバーが同じ Windows ドメインに存在する場合に使用できます。  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)]
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 または、次のように構成します。  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 以下のセクションでは、その他のクライアント資格情報の種類について説明します。  
  
#### <a name="basic"></a>基本  
 これは、IIS の基本認証方法に対応しています。 このモードを使用する場合は、Windows ユーザー アカウントと、適切な NTFS ファイル システムのアクセス許可を使用して IIS サーバーを構成する必要があります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[基本認証の有効化と領域名の構成](http://go.microsoft.com/fwlink/?LinkId=88592)します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)]、を参照してください[IIS 7.0 Beta: Configure Basic Authentication](http://go.microsoft.com/fwlink/?LinkId=88593)します。  
  
#### <a name="certificate"></a>証明書  
 IIS には、クライアントに証明書を使用してログオンすることを要求するオプションがあります。 この機能により、IIS はクライアント証明書を Windows アカウントにマップすることもできます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[Enabling Client Certificates in IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88594)します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)]を参照してください[IIS 7.0 Beta: Configuring Server Certificates in IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595)します。  
  
#### <a name="digest"></a>Digest  
 ダイジェスト認証は基本認証と似ていますが、資格情報をクリア テキストではなくハッシュとして送信できるという利点があります。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[IIS 6.0 のダイジェスト認証](http://go.microsoft.com/fwlink/?LinkID=88443)します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)]、を参照してください[IIS 7.0 Beta: Configure Digest Authentication](http://go.microsoft.com/fwlink/?LinkId=88596)します。  
  
#### <a name="windows"></a>Windows  
 これは、IIS の統合 Windows 認証に対応しています。 この値に設定する場合、サーバーは、Kerberos プロトコルを使用する Windows ドメインにドメイン コントローラーとして存在することにもなっています。 サーバーが Kerberos ベースのドメインに存在しない場合、または Kerberos システムに障害が発生した場合は、次のセクションで説明する NTLM (NT LAN Manager) 値を使用できます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[IIS 6.0 で統合 Windows 認証](http://go.microsoft.com/fwlink/?LinkId=88597)します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)]を参照してください[IIS 7.0 Beta: Configuring Server Certificates in IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595)します。  
  
#### <a name="ntlm"></a>NTLM  
 この値を使用すると、Kerberos プロトコルが失敗した場合に、サーバーは、NTLM を使用して認証を実行できます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]IIS を構成して[!INCLUDE[iis601](../../../../includes/iis601-md.md)]を参照してください[強制的に NTLM 認証](http://go.microsoft.com/fwlink/?LinkId=88598)します。 [!INCLUDE[iisver](../../../../includes/iisver-md.md)] では、Windows 認証に NTLM 認証が含まれます。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS 7.0 Beta: Configuring Server Certificates in IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595)します。  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding>クラスが ws-を実装するサービスと相互運用のために設計されています * の仕様です。 このバインディングのトランスポート セキュリティは、SSL (Secure Sockets Layer) over HTTP または HTTPS です。 SSL を使用する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションを作成するには、IIS を使用してアプリケーションをホストします。 自己ホスト型アプリケーションを作成する場合は、HttpCfg.exe ツールを使用して、X.509 証明書をコンピューターの特定のポートにバインドします。 ポート番号は、エンドポイント アドレスとして [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションの一部に指定されます。 トランスポート モードを使用する場合は、エンドポイント アドレスに HTTPS プロトコルを含める必要があります。そうしないと、実行時に例外が発生します。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HTTP トランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/http-transport-security.md)します。  
  
 クライアントの認証設定、 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A>のプロパティ、 <xref:System.ServiceModel.HttpTransportSecurity>クラスのいずれかに、 <xref:System.ServiceModel.HttpClientCredentialType>列挙値。 列挙値が同一のクライアント資格情報の種類を<xref:System.ServiceModel.BasicHttpBinding> IIS のサービスでホストされるように設計されています。  
  
 クライアント資格情報の種類が Windows の場合に使用するバインディングの例を次に示します。  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 このバインディングが提供するのは、トランスポート レベルのセキュリティではなく、メッセージ レベルのセキュリティだけです。  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding>クラスは、メッセージ トランスポートに TCP を使用します。 トランスポート モードのセキュリティは、TLS (Transport Layer Security) over TCP を実装することによって実現されます。 TLS 実装は、オペレーティング システムによって提供されます。  
  
 設定して、クライアントの資格情報の種類を指定することも、 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A>のプロパティ、 <xref:System.ServiceModel.TcpTransportSecurity>クラスのいずれかに、 <xref:System.ServiceModel.TcpClientCredentialType>値は、次のコードに示すようにします。  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>クライアント  
 クライアントを使用して、証明書を指定する必要があります、 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>のメソッド、 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>クラスです。  
  
> [!NOTE]
>  Windows セキュリティを使用している場合には、証明書は不要です。  
  
 証明書の拇印を使用するコードを次に示します。拇印により、証明書が一意に識別されます。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]証明書を参照してください[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)します。  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 または、証明書をクライアントの構成に指定を使用して、 [ <> \> ](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)動作セクション内の要素。  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding>クラスが効率的なマシン間の通信用に設計されています。 つまり、プロセスの名前付きパイプ チャネルは、同じコンピューターで実行されている間に作成できる、同じネットワーク上の&2; 台のコンピューターです。 このバインディングが提供するのは、トランスポート レベルのセキュリティだけです。 このバインディングを使用してアプリケーションを作成する場合は、エンドポイント アドレスにプロトコルとして "net.pipe" を含める必要があります。  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 このバインディングが発行されたトークンを使用して、HTTPS と呼ばれる、HTTP 経由で SSL を使用するトランスポート セキュリティを使用する場合 (<xref:System.ServiceModel.WSFederationHttpSecurityMode>)。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]フェデレーション アプリケーションを参照してください[フェデレーションと発行されたトークン](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)します。  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding>クラスはセキュリティで保護されたトランスポートでは、ピア ツー ピア ネットワーク機能を使用して効率的に通信するためです。 クラスとバインディングの名前が示すように、プロトコルは TCP です。 セキュリティ モードが Transport に設定されている場合、このバインディングは TLS over TCP を実装します。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]ピア ツー ピア機能を参照してください[ピア ツー ピア ネットワーク](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)します。  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding と NetMsmqBinding  
 トランスポートの詳細についてはセキュリティとメッセージ キュー (MSMQ と呼ばれていた) を参照してください[トランスポート セキュリティを使用してメッセージをセキュリティで保護する](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)です。  
  
## <a name="see-also"></a>関連項目  
 [WCF セキュリティのプログラミング](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)