---
title: Net.TCP ポート共有のサンプル
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 03da5959-0574-4e91-8a53-05854b6c55dc
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 0db4148f9be6db97dec2b8b680dad56171106b2c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="nettcp-port-sharing-sample"></a><span data-ttu-id="237d5-102">Net.TCP ポート共有のサンプル</span><span class="sxs-lookup"><span data-stu-id="237d5-102">Net.TCP Port Sharing Sample</span></span>
<span data-ttu-id="237d5-103">TCP/IP プロトコルはポートと呼ばれる 16 ビットの番号を使用して、同じコンピュータ上で実行されている複数のネットワーク アプリケーションへの接続を区別します。</span><span class="sxs-lookup"><span data-stu-id="237d5-103">The TCP/IP protocol uses a 16-bit number, called a port, to differentiate connections to multiple network applications running on the same machine.</span></span> <span data-ttu-id="237d5-104">アプリケーションがポートをリッスンすると、そのポートのすべての TCP トラフィックがそのアプリケーションに送られます。</span><span class="sxs-lookup"><span data-stu-id="237d5-104">If an application is listening on a port, then all TCP traffic for that port goes to that application.</span></span> <span data-ttu-id="237d5-105">他のアプリケーションは、そのポートを同時にリッスンできません。</span><span class="sxs-lookup"><span data-stu-id="237d5-105">Other applications cannot listen on that port at the same time.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="237d5-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="237d5-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="237d5-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="237d5-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="237d5-108">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="237d5-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="237d5-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="237d5-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\TCP\PortSharing`  
  
 <span data-ttu-id="237d5-110">多くのプロトコルは、使用する標準または既定のポート番号を持っています。</span><span class="sxs-lookup"><span data-stu-id="237d5-110">Many protocols have a standard or default port number that they use.</span></span> <span data-ttu-id="237d5-111">たとえば、HTTP プロトコルは一般的に TCP ポート 80 を使用します。</span><span class="sxs-lookup"><span data-stu-id="237d5-111">For example, the HTTP protocol typically uses TCP port 80.</span></span> <span data-ttu-id="237d5-112">インターネット インフォメーション サービス (IIS) には、複数の HTTP アプリケーション間でポートを共有するためのリスナーがあります。</span><span class="sxs-lookup"><span data-stu-id="237d5-112">Internet Information Services (IIS) has a listener to share a port between multiple HTTP applications.</span></span> <span data-ttu-id="237d5-113">IIS はポートを直接リッスンし、メッセージ ストリーム内の情報に基づいて、そのメッセージを適切なアプリケーションに転送します。</span><span class="sxs-lookup"><span data-stu-id="237d5-113">IIS listens on the port directly and forwards messages to the appropriate application based on information inside the message stream.</span></span> <span data-ttu-id="237d5-114">これにより、複数の HTTP アプリケーションで、メッセージ受信用のポートの予約が競合することなく同じポート番号を使用できます。</span><span class="sxs-lookup"><span data-stu-id="237d5-114">This allows multiple HTTP applications to use the same port number without having to compete to reserve the port for receiving messages.</span></span>  
  
 <span data-ttu-id="237d5-115">NetTcp ポート共有は、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]同様に複数のネットワーク アプリケーションを 1 つのポートを共有できるようにする機能。</span><span class="sxs-lookup"><span data-stu-id="237d5-115">NetTcp Port Sharing is a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]feature that similarly allows multiple network applications to share a single port.</span></span> <span data-ttu-id="237d5-116">NetTcp ポート共有サービスは net.tcp プロトコルを使用して接続を受け入れ、メッセージの送信先アドレスに基づいてメッセージを転送します。</span><span class="sxs-lookup"><span data-stu-id="237d5-116">The NetTcp Port Sharing Service accepts connections using the net.tcp protocol and forwards messages based on their destination address.</span></span>  
  
 <span data-ttu-id="237d5-117">既定では、NetTcp ポート共有サービスは有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="237d5-117">The NetTcp Port Sharing Service is not enabled by default.</span></span> <span data-ttu-id="237d5-118">このサンプルを実行する前に、手動でサービスを有効にする必要があります。</span><span class="sxs-lookup"><span data-stu-id="237d5-118">Before running this sample, you must manually enable the service.</span></span> <span data-ttu-id="237d5-119">詳細については、次を参照してください。[する方法: Net.TCP ポート共有サービスを有効にする](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)です。</span><span class="sxs-lookup"><span data-stu-id="237d5-119">For more information, see [How to: Enable the Net.TCP Port Sharing Service](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).</span></span> <span data-ttu-id="237d5-120">サービスが無効な場合は、サーバー アプリケーションの開始時に例外がスローされます。</span><span class="sxs-lookup"><span data-stu-id="237d5-120">If the service is disabled, an exception is thrown when the server application is started.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.CommunicationException: The TransportManager failed to listen on the supplied URI using the NetTcpPortSharing service: failed to start the service because it is disabled. An administrator can enable it by running 'sc.exe config NetTcpPortSharing start= demand'.. ---> System.InvalidOperationException: Cannot start service NetTcpPortSharing on computer '.'. ---> System.ComponentModel.Win32Exception: The service cannot be started, either because it is disabled or because it has no enabled devices associated with it  
