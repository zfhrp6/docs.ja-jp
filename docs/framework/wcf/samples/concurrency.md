---
title: "同時実行"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- service behaviors, concurency sample
- Concurrency Sample [Windows Communication Foundation]
ms.assetid: f8dbdfb3-6858-4f95-abe3-3a1db7878926
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c63882055718bd54d1983ea0aa10d208bd70793f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="concurrency"></a><span data-ttu-id="7e576-102">同時実行</span><span class="sxs-lookup"><span data-stu-id="7e576-102">Concurrency</span></span>
<span data-ttu-id="7e576-103">同時実行のサンプルでは、<xref:System.ServiceModel.ServiceBehaviorAttribute> を <xref:System.ServiceModel.ConcurrencyMode> 列挙体と共に使用する方法を示します。この列挙体は、サービスのインスタンスがメッセージを順番に処理するか、または同時に処理するかを制御します。</span><span class="sxs-lookup"><span data-stu-id="7e576-103">The Concurrency sample demonstrates using the <xref:System.ServiceModel.ServiceBehaviorAttribute> with the <xref:System.ServiceModel.ConcurrencyMode> enumeration, which controls whether an instance of a service processes messages sequentially or concurrently.</span></span> <span data-ttu-id="7e576-104">サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)を実装する、`ICalculator`サービス コントラクト。</span><span class="sxs-lookup"><span data-stu-id="7e576-104">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="7e576-105">このサンプルでは、`ICalculatorConcurrency` から継承される新しいコントラクト `ICalculator` を定義します。これによって、サービスの同時実行の状態を検査するための 2 つの操作が追加されます。</span><span class="sxs-lookup"><span data-stu-id="7e576-105">This sample defines a new contract, `ICalculatorConcurrency`, which inherits from `ICalculator`, providing two additional operations for inspecting the state of the service concurrency.</span></span> <span data-ttu-id="7e576-106">同時実行設定を変更してから、クライアントを実行して動作の変更を確認します。</span><span class="sxs-lookup"><span data-stu-id="7e576-106">By altering the concurrency setting, you can observe the change in behavior by running the client.</span></span>  
  
 <span data-ttu-id="7e576-107">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="7e576-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e576-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e576-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="7e576-109">選択可能な同時実行モードは次の 3 つです。</span><span class="sxs-lookup"><span data-stu-id="7e576-109">There are three concurrency modes available:</span></span>  
  
-   <span data-ttu-id="7e576-110">`Single`: 各サービス インスタンスは、一度に 1 つのメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="7e576-110">`Single`: Each service instance processes one message at a time.</span></span> <span data-ttu-id="7e576-111">これが既定の同時実行モードです。</span><span class="sxs-lookup"><span data-stu-id="7e576-111">This is the default concurrency mode.</span></span>  
  
-   <span data-ttu-id="7e576-112">`Multiple`: 各サービス インスタンスは、同時に複数のメッセージを処理します。</span><span class="sxs-lookup"><span data-stu-id="7e576-112">`Multiple`: Each service instance processes multiple messages concurrently.</span></span> <span data-ttu-id="7e576-113">この同時実行モードを使用するには、サービスの実装がスレッドセーフである必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e576-113">The service implementation must be thread-safe to use this concurrency mode.</span></span>  
  
