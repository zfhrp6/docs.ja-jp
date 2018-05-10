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
# <a name="stand-alone-diagnostics-feed-sample"></a>スタンドアロン診断フィードのサンプル
このサンプルは、RSS フィードおよび Atom 配信 Windows Communication Foundation (WCF) でのフィードを作成する方法を示します。 オブジェクト モデルの基本および Windows Communication Foundation (WCF) サービスをセットアップする方法を示す基本的な"Hello World"プログラムすることをお勧めします。  
  
 WCF 配信フィードを特殊なデータ型を返すサービス操作としてモデル化<xref:System.ServiceModel.Syndication.SyndicationFeedFormatter>です。 <xref:System.ServiceModel.Syndication.SyndicationFeedFormatter> のインスタンスは、フィードを RSS 2.0 形式および Atom 1.0 形式の両方にシリアル化できます。 使用するコントラクトを次のサンプル コードに示します。  
  
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
  
 `GetProcesses`操作の注釈が付いて、 <xref:System.ServiceModel.Web.WebGetAttribute> WCF が HTTP GET をディスパッチする方法を制御することができます属性に対する要求のサービス操作と送信されるメッセージの形式を指定します。  
  
 すべての WCF サービスのような配信フィードが、任意のマネージ アプリケーションでホストされる自己を指定できます。 配信サービスが適切に機能するには、特定のバインディング (<xref:System.ServiceModel.WebHttpBinding>) と、特定のエンドポイント動作 (<xref:System.ServiceModel.Description.WebHttpBehavior>) が必要です。 新しい <xref:System.ServiceModel.Web.WebServiceHost> クラスには、特定の構成を使用せずにこのようなエンドポイントを作成する際に便利な API が用意されています。  
  
```  
WebServiceHost host = new WebServiceHost(typeof(ProcessService), new Uri("http://localhost:8000/diagnostics"));  
  
            //The WebServiceHost will automatically provide a default endpoint at the base address  
            //using the proper binding (the WebHttpBinding) and endpoint behavior (the WebHttpBehavior)  
```  
  
 または、IIS でホストされる .svc ファイルから <xref:System.ServiceModel.Activation.WebServiceHostFactory> を使用して、同等の機能を用意することもできます (この手法は、このサンプル コードでは示されません)。  
  
```  
<%@ ServiceHost Language="C#|VB" Debug="true" Service="ProcessService" %>  
```  
  
 このサービスは標準の HTTP GET を使用して要求を受け取るので、サービスへのアクセスには、RSS または ATOM に対応している任意のクライアントを使用できます。 たとえばに移動してこのサービスの出力を表示できますhttp://localhost:8000/diagnostics/feed/?format=atomまたはhttp://localhost:8000/diagnostics/feed/?format=rssInternet Explorer 7 などの RSS 対応のブラウザーでします。  
  
 使用することも、[方法、WCF 配信オブジェクト モデルにマップ Atom および RSS](../../../../docs/framework/wcf/feature-details/how-the-wcf-syndication-object-model-maps-to-atom-and-rss.md)シンジケート データの読み取りし、命令型コードを使用してそれを処理します。  
  
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
  
### <a name="to-set-up-build-and-run-the-sample"></a>サンプルをセットアップ、ビルド、および実行するには  
  
1.  権限があるか、適切なアドレス登録 HTTP おようび HTTPS 用コンピューター上の指示の設定の説明に従って確認[Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。  
  
2.  ソリューションをビルドします。  
  
3.  コンソール アプリケーションを実行します。  
  
4.  コンソール アプリケーションの実行中に移動http://localhost:8000/diagnostics/feed/?format=atomまたはhttp://localhost:8000/diagnostics/feed/?format=rssRSS 対応のブラウザーを使用します。  
  
> [!IMPORTANT]
>  サンプルは、既にコンピューターにインストールされている場合があります。 続行する前に、次の (既定の) ディレクトリを確認してください。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  このディレクトリが存在しない場合に、 [Windows Communication Foundation (WCF) および .NET Framework 4 向けの Windows Workflow Foundation (WF) サンプル](http://go.microsoft.com/fwlink/?LinkId=150780)すべて Windows Communication Foundation (WCF) をダウンロードして[!INCLUDE[wf1](../../../../includes/wf1-md.md)]サンプルです。 このサンプルは、次のディレクトリに格納されます。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Syndication\DiagnosticsFeed`  
  
## <a name="see-also"></a>関連項目  
 [WCF Web HTTP プログラミング モデル](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-model.md)  
 [WCF 配信](../../../../docs/framework/wcf/feature-details/wcf-syndication.md)
