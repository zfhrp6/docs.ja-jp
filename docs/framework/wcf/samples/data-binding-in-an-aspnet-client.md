---
title: "ASP.NET クライアントでのデータ バインディング"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 68b49fa6-94e7-4d4c-a34e-902a2b3770b6
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 18d133b8eb5bef9e6e9152ef856265c1cbe18b51
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="data-binding-in-an-aspnet-client"></a><span data-ttu-id="8a29b-102">ASP.NET クライアントでのデータ バインディング</span><span class="sxs-lookup"><span data-stu-id="8a29b-102">Data Binding in an ASP.NET Client</span></span>
<span data-ttu-id="8a29b-103">このサンプルでは、一般的な [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サービスによって返されたデータを Web フォーム アプリケーションにバインドする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-103">This sample demonstrates how to bind data returned by a typical [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service in a Web Forms application.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="8a29b-104">このサンプルのセットアップ手順とビルド手順については、このトピックの最後を参照してください。</span><span class="sxs-lookup"><span data-stu-id="8a29b-104">The setup procedure and build instructions for this sample are located at the end of this topic.</span></span>  
  
 <span data-ttu-id="8a29b-105">このサンプルでは、要求/応答通信パターンを定義するコントラクトを実装するサービスを示します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-105">This sample demonstrates a service that implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8a29b-106">このサンプルは、ブラウザからアクセスできるクライアントの Web フォーム アプリケーションと、インターネット インフォメーション サービス (IIS) によってホストされる [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスとで構成されています。</span><span class="sxs-lookup"><span data-stu-id="8a29b-106">The sample consists of a client Web Forms application accessible from a browser and a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service hosted by Internet Information Services (IIS).</span></span>  
  
 <span data-ttu-id="8a29b-107">サービスは、要求/応答通信パターンを定義するコントラクトを実装します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-107">The service implements a contract that defines a request-reply communication pattern.</span></span> <span data-ttu-id="8a29b-108">コントラクトは `IWeatherService` インターフェイスによって定義されます。このインターフェイスでは、`GetWeatherData` という名前の操作が公開されます。</span><span class="sxs-lookup"><span data-stu-id="8a29b-108">The contract is defined by the `IWeatherService` interface, which exposes an operation named `GetWeatherData`.</span></span> <span data-ttu-id="8a29b-109">この操作は都市名の配列を受け付け、各都市の予想最高気温と最低気温を表す `WeatherData` オブジェクトの配列を返します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-109">This operation accepts an array of cities and returns an array of `WeatherData` objects that represent the high and low forecasted temperature for a city.</span></span>  
  
 <span data-ttu-id="8a29b-110">[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] クライアントの .aspx ページには DataGrid Web コントロールが定義されています。このコントロールには、サービスによって返されるデータのグラフィック表示が含まれます。</span><span class="sxs-lookup"><span data-stu-id="8a29b-110">On the [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] client .aspx page, a DataGrid Web control is defined, which contains the graphical representation of the data returned by the service.</span></span> <span data-ttu-id="8a29b-111">.aspx ページのコードによって気象データ用の [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] サービスが呼び出され、そのデータは `WeatherData` オブジェクトの配列に返されます。</span><span class="sxs-lookup"><span data-stu-id="8a29b-111">Code on the .aspx page calls the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] service for weather data and returns the data to an array of `WeatherData` objects.</span></span> <span data-ttu-id="8a29b-112">DataGrid の `DataSource` プロパティをこの配列に設定することにより、データを取得する場所を指定します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-112">The DataGrid specifies where to get its data from by setting its `DataSource` property to that array.</span></span> <span data-ttu-id="8a29b-113">データ バインディングは、DataGrid の `DataBind` メソッドが呼び出されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-113">The data binding occurs with a call to the DataGrid's `DataBind` method.</span></span> <span data-ttu-id="8a29b-114">このすべてのコードに含まれている、します。`aspx`</span><span class="sxs-lookup"><span data-stu-id="8a29b-114">All of this code is contained inside the .`aspx`</span></span> <span data-ttu-id="8a29b-115">ページの`Page_Load`DataGrid のたびにユーザーがブラウザーにページのデータを更新するためのメソッドを更新します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-115">page's `Page_Load` method, so every time the user refreshes the browser page, the data is updated in the DataGrid.</span></span>  
  
### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="8a29b-116">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="8a29b-116">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="8a29b-117">実行したことを確認してください、 [Windows Communication Foundation サンプルの 1 回限りのセットアップ手順](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)です。</span><span class="sxs-lookup"><span data-stu-id="8a29b-117">Ensure that you have performed the [One-Time Setup Procedure for the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).</span></span>  
  
2.  <span data-ttu-id="8a29b-118">ソリューションの C# 版または Visual Basic .NET 版をビルドするには、「 [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md)」の手順に従います。</span><span class="sxs-lookup"><span data-stu-id="8a29b-118">To build the C# or Visual Basic .NET edition of the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
3.  <span data-ttu-id="8a29b-119">このサンプルのクライアントは、開発用 Web サーバーで実行される Web サイトです。</span><span class="sxs-lookup"><span data-stu-id="8a29b-119">This sample's client is a Web site that runs under a development Web server.</span></span> <span data-ttu-id="8a29b-120">開発 Web サーバーを起動するには、コマンド プロンプトで、次を入力します。"`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`です。</span><span class="sxs-lookup"><span data-stu-id="8a29b-120">To launch the development Web server, type the following at the command prompt: "`%SystemDrive%\Program Files\Common Files\Microsoft Shared\DevServer\9.0\WebDev.WebServer.EXE" /port:8000 /path:<WebFormsSamplePath>\CS\client /vpath:/client`.</span></span> <span data-ttu-id="8a29b-121">次に、http://localhost:8000/client に移動します。</span><span class="sxs-lookup"><span data-stu-id="8a29b-121">Then browse to http://localhost:8000/client.</span></span> <span data-ttu-id="8a29b-122">このサンプルを複数のコンピューターで実行するには、クライアントの Web.config ファイル内の `localhost` へのすべての参照をサーバーのコンピューター名に置き換えます。</span><span class="sxs-lookup"><span data-stu-id="8a29b-122">To run this sample across computers, replace all references to `localhost` in the client's Web.config file with the computer name of the server.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="8a29b-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="8a29b-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="8a29b-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="8a29b-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="8a29b-125">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="8a29b-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="8a29b-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="8a29b-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Scenario\DataBinding\WebForms`  
  
## <a name="see-also"></a><span data-ttu-id="8a29b-127">関連項目</span><span class="sxs-lookup"><span data-stu-id="8a29b-127">See Also</span></span>