-   <span data-ttu-id="7e576-114">`Reentrant`: 各サービス インスタンスは、一度に 1 つのメッセージを処理しますが、再入可能呼び出しを受け入れます。</span><span class="sxs-lookup"><span data-stu-id="7e576-114">`Reentrant`: Each service instance processes one message at a time, but accepts reentrant calls.</span></span> <span data-ttu-id="7e576-115">サービスがこの呼び出しを受け入れるのは、コール アウトするときだけです。再入に示されている、 [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="7e576-115">The service only accepts these calls when it is calling out. Reentrant is demonstrated in the [ConcurrencyMode.Reentrant](../../../../docs/framework/wcf/samples/concurrencymode-reentrant.md) sample.</span></span>  
  
 <span data-ttu-id="7e576-116">同時実行の使用は、インスタンス化モードに関連します。</span><span class="sxs-lookup"><span data-stu-id="7e576-116">The use of concurrency is related to the instancing mode.</span></span> <span data-ttu-id="7e576-117"><xref:System.ServiceModel.InstanceContextMode.PerCall> インスタンス化では、各メッセージが新しいサービス インスタンスによって処理されるため、同時実行は関係しません。</span><span class="sxs-lookup"><span data-stu-id="7e576-117">In <xref:System.ServiceModel.InstanceContextMode.PerCall> instancing, concurrency is not relevant, because each message is processed by a new service instance.</span></span> <span data-ttu-id="7e576-118"><xref:System.ServiceModel.InstanceContextMode.Single> インスタンス化では、<xref:System.ServiceModel.ConcurrencyMode.Single> と <xref:System.ServiceModel.ConcurrencyMode.Multiple> のいずれかの同時実行が関係します。これは 1 つのインスタンスがメッセージを順番に処理するか、同時に処理するかによって決まります。</span><span class="sxs-lookup"><span data-stu-id="7e576-118">In <xref:System.ServiceModel.InstanceContextMode.Single> instancing, either <xref:System.ServiceModel.ConcurrencyMode.Single> or <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency is relevant, depending on whether the single instance processes messages sequentially or concurrently.</span></span> <span data-ttu-id="7e576-119"><xref:System.ServiceModel.InstanceContextMode.PerSession> インスタンス化では、どの同時実行モードも関係する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="7e576-119">In <xref:System.ServiceModel.InstanceContextMode.PerSession> instancing, any of the concurrency modes may be relevant.</span></span>  
  
 <span data-ttu-id="7e576-120">サービス クラスは、`[ServiceBehavior(ConcurrencyMode=<setting>)]` 属性を使用して同時実行動作を指定します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="7e576-120">The service class specifies concurrency behavior with the `[ServiceBehavior(ConcurrencyMode=<setting>)]` attribute as shown in the code sample that follows.</span></span> <span data-ttu-id="7e576-121">行のコメント化を変更して、`Single` および `Multiple` の同時実行モードをそれぞれ試してみてください。</span><span class="sxs-lookup"><span data-stu-id="7e576-121">By changing which lines are commented out, you can experiment with the `Single` and `Multiple` concurrency modes.</span></span> <span data-ttu-id="7e576-122">同時実行モードを変更したら、サービスを再ビルドする必要があります。</span><span class="sxs-lookup"><span data-stu-id="7e576-122">Remember to rebuild the service after changing the concurrency mode.</span></span>  
  
```  
// Single allows a single message to be processed sequentially by each service instance.  
//[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, InstanceContextMode = InstanceContextMode.Single)]  
  
// Multiple allows concurrent processing of multiple messages by a service instance.  
// The service implementation should be thread-safe. This can be used to increase throughput.  
[ServiceBehavior(ConcurrencyMode=ConcurrencyMode.Multiple, InstanceContextMode = InstanceContextMode.Single)]  
  
// Uses Thread.Sleep to vary the execution time of each operation.  
public class CalculatorService : ICalculatorConcurrency  
{  
    int operationCount;  
  
    public double Add(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(180);  
        return n1 + n2;  
    }  
  
    public double Subtract(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(100);  
        return n1 - n2;  
    }  
  
    public double Multiply(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(150);  
        return n1 * n2;  
    }  
  
    public double Divide(double n1, double n2)  
    {  
        operationCount++;  
        System.Threading.Thread.Sleep(120);  
        return n1 / n2;  
    }  
  
    public string GetConcurrencyMode()  
    {     
        // Return the ConcurrencyMode of the service.  
        ServiceHost host = (ServiceHost)OperationContext.Current.Host;  
        ServiceBehaviorAttribute behavior = host.Description.Behaviors.Find<ServiceBehaviorAttribute>();  
        return behavior.ConcurrencyMode.ToString();  
    }  
  
    public int GetOperationCount()  
    {     
        // Return the number of operations.  
        return operationCount;  
    }  
}  
```  
  
 <span data-ttu-id="7e576-123">サンプルの既定の設定では、<xref:System.ServiceModel.ConcurrencyMode.Multiple> インスタンス化と <xref:System.ServiceModel.InstanceContextMode.Single> 同時実行が使用されます。</span><span class="sxs-lookup"><span data-stu-id="7e576-123">The sample uses <xref:System.ServiceModel.ConcurrencyMode.Multiple> concurrency with <xref:System.ServiceModel.InstanceContextMode.Single> instancing by default.</span></span> <span data-ttu-id="7e576-124">クライアント コードは、非同期プロキシを使用するように変更されています。</span><span class="sxs-lookup"><span data-stu-id="7e576-124">The client code has been modified to use an asynchronous proxy.</span></span> <span data-ttu-id="7e576-125">これにより、クライアントはサービスを呼び出した後に、応答を待たずに次の呼び出しを行うことができます。</span><span class="sxs-lookup"><span data-stu-id="7e576-125">This allows the client to make multiple calls to the service without waiting for a response between each call.</span></span> <span data-ttu-id="7e576-126">サービスの同時実行モードの動作の違いを観察してください。</span><span class="sxs-lookup"><span data-stu-id="7e576-126">You can observe the difference in behavior of the service concurrency mode.</span></span>  
  
 <span data-ttu-id="7e576-127">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e576-127">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="7e576-128">実行中のサービスの同時実行モードが表示され、各操作が呼び出され、その後で操作数が表示されます。</span><span class="sxs-lookup"><span data-stu-id="7e576-128">The concurrency mode that the service is running under is displayed, each operation is called, and then the operation count is displayed.</span></span> <span data-ttu-id="7e576-129">同時実行モードが `Multiple` の場合、結果が返される順序は呼び出された順序とは異なります。サービスは複数のメッセージを同時に実行するからです。</span><span class="sxs-lookup"><span data-stu-id="7e576-129">Notice that when the concurrency mode is `Multiple`, the results are returned in a different order than how they were called, because the service processes multiple messages concurrently.</span></span> <span data-ttu-id="7e576-130">同時実行モードを `Single` に変更すると、結果は呼び出された順序どおりに返されます。サービスは各メッセージを順次処理するからです。</span><span class="sxs-lookup"><span data-stu-id="7e576-130">By changing the concurrency mode to `Single`, the results are returned in the order they were called, because the service processes each message sequentially.</span></span> <span data-ttu-id="7e576-131">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7e576-131">Press ENTER in the client window to shut down the client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="7e576-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="7e576-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="7e576-133">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e576-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="7e576-134">Svcutil.exe を使用してプロキシ クライアントを生成する場合は、含めることを確認して、`/async`オプション。</span><span class="sxs-lookup"><span data-stu-id="7e576-134">If you use Svcutil.exe to generate the proxy client, ensure that you include the `/async` option.</span></span>  
  
3.  <span data-ttu-id="7e576-135">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="7e576-135">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
4.  <span data-ttu-id="7e576-136">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="7e576-136">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="7e576-137">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="7e576-137">The samples may already be installed on your machine.</span></span> <span data-ttu-id="7e576-138">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="7e576-138">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="7e576-139">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="7e576-139">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="7e576-140">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="7e576-140">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Concurrency`  
  
## <a name="see-also"></a><span data-ttu-id="7e576-141">参照</span><span class="sxs-lookup"><span data-stu-id="7e576-141">See Also</span></span>
