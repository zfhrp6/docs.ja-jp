---
title: スタンドアロン診断フィードのサンプル
ms.date: 03/30/2017
ms.assetid: d31c6c1f-292c-4d95-8e23-ed8565970ea5
ms.openlocfilehash: 730cf011208ea1b57929fff4a1953fd3a935335c
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/07/2018
---
# <a name="stand-alone-diagnostics-feed-sample"></a><span data-ttu-id="cd9a7-102">スタンドアロン診断フィードのサンプル</span><span class="sxs-lookup"><span data-stu-id="cd9a7-102">Stand-Alone Diagnostics Feed Sample</span></span>
<span data-ttu-id="cd9a7-103">このサンプルは、RSS フィードおよび Atom 配信 Windows Communication Foundation (WCF) でのフィードを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-103">This sample demonstrates how to create an RSS/Atom feed for syndication with Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="cd9a7-104">オブジェクト モデルの基本および Windows Communication Foundation (WCF) サービスをセットアップする方法を示す基本的な"Hello World"プログラムすることをお勧めします。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-104">It is a basic "Hello World" program that shows the basics of the object model and how to set it up on a Windows Communication Foundation (WCF) service.</span></span>  
  
 <span data-ttu-id="cd9a7-105">WCF 配信フィードを特殊なデータ型を返すサービス操作としてモデル化<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>です。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-105">WCF models syndication feeds as service operations that return a special data type, <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>.</span></span> <span data-ttu-id="cd9a7-106"><xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> のインスタンスは、フィードを RSS 2.0 形式および Atom 1.0 形式の両方にシリアル化できます。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-106">Instances of <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> can serialize a feed into both the RSS 2.0 and Atom 1.0 formats.</span></span> <span data-ttu-id="cd9a7-107">使用するコントラクトを次のサンプル コードに示します。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-107">The following sample code shows the contract used.</span></span>  
  
```  
[ServiceContract(Namespace = "")]  
    interface IDiagnosticsService  
    {  
        [OperationContract]  
        //The [WebGet] attribute controls how WCF dispatches  
        //HTTP requests to service operations based on a URI suffix  
        //(the part of the request URI after the endpoint address)  
        //using the HTTP GET method. The UriTemplate specifies a relative  
        //path of 'feed', and specifies that the format is  
        //supplied using a query string.   
        [WebGet(UriTemplate="feed?format={format}")]  
        [ServiceKnownType(typeof(Atom10FeedFormatter))]  
        [ServiceKnownType(typeof(Rss20FeedFormatter))]  
        SyndicationFeedFormatter GetProcesses(string format);  
    }  
```  
  
 <span data-ttu-id="cd9a7-108">`GetProcesses`操作の注釈が付いて、 <xref:System.ServiceModel.Web.WebGetAttribute> WCF が HTTP GET をディスパッチする方法を制御することができます属性に対する要求のサービス操作と送信されるメッセージの形式を指定します。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-108">The `GetProcesses` operation is annotated with the <xref:System.ServiceModel.Web.WebGetAttribute> attribute that enables you to control how WCF dispatches HTTP GET requests to service operations and specify the format of the messages sent.</span></span>  
  
 <span data-ttu-id="cd9a7-109">すべての WCF サービスのような配信フィードが、任意のマネージ アプリケーションでホストされる自己を指定できます。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-109">Like any WCF service, syndication feeds can be self hosted in any managed application.</span></span> <span data-ttu-id="cd9a7-110">配信サービスが適切に機能するには、特定のバインディング (<xref:System.ServiceModel.WebHttpBinding>) と、特定のエンドポイント動作 (<xref:System.ServiceModel.Description.WebHttpBehavior>) が必要です。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-110">Syndication services require a specific binding (the <xref:System.ServiceModel.WebHttpBinding>) and a specific endpoint behavior (the <xref:System.ServiceModel.Description.WebHttpBehavior>) to function correctly.</span></span> <span data-ttu-id="cd9a7-111">新しい <xref:System.ServiceModel.Web.WebServiceHost> クラスには、特定の構成を使用せずにこのようなエンドポイントを作成する際に便利な API が用意されています。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-111">The new <xref:System.ServiceModel.Web.WebServiceHost> class provides a convenient API for creating such endpoints without specific configuration.</span></span>  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 <span data-ttu-id="cd9a7-112">または、IIS でホストされる .svc ファイルから <xref:System.ServiceModel.Activation.WebServiceHostFactory> を使用して、同等の機能を用意することもできます (この手法は、このサンプル コードでは示されません)。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-112">Alternatively, you can use <xref:System.ServiceModel.Activation.WebServiceHostFactory> from within an IIS-hosted .svc file to provide equivalent functionality (this technique is not demonstrated in this sample code).</span></span>  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 <span data-ttu-id="cd9a7-113">このサービスは標準の HTTP GET を使用して要求を受け取るので、サービスへのアクセスには、RSS または ATOM に対応している任意のクライアントを使用できます。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-113">Because this service receives requests using the standard HTTP GET, you can use any RSS or ATOM-aware client to access the service.</span></span> <span data-ttu-id="cd9a7-114">たとえばに移動してこのサービスの出力を表示できますhttp://localhost:8000/diagnostics/feed/?format=atomまたはhttp://localhost:8000/diagnostics/feed/?format=rssInternet Explorer 7 などの RSS 対応のブラウザーでします。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-114">For example, you can view the output of this service by navigating to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss in an RSS-aware browser such as Internet Explorer 7.</span></span>  
  
 <span data-ttu-id="cd9a7-115">使用することも、[方法、WCF 配信オブジェクト モデルにマップ Atom および RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)シンジケート データの読み取りし、命令型コードを使用してそれを処理します。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-115">You can also use the [How the WCF Syndication Object Model Maps to Atom and RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md) to read syndicated data and process it using imperative code.</span></span>  
  
