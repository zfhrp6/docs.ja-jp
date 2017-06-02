---
title: "方法 : セキュリティで保護されたセッションを作成する | Microsoft Docs"
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
  - "セキュリティ [WCF], セッションの作成"
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: 10
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 10
---
# 方法 : セキュリティで保護されたセッションを作成する
メッセージ セキュリティを有効にすると、[\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) バインディングを除き、システム提供のバインディング [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] では、セキュリティで保護されたセッションが自動的に使用されます。  
  
 既定では、セキュリティで保護されたセッションは、再利用される Web サーバーで存続します。  セキュリティで保護されたセッションが確立されると、クライアントとサービスが、セキュリティで保護されたセッションに関連付けられているキーをキャッシュします。  メッセージを交換するときは、キャッシュされたキーの識別子のみが交換されます。  Web サーバーが再利用される場合は、Web サーバーが識別子のキャッシュされたキーを取得できないようにキャッシュも再利用されます。  これが発生した場合、例外がクライアントにスローされます。  ステートフルなセキュリティ コンテキスト トークン \(SCT: Security Context Token\) を使用するセキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。  セキュリティで保護されたセッションでステートフルな SCT を使用する方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : セキュリティで保護されたセッションに対しセキュリティ コンテキスト トークンを作成する](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)」を参照してください。  
  
### サービスが、システム提供のバインディングの 1 つを使用して、セキュリティで保護されたセッションを使用するように指定するには  
  
-   メッセージ セキュリティをサポートするシステム提供のバインディングを使用するようにサービスを構成します。  
  
     [\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) バインディングを除き、システム提供のバインディングでメッセージ セキュリティが使用されるように設定しておくと、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ではセキュリティで保護されたセッションが自動的に使用されます。  次の表は、メッセージ セキュリティをサポートするシステム提供のバインディングを示し、そのバインディングでメッセージ セキュリティが既定のセキュリティ機構であるかどうかを示しています。  
  
    |システム提供のバインディング|構成要素|既定でメッセージ セキュリティが有効|  
    |--------------------|----------|------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Ｘ|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|はい|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|はい|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|はい|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Ｘ|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Ｘ|  
  
     次のコード例に使用されている構成では、[\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションを使用する `wsHttpBinding_Calculator` という名前のバインディングを指定しています。  
  
    ```  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションを使用して、`secureCalculator` サービスをセキュリティで保護するように指定するコード例を次に示します。  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  [\<wsHttpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) については、`establishSecurityContext` 属性を `false` に設定してセキュリティで保護されたセッションを無効にできます。  他のシステム提供のバインディングについては、カスタム バインディングを作成することでのみ、セキュリティで保護されたセッションを無効にできます。  
  
### カスタム バインディングを使用して、サービスでセキュリティで保護されたセッションが使用されるように指定するには  
  
-   セキュリティで保護されたセッションで SOAP メッセージが保護されるように指定したカスタム バインディングを作成します。  
  
     カスタム バインディングの作成[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : システム指定のバインディングをカスタマイズする](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)」を参照してください。  
  
     次のコード例で使用されている構成では、セキュリティで保護されたセッションを使用して SOAP メッセージを保護するカスタム バインディングを指定しています。  
  
    ```  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode> 認証モードを使用する、カスタム バインディングを作成するコード例を次に示します。  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## 参照  
 [WCF のバインディングの概要](../../../../docs/framework/wcf/bindings-overview.md)