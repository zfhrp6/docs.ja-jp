---
title: "予期される例外"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 299a6987-ae6b-43c6-987f-12b034b583ae
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 77ddddd51229712f85bc780889169e159c1c83e8
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="expected-exceptions"></a><span data-ttu-id="9c9c0-102">予期される例外</span><span class="sxs-lookup"><span data-stu-id="9c9c0-102">Expected Exceptions</span></span>
<span data-ttu-id="9c9c0-103">このサンプルでは、型指定のあるクライアントを使用する際に、予期される例外をキャッチする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-103">This sample demonstrates how to catch expected exceptions when using a typed client.</span></span> <span data-ttu-id="9c9c0-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="9c9c0-105">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9c9c0-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9c9c0-107">このサンプルでは、正しいプログラムが処理する必要のある `TimeoutException` および `CommunicationException` という 2 種類の予期される例外を、キャッチして処理する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-107">This sample demonstrates catching and handling the two expected exception types that correct programs must handle: `TimeoutException` and `CommunicationException`.</span></span>  
  
 <span data-ttu-id="9c9c0-108">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] クライアントの通信メソッドからスローされる例外には、予期される例外と予期しない例外があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-108">Exceptions that are thrown from communication methods on a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] client are either expected or unexpected.</span></span> <span data-ttu-id="9c9c0-109">予期しない例外には、`OutOfMemoryException` などの致命的なエラーや、`ArgumentNullException` や `InvalidOperationException` などのプログラミング エラーが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-109">Unexpected exceptions include catastrophic failures like `OutOfMemoryException` and programming errors like `ArgumentNullException` or `InvalidOperationException`.</span></span> <span data-ttu-id="9c9c0-110">一般に、予期しないエラーを処理する有効な方法はありません。したがって [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの通信メソッドを呼び出す際、通常は、予期しないエラーをキャッチしないでください。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-110">Typically there is no useful way to handle unexpected errors, so typically you should not catch them when calling a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client communication method.</span></span>  
  
 <span data-ttu-id="9c9c0-111">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントの通信メソッドからの予期される例外には、`TimeoutException`、`CommunicationException`、および `CommunicationException` の任意の派生クラスが含まれます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-111">Expected exceptions from communication methods on a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client include `TimeoutException`, `CommunicationException`, and any derived class of `CommunicationException`.</span></span> <span data-ttu-id="9c9c0-112">これらの例外は通信中の問題を示しますが、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] クライアントを中止して通信エラーを報告することによって安全に処理できます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-112">These indicate a problem during communication that can be safely handled by aborting the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] client and reporting a communication failure.</span></span> <span data-ttu-id="9c9c0-113">どのアプリケーションでも外部要因によってこうしたエラーが発生する可能性があるので、正しいアプリケーションはこのようなエラーをキャッチし、発生した場合には回復させる必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-113">Because external factors can cause these errors in any application, correct applications must catch these exceptions and recover when they occur.</span></span>  
  
 <span data-ttu-id="9c9c0-114">`CommunicationException` の派生クラスには、クライアントがスローできるものがいくつかあります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-114">There are several derived classes of `CommunicationException` that a client can throw.</span></span> <span data-ttu-id="9c9c0-115">状況によっては、アプリケーションでこれらのサブクラスをキャッチして特別な処理を行うこともできます。しかし、それ以外の場合は `CommunicationException` として処理する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-115">In some cases, applications also catch some of these to do special handling, but let the others be handled as a `CommunicationException`.</span></span> <span data-ttu-id="9c9c0-116">この処理は、より具体的な例外の種類を最初にキャッチし、後の catch 句で `CommunicationException` をキャッチすることによって実現できます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-116">This can be accomplished by catching the more specific exception type first and then catching `CommunicationException` in a later catch-clause.</span></span>  
  
 <span data-ttu-id="9c9c0-117">クライアントの通信メソッドを呼び出すコードでは、`TimeoutException` と `CommunicationException` をキャッチする必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-117">Code that calls a client communication method must catch the `TimeoutException` and `CommunicationException`.</span></span> <span data-ttu-id="9c9c0-118">こうしたエラーの処理方法の 1 つに、クライアントを中止して通信エラーを報告するという方法があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-118">One way to handle such errors is to abort the client and report the communication failure.</span></span>  
  
