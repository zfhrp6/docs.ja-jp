---
title: 単一 ListenUri に対する複数のエンドポイント
ms.date: 03/30/2017
ms.assetid: 911ffad4-4d47-4430-b7c2-79192ce6bcbd
ms.openlocfilehash: f3eb2036ffbb7c5e8cae77ebc1a86e07d31626c9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33506507"
---
# <a name="multiple-endpoints-at-a-single-listenuri"></a><span data-ttu-id="4ec46-102">単一 ListenUri に対する複数のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="4ec46-102">Multiple Endpoints at a Single ListenUri</span></span>
<span data-ttu-id="4ec46-103">このサンプルでは、単一 `ListenUri` で複数のエンドポイントをホストするサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-103">This sample demonstrates a service that hosts multiple endpoints at a single `ListenUri`.</span></span> <span data-ttu-id="4ec46-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4ec46-105">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="4ec46-105">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="4ec46-106">ように、[複数のエンドポイント](../../../../docs/framework/wcf/samples/multiple-endpoints.md)サンプルでは、サービスは、それぞれ異なるアドレス、またはまた各種のバインディングが複数のエンドポイントをホストできます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-106">As demonstrated in the [Multiple Endpoints](../../../../docs/framework/wcf/samples/multiple-endpoints.md) sample, a service can host multiple endpoints, each with different addresses and possibly also different bindings.</span></span> <span data-ttu-id="4ec46-107">このサンプルは、同じアドレスで複数のエンドポイントをホストできることを示しています。</span><span class="sxs-lookup"><span data-stu-id="4ec46-107">This sample shows that it is possible to host multiple endpoints at the same address.</span></span> <span data-ttu-id="4ec46-108">さらに、サービス エンドポイントが持つ、`EndpointAddress` と `ListenUri` の 2 種類のアドレスの違いも示します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-108">This sample also demonstrates the differences between the two kinds of addresses that a service endpoint has: `EndpointAddress` and `ListenUri`.</span></span>  
  
 <span data-ttu-id="4ec46-109">`EndpointAddress` とは、サービスの論理アドレスです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-109">The `EndpointAddress` is the logical address of a service.</span></span> <span data-ttu-id="4ec46-110">これは、SOAP メッセージの宛先となるアドレスです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-110">It is the address that SOAP messages are addressed to.</span></span> <span data-ttu-id="4ec46-111">`ListenUri` とはサービスの物理アドレスです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-111">The `ListenUri` is the physical address of the service.</span></span> <span data-ttu-id="4ec46-112">これには、サービス エンドポイントが現在のコンピュータで実際にメッセージをリッスンする、ポートとアドレスの情報が含まれます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-112">It has the port and address information where the service endpoint actually listens for messages on the current machine.</span></span> <span data-ttu-id="4ec46-113">ほとんどの場合、これらのアドレスが異なっている必要はありません。`ListenUri` が明示的に指定されていない場合は、エンドポイントの `EndpointAddress` の URI が既定値になります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-113">In most cases, there is no need for these addresses to differ; when a `ListenUri` is not explicitly specified, it defaults to the URI of the `EndpointAddress` of the endpoint.</span></span> <span data-ttu-id="4ec46-114">ただし、複数の異なるサービス宛てのメッセージを受け入れることができるルーターを構成する場合など、2 つのアドレスを区別すると便利な場合もあります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-114">In a few cases, it is useful to distinguish them, such as when configuring a router, which might accept messages addressed to a number of different services.</span></span>  
  
## <a name="service"></a><span data-ttu-id="4ec46-115">サービス</span><span class="sxs-lookup"><span data-stu-id="4ec46-115">Service</span></span>  
 <span data-ttu-id="4ec46-116">このサンプルのサービスには、`ICalculator` と `IEcho` という 2 つのコントラクトがあります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-116">The service in this sample has two contracts, `ICalculator` and `IEcho`.</span></span> <span data-ttu-id="4ec46-117">また、一般的な `IMetadataExchange` エンドポイントに加え、次のコードに示すように 3 つのアプリケーション エンドポイントがあります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-117">In addition to the customary `IMetadataExchange` endpoint, there are three application endpoints, as shown in the following code.</span></span>  
  
