---
title: WMI プロバイダー
ms.date: 03/30/2017
ms.assetid: 462f0db3-f4a4-4a4b-ac26-41fc25c670a4
ms.openlocfilehash: d135466c402fa21b6a1b11f208ca900f58748bdb
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="wmi-provider"></a><span data-ttu-id="99c29-102">WMI プロバイダー</span><span class="sxs-lookup"><span data-stu-id="99c29-102">WMI Provider</span></span>
<span data-ttu-id="99c29-103">このサンプルでは、実行時に Windows Communication Foundation (WCF) サービスから WCF に組み込まれている Windows Management Instrumentation (WMI) プロバイダーを使用してデータを収集する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="99c29-103">This sample demonstrates how to gather data from Windows Communication Foundation (WCF) services at runtime by using the Windows Management Instrumentation (WMI) provider that is built into WCF.</span></span> <span data-ttu-id="99c29-104">また、このサンプルでは、ユーザー定義の WMI オブジェクトをサービスに追加する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="99c29-104">Also, this sample demonstrates how to add a user-defined WMI object to a service.</span></span> <span data-ttu-id="99c29-105">サンプル用の WMI プロバイダーをアクティブ化、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)からデータを収集する方法を説明し、`ICalculator`実行時にサービス。</span><span class="sxs-lookup"><span data-stu-id="99c29-105">The sample activates the WMI provider for the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md) and demonstrates how to gather data from the `ICalculator` service at runtime.</span></span>  
  
 <span data-ttu-id="99c29-106">WMI は、Web ベースのエンタープライズ管理 (WBEM) 標準をマイクロソフトが実装したものです。</span><span class="sxs-lookup"><span data-stu-id="99c29-106">WMI is Microsoft's implementation of the Web-Based Enterprise Management (WBEM) standard.</span></span> <span data-ttu-id="99c29-107">WMI SDK の詳細については、次を参照してください。 [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx)です。</span><span class="sxs-lookup"><span data-stu-id="99c29-107">For more information about the WMI SDK, see [Windows Management Instrumentation](https://msdn.microsoft.com/library/aa394582.aspx).</span></span> <span data-ttu-id="99c29-108">WBEM は、アプリケーションが Management Instrumentation を外部管理ツールに開示する業界標準の方法です。</span><span class="sxs-lookup"><span data-stu-id="99c29-108">WBEM is an industry standard for how applications expose management instrumentation to external management tools.</span></span>  
  
 <span data-ttu-id="99c29-109">WCF では、WMI プロバイダー、WBEM と互換性のあるインターフェイスを通して実行時にインストルメンテーションを公開するコンポーネントを実装します。</span><span class="sxs-lookup"><span data-stu-id="99c29-109">WCF implements a WMI provider, a component that exposes instrumentation at runtime through a WBEM-compatible interface.</span></span> <span data-ttu-id="99c29-110">管理ツールは、実行時にインターフェイスを介してサービスに接続できます。</span><span class="sxs-lookup"><span data-stu-id="99c29-110">Management tools can connect to the services through the interface at runtime.</span></span> <span data-ttu-id="99c29-111">WCF では、アドレス、バインディング、動作、リスナーなどのサービスの属性を公開します。</span><span class="sxs-lookup"><span data-stu-id="99c29-111">WCF exposes attributes of services such as addresses, bindings, behaviors, and listeners.</span></span>  
  
 <span data-ttu-id="99c29-112">組み込みの WMI プロバイダーは、アプリケーションの構成ファイルでアクティブにされます。</span><span class="sxs-lookup"><span data-stu-id="99c29-112">The built-in WMI provider is activated in the configuration file of the application.</span></span> <span data-ttu-id="99c29-113">これには、`wmiProviderEnabled`の属性、 [\<診断 >](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md)で、 [ \<system.serviceModel >](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)セクションで、次の例のように構成:</span><span class="sxs-lookup"><span data-stu-id="99c29-113">This is done through the `wmiProviderEnabled` attribute of the [\<diagnostics>](../../../../docs/framework/configure-apps/file-schema/wcf/diagnostics.md) in the [\<system.serviceModel>](../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md) section, as shown in the following sample configuration:</span></span>  
  
