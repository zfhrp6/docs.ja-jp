---
title: JSONP
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c13b4d7b-dac7-4ffd-9f84-765c903511e1
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f9a9355c223d3d37811383d52d64f0ac6ddeeaea
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="jsonp"></a><span data-ttu-id="57734-102">JSONP</span><span class="sxs-lookup"><span data-stu-id="57734-102">JSONP</span></span>
<span data-ttu-id="57734-103">このサンプルでは、WCF REST サービスの JSONP (JSON with Padding) をサポートする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="57734-103">This sample demonstrates how to support JSON with Padding (JSONP) in WCF REST services.</span></span> <span data-ttu-id="57734-104">JSONP とは、現在のドキュメントでスクリプト タグを生成してドメイン間スクリプトを呼び出す際に使用される変換です。</span><span class="sxs-lookup"><span data-stu-id="57734-104">JSONP is a convention used to invoke cross-domain scripts by generating script tags in the current document.</span></span> <span data-ttu-id="57734-105">結果は、指定したコールバック関数で返されます。</span><span class="sxs-lookup"><span data-stu-id="57734-105">The result is returned in a specified callback function.</span></span> <span data-ttu-id="57734-106">JSONP はなどのタグするという考えに基づいて\<スクリプトの src =「http://...」> の任意のドメインからのスクリプトを評価することができ、ようなタグによって取得されたスクリプトが、その他の関数が既に定義されて範囲で評価します。</span><span class="sxs-lookup"><span data-stu-id="57734-106">JSONP is based on the idea that tags such as \<script src="http://..." > can evaluate scripts from any domain and the script retrieved by those tags is evaluated within a scope in which other functions may already be defined.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="57734-107">使用例</span><span class="sxs-lookup"><span data-stu-id="57734-107">Demonstrates</span></span>  
 <span data-ttu-id="57734-108">JSONP によるドメイン間スクリプト。</span><span class="sxs-lookup"><span data-stu-id="57734-108">Cross-domain scripting with JSONP.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="57734-109">説明</span><span class="sxs-lookup"><span data-stu-id="57734-109">Discussion</span></span>  
 <span data-ttu-id="57734-110">このサンプルには、ブラウザーで表示された後にスクリプト ブロックを動的に追加する Web ページが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57734-110">The sample includes a Web page that dynamically adds a script block after the page has been rendered in the browser.</span></span> <span data-ttu-id="57734-111">このスクリプト ブロックは、`GetCustomer` 操作を 1 つ持つ WCF REST サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57734-111">This script block calls a WCF REST service that has a single operation, `GetCustomer`.</span></span> <span data-ttu-id="57734-112">WCF REST サービスは、コールバック関数名でラップされた顧客の名前とアドレスを返します。</span><span class="sxs-lookup"><span data-stu-id="57734-112">The WCF REST service returns a customer’s name and address wrapped in a callback function name.</span></span> <span data-ttu-id="57734-113">WCF REST サービスが応答を返すと、顧客データを使用して Web ページ上のコールバック関数が呼び出され、このコールバック関数によって Web ページ上に顧客データが表示されます。</span><span class="sxs-lookup"><span data-stu-id="57734-113">When the WCF REST service responds, the callback function on the Web page is invoked with the customer data and the callback function displays the data on the Web page.</span></span> <span data-ttu-id="57734-114">スクリプト タグの挿入とコールバック関数の実行は、ASP.NET AJAX ScriptManager コントロールによって自動的に処理されます。</span><span class="sxs-lookup"><span data-stu-id="57734-114">The injection of the script tag and the execution of the callback function is automatically handled by the ASP.NET AJAX ScriptManager control.</span></span> <span data-ttu-id="57734-115">次のコードに示すように、使用パターンはすべての ASP.NET AJAX プロキシと同じで、JSONP を有効にするための行が 1 つ追加されます。</span><span class="sxs-lookup"><span data-stu-id="57734-115">The usage pattern is the same as with all ASP.NET AJAX proxies, with the addition of one line to enable JSONP, as shown in the following code:</span></span>  
  
