---
title: セッションとキュー
ms.date: 03/30/2017
ms.assetid: 47d7c5c2-1e6f-4619-8003-a0ff67dcfbd6
ms.openlocfilehash: ee360f7a95529142437764a74c9f6261221af8b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506830"
---
# <a name="sessions-and-queues"></a><span data-ttu-id="eed17-102">セッションとキュー</span><span class="sxs-lookup"><span data-stu-id="eed17-102">Sessions and Queues</span></span>
<span data-ttu-id="eed17-103">このサンプルでは、メッセージ キュー (MSMQ) トランスポートを介して、キュー通信で一連の関連メッセージを送受信する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="eed17-103">This sample demonstrates how to send and receive a set of related messages in queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="eed17-104">このサンプルでは、`netMsmqBinding` バインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="eed17-104">This sample uses the `netMsmqBinding` binding.</span></span> <span data-ttu-id="eed17-105">サービスは自己ホスト型コンソール アプリケーションであるので、キューに置かれたメッセージをサービスが受信するようすを観察できます。</span><span class="sxs-lookup"><span data-stu-id="eed17-105">The service is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="eed17-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="eed17-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="eed17-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="eed17-107">The samples may already be installed on your machine.</span></span> <span data-ttu-id="eed17-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="eed17-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="eed17-109">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="eed17-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="eed17-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="eed17-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Session`  
  
 <span data-ttu-id="eed17-111">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="eed17-111">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="eed17-112">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="eed17-112">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="eed17-113">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="eed17-113">The service receives messages from the queue.</span></span> <span data-ttu-id="eed17-114">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="eed17-114">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="eed17-115">クライアントは、グループ内で相互に関連する一連のメッセージを送信する場合があります。</span><span class="sxs-lookup"><span data-stu-id="eed17-115">Sometimes, a client sends a set of messages that are related to each other in a group.</span></span> <span data-ttu-id="eed17-116">メッセージを一緒に処理するか、または特定の順序で処理する必要がある場合は、キューを使用すると、単一の受信側アプリケーションでの処理に対応するためにメッセージをグループ化できます。</span><span class="sxs-lookup"><span data-stu-id="eed17-116">When messages must be processed together or in a specified order, a queue can be used to group them together, for processing by a single receiving application.</span></span> <span data-ttu-id="eed17-117">このことは、サーバーのグループに複数の受信側アプリケーションが存在する場合、メッセージのグループを同一の受信側アプリケーションで確実に処理する必要があるときに特に重要です。</span><span class="sxs-lookup"><span data-stu-id="eed17-117">This is particularly important when there are several receiving applications on a group of servers and it is necessary to ensure that a group of messages is processed by the same receiving application.</span></span> <span data-ttu-id="eed17-118">キューに置かれたセッションは、同時処理を行う必要がある一連の関連メッセージを送受信する目的で使用される機構です。</span><span class="sxs-lookup"><span data-stu-id="eed17-118">Queued sessions are a mechanism used to send and receive a related set of messages that must get processed all at once.</span></span> <span data-ttu-id="eed17-119">キューに置かれたセッションには、このパターンを表すトランザクションが必要です。</span><span class="sxs-lookup"><span data-stu-id="eed17-119">Queued sessions require a transaction to exhibit this pattern.</span></span>  
  
 <span data-ttu-id="eed17-120">このサンプルでは、クライアントは、複数のメッセージを単一トランザクションのスコープ内にあるセッションの一部として、サービスに送信します。</span><span class="sxs-lookup"><span data-stu-id="eed17-120">In the sample, the client sends a number of messages to the service as part of a session within the scope of a single transaction.</span></span>  
  
 <span data-ttu-id="eed17-121">サービス コントラクトは `IOrderTaker` です。これは、キューでの使用に適した一方向サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="eed17-121">The service contract is `IOrderTaker`, which defines a one-way service that is suitable for use with queues.</span></span> <span data-ttu-id="eed17-122">このコントラクトに使用される <xref:System.ServiceModel.SessionMode> は、次のサンプル コードで示すように、メッセージがセッションの一部であることを示します。</span><span class="sxs-lookup"><span data-stu-id="eed17-122">The <xref:System.ServiceModel.SessionMode> used in the contract shown in the following sample code indicates that the messages are part of the session.</span></span>  

```csharp
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples", SessionMode=SessionMode.Required)]  
public interface IOrderTaker  
{  
    [OperationContract(IsOneWay = true)]  
    void OpenPurchaseOrder(string customerId);  
  
