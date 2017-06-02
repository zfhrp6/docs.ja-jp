---
title: "カスタム Demux | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: 41
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 41
---
# カスタム Demux
このサンプルでは、MSMQ メッセージ ヘッダーをさまざまなサービス操作にマッピングする方法を通して、<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> を使用する [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスで複数のサービス操作を使用できることを示します \(「[Windows Communication Foundation へのメッセージ キュー](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)」と「[Windows Communication Foundation でのメッセージ キュー](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)」のサンプルでは 1 つだけ使用しています\)。  
  
 このサンプルのサービスは自己ホスト型コンソール アプリケーションであるので、サービスを実行すると、キューに置かれたメッセージを受信するようすを観察できます。  
  
 サービス コントラクトは `IOrderProcessor` です。これは、キューでの使用に適した一方向サービスを定義します。  
  
```  
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
  
 MSMQ メッセージには Action ヘッダーがないので、  さまざまな MSMQ メッセージを操作コントラクトに自動的にマッピングすることはできません。  したがって、存在する操作コントラクトは 1 つだけです。  この制限を克服するために、サービスは <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> インターフェイスの <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> メソッドを実装します。  <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> メソッドによって、メッセージの特定のヘッダーを特定のサービス操作にマッピングできるようになります。  このサンプルでは、メッセージのラベル ヘッダーをサービス操作にマッピングします。  操作コントラクトの `Name` パラメータは、特定のメッセージ ラベルに対してどのサービス操作をディスパッチするかを示します。  たとえば、メッセージのラベル ヘッダーに "SubmitPurchaseOrder" が含まれている場合に、"SubmitPurchaseOrder" サービス操作を呼び出します。  
  
```  
public class OperationSelector : IDispatchOperationSelector  
{  
    public string SelectOperation(ref System.ServiceModel.Channels.Message message)  
    {  
        MsmqIntegrationMessageProperty property = MsmqIntegrationMessageProperty.Get(message);  
        return property.Label;  
    }  
}  
```  
  
 サービスは <xref:System.ServiceModel.Description.IContractBehavior> インターフェイスの <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> メソッドを実装する必要があります。次のサンプル コードを参照してください。  これによって、カスタムの `OperationSelector` がサービス フレームワークのディスパッチ ランタイムに適用されます。  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 メッセージが OperationSelector に到達するには、ディスパッチャの <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> を通過する必要があります。  既定の設定では、メッセージのアクションが、サービスによって実装されているどのコントラクトにも見つからない場合に、メッセージが拒否されます。  この検査を回避するために、`MatchAllFilterBehavior` という名前の <xref:System.ServiceModel.Description.IEndpointBehavior> を実装します。これは、次に示すように <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> を適用して、どのメッセージも `ContractFilter` を通過できるようにするものです。  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 メッセージをサービスが受信すると、ラベル ヘッダーからの情報を使用して該当するサービス操作がディスパッチされます。  メッセージの本文が逆シリアル化されて `PurchaseOrder` オブジェクトが作成されます。次のサンプル コードを参照してください。  
  
```  
[OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]  
public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
{  
    PurchaseOrder po = (PurchaseOrder)msg.Body;  
    Random statusIndexer = new Random();  
    po.Status = (OrderStates)statusIndexer.Next(3);  
    Console.WriteLine("Processing {0} ", po);  
}  
```  
  
 サービスは自己ホスト型です。  MSMQ を使用するときは、使用するキューをあらかじめ作成しておく必要があります。  手動で作成することもコードで作成することもできます。  このサンプルでは、サービスのコードの中でキューの存在を確認し、存在しない場合は作成します。  キュー名は構成ファイルから読み込まれます。  
  
```  
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
>  キュー名では、ドット \(.\) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。  [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイント アドレスでは msmq.formatname スキームが指定され、ローカル コンピューターを表す localhost が使用されます。  このスキームの後には、MSMQ 形式名のアドレス指定ガイドラインに沿って正しく書式設定されたキューのアドレスが続きます。  
  
```  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
  
```  
  
> [!NOTE]
>  このサンプルを実行するには、[メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=95143)がインストールされている必要があります。  
  
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
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。  キューが存在しない場合、サービスによってキューが作成されます。  最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。  Windows 2008 でキューを作成するには、次の手順に従います。  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。  
  
    2.  **\[機能\]** タブを展開します。  
  
    3.  **\[プライベート メッセージ キュー\]** を右クリックし、**\[新規作成\]**、**\[専用キュー\]** の順にクリックします。  
  
    4.  **\[トランザクション\]** ボックスをオンにします。  
  
    5.  新しいキューの名前として、`「ServiceModelSamplesTransacted」`と入力します。  
  
3.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  サンプルを単一コンピューター構成または複数コンピューター構成で実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
### サンプルを複数のコンピューターで実行するには  
  
1.  サービスのプログラム ファイルを、言語固有のフォルダーにある \\service\\bin\\ フォルダーからサービス コンピューターにコピーします。  
  
2.  クライアント プログラム ファイルを、言語固有のフォルダーにある \\client\\bin\\ フォルダーからクライアント コンピューターにコピーします。  
  
3.  Client.exe.config ファイルを開き、orderQueueName を変更して "." の代わりにサービス コンピューター名を指定します。  
  
4.  サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。  
  
5.  クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。  続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。  このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## 参照  
 [WCF でのキュー](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)   
 [メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=95143)