---
title: "揮発性キューによる通信"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0d012f64-51c7-41d0-8e18-c756f658ee3d
caps.latest.revision: "28"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 67fa95ffb23aee4dc3137dcab23eade8f87e9b9d
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="volatile-queued-communication"></a><span data-ttu-id="07a06-102">揮発性キューによる通信</span><span class="sxs-lookup"><span data-stu-id="07a06-102">Volatile Queued Communication</span></span>
<span data-ttu-id="07a06-103">このサンプルでは、メッセージ キュー (MSMQ) トランスポートで揮発性キューによる通信を実行する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="07a06-103">This sample demonstrates how to perform volatile queued communication over the Message Queuing (MSMQ) transport.</span></span> <span data-ttu-id="07a06-104">このサンプルでは、<xref:System.ServiceModel.NetMsmqBinding> を使用しています。</span><span class="sxs-lookup"><span data-stu-id="07a06-104">This sample uses <xref:System.ServiceModel.NetMsmqBinding>.</span></span> <span data-ttu-id="07a06-105">この場合、サービスは自己ホスト型コンソール アプリケーションで、サービスがキュー内のメッセージを受信したかどうかを監視できます。</span><span class="sxs-lookup"><span data-stu-id="07a06-105">The service in this case is a self-hosted console application to enable you to observe the service receiving queued messages.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07a06-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="07a06-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="07a06-107">キュー通信では、クライアントはサービスとの通信にキューを使用します。</span><span class="sxs-lookup"><span data-stu-id="07a06-107">In queued communication, the client communicates to the service using a queue.</span></span> <span data-ttu-id="07a06-108">厳密には、クライアントはメッセージをキューに送信します。</span><span class="sxs-lookup"><span data-stu-id="07a06-108">More precisely, the client sends messages to a queue.</span></span> <span data-ttu-id="07a06-109">サービスは、メッセージをキューから受信します。</span><span class="sxs-lookup"><span data-stu-id="07a06-109">The service receives messages from the queue.</span></span> <span data-ttu-id="07a06-110">したがって、キューを使用する通信では、サービスとクライアントが同時に実行されていなくてもかまいません。</span><span class="sxs-lookup"><span data-stu-id="07a06-110">The service and client therefore, do not have to be running at the same time to communicate using a queue.</span></span>  
  
 <span data-ttu-id="07a06-111">メッセージを保証なしで送信する場合、MSMQ ではメッセージ配信のみをベスト エフォートで実行します。これとは異なり、正確に 1 回の保証がある場合は、MSMQ はメッセージの配信を確認し、配信できない場合にはメッセージが配信できないことをユーザーに通知します。</span><span class="sxs-lookup"><span data-stu-id="07a06-111">When you send a message with no assurances, MSMQ only makes a best effort to deliver the message, unlike with Exactly Once assurances where MSMQ ensures that the message gets delivered or, if it cannot be delivered, lets you know that the message cannot be delivered.</span></span>  
  
 <span data-ttu-id="07a06-112">一部のシナリオでは、保証なしの揮発性メッセージをキューに送信する場合があります。この場合は、メッセージの損失より適切な時間での配信が重要です。</span><span class="sxs-lookup"><span data-stu-id="07a06-112">In certain scenarios, you may want to send a volatile message with no assurances over a queue, when timely delivery is more important than losing messages.</span></span> <span data-ttu-id="07a06-113">揮発性メッセージは、キュー マネージャがクラッシュすると失われます。</span><span class="sxs-lookup"><span data-stu-id="07a06-113">Volatile messages do not survive queue manager crashes.</span></span> <span data-ttu-id="07a06-114">したがって、キュー マネージャがクラッシュした場合は、揮発性メッセージの保存に使用される非トランザクション キューは残りますが、メッセージそのものは失われます。メッセージはディスク上に保存されないためです。</span><span class="sxs-lookup"><span data-stu-id="07a06-114">Therefore if the queue manager crashes, the non-transactional queue used to store volatile messages survives but the messages themselves do not because the messages are not stored on the disk.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07a06-115">MSMQ を使用するトランザクションのスコープ内では、保証なしの揮発性メッセージを送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="07a06-115">You cannot send volatile messages with no assurances within the scope of a transaction using MSMQ.</span></span> <span data-ttu-id="07a06-116">また、揮発性メッセージを送信するには非トランザクション キューを作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="07a06-116">You also must create a non-transactional queue to send volatile messages.</span></span>  
  
 <span data-ttu-id="07a06-117">このサンプルのサービス コントラクトは `IStockTicker` です。これは、キューでの使用に最適な一方向サービスを定義します。</span><span class="sxs-lookup"><span data-stu-id="07a06-117">The service contract in this sample is `IStockTicker` that defines one-way services that are best suited for use with queuing.</span></span>  
  
