---
title: インライン コードを使用した IIS ホスティング
ms.date: 03/30/2017
helpviewer_keywords:
- Web hosted service
- IIS Hosting Using Inline Code Sample [Windows Communication Foundation]
ms.assetid: 56fe3687-a34b-4661-8e30-b33770f413fa
ms.openlocfilehash: 760607bc7ebf2662a7a3a93b2ebf76114580f42b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="iis-hosting-using-inline-code"></a><span data-ttu-id="70b22-102">インライン コードを使用した IIS ホスティング</span><span class="sxs-lookup"><span data-stu-id="70b22-102">IIS Hosting Using Inline Code</span></span>
<span data-ttu-id="70b22-103">このサンプルでは、インターネット インフォメーション サービス (IIS) によってホストされるサービスを実装する方法を示します。サービス コードは .svc ファイルにインラインで含まれており、必要に応じてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="70b22-103">This sample demonstrates how to implement a service hosted by Internet Information Services (IIS), where the service code is contained in-line in a .svc file and is compiled on demand.</span></span> <span data-ttu-id="70b22-104">サービス コードは、アプリケーションの \App_Code ディレクトリにあるソース コード ファイルに直接実装するか、または \bin に配置されるアセンブリにコンパイルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="70b22-104">Service code can also be implemented directly in source code files located in the application's \App_Code directory, or compiled into assembly deployed in \bin.</span></span> <span data-ttu-id="70b22-105">ただし、このサンプルではこれらの手法は示しません。</span><span class="sxs-lookup"><span data-stu-id="70b22-105">This sample does not demonstrate these techniques.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="70b22-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="70b22-106">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="70b22-107">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="70b22-107">The samples may already be installed on your computer.</span></span> <span data-ttu-id="70b22-108">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="70b22-108">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="70b22-109">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="70b22-109">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="70b22-110">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="70b22-110">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WebHost\InlineCode`  
  
 <span data-ttu-id="70b22-111">このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装する一般的なサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="70b22-111">The sample demonstrates a typical service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="70b22-112">このサービスは IIS によってホストされ、サービス コードは Service.svc ファイルに完全に含まれています。</span><span class="sxs-lookup"><span data-stu-id="70b22-112">The service is hosted in IIS and the service code is entirely contained in the Service.svc file.</span></span> <span data-ttu-id="70b22-113">サービスはホストによってアクティブ化され、このサービスに最初に送信されるメッセージによって必要に応じてコンパイルされます。</span><span class="sxs-lookup"><span data-stu-id="70b22-113">The service is host-activated and compiled on-demand by the first message sent to the service.</span></span> <span data-ttu-id="70b22-114">あらかじめコンパイルしておく必要はありません。</span><span class="sxs-lookup"><span data-stu-id="70b22-114">There is no pre-compilation necessary.</span></span> <span data-ttu-id="70b22-115">サービスは、次に示すコードで定義される `ICalculator` コントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="70b22-115">The service implements an `ICalculator` contract as defined in the following code:</span></span>  
  
```  
// Define a service contract.  
[ServiceContract(Namespace="http://Microsoft.ServiceModel.Samples")]  
    public interface ICalculator  
{  
    [OperationContract]  
    double Add(double n1, double n2);  
    [OperationContract]  
    double Subtract(double n1, double n2);  
    [OperationContract]  
    double Multiply(double n1, double n2);  
    [OperationContract]  
    double Divide(double n1, double n2);  
}  
```  
  
 <span data-ttu-id="70b22-116">このサービス実装は、計算を行い、結果を返します。</span><span class="sxs-lookup"><span data-stu-id="70b22-116">The service implementation calculates and returns the appropriate result.</span></span>  
  
```  
<%@ServiceHost language=c# Debug="true" Service="Microsoft.ServiceModel.Samples.CalculatorService" %>   
…  
// Service class that implements the service contract.  
public class CalculatorService : ICalculator  
{  
    public double Add(double n1, double n2)  
    {  
        return n1 + n2;  
    }  
    public double Subtract(double n1, double n2)  
    {  
        return n1 - n2;  
    }  
    public double Multiply(double n1, double n2)  
    {  
        return n1 * n2;  
    }  
    public double Divide(double n1, double n2)  
    {  
        return n1 / n2;  
    }  
}  
```  
  
 <span data-ttu-id="70b22-117">このサンプルを実行すると、操作要求および応答がクライアントのコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="70b22-117">When you run the sample, the operation requests and responses are displayed in the client console window.</span></span> <span data-ttu-id="70b22-118">クライアントをシャットダウンするには、クライアント ウィンドウで Enter キーを押します。</span><span class="sxs-lookup"><span data-stu-id="70b22-118">Press ENTER in the client window to shut down the client.</span></span>  
  
```  
Add(100,15.99) = 115.99  
Subtract(145,76.54) = 68.46  
Multiply(9,81.25) = 731.25  
Divide(22,7) = 3.14285714285714  
  
Press <ENTER> to terminate client.  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="70b22-119">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="70b22-119">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="70b22-120">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="70b22-120">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="70b22-121">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="70b22-121">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="70b22-122">ソリューションがビルドされたら、setup.bat を実行し、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] で ServiceModelSamples アプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="70b22-122">After the solution has been built, run setup.bat to set up the ServiceModelSamples Application in [!INCLUDE[iisver](../../../../includes/iisver-md.md)].</span></span> <span data-ttu-id="70b22-123">ServiceModelSamples ディレクトリは、[!INCLUDE[iisver](../../../../includes/iisver-md.md)] アプリケーションとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="70b22-123">The ServiceModelSamples directory should now appear as an [!INCLUDE[iisver](../../../../includes/iisver-md.md)] Application.</span></span>  
  
4.  <span data-ttu-id="70b22-124">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="70b22-124">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span> <span data-ttu-id="70b22-125">このサービスを呼び出すことができるクライアント アプリケーションを作成する方法の例は、次を参照してください。[する方法: クライアントを作成する](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md)です。</span><span class="sxs-lookup"><span data-stu-id="70b22-125">For an example on how to create a client application that can call this service, see [How to: Create a Client](../../../../docs/framework/wcf/how-to-create-a-wcf-client.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="70b22-126">関連項目</span><span class="sxs-lookup"><span data-stu-id="70b22-126">See Also</span></span>  
 [<span data-ttu-id="70b22-127">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="70b22-127">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