    [OperationContract(IsOneWay = true)]  
    void AddProductLineItem(string productId, int quantity);  
  
    [OperationContract(IsOneWay = true)]  
    void EndPurchaseOrder();  
}  
```

 <span data-ttu-id="eed17-123">このサービスは、最初の操作をトランザクションに参加させ、トランザクションを自動的に完了しないように、サービス操作を定義します。</span><span class="sxs-lookup"><span data-stu-id="eed17-123">The service defines service operations in such a way that the first operation enlists in a transaction but does not automatically complete the transaction.</span></span> <span data-ttu-id="eed17-124">後続の操作も同じトランザクションに参加しますが、同様に自動的に完了しません。</span><span class="sxs-lookup"><span data-stu-id="eed17-124">Subsequent operations also enlist in the same transaction but do not automatically complete.</span></span> <span data-ttu-id="eed17-125">セッションの最後の操作は、トランザクションを自動的に完了します。</span><span class="sxs-lookup"><span data-stu-id="eed17-125">The last operation in the session automatically completes the transaction.</span></span> <span data-ttu-id="eed17-126">つまりサービス コントラクトでは、複数の操作呼び出しで同じトランザクションが使用されます。</span><span class="sxs-lookup"><span data-stu-id="eed17-126">Thus, the same transaction is used for several operation invocations in the service contract.</span></span> <span data-ttu-id="eed17-127">任意の操作で例外がスローされた場合は、トランザクションはロールバックされてセッションはキューに戻ります。</span><span class="sxs-lookup"><span data-stu-id="eed17-127">If any of the operations throw an exception, then the transaction rolls back and the session is put back into the queue.</span></span> <span data-ttu-id="eed17-128">最後の操作が正常に完了すると、トランザクションはコミットされます。</span><span class="sxs-lookup"><span data-stu-id="eed17-128">Upon successful completion of the last operation, the transaction is committed.</span></span> <span data-ttu-id="eed17-129">このサービスでは `PerSession` として <xref:System.ServiceModel.InstanceContextMode> を使用します。セッション内のすべてのメッセージをサービスの同じインスタンスで受信するためです。</span><span class="sxs-lookup"><span data-stu-id="eed17-129">The service uses `PerSession` as the <xref:System.ServiceModel.InstanceContextMode> to receive all messages in a session on the same instance of the service.</span></span>  

```csharp
[ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
public class OrderTakerService : IOrderTaker  
{  
    PurchaseOrder po;  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                 TransactionAutoComplete = false)]  
    public void OpenPurchaseOrder(string customerId)  
    {  
        Console.WriteLine("Creating purchase order");  
        po = new PurchaseOrder(customerId);  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = false)]  
    public void AddProductLineItem(string productId, int quantity)  
    {  
        po.AddProductLineItem(productId, quantity);  
        Console.WriteLine("Product " + productId + " quantity " +   
                            quantity + " added to purchase order");  
    }  
  
    [OperationBehavior(TransactionScopeRequired = true,   
                                  TransactionAutoComplete = true)]  
    public void EndPurchaseOrder()  
    {  
       Console.WriteLine("Purchase Order Completed");  
       Console.WriteLine();  
       Console.WriteLine(po.ToString());  
    }  
}  
```

 <span data-ttu-id="eed17-130">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="eed17-130">The service is self hosted.</span></span> <span data-ttu-id="eed17-131">MSMQ トランスポートを使用する場合、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed17-131">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="eed17-132">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="eed17-132">This can be done manually or through code.</span></span> <span data-ttu-id="eed17-133">このサンプルでは、キューの存在を確認して、必要な場合は作成するための <xref:System.Messaging> コードがサービスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="eed17-133">In this sample, the service contains <xref:System.Messaging> code to check for the existence of the queue and creates it, if necessary.</span></span> <span data-ttu-id="eed17-134">キュー名は、<xref:System.Configuration.ConfigurationManager.AppSettings%2A> クラスを使用して構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="eed17-134">The queue name is read from the configuration file using the <xref:System.Configuration.ConfigurationManager.AppSettings%2A> class.</span></span>  

```csharp
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName, true);  
  
    // Create a ServiceHost for the OrderTakerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(OrderTakerService)))  
    {  
        // Open the ServiceHost to create listeners and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
  
        // Close the ServiceHost to shutdown the service.  
        serviceHost.Close();   
    }  
}  
```

 <span data-ttu-id="eed17-135">MSMQ キュー名は、構成ファイルの appSettings セクションで指定されます。</span><span class="sxs-lookup"><span data-stu-id="eed17-135">The MSMQ queue name is specified in an appSettings section of the configuration file.</span></span> <span data-ttu-id="eed17-136">サービスのエンドポイントは、構成ファイルの system.serviceModel セクションで定義されます。このエンドポイントは `netMsmqBinding` バインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="eed17-136">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
```xml  
<appSettings>  
  <!-- Use appSetting to configure MSMQ queue name. -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesSession" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
        behaviorConfiguration="CalculatorServiceBehavior">  
      ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesSession"  
                binding="netMsmqBinding"  
                contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
      ...  
    </service>  
  </services>  
  ...  