```  
XmlReader reader = XmlReader.Create( "http://localhost:8000/diagnostics/feed/?format=rss",  
new XmlReaderSettings()  
{  
//MaxCharactersInDocument can be used to control the maximum amount of data   
//read from the reader and helps prevent OutOfMemoryException  
MaxCharactersInDocument = 1024 * 64  
} );  
  
SyndicationFeed feed = SyndicationFeed.Load( reader );  
  
foreach (SyndicationItem i in feed.Items)  
{  
        XmlSyndicationContent content = i.Content as XmlSyndicationContent;  
        ProcessData pd = content.ReadContent<ProcessData>();  
  
        Console.WriteLine(i.Title.Text);  
        Console.WriteLine(pd.ToString());  
}  
```  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="cd9a7-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="cd9a7-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="cd9a7-117">権限があるか、適切なアドレス登録 HTTP おようび HTTPS 用コンピューター上の指示の設定の説明に従って確認[Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-117">Ensure that you have the right address registration permission for HTTP and HTTPS on the computer as explained in the set up instructions in [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="cd9a7-118">ソリューションをビルドします。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-118">Build the solution.</span></span>  
  
3.  <span data-ttu-id="cd9a7-119">コンソール アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-119">Run the console application.</span></span>  
  
4.  <span data-ttu-id="cd9a7-120">コンソール アプリケーションの実行中に移動http://localhost:8000/diagnostics/feed/?format=atomまたはhttp://localhost:8000/diagnostics/feed/?format=rssRSS 対応のブラウザーを使用します。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-120">While the console application is running, navigate to http://localhost:8000/diagnostics/feed/?format=atom or http://localhost:8000/diagnostics/feed/?format=rss using an RSS-aware browser.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="cd9a7-121">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-121">The samples may already be installed on your computer.</span></span> <span data-ttu-id="cd9a7-122">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-122">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="cd9a7-123">このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-123">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="cd9a7-124">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="cd9a7-124">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a><span data-ttu-id="cd9a7-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="cd9a7-125">See Also</span></span>  
 [<span data-ttu-id="cd9a7-126">WCF Web HTTP プログラミング モデル</span><span class="sxs-lookup"><span data-stu-id="cd9a7-126">WCF Web HTTP Programming Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [<span data-ttu-id="cd9a7-127">WCF 配信</span><span class="sxs-lookup"><span data-stu-id="cd9a7-127">WCF Syndication</span></span>](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
