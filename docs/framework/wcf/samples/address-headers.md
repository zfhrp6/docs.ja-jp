---
title: "アドレス ヘッダー"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0c94d4a-3bde-4b4d-bb6d-9f12bc3a6940
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: aafd6ec911464dcc2b936b9f9fc74b9bc39808bf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="address-headers"></a><span data-ttu-id="ca603-102">アドレス ヘッダー</span><span class="sxs-lookup"><span data-stu-id="ca603-102">Address Headers</span></span>
<span data-ttu-id="ca603-103">アドレス ヘッダーのサンプルでは、クライアントが [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、サービスに参照パラメータを渡す方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ca603-103">The Address Headers sample demonstrates how clients can pass reference parameters to a service using [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ca603-104">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ca603-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="ca603-105">WS-Addressing 仕様では、特定の Web サービスのエンドポイントのアドレスを指定するための方法として、エンドポイント参照の概念が定義されています。</span><span class="sxs-lookup"><span data-stu-id="ca603-105">The WS-Addressing specification defines the notion of an endpoint reference as a way to address a particular Web service endpoint.</span></span> <span data-ttu-id="ca603-106">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、エンドポイント参照は `EndpointAddress` クラスを通じてモデル化されます。`EndpointAddress` は、`ServiceEndpoint` クラスの Address フィールドの型です。</span><span class="sxs-lookup"><span data-stu-id="ca603-106">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], endpoint references are modeled using the `EndpointAddress` class - `EndpointAddress` is the type of the Address field of the `ServiceEndpoint` class.</span></span>  
  
 <span data-ttu-id="ca603-107">エンドポイント参照モデルの一部では、各参照は、追加の識別情報を追加する複数の参照パラメータを伝達できます。</span><span class="sxs-lookup"><span data-stu-id="ca603-107">Part of the endpoint reference model is that each reference can carry some reference parameters that add extra identifying information.</span></span> <span data-ttu-id="ca603-108">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] では、これらの参照パラメータは `AddressHeader` クラスのインスタンスとしてモデル化されます。</span><span class="sxs-lookup"><span data-stu-id="ca603-108">In [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], these reference parameters are modeled as instances of `AddressHeader` class.</span></span>  
  
 <span data-ttu-id="ca603-109">このサンプルでは、クライアントはクライアント エンドポイントの `EndpointAddress` に参照パラメータを追加します。</span><span class="sxs-lookup"><span data-stu-id="ca603-109">In this sample, the client adds a reference parameter to the `EndpointAddress` of the client endpoint.</span></span> <span data-ttu-id="ca603-110">サービスはこの参照パラメータを検索し、その値を "Hello" サービス操作のロジックに使用します。</span><span class="sxs-lookup"><span data-stu-id="ca603-110">The service looks for this reference parameter and uses its value in the logic of its "Hello" service operation.</span></span>  
  
## <a name="client"></a><span data-ttu-id="ca603-111">クライアント</span><span class="sxs-lookup"><span data-stu-id="ca603-111">Client</span></span>  
 <span data-ttu-id="ca603-112">クライアントから参照パラメータを送信するには、`AddressHeader` の `EndpointAddress` に `ServiceEndpoint` を追加する必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca603-112">For the client to send a reference parameter, it must add an `AddressHeader` to the `EndpointAddress` of the `ServiceEndpoint`.</span></span> <span data-ttu-id="ca603-113">`EndpointAddress` クラスは不変なので、EndpointAddress の変更は `EndpointAddressBuilder` クラスを通じて行う必要があります。</span><span class="sxs-lookup"><span data-stu-id="ca603-113">Because the `EndpointAddress` class is immutable, modification of an endpoint address must be done using the `EndpointAddressBuilder` class.</span></span> <span data-ttu-id="ca603-114">参照パラメータをメッセージの一部として送信するためにクライアントを初期化するコードを、次に示します。</span><span class="sxs-lookup"><span data-stu-id="ca603-114">The following code initializes the client to send a reference parameter as part of its message.</span></span>  
  
