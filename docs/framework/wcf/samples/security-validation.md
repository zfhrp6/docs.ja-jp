---
title: "セキュリティ検証"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 48dcd496-0c4f-48ce-8b9b-0e25b77ffa58
caps.latest.revision: "35"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 86a10a4117a5bbeb48e9d1d15b1ce8da9d7c7751
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="security-validation"></a><span data-ttu-id="a27b6-102">セキュリティ検証</span><span class="sxs-lookup"><span data-stu-id="a27b6-102">Security Validation</span></span>
<span data-ttu-id="a27b6-103">このサンプルでは、サービスが特定の条件を満たしていることを確認するカスタム動作を使用して、コンピューター上のサービスを検証する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a27b6-103">This sample demonstrates how to use a custom behavior to validate services on a computer to ensure they meet specific criteria.</span></span> <span data-ttu-id="a27b6-104">このサンプルでは、サービス上の各エンドポイントをスキャンし、セキュリティ保護されたバインド要素が含まれているかどうかを確認するカスタム動作を使用して、サービスを検証します。</span><span class="sxs-lookup"><span data-stu-id="a27b6-104">In this sample, services are validated by the custom behavior by scanning through each endpoint on the service and checking to see whether they contain secure binding elements.</span></span> <span data-ttu-id="a27b6-105">このサンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)です。</span><span class="sxs-lookup"><span data-stu-id="a27b6-105">This sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a27b6-106">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="a27b6-106">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
## <a name="endpoint-validation-custom-behavior"></a><span data-ttu-id="a27b6-107">エンドポイント検証のカスタム動作</span><span class="sxs-lookup"><span data-stu-id="a27b6-107">Endpoint Validation Custom Behavior</span></span>  
 <span data-ttu-id="a27b6-108">`Validate` インターフェイスに含まれる <xref:System.ServiceModel.Description.IServiceBehavior> メソッドにユーザー コードを追加することによって、サービスまたはエンドポイントにカスタム動作を与え、ユーザー定義のアクションを実行することができます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-108">By adding user code to the `Validate` method contained in the <xref:System.ServiceModel.Description.IServiceBehavior> interface, custom behavior can be given to a service or endpoint to perform user-defined actions.</span></span> <span data-ttu-id="a27b6-109">次のコードを使用すると、サービスに含まれる各エンドポイントをループし、バインディング コレクションからセキュリティ保護されたバインディングが検索されます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-109">The following code is used to loop through each endpoint contained in a service, which searches through their binding collections for secure bindings.</span></span>  
  
```  
public void Validate(ServiceDescription serviceDescription,   
                                       ServiceHostBase serviceHostBase)  
{  
    // Loop through each endpoint individually gathering their    
       binding elements.  
    foreach (ServiceEndpoint endpoint in serviceDescription.Endpoints)  
    {  
        secureElementFound = false;  
  
        // Retrieve the endpoint's binding element collection.  
        BindingElementCollection bindingElements =   
            endpoint.Binding.CreateBindingElements();  
  
        // Look to see if the binding elements collection contains any   
        // secure binding elements. Transport, Asymmetric, and Symmetric      
        // binding elements are all derived from SecurityBindingElement.  
        if ((bindingElements.Find<SecurityBindingElement>() != null) || (bindingElements.Find<HttpsTransportBindingElement>() != null) || (bindingElements.Find<WindowsStreamSecurityBindingElement>() != null) || (bindingElements.Find<SslStreamSecurityBindingElement>() != null))  
        {  
            secureElementFound = true;  
        }  
  
    // Send a message to the system event viewer when an endpoint is deemed insecure.  
    if (!secureElementFound)  
        throw new Exception(System.DateTime.Now.ToString() + ": The endpoint \"" + endpoint.Name + "\" has no secure bindings.");  
    }  
}  
```  
  
 <span data-ttu-id="a27b6-110">次のコードを Web.config ファイルに追加すると、サービスで識別される `serviceValidate` 動作の拡張が追加されます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-110">Adding the following code to Web.config file adds the `serviceValidate` behavior extension for the service to recognize.</span></span>  
  
```xml  
<system.serviceModel>  
    <extensions>  
        <behaviorExtensions>  
            <add name="endpointValidate" type="Microsoft.ServiceModel.Samples.EndpointValidateElement, endpointValidate, Version=0.0.0.0, Culture=neutral, PublicKeyToken=null" />  
        </behaviorExtensions>  
    </extensions>  
...  
```  
  
 <span data-ttu-id="a27b6-111">動作の拡張がサービスに追加されると、`endpointValidate` の動作を Web.config ファイルの動作リストに追加でき、さらにはサービスに追加できるようになります。</span><span class="sxs-lookup"><span data-stu-id="a27b6-111">Once the behavior extension is added to the service, it is now possible to add the `endpointValidate` behavior to the list of behaviors in the Web.config file and thus, to the service.</span></span>  
  
