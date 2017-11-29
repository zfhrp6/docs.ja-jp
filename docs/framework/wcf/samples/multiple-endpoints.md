---
title: "複数のエンドポイント"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Multiple EndPoints
ms.assetid: 8f0c2e1f-9aee-41c2-8301-c72b7f664412
caps.latest.revision: "31"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 3b7e3a6da177c381bafe3adee16be36ceba50616
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="multiple-endpoints"></a><span data-ttu-id="83cf0-102">複数のエンドポイント</span><span class="sxs-lookup"><span data-stu-id="83cf0-102">Multiple Endpoints</span></span>
<span data-ttu-id="83cf0-103">この複数のエンドポイントのサンプルでは、複数のエンドポイントを 1 つのサービスに構成する方法と、クライアントから各エンドポイントと通信を行う方法を示します。</span><span class="sxs-lookup"><span data-stu-id="83cf0-103">The Multiple Endpoints sample demonstrates how to configure multiple endpoints on a service and how to communicate with each endpoint from a client.</span></span> <span data-ttu-id="83cf0-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="83cf0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="83cf0-105">サービス構成は、`ICalculator` コントラクトをサポートする 2 つのエンドポイントを定義するように変更されていますが、各エンドポイントは異なるアドレスで異なるバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="83cf0-105">The service configuration has been modified to define two endpoints that support the `ICalculator` contract, but each at a different address using a different binding.</span></span> <span data-ttu-id="83cf0-106">クライアント構成とコードは、両方のサービス エンドポイントと通信するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="83cf0-106">The client configuration and code have been modified to communicate with both of the service endpoints.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="83cf0-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="83cf0-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="83cf0-108">サービスの Web.config ファイルは、2 つのエンドポイントを定義するように変更されています。各エンドポイントは同じ `ICalculator` コントラクトをサポートしますが、異なるアドレスで異なるバインディングを使用します。</span><span class="sxs-lookup"><span data-stu-id="83cf0-108">The service Web.config file has been modified to define two endpoints, each supporting the same `ICalculator` contract, but at different addresses using different bindings.</span></span> <span data-ttu-id="83cf0-109">1 つ目のエンドポイントは、`basicHttpBinding` バインディングを使用して基本アドレスで定義されます。このエンドポイントではセキュリティは有効ではありません。</span><span class="sxs-lookup"><span data-stu-id="83cf0-109">The first endpoint is defined at the base address using a `basicHttpBinding` binding, which does not have security enabled.</span></span> <span data-ttu-id="83cf0-110">2 つ目のエンドポイントは、`wsHttpBinding` バインディングを使用して {baseaddress}/secure で定義されます。このエンドポイントは既定で、Windows 認証による WS-Security を使用してセキュリティ保護されています。</span><span class="sxs-lookup"><span data-stu-id="83cf0-110">The second endpoint is defined at {baseaddress}/secure using a `wsHttpBinding` binding, which is secure by default, using WS-Security with Windows authentication.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <!-- This endpoint is exposed at the base address provided by host:  
       http://localhost/servicemodelsamples/service.svc  -->  
  <endpoint address=""  
            binding="basicHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- secure endpoint exposed at {base address}/secure:  
       http://localhost/servicemodelsamples/service.svc/secure -->  
  <endpoint address="secure"  
            binding="wsHttpBinding"  
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  ...  
</service>  
```  
  
 <span data-ttu-id="83cf0-111">両方のエンドポイントは、さらにクライアントでも構成されます。</span><span class="sxs-lookup"><span data-stu-id="83cf0-111">Both endpoints are also configured on the client.</span></span> <span data-ttu-id="83cf0-112">呼び出し元が必要なエンドポイント名をクライアントのコンストラクタに渡せるように、これらのエンドポイントには名前が付けられます。</span><span class="sxs-lookup"><span data-stu-id="83cf0-112">These endpoints are given names so that the caller can pass the desired endpoint name into the constructor of the client.</span></span>  
  
```xml  
<client>  
  <!-- Passing "basic" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="basic"  
            address="http://localhost/servicemodelsamples/service.svc"   
            binding="basicHttpBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
  <!-- Passing "secure" into the constructor of the CalculatorClient  
       class selects this endpoint.-->  
  <endpoint name="secure"  
address="http://localhost/servicemodelsamples/service.svc/secure"   
            binding="wsHttpBinding"   
            contract="Microsoft.ServiceModel.Samples.ICalculator" />  
</client>  
```  
  
 <span data-ttu-id="83cf0-113">次のコードに示すように、クライアントは両方のエンドポイントを使用します。</span><span class="sxs-lookup"><span data-stu-id="83cf0-113">The client uses both endpoints as shown in the following code.</span></span>  
  
```  
static void Main()  
{  
    // Create a client to the basic endpoint configuration.  
    CalculatorClient client = new CalculatorClient("basic");  
    Console.WriteLine("Communicate with basic endpoint.");  
    // call operations  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    // Create a client to the secure endpoint configuration.  
    client = new CalculatorClient("secure");  
    Console.WriteLine("Communicate with secure endpoint.");  
    // Call operations.  
    DoCalculations(client);  
  
    // Close the client and release resources.  
    client.Close();  
  
    Console.WriteLine();  
    Console.WriteLine("Press <ENTER> to terminate client.");  
    Console.ReadLine();  
}  
```  
  
 <span data-ttu-id="83cf0-114">クライアントを実行すると、両方のエンドポイントとのやり取りが表示されます。</span><span class="sxs-lookup"><span data-stu-id="83cf0-114">When you run the client, interactions with both endpoints are displayed.</span></span>  
  
```  
Communicate with basic endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
Communicate with secure endpoint.  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="83cf0-115">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="83cf0-115">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="83cf0-116">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="83cf0-116">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="83cf0-117">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="83cf0-117">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="83cf0-118">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="83cf0-118">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="83cf0-119">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="83cf0-119">The samples may already be installed on your machine.</span></span> <span data-ttu-id="83cf0-120">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="83cf0-120">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="83cf0-121">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="83cf0-121">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="83cf0-122">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="83cf0-122">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\MultipleEndpoints`  
  
## <a name="see-also"></a><span data-ttu-id="83cf0-123">関連項目</span><span class="sxs-lookup"><span data-stu-id="83cf0-123">See Also</span></span>
