---
title: "方法 : トランスポート セキュリティとメッセージ資格情報を使用する | Microsoft Docs"
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
  - "TransportWithMessageCredentials"
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# 方法 : トランスポート セキュリティとメッセージ資格情報を使用する
トランスポート資格情報とメッセージ資格情報の両方を使用してサービスをセキュリティで保護する場合、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、トランスポート セキュリティ モードとメッセージ セキュリティ モードの両方が最適に使用されます。つまり、トランスポート層セキュリティでは整合性と機密性が提供され、メッセージ層セキュリティでは、厳密なトランスポート セキュリティ機構では実現できないさまざまな資格情報が提供されます。ここでは、<xref:System.ServiceModel.WSHttpBinding> バインディングと <xref:System.ServiceModel.NetTcpBinding> バインディングを使用して、メッセージ資格情報付きトランスポートを実装するための基本手順を示します。セキュリティ モードの設定[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : セキュリティ モードを設定する](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)」を参照してください。  
  
 セキュリティ モードを `TransportWithMessageCredential` に設定した場合、トランスポート レベルのセキュリティを提供する実際の機構は、トランスポートによって決まります。この機構は、HTTP の場合は SSL \(Secure Sockets Layer\) over HTTP \(HTTPS\)、TCP の場合は SSL over TCP または Windows です。  
  
 トランスポートが HTTP \(<xref:System.ServiceModel.WSHttpBinding> を使用\) の場合は、トランスポート レベルのセキュリティが SSL over HTTP によって提供されます。この場合、このトピックで後述するように、ポートにバインドされた SSL 証明書を使用してサービスをホストするコンピューターを構成する必要があります。  
  
 トランスポートが TCP \(<xref:System.ServiceModel.NetTcpBinding> を使用\) の場合、既定では、Windows セキュリティ または SSL over TCP によってトランスポート レベルのセキュリティが提供されます。SSL over TCP を使用する場合は、このトピックで後述するように、<xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> メソッドを使用して証明書を指定する必要があります。  
  
### WSHttpBinding と証明書を使用してトランスポート セキュリティを提供するには \(コードを使用する場合\)  
  
1.  HttpCfg.exe ツールを使用して、コンピューターの任意のポートに SSL 証明書をバインドします。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : SSL 証明書を使用してポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  <xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.WSHttpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode> に設定します。  
  
3.  <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> プロパティに適切な値を設定します \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][資格情報の種類の選択](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).\)次のコードでは、<xref:System.ServiceModel.MessageCredentialType> 値を使用しています。  
  
4.  適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。このアドレスでは、"HTTPS" スキームを使用し、コンピューターの実際の名前と SSL 証明書のバインド先のポート番号を含める必要があります \(または、構成で基本アドレスを設定できます。\)  
  
5.  <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。  
  
6.  <xref:System.ServiceModel.ServiceHost> のインスタンスを作成し、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。コードは次のようになります。  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### NetTcpBinding と証明書を使用してトランスポート セキュリティを提供するには \(コードを使用する場合\)  
  
1.  <xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode> に設定します。  
  
2.  <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> を適切な値に設定します。次のコードでは、<xref:System.ServiceModel.MessageCredentialType> 値を使用しています。  
  
3.  適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。アドレスには "net.tcp" スキーマを使用する必要があることに注意してください。\(または、構成で基本アドレスを設定できます。\)  
  
4.  <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。  
  
5.  <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> メソッドを使用して、サービスに X.509 資格情報を明示的に設定します。  
  
6.  <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。  
  
7.  次のコードに示すように、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### NetTcpBinding と Windows を使用してトランスポート セキュリティを提供するには \(コードを使用する場合\)  
  
1.  <xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpSecurity.Mode%2A> プロパティを <xref:System.ServiceModel.SecurityMode> に設定します。  
  
2.  トランスポート セキュリティが Windows を使用するように、<xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> を <xref:System.ServiceModel.TcpClientCredentialType> に設定します \(これは、既定の設定です\)。  
  
3.  <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> を適切な値に設定します。次のコードでは、<xref:System.ServiceModel.MessageCredentialType> 値を使用しています。  
  
4.  適切なベース アドレスを持つ <xref:System.Uri> クラスのインスタンスを作成します。アドレスには "net.tcp" スキーマを使用する必要があることに注意してください。\(または、構成で基本アドレスを設定できます。\)  
  
5.  <xref:System.ServiceModel.ServiceHost> クラスのインスタンスを作成します。  
  
6.  <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> クラスの <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> メソッドを使用して、サービスに X.509 資格情報を明示的に設定します。  
  
7.  <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> メソッドを使用してサービス エンドポイントを追加します。  
  
8.  次のコードに示すように、<xref:System.ServiceModel.ICommunicationObject.Open%2A> メソッドを呼び出します。  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## 構成の使用  
  
#### WSHttpBinding を使用するには  
  
1.  ポートにバインドされた SSL 証明書を使用してコンピューターを構成します \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][方法 : SSL 証明書を使用してポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)\).この構成では、\<`transport`\> 要素値を設定する必要はありません。  
  
2.  メッセージ レベルのセキュリティのクライアント資格情報の種類を指定します。次の例では、\<`message`\> 要素の `clientCredentialType` 属性を `UserName` に設定しています。  
  
    ```  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### NetTcpBinding と証明書を使用してトランスポート セキュリティを提供するには  
  
1.  SSL over TCP の場合、`<behaviors>` 要素内で証明書を明示的に指定する必要があります。既定のストアの場所 \(ローカル コンピューターの個人ストア\) にある証明書を、発行者で指定する例を次に示します。  
  
    ```  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)をバインディング セクションに追加します。  
  
3.  バインド要素を追加して、`name` 属性を適切な値に設定します。  
  
4.  \<`security`\> 要素を追加し、`mode` 属性に `TransportWithMessageCredential` を設定します。  
  
5.  \<`message>` 要素を追加し、`clientCredentialType` 属性を適切な値に設定します。  
  
    ```  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### NetTcpBinding と Windows を使用してトランスポート セキュリティを提供するには  
  
1.  [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)をバインディング セクションに追加します。  
  
2.  \<`binding`\> 要素を追加し、`name` 属性を適切な値に設定します。  
  
3.  \<`security`\> 要素を追加し、`mode` 属性に `TransportWithMessageCredential` を設定します。  
  
4.  \<`transport`\> 要素を追加し、`clientCredentialType` 属性に `Windows` を設定します。  
  
5.  \<`message`\> 要素を追加し、`clientCredentialType` 属性を適切な値に設定します。次のコードは、値を証明書に設定します。  
  
    ```  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
  
    ```  
  
## 参照  
 [方法 : セキュリティ モードを設定する](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)   
 [サービスのセキュリティ保護](../../../../docs/framework/wcf/securing-services.md)   
 [サービスおよびクライアントのセキュリティ保護](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)