<system.serviceModel>  
```  
  
 <span data-ttu-id="eed17-137">クライアントはトランザクション スコープを作成します。</span><span class="sxs-lookup"><span data-stu-id="eed17-137">The client creates a transaction scope.</span></span> <span data-ttu-id="eed17-138">セッション内のすべてのメッセージは、トランザクション スコープ内のキューに送信され、すべてのメッセージが成功か失敗かを示すアトミックな単位として扱われます。</span><span class="sxs-lookup"><span data-stu-id="eed17-138">All messages in the session are sent to the queue within the transaction scope, causing it to be treated as an atomic unit where all messages succeed or fail.</span></span> <span data-ttu-id="eed17-139">トランザクションは <xref:System.Transactions.TransactionScope.Complete%2A> を呼び出してコミットされます。</span><span class="sxs-lookup"><span data-stu-id="eed17-139">The transaction is committed by calling <xref:System.Transactions.TransactionScope.Complete%2A>.</span></span>  

```csharp
//Create a transaction scope.  
using (TransactionScope scope = new TransactionScope(TransactionScopeOption.Required))  
{  
    // Create a client with given client endpoint configuration.  
    OrderTakerClient client = new OrderTakerClient("OrderTakerEndpoint");  
    // Open a purchase order.  
    client.OpenPurchaseOrder("somecustomer.com");  
    Console.WriteLine("Purchase Order created");  
  
    // Add product line items.  
    Console.WriteLine("Adding 10 quantities of blue widget");  
    client.AddProductLineItem("Blue Widget", 10);  
  
    Console.WriteLine("Adding 23 quantities of red widget");  
    client.AddProductLineItem("Red Widget", 23);  
  
    // Close the purchase order.  
    Console.WriteLine("Closing the purchase order");  
    client.EndPurchaseOrder();  
  
    //Closing the client gracefully closes the connection and cleans up resources.  
    client.Close();                  
  
    // Complete the transaction.  
    scope.Complete();  
}  
```

> [!NOTE]
>  <span data-ttu-id="eed17-140">セッション内のすべてのメッセージに対して使用できるトランザクションは 1 つだけです。さらに、トランザクションをコミットする前にセッション内のすべてのメッセージを送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed17-140">You can use only a single transaction for all messages in the session and all messages in the session must be sent before committing the transaction.</span></span> <span data-ttu-id="eed17-141">クライアントを閉じると、セッションも閉じられます。</span><span class="sxs-lookup"><span data-stu-id="eed17-141">Closing the client closes the session.</span></span> <span data-ttu-id="eed17-142">したがって、トランザクションが完了する前にクライアントを閉じ、セッション内のすべてのメッセージをキューに送信する必要があります。</span><span class="sxs-lookup"><span data-stu-id="eed17-142">Therefore, the client has to be closed before the transaction is completed to send all messages in the session to the queue.</span></span>  
  
 <span data-ttu-id="eed17-143">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="eed17-143">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="eed17-144">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="eed17-144">You can see the service receive messages from the client.</span></span> <span data-ttu-id="eed17-145">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="eed17-145">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="eed17-146">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="eed17-146">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="eed17-147">クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="eed17-147">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
 <span data-ttu-id="eed17-148">クライアント側</span><span class="sxs-lookup"><span data-stu-id="eed17-148">On the client.</span></span>  
  
```  
Purchase Order created  
Adding 10 quantities of blue widget  
Adding 23 quantities of red widget  
Closing the purchase order  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="eed17-149">サービス側</span><span class="sxs-lookup"><span data-stu-id="eed17-149">On the service.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Creating purchase order  
Product Blue Widget quantity 10 added to purchase order  
Product Red Widget quantity 23 added to purchase order  
Purchase Order Completed  
  