```  
try  
{  
    ...  
    double result = client.Add(value1, value2);  
    ...  
    client.Close();  
}  
catch (TimeoutException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
catch (CommunicationException exception)  
{  
    Console.WriteLine("Got {0}", exception.GetType());  
    client.Abort();  
}  
```  
  
 <span data-ttu-id="9c9c0-119">予期される例外が発生した場合、それ以降、クライアントを使用できる場合もできない場合もあります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-119">If an expected exception occurs, the client may or may not be usable afterwards.</span></span> <span data-ttu-id="9c9c0-120">クライアントがそのまま使用可能かどうかを確認するには、`State` プロパティが `CommunicationState`.Opened であることを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-120">To determine if the client is still usable, check that the `State` property is `CommunicationState`.Opened.</span></span> <span data-ttu-id="9c9c0-121">Opened の場合は、そのまま使用できます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-121">If it is still opened, then it is still usable.</span></span> <span data-ttu-id="9c9c0-122">それ以外の場合は、クライアントを中止してすべての参照を解放する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-122">Otherwise you should abort the client and release all references to it.</span></span>  
  
> [!CAUTION]
>  <span data-ttu-id="9c9c0-123">一般に、セッションを持つクライアントは、例外発生後に使用できなくなり、セッションを持たないクライアントは、例外発生後も使用可能なままです。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-123">You may observe that clients that have a session are often no longer usable after an exception, and clients that do not have a session are often still usable after an exception.</span></span> <span data-ttu-id="9c9c0-124">ただし、どちらも必ずそうなるとは限りません。したがって、例外発生後も引き続きクライアントを使用する場合は、アプリケーションで `State` プロパティをチェックし、クライアントが Opened 状態のままであることを検証する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-124">However, neither of these is guaranteed, so if you want to try to continue using the client after an exception your application should check the `State` property to verify the client is still opened.</span></span>  
  
 <span data-ttu-id="9c9c0-125">このサンプルを実行すると、操作応答と例外がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-125">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="9c9c0-126">クライアント プロセスでは 2 つのシナリオが実行されます。各シナリオでは、`Add`、`Divide` の順に呼び出しが試行されます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-126">The client process runs two scenarios, each of which attempts to call `Add` followed by `Divide`.</span></span> <span data-ttu-id="9c9c0-127">最初のシナリオでは、`Divide` を呼び出す前にクライアントを中止することによってネットワーク問題をシミュレートします。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-127">The first scenario simulates a network issue by aborting the client before making the call to `Divide`.</span></span> <span data-ttu-id="9c9c0-128">2 番目のシナリオでは、メソッドを完了できないようにタイムアウト値をごく短く設定することによって、タイムアウトを発生させます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-128">The second scenario causes a timeout condition by setting the timeout too short for the method to complete.</span></span> <span data-ttu-id="9c9c0-129">クライアント プロセスから予期される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-129">The expected output from the client process is:</span></span>  
  
```  
Add(100,15.99) = 115.99  
Simulated network problem occurs...  
Got System.ServiceModel.CommunicationObjectAbortedException  
Add(100,15.99) = 115.99  
Set timeout too short for method to complete...  
Got System.TimeoutException  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9c9c0-130">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="9c9c0-130">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9c9c0-131">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-131">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9c9c0-132">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-132">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9c9c0-133">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-133">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9c9c0-134">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-134">The samples may already be installed on your machine.</span></span> <span data-ttu-id="9c9c0-135">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-135">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9c9c0-136">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-136">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9c9c0-137">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9c9c0-137">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\ExpectedExceptions`  
  
## <a name="see-also"></a><span data-ttu-id="9c9c0-138">関連項目</span><span class="sxs-lookup"><span data-stu-id="9c9c0-138">See Also</span></span>
