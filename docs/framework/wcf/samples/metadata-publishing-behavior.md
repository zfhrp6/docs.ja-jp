---
title: メタデータ公開動作
ms.date: 03/30/2017
helpviewer_keywords:
- service behaviors, metadata publishing sample
- Metadata Publishing Behaviors Sample [Windows Communication Foundation]
ms.assetid: 78c13633-d026-4814-910e-1c801cffdac7
ms.openlocfilehash: 547ff9fcaca8b9af7a7559a11ef4c4a8b5996174
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33505522"
---
# <a name="metadata-publishing-behavior"></a><span data-ttu-id="c69a2-102">メタデータ公開動作</span><span class="sxs-lookup"><span data-stu-id="c69a2-102">Metadata Publishing Behavior</span></span>
<span data-ttu-id="c69a2-103">メタデータ公開動作のサンプルでは、サービスのメタデータ公開機能を制御する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c69a2-103">The Metadata Publishing Behavior sample demonstrates how to control the metadata publishing features of a service.</span></span> <span data-ttu-id="c69a2-104">機密性の高いサービス メタデータが誤って漏洩を防ぐためには、Windows Communication Foundation (WCF) サービスの既定の構成はメタデータの公開を無効にします。</span><span class="sxs-lookup"><span data-stu-id="c69a2-104">To prevent unintentional disclosure of potentially sensitive service metadata, the default configuration for Windows Communication Foundation (WCF) services disables metadata publishing.</span></span> <span data-ttu-id="c69a2-105">この動作は、既定の設定ではセキュリティで保護されますが、同時に、サービスの構成の中でメタデータ発行の動作が明示的に有効化されない限り、サービスの呼び出しに必要なクライアント コードをメタデータ インポート ツール (Svcutil.exe など) を使用して生成できないことも意味します。</span><span class="sxs-lookup"><span data-stu-id="c69a2-105">This behavior is secure by default, but also means that you cannot use a metadata import tool (such as Svcutil.exe) to generate the client code required to call the service unless the service’s metadata publishing behavior is explicitly enabled in configuration.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c69a2-106">このサンプルでは、わかりやすくするために、セキュリティで保護されていないメタデータ公開エンドポイントを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c69a2-106">For clarity, this sample demonstrates how to create an unsecured metadata publishing endpoint.</span></span> <span data-ttu-id="c69a2-107">このようなエンドポイントを利用するコンシューマーは、匿名で、認証を受けていない可能性もあります。したがって、エンドポイントを配置する前には注意を払い、サービスのメタデータをパブリックに開示することが適切であることを確認する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c69a2-107">Such endpoints are potentially available to anonymous unauthenticated consumers and care must be taken before deploying such endpoints to ensure that publicly disclosing a service’s metadata is appropriate.</span></span> <span data-ttu-id="c69a2-108">参照してください、[カスタム セキュリティで保護されたメタデータ エンドポイント](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)メタデータ エンドポイントをセキュリティで保護するサンプルのサンプルです。</span><span class="sxs-lookup"><span data-stu-id="c69a2-108">See the [Custom Secure Metadata Endpoint](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md) sample for a sample that secures a metadata endpoint.</span></span>  
  
 <span data-ttu-id="c69a2-109">サンプルがに基づいて、[作業の開始](../../../../docs/framework/wcf/samples/getting-started-sample.md)を実装する、`ICalculator`サービス コントラクト。</span><span class="sxs-lookup"><span data-stu-id="c69a2-109">The sample is based on the [Getting Started](../../../../docs/framework/wcf/samples/getting-started-sample.md), which implements the `ICalculator` service contract.</span></span> <span data-ttu-id="c69a2-110">この例では、クライアントはコンソール アプリケーション (.exe) であり、サービスはインターネット インフォメーション サービス (IIS) によってホストされます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-110">In this sample, the client is a console application (.exe) and the service is hosted by Internet Information Services (IIS).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c69a2-111">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="c69a2-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="c69a2-112">サービスでメタデータを公開するには、サービス上に <xref:System.ServiceModel.Description.ServiceMetadataBehavior> を構成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="c69a2-112">For a service to expose metadata, the <xref:System.ServiceModel.Description.ServiceMetadataBehavior> must be configured on the service.</span></span> <span data-ttu-id="c69a2-113">この動作が存在する場合は、エンドポイントを構成してメタデータを公開し、<xref:System.ServiceModel.Description.IMetadataExchange> コントラクトを WS-MetadataExchange (MEX) プロトコルの実装として公開できます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-113">When this behavior is present, you can publish metadata by configuring an endpoint to expose the <xref:System.ServiceModel.Description.IMetadataExchange> contract as an implementation of a WS-MetadataExchange (MEX) protocol.</span></span> <span data-ttu-id="c69a2-114">便宜上、このコントラクトには、構成名を略した "IMetadataExchange" という名前が付けられています。</span><span class="sxs-lookup"><span data-stu-id="c69a2-114">As a convenience, this contract has been given the abbreviated configuration name of "IMetadataExchange".</span></span> <span data-ttu-id="c69a2-115">このサンプルでは、`mexHttpBinding` を使用します。これは使いやすい標準バインディングで、セキュリティ モードが `wsHttpBinding` に設定されている `None` と同等です。</span><span class="sxs-lookup"><span data-stu-id="c69a2-115">This sample uses the `mexHttpBinding`, which is a convenience standard binding that is equivalent to the `wsHttpBinding` with the security mode set to `None`.</span></span> <span data-ttu-id="c69a2-116">相対アドレスの"mex"が使用されるエンドポイントには、どのに対して解決とサービスのベース アドレスのエンドポイント アドレスhttp://localhost/servicemodelsamples/service.svc/mexです。</span><span class="sxs-lookup"><span data-stu-id="c69a2-116">A relative address of "mex" is used in the endpoint, which when resolved against the services base address results in an endpoint address of http://localhost/servicemodelsamples/service.svc/mex.</span></span> <span data-ttu-id="c69a2-117">この動作の構成を次に示します。</span><span class="sxs-lookup"><span data-stu-id="c69a2-117">The following shows the behavior configuration:</span></span>  
  
