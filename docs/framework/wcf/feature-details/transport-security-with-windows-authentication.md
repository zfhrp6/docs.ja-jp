---
title: "トランスポート セキュリティと Windows 認証 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 96dd26e2-46e7-4de0-9a29-4fcb05bf187b
caps.latest.revision: 17
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 17
---
# トランスポート セキュリティと Windows 認証
次のシナリオでは、Windows セキュリティによって保護されている [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントおよびサービスを示します。プログラミング[!INCLUDE[crabout](../../../../includes/crabout-md.md)]、「[方法 : Windows 資格情報でサービスをセキュリティで保護する](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)」を参照してください。  
  
 イントラネットの Web サービスでは人事情報を表示しています。クライアントは Windows フォーム アプリケーションです。このアプリケーションは、Kerberos コントローラーで保護されたドメインに展開されています。  
  
 ![Windows 認証を使用する場合のトランスポート セキュリティ](../../../../docs/framework/wcf/feature-details/media/securedbywindows.gif "SecuredByWindows")  
  
|特性|説明|  
|--------|--------|  
|セキュリティ モード|トランスポート|  
|相互運用性|[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] のみ|  
|認証 \(サーバー\)<br /><br /> 認証 \(クライアント\)|○ \(Windows 統合認証を使用\)<br /><br /> ○ \(Windows 統合認証を使用\)|  
|整合性|○|  
|機密性|○|  
|トランスポート|NET.TCP|  
|バインディング|<xref:System.ServiceModel.NetTcpBinding>|  
  
## サービス  
 次のコードと構成は、別々に実行します。以下のいずれかを実行します。  
  
-   構成を使用せずに、コードを使用してスタンドアロン サービスを作成します。  
  
-   提供された構成を使用してサービスを作成しますが、エンドポイントを定義しません。  
  
### コード  
 次のコードは、Windows セキュリティを使用するサービス エンドポイントの作成方法を示します。  
  
 [!code-csharp[C_SecurityScenarios#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#3)]
 [!code-vb[C_SecurityScenarios#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#3)]  
  
### 構成  
 コードの代わりに次の構成を使用して、サービス エンドポイントをセットアップできます。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <behaviors />  
    <services>  
      <service behaviorConfiguration="" name="ServiceModel.Calculator">  
        <endpoint address="net.tcp://localhost:8008/Calculator"   
                  binding="netTcpBinding"  
          bindingConfiguration="WindowsClientOverTcp"   
                  name="WindowsClientOverTcp"  
                  contract="ServiceModel.ICalculator" />  
      </service>  
    </services>  
    <bindings>  
      <netTcpBinding>  
        <binding name="WindowsClientOverTcp">  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client />  
  </system.serviceModel>  
</configuration>  
```  
  
## クライアント  
 次のコードと構成は、別々に実行します。以下のいずれかの操作を行います。  
  
-   コード \(およびクライアント コード\) を使用してスタンドアロン クライアントを作成します。  
  
-   エンドポイント アドレスを定義しないクライアントを作成します。代わりに、引数として構成名を受け取るクライアント コンストラクターを使用する。次に例を示します。  
  
     [!code-csharp[C_SecurityScenarios#0](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#0)]
     [!code-vb[C_SecurityScenarios#0](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#0)]  
  
### コード  
 クライアントを作成する場合のコード例を次に示します。バインディングは、クライアントの資格情報の種類が Windows に設定された、TCP トランスポートによるトランスポート モード セキュリティを使用するように構成されます。  
  
 [!code-csharp[C_SecurityScenarios#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_securityscenarios/cs/source.cs#4)]
 [!code-vb[C_SecurityScenarios#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_securityscenarios/vb/source.vb#4)]  
  
### 構成  
 コードの代わりに次の構成を使用して、クライアントを作成できます。  
  
```  
<?xml version="1.0" encoding="utf-8"?>  
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <netTcpBinding>  
        <binding name="NetTcpBinding_ICalculator" >  
          <security mode="Transport">  
            <transport clientCredentialType="Windows" />  
          </security>  
        </binding>  
      </netTcpBinding>  
    </bindings>  
    <client>  
      <endpoint address="net.tcp://localhost:8008/Calculator"   
                binding="netTcpBinding"            
                bindingConfiguration="NetTcpBinding_ICalculator"   
                contract="ICalculator"  
                name="NetTcpBinding_ICalculator">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## 参照  
 [セキュリティの概要](../../../../docs/framework/wcf/feature-details/security-overview.md)   
 [方法 : Windows 資格情報でサービスをセキュリティで保護する](../../../../docs/framework/wcf/how-to-secure-a-service-with-windows-credentials.md)   
 [Windows Server AppFabric のセキュリティ モデル](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)