---
title: "アドレス指定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d438e6f2-d0f3-43aa-b259-b51b5bda2e64
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 05fe983832eb3931549bbda5ee7db7c70766cd3c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="addressing"></a><span data-ttu-id="8f14b-102">アドレス指定</span><span class="sxs-lookup"><span data-stu-id="8f14b-102">Addressing</span></span>
<span data-ttu-id="8f14b-103">アドレス指定のサンプルでは、エンドポイント アドレスのさまざまな特性と機能を示します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-103">The Addressing sample demonstrates various aspects and features of endpoint addresses.</span></span> <span data-ttu-id="8f14b-104">サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="8f14b-105">このサンプルでは、サービスは自己ホスト型です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-105">In this sample the service is self-hosted.</span></span> <span data-ttu-id="8f14b-106">サービスとクライアントは両方ともコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="8f14b-106">Both the service and the client are console applications.</span></span> <span data-ttu-id="8f14b-107">サービスでは、エンドポイントの相対アドレスと絶対アドレスを組み合わせて複数のエンドポイントを定義します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-107">The service defines multiple endpoints using a combination of relative and absolute endpoint addresses.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8f14b-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f14b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8f14b-109">サービス構成ファイルでは、1 つのベース アドレスと 4 つのエンドポイントを指定します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-109">The service configuration file specifies a base address and four endpoints.</span></span> <span data-ttu-id="8f14b-110">ベース アドレスは、次のサンプル構成のように add 要素を使用して service/host/baseAddresses の下に指定します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-110">The base address is specified using the add element, under service/host/baseAddresses as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service name="Microsoft.ServiceModel.Samples.CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />  
    </baseAddresses>  
  </host>  
</service>  
```  
  
 <span data-ttu-id="8f14b-111">次のサンプル構成の 1 番目のエンドポイント定義では、相対アドレスを指定します。つまり、エンドポイント アドレスは、ベース アドレスと URI 構造の規則に従った相対アドレスの組み合わせということを意味します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-111">The first endpoint definition shown in the following sample configuration specifies a relative address, which means the endpoint address is a combination of the base address and the relative address following the rules of URI composition.</span></span>  
  
```xml
<!-- Empty relative address specified:   
     use the base address provided by the host. -->  
<!-- The endpoint address is  
     http://localhost:8000/ServiceModelSamples/service. -->  
<endpoint address=""  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="8f14b-112">この場合、相対アドレスが空 ("") のため、エンドポイント アドレスはベース アドレスと同じになります。</span><span class="sxs-lookup"><span data-stu-id="8f14b-112">In this case, the relative address is empty (""), so the endpoint address is the same as the base address.</span></span> <span data-ttu-id="8f14b-113">具体的には http://localhost:8000/servicemodelsamples/service です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-113">The actual endpoint address is http://localhost:8000/servicemodelsamples/service.</span></span>  
  
 <span data-ttu-id="8f14b-114">2 番目のエンドポイント定義でも、相対アドレスを指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f14b-114">The second endpoint definition also specifies a relative address, as shown in the following sample configuration.</span></span>  
  
```xml  
<!-- The relative address specified: use the base address -->  
<!-- provided by the host + path. The endpoint address is -->  
<!-- http://localhost:8000/servicemodelsamples/service/test. -->  
<endpoint address="/test"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="8f14b-115">相対アドレス "test" がベース アドレスの末尾に追加されています。</span><span class="sxs-lookup"><span data-stu-id="8f14b-115">The relative address, "test", is appended to the base address.</span></span> <span data-ttu-id="8f14b-116">具体的には http://localhost:8000/servicemodelsamples/service/test です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-116">The actual endpoint address is http://localhost:8000/servicemodelsamples/service/test.</span></span>  
  
 <span data-ttu-id="8f14b-117">3 番目のエンドポイント定義では、絶対アドレスを指定します。次のサンプル構成を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8f14b-117">The third endpoint definition specifies an absolute address, as shown in the following sample configuration.</span></span>  
  
```xml  
<endpoint address="http://localhost:8001/hello/servicemodelsamples"  
          binding="wsHttpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
