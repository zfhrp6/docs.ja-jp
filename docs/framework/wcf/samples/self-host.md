---
title: "自己ホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Self hosted service
- Self Host Sample [Windows Communication Foundation]
ms.assetid: 05e68661-1ddf-4abf-a899-9bb1b8272a5b
caps.latest.revision: "38"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1513d0e534da4ef12d8bcf345bdb34ac40912b4e
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="self-host"></a><span data-ttu-id="723f9-102">自己ホスト</span><span class="sxs-lookup"><span data-stu-id="723f9-102">Self-Host</span></span>
<span data-ttu-id="723f9-103">このサンプルでは、自己ホスト型サービスをコンソール アプリケーションに実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="723f9-103">This sample demonstrates how to implement a self-hosted service in a console application.</span></span> <span data-ttu-id="723f9-104">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="723f9-104">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span> <span data-ttu-id="723f9-105">サービス構成ファイルは、名前が Web.config から App.config に変更され、ホストが使用するベース アドレスを構成するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="723f9-105">The service configuration file has been renamed from Web.config to App.config and modified to configure a base address, which the host uses.</span></span> <span data-ttu-id="723f9-106">サービス ソース コードは、構成されたベース アドレスを提供するサービス ホストを作成して開く、静的な `Main` 関数を実装するように変更されました。</span><span class="sxs-lookup"><span data-stu-id="723f9-106">The service source code has been modified to implement a static `Main` function that creates and opens a service host that provides the configured base address.</span></span> <span data-ttu-id="723f9-107">サービス実装は、操作ごとにコンソールに出力を書き込むように変更されました。</span><span class="sxs-lookup"><span data-stu-id="723f9-107">The service implementation has been modified to write output to the console for each operation.</span></span> <span data-ttu-id="723f9-108">クライアントは、サービスのエンドポイント アドレスが正しく構成されたことを除き、変更されていません。</span><span class="sxs-lookup"><span data-stu-id="723f9-108">The client has been unmodified, except for configuring the correct endpoint address of the service.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="723f9-109">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="723f9-109">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="723f9-110">このサンプルは、静的な main 関数を実装し、指定された <xref:System.ServiceModel.ServiceHost> 型の `CalculatorService` を作成します。次のサンプル コードを参照してください。</span><span class="sxs-lookup"><span data-stu-id="723f9-110">The sample implements a static main function to create a <xref:System.ServiceModel.ServiceHost> for the given `CalculatorService` type, as shown in the following sample code.</span></span>  
  
```  
// Host the service within this EXE console application.  
public static void Main()  
{  
    // Create a ServiceHost for the CalculatorService type.  
    using (ServiceHost serviceHost =   
           new ServiceHost(typeof(CalculatorService)))  
    {  
        // Open the ServiceHost to create listeners   
        // and start listening for messages.  
        serviceHost.Open();  
  
        // The service can now be accessed.  
        Console.WriteLine("The service is ready.");  
        Console.WriteLine("Press <ENTER> to terminate service.");  
        Console.WriteLine();  
        Console.ReadLine();  
    }  
}  
```  
  
 <span data-ttu-id="723f9-111">サービスがインターネット インフォメーション サービス (IIS) または Windows プロセス アクティブ化サービス (WAS) にホストされている場合、サービスのベース アドレスはホスト環境から提供されます。</span><span class="sxs-lookup"><span data-stu-id="723f9-111">When a service is hosted in Internet Information Services (IIS) or Windows Process Activation Service (WAS), the base address of the service is provided by the hosting environment.</span></span> <span data-ttu-id="723f9-112">自己ホスト型の場合は、ベース アドレスを手動で指定する必要があります。</span><span class="sxs-lookup"><span data-stu-id="723f9-112">In the self-hosted case, you must specify the base address yourself.</span></span> <span data-ttu-id="723f9-113">これを使用して、 `add` 、要素の子[ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)の子[\<ホスト >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)の子[\<サービス >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)のサンプル構成を次に示すようにします。</span><span class="sxs-lookup"><span data-stu-id="723f9-113">This is done using the `add` element, child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), child of [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md), child of [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) as demonstrated in the following sample configuration.</span></span>  
  
```xml  
<service   
    name="Microsoft.ServiceModel.Samples.CalculatorService"  
    behaviorConfiguration="CalculatorServiceBehavior">  
  <host>  
    <baseAddresses>  
      <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
    </baseAddresses>  
  </host>  
  ...  
</service>  
```  
  
 <span data-ttu-id="723f9-114">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="723f9-114">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="723f9-115">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="723f9-115">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="723f9-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="723f9-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="723f9-117">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="723f9-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="723f9-118">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="723f9-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="723f9-119">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="723f9-119">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="723f9-120">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="723f9-120">The samples may already be installed on your computer.</span></span> <span data-ttu-id="723f9-121">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="723f9-121">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="723f9-122">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="723f9-122">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="723f9-123">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="723f9-123">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\SelfHost`  
  
## <a name="see-also"></a><span data-ttu-id="723f9-124">関連項目</span><span class="sxs-lookup"><span data-stu-id="723f9-124">See Also</span></span>  
 [<span data-ttu-id="723f9-125">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="723f9-125">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
