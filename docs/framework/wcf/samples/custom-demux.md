---
title: "カスタム Demux"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc54065c-518e-4146-b24a-0fe00038bfa7
caps.latest.revision: "41"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 5d4a460adfb8076f5d2c0fe273511e6de80be4ec
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="custom-demux"></a><span data-ttu-id="af892-102">カスタム Demux</span><span class="sxs-lookup"><span data-stu-id="af892-102">Custom Demux</span></span>
<span data-ttu-id="af892-103">このサンプルでは、MSMQ メッセージ ヘッダーをさまざまなサービス操作にマップする方法を[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]を使用するサービス<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>で示したように 1 つのサービス操作の使用に限定されない、[メッセージ キューをWindows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)と[メッセージ キューへの Windows Communication Foundation](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="af892-103">This sample demonstrates how MSMQ message headers can be mapped to different service operations so that [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services that use <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> are not limited to using one service operation as demonstrated in the [Message Queuing to Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md) and [Windows Communication Foundation to Message Queuing](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md) samples.</span></span>  
  
 <span data-ttu-id="af892-104">このサンプルのサービスは自己ホスト型コンソール アプリケーションであるので、サービスを実行すると、キューに置かれたメッセージを受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="af892-104">The service in this sample is a self-hosted console application to enable you to observe the service that receives queued messages.</span></span>  
  
 <span data-ttu-id="af892-105">サービス コントラクトは `IOrderProcessor` です。これは、キューでの使用に適した一方向サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="af892-105">The service contract is `IOrderProcessor`, and defines a one-way service that is suitable for use with queues.</span></span>  
  
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
  
 <span data-ttu-id="af892-106">MSMQ メッセージには Action ヘッダーがないので、</span><span class="sxs-lookup"><span data-stu-id="af892-106">An MSMQ message does not have an Action header.</span></span> <span data-ttu-id="af892-107">さまざまな MSMQ メッセージを操作コントラクトに自動的にマッピングすることはできません。</span><span class="sxs-lookup"><span data-stu-id="af892-107">It is not possible to map different MSMQ messages to operation contracts automatically.</span></span> <span data-ttu-id="af892-108">したがって、存在する操作コントラクトは 1 つだけです。</span><span class="sxs-lookup"><span data-stu-id="af892-108">Therefore, there can be only one operation contract.</span></span> <span data-ttu-id="af892-109">この制限を克服するために、サービスは <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> インターフェイスの <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="af892-109">To overcome this limitation, the service implements the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method of the <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector> interface.</span></span> <span data-ttu-id="af892-110"><xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> メソッドによって、メッセージの特定のヘッダーを特定のサービス操作にマッピングできるようになります。</span><span class="sxs-lookup"><span data-stu-id="af892-110">The <xref:System.ServiceModel.Dispatcher.IDispatchOperationSelector.SelectOperation%2A> method enables the service to map a given header of the message to a particular service operation.</span></span> <span data-ttu-id="af892-111">このサンプルでは、メッセージのラベル ヘッダーをサービス操作にマッピングします。</span><span class="sxs-lookup"><span data-stu-id="af892-111">In this sample, the message's label header is mapped to the service operations.</span></span> <span data-ttu-id="af892-112">操作コントラクトの `Name` パラメータは、特定のメッセージ ラベルに対してどのサービス操作をディスパッチするかを示します。</span><span class="sxs-lookup"><span data-stu-id="af892-112">The `Name` parameter of the operation contract determines which service operation must be dispatched for a given message label.</span></span> <span data-ttu-id="af892-113">たとえば、メッセージのラベル ヘッダーに "SubmitPurchaseOrder" が含まれている場合に、"SubmitPurchaseOrder" サービス操作を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="af892-113">For example, if the message's label header contains "SubmitPurchaseOrder", the "SubmitPurchaseOrder" service operation is invoked.</span></span>  
  
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
  
 <span data-ttu-id="af892-114">サービスは <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> インターフェイスの <xref:System.ServiceModel.Description.IContractBehavior> メソッドを実装する必要があります。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af892-114">The service must implement the <xref:System.ServiceModel.Description.IContractBehavior.ApplyDispatchBehavior%28System.ServiceModel.Description.ContractDescription%2CSystem.ServiceModel.Description.ServiceEndpoint%2CSystem.ServiceModel.Dispatcher.DispatchRuntime%29> method of the <xref:System.ServiceModel.Description.IContractBehavior> interface as shown in the following sample code.</span></span> <span data-ttu-id="af892-115">これによって、カスタムの `OperationSelector` がサービス フレームワークのディスパッチ ランタイムに適用されます。</span><span class="sxs-lookup"><span data-stu-id="af892-115">This applies the custom `OperationSelector` to the service framework dispatch runtime.</span></span>  
  
```  
void IContractBehavior.ApplyDispatchBehavior(ContractDescription description, ServiceEndpoint endpoint, DispatchRuntime dispatch)  
{  
    dispatch.OperationSelector = new OperationSelector();  
}  
```  
  
 <span data-ttu-id="af892-116">メッセージが OperationSelector に到達するには、ディスパッチャの <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> を通過する必要があります。</span><span class="sxs-lookup"><span data-stu-id="af892-116">A message must pass through the dispatcher's <xref:System.ServiceModel.Dispatcher.EndpointDispatcher.ContractFilter%2A> before getting to the OperationSelector.</span></span> <span data-ttu-id="af892-117">既定の設定では、メッセージのアクションが、サービスによって実装されているどのコントラクトにも見つからない場合に、メッセージが拒否されます。</span><span class="sxs-lookup"><span data-stu-id="af892-117">By default a message is rejected if its action cannot be found on any contract implemented by the service.</span></span> <span data-ttu-id="af892-118">この検査を回避するために、<xref:System.ServiceModel.Description.IEndpointBehavior> という名前の `MatchAllFilterBehavior` を実装します。これは、次に示すように `ContractFilter` を適用して、どのメッセージも <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> を通過できるようにするものです。</span><span class="sxs-lookup"><span data-stu-id="af892-118">To avoid this check, we implement an <xref:System.ServiceModel.Description.IEndpointBehavior> named `MatchAllFilterBehavior`, which allows any message to pass through the `ContractFilter` by applying the <xref:System.ServiceModel.Dispatcher.MatchAllMessageFilter> as follows.</span></span>  
  
```  
public void ApplyDispatchBehavior(ServiceEndpoint serviceEndpoint, EndpointDispatcher endpointDispatcher)  
{  
    endpointDispatcher.ContractFilter = new MatchAllMessageFilter();  
}  
```  
  
 <span data-ttu-id="af892-119">メッセージをサービスが受信すると、ラベル ヘッダーからの情報を使用して該当するサービス操作がディスパッチされます。</span><span class="sxs-lookup"><span data-stu-id="af892-119">When a message is received by the service, the appropriate service operation is dispatched using the information provided by the label header.</span></span> <span data-ttu-id="af892-120">メッセージの本文が逆シリアル化されて `PurchaseOrder` オブジェクトが作成されます。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="af892-120">The body of the message is deserialized into a `PurchaseOrder` object, as shown in the following sample code.</span></span>  
  
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
  
 <span data-ttu-id="af892-121">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="af892-121">The service is self-hosted.</span></span> <span data-ttu-id="af892-122">MSMQ を使用するときは、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="af892-122">When using the MSMQ, the queue that is used must be created in advance.</span></span> <span data-ttu-id="af892-123">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="af892-123">This can be done manually or through code.</span></span> <span data-ttu-id="af892-124">このサンプルでは、サービスのコードの中でキューの存在を確認し、存在しない場合は作成します。</span><span class="sxs-lookup"><span data-stu-id="af892-124">In this sample, the service contains code to check for the existence of the queue and creates it if the queue does not exist.</span></span> <span data-ttu-id="af892-125">キュー名は構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="af892-125">The queue name is read from the configuration file.</span></span>  
  
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
  
 <span data-ttu-id="af892-126">MSMQ キュー名は、構成ファイルの appSettings セクションで指定されます。</span><span class="sxs-lookup"><span data-stu-id="af892-126">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af892-127">キュー名では、ドット (.) を使用してローカル コンピューターを表し、バックスラッシュを使用してパスを区切ります。</span><span class="sxs-lookup"><span data-stu-id="af892-127">The queue name uses a dot (.) for the local computer and backslash separators in its path.</span></span> <span data-ttu-id="af892-128">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] エンドポイント アドレスでは msmq.formatname スキームが指定され、ローカル コンピューターを表す localhost が使用されます。</span><span class="sxs-lookup"><span data-stu-id="af892-128">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] endpoint address specifies a msmq.formatname scheme, and uses localhost for the local computer.</span></span> <span data-ttu-id="af892-129">このスキームの後には、MSMQ 形式名のアドレス指定ガイドラインに沿って正しく書式設定されたキューのアドレスが続きます。</span><span class="sxs-lookup"><span data-stu-id="af892-129">What follows the scheme is a properly formatted queue address according to the MSMQ Format name addressing guidelines.</span></span>  
  
```xml  
<appSettings>  
    <!-- Use appSetting to configure the MSMQ queue name. -->  
    <add key="queueName" value=".\private$\Orders" />  
</appSettings>  
```  
  
> [!NOTE]
>  <span data-ttu-id="af892-130">このサンプルのインストールが必要[メッセージ キュー](http://go.microsoft.com/fwlink/?LinkId=95143)です。</span><span class="sxs-lookup"><span data-stu-id="af892-130">This sample requires the installation of [Message Queuing](http://go.microsoft.com/fwlink/?LinkId=95143).</span></span>  
  
 <span data-ttu-id="af892-131">サービスを開始してクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="af892-131">Start the service and run the client.</span></span>  
  
 <span data-ttu-id="af892-132">クライアントには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="af892-132">The following output is seen on the client.</span></span>  
  
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
  
 <span data-ttu-id="af892-133">サービスには、次の出力が表示されます。</span><span class="sxs-lookup"><span data-stu-id="af892-133">The following output must be seen on the service.</span></span>  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af892-134">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="af892-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="af892-135">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="af892-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="af892-136">サービスを最初に実行すると、サービスはキューが存在するかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="af892-136">If the service is run first, it will check to ensure that the queue is present.</span></span> <span data-ttu-id="af892-137">キューが存在しない場合、サービスによってキューが作成されます。</span><span class="sxs-lookup"><span data-stu-id="af892-137">If the queue is not present, the service will create one.</span></span> <span data-ttu-id="af892-138">最初にサービスを実行してキューを作成することも、MSMQ キュー マネージャーでキューを作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="af892-138">You can run the service first to create the queue, or you can create one via the MSMQ Queue Manager.</span></span> <span data-ttu-id="af892-139">Windows 2008 でキューを作成するには、次の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="af892-139">Follow these steps to create a queue in Windows 2008.</span></span>  
  
    1.  <span data-ttu-id="af892-140">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] でサーバー マネージャーを開きます。</span><span class="sxs-lookup"><span data-stu-id="af892-140">Open Server Manager in [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].</span></span>  
  
    2.  <span data-ttu-id="af892-141">展開して、**機能**タブです。</span><span class="sxs-lookup"><span data-stu-id="af892-141">Expand the **Features** tab.</span></span>  
  
    3.  <span data-ttu-id="af892-142">右クリック**プライベート メッセージ キュー**を選択して**新規**、**プライベート キュー**です。</span><span class="sxs-lookup"><span data-stu-id="af892-142">Right-click **Private Message Queues**, and select **New**, **Private Queue**.</span></span>  
  
    4.  <span data-ttu-id="af892-143">チェック、**トランザクション**ボックス。</span><span class="sxs-lookup"><span data-stu-id="af892-143">Check the **Transactional** box.</span></span>  
  
    5.  <span data-ttu-id="af892-144">入力`ServiceModelSamplesTransacted`として、新しいキューの名前。</span><span class="sxs-lookup"><span data-stu-id="af892-144">Enter `ServiceModelSamplesTransacted` as the name of the new queue.</span></span>  
  
3.  <span data-ttu-id="af892-145">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="af892-145">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="af892-146">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="af892-146">To run the sample in a single- or cross- computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
### <a name="to-run-the-sample-across-computers"></a><span data-ttu-id="af892-147">サンプルを複数のコンピューターで実行するには</span><span class="sxs-lookup"><span data-stu-id="af892-147">To run the sample across computers</span></span>  
  
1.  <span data-ttu-id="af892-148">サービスのプログラム ファイルを、言語固有のフォルダーにある \service\bin\ フォルダーからサービス コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="af892-148">Copy the service program files from the \service\bin\ folder, under the language-specific folder, to the service computer.</span></span>  
  
2.  <span data-ttu-id="af892-149">クライアント プログラム ファイルを、言語固有のフォルダーにある \client\bin\ フォルダーからクライアント コンピューターにコピーします。</span><span class="sxs-lookup"><span data-stu-id="af892-149">Copy the client program files from the \client\bin\ folder, under the language-specific folder, to the client computer.</span></span>  
  
3.  <span data-ttu-id="af892-150">Client.exe.config ファイルを開き、orderQueueName を変更して "." の代わりにサービス コンピューター名を指定します。</span><span class="sxs-lookup"><span data-stu-id="af892-150">In the Client.exe.config file, change the orderQueueName to specify the service computer name instead of ".".</span></span>  
  
4.  <span data-ttu-id="af892-151">サービス コンピューターで、コマンド プロンプトから Service.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="af892-151">On the service computer, launch Service.exe from a command prompt.</span></span>  
  
5.  <span data-ttu-id="af892-152">クライアント コンピューターで、コマンド プロンプトから Client.exe を起動します。</span><span class="sxs-lookup"><span data-stu-id="af892-152">On the client computer, launch Client.exe from a command prompt.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="af892-153">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="af892-153">The samples may already be installed on your computer.</span></span> <span data-ttu-id="af892-154">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af892-154">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af892-155">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="af892-155">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af892-156">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="af892-156">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\MSMQIntegration\CustomDemux`  
  
## <a name="see-also"></a><span data-ttu-id="af892-157">関連項目</span><span class="sxs-lookup"><span data-stu-id="af892-157">See Also</span></span>  
 [<span data-ttu-id="af892-158">WCF でのキュー</span><span class="sxs-lookup"><span data-stu-id="af892-158">Queuing in WCF</span></span>](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [<span data-ttu-id="af892-159">メッセージ キュー</span><span class="sxs-lookup"><span data-stu-id="af892-159">Message Queuing</span></span>](http://go.microsoft.com/fwlink/?LinkId=95143)