```  
  
 <span data-ttu-id="8f14b-118">このアドレスでは、ベース アドレスは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="8f14b-118">The base address plays no role in the address.</span></span> <span data-ttu-id="8f14b-119">具体的には http://localhost:8001/hello/servicemodelsamples です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-119">The actual endpoint address is http://localhost:8001/hello/servicemodelsamples.</span></span>  
  
 <span data-ttu-id="8f14b-120">4 番目のエンドポイント アドレスは、絶対アドレスと別のトランスポート (ここでは TCP) を指定しています。</span><span class="sxs-lookup"><span data-stu-id="8f14b-120">The fourth endpoint address specifies an absolute address and a different transport—TCP.</span></span> <span data-ttu-id="8f14b-121">このアドレスでは、ベース アドレスは使用されていません。</span><span class="sxs-lookup"><span data-stu-id="8f14b-121">The base address plays no role in the address.</span></span> <span data-ttu-id="8f14b-122">具体的には net.tcp://localhost:9000/servicemodelsamples/service です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-122">The actual endpoint address is net.tcp://localhost:9000/servicemodelsamples/service.</span></span>  
  
```xml  
<!-- The absolute address specified, different transport: -->  
<!-- use the specified address, and ignore the base address. -->  
<!-- The endpoint address is -->  
<!-- net.tcp://localhost:9000/servicemodelsamples/service. -->  
<endpoint address=  
          "net.tcp://localhost:9000/servicemodelsamples/service"  
          binding="netTcpBinding"  
          contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</service>  
```  
  
 <span data-ttu-id="8f14b-123">クライアントがアクセスするのは、4 つのサービス エンドポイントのうちの 1 つだけですが、4 つすべてのエンドポイントがこの構成ファイルに定義されています。</span><span class="sxs-lookup"><span data-stu-id="8f14b-123">The client accesses just one of the four service endpoints, but all four are defined in its configuration file.</span></span> <span data-ttu-id="8f14b-124">クライアントは `CalculatorProxy` オブジェクトの作成時にエンドポイントを選択します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-124">The client selects an endpoint when it creates the `CalculatorProxy` object.</span></span> <span data-ttu-id="8f14b-125">`CalculatorEndpoint1` から `CalculatorEndpoint4` までの構成名を変更することにより、それぞれのエンドポイントを実行できます。</span><span class="sxs-lookup"><span data-stu-id="8f14b-125">By changing the configuration name from `CalculatorEndpoint1` through `CalculatorEndpoint4`, you can exercise each of the endpoints.</span></span>  
  
 <span data-ttu-id="8f14b-126">このサンプルを実行する際、サービスはそれぞれのエンドポイントのアドレス、バインディング名、およびコントラクト名を列挙します。</span><span class="sxs-lookup"><span data-stu-id="8f14b-126">When you run the sample, the service enumerates the address, binding name and contract name for each of its endpoints.</span></span> <span data-ttu-id="8f14b-127">ServiceHost から見た場合、メタデータ交換 (MEX) エンドポイントは他と同じエンドポイントにすぎません。したがって、このエンドポイントもこの一覧に表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f14b-127">The metadata exchange (MEX) endpoint is just another endpoint from the ServiceHost's perspective so it shows up in the list.</span></span>  
  
```  
Service endpoints:  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/test  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8001/hello/servicemodelsamples  
           binding:  WSHttpBinding  
           contract: ICalculator  
Endpoint - address:  net.tcp://localhost:9000/servicemodelsamples/service  
           binding:  NetTcpBinding  
           contract: ICalculator  
Endpoint - address:  http://localhost:8000/ServiceModelSamples/service/mex  
           binding:  MetadataExchangeHttpBinding  
           contract: IMetadataExchange  
  
The service is ready.  
Press <ENTER> to terminate service.  
```  
  
 <span data-ttu-id="8f14b-128">このクライアントを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="8f14b-128">When you run the client, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="8f14b-129">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="8f14b-129">Press ENTER in each console window to shut down the service and client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8f14b-130">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="8f14b-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8f14b-131">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8f14b-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8f14b-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8f14b-133">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8f14b-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="8f14b-134">Svcutil.exe を使用してこのサンプルの構成を再生成した場合は、クライアント コードに一致するように、クライアント構成内のエンドポイント名を変更してください。</span><span class="sxs-lookup"><span data-stu-id="8f14b-134">If you use Svcutil.exe to regenerate the configuration for this sample, be sure to modify the endpoint name in the client configuration to match the client code.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8f14b-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8f14b-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8f14b-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8f14b-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8f14b-137">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="8f14b-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8f14b-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8f14b-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Addressing`  
  
## <a name="see-also"></a><span data-ttu-id="8f14b-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="8f14b-139">See Also</span></span>
