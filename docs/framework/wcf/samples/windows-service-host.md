---
title: "Windows サービス ホスト"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- NT Service
- NT Service Host Sample [Windows Communication Foundation]
ms.assetid: 1b2f45c5-2bed-4979-b0ee-8f9efcfec028
caps.latest.revision: "40"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e3dd2b4880ea61f5c3236a3e15ba1c939dbc2952
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="windows-service-host"></a><span data-ttu-id="605b0-102">Windows サービス ホスト</span><span class="sxs-lookup"><span data-stu-id="605b0-102">Windows Service Host</span></span>
<span data-ttu-id="605b0-103">このサンプルでは、マネージ Windows サービスでホストされる [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスを示します。</span><span class="sxs-lookup"><span data-stu-id="605b0-103">This sample demonstrates a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service hosted in a managed Windows Service.</span></span> <span data-ttu-id="605b0-104">サービス アプレットを使用して Windows サービスが制御される**コントロール パネルの** システムの再起動後に自動的に開始するように構成できます。</span><span class="sxs-lookup"><span data-stu-id="605b0-104">Windows Services are controlled using the Services applet in **Control Panel** and can be configured to start up automatically after a system reboot.</span></span> <span data-ttu-id="605b0-105">このサンプルは、クライアント プログラムと Windows サービス プログラムで構成されています。</span><span class="sxs-lookup"><span data-stu-id="605b0-105">The sample consists of a client program and an Windows Service program.</span></span> <span data-ttu-id="605b0-106">サービスは .exe プログラムとして実装され、独自のホスティング コードが指定されます。</span><span class="sxs-lookup"><span data-stu-id="605b0-106">The service is implemented as an .exe program and contains its own hosting code.</span></span> <span data-ttu-id="605b0-107">Windows プロセス アクティブ化サービス (WAS) やインターネット インフォメーション サービス (IIS) などの他のホスト環境では、ホスティング コードを記述する必要はありません。</span><span class="sxs-lookup"><span data-stu-id="605b0-107">In other hosting environments, such as Windows Process Activation Services (WAS) or Internet Information Services (IIS), it is not necessary for you to write hosting code.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="605b0-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="605b0-108">The set-up procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="605b0-109">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="605b0-109">The samples may already be installed on your computer.</span></span> <span data-ttu-id="605b0-110">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="605b0-110">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="605b0-111">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="605b0-111">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="605b0-112">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="605b0-112">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Hosting\WindowsService`  
  
 <span data-ttu-id="605b0-113">このサービスをビルドしたら、他の Windows サービスと同様、Installutil.exe ユーティリティを使用してインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="605b0-113">After building this service, it must be installed with the Installutil.exe utility like any other Windows Service.</span></span> <span data-ttu-id="605b0-114">サービスを変更する場合は、`installutil /u` を使用して、まずそのサービスをアンインストールする必要があります。</span><span class="sxs-lookup"><span data-stu-id="605b0-114">If you are going to make changes to the service, you must first uninstall it with `installutil /u`.</span></span> <span data-ttu-id="605b0-115">このサンプルに含まれている Setup.bat ファイルは Windows Service をインストールして起動するコマンド ファイルです。同様にこのサンプルに含まれている Cleanup.bat ファイルは、Windows サービスをシャットダウンしてアンインストールするコマンド ファイルです。</span><span class="sxs-lookup"><span data-stu-id="605b0-115">The Setup.bat and Cleanup.bat files included in this sample are the commands to install and start up the Windows Service, and to shut down and uninstall the Windows Service.</span></span> <span data-ttu-id="605b0-116">Windows サービスが実行されている場合、クライアントに応答できるサービスは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのみです。</span><span class="sxs-lookup"><span data-stu-id="605b0-116">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service can only respond to clients if the Windows Service is running.</span></span> <span data-ttu-id="605b0-117">サービス アプレットを使用して、Windows サービスを停止するかどうかは**コントロール パネルの**  、クライアントを実行し、<xref:System.ServiceModel.EndpointNotFoundException>クライアントがサービスにアクセスしようとしたときに例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="605b0-117">If you stop the Windows Service by using the Services applet from **Control Panel** and run the client, a <xref:System.ServiceModel.EndpointNotFoundException> exception occurs when a client attempts to access the service.</span></span> <span data-ttu-id="605b0-118">Windows サービスを再起動してクライアントを再実行した場合は、通信が正常に行われます。</span><span class="sxs-lookup"><span data-stu-id="605b0-118">If you restart the Windows Service and rerun the client, communication succeeds.</span></span>  
  
 <span data-ttu-id="605b0-119">サービス コードにはインストーラー クラス、ICalculator コントラクトを実装する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービス実装クラス、およびランタイム ホストとして機能する Windows サービス クラスが含まれています。</span><span class="sxs-lookup"><span data-stu-id="605b0-119">The service code includes an installer class, a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service implementation class which implements the ICalculator contract, and a Windows Service class that acts as the run-time host.</span></span> <span data-ttu-id="605b0-120">インストーラー クラスは <xref:System.Configuration.Install.Installer> を継承します。このクラスを使用すると、Installutil.exe ツールにより、プログラムを NT サービスとしてインストールできます。</span><span class="sxs-lookup"><span data-stu-id="605b0-120">The installer class, which inherits from <xref:System.Configuration.Install.Installer>, allows the program to be installed as an NT service by the Installutil.exe tool.</span></span> <span data-ttu-id="605b0-121">サービス実装クラス `WcfCalculatorService` は、基本的なサービス コントラクトを実装する [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="605b0-121">The service implementation class, `WcfCalculatorService`, is an [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service that implements a basic service contract.</span></span> <span data-ttu-id="605b0-122">この [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスは、`WindowsCalculatorService` と呼ばれる Windows サービス クラス内でホストされます。</span><span class="sxs-lookup"><span data-stu-id="605b0-122">This [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service is hosted inside a Windows Service class called `WindowsCalculatorService`.</span></span> <span data-ttu-id="605b0-123">Windows サービスとして限定するため、このクラスは <xref:System.ServiceProcess.ServiceBase> を継承し、<xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> メソッドと <xref:System.ServiceProcess.ServiceBase.OnStop> メソッドを実装しています。</span><span class="sxs-lookup"><span data-stu-id="605b0-123">To qualify as a Windows Service, the class inherits from <xref:System.ServiceProcess.ServiceBase> and implements the <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> and <xref:System.ServiceProcess.ServiceBase.OnStop> methods.</span></span> <span data-ttu-id="605b0-124"><xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29> では、<xref:System.ServiceModel.ServiceHost> 型の `WcfCalculatorService` オブジェクトが作成され、開かれます。</span><span class="sxs-lookup"><span data-stu-id="605b0-124">In <xref:System.ServiceProcess.ServiceBase.OnStart%28System.String%5B%5D%29>, a <xref:System.ServiceModel.ServiceHost> object is created for the `WcfCalculatorService` type and opened.</span></span> <span data-ttu-id="605b0-125"><xref:System.ServiceProcess.ServiceBase.OnStop> では、<xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> オブジェクトの <xref:System.ServiceModel.ServiceHost> メソッドが呼び出されて ServiceHost が閉じられます。</span><span class="sxs-lookup"><span data-stu-id="605b0-125">In <xref:System.ServiceProcess.ServiceBase.OnStop>, the ServiceHost is closed by calling the <xref:System.ServiceModel.Channels.CommunicationObject.Close%28System.TimeSpan%29> method of the <xref:System.ServiceModel.ServiceHost> object.</span></span> <span data-ttu-id="605b0-126">使用して、ホストのベース アドレスを構成、 [\<追加 >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md)子である要素の[ \<baseAddresses >](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md)の子である、 [ \<ホスト >](../../../../docs/framework/configure-apps/file-schema/wcf/host.md)子である要素の[\<サービス >](../../../../docs/framework/configure-apps/file-schema/wcf/service.md)要素。</span><span class="sxs-lookup"><span data-stu-id="605b0-126">The host's base address is configured using the [\<add>](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-baseaddresses.md) element, which is a child of [\<baseAddresses>](../../../../docs/framework/configure-apps/file-schema/wcf/baseaddresses.md), which is a child of the [\<host>](../../../../docs/framework/configure-apps/file-schema/wcf/host.md) element, which is a child of the [\<service>](../../../../docs/framework/configure-apps/file-schema/wcf/service.md) element.</span></span>  
  
 <span data-ttu-id="605b0-127">定義されているエンドポイントは、ベース アドレスを使用し、 [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)です。</span><span class="sxs-lookup"><span data-stu-id="605b0-127">The endpoint that is defined uses the base address and a [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).</span></span> <span data-ttu-id="605b0-128">ベース アドレスの構成と CalculatorService を公開するエンドポイントのサンプルを次に示します。</span><span class="sxs-lookup"><span data-stu-id="605b0-128">The following sample shows the configuration of the base address as well as the endpoint that exposes the CalculatorService.</span></span>  
  
```xml  
<services>  
  <service name="Microsoft.ServiceModel.Samples.WcfCalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
    <host>  
      <baseAddresses>  
        <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
      </baseAddresses>  
    </host>  
    <!-- This endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service.  -->  
    <endpoint address=""  
              binding="wsHttpBinding"  
              contract="Microsoft.ServiceModel.Samples.ICalculator" />  
    ...  
  </service>  
</services>  
```  
  
 <span data-ttu-id="605b0-129">このサンプルを実行すると、操作要求と応答がサービスとクライアントの両方のコンソール ウィンドウに表示されます。</span><span class="sxs-lookup"><span data-stu-id="605b0-129">When you run the sample, the operation requests and responses are displayed in both the service and client console windows.</span></span> <span data-ttu-id="605b0-130">どちらかのコンソールで Enter キーを押すと、サービスとクライアントがどちらもシャットダウンされます。</span><span class="sxs-lookup"><span data-stu-id="605b0-130">Press ENTER in each console window to shut down the service and client.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="605b0-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="605b0-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="605b0-132">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="605b0-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="605b0-133">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="605b0-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="605b0-134">ソリューションがビルドされたら、権限のレベルが高い [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] コマンド プロンプトから Setup.bat を実行し、Installutil.exe ツールを使用して Windows サービスをインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="605b0-134">After the solution has been built, run Setup.bat from an elevated [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] command prompt to install the Windows service using the Installutil.exe tool.</span></span> <span data-ttu-id="605b0-135">このサービスは、[サービス] に表示されます。</span><span class="sxs-lookup"><span data-stu-id="605b0-135">The service should appear in Services.</span></span>  
  
4.  <span data-ttu-id="605b0-136">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="605b0-136">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="605b0-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="605b0-137">See Also</span></span>  
 [<span data-ttu-id="605b0-138">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="605b0-138">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
