---
title: "方法 : ポート共有を使用するように Windows Communication Foundation サービスを構成する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 6400bc71-a858-4ac2-8d5a-caa72d3b5482
caps.latest.revision: 11
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 11
---
# 方法 : ポート共有を使用するように Windows Communication Foundation サービスを構成する
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションで net.tcp:\/\/ ポート共有を使用する最も簡単な方法は、<xref:System.ServiceModel.NetTcpBinding> を使用してサービスを公開することです。  
  
 このバインディングは、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> プロパティを提供します。このプロパティは、このバインディングを使用して構成されるサービスに対して net.tcp:\/\/ ポート共有を有効にするかどうかを制御します。  
  
 以下の手順では、<xref:System.ServiceModel.NetTcpBinding> クラスを使用して URI \(Uniform Resource Identifier\)、net.tcp:\/\/localhost\/MyService にあるエンドポイントを開く方法を示します。最初にコードを使用する場合の手順を示し、次に構成要素を使用する場合の手順を示します。  
  
### コードで NetTcpBinding の net.tcp:\/\/ ポート共有を有効にするには  
  
1.  `IMyService` という名前のコントラクトを実装するサービスを作成し、`MyService` という名前を付けます。  
  
     [!code-csharp[c_ConfigurePortSharing#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#1)]
     [!code-vb[c_ConfigurePortSharing#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#1)]  
  
2.  <xref:System.ServiceModel.NetTcpBinding> クラスのインスタンスを作成し、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> プロパティを `true` に設定します。  
  
     [!code-csharp[c_ConfigurePortSharing#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#2)]
     [!code-vb[c_ConfigurePortSharing#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#2)]  
  
3.  <xref:System.ServiceModel.ServiceHost> を作成し、ポート共有を有効にした <xref:System.ServiceModel.NetTcpBinding> を使用し、エンドポイント アドレス URI "net.tcp:\/\/localhost\/MyService" をリッスンする `MyService` のサービス エンドポイントを追加します。  
  
     [!code-csharp[c_ConfigurePortSharing#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_configureportsharing/cs/source.cs#3)]
     [!code-vb[c_ConfigurePortSharing#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_configureportsharing/vb/source.vb#3)]  
  
    > [!NOTE]
    >  このエンドポイント アドレス URI は異なるポート番号を指定しないため、この例では既定の TCP ポートである 808 を使用します。トランスポート バインディングでポート共有が明示的に有効になっているため、このサービスはポート 808 を他のプロセスの他のサービスと共有できます。ポート共有が許可されておらず、既に別のアプリケーションがポート 808 を使用している場合は、このサービスを開こうとすると <xref:System.ServiceModel.AddressAlreadyInUseException> がスローされます。  
  
### 構成で NetTcpBinding の net.tcp:\/\/ ポート共有を有効にするには  
  
1.  次の例では、構成要素を使用してポート共有を有効にし、サービス エンドポイントを追加します。  
  
```  
<system.serviceModel>  
  <bindings>  
    <netTcpBinding name="portSharingBinding"   
                   portSharingEnabled="true" />  
  </bindings>  
  <services>  
    <service name="MyService">  
        <endpoint address="net.tcp://localhost/MyService"  
                  binding="netTcpBinding"  
                  contract="IMyService"  
                  bindingConfiguration="portSharingBinding" />  
    </service>  
  </services>  
</system.serviceModel>  
```  
  
## 参照  
 [Net.TCP Port Sharing](http://msdn.microsoft.com/ja-jp/f13692ee-a179-4439-ae72-50db9534eded)   
 [方法 : Net.TCP ポート共有サービスを有効にする](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)