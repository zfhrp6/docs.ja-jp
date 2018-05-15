---
title: Windows Communication Foundation でのメッセージ キュー
ms.date: 03/30/2017
ms.assetid: 78d0d0c9-648e-4d4a-8f0a-14d9cafeead9
ms.openlocfilehash: 0864098a55cbd7b43100bf9e0a1836e749eb2bc9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="windows-communication-foundation-to-message-queuing"></a><span data-ttu-id="32371-102">Windows Communication Foundation でのメッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="32371-102">Windows Communication Foundation to Message Queuing</span></span>
<span data-ttu-id="32371-103">このサンプルでは、Windows Communication Foundation (WCF) アプリケーションがメッセージ キュー (MSMQ) アプリケーションにメッセージを送信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="32371-103">This sample demonstrates how a Windows Communication Foundation (WCF) application can send a message to a Message Queuing (MSMQ) application.</span></span> <span data-ttu-id="32371-104">サービスは自己ホスト型コンソール アプリケーションであるので、キューに置かれたメッセージをサービスが受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="32371-104">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span> <span data-ttu-id="32371-105">サービスとクライアントは同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="32371-105">The service and client do not have to be running at the same time.</span></span>  
  
 <span data-ttu-id="32371-106">サービスは、メッセージをキューから受信して注文を処理します。</span><span class="sxs-lookup"><span data-stu-id="32371-106">The service receives messages from the queue and processes orders.</span></span> <span data-ttu-id="32371-107">サービスはトランザクション キューを作成し、メッセージがメッセージ ハンドラによって受信されるように設定します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32371-107">The service creates a transactional queue and sets up a message received message handler, as shown in the following sample code.</span></span>  

```csharp
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

 <span data-ttu-id="32371-108">メッセージがキュー内で受信されると、メッセージ ハンドラ `ProcessOrder` が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="32371-108">When a message is received in the queue, the message handler `ProcessOrder` is invoked.</span></span>  

```csharp
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

 <span data-ttu-id="32371-109">サービスは MSMQ メッセージ本文から `ProcessOrder` を抽出し、注文を処理します。</span><span class="sxs-lookup"><span data-stu-id="32371-109">The service extracts the `ProcessOrder` from the MSMQ message body, and processes the order.</span></span>  
  
 <span data-ttu-id="32371-110">MSMQ キュー名は、構成ファイルの appSettings セクションに指定されます。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="32371-110">The MSMQ queue name is specified in an appSettings section of the configuration file, as shown in the following sample configuration.</span></span>  
  
```xml  
<appSettings>  
    <add key="orderQueueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="32371-111">キュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="32371-111">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span>  
  
 <span data-ttu-id="32371-112">クライアントは発注書を作成してトランザクションのスコープ内に送信します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="32371-112">The client creates a purchase order and submits the purchase order within the scope of a transaction, as shown in the following sample code.</span></span>  

```csharp
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

 <span data-ttu-id="32371-113">クライアントは、MSMQ メッセージをキューに送信するためにカスタム クライアントを順に使用します。</span><span class="sxs-lookup"><span data-stu-id="32371-113">The client uses a custom client in-order to send the MSMQ message to the queue.</span></span> <span data-ttu-id="32371-114">受信してメッセージを処理するアプリケーションは、MSMQ アプリケーションと WCF アプリケーションではありませんは暗黙のサービス コントラクト、2 つのアプリケーション間です。</span><span class="sxs-lookup"><span data-stu-id="32371-114">Because the application that receives and processes the message is an MSMQ application and not a WCF application, there is no implicit service contract between the two applications.</span></span> <span data-ttu-id="32371-115">したがって、このシナリオでは Svcutil.exe ツールを使用してプロキシを作成することはできません。</span><span class="sxs-lookup"><span data-stu-id="32371-115">So, we cannot create a proxy using the Svcutil.exe tool in this scenario.</span></span>  
  
 <span data-ttu-id="32371-116">カスタムのクライアントには基本的を使用するすべての WCF アプリケーションの同じ、`MsmqIntegration`メッセージを送信するバインディング。</span><span class="sxs-lookup"><span data-stu-id="32371-116">The custom client is essentially the same for all WCF applications that use the `MsmqIntegration` binding to send messages.</span></span> <span data-ttu-id="32371-117">他のクライアントと異なり、サービス操作の範囲は含まれません。</span><span class="sxs-lookup"><span data-stu-id="32371-117">Unlike other clients, it does not include a range of service operations.</span></span> <span data-ttu-id="32371-118">メッセージ送信操作のみです。</span><span class="sxs-lookup"><span data-stu-id="32371-118">It is a submit message operation only.</span></span>  

```csharp
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

 <span data-ttu-id="32371-119">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="32371-119">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="32371-120">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="32371-120">You can see the service receive messages from the client.</span></span> <span data-ttu-id="32371-121">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="32371-121">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="32371-122">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="32371-122">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="32371-123">たとえば、クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="32371-123">For example, you could run the client, shut it down, and then start up the service and it would still receive its messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="32371-124">このサンプルを実行するには、メッセージ キューがインストールされている必要があります。</span><span class="sxs-lookup"><span data-stu-id="32371-124">This sample requires the installation of Message Queuing.</span></span> <span data-ttu-id="32371-125">インストール手順を参照して[メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=94968)です。</span><span class="sxs-lookup"><span data-stu-id="32371-125">See the installation instructions in [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=94968).</span></span>  
  
### <a name="to-setup-build-and-run-the-sample"></a><span data-ttu-id="32371-126">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="32371-126">To setup, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="32371-127">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="32371-127">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="32371-128">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="32371-128">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="32371-129">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="32371-129">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="32371-130">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="32371-130">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="32371-131">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="32371-131">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="32371-132">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="32371-132">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="32371-133">展開して、**機能**タブです。</span><span class="sxs-lookup"><span data-stu-id="32371-133">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="32371-134">右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。</span><span class="sxs-lookup"><span data-stu-id="32371-134">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="32371-135">チェック、**トランザクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="32371-135">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="32371-136">入力`ServiceModelSamplesTransacted`として、新しいキューの名前。</span><span class="sxs-lookup"><span data-stu-id="32371-136">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="32371-137">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="32371-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="32371-138">単一コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="32371-138">To run the sample in a single-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="32371-139">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="32371-139">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="32371-140">サービスのプログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="32371-140">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="32371-141">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="32371-141">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="32371-142">Client.exe.config ファイルで、クライアント エンドポイントのアドレスを変更して "." の代わりにサービス コンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="32371-142">In the Client.exe.config file, change the client endpoint address to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="32371-143">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="32371-143">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="32371-144">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="32371-144">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="32371-145">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="32371-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="32371-146">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="32371-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="32371-147">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="32371-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="32371-148">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="32371-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\WcfToMsmq`  
  
## <a name="see-also"></a><span data-ttu-id="32371-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="32371-149">See Also</span></span>  
 [<span data-ttu-id="32371-150">方法 : WCF エンドポイントとメッセージ キュー アプリケーションを使用してメッセージを交換する</span><span class="sxs-lookup"><span data-stu-id="32371-150">How to: Exchange Messages with WCF Endpoints and Message Queuing Applications</span></span>](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [<span data-ttu-id="32371-151">メッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="32371-151">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=94968)
