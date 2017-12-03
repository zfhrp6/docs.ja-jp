---
title: "複合型を使用した AJAX サービスのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d071bf182fb231b08f397db163059fda730fca21
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="9bbf8-102">複合型を使用した AJAX サービスのサンプル</span><span class="sxs-lookup"><span data-stu-id="9bbf8-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="9bbf8-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、複合型のインスタンスを作成し、そのインスタンスをサービスとクライアント間で JSON (JavaScript Object Notation) として送信する ASP.NET AJAX (Asynchronous JavaScript and XML) サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="9bbf8-104">AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="9bbf8-105">このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="9bbf8-106">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] での AJAX サポートは、<xref:System.Web.UI.ScriptManager> コントロールを介して ASP.NET AJAX と共に使用できるように最適化されています。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-106">AJAX support in [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="9bbf8-107">使用する例については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET AJAX を参照してください。、 [AJAX サンプル](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-107">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bbf8-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9bbf8-109">次に示すサンプルのサービスは、AJAX 固有のコードを持たない [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-109">The service in the following sample is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with no AJAX-specific code.</span></span> <span data-ttu-id="9bbf8-110"><xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 ("POST") が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="9bbf8-111">サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="9bbf8-112">複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  
  
```  
[DataContract]  
    public class MathResult  
    {  
        [DataMember]  
        public double sum;  
        [DataMember]  
        public double difference;  
        [DataMember]  
        public double product;  
        [DataMember]  
        public double quotient;  
    }  
```  
  
 <span data-ttu-id="9bbf8-113">基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="9bbf8-114">クライアント Web ページ ComplexTypeClientPage.aspx には、ユーザーがクリックしたときに、サービスを呼び出す ASP.NET および JavaScript のコードが含まれています、**計算を実行する** ページでボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="9bbf8-115">サービスを呼び出すコードが JSON 本文を構築し、送信のような HTTP POST を使用して、 [HTTP POST を使用して AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="9bbf8-116">サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー (`sum`、`difference`、`product`、および `quotient`) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  
  
```  
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9bbf8-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="9bbf8-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9bbf8-118">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9bbf8-119">ソリューションをビルドします ComplexTypeAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9bbf8-120">http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx に移動します (プロジェクト ディレクトリからブラウザーで ComplexTypeClientPage.aspx を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9bbf8-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9bbf8-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9bbf8-123">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9bbf8-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9bbf8-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="9bbf8-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bbf8-125">See Also</span></span>  
 [<span data-ttu-id="9bbf8-126">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="9bbf8-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
