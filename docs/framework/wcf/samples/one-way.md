---
title: "一方向"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 74e3e03d-cd15-4191-a6a5-1efa2dcb9e73
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a781963205f260c82d3db316680c9e8c33045434
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="one-way"></a><span data-ttu-id="207e5-102">一方向</span><span class="sxs-lookup"><span data-stu-id="207e5-102">One-Way</span></span>
<span data-ttu-id="207e5-103">このサンプルでは、一方向サービス操作へのサービスのアクセスを示します。</span><span class="sxs-lookup"><span data-stu-id="207e5-103">This sample demonstrates a service contact with one-way service operations.</span></span> <span data-ttu-id="207e5-104">クライアントは、双方向サービス操作の場合と同様、サービス操作の完了を待機しません。</span><span class="sxs-lookup"><span data-stu-id="207e5-104">The client does not wait for service operations to complete as is the case with two-way service operations.</span></span> <span data-ttu-id="207e5-105">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)を使用して、`wsHttpBinding`バインドします。</span><span class="sxs-lookup"><span data-stu-id="207e5-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and uses the `wsHttpBinding` binding.</span></span> <span data-ttu-id="207e5-106">このサンプルでは、サービスは自己ホスト型コンソール アプリケーションであり、サービスが要求を受信して処理するかどうかを監視できます。</span><span class="sxs-lookup"><span data-stu-id="207e5-106">The service in this sample is a self-hosted console application to enable you to observe the service that receives and processes requests.</span></span> <span data-ttu-id="207e5-107">また、クライアントもコンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="207e5-107">The client is also a console application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="207e5-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="207e5-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="207e5-109">一方向サービス コントラクトを作成するには、サービス コントラクトを定義し、<xref:System.ServiceModel.OperationContractAttribute> クラスを各操作に適用し、<xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> を `true` に設定します。次のコードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="207e5-109">To create a one-way service contract, define your service contract, apply the <xref:System.ServiceModel.OperationContractAttribute> class to each operation, and set <xref:System.ServiceModel.OperationContractAttribute.IsOneWay%2A> to `true` as shown in the following sample code:</span></span>  
  
```  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
public interface IOneWayCalculator  
{  
    [OperationContract(IsOneWay=true)]  
    void Add(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Subtract(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Multiply(double n1, double n2);  
    [OperationContract(IsOneWay = true)]  
    void Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="207e5-110">クライアントがサービス操作の完了を待機しないことを示すため、このサンプルではサービス コードに 5 秒の遅延を実装します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="207e5-110">To demonstrate that the client does not wait for the service operations to complete, the service code in this sample implements a five-second delay, as shown in the following sample code:</span></span>  
  
```  
/ This service class implements the service contract.  
// This code writes output to the console window.  
 [ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Multiple,  
    InstanceContextMode = InstanceContextMode.PerCall)]  
public class CalculatorService : IOneWayCalculator  
{  
    public void Add(double n1, double n2)  
    {  
        Console.WriteLine("Received Add({0},{1}) - sleeping", n1, n2);  
        System.Threading.Thread.Sleep(1000 * 5);  
        double result = n1 + n2;  
        Console.WriteLine("Processing Add({0},{1}) - result: {2}", n1, n2, result);  
    }  
    ...  
}  
```  
  
 <span data-ttu-id="207e5-111">クライアントがサービスを呼び出すと、サービス操作の完了を待たずに呼び出しが返されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-111">When the client calls the service, the call returns without waiting for the service operation to complete.</span></span>  
  
 <span data-ttu-id="207e5-112">サンプルを実行すると、クライアントとサービスのアクティビティがサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-112">When you run the sample, the client and service activities are displayed in both the service and client console windows.</span></span> <span data-ttu-id="207e5-113">サービスがクライアントから受信したメッセージを表示できます。</span><span class="sxs-lookup"><span data-stu-id="207e5-113">You can see the service receive messages from the client.</span></span> <span data-ttu-id="207e5-114">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="207e5-114">Press ENTER in each console window to shut down both the service and the client.</span></span>  
  
 <span data-ttu-id="207e5-115">先にクライアントが完了してその次にサービスが完了し、クライアントが一方向サービス操作の完了を待たないことが示されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-115">The client finishes ahead of the service, demonstrating that a client does not wait for one-way service operations to complete.</span></span> <span data-ttu-id="207e5-116">クライアントからの出力を次に示します。</span><span class="sxs-lookup"><span data-stu-id="207e5-116">The client output is as follows:</span></span>  
  
```  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Press <ENTER> to terminate client.  
```  
  
 <span data-ttu-id="207e5-117">サービスからの出力が次のように表示されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-117">The following service output is shown:</span></span>  
  
```  
The service is ready.  
Press <ENTER> to terminate service.  
  
