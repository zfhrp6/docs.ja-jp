---
title: "トランスポート セキュリティと匿名クライアント | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 056653a5-384e-4a02-ae3c-1b0157d2ccb4
caps.latest.revision: 14
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 14
---
# トランスポート セキュリティと匿名クライアント
この [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] シナリオでは、トランスポート セキュリティ \(HTTPS\) を使用して機密性と整合性を確保します。サーバーは SSL \(Secure Sockets Layer\) 証明書で認証される必要があり、クライアントはサーバーの証明書を信頼する必要があります。クライアントを認証する機構はないため、匿名となります。  
  
 サンプル アプリケーションについては、「[WS トランスポート セキュリティ](../../../../docs/framework/wcf/samples/ws-transport-security.md)」を参照してください。トランスポート セキュリティ[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)」を参照してください。  
  
 サービスでの証明書の使用方法[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[証明書の使用](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)」および「[方法 : SSL 証明書を使用してポートを構成する](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)」を参照してください。  
  
 ![匿名クライアントを使用する場合のトランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/media/8fa2e931-0cfb-4aaa-9272-91d652b85d8d.gif "8fa2e931\-0cfb\-4aaa\-9272\-91d652b85d8d")  
  
|特性|説明|  
|--------|--------|  
|セキュリティ モード|トランスポート|  
|相互運用性|既存の Web サービスとクライアントを使用する|  
|認証 \(サーバー\)<br /><br /> 認証 \(クライアント\)|○<br /><br /> アプリケーション レベル \([!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のサポートなし\)|  
|整合性|○|  
|機密性|○|  
|トランスポート|HTTPS|  
|バインディング|<xref:System.ServiceModel.WsHttpBinding>|  
  
## サービス  
 次のコードと構成は、別々に実行します。以下のいずれかを実行します。  
  
-   構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。  
  
-   提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。  
  
### コード  
 次のコードは、トランスポート セキュリティを使用してエンドポイントを作成する方法を示しています。  
  
 [!code-csharp[c_SecurityScenarios#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#5)]
 [!code-vb[c_SecurityScenarios#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#5)]  
  
### 構成  
 次のコードは、次に示す構成を使用して同一のエンドポイントをセットアップします。クライアントを認証する機構はないため、匿名となります。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="ServiceModel.Calculator">  
        <endpoint address="http://localhost/Calculator"   
                  binding="wsHttpBinding"  
                  bindingConfiguration="WSHttpBinding_ICalculator"   
                  name="SecuredByTransportEndpoint"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator">  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## クライアント  
 次のコードと構成は、別々に実行します。以下のいずれかの操作を行います。  
  
-   コード \(およびクライアント コード\) を使用してスタンドアロン クライアントを作成します。  
  
-   エンドポイント アドレスを定義しないクライアントを作成します。代わりに、引数として構成名を受け取るクライアント コンストラクターを使用します。例 :  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### コード  
 [!code-csharp[c_SecurityScenarios#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#6)]
 [!code-vb[c_SecurityScenarios#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#6)]  
  
### 構成  
 コードの代わりに次の構成を使用して、サービスをセットアップできます。  
  
```  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <wsHttpBinding>  
        <binding name="WSHttpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="None" />  
          </security>  
        </binding>  
      </wsHttpBinding>  
    </bindings>  
    <client>  
      <endpoint address="https://machineName/Calculator"   
                binding="wsHttpBinding"  
                bindingConfiguration="WSHttpBinding_ICalculator"   
                contract="ICalculator"  
                name="WSHttpBinding_ICalculator" />  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 参照  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [WS トランスポート セキュリティ](../../../../docs/framework/wcf/samples/ws-transport-security.md)   
 [トランスポート セキュリティの概要](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)