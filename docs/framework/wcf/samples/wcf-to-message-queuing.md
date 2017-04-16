---
title: "Windows Communication Foundation でのメッセージ キュー | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: 32
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 32
---
# Windows Communication Foundation でのメッセージ キュー
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションでメッセージをメッセージ キュー \(MSMQ\) アプリケーションに送信する方法について説明します。サービスは、自己ホスト型コンソール アプリケーションで、サービスがキュー内のメッセージを受信したかどうかを監視できます。サービスとクライアントは同時に実行されていなくてもかまいません。  
  
 サービスは、メッセージをキューから受信して注文を処理します。サービスはトランザクション キューを作成し、メッセージがメッセージ ハンドラによって受信されるように設定します。次のサンプル コードを参照してください。  
  
```  
static void Main(string[] args)  
{  
    if (!MessageQueue.Exists(  
              ConfigurationManager.AppSettings["queueName"]))  
       MessageQueue.Create(  
           ConfigurationManager.AppSettings["queueName"], true);  
        //Connect to the queue  
        MessageQueue Queue = new   
    MessageQueue(ConfigurationManager.AppSettings["queueName"]);  
    Queue.ReceiveCompleted +=   
                 new ReceiveCompletedEventHandler(ProcessOrder);  
    Queue.BeginReceive();  
    Console.WriteLine("Order Service is running");  
    Console.ReadLine();  
}  
  
```  
  
 メッセージがキュー内で受信されると、メッセージ ハンドラ `ProcessOrder` が呼び出されます。  
  
```  
public static void ProcessOrder(Object source,  
    ReceiveCompletedEventArgs asyncResult)  
{  
    try  
    {  
        // Connect to the queue.  
        MessageQueue Queue = (MessageQueue)source;  
        // End the asynchronous receive operation.  
        System.Messaging.Message msg =   
                     Queue.EndReceive(asyncResult.AsyncResult);  
        msg.Formatter = new System.Messaging.XmlMessageFormatter(  
                                new Type[] { typeof(PurchaseOrder) });  
        PurchaseOrder po = (PurchaseOrder) msg.Body;  
        Random statusIndexer = new Random();  
        po.Status = PurchaseOrder.OrderStates[statusIndexer.Next(3)];  
        Console.WriteLine("Processing {0} ", po);  
        Queue.BeginReceive();  
    }  
    catch (System.Exception ex)  
    {  
        Console.WriteLine(ex.Message);  
    }  
  
}  
  
```  
  
 サービスは MSMQ メッセージ本文から `ProcessOrder` を抽出し、注文を処理します。  
  
 MSMQ キュー名は、構成ファイルの appSettings セクションに指定されます。次のサンプル構成を参照してください。  
  
```  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
  
```  
  
> [!NOTE]
>  キュー名では、ドット \(.\) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。  
  
 クライアントは発注書を作成してトランザクションのスコープ内に送信します。次のサンプル コードを参照してください。  
  
```  
// Create the purchase order  
PurchaseOrder po = new PurchaseOrder();  
// Fill in the details  
...  
  
OrderProcessorClient client = new OrderProcessorClient("OrderResponseEndpoint");  
  
MsmqMessage<PurchaseOrder> ordermsg = new MsmqMessage<PurchaseOrder>(po);  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    client.SubmitPurchaseOrder(ordermsg);  
    scope.Complete();  
}  
Console.WriteLine("Order has been submitted:{0}", po);  
  
//Closing the client gracefully closes the connection and cleans up resources  
client.Close();  
  
```  
  
 クライアントは、MSMQ メッセージをキューに送信するためにカスタム クライアントを順に使用します。メッセージを受信して処理するアプリケーションが MSMQ アプリケーションであり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションではないので、2 つのアプリケーション間で暗黙のサービス コントラクトはありません。したがって、このシナリオでは Svcutil.exe ツールを使用してプロキシを作成することはできません。  
  
 カスタム クライアントは基本的に、`MsmqIntegration` バインディングを使用してメッセージを送信するすべての [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションで同じです。他のクライアントと異なり、サービス操作の範囲は含まれません。メッセージ送信操作のみです。  
  
```  
  
[System.ServiceModel.ServiceContractAttribute(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IOrderProcessor  
{  
    [OperationContract(IsOneWay = true, Action = "*")]  
    void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg);  
}  
  
public partial class OrderProcessorClient : System.ServiceModel.ClientBase<IOrderProcessor>, IOrderProcessor  
{  
    public OrderProcessorClient(){}  
  
    public OrderProcessorClient(string configurationName)  
        : base(configurationName)  
    { }  
  
    public OrderProcessorClient(System.ServiceModel.Channels.Binding binding, System.ServiceModel.EndpointAddress address)  
        : base(binding, address)  
    { }  
  
    public void SubmitPurchaseOrder(MsmqMessage<PurchaseOrder> msg)  
    {  
        base.Channel.SubmitPurchaseOrder(msg);  
    }  
}  
```  
  
 サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。サービスがクライアントからメッセージを受信するようすがわかります。どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。たとえば、クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。  
  
> [!NOTE]
>  このサンプルを実行するには、メッセージ キューがインストールされている必要があります。インストールの手順については、「[メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=94968)」を参照してください。  
  
### サンプルをセットアップ、ビルド、および実行するには  
  
1.  「[Windows Communication Foundation サンプルの 1 回限りのセットアップの手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)」が実行済みであることを確認します。  
  
2.  サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。キューが存在しない場合、サービスによってキューが作成されます。最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。Windows 2008 でキューを作成するには、次の手順に従います。  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。  
  
    2.  **\[機能\]** タブを展開します。  
  
    3.  **\[プライベート メッセージ キュー\]** を右クリックし、**\[新規作成\]**、**\[専用キュー\]** の順にクリックします。  
  
    4.  **\[トランザクション\]** ボックスをオンにします。  
  
    5.  新しいキューの名前として、「`ServiceModelSamplesTransacted`」と入力します。  
  
3.  ソリューションの C\# 版または Visual Basic .NET 版をビルドするには、「[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  単一コンピューター構成でサンプルを実行するには、「[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)」の手順に従います。  
  
### サンプルを複数のコンピューターで実行するには  
  
1.  サービスのプログラム ファイルを、言語固有のフォルダーにある \\service\\bin\\ フォルダーからサービス コンピューターにコピーします。  
  
2.  クライアント プログラム ファイルを、言語固有のフォルダーにある \\client\\bin\\ フォルダーからクライアント コンピューターにコピーします。  
  
3.  Client.exe.config ファイルで、クライアント エンドポイントのアドレスを変更して "." の代わりにサービス コンピューター名を指定します。  
  
4.  サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。  
  
5.  クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。続行する前に、次の \(既定の\) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「[.NET Framework 4 向けの Windows Communication Foundation \(WCF\) および Windows Workflow Foundation \(WF\) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780)」にアクセスして、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## 参照  
 [方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)   
 [メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=94968)