```xml  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.ICalculator"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:Stuff"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
<endpoint address="urn:OtherEcho"  
        binding="wsHttpBinding"  
        contract="Microsoft.ServiceModel.Samples.IEcho"   
        listenUri="http://localhost/servicemodelsamples/service.svc" />  
```  
  
 <span data-ttu-id="4ec46-118">3 つすべてのエンドポイントは、同じ `ListenUri` でホストされ、同じ `binding` を使用します。`ListenUri` が同じエンドポイントは、コンピュータの物理アドレスでメッセージをリッスンする 1 つのチャネル スタックを共有するので、同じバインディングを使用する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-118">All three endpoints are hosted at the same `ListenUri` and use the same `binding` - endpoints at the same `ListenUri` must have the same binding, because they are sharing a single channel stack that listens for messages at that physical address on the machine.</span></span> <span data-ttu-id="4ec46-119">各エンドポイントの `address` は URN です。通常、アドレスは物理的な場所を表し、実際は任意の種類の URI を設定できますが、サンプルで示すようにこのアドレスは照合とフィルタ処理を行う目的で使用されるので、このように設定されています。</span><span class="sxs-lookup"><span data-stu-id="4ec46-119">The `address` of each endpoint is a URN; though typically addresses represent physical locations, in fact the address can be any kind of URI, because the address is used for matching and filtering purposes as is demonstrated in this sample.</span></span>  
  
 <span data-ttu-id="4ec46-120">次の 3 つのすべてのエンドポイントが同じため`ListenUri`メッセージが到着したときに、Windows Communication Foundation (WCF) がメッセージの送信先のエンドポイントを決定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-120">Because all three endpoints share the same `ListenUri`, when a message arrives there, Windows Communication Foundation (WCF) must decide which endpoint the message is destined for.</span></span> <span data-ttu-id="4ec46-121">各エンドポイントにはメッセージ フィルタがあり、これはアドレス フィルタとコントラクト フィルタの 2 つの部分で構成されます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-121">Each endpoint has a message filter that is comprised of two parts: the address filter and the contract filter.</span></span> <span data-ttu-id="4ec46-122">アドレス フィルタは、SOAP メッセージの `To` とサービス エンドポイントのアドレスを照合します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-122">The address filter matches the `To` of the SOAP message to the address of the service endpoint.</span></span> <span data-ttu-id="4ec46-123">たとえば、`To "Urn:OtherEcho"` 宛てのメッセージだけが、このサービスの 3 つ目のエンドポイントの対象となります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-123">For example, only messages addressed `To "Urn:OtherEcho"` are candidates for the third endpoint of this service.</span></span> <span data-ttu-id="4ec46-124">コントラクト フィルタは、特定のコントラクトの操作に関連付けられたアクションを照合します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-124">The contract filter matches the Actions associated with the operations of a particular contract.</span></span> <span data-ttu-id="4ec46-125">たとえば、`IEcho` のアクションが含まれるメッセージを照合します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-125">For example, messages with the action of `IEcho`.</span></span> <span data-ttu-id="4ec46-126">`Echo` は、このサービスの 2 つ目と 3 つ目の、両方のエンドポイントのコントラクト フィルターと照合します。これらのエンドポイントは、どちらも `IEcho` コントラクトをホストするからです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-126">`Echo` matches the contract filters of both the second and third endpoints of this service, because both of those endpoints host the `IEcho` contract.</span></span>  
  
 <span data-ttu-id="4ec46-127">このように、アドレス フィルタとコントラクト フィルタを組み合わせることによって、このサービスの `ListenUri` に到着する各メッセージを、正しいエンドポイントにルーティングすることができます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-127">Thus the combination of address filter and contract filter makes it possible to route each message that arrives at this service's `ListenUri` to the correct endpoint.</span></span> <span data-ttu-id="4ec46-128">3 つ目のエンドポイントは、他の 2 つのエンドポイントと区別されます。このエンドポイントは、他のエンドポイントとは異なるアドレスに送信されるメッセージを受け入れるからです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-128">The third endpoint is differentiated from the other two because it accepts messages sent to a different address from the other endpoints.</span></span> <span data-ttu-id="4ec46-129">1 つ目のエンドポイントと 2 つ目のエンドポイントは、コントラクト (受信メッセージのアクション) に基づいて相互に区別されます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-129">The first and second endpoints are differentiated from each other based on their contracts (the Action of the incoming message).</span></span>  
  
