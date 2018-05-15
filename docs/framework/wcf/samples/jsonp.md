---
title: JSONP
ms.date: 03/30/2017
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
ms.openlocfilehash: 9002597ef662c78b6519ab0c04700cddf7ee3714
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="jsonp"></a><span data-ttu-id="e961e-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="e961e-102">JSONP</span></span>
<span data-ttu-id="e961e-103">このサンプルでは、WCF REST サービスの JSONP (JSON with Padding) をサポートする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="e961e-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="e961e-104">JSONP とは、現在のドキュメントでスクリプト タグを生成してドメイン間スクリプトを呼び出す際に使用される変換です。</span><span class="sxs-lookup"><span data-stu-id="e961e-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="e961e-105">結果は、指定したコールバック関数で返されます。</span><span class="sxs-lookup"><span data-stu-id="e961e-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="e961e-106">JSONP は、`<script src="http://..." >` などのタグで任意のドメインからのスクリプトを評価でき、このようなタグによって取得されたスクリプトを既に他の関数が定義されている範囲で評価するという考えに基づいています。</span><span class="sxs-lookup"><span data-stu-id="e961e-106">JSONP is based on the idea that tags such as `<script src="http://..." >` can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="e961e-107">使用例</span><span class="sxs-lookup"><span data-stu-id="e961e-107">Demonstrates</span></span>  
 <span data-ttu-id="e961e-108">JSONP によるドメイン間スクリプト。</span><span class="sxs-lookup"><span data-stu-id="e961e-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="e961e-109">説明</span><span class="sxs-lookup"><span data-stu-id="e961e-109">Discussion</span></span>  
 <span data-ttu-id="e961e-110">このサンプルには、ブラウザーで表示された後にスクリプト ブロックを動的に追加する Web ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e961e-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="e961e-111">このスクリプト ブロックは、`GetCustomer` 操作を 1 つ持つ WCF REST サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e961e-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="e961e-112">WCF REST サービスは、コールバック関数名でラップされた顧客の名前とアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="e961e-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="e961e-113">WCF REST サービスが応答を返すと、顧客データを使用して Web ページ上のコールバック関数が呼び出され、このコールバック関数によって Web ページ上に顧客データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="e961e-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="e961e-114">スクリプト タグの挿入とコールバック関数の実行は、ASP.NET AJAX ScriptManager コントロールによって自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="e961e-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="e961e-115">次のコードに示すように、使用パターンはすべての ASP.NET AJAX プロキシと同じで、JSONP を有効にするための行が 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="e961e-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="e961e-116">Web ページでは、WCF REST サービスを呼び出すことができます。これは、WCF REST サービスが、<xref:System.ServiceModel.Description.WebScriptEndpoint> が `crossDomainScriptAccessEnabled` に設定された `true` を使用しているからです。</span><span class="sxs-lookup"><span data-stu-id="e961e-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="e961e-117">下にある Web.config ファイルでこれらの構成が終わったら、 \<system.serviceModel > 要素。</span><span class="sxs-lookup"><span data-stu-id="e961e-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
```xml  
<system.serviceModel>  
  <serviceHostingEnvironment aspNetCompatibilityEnabled="true"/>  
  <standardEndpoints>  
    <webScriptEndpoint>  
      <standardEndpoint name="" crossDomainScriptAccessEnabled="true"/>  
    </webScriptEndpoint>  
  </standardEndpoints>  
</system.serviceModel>  
```  
  
 <span data-ttu-id="e961e-118">ScriptManager はサービスとのやり取りを管理し、JSONP アクセスの手動実装の複雑さを隠蔽します。</span><span class="sxs-lookup"><span data-stu-id="e961e-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="e961e-119">ときに`crossDomainScriptAccessEnabled`に設定されている`true`操作の応答形式が JSON と、WCF インフラストラクチャがコールバック クエリ文字列パラメーターの要求の URI を検査し、コールバック クエリ文字列の値と JSON 応答をラップパラメーター。</span><span class="sxs-lookup"><span data-stu-id="e961e-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the WCF infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="e961e-120">このサンプルでは、Web ページは次の URI を使用して WCF REST サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="e961e-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="e961e-121">コールバック クエリ文字列パラメーターには `JsonPCallback` の値が含まれているため、WCF サービスは次の例に示す JSONP 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="e961e-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="e961e-122">JSONP 応答には、JSON として書式設定され、Web ページが要求したコールバック関数名でラップされた顧客データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e961e-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="e961e-123">ScriptManager は、ドメイン間要求を実現するスクリプト タグを使用してこのコールバックを実行し、ASP.NET AJAX プロキシの GetCustomer 操作に渡された onSuccess ハンドラーに結果を渡します。</span><span class="sxs-lookup"><span data-stu-id="e961e-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="e961e-124">サンプルを次の 2 つの ASP.NET web アプリケーションの構成: WCF サービスだけを含む 1 つともう 1 つにはサービスを呼び出す .aspx web ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="e961e-124">The sample consists of two ASP.NET web applications: one contains just a WCF service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="e961e-125">ソリューションの実行中、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] は 2 つの Web サイトを別々のポート上にホストします。これにより、サービスとクライアントが別々のドメインに存在する環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="e961e-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="e961e-126">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="e961e-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="e961e-127">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="e961e-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="e961e-128">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="e961e-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="e961e-129">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="e961e-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="e961e-130">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="e961e-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="e961e-131">JSONP サンプルのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="e961e-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="e961e-132">起動する f5 キーを押して`http://localhost:26648/JSONPClientPage.aspx`ブラウザーにします。</span><span class="sxs-lookup"><span data-stu-id="e961e-132">Press F5 to launch `http://localhost:26648/JSONPClientPage.aspx` in the browser.</span></span>  
  
3.  <span data-ttu-id="e961e-133">ページが読み込まれると、"Name"および"Address"のテキスト入力が設定されている値に注意してください。</span><span class="sxs-lookup"><span data-stu-id="e961e-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="e961e-134">これらの値は、ブラウザーがページのレンダリングを完了した後に、WCF サービスへの呼び出しから提供されたものです。</span><span class="sxs-lookup"><span data-stu-id="e961e-134">These values were supplied from a call to the WCF service after the browser finished rendering the page.</span></span>