```xml  
<system.serviceModel>  
    ...  
    <diagnostics wmiProviderEnabled="true" />  
    ...  
</system.serviceModel>  
```  
  
 <span data-ttu-id="99c29-114">この構成エントリには、WMI インターフェイスが開示されます。</span><span class="sxs-lookup"><span data-stu-id="99c29-114">This configuration entry exposes a WMI interface.</span></span> <span data-ttu-id="99c29-115">管理アプリケーションはこのインターフェイスを通して接続し、アプリケーションの Management Instrumentation にアクセスできるようになります。</span><span class="sxs-lookup"><span data-stu-id="99c29-115">Management applications can now connect through this interface and access the management instrumentation of the application.</span></span>  
  
## <a name="custom-wmi-object"></a><span data-ttu-id="99c29-116">カスタム WMI オブジェクト</span><span class="sxs-lookup"><span data-stu-id="99c29-116">Custom WMI Object</span></span>  
 <span data-ttu-id="99c29-117">WMI オブジェクトをサービスに追加すると、組み込みの WMI プロバイダーの情報と共にユーザー定義の情報を開示できます。</span><span class="sxs-lookup"><span data-stu-id="99c29-117">Adding WMI objects to a service makes it possible to reveal user-defined information along with the built-in WMI provider information.</span></span> <span data-ttu-id="99c29-118">これは、Installutil.exe アプリケーションを使用してサービスのスキーマを WMI に公開することによって実現されます。</span><span class="sxs-lookup"><span data-stu-id="99c29-118">This is accomplished by publishing the schema of the service to WMI by using the Installutil.exe application.</span></span> <span data-ttu-id="99c29-119">これを行うための手順および詳細情報は、このトピックの最後のセットアップ手順で示します。</span><span class="sxs-lookup"><span data-stu-id="99c29-119">Instructions to accomplish this, along with more details can be found in the setup instructions at the end of the topic.</span></span>  
  
