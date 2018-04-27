---
title: Using ステートメントに関する問題の回避
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: aff82a8d-933d-4bdc-b0c2-c2f7527204fb
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd3065a21c1714b0643bfb87b731193d3367352f
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/27/2018
---
# <a name="avoiding-problems-with-the-using-statement"></a><span data-ttu-id="0f2e2-102">Using ステートメントに関する問題の回避</span><span class="sxs-lookup"><span data-stu-id="0f2e2-102">Avoiding Problems with the Using Statement</span></span>
<span data-ttu-id="0f2e2-103">このサンプルでは、型指定のあるクライアントを使用する際に C# の "using" ステートメントを使用せずに、リソースを自動的にクリーンアップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-103">This sample demonstrates how you should not use the C# "using" statement to automatically clean up resources when using a typed client.</span></span> <span data-ttu-id="0f2e2-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span> <span data-ttu-id="0f2e2-105">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-105">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="0f2e2-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="0f2e2-107">このサンプルでは、C# の "using" ステートメントを型指定のあるクライアントと共に使用する際に発生する 2 つの一般的な問題と、例外が発生した後に正しくクリーンアップするコードを示します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-107">This sample shows two of the common problems that occur when using the C# "using" statement with typed clients, as well as code that correctly cleans up after exceptions.</span></span>  
  
 <span data-ttu-id="0f2e2-108">C# の "using" ステートメントにより `Dispose`() が呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-108">The C# "using" statement results in a call to `Dispose`().</span></span> <span data-ttu-id="0f2e2-109">これは `Close`() と同じで、ネットワーク エラーが発生したときに例外をスローする場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-109">This is the same as `Close`(), which may throw exceptions when a network error occurs.</span></span> <span data-ttu-id="0f2e2-110">`Dispose`() への呼び出しは、"using" ブロックの閉じかっこで暗黙的に発生するので、コードを記述するユーザーとコードを読み取るユーザーの両者が、これを例外の発生元と気付かない可能性があります。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-110">Because the call to `Dispose`() happens implicitly at the closing brace of the "using" block, this source of exceptions is likely to go unnoticed both by people writing the code and reading the code.</span></span> <span data-ttu-id="0f2e2-111">これは、アプリケーション エラーの潜在的な原因となります。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-111">This represents a potential source of application errors.</span></span>  
  
 <span data-ttu-id="0f2e2-112">最初の問題は、次の `DemonstrateProblemUsingCanThrow` メソッドに示すように、閉じかっこで例外がスローされるとその後のコードが実行されないことです。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-112">The first problem, illustrated in the `DemonstrateProblemUsingCanThrow` method, is that the closing brace throws an exception and the code after the closing brace does not execute:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
} // <-- this line might throw  
Console.WriteLine("Hope this code wasn't important, because it might not happen.");  
```  
  
 <span data-ttu-id="0f2e2-113">using ブロック内部からスローされる例外がない場合、または using ブロック内のすべての例外がキャッチされた場合でも、`Console.Writeline` は発生しません。閉じかっこでの `Dispose`() の暗黙の呼び出しによって例外がスローされるためです。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-113">Even if nothing inside the using block throws an exception or all exceptions inside the using block are caught, the `Console.Writeline` might not happen because the implicit `Dispose`() call at the closing brace might throw an exception.</span></span>  
  
 <span data-ttu-id="0f2e2-114">2 番目の問題は、次の `DemonstrateProblemUsingCanThrowAndMask` メソッドで示すように、閉じかっこで別の例外が暗黙的にスローされる点です。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-114">The second problem, illustrated in the `DemonstrateProblemUsingCanThrowAndMask` method, is another implication of the closing brace throwing an exception:</span></span>  
  
```csharp   
using (CalculatorClient client = new CalculatorClient())  
{  
    ...  
    throw new ApplicationException("Hope this exception was not important, because "+  
                                   "it might be masked by the Close exception.");  
} // <-- this line might throw an exception.  
```  
  
 <span data-ttu-id="0f2e2-115">`Dispose`() は "最後の" ブロック内で発生するので、`ApplicationException`() が失敗した場合、`Dispose` は using ブロックの外側には表示されません。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-115">Because the `Dispose`() occurs inside a "finally" block, the `ApplicationException` is never seen outside the using block if the `Dispose`() fails.</span></span> <span data-ttu-id="0f2e2-116">外側のコードで、`ApplicationException` の発生時期を認識できるよう考慮されている場合は、この例外をマスクすると、"using" コンストラクトが問題の原因となる場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-116">If the code outside must know about when the `ApplicationException` occurs, the "using" construct may cause problems by masking this exception.</span></span>  
  
 <span data-ttu-id="0f2e2-117">最後に、このサンプルでは、`DemonstrateCleanupWithExceptions` で例外が発生した場合に正しくクリーンアップする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-117">Finally, the sample demonstrates how to clean up correctly when exceptions occur in `DemonstrateCleanupWithExceptions`.</span></span> <span data-ttu-id="0f2e2-118">ここでは、try/catch ブロックを使用してエラーを報告し、`Abort` を呼び出します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-118">This uses a try/catch block to report errors and call `Abort`.</span></span> <span data-ttu-id="0f2e2-119">参照してください、[予想例外](../../../../docs/framework/wcf/samples/expected-exceptions.md)サンプルの詳細については、クライアントの呼び出しから例外をキャッチします。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-119">See the [Expected Exceptions](../../../../docs/framework/wcf/samples/expected-exceptions.md) sample for more details about catching exceptions from client calls.</span></span>  
  
```csharp   
try  
{  
    ...  
    client.Close();  
}  
catch (CommunicationException e)  
{  
    ...  
    client.Abort();  
}  
catch (TimeoutException e)  
{  
    ...  
    client.Abort();  
}  
catch (Exception e)  
{  
    ...  
    client.Abort();  
    throw;  
}  
```  
  
> [!NOTE]
>  <span data-ttu-id="0f2e2-120">using ステートメントと ServiceHost: 多くの自己ホスト アプリケーションでは、サービスをホストする以外の処理はほとんど行われず、ServiceHost.Close から例外がスローされることはほとんどありません。したがって、このようなアプリケーションでは、using ステートメントを ServiceHost と共に使用しても安全です。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-120">The using statement and ServiceHost: Many self-hosting applications do little more than host a service, and ServiceHost.Close rarely throws an exception, so such applications can safely use the using statement with ServiceHost.</span></span> <span data-ttu-id="0f2e2-121">ただし、ServiceHost.Close では `CommunicationException` がスローされる場合があることに注意してください。したがって、ServiceHost を閉じた後でアプリケーションを続行する場合は、using ステートメントを使用せずに前のパターンに従う必要があります。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-121">However, be aware that ServiceHost.Close can throw a `CommunicationException`, so if your application continues after closing the ServiceHost, you should avoid the using statement and follow the pattern previously given.</span></span>  
  
 <span data-ttu-id="0f2e2-122">このサンプルを実行すると、操作応答と例外がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-122">When you run the sample, the operation responses and exceptions are displayed in the client console window.</span></span>  
  
 <span data-ttu-id="0f2e2-123">クライアント プロセスでは 3 つのシナリオが実行されます。各シナリオでは `Divide` の呼び出しが試行されます。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-123">The client process runs three scenarios, each of which attempts to call `Divide`.</span></span> <span data-ttu-id="0f2e2-124">最初のシナリオでは、`Dispose`() からの例外のためにスキップされるコードを示します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-124">The first scenario demonstrates code being skipped because of an exception from `Dispose`().</span></span> <span data-ttu-id="0f2e2-125">2 番目のシナリオでは、`Dispose`() からの例外のためにマスクされる重要な例外を示します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-125">The second scenario demonstrates an important exception being masked because of an exception from `Dispose`().</span></span> <span data-ttu-id="0f2e2-126">3 番目のシナリオでは、正しいクリーンアップを示します。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-126">The third scenario demonstrates correct clean up.</span></span>  
  
 <span data-ttu-id="0f2e2-127">クライアント プロセスから予期される出力は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-127">The expected output from the client process is:</span></span>  
  
```  
=  
= Demonstrating problem:  closing brace of using statement can throw.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating problem:  closing brace of using statement can mask other Exceptions.  
=  
Got System.ServiceModel.CommunicationException from Divide.  
Got System.ServiceModel.Security.MessageSecurityException  
=  
= Demonstrating cleanup with Exceptions.  
=  
Calling client.Add(0.0, 0.0);  
        client.Add(0.0, 0.0); returned 0  
Calling client.Divide(0.0, 0.0);  
Got System.ServiceModel.CommunicationException from Divide.  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="0f2e2-128">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="0f2e2-128">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="0f2e2-129">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-129">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="0f2e2-130">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-130">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="0f2e2-131">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-131">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="0f2e2-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="0f2e2-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="0f2e2-134">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="0f2e2-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="0f2e2-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Client\UsingUsing`  
  
## <a name="see-also"></a><span data-ttu-id="0f2e2-136">関連項目</span><span class="sxs-lookup"><span data-stu-id="0f2e2-136">See Also</span></span>