```xml  
<behaviors>  
    <serviceBehaviors>  
        <behavior name="CalcServiceSEB1">  
            <serviceMetadata httpGetEnabled="true" />  
            <endpointValidate />  
        </behavior>  
    </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="a27b6-112">動作とその拡張が Web.config ファイルに追加されると、動作は個別のサービスに適用されます。一方で Machine.config ファイルに追加された場合は、動作はコンピューター上でアクティブなすべてのサービスに適用されます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-112">Behaviors and their extensions that are added to the Web.config file apply behavior to individual services, while when added to the Machine.config file apply behavior to every service active on the computer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a27b6-113">動作をすべてのサービスに追加する場合、Machine.config ファイルの変更を行う前に、このファイルのバックアップを推奨するメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-113">When adding behavior to all services, it is suggested to backup the Machine.config file before making any change.</span></span>  
  
 <span data-ttu-id="a27b6-114">ここで、このサンプルの client\bin ディレクトリに用意されたクライアントを実行します。</span><span class="sxs-lookup"><span data-stu-id="a27b6-114">Now run the client provided in the client\bin directory of this sample.</span></span> <span data-ttu-id="a27b6-115">例外が発生して、"要求されたサービス、'http://localhost/servicemodelsamples/service.svc' を起動できませんでした。" というメッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-115">An exception has occurs with the following message: "The requested service, 'http://localhost/servicemodelsamples/service.svc' could not be activated."</span></span> <span data-ttu-id="a27b6-116">これは予期される例外です。エンドポイント検証の動作により、エンドポイントがセキュリティで保護されていないと見なされ、サービスが開始されないためです。</span><span class="sxs-lookup"><span data-stu-id="a27b6-116">This is expected because an endpoint is considered insecure by the endpoint validating behavior and prevents the service from being started.</span></span> <span data-ttu-id="a27b6-117">さらにこの動作によって、エンドポイントがセキュリティ保護されていないという内部例外がスローされ、システム イベント ビューアで "WebHost" カテゴリの "System.ServiceModel 4.0.0.0" ソースの下にメッセージが書き込まれます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-117">The behavior also throws an internal exception that describes which endpoint is insecure and writes a message to the system Event Viewer under the "System.ServiceModel 4.0.0.0" source and the "WebHost" category.</span></span> <span data-ttu-id="a27b6-118">さらにこのサンプルでは、サービスのトレースを有効にできます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-118">It is also possible to turn on tracing on the service in this sample.</span></span> <span data-ttu-id="a27b6-119">これによって、サービス トレース ビューア ツールを使用してサービス トレースの結果を開き、エンドポイント検証の動作からスローされた例外を表示することができます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-119">This allows the user to view the exceptions thrown by endpoint validating behavior by opening the resulting service traces using the Service Trace Viewer tool.</span></span>  
  
#### <a name="to-view-failed-endpoint-validation-exception-messages-in-the-event-viewer"></a><span data-ttu-id="a27b6-120">エンドポイント検証エラーの例外メッセージをイベント ビューアーで表示するには</span><span class="sxs-lookup"><span data-stu-id="a27b6-120">To view failed endpoint validation exception messages in the Event Viewer</span></span>  
  
1.  <span data-ttu-id="a27b6-121">をクリックして、**開始**メニュー**を実行しています.**.</span><span class="sxs-lookup"><span data-stu-id="a27b6-121">Click the **Start** menu and select **Run…**.</span></span>  
  
2.  <span data-ttu-id="a27b6-122">型`eventvwr` をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="a27b6-122">Type `eventvwr` and click **OK**.</span></span>  
  
3.  <span data-ttu-id="a27b6-123">[イベント ビューアー] ウィンドウ**アプリケーション**です。</span><span class="sxs-lookup"><span data-stu-id="a27b6-123">In the Event Viewer window, click **Application**.</span></span>  
  
4.  <span data-ttu-id="a27b6-124">"WebHost"カテゴリの下で、最近追加された"System.ServiceModel 4.0.0.0"イベントをダブルクリックして、**アプリケーション**安全でないエンドポイントのメッセージを表示するウィンドウです。</span><span class="sxs-lookup"><span data-stu-id="a27b6-124">Double-click the recently added "System.ServiceModel 4.0.0.0" event under the "WebHost" category in the **Application** window to view insecure endpoint messages.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="a27b6-125">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="a27b6-125">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="a27b6-126">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a27b6-126">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="a27b6-127">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="a27b6-127">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="a27b6-128">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="a27b6-128">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a27b6-129">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a27b6-129">The samples may already be installed on your computer.</span></span> <span data-ttu-id="a27b6-130">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a27b6-130">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a27b6-131">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a27b6-131">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a27b6-132">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a27b6-132">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ServiceValidation`  
  
## <a name="see-also"></a><span data-ttu-id="a27b6-133">参照</span><span class="sxs-lookup"><span data-stu-id="a27b6-133">See Also</span></span>  
 [<span data-ttu-id="a27b6-134">AppFabric の監視のサンプル</span><span class="sxs-lookup"><span data-stu-id="a27b6-134">AppFabric Monitoring Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193959)