```  
[ServiceContract(Namespace = "http://Microsoft.ServiceModel.Samples")]  
public interface IStockTicker  
{  
    [OperationContract(IsOneWay = true)]  
    void StockTick(string symbol, float price);  
}  
```  
  
 <span data-ttu-id="07a06-118">このサービス操作は、株価情報のシンボルと価格を表示します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="07a06-118">The service operation displays the stock ticker symbol and price, as shown in the following sample code:</span></span>  
  
```  
public class StockTickerService : IStockTicker  
{  
    public void StockTick(string symbol, float price)  
    {  
        Console.WriteLine("Stock Tick {0}:{1} ", symbol, price);  
     }  
     …  
}  
```  
  
 <span data-ttu-id="07a06-119">サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="07a06-119">The service is self hosted.</span></span> <span data-ttu-id="07a06-120">MSMQ トランスポートを使用する場合、使用するキューをあらかじめ作成しておく必要があります。</span><span class="sxs-lookup"><span data-stu-id="07a06-120">When using the MSMQ transport, the queue used must be created in advance.</span></span> <span data-ttu-id="07a06-121">手動で作成することもコードで作成することもできます。</span><span class="sxs-lookup"><span data-stu-id="07a06-121">This can be done manually or through code.</span></span> <span data-ttu-id="07a06-122">このサンプルでは、キューの存在を確認して、必要な場合は作成するためのコードがサービスに含まれています。</span><span class="sxs-lookup"><span data-stu-id="07a06-122">In this sample, the service contains code to check for the existence of the queue and create it if required.</span></span> <span data-ttu-id="07a06-123">キュー名は構成ファイルから読み込まれます。</span><span class="sxs-lookup"><span data-stu-id="07a06-123">The queue name is read from the configuration file.</span></span> <span data-ttu-id="07a06-124">ベース アドレスを使って、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)サービスのプロキシを生成します。</span><span class="sxs-lookup"><span data-stu-id="07a06-124">The base address is used by the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) to generate the proxy for the service.</span></span>  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Get MSMQ queue name from app settings in configuration.  
    string queueName = ConfigurationManager.AppSettings["queueName"];  
  
    // Create the transacted MSMQ queue if necessary.  
    if (!MessageQueue.Exists(queueName))  
        MessageQueue.Create(queueName);  
  
    // Create a ServiceHost for the StockTickerService type.  
    using (ServiceHost serviceHost = new ServiceHost(typeof(StockTickerService)))  
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
  
 <span data-ttu-id="07a06-125">MSMQ キュー名は、構成ファイルの appSettings セクションに指定されます。</span><span class="sxs-lookup"><span data-stu-id="07a06-125">The MSMQ queue name is specified in the appSettings section of the configuration file.</span></span> <span data-ttu-id="07a06-126">サービスのエンドポイントは、構成ファイルの system.serviceModel セクションで定義されます。このエンドポイントは `netMsmqBinding` バインディングを指定します。</span><span class="sxs-lookup"><span data-stu-id="07a06-126">The endpoint for the service is defined in the system.serviceModel section of the configuration file and specifies the `netMsmqBinding` binding.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="07a06-127"><xref:System.Messaging> を使用してキューを作成する場合、キュー名では、ローカル コンピューターを表すのにドット (.) を使用し、パスの区切りにはバックスラッシュを使用します。</span><span class="sxs-lookup"><span data-stu-id="07a06-127">The queue name uses a dot (.) for the local machine and backslash separators in its path when creating a queue using <xref:System.Messaging>.</span></span> <span data-ttu-id="07a06-128">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] エンドポイント アドレスでは net.msmq: スキームが指定されます。ローカル コンピュータには "localhost" が使用され、そのパスにはスラッシュが先行します。</span><span class="sxs-lookup"><span data-stu-id="07a06-128">The [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] endpoint address specifies a net.msmq: scheme, uses "localhost" for the local machine and forward slashes in its path.</span></span>  
  
 <span data-ttu-id="07a06-129">メッセージの保証および持続性または揮発性についても、構成ファイルで指定します。</span><span class="sxs-lookup"><span data-stu-id="07a06-129">The assurances and durability or volatility of messages are also specified in the configuration.</span></span>  
  
