---
title: "方法 : クライアントの資格情報の値を指定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# 方法 : クライアントの資格情報の値を指定する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] では、サービスに対するクライアントの認証方法を指定できます。  たとえば、証明書を使用してクライアントを認証するように指定できます。  
  
### クライアント資格情報の種類を特定するには  
  
1.  サービスのメタデータ エンドポイントからメタデータを取得します。  一般的に、メタデータは、選択したプログラミング言語 \(既定は Visual C\#\) のクライアント コードおよび XML 構成ファイルという 2 つのファイルで構成されています。  メタデータは、クライアント コードおよびクライアント構成を返す Svcutil.exe ツールを使用して取得できます。  詳細については、「[メタデータを取得する](../../../docs/framework/wcf/feature-details/retrieving-metadata.md)」および「[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)」を参照してください。  
  
2.  XML 構成ファイルを開きます。  Svcutil.exe ツールを使用する場合、ファイルの既定の名前は、Output.config です。  
  
3.  **mode** 属性のある **\<security\>** 要素 \(**\<security mode \=** `MessageOrTransport`**\>**\) を見つけます。ここで、`MessageOrTransport` は、セキュリティ モードの 1 つに設定されています。  
  
4.  mode 値に一致する子要素を見つけます。  たとえば、mode が **Message** に設定されている場合、**\<security\>** 要素に含まれる **\<message\>** 要素を見つけます。  
  
5.  **clientCredentialType** 属性に割り当てられている値に注意します。  実際の値は、使用されているモード \(トランスポートまたはメッセージ\) に依存します。  
  
 次の XML コードは、メッセージ セキュリティを使用し、クライアントの認証に証明書を要求するクライアントの構成を示します。  
  
```  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## 例: クライアント資格情報としての証明書による TCP トランスポート モード  
 この例では、セキュリティ モードを "Transport \(トランスポート\)" モードに設定し、クライアント資格情報の値を X.509 証明書に設定します。  次の手順では、クライアントでクライアント資格情報の値をコードと構成を使用して設定する方法を示します。  ここでは、サービスからメタデータ \(コードと構成\) を返すために [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用していることを前提としています。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)][方法 : クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
#### クライアントでクライアント資格情報の値をコードによって指定するには  
  
1.  サービスからコードと構成を生成するために [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用します。  
  
2.  生成されたコードを使用して、[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] クライアントのインスタンスを作成します。  
  
3.  クライアント クラスで、<xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> クラスの <xref:System.ServiceModel.ClientBase%601> プロパティを適切な値に設定します。  この例では、<xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> クラスの <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> メソッドを使用して、このプロパティを X.509 証明書に設定します。  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     <xref:System.Security.Cryptography.X509Certificates.X509FindType> クラスの任意の列挙体を使用できます。  ここでは、有効期限が切れて証明書が変更された場合に備えて、サブジェクト名を使用しています。  サブジェクト名を使用することにより、インフラストラクチャは証明書を再検索できます。  
  
#### クライアントでクライアント資格情報の値を構成によって指定するには  
  
1.  [\<behavior\>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 要素を [\<behaviors\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素に追加します。  
  
2.  [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 要素を [\<behaviors\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 要素に追加します。  `name` 属性 \(必須\) を適切な値に必ず設定してください。  
  
3.  [\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) 要素を [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 要素に追加します。  
  
4.  次のコードに示すように、`storeLocation`、`storeName`、`x509FindType`、および `findValue` の各属性を適切な値に設定します。  証明書の[!INCLUDE[crabout](../../../includes/crabout-md.md)]については、「[証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)」を参照してください。  
  
    ```  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5.  クライアントを構成するときは、次のコードに示すように、`behaviorConfiguration` 要素の `<endpoint>` 属性を設定して動作を指定します。  エンドポイント要素は [\<client\>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) 要素の子です。  また、`bindingConfiguration` 属性をクライアントのバインディングに設定することにより、バインディング構成の名前を指定します。  生成された構成ファイルを使用している場合は、バインディングの名前は自動的に生成されます。  この例では、名前は `"tcpBindingWithCredential"` です。  
  
    ```  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## 参照  
 <xref:System.ServiceModel.NetTcpBinding>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>   
 <xref:System.ServiceModel.ClientBase%601>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>   
 [WCF セキュリティのプログラミング](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)   
 [資格情報の種類の選択](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [証明書の使用](../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [方法 : クライアントを作成する](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [\<netTcpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)   
 [\<security\>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)   
 [\<message\>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)   
 [\<behavior\>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)   
 [\<behaviors\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)   
 [\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)   
 [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)