```csharp  
var proxy = new JsonpAjaxService.CustomerService();  
proxy.set_enableJsonp(true);  
proxy.GetCustomer(onSuccess, onFail, null);  
```  
  
 <span data-ttu-id="57734-116">Web ページでは、WCF REST サービスを呼び出すことができます。これは、WCF REST サービスが、<xref:System.ServiceModel.Description.WebScriptEndpoint> が `crossDomainScriptAccessEnabled` に設定された `true` を使用しているからです。</span><span class="sxs-lookup"><span data-stu-id="57734-116">The Web page can call the WCF REST service because the service is using the <xref:System.ServiceModel.Description.WebScriptEndpoint> with `crossDomainScriptAccessEnabled` set to `true`.</span></span> <span data-ttu-id="57734-117">下にある Web.config ファイルでこれらの構成が終わったら、 \<system.serviceModel > 要素。</span><span class="sxs-lookup"><span data-stu-id="57734-117">Both of these configurations are done in the Web.config file under the \<system.serviceModel> element.</span></span>  
  
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
  
 <span data-ttu-id="57734-118">ScriptManager はサービスとのやり取りを管理し、JSONP アクセスの手動実装の複雑さを隠蔽します。</span><span class="sxs-lookup"><span data-stu-id="57734-118">ScriptManager manages the interaction with the service and hides away the complexity of manually implementing JSONP access.</span></span> <span data-ttu-id="57734-119">`crossDomainScriptAccessEnabled` が `true` に設定されていて、操作の応答形式が JSON である場合、[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] インフラストラクチャは要求の URI からコールバック クエリ文字列パラメーターを検出し、そのコールバック クエリ文字列パラメーターの値で JSON 応答をラップします。</span><span class="sxs-lookup"><span data-stu-id="57734-119">When `crossDomainScriptAccessEnabled` is set to `true` and the response format for an operation is JSON, the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] infrastructure inspects the URI of the request for a callback query string parameter and wraps the JSON response with the value of the callback query string parameter.</span></span> <span data-ttu-id="57734-120">このサンプルでは、Web ページは次の URI を使用して WCF REST サービスを呼び出します。</span><span class="sxs-lookup"><span data-stu-id="57734-120">In the sample, the Web page calls the WCF REST service with the following URI.</span></span>  
  
```  
http://localhost:33695/CustomerService/GetCustomer?callback=Sys._json0  
```  
  
 <span data-ttu-id="57734-121">コールバック クエリ文字列パラメーターには `JsonPCallback` の値が含まれているため、WCF サービスは次の例に示す JSONP 応答を返します。</span><span class="sxs-lookup"><span data-stu-id="57734-121">Because the callback query string parameter has a value of `JsonPCallback`, the WCF service returns a JSONP response shown in the following example.</span></span>  
  
```  
Sys._json0({"__type":"Customer:#Microsoft.Samples.Jsonp","Address":"1 Example Way","Name":"Bob"});  
```  
  
 <span data-ttu-id="57734-122">JSONP 応答には、JSON として書式設定され、Web ページが要求したコールバック関数名でラップされた顧客データが含まれています。</span><span class="sxs-lookup"><span data-stu-id="57734-122">This JSONP response includes the customer data formatted as JSON, wrapped with the callback function name that the Web page requested.</span></span> <span data-ttu-id="57734-123">ScriptManager は、ドメイン間要求を実現するスクリプト タグを使用してこのコールバックを実行し、ASP.NET AJAX プロキシの GetCustomer 操作に渡された onSuccess ハンドラーに結果を渡します。</span><span class="sxs-lookup"><span data-stu-id="57734-123">ScriptManager will execute this callback using a script tag to accomplish the cross-domain request, and then pass the result to the onSuccess handler that was passed to the GetCustomer operation of the ASP.NET AJAX proxy.</span></span>  
  
 <span data-ttu-id="57734-124">このサンプルは 2 つの ASP.NET Web アプリケーションで構成されます。1 つは [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスのみを含み、もう 1 つはサービスを呼び出す .aspx Web ページを含みます。</span><span class="sxs-lookup"><span data-stu-id="57734-124">The sample consists of two ASP.NET web applications: one contains just a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service, and another one contains the .aspx webpage, which calls the service.</span></span> <span data-ttu-id="57734-125">ソリューションの実行中、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] は 2 つの Web サイトを別々のポート上にホストします。これにより、サービスとクライアントが別々のドメインに存在する環境が作成されます。</span><span class="sxs-lookup"><span data-stu-id="57734-125">When running the solution, [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] will host the two websites on different ports, which creates an environment where the service and client live on different domains.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="57734-126">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="57734-126">The samples may already be installed on your machine.</span></span> <span data-ttu-id="57734-127">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="57734-127">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="57734-128">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="57734-128">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="57734-129">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="57734-129">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\AJAX\JSONP`  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="57734-130">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="57734-130">To run the sample</span></span>  
  
1.  <span data-ttu-id="57734-131">JSONP サンプルのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="57734-131">Open the solution for the JSONP Sample.</span></span>  
  
2.  <span data-ttu-id="57734-132">F5 キーを押して、http://localhost:26648/jsonpclientpage.aspx ハイパーリンク""http://localhost:26648/JSONPClientPage.aspx をブラウザーにします。</span><span class="sxs-lookup"><span data-stu-id="57734-132">Press F5 to launch  HYPERLINK "http://localhost:26648/JSONPClientPage.aspx" http://localhost:26648/JSONPClientPage.aspx in the browser.</span></span>  
  
3.  <span data-ttu-id="57734-133">ページが読み込まれると、"Name"および"Address"のテキスト入力が設定されている値に注意してください。</span><span class="sxs-lookup"><span data-stu-id="57734-133">Notice that after the page loads, the text inputs for "Name" and "Address" are populated by values.</span></span>  <span data-ttu-id="57734-134">これらの値は、ブラウザーがページを表示した後に [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスの呼び出しから提供されたものです。</span><span class="sxs-lookup"><span data-stu-id="57734-134">These values were supplied from a call to the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service after the browser finished rendering the page.</span></span>