Received Add(100,15.99) - sleeping  
Received Subtract(145,76.54) - sleeping  
Received Multiply(9,81.25) - sleeping  
Received Divide(22,7) - sleeping  
Processing Add(100,15.99) - result: 115.99  
Processing Subtract(145,76.54) - result: 68.46  
Processing Multiply(9,81.25) - result: 731.25  
Processing Divide(22,7) - result: 3.14285714285714  
```  
  
> [!NOTE]
>  <span data-ttu-id="207e5-118">HTTP は本来、要求/応答プロトコルです。つまり、要求が行われると応答が返されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-118">HTTP is, by definition, a request/response protocol; when a request is made, a response is returned.</span></span> <span data-ttu-id="207e5-119">これは、HTTP を介して公開される一方向サービス操作にも当てはまります。</span><span class="sxs-lookup"><span data-stu-id="207e5-119">This is true even for a one-way service operation that is exposed over HTTP.</span></span> <span data-ttu-id="207e5-120">この操作が呼び出されると、サービスは HTTP ステータス コード 202 を返し、その後サービス操作が実行されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-120">When the operation is called, the service returns an HTTP status code of 202 before the service operation has executed.</span></span> <span data-ttu-id="207e5-121">このステータス コードは、要求は処理用に受け入れられたが、処理はまだ完了していないことを示します。</span><span class="sxs-lookup"><span data-stu-id="207e5-121">This status code means that the request has been accepted for processing, but the processing has not yet been completed.</span></span> <span data-ttu-id="207e5-122">操作を呼び出したクライアントは、サービスから 202 応答を受信するまでブロックします。</span><span class="sxs-lookup"><span data-stu-id="207e5-122">The client that called the operation blocks until it receives the 202 response from the service.</span></span> <span data-ttu-id="207e5-123">これにより、セッションを使用するように構成されているバインディングを使用して複数の一方向メッセージが送信されたときに、いくつかの予期しない動作が発生する場合があります。</span><span class="sxs-lookup"><span data-stu-id="207e5-123">This can cause some unexpected behavior when multiple one-way messages are sent using a binding that is configured to use sessions.</span></span> <span data-ttu-id="207e5-124">このサンプルで使用されている `wsHttpBinding` バインディングは、既定ではセッションを使用してセキュリティ コンテキストを確立するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="207e5-124">The `wsHttpBinding` binding used in this sample is configured to use sessions by default to establish a security context.</span></span> <span data-ttu-id="207e5-125">既定では、セッション内のメッセージは、送信される順序で到着することが保証されています。</span><span class="sxs-lookup"><span data-stu-id="207e5-125">By default, messages in a session are guaranteed to arrive in the order in which they are sent.</span></span> <span data-ttu-id="207e5-126">このため、セッション内の 2 番目のメッセージが送信されても、最初のメッセージが処理されるまでは処理されません。</span><span class="sxs-lookup"><span data-stu-id="207e5-126">Because of this, when the second message in a session is sent, it is not processed until the first message has been processed.</span></span> <span data-ttu-id="207e5-127">この結果、クライアントは、前のメッセージの処理が完了するまではメッセージの 202 応答を受信しません。</span><span class="sxs-lookup"><span data-stu-id="207e5-127">The result of this is that the client does not receive the 202 response for a message until the processing of the previous message has been completed.</span></span> <span data-ttu-id="207e5-128">このため、クライアントは以降のそれぞれの操作呼び出しでブロックしているように見えます。</span><span class="sxs-lookup"><span data-stu-id="207e5-128">The client therefore appears to block on each subsequent operation call.</span></span> <span data-ttu-id="207e5-129">この動作を回避するため、サンプルでは、メッセージを処理用の各インスタンスに同時にディスパッチするようにランタイムを構成します。</span><span class="sxs-lookup"><span data-stu-id="207e5-129">To avoid this behavior, this sample configures the runtime to dispatch messages concurrently to distinct instances for processing.</span></span> <span data-ttu-id="207e5-130">サンプルでは、各メッセージが異なるインスタンスによって処理できるように <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> を `PerCall` に設定します。</span><span class="sxs-lookup"><span data-stu-id="207e5-130">The sample sets <xref:System.ServiceModel.ServiceBehaviorAttribute.InstanceContextMode%2A> to `PerCall` so that each message can be processed by a different instance.</span></span> <span data-ttu-id="207e5-131">複数のスレッドがメッセージを同時にディスパッチするように、<xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> が `Multiple` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="207e5-131"><xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to `Multiple` to allow more than one thread to dispatch messages at a time.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="207e5-132">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="207e5-132">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="207e5-133">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="207e5-133">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="207e5-134">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="207e5-134">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="207e5-135">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="207e5-135">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="207e5-136">サービスを先に実行してからクライアントを実行してください。また、クライアントをシャットダウンした後でサービスをシャットダウンしてください。</span><span class="sxs-lookup"><span data-stu-id="207e5-136">Run the service before you run the client and shut down the client before shutting down the service.</span></span> <span data-ttu-id="207e5-137">これにより、サービスが終了したことによりクライアントでセキュリティ セッションが正常に終了できない場合に発生する、クライアント側の例外が回避できます。</span><span class="sxs-lookup"><span data-stu-id="207e5-137">This avoids a client exception when the client cannot close the security session cleanly because the service is gone.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="207e5-138">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="207e5-138">The samples may already be installed on your machine.</span></span> <span data-ttu-id="207e5-139">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="207e5-139">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="207e5-140">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="207e5-140">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="207e5-141">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="207e5-141">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Contract\Service\Oneway`  
  
## <a name="see-also"></a><span data-ttu-id="207e5-142">参照</span><span class="sxs-lookup"><span data-stu-id="207e5-142">See Also</span></span>
