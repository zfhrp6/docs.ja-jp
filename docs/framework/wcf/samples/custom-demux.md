---
title: カスタム Demux
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: 41
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 45184c2d884347baef4090ed496e22e77aab5423
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="custom-demux"></a>カスタム Demux
このサンプルでは、MSMQ メッセージ ヘッダーをさまざまなサービス操作にマップする方法を[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]を使用するサービス<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>で示したように 1 つのサービス操作の使用に限定されない、[メッセージ キューをWindows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)と[メッセージ キューへの Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)サンプルです。  
  
 このサンプルのサービスは自己ホスト型コンソール アプリケーションであるので、サービスを実行すると、キューに置かれたメッセージを受信するようすを観察できます。  
  
 サービス コントラクトは `IOrderProcessor` です。これは、キューでの使用に適した一方向サービスを定義します。  

```csharp
[ServiceContract]  
[KnownType(typeof(PurchaseOrder))]  
[KnownType(typeof(String))]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Name = "SubmitPurchaseOrder")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
  
    [OperationContract(IsOneWay = true, Name = "CancelPurchaseOrder")]  
    void CancelPurchaseOrder(MsmqMessage<string> ponumber);  
}  
```

 MSMQ メッセージには Action ヘッダーがないので、 さまざまな MSMQ メッセージを操作コントラクトに自動的にマッピングすることはできません。 したがって、存在する操作コントラクトは 1 つだけです。 この制限を克服するために、サービスは <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> インターフェイスの <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> メソッドを実装します。 <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> メソッドによって、メッセージの特定のヘッダーを特定のサービス操作にマッピングできるようになります。 このサンプルでは、メッセージのラベル ヘッダーをサービス操作にマッピングします。 操作コントラクトの `Name` パラメータは、特定のメッセージ ラベルに対してどのサービス操作をディスパッチするかを示します。 たとえば、メッセージのラベル ヘッダーに "SubmitPurchaseOrder" が含まれている場合に、"SubmitPurchaseOrder" サービス操作を呼び出します。  

```csharp
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```

 サービスは <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> インターフェイスの <xref:System.ServiceModel.Description.IContractBehavior> メソッドを実装する必要があります。次のサンプル コードを参照してください。 これによって、カスタムの `OperationSelector` がサービス フレームワークのディスパッチ ランタイムに適用されます。  

```csharp
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```

 メッセージが OperationSelector に到達するには、ディスパッチャの <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> を通過する必要があります。 既定の設定では、メッセージのアクションが、サービスによって実装されているどのコントラクトにも見つからない場合に、メッセージが拒否されます。 この検査を回避するために、<xref:System.ServiceModel.Description.IEndpointBehavior> という名前の `MatchAllFilterBehavior` を実装します。これは、次に示すように `ContractFilter` を適用して、どのメッセージも <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> を通過できるようにするものです。  

```csharp
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```
  
 メッセージをサービスが受信すると、ラベル ヘッダーからの情報を使用して該当するサービス操作がディスパッチされます。 メッセージの本文が逆シリアル化されて `PurchaseOrder` オブジェクトが作成されます。次のサンプル コードを参照してください。  

```csharp
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```

 サービスは自己ホスト型です。 MSMQ を使用するときは、使用するキューをあらかじめ作成しておく必要があります。 手動で作成することもコードで作成することもできます。 このサンプルでは、サービスのコードの中でキューの存在を確認し、存在しない場合は作成します。 キュー名は構成ファイルから読み込まれます。  

```csharp
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration  
    string queueName = ConfigurationManager.AppSettings["orderQueueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))  
    {                 
        ServiceEndpoint endpoint = serviceHost.Description.Endpoints[0];  
        endpoint.Behaviors.Add(new MatchAllFilterBehavior());  
  
        //Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();  
    }  
}  
```

 MSMQ キュー名は、構成ファイルの appSettings セクションで指定されます。  
  
> [!NOTE]
>  キュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイント アドレスでは msmq.formatname スキームが指定され、ローカル コンピューターを表す localhost が使用されます。 このスキームの後には、MSMQ 形式名のアドレス指定ガイドラインに沿って正しく書式設定されたキューのアドレスが続きます。  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  このサンプルのインストールが必要[メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=95143)です。  
  
 サービスを開始してクライアントを実行します。  
  
 クライアントには、次の出力が表示されます。  
  
```  
Placed the order:Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Pending  
Canceled the Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
Press <ENTER> to terminate client.  
```  
  
 サービスには、次の出力が表示されます。  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
Processing Purchase Order: 28fc457a-1a56-4fe0-9dde-156965c21ed6  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 54 of Blue Widget @unit price: $29.99  
                Order LineItem: 890 of Red Widget @unit price: $45.89  
        Total cost of this order: $42461.56  
        Order status: Shipped  
Purchase Order 28fc457a-1a56-4fe0-9dde-156965c21ed6 is canceled  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。 キューが存在しない場合、サービスによってキューが作成されます。 最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。 Windows 2008 でキューを作成するには、次の手順に従います。  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。  
  
    2.  展開して、**機能**タブです。  
  
    3.  右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。  
  
    4.  チェック、**トランザクション**ボックス。  
  
    5.  入力`ServiceModelSamplesTransacted`として、新しいキューの名前。  
  
3.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
### <a name="to-run-the-sample-across-computers"></a>サンプルを複数のコンピューターで実行するには  
  
1.  サービスのプログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。  
  
2.  クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。  
  
3.  Client.exe.config ファイルを開き、orderQueueName を変更して "." の代わりにサービス コンピューター名を指定します。  
  
4.  サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。  
  
5.  クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a>関連項目  
 [WCF でのキュー](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=95143)