Purchase Order: 7c86fef0-2306-4c51-80e6-bcabcc1a6e5e  
        Customer: somecustomer.com  
        OrderDetails  
                Order LineItem: 10 of Blue Widget @unit price: $2985  
                Order LineItem: 23 of Red Widget @unit price: $156  
        Total cost of this order: $33438  
        Order status: Pending  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="eed17-150">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="eed17-150">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="eed17-151">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="eed17-151">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="eed17-152">C#、C++、または Visual Basic .NET のバージョンのソリューションをビルドするの指示に従って、 [Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="eed17-152">To build the C#, C++, or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="eed17-153">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="eed17-153">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="eed17-154"><xref:System.ServiceModel.NetMsmqBinding> を使用する場合の既定では、トランスポート セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="eed17-154">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="eed17-155">つまり、MSMQ トランスポート セキュリティに関連する 2 つのプロパティがある<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>と<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`既定では、認証モードに設定`Windows`保護レベルに設定されていると`Sign`です。</span><span class="sxs-lookup"><span data-stu-id="eed17-155">There are two relevant properties for MSMQ transport security namely, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="eed17-156">MSMQ の認証機能と署名機能を利用するには、ドメインに MSMQ があることと、MSMQ に関する Active Directory の統合オプションがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="eed17-156">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="eed17-157">この条件を満たしていないコンピューターでこのサンプルを実行すると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="eed17-157">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="eed17-158">ワークグループに属しているコンピューターまたは Active Directory 統合のないコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="eed17-158">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="eed17-159">ドメインに属していないコンピューター、または Active Directory 統合がインストールされていないコンピューターを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを `None` にします。この構成の例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="eed17-159">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <services>  
        <service name="Microsoft.ServiceModel.Samples.OrderTakerService"  
                 behaviorConfiguration="OrderTakerServiceBehavior">  
          <host>  
            <baseAddresses>  
              <add baseAddress=  
             "http://localhost:8000/ServiceModelSamples/service"/>  
            </baseAddresses>  
          </host>  
          <!-- Define NetMsmqEndpoint -->  
          <endpoint  
              address=  
            "net.msmq://localhost/private/ServiceModelSamplesSession"  
              binding="netMsmqBinding"  
              bindingConfiguration="Binding1"  
           contract="Microsoft.ServiceModel.Samples.IOrderTaker" />  
          <!-- The mex endpoint is exposed at-->      
          <!--http://localhost:8000/ServiceModelSamples/service/mex. -->  
          <endpoint address="mex"  
                    binding="mexHttpBinding"  
                    contract="IMetadataExchange" />  
        </service>  
      </services>  
  
      <bindings>  
        <netMsmqBinding>  
          <binding name="Binding1">  
            <security mode="None" />  
          </binding>  
        </netMsmqBinding>  
      </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="OrderTakerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="eed17-160">サーバーとクライアントの両方の構成を変更したことを確認してから、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="eed17-160">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="eed17-161">セキュリティ モードを `None` に設定することは、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>、および `Message` のセキュリティを `None` に設定することと同じです。</span><span class="sxs-lookup"><span data-stu-id="eed17-161">Setting security mode to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eed17-162">関連項目</span><span class="sxs-lookup"><span data-stu-id="eed17-162">See Also</span></span>
