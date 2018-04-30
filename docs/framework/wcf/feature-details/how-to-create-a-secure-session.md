---
title: '方法 : セキュリティで保護されたセッションを作成する'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
caps.latest.revision: 10
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 0316d1120fe5f5b596374594de66e4f48dae84e8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="how-to-create-a-secure-session"></a>方法 : セキュリティで保護されたセッションを作成する
例外を除いて、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)のシステム指定のバインディング、バインディング[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]メッセージ セキュリティが有効になっているセキュリティで保護されたセッションを自動的に使用します。  
  
 既定では、セキュリティで保護されたセッションは、再利用される Web サーバーで存続します。 セキュリティで保護されたセッションが確立されると、クライアントとサービスが、セキュリティで保護されたセッションに関連付けられているキーをキャッシュします。 メッセージを交換するときは、キャッシュされたキーの識別子のみが交換されます。 Web サーバーが再利用される場合は、Web サーバーが識別子のキャッシュされたキーを取得できないようにキャッシュも再利用されます。 これが発生した場合、例外がクライアントにスローされます。 ステートフルなセキュリティ コンテキスト トークン (SCT: Security Context Token) を使用するセキュリティで保護されたセッションは、再利用される Web サーバーで存続することができます。 詳細については、セキュリティで保護されたセッションでステートフルな SCT を使用して、次を参照してください。[する方法: セキュリティで保護されたセッションのセキュリティ コンテキスト トークンを作成](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)です。  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a>サービスが、システム提供のバインディングの 1 つを使用して、セキュリティで保護されたセッションを使用するように指定するには  
  
-   メッセージ セキュリティをサポートするシステム提供のバインディングを使用するようにサービスを構成します。  
  
     例外を除いて、 [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)メッセージ セキュリティを使用するシステム提供のバインディングが構成されている場合、バインディング、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]自動的にセキュリティで保護されたセッションを使用します。 次の表は、メッセージ セキュリティをサポートするシステム提供のバインディングを示し、そのバインディングでメッセージ セキュリティが既定のセキュリティ機構であるかどうかを示しています。  
  
    |システム提供のバインディング|構成要素|既定でメッセージ セキュリティが有効|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|×|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|[はい]|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|[はい]|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|[はい]|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|×|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|×|  
  
     次のコード例は、という名前のバインディングを指定する構成を使用して`wsHttpBinding_Calculator`を使用して、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションです。  
  
    ```xml  
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
  
     次のコード例を指定する、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、メッセージ セキュリティ、およびセキュリティで保護されたセッションをセキュリティで保護を使用する、`secureCalculator`サービス。  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  セキュリティで保護されたセッションを無効にできる、 [ <wsHttpBinding> ](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)を設定して、`establishSecurityContext`属性を`false`です。 他のシステム提供のバインディングについては、カスタム バインドを作成することでのみ、セキュリティで保護されたセッションを無効にできます。  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a>カスタム バインディングを使用して、サービスでセキュリティで保護されたセッションが使用されるように指定するには  
  
-   セキュリティで保護されたセッションで SOAP メッセージが保護されるように指定したカスタム バインドを作成します。  
  
     カスタム バインドの作成の詳細については、次を参照してください。[する方法: システム指定のバインディングをカスタマイズ](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)です。  
  
     次のコード例で使用されている構成では、セキュリティで保護されたセッションを使用して SOAP メッセージを保護するカスタム バインドを指定しています。  
  
    ```xml  
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
  
     セキュリティで保護されたセッションをブートストラップするための <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 認証モードを使用する、カスタム バインディングを作成するコード例を次に示します。  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a>関連項目  
 [WCF のバインディングの概要](../../../../docs/framework/wcf/bindings-overview.md)