## <a name="accessing-wmi-information"></a><span data-ttu-id="99c29-120">WMI 情報へのアクセス</span><span class="sxs-lookup"><span data-stu-id="99c29-120">Accessing WMI Information</span></span>  
 <span data-ttu-id="99c29-121">WMI データには、複数の異なる方法でアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="99c29-121">WMI data can be accessed many different ways.</span></span> <span data-ttu-id="99c29-122">マイクロソフトでは、WMI Api を提供するスクリプト、Visual Basic アプリケーションの場合、C++ アプリケーション、および[!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)](http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp)です。</span><span class="sxs-lookup"><span data-stu-id="99c29-122">Microsoft provides WMI APIs for scripts, Visual Basic applications, C++ applications, and the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] (http://msdn.microsoft.com/library/default.asp?url=/library/wmisdk/wmi/using_wmi.asp).</span></span>  
  
 <span data-ttu-id="99c29-123">このサンプルでは、2 つの Java スクリプトを使用します。1 つ目は、コンピューター上で実行されているサービスとその一部のプロパティを列挙するスクリプトで、2 つ目はユーザー定義の WMI データを表示するスクリプトです。</span><span class="sxs-lookup"><span data-stu-id="99c29-123">This sample uses two Java scripts: one to enumerate services running on the computer along with some of their properties and the second to view user-defined WMI data.</span></span> <span data-ttu-id="99c29-124">スクリプトは、WMI プロバイダーへの接続を開き、データを解析し、収集されたデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="99c29-124">The script opens a connection to the WMI provider, parses data, and displays the data gathered.</span></span>  
  
 <span data-ttu-id="99c29-125">サンプルを開始して、WCF サービスの実行中のインスタンスを作成します。</span><span class="sxs-lookup"><span data-stu-id="99c29-125">Start the sample to create a running instance of a WCF service.</span></span> <span data-ttu-id="99c29-126">サービスの実行中は、コマンド プロンプトで次のコマンドを入力することによって、それぞれの Java スクリプトを実行してください。</span><span class="sxs-lookup"><span data-stu-id="99c29-126">While the service is running, run each Java script by using the following command at the command prompt:</span></span>  
  
```  
cscript EnumerateServices.js  
```  
  
 <span data-ttu-id="99c29-127">スクリプトは、サービスに含まれているインストルメンテーションにアクセスし、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="99c29-127">The script accesses the instrumentation contained in the service and produces the following output:</span></span>  
  
```  
Microsoft (R) Windows Script Host Version 5.6  
Copyright © Microsoft Corporation 1996-2001. All rights reserved.  
  
1 service(s) found.  
|-PID:           5776  
|-DistinguishedName:  CalculatorService@http://localhost/ServiceModelSamples/service.svc  
|-Endpoints:     1 endpoints  
  |-CalculatorService.ICalculator@http://localhost/ServiceModelSamples/service.svc  
    |-Address:                        http://localhost/ServiceModelSamples/service.svc  
    |-CounterInstanceName:  
    |-AddressHeaders:                 0  
    |-ContractType:                   Contract.Name='ICalculator'  
    |-BindingElements:                4 bindings  
      |-BindingElements[0]  
        |-Type:                       TransactionFlowBindingElement  
      |-BindingElements[1]  
        |-Type:                       SymmetricSecurityBindingElement  
      |-BindingElements[2]  
        |-Type:                       TextMessageEncodingBindingElement  
        |-MaxReadPoolSize:            64  
        |-MaxWritePoolSize:           16  
      |-BindingElements[3]  
        |-Type:                       HttpTransportBindingElement  
        |-ManualAddressing:           false  
        |-MaxBufferSize:              65536  
        |-AllowCookies:               false  
        |-AuthenticationScheme:       Anonymous  
        |-BypassProxyOnLocal:         false  
        |-HostNameComparisonMode:     StrongWildcard  
        |-ProxyAddress:               null  
        |-ProxyAuthenticationScheme:  Anonymous  
        |-Realm:  
        |-TransferMode:               Buffered  
        |-UseDefaultWebProxy:         true  
|-Behaviors:     5 behaviors  
      |-Behavior[0]  
      |-Type:                       ServiceBehaviorAttribute  
        |-AddressFilterMode:               Exact  
        |-AutomaticSessionShutdown:        true  
        |-ConcurrencyMode:                 Single  
        |-IncludeExceptionDetailInFaults:  false  
        |-InstanceContextMode:             PerSession  
        |-TransactionIsolationLevel:       Unspecified  
        |-TransactionTimeout:              null  
        |-ValidateMustUnderstand:          true  
      |-Behavior[1]  
      |-Type:                       AspNetCompatibilityRequirementsAttribute  
      |-Behavior[2]  
      |-Type:                       ServiceDebugBehavior  
      |-Behavior[3]  
      |-Type:                       ServiceAuthorizationBehavior  
      |-Behavior[4]  
      |-Type:                       Behavior  
```  
  
 <span data-ttu-id="99c29-128">次に、2 つ目の Java スクリプトを実行して、ユーザー定義の WMI データを表示します。</span><span class="sxs-lookup"><span data-stu-id="99c29-128">Next, run the second Java Script to display the user-defined WMI data:</span></span>  
  
```  
cscript EnumerateCustomObjects.js  
```  
  
 <span data-ttu-id="99c29-129">スクリプトは、サービスに含まれているユーザー定義のインストルメンテーションにアクセスし、次の出力を生成します。</span><span class="sxs-lookup"><span data-stu-id="99c29-129">The script accesses the user-defined instrumentation contained in the services and produces the following output:</span></span>  
  
```  
1 WMIObject(s) found.  
|-PID:           30285bfd-9d66-4c4e-9be2-310499c5cef5  
|-InstanceId:    3839  
|-WMIInfo:       User Defined WMI Information.  
```  
  
 <span data-ttu-id="99c29-130">この出力は、コンピューター上で 1 つのサービスが実行中であることを示しています。</span><span class="sxs-lookup"><span data-stu-id="99c29-130">The output shows that there is a single service running on the computer.</span></span> <span data-ttu-id="99c29-131">サービスは、`ICalculator` コントラクトを実装する 1 つのエンドポイントを公開します。</span><span class="sxs-lookup"><span data-stu-id="99c29-131">The service exposes one endpoint that implements the `ICalculator` contract.</span></span> <span data-ttu-id="99c29-132">このエンドポイントによって実装されている動作とバインディングの設定は、メッセージ スタックの個々の要素の合計として表示されます。</span><span class="sxs-lookup"><span data-stu-id="99c29-132">The settings of the behavior and binding that are implemented by the endpoint are listed as the sum of individual elements of the messaging stack.</span></span>  
  
 <span data-ttu-id="99c29-133">WMI では、WCF インフラストラクチャの management instrumentation を公開することに限定されません。</span><span class="sxs-lookup"><span data-stu-id="99c29-133">WMI is not limited to exposing the management instrumentation of the WCF infrastructure.</span></span> <span data-ttu-id="99c29-134">独自のドメイン固有のデータ アイテムを、同じ機構を使用して公開できます。</span><span class="sxs-lookup"><span data-stu-id="99c29-134">The application can expose its own domain-specific data items through the same mechanism.</span></span> <span data-ttu-id="99c29-135">WMI は、Web サービスの検査と制御のための統一された機構です。</span><span class="sxs-lookup"><span data-stu-id="99c29-135">WMI is a unified mechanism for inspection and control of a Web service.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="99c29-136">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="99c29-136">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="99c29-137">確実に実行する、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="99c29-137">Ensure you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="99c29-138">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="99c29-138">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="99c29-139">サービス スキーマを WMI に公開します。これを行うには、ホスト ディレクトリ内の service.dll ファイルに対して、InstallUtil.exe (既定の場所は "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") を実行します。</span><span class="sxs-lookup"><span data-stu-id="99c29-139">Publish the services schema to WMI by running the InstallUtil.exe (the default locations for InstallUtil.exe is "%WINDIR%\Microsoft.NET\Framework\v4.0.30319") on the service.dll file in the hosting directory.</span></span> <span data-ttu-id="99c29-140">この手順を実行する必要があるのは、service.dll ファイルを変更した場合のみです。</span><span class="sxs-lookup"><span data-stu-id="99c29-140">This step only needs to be executed when changes have been made to the service.dll file.</span></span> <span data-ttu-id="99c29-141">詳細については、アプリケーションのインストルメント化による管理情報の提供を参照してください: http://msdn2.microsoft.com/library/ms186147.aspx 「方法に:: 発行のスキームをインストルメント化されたアプリケーションの WMI に」セクションでします。</span><span class="sxs-lookup"><span data-stu-id="99c29-141">For more information, see Providing Management Information by Instrumenting Applications at: http://msdn2.microsoft.com/library/ms186147.aspx in the "How To: Publish the Scheme to WMI for an Instrumented Application" section.</span></span>  
  
4.  <span data-ttu-id="99c29-142">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="99c29-142">To run the sample in a single- or cross-computer configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="99c29-143">ASP.NET のインストール後に WCF がインストールされている場合場合があります"%WINDIR%\ を実行する必要があります。Microsoft.Net\Framework\v3.0\Windows 通信 Foundation\servicemodelreg.exe"-r-x WMI オブジェクトをパブリッシュする、ASPNET アカウントの権限を付与します。</span><span class="sxs-lookup"><span data-stu-id="99c29-143">If you installed WCF after installing ASP.NET, you may need to run "%WINDIR%\ Microsoft.Net\Framework\v3.0\Windows Communication Foundation\servicemodelreg.exe " -r -x to give the ASPNET account permission to publish WMI objects.</span></span>  
  
5.  <span data-ttu-id="99c29-144">コマンド `cscript EnumerateServices.js` または `cscript EnumerateCustomObjects.js` を使用して、WMI を通じて示されるサンプルのデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="99c29-144">View data from the sample surfaced through WMI by using the commands: `cscript EnumerateServices.js` or `cscript EnumerateCustomObjects.js`.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="99c29-145">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="99c29-145">The samples may already be installed on your computer.</span></span> <span data-ttu-id="99c29-146">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="99c29-146">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="99c29-147">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="99c29-147">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="99c29-148">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="99c29-148">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\WMIProvider`  
  
## <a name="see-also"></a><span data-ttu-id="99c29-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="99c29-149">See Also</span></span>  
 [<span data-ttu-id="99c29-150">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="99c29-150">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
