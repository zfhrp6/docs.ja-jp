---
title: "構成を使用しない AJAX サービス"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 82d9bb27ef20aa4e425e232a23c785af3b7e6e5a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="89344-102">構成を使用しない AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="89344-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="89344-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、構成設定を使用せずに基本的な ASP.NET AJAX (Asynchronous JavaScript and XML) サービス (Web ブラウザー クライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="89344-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="89344-104">このサービスは .svc ファイルの特殊な構文を使用して AJAX エンドポイントを自動的に有効にします。</span><span class="sxs-lookup"><span data-stu-id="89344-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="89344-105">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートは、`ScriptManager` コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="89344-105">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="89344-106">使用する例については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET AJAX を参照してください。、 [Ajax サンプル](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。</span><span class="sxs-lookup"><span data-stu-id="89344-106">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89344-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="89344-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="89344-108">このサンプルは、HTTP POST を使用した AJAX サービスに基づいています。</span><span class="sxs-lookup"><span data-stu-id="89344-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="89344-109">」の説明に従って、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルについては、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>サービスをホストするために使用します。</span><span class="sxs-lookup"><span data-stu-id="89344-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  
  
```  
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```  
  
 <span data-ttu-id="89344-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> は、<xref:System.ServiceModel.Description.WebScriptEndpoint> をサービスに自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="89344-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="89344-111">構成の変更をエンドポイントに対して行う必要がない場合、\<システムです。ServiceModel > セクションは、サービスの Web.config ファイルから完全に削除することができます。</span><span class="sxs-lookup"><span data-stu-id="89344-111">If no configuration changes need to be made to the endpoint, the \<system.ServiceModel> section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="89344-112">Web.config ファイルには、ConfigFreeClientPage.aspx で使用される ASP.NET 設定がいくつか含まれます。</span><span class="sxs-lookup"><span data-stu-id="89344-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="89344-113">そうでない場合は、Web.config ファイル全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="89344-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="89344-114">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="89344-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="89344-115">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="89344-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="89344-116">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="89344-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="89344-117">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="89344-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="89344-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="89344-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="89344-119">セットアップ手順を実行することを確認してください。 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="89344-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="89344-120">ソリューションをビルドします ConfigFreeAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="89344-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="89344-121">http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx に移動します (プロジェクト ディレクトリからブラウザーで ConfigFreeClientPage.aspx を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="89344-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="89344-122">このサンプルを実行する場合、IIS の ServiceModelSamples フォルダーで匿名認証と Windows 認証が同時に有効になっていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="89344-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="89344-123">有効になっている場合は、Windows 認証を無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="89344-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="89344-124">サンプルの実行が終了したら、Windows 認証を有効にし、"iisreset" を実行します。</span><span class="sxs-lookup"><span data-stu-id="89344-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="89344-125">参照</span><span class="sxs-lookup"><span data-stu-id="89344-125">See Also</span></span>  
 [<span data-ttu-id="89344-126">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="89344-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
