---
title: "構成ベースのアクティブ化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 21bb762e-c43e-4b0c-887b-5e434d665838
caps.latest.revision: "26"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d520a46bc3380fc5dff76f5df866ae3411d5a6a7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="configuration-based-activation"></a><span data-ttu-id="ddfb2-102">構成ベースのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="ddfb2-102">Configuration-Based Activation</span></span>
<span data-ttu-id="ddfb2-103">このサンプルでは、.svc ファイルを使用せずに [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスをアクティブ化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-103">This sample demonstrates how to activate [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] services without requiring a .svc file.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="ddfb2-104">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-104">The samples may already be installed on your computer.</span></span> <span data-ttu-id="ddfb2-105">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-105">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="ddfb2-106">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-106">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="ddfb2-107">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-107">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\ConfigBasedActivation`  
  
## <a name="sample-details"></a><span data-ttu-id="ddfb2-108">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="ddfb2-108">Sample Details</span></span>  
 <span data-ttu-id="ddfb2-109">このサンプルでは、クライアントは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] テスト クライアントで、サービスは IIS によってホストされています。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-109">In this sample, the client is the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] test client and the service is hosted in IIS.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddfb2-110">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-110">The setup and build instructions for this sample are located at the end of this topic.</span></span>  
  
### <a name="activation-of-services-without-requiring-a-svc-file"></a><span data-ttu-id="ddfb2-111">.svc ファイルを必要としない、サービスのアクティブ化</span><span class="sxs-lookup"><span data-stu-id="ddfb2-111">Activation of services without requiring a .svc file</span></span>  
 <span data-ttu-id="ddfb2-112">[!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)] では、サービスをアクティブ化するために .svc ファイルが必要でした。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-112">In [!INCLUDE[netfx35_short](../../../../includes/netfx35-short-md.md)], a .svc file was required for activating a service.</span></span> <span data-ttu-id="ddfb2-113">アプリケーションと共に追加ファイルを配置して管理する必要があったため、このことは管理のオーバーヘッドを増やす原因となりました。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-113">This caused additional management overhead, because an additional file was required to be deployed and maintained along with the application.</span></span> <span data-ttu-id="ddfb2-114">[!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] リリースでは、アプリケーション構成ファイルを使用してアクティブ化コンポーネントを構成することができます。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-114">With the release of [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)], the activation components can be configured using the application configuration file.</span></span>  
  
 [!INCLUDE[netfx40_short](../../../../includes/netfx40-short-md.md)]<span data-ttu-id="ddfb2-115"> では、アプリケーション構成ファイルの <xref:System.ServiceModel.Configuration.ServiceActivationElement> に、新しい構成要素 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> が導入されています。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-115"> introduces a new configuration element (<xref:System.ServiceModel.Configuration.ServiceActivationElement>), in the <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> of the application configuration file.</span></span> <span data-ttu-id="ddfb2-116"><xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> コレクションは、次のコード例に示すように、サービスのコレクションを受け取ってアクティブ化を行います。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-116">The <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection> collection accepts a collection of services to activate, as shown in the following code example.</span></span>  
  
```xml  
<serviceActivations>  
   <add relativeAddress="Calculator.svc" service="Microsoft.ServiceModel.Samples.CalculatorService" />  
  
<serviceActivations>  
```  
  
 <span data-ttu-id="ddfb2-117">注目すべき点は、構成が .svc ファイルの構成に非常に似ていることです。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-117">The observation to make is the configuration looks very similar to the configuration of .svc files.</span></span> <span data-ttu-id="ddfb2-118">導入された追加の属性は、サービスのアドレスを提供する `relativeAddress` です。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-118">An additional attribute that is introduced is the `relativeAddress` that provides the address of the service.</span></span> <span data-ttu-id="ddfb2-119">相対アドレスは、サービスの仮想パスでもあります。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-119">The relative address is also the virtual path for the service.</span></span> <span data-ttu-id="ddfb2-120">ホストは、ファイルの Web.config ファイルが存在する場合に、そのファイルを `virtualPath` の場所から取得します。ファイルが存在しない場合、ホストはその親フォルダーを再帰的に検索します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-120">The host retrieves the Web.config file of the file from the `virtualPath` location, if present; otherwise the host searches its parent folder recursively.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="ddfb2-121">このサンプルを機能させるには、IIS でホストする必要があります。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-121">This sample requires hosting in IIS to function.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="ddfb2-122">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="ddfb2-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="ddfb2-123">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して、Service.csproj ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-123">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open the Service.csproj file.</span></span>  
  
2.  <span data-ttu-id="ddfb2-124">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="ddfb2-125">WCFTestClient.exe を実行してサービスをテストします。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-125">Test the service by running WCFTestClient.exe.</span></span>  
  
4.  <span data-ttu-id="ddfb2-126">[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)]を使用して、%SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-126">Using [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)], navigate to the %SystemDrive%\Program Files\Microsoft Visual Studio 10.0\Common7\IDE folder.</span></span>  
  
5.  <span data-ttu-id="ddfb2-127">WcfTestClient.exe を実行します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-127">Run WcfTestClient.exe.</span></span>  
  
6.  <span data-ttu-id="ddfb2-128">サービスの MEX アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-128">Set the MEX address of the service.</span></span>  
  
7.  <span data-ttu-id="ddfb2-129">Ctrl と Shift キーを押しながら A キーを押して、サービス アドレスを設定します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-129">Press CTRL+SHIFT+A to set the service address.</span></span>  
  
8.  <span data-ttu-id="ddfb2-130">アドレスを http://localhost/ServiceModelSamples/Calculator.svc に設定します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-130">Set the address to http://localhost/ServiceModelSamples/Calculator.svc.</span></span>  
  
9. <span data-ttu-id="ddfb2-131">`Add` 操作を実行します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-131">Perform the `Add` operation.</span></span> <span data-ttu-id="ddfb2-132">`n1` パラメーターの値を 10 に、`n2` パラメーターの値を 15 に設定します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-132">Set value on the `n1` parameter to 10 and set value on the `n2` parameter to 15.</span></span>  
  
10. <span data-ttu-id="ddfb2-133">キーを押して**呼び出す**です。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-133">Press **Invoke**.</span></span>  
  
     <span data-ttu-id="ddfb2-134">予期される結果は 25 です。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-134">The expected result is 25.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="ddfb2-135">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="ddfb2-135">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="ddfb2-136">実行することを確認、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-136">Be sure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="ddfb2-137">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-137">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="ddfb2-138">ソリューションがビルドされたら、Setup.bat を実行し、IIS で ServiceModelSamples アプリケーションを設定します。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-138">After the solution has been built, run Setup.bat to set up the ServiceModelSamples Application in IIS.</span></span> <span data-ttu-id="ddfb2-139">ServiceModelSamples ディレクトリは、IIS アプリケーションとして表示されます。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-139">The ServiceModelSamples directory should now appear as an IIS Application.</span></span>  
  
4.  <span data-ttu-id="ddfb2-140">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="ddfb2-140">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ddfb2-141">参照</span><span class="sxs-lookup"><span data-stu-id="ddfb2-141">See Also</span></span>  
 [<span data-ttu-id="ddfb2-142">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="ddfb2-142">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
