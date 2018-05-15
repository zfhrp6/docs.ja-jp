---
title: 複合型を使用した AJAX サービスのサンプル
ms.date: 03/30/2017
ms.assetid: 88242b99-4811-4cbe-8201-52ddf48fb174
ms.openlocfilehash: c284fbef36ee7f6dda725ba9a3db9b98fb1549ed
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="ajax-service-using-complex-types-sample"></a><span data-ttu-id="9bba8-102">複合型を使用した AJAX サービスのサンプル</span><span class="sxs-lookup"><span data-stu-id="9bba8-102">AJAX Service Using Complex Types Sample</span></span>
<span data-ttu-id="9bba8-103">このサンプルでは、Windows Communication Foundation (WCF) を使用して、複合型のインスタンスを作成し、サービスとクライアントの JavaScript Object Notation (JSON) との間で送信する ASP.NET Asynchronous JavaScript and XML (AJAX) サービスを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9bba8-103">This sample demonstrates how to use Windows Communication Foundation (WCF) to create an ASP.NET Asynchronous JavaScript and XML (AJAX) service that creates instances of complex types and sends them between service and client as JavaScript Object Notation (JSON).</span></span> <span data-ttu-id="9bba8-104">AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9bba8-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="9bba8-105">このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9bba8-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="9bba8-106">WCF での AJAX サポートがを介して ASP.NET AJAX と共に使用できるように最適化、<xref:System.Web.UI.ScriptManager>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9bba8-106">AJAX support in WCF is optimized for use with ASP.NET AJAX through the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="9bba8-107">WCF を ASP.NET AJAX と共に使用しての例は、次を参照してください。、 [AJAX サンプル](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。</span><span class="sxs-lookup"><span data-stu-id="9bba8-107">For an example of using WCF with ASP.NET AJAX, see the [AJAX Samples](http://msdn.microsoft.com/library/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9bba8-108">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9bba8-108">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="9bba8-109">次のサンプルのサービスには、AJAX 固有のコードを持たない WCF サービスです。</span><span class="sxs-lookup"><span data-stu-id="9bba8-109">The service in the following sample is a WCF service with no AJAX-specific code.</span></span> <span data-ttu-id="9bba8-110"><xref:System.ServiceModel.Web.WebGetAttribute> 属性は適用されないため、既定の HTTP 動詞 ("POST") が使用されます。</span><span class="sxs-lookup"><span data-stu-id="9bba8-110">Because the <xref:System.ServiceModel.Web.WebGetAttribute> attribute is not applied, the default HTTP verb ("POST") is used.</span></span> <span data-ttu-id="9bba8-111">サービスには 1 つの `DoMath` 操作があります。この操作は、`MathResult` という名前の複合型を返します。</span><span class="sxs-lookup"><span data-stu-id="9bba8-111">The service has one operation, `DoMath`, which returns a complex type named `MathResult`.</span></span> <span data-ttu-id="9bba8-112">複合型は標準のデータ コントラクト型で、AJAX 固有のコードも含まれていません。</span><span class="sxs-lookup"><span data-stu-id="9bba8-112">The complex type is a standard data contract type, which also contains no AJAX-specific code.</span></span>  

```csharp
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

 <span data-ttu-id="9bba8-113">基本的な AJAX サービスのサンプルの場合と同様に、<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> を使用してサービスに AJAX エンドポイントを作成します。</span><span class="sxs-lookup"><span data-stu-id="9bba8-113">Create an AJAX endpoint on the service by using the <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>, just as in the Basic AJAX Service sample.</span></span>  
  
 <span data-ttu-id="9bba8-114">クライアント Web ページ ComplexTypeClientPage.aspx には、ユーザーがクリックしたときに、サービスを呼び出す ASP.NET および JavaScript のコードが含まれています、**計算を実行する** ページでボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9bba8-114">The client Web page ComplexTypeClientPage.aspx contains ASP.NET and JavaScript code to invoke the service when the user clicks the **Perform calculation** button on the page.</span></span> <span data-ttu-id="9bba8-115">サービスを呼び出すコードが JSON 本文を構築し、送信のような HTTP POST を使用して、 [HTTP POST を使用して AJAX サービス](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9bba8-115">The code to invoke the service constructs a JSON body and sends it using HTTP POST, similar to the [AJAX Service Using HTTP POST](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md) sample.</span></span>  
  
 <span data-ttu-id="9bba8-116">サービス呼び出しに成功したら、生成された JavaScript オブジェクトのそれぞれのデータ メンバー (`sum`、`difference`、`product`、および `quotient`) にアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="9bba8-116">After the service call succeeds, you can access the individual data members (`sum`, `difference`, `product` and `quotient`) on the resulting JavaScript object.</span></span>  

```javascript
function onSuccess(mathResult){  
     document.getElementById("sum").value = mathResult.sum;  
     document.getElementById("difference").value = mathResult.difference;  
     document.getElementById("product").value = mathResult.product;  
     document.getElementById("quotient").value = mathResult.quotient;  
}  
```

### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="9bba8-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="9bba8-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="9bba8-118">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bba8-118">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="9bba8-119">ソリューションをビルドします ComplexTypeAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="9bba8-119">Build the solution ComplexTypeAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="9bba8-120">移動http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx(開かないで ComplexTypeClientPage.aspx プロジェクト ディレクトリからブラウザーで)。</span><span class="sxs-lookup"><span data-stu-id="9bba8-120">Navigate to http://localhost/ServiceModelSamples/ComplexTypeClientPage.aspx (do not open ComplexTypeClientPage.aspx in the browser from the project directory).</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="9bba8-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="9bba8-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="9bba8-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="9bba8-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="9bba8-123">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="9bba8-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="9bba8-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="9bba8-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Ajax\ComplexTypeAjaxService`  
  
## <a name="see-also"></a><span data-ttu-id="9bba8-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="9bba8-125">See Also</span></span>  
 [<span data-ttu-id="9bba8-126">基本的な AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="9bba8-126">Basic AJAX Service</span></span>](../../../../docs/framework/wcf/samples/basic-ajax-service.md)
