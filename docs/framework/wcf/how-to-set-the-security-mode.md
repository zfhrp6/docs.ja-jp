---
title: "方法 : セキュリティ モードを設定する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Mode プロパティ"
  - "WCF, セキュリティ"
  - "WCF, セキュリティ モード"
ms.assetid: 6e01dd9f-b5dd-4474-b24c-06e124de4ff7
caps.latest.revision: 22
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 22
---
# 方法 : セキュリティ モードを設定する
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] セキュリティには、"トランスポート"、"メッセージ"、および "メッセージ資格情報付きトランスポート" という 3 つの共通のセキュリティ モードがあり、ほとんどの定義済みバインディングでサポートされます。これ以外に、2 つのバインディングに固有の 2 つのモードがあります。<xref:System.ServiceModel.BasicHttpBinding> の "トランスポート資格情報専用" モードと、<xref:System.ServiceModel.NetMsmqBinding> の "両方" モードです。ここでは、3 つの共通のセキュリティモードである <xref:System.ServiceModel.SecurityMode>、<xref:System.ServiceModel.SecurityMode>、および <xref:System.ServiceModel.SecurityMode> に重点を置いて説明します。  
  
 ただし、これらのモードがすべての定義済みバインディングでサポートされるわけではありません。ここでは、<xref:System.ServiceModel.WSHttpBinding> クラスと <xref:System.ServiceModel.NetTcpBinding> クラスでモードを設定し、プログラムと構成の両方を使用してモードを設定する方法を示します。  
  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] のセキュリティ[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)」、「[サービスのセキュリティ保護](../../../docs/framework/wcf/securing-services.md)」、および「[サービスおよびクライアントのセキュリティ保護](../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)」を参照してください。トランスポート モードとメッセージ[!INCLUDE[crabout](../../../includes/crabout-md.md)]、「[トランスポート セキュリティ](../../../docs/framework/wcf/feature-details/transport-security.md)」および「[メッセージのセキュリティ](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)」を参照してください。  
  
### コードでセキュリティ モードを設定するには  
  
1.  使用しているバインディング クラスのインスタンスを作成します。定義済みバインディングの一覧については、「[システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)」を参照してください。この例では、<xref:System.ServiceModel.WSHttpBinding> クラスのインスタンスを作成します。  
  