```  
HelloClient client = new HelloClient();  
EndpointAddressBuilder builder =   
    new EndpointAddressBuilder(client.Endpoint.Address);  
AddressHeader header =   
    AddressHeader.CreateAddressHeader(IDName, IDNamespace, "John");  
builder.Headers.Add(header);  
client.Endpoint.Address = builder.ToEndpointAddress();  
```  
  
 <span data-ttu-id="ca603-115">このコードは、元の `EndpointAddressBuilder` を初期値として使用して `EndpointAddress` を作成します。</span><span class="sxs-lookup"><span data-stu-id="ca603-115">The code creates an `EndpointAddressBuilder` using the original `EndpointAddress` as an initial value.</span></span> <span data-ttu-id="ca603-116">次に、新しく作成されたアドレス ヘッダーを追加します。つまり `CreateAddressHeadercreates` を呼び出して、特定の名前、名前空間、および値を持つヘッダーを作成します。</span><span class="sxs-lookup"><span data-stu-id="ca603-116">It then adds a newly created address header; the call to `CreateAddressHeadercreates` a header with a particular name, namespace, and value.</span></span> <span data-ttu-id="ca603-117">ここでの値は "John" です。</span><span class="sxs-lookup"><span data-stu-id="ca603-117">Here the value is "John".</span></span> <span data-ttu-id="ca603-118">ヘッダーがビルダに追加されると、`ToEndpointAddress()` メソッドが (不変の) ビルダを (不変の) エンドポイント アドレスに変換し直し、これをクライアント エンドポイントの Address フィールドに再度割り当てます。</span><span class="sxs-lookup"><span data-stu-id="ca603-118">Once the header is added to the builder, the `ToEndpointAddress()` method converts the (mutable) builder back into an (immutable) endpoint address, which is assigned back to the client endpoint's Address field.</span></span>  
  
 <span data-ttu-id="ca603-119">ここで、クライアントは `Console.WriteLine(client.Hello());` サービスを呼び出します。このサービスは、このアドレス パラメータの値を取得できます。結果として得られるクライアントの出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="ca603-119">Now when the client calls `Console.WriteLine(client.Hello());`, the service is able to get the value of this address parameter, as seen in the resulting output of the client.</span></span>  
  
 `Hello, John`  
  
## <a name="server"></a><span data-ttu-id="ca603-120">サーバー</span><span class="sxs-lookup"><span data-stu-id="ca603-120">Server</span></span>  
 <span data-ttu-id="ca603-121">サービス操作 `Hello()` の実装では、現在の `OperationContext` を使用して、入力メッセージのヘッダーの値を検査します。</span><span class="sxs-lookup"><span data-stu-id="ca603-121">The implementation of the service operation `Hello()` uses the current `OperationContext` to inspect the values of the headers on the incoming message.</span></span>  
  
```  
string id = null;  
// look at headers on incoming message  
for (int i = 0;   
     i < OperationContext.Current.IncomingMessageHeaders.Count;   
     ++i)  
{  
    MessageHeaderInfo h =   
        OperationContext.Current.IncomingMessageHeaders[i];  
    // for any reference parameters with the correct name & namespace  
    if (h.IsReferenceParameter &&   
        h.Name == IDName &&   
        h.Namespace == IDNamespace)  
    {  
        // read the value of that header  
        XmlReader xr =   
OperationContext.Current.IncomingMessageHeaders.GetReaderAtHeader(i);  
        id = xr.ReadElementContentAsString();  
    }  
}  
return "Hello, " + id;  
```  
  
 <span data-ttu-id="ca603-122">このコードでは、入力メッセージのすべてのヘッダーを反復処理して、特定の名前を持つ参照パラメーターを検索します。</span><span class="sxs-lookup"><span data-stu-id="ca603-122">The code iterates over all the headers on the incoming message, looking for headers that are reference parameters with the particular name and.</span></span> <span data-ttu-id="ca603-123">パラメーターが見つかると、そのパラメーター値を読み取って "id" 変数に格納します。</span><span class="sxs-lookup"><span data-stu-id="ca603-123">When the parameter is found, it reads the value of the parameter and stores it in the "id" variable.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ca603-124">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ca603-124">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ca603-125">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca603-125">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ca603-126">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ca603-126">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ca603-127">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="ca603-127">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ca603-128">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ca603-128">The samples may already be installed on your machine.</span></span> <span data-ttu-id="ca603-129">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ca603-129">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ca603-130">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="ca603-130">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ca603-131">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ca603-131">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\AddressHeaders`  
  
## <a name="see-also"></a><span data-ttu-id="ca603-132">参照</span><span class="sxs-lookup"><span data-stu-id="ca603-132">See Also</span></span>