```  
  
 <span data-ttu-id="237d5-121">ポート共有をサーバー上で有効にするには、<xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> バインディングまたは <xref:System.ServiceModel.NetTcpBinding> バインディング要素の <xref:System.ServiceModel.Channels.TcpTransportBindingElement> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="237d5-121">Port sharing is enabled on the server by setting the <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> property of the <xref:System.ServiceModel.NetTcpBinding> binding or the <xref:System.ServiceModel.Channels.TcpTransportBindingElement> binding element.</span></span> <span data-ttu-id="237d5-122">クライアントは、サーバー上で使用されるポート共有の構成内容を知る必要はありません。</span><span class="sxs-lookup"><span data-stu-id="237d5-122">The client does not have to know how port sharing has been configured to use it on the server.</span></span>  
  
## <a name="enabling-port-sharing"></a><span data-ttu-id="237d5-123">ポート共有の有効化</span><span class="sxs-lookup"><span data-stu-id="237d5-123">Enabling Port Sharing</span></span>  
 <span data-ttu-id="237d5-124">次のコードでは、サーバー上でのポート共有の有効化を示します。</span><span class="sxs-lookup"><span data-stu-id="237d5-124">The following code demonstrates enabling port sharing on the server.</span></span> <span data-ttu-id="237d5-125">ランダムな URI パスが含まれる固定ポートで、`ICalculator` サービスのインスタンスを開始します。</span><span class="sxs-lookup"><span data-stu-id="237d5-125">It starts an instance of the `ICalculator` service on a fixed port with a random URI path.</span></span> <span data-ttu-id="237d5-126">2 つのサービスは同じポートを共有できますが、NetTcp ポート共有サービスが正しいアプリケーションにメッセージをルーティングできるように、これらのエンドポイント アドレスは全体で一意であることが必要です。</span><span class="sxs-lookup"><span data-stu-id="237d5-126">Even though two services can share the same port, their overall endpoint addresses still must be unique so that the NetTcp Port Sharing Service can route messages to the correct application.</span></span>  

```csharp
// Configure a binding with TCP port sharing enabled  
NetTcpBinding binding = new NetTcpBinding();  
binding.PortSharingEnabled = true;  
  
// Start a service on a fixed TCP port  
ServiceHost host = new ServiceHost(typeof(CalculatorService));  
ushort salt = (ushort)new Random().Next();  
string address =  
   String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