## <a name="client"></a><span data-ttu-id="4ec46-130">クライアント</span><span class="sxs-lookup"><span data-stu-id="4ec46-130">Client</span></span>  
 <span data-ttu-id="4ec46-131">サーバー上のエンドポイントに 2 つの異なるアドレスがあるのと同様に、クライアント エンドポイントにも 2 つのアドレスがあります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-131">Just as endpoints on the server have two different addresses, client endpoints also have two addresses.</span></span> <span data-ttu-id="4ec46-132">サーバーとクライアントのどちらでも、論理アドレスは `EndpointAddress` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-132">On both server and client, the logical address is called the `EndpointAddress`.</span></span> <span data-ttu-id="4ec46-133">ただし、サーバーの物理アドレスは `ListenUri` と呼ばれるのに対し、クライアントの物理アドレスは `Via` と呼ばれます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-133">But whereas the physical address is called the `ListenUri` on the server, on the client, the physical address is called the `Via`.</span></span>  
  
 <span data-ttu-id="4ec46-134">これら 2 つのアドレスがサーバー上にある場合、既定では同じアドレスを示します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-134">As on the server, by default, these two addresses are the same.</span></span> <span data-ttu-id="4ec46-135">クライアントで、エンドポイントのアドレスとは異なる `Via` を指定するには、次のように `ClientViaBehavior` を使用します。</span><span class="sxs-lookup"><span data-stu-id="4ec46-135">To specify a `Via` on the client that is different from the endpoint's address, `ClientViaBehavior` is used:</span></span>  
  
```  
Uri via = new Uri("http://localhost/ServiceModelSamples/service.svc");  
CalculatorClient calcClient = new CalculatorClient();  
calcClient.ChannelFactory.Endpoint.Behaviors.Add(  
        new ClientViaBehavior(via));  
```  
  
 <span data-ttu-id="4ec46-136">このアドレスは、通常どおりクライアントの構成ファイルで指定します。この構成ファイルは Svcutil.exe によって生成されたものです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-136">As usual, the address comes from the client configuration file, which was generated by Svcutil.exe.</span></span> <span data-ttu-id="4ec46-137">`Via` (サービスの `ListenUri` に相当) は、サービスのメタデータ内では示されません。したがってこの情報は、(サービスのメタデータ アドレスと同様に) クライアントに帯域外で伝達する必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-137">The `Via` (which corresponds to the `ListenUri` of the service) does not appear in the service's metadata and so this information must be communicated to the client out-of-band (just like the service's metadata address).</span></span>  
  
 <span data-ttu-id="4ec46-138">このサンプルでは、クライアントはサーバーの 3 つの各アプリケーション エンドポイントにメッセージを送信し、3 つすべてのエンドポイントと通信できる (さらにそれらのエンドポイントを区別できる) ことを示します。これらすべてのエンドポイントが同じ `Via` を持つ場合でも同様です。</span><span class="sxs-lookup"><span data-stu-id="4ec46-138">The client in this sample sends messages to each of the server's three application endpoints, to demonstrate that it can communicate with (and differentiate) all three endpoints, even though they all have the same `Via`.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="4ec46-139">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="4ec46-139">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="4ec46-140">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ec46-140">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="4ec46-141">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="4ec46-141">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="4ec46-142">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="4ec46-142">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="4ec46-143">複数コンピューターの場合は、Client.cs ファイルで、localhost をサービス コンピューターの名前に置き換える必要があります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-143">For cross-machine, you must replace localhost in the Client.cs file with the name of the service machine.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="4ec46-144">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="4ec46-144">The samples may already be installed on your machine.</span></span> <span data-ttu-id="4ec46-145">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="4ec46-145">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="4ec46-146">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="4ec46-146">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="4ec46-147">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="4ec46-147">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpointsSingleUri`  
  
## <a name="see-also"></a><span data-ttu-id="4ec46-148">関連項目</span><span class="sxs-lookup"><span data-stu-id="4ec46-148">See Also</span></span>
