---
title: 構成を使用しない AJAX サービス
ms.date: 03/30/2017
ms.assetid: e6db7acd-5679-45d4-b98a-8449c6873838
ms.openlocfilehash: 53a0de88d08fbc12cb8861042a50da6503fa5def
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-without-configuration"></a><span data-ttu-id="8ac02-102">構成を使用しない AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="8ac02-102">AJAX Service Without Configuration</span></span>
<span data-ttu-id="8ac02-103">このサンプルは、Windows Communication Foundation (WCF) を使用して構成を使用せずに、基本的な ASP.NET Asynchronous JavaScript and XML (AJAX) サービス (Web ブラウザー クライアントから JavaScript コードを使用してアクセスできるサービス) を作成する方法を示します。設定。</span><span class="sxs-lookup"><span data-stu-id="8ac02-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create a basic ASP.NET Asynchronous JavaScript and XML (AJAX) service (a service that you can access by using JavaScript code from a Web browser client) without using any configuration settings.</span></span> <span data-ttu-id="8ac02-104">このサービスは .svc ファイルの特殊な構文を使用して AJAX エンドポイントを自動的に有効にします。</span><span class="sxs-lookup"><span data-stu-id="8ac02-104">The service uses special syntax in the .svc file to automatically enable an AJAX endpoint.</span></span>  
  
 <span data-ttu-id="8ac02-105">WCF での AJAX サポートがを介して ASP.NET AJAX と共に使用できるように最適化、`ScriptManager`コントロール。</span><span class="sxs-lookup"><span data-stu-id="8ac02-105">AJAX support in WCF is optimized for use with ASP.NET AJAX through the `ScriptManager` control.</span></span> <span data-ttu-id="8ac02-106">WCF を ASP.NET AJAX と共に使用しての例は、次を参照してください。、 [Ajax サンプル](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。</span><span class="sxs-lookup"><span data-stu-id="8ac02-106">For an example of using WCF with ASP.NET AJAX, see the [Ajax Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac02-107">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8ac02-107">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8ac02-108">このサンプルは、HTTP POST を使用した AJAX サービスに基づいています。</span><span class="sxs-lookup"><span data-stu-id="8ac02-108">This sample builds upon the AJAX Service Using HTTP POST.</span></span> <span data-ttu-id="8ac02-109">」の説明に従って、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルについては、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>サービスをホストするために使用します。</span><span class="sxs-lookup"><span data-stu-id="8ac02-109">As described in the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample, <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> is used to host the service.</span></span>  

```svc
<%ServiceHost  
    language=c#  
    Debug="true"  
    Service="Microsoft.Ajax.Samples.CalculatorService  
    Factory="System.ServiceModel.Activation.WebScriptServiceHostFactory"  
%>  
```

 <span data-ttu-id="8ac02-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> は、<xref:System.ServiceModel.Description.WebScriptEndpoint> をサービスに自動的に追加します。</span><span class="sxs-lookup"><span data-stu-id="8ac02-110"><xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> automatically adds a <xref:System.ServiceModel.Description.WebScriptEndpoint> to the service.</span></span> <span data-ttu-id="8ac02-111">エンドポイントに対する構成変更が不要な場合、`<system.ServiceModel>` セクションはサービスの Web.config ファイルから完全に削除できます。</span><span class="sxs-lookup"><span data-stu-id="8ac02-111">If no configuration changes need to be made to the endpoint, the `<system.ServiceModel>` section can be completely removed from the Web.config file for the service.</span></span> <span data-ttu-id="8ac02-112">Web.config ファイルには、ConfigFreeClientPage.aspx で使用される ASP.NET 設定がいくつか含まれます。</span><span class="sxs-lookup"><span data-stu-id="8ac02-112">The Web.config file contains some ASP.NET settings, which are used by ConfigFreeClientPage.aspx.</span></span> <span data-ttu-id="8ac02-113">そうでない場合は、Web.config ファイル全体を削除できます。</span><span class="sxs-lookup"><span data-stu-id="8ac02-113">If that were not the case, the entire Web.config file could be removed.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8ac02-114">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8ac02-114">The samples may already be installed on your computer.</span></span> <span data-ttu-id="8ac02-115">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8ac02-115">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8ac02-116">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="8ac02-116">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8ac02-117">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8ac02-117">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ConfigFreeAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8ac02-118">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="8ac02-118">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8ac02-119">セットアップ手順を実行することを確認してください。 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ac02-119">Ensure that you perform the setup instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8ac02-120">ソリューションをビルドします ConfigFreeAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8ac02-120">Build the solution ConfigFreeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8ac02-121">移動http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx(開かないで ConfigFreeClientPage.aspx プロジェクト ディレクトリ内からブラウザーで)。</span><span class="sxs-lookup"><span data-stu-id="8ac02-121">Navigate to http://localhost/ServiceModelSamples/ConfigFreeClientPage.aspx (do not open ConfigFreeClientPage.aspx in the browser from within the project directory).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8ac02-122">このサンプルを実行する場合、IIS の ServiceModelSamples フォルダーで匿名認証と Windows 認証が同時に有効になっていないことを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8ac02-122">When running this sample, please ensure that Anonymous Authentication and Windows Authentication are not enabled simultaneously for the ServiceModelSamples folder in IIS.</span></span> <span data-ttu-id="8ac02-123">有効になっている場合は、Windows 認証を無効にしてください。</span><span class="sxs-lookup"><span data-stu-id="8ac02-123">If that is the case, please disable Windows Authentication.</span></span> <span data-ttu-id="8ac02-124">サンプルの実行が終了したら、Windows 認証を有効にし、"iisreset" を実行します。</span><span class="sxs-lookup"><span data-stu-id="8ac02-124">Once you have run the sample, enable Windows Authentication and run "iisreset".</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ac02-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="8ac02-125">See Also</span></span>  
 [<span data-ttu-id="8ac02-126">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="8ac02-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