host.AddServiceEndpoint(typeof(ICalculator), binding, address);  
host.Open();  
```

 <span data-ttu-id="237d5-127">ポート共有を有効にすると、ポート番号の競合を起こすことなく、何度もサービスを実行できます。</span><span class="sxs-lookup"><span data-stu-id="237d5-127">With port sharing enabled, you can run the service multiple times without having a conflict over the port number.</span></span> <span data-ttu-id="237d5-128">コードを変更してポート共有を無効にした場合、サービスを 2 つ開始すると 2 つ目のサービスが失敗し、<xref:System.ServiceModel.AddressAlreadyInUseException> が発生します。</span><span class="sxs-lookup"><span data-stu-id="237d5-128">If you change the code to disable port sharing, starting up two copies of the service results in the second failing with an <xref:System.ServiceModel.AddressAlreadyInUseException>.</span></span>  
  
```  
Unhandled Exception: System.ServiceModel.AddressAlreadyInUseException: There is already a listener on IP endpoint 0.0.0.0:9000.  Make sure that you are not trying to use this endpoint multiple times in your application and that there are no other applications listening on this endpoint. ---> System.Net.Sockets.SocketException: Only one usage of each socket address (protocol/network address/port) is normally permitted  
```  
  
## <a name="running-the-sample"></a><span data-ttu-id="237d5-129">サンプルの実行</span><span class="sxs-lookup"><span data-stu-id="237d5-129">Running the Sample</span></span>  
 <span data-ttu-id="237d5-130">テスト クライアントを使用して、ポートを共有しているサービスにメッセージが正しくルーティングされていることを確認できます。</span><span class="sxs-lookup"><span data-stu-id="237d5-130">You can use the test client to check that messages are correctly routed to services sharing the port.</span></span>  

```csharp
class client  
{  
   static void Main(string[] args)  
   {  
      Console.Write("Enter the service number to test: ");  
      ushort salt = ushort.Parse(Console.ReadLine());  
      string address = String.Format("net.tcp://localhost:9000/calculator/{0}", salt);  
      ChannelFactory<ICalculator> factory = new ChannelFactory<ICalculator>(new NetTcpBinding());  
      ICalculator proxy = factory.CreateChannel(new EndpointAddress(address));  
  
      // Call the Add service operation.  
      double value1 = 100.00D;  
      double value2 = 15.99D;  
      double result = proxy.Add(value1, value2);  
      Console.WriteLine("Add({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Subtract service operation.  
      value1 = 145.00D;  
      value2 = 76.54D;  
      result = proxy.Subtract(value1, value2);  
      Console.WriteLine("Subtract({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Multiply service operation.  
      value1 = 9.00D;  
      value2 = 81.25D;  
      result = proxy.Multiply(value1, value2);  
      Console.WriteLine("Multiply({0},{1}) = {2}", value1, value2, result);  
  
      // Call the Divide service operation.  
      value1 = 22.00D;  
      value2 = 7.00D;  
      result = proxy.Divide(value1, value2);  
      Console.WriteLine("Divide({0},{1}) = {2}", value1, value2, result);  
  
      Console.WriteLine();  
      Console.WriteLine("Press <ENTER> to terminate client.");  
      Console.ReadLine();  
  
      factory.Close();  
   }  
}  
```

 <span data-ttu-id="237d5-131">サービスの各インスタンスは、一意の番号とアドレスを出力します。</span><span class="sxs-lookup"><span data-stu-id="237d5-131">Each instance of the service prints out its unique number and address.</span></span> <span data-ttu-id="237d5-132">たとえば、service.exe を実行すると、次のテキストが表示されます。</span><span class="sxs-lookup"><span data-stu-id="237d5-132">For instance, you may see the following text when you run service.exe.</span></span>  
  
```  
Service #4381 listening on net.tcp://localhost:9000/calculator/4381.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="237d5-133">client.exe を実行する際に、ここに表示されるサービス番号を入力します。</span><span class="sxs-lookup"><span data-stu-id="237d5-133">Enter the service number you see here when you run client.exe.</span></span>  
  
```  
Enter the service number to test: 4381  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="237d5-134">このサンプルは、クライアントが使用する生成アドレスを変更することにより、複数コンピュータの構成で実行できます。</span><span class="sxs-lookup"><span data-stu-id="237d5-134">This sample can be run in a cross-machine configuration by changing the generated address that the client uses.</span></span> <span data-ttu-id="237d5-135">Client.cs で、エンドポイント アドレスの書式文字列をサービスの新しいアドレスに合わせます。</span><span class="sxs-lookup"><span data-stu-id="237d5-135">In the Client.cs, change the endpoint address format string to match the new address of your service.</span></span> <span data-ttu-id="237d5-136">"localhost" への参照をすべてサーバー コンピュータの IP アドレスに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="237d5-136">Replace any references to "localhost" with the IP address of the server machine.</span></span> <span data-ttu-id="237d5-137">この変更を行った後に、サンプルを再コンパイルする必要があります。</span><span class="sxs-lookup"><span data-stu-id="237d5-137">You must recompile the sample after making this change.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="237d5-138">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="237d5-138">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="237d5-139">次のコマンドを使用して、[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 をインストールします。</span><span class="sxs-lookup"><span data-stu-id="237d5-139">Install [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0 using the following command.</span></span>  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  <span data-ttu-id="237d5-140">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="237d5-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
3.  <span data-ttu-id="237d5-141">概要セクションに示したように、NetTcp ポート共有サービスを有効にします。</span><span class="sxs-lookup"><span data-stu-id="237d5-141">Enable the NetTcp Port Sharing Service as previously described in the introduction section.</span></span>  
  
4.  <span data-ttu-id="237d5-142">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="237d5-142">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
5.  <span data-ttu-id="237d5-143">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="237d5-143">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="237d5-144">このサンプルを実行するための詳細情報については、前述の「サンプルの実行」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="237d5-144">Specific details for running this sample are included previously in the Running the Sample section.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="237d5-145">関連項目</span><span class="sxs-lookup"><span data-stu-id="237d5-145">See Also</span></span>
