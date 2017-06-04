---
title: "チャネル ファクトリ | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 09b53aa1-b13c-476c-a461-e82fcacd2a8b
caps.latest.revision: 24
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 24
---
# チャネル ファクトリ
このサンプルでは、クライアント アプリケーションが、生成されたクライアントではなく <xref:System.ServiceModel.ChannelFactory> クラスを含むチャネルを作成できる方法を示します。このサンプルは、電卓サービスを実装する「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」に基づいています。  
  
> [!NOTE]
>  このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。  
  
 このサンプルは、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用して、サービス エンドポイントにチャネルを作成します。通常、サービス エンドポイントへのチャネルを作成するには、[ServiceModel メタデータ ユーティリティ ツール \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) を使用してクライアント型を生成し、生成された型のインスタンスを作成します。また、<xref:System.ServiceModel.ChannelFactory%601> クラスを使用してチャネルを作成することもできます。サンプルを参照してください。次のサンプル コードで作成されるサービスは、「[概要](../../../../docs/framework/wcf/samples/getting-started-sample.md)」内のサービスと同じものです。  
  
```  
EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
WSHttpBinding binding = new WSHttpBinding();  
ChannelFactory<ICalculator> factory = new   
                    ChannelFactory<ICalculator>(binding, address);  
ICalculator channel = factory.CreateChannel();  
```  
  
> [!IMPORTANT]
>  このサンプルを複数コンピュータのシナリオで実行している場合は、前述のコードの "localhost" を、サービスを実行中のコンピュータの完全修飾名に置き換える必要があります。このサンプルは、エンドポイント アドレスを設定する構成を使用していません。したがって、コード内でアドレスを設定する必要があります。  
  
 チャネルが作成されたら、生成されたクライアントと同様にサービス操作を呼び出すことができます。  
  
```  
// Call the Add service operation.  
double value1 = 100.00D;  
double value2 = 15.99D;  
double result = channel.Add(value1, value2);  
Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
```  
  
 チャネルを閉じるには、最初にチャネルを <xref:System.ServiceModel.IClientChannel> インターフェイスにキャストする必要があります。これは、生成されたチャネルが `ICalculator` インターフェイスによってクライアント アプリケーション内で宣言されているからです。このインターフェイスには `Add` および `Subtract` などのメソッドは含まれていますが、`Close` は含まれていません。`Close` メソッドは、<xref:System.ServiceModel.ICommunicationObject> インターフェイスで発生します。  
  
```  
// Close the channel.  
 ((IClientChannel)client).Close();  
  
```  
  
 このサンプルを実行する場合は、操作要求および応答はクライアントのコンソール ウィンドウに表示されます。クライアント アプリケーションをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### サンプルを設定、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。このサンプルではメタデータの公開は有効化されないことに注意してください。最初にこのサンプルのメタデータ公開を有効にして、クライアント型を再生成する必要があります。  
  
3.  単一コンピュータ構成か複数コンピュータ構成かに応じて、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
### サンプルを複数コンピュータで実行するには  
  
1.  次のコードの "localhost" を、サービスを実行中のコンピューターの完全修飾名に置き換えます。  
  
    ```  
    EndpointAddress address = new EndpointAddress("http://localhost/servicemodelsamples/service.svc");  
    ```  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ChannelFactory`  
  
## 参照