```xml  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <!-- The serviceMetadata behavior publishes metadata through   
           the IMetadataExchange contract. When this behavior is   
           present, you can expose this contract through an endpoint   
           as shown below. Setting httpGetEnabled to true publishes   
           the service's WSDL at the <baseaddress>?wsdl, for example,  
           http://localhost/servicemodelsamples/service.svc?wsdl -->  
      <serviceMetadata httpGetEnabled="True"/>  
      <serviceDebug includeExceptionDetailInFaults="False" />  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
```  
  
 <span data-ttu-id="c69a2-118">MEX エンドポイントを次に示します。</span><span class="sxs-lookup"><span data-stu-id="c69a2-118">The following shows the MEX endpoint.</span></span>  
  
```xml  
<!-- the MEX endpoint is exposed at   
     http://localhost/servicemodelsamples/service.svc/mex   
     To expose the IMetadataExchange contract, you   
     must enable the serviceMetadata behavior as demonstrated                           
     previously. -->  
<endpoint address="mex"  
          binding="mexHttpBinding"  
          contract="IMetadataExchange" />  
```  
  
 <span data-ttu-id="c69a2-119">このサンプルでは、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> プロパティを `true` に設定します。これにより、HTTP GET を使用してサービスのメタデータも公開されます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-119">This sample sets the <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpGetEnabled%2A> property to `true`, which also exposes the service's metadata using HTTP GET.</span></span> <span data-ttu-id="c69a2-120">HTTP GET メタデータのエンドポイントを有効にするには、サービスに HTTP ベース アドレスが設定されている必要があります。</span><span class="sxs-lookup"><span data-stu-id="c69a2-120">To enable an HTTP GET metadata endpoint, the service must have an HTTP base address.</span></span> <span data-ttu-id="c69a2-121">クエリ文字列 `?wsdl` は、メタデータにアクセスするサービスのベース アドレスで使用されます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-121">The query string `?wsdl` is used on the base address of the service to access the metadata.</span></span> <span data-ttu-id="c69a2-122">たとえば、Web ブラウザーでサービスの WSDL を表示するとアドレスを使用する、http://localhost/servicemodelsamples/service.svc?wsdlです。</span><span class="sxs-lookup"><span data-stu-id="c69a2-122">For example, to see the WSDL for the service in a Web browser you would use the address http://localhost/servicemodelsamples/service.svc?wsdl.</span></span> <span data-ttu-id="c69a2-123">または、<xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> を `true` に設定してこの動作を使用することにより、HTTPS を通じてメタデータを公開することもできます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-123">Alternatively, you can use this behavior to expose metadata over HTTPS by setting <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> to `true`.</span></span> <span data-ttu-id="c69a2-124">これには、HTTPS ベース アドレスが必要です。</span><span class="sxs-lookup"><span data-stu-id="c69a2-124">This requires an HTTPS base address.</span></span>  
  
 <span data-ttu-id="c69a2-125">サービスの MEX エンドポイントの使用にアクセスする、 [ServiceModel メタデータ ユーティリティ ツール (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="c69a2-125">To access the service's MEX endpoint use the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
 `svcutil.exe /n:"http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples" http://localhost/servicemodelsamples/service.svc/mex /out:generatedClient.cs`  
  
 <span data-ttu-id="c69a2-126">これにより、サービスのメタデータに基づくクライアントが生成されます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-126">This generates a client based on the service's metadata.</span></span>  
  
 <span data-ttu-id="c69a2-127">HTTP GET を使用して、サービスのメタデータにアクセスするには、ブラウザーをポイントhttp://localhost/servicemodelsamples/service.svc?wsdlです。</span><span class="sxs-lookup"><span data-stu-id="c69a2-127">To access the service's metadata using HTTP GET, point your browser to http://localhost/servicemodelsamples/service.svc?wsdl.</span></span>  
  
 <span data-ttu-id="c69a2-128">この動作を削除してサービスを開こうとすると、例外が発生します。</span><span class="sxs-lookup"><span data-stu-id="c69a2-128">If you remove this behavior and try to open the service you get an exception.</span></span> <span data-ttu-id="c69a2-129">動作がない場合にこのエラーが発生するのは、`IMetadataExchange` コントラクトを使用して構成されたエンドポイントに実装が存在しないからです。</span><span class="sxs-lookup"><span data-stu-id="c69a2-129">This error occurs because without the behavior, the endpoint configured with the `IMetadataExchange` contract has no implementation.</span></span>  
  
 <span data-ttu-id="c69a2-130">`HttpGetEnabled` を `false` に設定すると、サービスのメタデータが表示される代わりに CalculatorService ヘルプ ページが表示されます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-130">If you set `HttpGetEnabled` to `false`, you see the CalculatorService help page instead of seeing the service's metadata.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="c69a2-131">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="c69a2-131">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="c69a2-132">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="c69a2-132">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="c69a2-133">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="c69a2-133">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="c69a2-134">1 つまたは複数コンピューター構成でサンプルを実行する手順についてで[Windows Communication Foundation サンプルの実行](../../../../docs/framework/wcf/samples/running-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="c69a2-134">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c69a2-135">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c69a2-135">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c69a2-136">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c69a2-136">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c69a2-137">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="c69a2-137">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c69a2-138">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c69a2-138">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Services\Behaviors\Metadata`  
  
## <a name="see-also"></a><span data-ttu-id="c69a2-139">関連項目</span><span class="sxs-lookup"><span data-stu-id="c69a2-139">See Also</span></span>
