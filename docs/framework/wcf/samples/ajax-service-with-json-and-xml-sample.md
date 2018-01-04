---
title: "JSON および XML 形式の AJAX サービスのサンプル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8ea5860d-0c42-4ae9-941a-e07efdd8e29c
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 665e05907f837887a7dd0375e540b6e9167a820e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="ajax-service-with-json-and-xml-sample"></a><span data-ttu-id="af497-102">JSON および XML 形式の AJAX サービスのサンプル</span><span class="sxs-lookup"><span data-stu-id="af497-102">AJAX Service with JSON and XML Sample</span></span>
<span data-ttu-id="af497-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] を使用して、JSON (JavaScript Object Notation) または XML データのいずれかを返す AJAX (Asynchronous JavaScript and XML) サービスを作成する方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="af497-103">This sample demonstrates how to use [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] to create an Asynchronous JavaScript and XML (AJAX) service that returns either JavaScript Object Notation (JSON) or XML data.</span></span> <span data-ttu-id="af497-104">AJAX サービスには、Web ブラウザー クライアントから JavaScript コードを使用してアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="af497-104">You can access an AJAX service by using JavaScript code from a Web browser client.</span></span> <span data-ttu-id="af497-105">このサンプルでビルド、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルです。</span><span class="sxs-lookup"><span data-stu-id="af497-105">This sample builds on the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample.</span></span>  
  
 <span data-ttu-id="af497-106">他の AJAX サンプルとは異なり、このサンプルでは ASP.NET AJAX および <xref:System.Web.UI.ScriptManager> コントロールを使用しません。</span><span class="sxs-lookup"><span data-stu-id="af497-106">Unlike the other AJAX samples, this sample does not use ASP.NET AJAX and the <xref:System.Web.UI.ScriptManager> control.</span></span> <span data-ttu-id="af497-107">追加の構成を行うと、JavaScript を使用して HTML ページから [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX サービスにアクセスできます。このシナリオを次に示します。</span><span class="sxs-lookup"><span data-stu-id="af497-107">With some additional configuration, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] AJAX services can be accessed from any HTML page through JavaScript, and this scenario is shown here.</span></span> <span data-ttu-id="af497-108">使用する例については[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ASP.NET AJAX を参照してください。 [AJAX サンプル](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e)です。</span><span class="sxs-lookup"><span data-stu-id="af497-108">For an example of using [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] with ASP.NET AJAX, see [AJAX Samples](http://msdn.microsoft.com/en-us/f3fa45b3-44d5-4926-8cc4-a13c30a3bf3e).</span></span>  
  
 <span data-ttu-id="af497-109">このサンプルでは、JSON と XML 間で操作の応答のタイプを切り替える方法を示します。</span><span class="sxs-lookup"><span data-stu-id="af497-109">This sample shows how to switch the response type of an operation between JSON and XML.</span></span> <span data-ttu-id="af497-110">この機能は、サービスが ASP.NET AJAX または HTML/JavaScript クライアント ページでアクセスできるように構成されているかどうかにかかわらず使用できます。</span><span class="sxs-lookup"><span data-stu-id="af497-110">This functionality is available regardless of whether the service is configured to be accessed by ASP.NET AJAX or by an HTML/JavaScript client page.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="af497-111">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="af497-111">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="af497-112">ASP.NET AJAX 以外のクライアントを使用するには、.svc ファイルで <xref:System.ServiceModel.Activation.WebServiceHostFactory> (<xref:System.ServiceModel.Activation.WebScriptServiceHostFactory> ではありません) を使用します。</span><span class="sxs-lookup"><span data-stu-id="af497-112">To enable the use of non-ASP.NET AJAX clients, use <xref:System.ServiceModel.Activation.WebServiceHostFactory> (not <xref:System.ServiceModel.Activation.WebScriptServiceHostFactory>) in the .svc file.</span></span> <span data-ttu-id="af497-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> によって、<xref:System.ServiceModel.Description.WebHttpEndpoint> 標準エンドポイントがサービスに追加されます。</span><span class="sxs-lookup"><span data-stu-id="af497-113"><xref:System.ServiceModel.Activation.WebServiceHostFactory> adds a <xref:System.ServiceModel.Description.WebHttpEndpoint> standard endpoint to the service.</span></span> <span data-ttu-id="af497-114">エンドポイントは .svc ファイルに相対する空のアドレス位置に作成されます。つまり、サービスのアドレスは、操作名以外の追加のサフィックスのない http://localhost/ServiceModelSamples/service.svc になります。</span><span class="sxs-lookup"><span data-stu-id="af497-114">The endpoint is configured at an empty address relative to the .svc file; this means that the address of the service is http://localhost/ServiceModelSamples/service.svc, with no additional suffixes other than the operation name.</span></span>  
  
```html  
<%@ServiceHost language="c#" Debug="true" Service="Microsoft.Samples.XmlAjaxService.CalculatorService" Factory="System.ServiceModel.Activation.WebServiceHostFactory" %>  
```  
  
 <span data-ttu-id="af497-115">Web.config 内の次のセクションを使用して、エンドポイントに対する構成変更を追加できます。</span><span class="sxs-lookup"><span data-stu-id="af497-115">The following section in Web.config can be used to make additional configuration changes to the endpoint.</span></span> <span data-ttu-id="af497-116">追加の変更が不要な場合は、このセクションを削除できます。</span><span class="sxs-lookup"><span data-stu-id="af497-116">It can be removed if no extra changes are needed.</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>  
    <webHttpEndpoint>  
      <!-- Use this element to configure the endpoint -->  
      <standardEndpoint name="" />  
    </webHttpEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="af497-117">既定のデータ形式<xref:System.ServiceModel.Description.WebHttpEndpoint>の既定のデータ形式の中には、XML、 <xref:System.ServiceModel.Description.WebScriptEndpoint> JSON がします。</span><span class="sxs-lookup"><span data-stu-id="af497-117">The default data format for <xref:System.ServiceModel.Description.WebHttpEndpoint> is XML, while the default data format for <xref:System.ServiceModel.Description.WebScriptEndpoint> is JSON.</span></span> <span data-ttu-id="af497-118">詳細については、次を参照してください。 [ASP.NET を使用せずに作成する WCF AJAX サービス](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md)です。</span><span class="sxs-lookup"><span data-stu-id="af497-118">For more information, see [Creating WCF AJAX Services without ASP.NET](../../../../docs/framework/wcf/feature-details/creating-wcf-ajax-services-without-aspnet.md).</span></span>  
  
 <span data-ttu-id="af497-119">次に示すサンプル内のサービスは、2 つの操作が設定された標準の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスです。</span><span class="sxs-lookup"><span data-stu-id="af497-119">The service in the following sample is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service with two operations.</span></span> <span data-ttu-id="af497-120">どちらの操作でも <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> または <xref:System.ServiceModel.Web.WebGetAttribute> 属性に <xref:System.ServiceModel.Web.WebInvokeAttribute> の本文スタイルが必要です。この本文スタイルは、`webHttp` 動作に固有で、JSON/XML データ形式の切り替えに影響しません。</span><span class="sxs-lookup"><span data-stu-id="af497-120">Both operations require the <xref:System.ServiceModel.Web.WebMessageBodyStyle.Wrapped> body style on the <xref:System.ServiceModel.Web.WebGetAttribute> or <xref:System.ServiceModel.Web.WebInvokeAttribute> attributes, which is specific to the `webHttp` behavior and has no bearing on the JSON/XML data format switch.</span></span>  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Xml, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathXml(double n1, double n2);  
```  
  
 <span data-ttu-id="af497-121">既定では XML として、操作の応答形式を指定の設定、 [ \<webHttp >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md)動作します。</span><span class="sxs-lookup"><span data-stu-id="af497-121">The response format for the operation is specified as XML, which is the default setting for the [\<webHttp>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttp.md) behavior.</span></span> <span data-ttu-id="af497-122">ただし、応答形式を明示的に指定することをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="af497-122">However, it is good practice explicitly specify the response format.</span></span>  
  
 <span data-ttu-id="af497-123">その他の操作では `WebInvokeAttribute` 属性を使用し、応答に XML ではなく JSON を明示的に指定します。</span><span class="sxs-lookup"><span data-stu-id="af497-123">The other operation uses the `WebInvokeAttribute` attribute and explicitly specifies JSON instead of XML for the response.</span></span>  
  
```  
[OperationContract]  
[WebInvoke(ResponseFormat = WebMessageFormat.Json, BodyStyle = WebMessageBodyStyle.Wrapped)]  
MathResult DoMathJson(double n1, double n2);  
```  
  
 <span data-ttu-id="af497-124">どちらの場合でも、操作により、標準の `MathResult` データ コントラクト型である複合型 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] が返されます。</span><span class="sxs-lookup"><span data-stu-id="af497-124">Note that in both cases the operations return a complex type, `MathResult`, which is a standard [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] data contract type.</span></span>  
  
 <span data-ttu-id="af497-125">クライアント Web ページ XmlAjaxClientPage.htm には、ユーザーがクリックしたときに、上記の 2 つの操作のいずれかを呼び出す JavaScript コードが含まれています、**計算 (return JSON) を実行する**または**calculation (return XML) を実行します。**ページのボタンです。</span><span class="sxs-lookup"><span data-stu-id="af497-125">The client Web page XmlAjaxClientPage.htm contains JavaScript code that invokes one of the preceding two operations when the user clicks the **Perform calculation (return JSON)** or **Perform calculation (return XML)** buttons on the page.</span></span> <span data-ttu-id="af497-126">サービスを呼び出すコードによって JSON 本文が作成され、HTTP POST を使用して送信されます。</span><span class="sxs-lookup"><span data-stu-id="af497-126">The code to invoke the service constructs a JSON body and sends it using HTTP POST.</span></span> <span data-ttu-id="af497-127">要求を手動で作成、JavaScript とは異なり、[基本的な AJAX サービス](../../../../docs/framework/wcf/samples/basic-ajax-service.md)サンプルと ASP.NET AJAX を使用して、他のサンプルです。</span><span class="sxs-lookup"><span data-stu-id="af497-127">The request is created manually in JavaScript, unlike the [Basic AJAX Service](../../../../docs/framework/wcf/samples/basic-ajax-service.md) sample and the other samples using ASP.NET AJAX.</span></span>  
  
```  
// Create HTTP request  
var xmlHttp;  
// Request instantiation code omitted…  
// Result handler code omitted…  
  
// Build the operation URL  
var url = "service.svc/ajaxEndpoint/";  
url = url + operation;  
  
// Build the body of the JSON message  
var body = '{"n1":';  
body = body + document.getElementById("num1").value + ',"n2":';  
body = body + document.getElementById("num2").value + '}';  
  
// Send the HTTP request  
xmlHttp.open("POST", url, true);  
xmlHttp.setRequestHeader("Content-type", "application/json");  
xmlHttp.send(body);  
```  
  
 <span data-ttu-id="af497-128">サービスが応答すると、応答はこれ以上の処理を行わずにページ上のテキスト ボックスに表示されます。</span><span class="sxs-lookup"><span data-stu-id="af497-128">When the service responds, the response is displayed without any further processing in a textbox on the page.</span></span> <span data-ttu-id="af497-129">これは、使用される XML および JSON データ形式を直接確認できるように、デモンストレーションの目的で実装されています。</span><span class="sxs-lookup"><span data-stu-id="af497-129">This is implemented for demonstration purposes to allow you to directly observe the XML and JSON data formats used.</span></span>  
  
```  
// Create result handler   
xmlHttp.onreadystatechange=function(){  
     if(xmlHttp.readyState == 4){  
          document.getElementById("result").value = xmlHttp.responseText;  
     }  
}  
```  
  
> [!IMPORTANT]
>  <span data-ttu-id="af497-130">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="af497-130">The samples may already be installed on your machine.</span></span> <span data-ttu-id="af497-131">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="af497-131">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="af497-132">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="af497-132">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="af497-133">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="af497-133">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\XmlAjaxService`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="af497-134">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="af497-134">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="af497-135">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="af497-135">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="af497-136">ソリューションをビルドします XmlAjaxService.sln」の説明に従って[Windows Communication Foundation サンプルのビルド](../../../../docs/framework/wcf/samples/building-the-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="af497-136">Build the solution XmlAjaxService.sln as described in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="af497-137">http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm に移動します (プロジェクト ディレクトリからブラウザで XmlAjaxClientPage.htm を開かないでください)。</span><span class="sxs-lookup"><span data-stu-id="af497-137">Navigate to http://localhost/ServiceModelSamples/XmlAjaxClientPage.htm (do not open XmlAjaxClientPage.htm in the browser from the project directory).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="af497-138">参照</span><span class="sxs-lookup"><span data-stu-id="af497-138">See Also</span></span>  
 [<span data-ttu-id="af497-139">HTTP POST を使用する AJAX サービス</span><span class="sxs-lookup"><span data-stu-id="af497-139">AJAX Service Using HTTP POST</span></span>](../../../../docs/framework/wcf/samples/ajax-service-using-http-post.md)