```xml  
<appSettings>  
  <!-- use appSetting to configure MSMQ queue name -->  
  <add key="queueName" value=".\private$\ServiceModelSamplesVolatile" />  
</appSettings>  
  
<system.serviceModel>  
  <services>  
    <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
             behaviorConfiguration="CalculatorServiceBehavior">  
    ...  
      <!-- Define NetMsmqEndpoint -->  
      <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                binding="netMsmqBinding"  
                bindingConfiguration="volatileBinding"   
                contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
    ...  
          </service>  
  </services>  
  
  <bindings>  
    <netMsmqBinding>  
      <binding name="volatileBinding"   
             durable="false"  
           exactlyOnce="false"/>  
    </netMsmqBinding>  
  </bindings>  
  ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="07a06-130">サンプルでは非トランザクション キューを使用してキューに置かれたメッセージを送信するので、トランザクション メッセージをキューに送信することはできません。</span><span class="sxs-lookup"><span data-stu-id="07a06-130">Because the sample sends queued messages by using a non-transactional queue, transacted messages cannot be sent to the queue.</span></span>  
  
```  
// Create a client.  
Random r = new Random(137);  
  
StockTickerClient client = new StockTickerClient();  
  
float price = 43.23F;  
for (int i = 0; i < 10; i++)  
{  
    float increment = 0.01f * (r.Next(10));  
    client.StockTick("zzz" + i, price + increment);  
}  
  
//Closing the client gracefully cleans up resources.  
client.Close();  
```  
  
 <span data-ttu-id="07a06-131">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="07a06-131">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="07a06-132">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="07a06-132">You can see the service receive messages from the client.</span></span> <span data-ttu-id="07a06-133">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="07a06-133">Press ENTER in each console window to shut down the service and client.</span></span> <span data-ttu-id="07a06-134">キューが使用されているので、クライアントとサービスが同時に実行されている必要はありません。</span><span class="sxs-lookup"><span data-stu-id="07a06-134">Note that because queuing is in use, the client and service do not have to be up and running at the same time.</span></span> <span data-ttu-id="07a06-135">クライアントを実行してシャットダウンした後にサービスを起動しても、サービスはメッセージを受信します。</span><span class="sxs-lookup"><span data-stu-id="07a06-135">You can run the client, shut it down, and then start up the service and it still receives its messages.</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Stock Tick zzz0:43.25  
Stock Tick zzz1:43.23  
Stock Tick zzz2:43.28  
Stock Tick zzz3:43.3  
Stock Tick zzz4:43.23  
Stock Tick zzz5:43.25  
Stock Tick zzz6:43.25  
Stock Tick zzz7:43.24  
Stock Tick zzz8:43.32  
Stock Tick zzz9:43.3  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="07a06-136">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="07a06-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="07a06-137">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="07a06-137">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="07a06-138">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="07a06-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="07a06-139">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="07a06-139">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
 <span data-ttu-id="07a06-140"><xref:System.ServiceModel.NetMsmqBinding> を使用する場合の既定では、トランスポート セキュリティが有効です。</span><span class="sxs-lookup"><span data-stu-id="07a06-140">By default with the <xref:System.ServiceModel.NetMsmqBinding>, transport security is enabled.</span></span> <span data-ttu-id="07a06-141">MSMQ トランスポート セキュリティでは、2 つの関連するプロパティがある<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>と<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.`既定では、認証モードに設定`Windows`保護レベルに設定されていると`Sign`です。</span><span class="sxs-lookup"><span data-stu-id="07a06-141">There are two pertinent properties for MSMQ transport security, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A> and <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>`.` By default, the authentication mode is set to `Windows` and the protection level is set to `Sign`.</span></span> <span data-ttu-id="07a06-142">MSMQ の認証機能と署名機能を利用するには、ドメインに MSMQ があることと、MSMQ に関する Active Directory の統合オプションがインストールされていることが必要です。</span><span class="sxs-lookup"><span data-stu-id="07a06-142">For MSMQ to provide the authentication and signing feature, it must be part of a domain and the active directory integration option for MSMQ must be installed.</span></span> <span data-ttu-id="07a06-143">この条件を満たしていないコンピューターでこのサンプルを実行すると、エラーになります。</span><span class="sxs-lookup"><span data-stu-id="07a06-143">If you run this sample on a computer that does not satisfy these criteria you receive an error.</span></span>  
  
