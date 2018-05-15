---
title: 調整
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, throttling sample
- Throttling Sample [Windows Communication Foundation]
ms.assetid: 40bb3582-8ae9-4410-96f0-6c515bfaf47c
ms.openlocfilehash: 686cc1ef74f11cbccfeba49a642239cb6bd33204
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="throttling"></a><span data-ttu-id="b5b8b-102">調整</span><span class="sxs-lookup"><span data-stu-id="b5b8b-102">Throttling</span></span>
<span data-ttu-id="b5b8b-103">調整のサンプルでは、調整コントロールの使用方法を示します。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-103">The Throttling sample demonstrates the use of throttling controls.</span></span> <span data-ttu-id="b5b8b-104">調整コントロールは、同時呼び出し、同時インスタンス、または同時セッションの数を制限して、リソースの過剰消費を防ぎます。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-104">Throttling controls place limits on the number of concurrent calls, instances, or sessions to prevent over-consumption of resources.</span></span> <span data-ttu-id="b5b8b-105">調整の動作は、サービス構成ファイルの設定で指定されます。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-105">Throttling behavior is specified in service configuration file settings.</span></span> <span data-ttu-id="b5b8b-106">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)電卓サービスを実装します。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-106">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) that implements a calculator service.</span></span>  
  
 <span data-ttu-id="b5b8b-107">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-107">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b5b8b-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="b5b8b-109">サービス構成ファイルで調整コントロールの指定、 [ \<serviceThrottling >](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md)のサンプル構成を次に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-109">The service configuration file specifies throttling controls in a [\<serviceThrottling>](../../../../docs/framework/configure-apps/file-schema/wcf/servicethrottling.md), as shown in the following sample configuration.</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDebug includeExceptionDetailInFaults="False" />  
      <serviceMetadata httpGetEnabled="True"/>  
      <!-- Specify throttling behavior -->  
    <serviceThrottling maxConcurrentCalls="2"  
                       maxConcurrentInstances="10"/>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="b5b8b-110">上記の構成では、サービスは同時呼び出しの最大数を 2 に、同時インスタンスの最大数を 10 に制限しています。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-110">As configured, the service limits the maximum concurrent calls to 2, and the maximum number of concurrent instances to 10.</span></span>  
  
 <span data-ttu-id="b5b8b-111">調整の例を示すため、サービス メソッド上でスリープ時間を次のように定義しています。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-111">In order to demonstrate throttling we define a sleep time on the service methods as follows:</span></span>  
  
```  
public double Add(double n1, double n2)  
{  
    System.Threading.Thread.Sleep(2000);  
    return n1 + n2;  
}  
```  
  
 <span data-ttu-id="b5b8b-112">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-112">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="b5b8b-113">Add メソッドと Subtract メソッドは同時に実行され、Multiply メソッドと Divide メソッドは同時に実行されます。このようにして、同時実行できるメソッドは 2 つ以下であることが証明され、調整の例が示されます。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-113">The Add and Subtract methods are executed concurrently and the Multiply and Divide methods are executed concurrently proving that not more than 2 methods can be executed concurrently thus demonstrating throttling.</span></span>  
  
```  
Press <ENTER> to terminate client.  
Add(100,15.99)  
Subtract(145,76.54)  
Multiply(9,81.25)  
Divide(22,7)  
  
Add Result: 115.99  
Subtract Result: 68.46  
Multiply Result: 731.25  
Divide Result: 3.14285714285714  
  
Press any key to continue . . .  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="b5b8b-114">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="b5b8b-114">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="b5b8b-115">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-115">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="b5b8b-116">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-116">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="b5b8b-117">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-117">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="b5b8b-118">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-118">The samples may already be installed on your machine.</span></span> <span data-ttu-id="b5b8b-119">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-119">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="b5b8b-120">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-120">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="b5b8b-121">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="b5b8b-121">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Throttling`  
  
## <a name="see-also"></a><span data-ttu-id="b5b8b-122">関連項目</span><span class="sxs-lookup"><span data-stu-id="b5b8b-122">See Also</span></span>
