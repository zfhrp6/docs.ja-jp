---
title: "Windows Communication Foundation でのメッセージ キュー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
caps.latest.revision: "32"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6800db4e5f8dc1a0d571be3eed556503b907e16e
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="windows-communication-foundation-to-message-queuing"></a>Windows Communication Foundation でのメッセージ キュー
このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] アプリケーションでメッセージをメッセージ キュー (MSMQ) アプリケーションに送信する方法について説明します。 サービスは自己ホスト型コンソール アプリケーションであるので、キューに置かれたメッセージをサービスが受信するようすを観察できます。 サービスとクライアントは同時に実行されていなくてもかまいません。  
  
 サービスは、メッセージをキューから受信して注文を処理します。 サービスはトランザクション キューを作成し、メッセージがメッセージ ハンドラによって受信されるように設定します。次のサンプル コードを参照してください。  
  
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
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  キュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。  
  
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
  
 クライアントは、MSMQ メッセージをキューに送信するためにカスタム クライアントを順に使用します。 メッセージを受信して処理するアプリケーションが MSMQ アプリケーションであり、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] アプリケーションではないので、2 つのアプリケーション間で暗黙のサービス コントラクトはありません。 したがって、このシナリオでは Svcutil.exe ツールを使用してプロキシを作成することはできません。  
  
 カスタム クライアントは基本的に、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] バインディングを使用してメッセージを送信するすべての `MsmqIntegration` アプリケーションで同じです。 他のクライアントと異なり、サービス操作の範囲は含まれません。 メッセージ送信操作のみです。  
  
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
  
 サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。 サービスがクライアントから受信したメッセージを表示できます。 どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。 キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。 たとえば、クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。  
  
> [!NOTE]
>  このサンプルを実行するには、メッセージ キューがインストールされている必要があります。 インストール手順を参照して[メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=94968)です。  
  
### <a name="to-setup-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。 キューが存在しない場合、サービスによってキューが作成されます。 最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。 Windows 2008 でキューを作成するには、次の手順に従います。  
  
    1.  [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。  
  
    2.  展開して、**機能**タブです。  
  
    3.  右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。  
  
    4.  チェック、**トランザクション**ボックス。  
  
    5.  入力`ServiceModelSamplesTransacted`として、新しいキューの名前。  
  
3.  ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。  
  
4.  単一コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。  
  
### <a name="to-run-the-sample-across-computers"></a>サンプルを複数のコンピューターで実行するには  
  
1.  サービスのプログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。  
  
2.  クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。  
  
3.  Client.exe.config ファイルで、クライアント エンドポイントのアドレスを変更して "." の代わりにサービス コンピューター名を指定します。  
  
4.  サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。  
  
5.  クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a>関連項目  
 [方法: WCF エンドポイントでメッセージを交換して、メッセージ キュー アプリケーション](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=94968)