### <a name="to-run-the-sample-on-a-computer-joined-to-a-workgroup-or-without-active-directory-integration"></a><span data-ttu-id="07a06-144">ワークグループに属しているコンピューターまたは Active Directory 統合のないコンピューターでこのサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="07a06-144">To run the sample on a computer joined to a workgroup or without active directory integration</span></span>  
  
1.  <span data-ttu-id="07a06-145">ドメインに属していないコンピュータ、または Active Directory 統合がインストールされていないコンピュータを使用する場合は、トランスポート セキュリティをオフにします。オフにするには、認証モードと保護レベルを `None` にします。この構成コードの例を次に示します。</span><span class="sxs-lookup"><span data-stu-id="07a06-145">If your computer is not part of a domain or does not have active directory integration installed, turn off transport security by setting the authentication mode and protection level to `None` as shown in the following sample configuration code:</span></span>  
  
    ```xml  
    <system.serviceModel>  
        <services>  
          <service name="Microsoft.ServiceModel.Samples.StockTickerService"  
                   behaviorConfiguration="StockTickerServiceBehavior">  
            <host>  
              <baseAddresses>  
                <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
              </baseAddresses>  
            </host>  
  
            <!-- Define NetMsmqEndpoint -->  
            <endpoint address="net.msmq://localhost/private/ServiceModelSamplesVolatile"  
                      binding="netMsmqBinding"  
                      bindingConfiguration="volatileBinding"   
                      contract="Microsoft.ServiceModel.Samples.IStockTicker" />  
            <!-- the mex endpoint is explosed at http://localhost:8000/ServiceModelSamples/service/mex -->  
            <endpoint address="mex"  
                      binding="mexHttpBinding"  
                      contract="IMetadataExchange" />  
  
          </service>  
        </services>  
  
        <bindings>  
          <netMsmqBinding>  
            <binding name="volatileBinding"   
                  durable="false"  
                  exactlyOnce="false">  
              <security mode="None" />  
            </binding>  
          </netMsmqBinding>  
        </bindings>  
  
        <behaviors>  
          <serviceBehaviors>  
            <behavior name="StockTickerServiceBehavior">  
              <serviceMetadata httpGetEnabled="True"/>  
            </behavior>  
          </serviceBehaviors>  
        </behaviors>  
  
      </system.serviceModel>  
    ```  
  
2.  <span data-ttu-id="07a06-146">サーバーとクライアントの両方の構成を変更したことを確認してから、サンプルを実行します。</span><span class="sxs-lookup"><span data-stu-id="07a06-146">Ensure that you change the configuration on both the server and the client before you run the sample.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="07a06-147">`security mode` を `None` に設定することは、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>、<xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>、および `Message` のセキュリティを `None` に設定することに相当します。</span><span class="sxs-lookup"><span data-stu-id="07a06-147">Setting `security mode` to `None` is equivalent to setting <xref:System.ServiceModel.MsmqTransportSecurity.MsmqAuthenticationMode%2A>, <xref:System.ServiceModel.MsmqTransportSecurity.MsmqProtectionLevel%2A>, and `Message` security to `None`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="07a06-148">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="07a06-148">The samples may already be installed on your computer.</span></span> <span data-ttu-id="07a06-149">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="07a06-149">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="07a06-150">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="07a06-150">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="07a06-151">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="07a06-151">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\Volatile`  
  
## <a name="see-also"></a><span data-ttu-id="07a06-152">関連項目</span><span class="sxs-lookup"><span data-stu-id="07a06-152">See Also</span></span>