2.  `Security` プロパティから返されるオブジェクトの `Mode` プロパティを設定します。  
  
     [!code-csharp[c_SettingSecurityMode#1](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#1)]
     [!code-vb[c_SettingSecurityMode#1](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#1)]  
  
     または、モードを Message \(メッセージ\) に設定します。コードは次のようになります。  
  
     [!code-csharp[c_SettingSecurityMode#2](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#2)]
     [!code-vb[c_SettingSecurityMode#2](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#2)]  
  
     または、モードを TransportWithMessageCredential \(メッセージ資格情報付きトランスポート\) に設定します。コードは次のようになります。  
  
     [!code-csharp[c_SettingSecurityMode#3](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#3)]
     [!code-vb[c_SettingSecurityMode#3](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#3)]  
  
3.  次のコードに示すように、バインディングのコンストラクターでモードを設定することもできます。  
  
     [!code-csharp[c_SettingSecurityMode#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#4)]
     [!code-vb[c_SettingSecurityMode#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#4)]  
  
## ClientCredentialType プロパティの設定  
 モードを上記の 3 つの値のいずれかに設定すると、`ClientCredentialType` プロパティの設定方法が決まります。たとえば、<xref:System.ServiceModel.WSHttpBinding> クラスを使用し、モードを `Transport` に設定した場合、<xref:System.ServiceModel.HttpTransportSecurity> クラスの <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> プロパティを適切な値に設定する必要があります。  
  
#### トランスポート モードの ClientCredentialType プロパティを設定するには  
  
1.  バインディングのインスタンスを作成します。  
  
2.  `Mode` プロパティを `Transport` に設定します。  
  
3.  `ClientCredential` プロパティに適切な値を設定します。プロパティを `Windows` に設定するコードを次に示します。  
  
     [!code-csharp[c_SettingSecurityMode#5](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#5)]
     [!code-vb[c_SettingSecurityMode#5](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#5)]  
  
#### メッセージ モードの ClientCredentialType プロパティを設定するには  
  
1.  バインディングのインスタンスを作成します。  
  
2.  `Mode` プロパティを `Message` に設定します。  
  
3.  `ClientCredential` プロパティに適切な値を設定します。プロパティを `Certificate` に設定するコードを次に示します。  
  
     [!code-csharp[c_SettingSecurityMode#6](../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#6)]
     [!code-vb[c_SettingSecurityMode#6](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#6)]  
  
#### 構成でモードと ClientCredentialType プロパティを設定するには  
  
1.  構成ファイルの [\<bindings\>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) 要素に、適切なバインド要素を追加します。次の例では [\<wsHttpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) 要素を追加しています。  
  
2.  `<binding>` 要素を追加し、`name` 属性に適切な値を設定します。  
  
3.  `<security>` 要素を追加し、`mode` 属性を `Message`、`Transport`、または `TransportWithMessageCredential` に設定します。  
  
4.  モードを `Transport` に設定した場合は、`<transport>` 要素を追加し、`clientCredential` 属性を適切な値に設定します。  
  
     モードを "`Transport"` に設定し、`<transport>` 要素の `clientCredentialType` 属性を "`Windows"` に設定する例を次に示します。  
  
    ```  
    <wsHttpBinding>  
    <binding name="TransportSecurity">  
        <security mode="Transport" />  
           <transport clientCredentialType = "Windows" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     または、`security mode` を "`Message"` に設定し、その後に `<"message">` 要素を指定します。この例では、`clientCredentialType` を "`Certificate"` に設定しています。  
  
    ```  
    <wsHttpBinding>  
    <binding name="MessageSecurity">  
        <security mode="Message" />  
           <message clientCredentialType = "Certificate" />  
        </security>  
    </binding>  
    </wsHttpBinding >  
    ```  
  
     次に説明する <xref:System.ServiceModel.BasicHttpSecurityMode> 値は、特殊なケースで使用されます。  
  
### TransportWithMessageCredential の使用  
 セキュリティ モードを `TransportWithMessageCredential` に設定した場合、トランスポート レベルのセキュリティを提供する実際の機構はトランスポートによって決まります。たとえば、HTTP プロトコルでは SSL \(Secure Sockets Layer\) over HTTP \(HTTPS\) を使用します。このため、トランスポート セキュリティ オブジェクト \(<xref:System.ServiceModel.HttpTransportSecurity> など\) の `ClientCredentialType` プロパティを設定しても無視されます。つまり、メッセージ セキュリティ オブジェクト \(`WSHttpBinding` バインディングの場合は <xref:System.ServiceModel.NonDualMessageSecurityOverHttp> オブジェクト\) の `ClientCredentialType` だけを設定できます。  
  
 [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [方法 : トランスポート セキュリティとメッセージ資格情報を使用する](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md).  
  
## 参照  
 [方法 : SSL 証明書を使用してポートを構成する](../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)   
 [方法 : トランスポート セキュリティとメッセージ資格情報を使用する](../../../docs/framework/wcf/feature-details/how-to-use-transport-security-and-message-credentials.md)   
 [トランスポート セキュリティ](../../../docs/framework/wcf/feature-details/transport-security.md)   
 [メッセージのセキュリティ](../../../docs/framework/wcf/feature-details/message-security-in-wcf.md)   
 [セキュリティの概要](../../../docs/framework/wcf/feature-details/security-overview.md)   
 [システム標準のバインディング](../../../docs/framework/wcf/system-provided-bindings.md)   
 [\<security\>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-wshttpbinding.md)   
 [\<security\>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)   
 [\<security\>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)