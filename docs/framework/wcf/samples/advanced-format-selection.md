---
title: 高度な形式選択
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e02d9082-4d55-41d8-9329-98f6d1c77f06
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 93d7fe0742e16abd92682094ca20d51488516e6e
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 04/30/2018
---
# <a name="advanced-format-selection"></a><span data-ttu-id="f5022-102">高度な形式選択</span><span class="sxs-lookup"><span data-stu-id="f5022-102">Advanced Format Selection</span></span>
<span data-ttu-id="f5022-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST プログラミング モデルを拡張して新しい送信応答形式をサポートする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="f5022-103">This sample demonstrates how to extend the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] REST programming model to support new outgoing response formats.</span></span> <span data-ttu-id="f5022-104">また、このサンプルでは T4 テンプレートを使用して応答を XHTML ページとして返し、ビュースタイル プログラミング モデルの実装方法も示します。</span><span class="sxs-lookup"><span data-stu-id="f5022-104">In addition, the sample uses a T4 Template to return the response as an XHTML page, demonstrating how a view-style programming model can be implemented.</span></span>  
  
## <a name="sample-details"></a><span data-ttu-id="f5022-105">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="f5022-105">Sample Details</span></span>  
 <span data-ttu-id="f5022-106">このサンプルは、単純なサービスと、サービスに要求を発行するクライアント コードで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-106">The sample consists of a simple service along with client code that makes requests to the service.</span></span>  <span data-ttu-id="f5022-107">サービスは、単一の [WebGet] 操作をサポートします。この操作には、`Message EchoListWithGet(string list);` のメソッド シグネチャがあります。</span><span class="sxs-lookup"><span data-stu-id="f5022-107">The service supports a single [WebGet] operation, which has the following method signature: `Message EchoListWithGet(string list);`</span></span>  
  
 <span data-ttu-id="f5022-108">クライアントでサービスに対する要求が発行されると、`list` クエリ文字列パラメーターの項目のコンマで区切られた一覧が示され、サービスからは、XML、JSON、Atom、XHTML、または jpeg のいずれかの形式で同じ一覧が返されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-108">When the client makes a request to the service, it provides a comma-separated list of items from the `list` query-string parameter and the service returns that same list in one of the following formats: XML, JSON, Atom, XHTML, or jpeg.</span></span>  
  
 <span data-ttu-id="f5022-109">サービスから返される応答の形式は、最初は `format` クエリ文字列パラメーターで決定され、2 回目は要求で指定された HTTP Accept ヘッダーで決定されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-109">The response format returned by the service is determined first by a `format` query-string parameter and second by an HTTP Accept header supplied with the request.</span></span> <span data-ttu-id="f5022-110">`format` クエリ文字列パラメーターの値が前に示した形式のいずれかである場合、応答はその形式で返されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-110">If the value of `format` query-string parameter is one of the preceding formats, then the response is returned in that format.</span></span> <span data-ttu-id="f5022-111">`format` クエリ文字列が存在しない場合、サービスは要求からの Accept ヘッダー要素を反復処理し、サービスがサポートする最初のコンテンツ タイプの形式を返します。</span><span class="sxs-lookup"><span data-stu-id="f5022-111">If the `format` query-string is not present, then the service iterates through the Accept header elements from the request and returns the format of the first content-type that the service supports.</span></span>  
  
 <span data-ttu-id="f5022-112">操作の戻り値の型については注意が必要です。</span><span class="sxs-lookup"><span data-stu-id="f5022-112">The return type of the operation is worth noting.</span></span> <span data-ttu-id="f5022-113">[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST プログラミング モデルは、操作で  <xref:System.ServiceModel.Channels.Message> 以外の型が返される場合にのみ XML 応答形式と JSON 応答形式をネイティブでサポートします。</span><span class="sxs-lookup"><span data-stu-id="f5022-113">The [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] REST programming model only natively supports XML and JSON response formats when an operation returns a type other than <xref:System.ServiceModel.Channels.Message>.</span></span> <span data-ttu-id="f5022-114">ただし、戻り値の型として <xref:System.ServiceModel.Channels.Message> が使用されている場合、メッセージの内容の形式の設定は、開発者によって完全に制御されています。</span><span class="sxs-lookup"><span data-stu-id="f5022-114">However, when using <xref:System.ServiceModel.Channels.Message> as the return type, the developer has complete control over how the content of the message should be formatted.</span></span>  
  
 <span data-ttu-id="f5022-115">このサンプルでは、<xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A> メソッド、<xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> メソッドおよび <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> メソッドを使用して、文字列の一覧を XML、JSON、および ATOM のメッセージにそれぞれシリアル化しています。</span><span class="sxs-lookup"><span data-stu-id="f5022-115">The sample uses the <xref:System.ServiceModel.Web.WebOperationContext.CreateXmlResponse%2A>, <xref:System.ServiceModel.Web.WebOperationContext.CreateJsonResponse%2A> and <xref:System.ServiceModel.Web.WebOperationContext.CreateAtom10Response%2A> methods to serialize the list of strings into XML, JSON, and ATOM messages respectively.</span></span> <span data-ttu-id="f5022-116">jpeg 応答形式の場合は、<xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> メソッドが使用され、画像はストリームに保存されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-116">For the jpeg response format, the <xref:System.ServiceModel.Web.WebOperationContext.CreateStreamResponse%2A> method is used and the image is saved to the stream.</span></span> <span data-ttu-id="f5022-117">XHTML 応答の場合、<xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> が事前に処理された T4 テンプレートと共に使用されます。この T4 テンプレートは .tt ファイルと自動生成された .cs ファイルで構成されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-117">For the XHTML response, the <xref:System.ServiceModel.Web.WebOperationContext.CreateTextResponse%2A> is used along with a preprocessed T4 template, which consists of a .tt file and an auto-generated .cs file.</span></span> <span data-ttu-id="f5022-118">開発者は、.tt ファイルを使用して変数と制御構造を含むテンプレート フォームで応答を作成できます。</span><span class="sxs-lookup"><span data-stu-id="f5022-118">The .tt file allows a developer to write a response in a template form that contains variables and control structures.</span></span> <span data-ttu-id="f5022-119">T4 の詳細については、次を参照してください。[を使用してテキスト テンプレートで成果物を生成する](http://go.microsoft.com/fwlink/?LinkId=166023)です。</span><span class="sxs-lookup"><span data-stu-id="f5022-119">For more information about T4, see [Generating Artifacts By Using Text Templates](http://go.microsoft.com/fwlink/?LinkId=166023).</span></span>  
  
 <span data-ttu-id="f5022-120">このサンプルは、コンソール アプリケーション内で実行される自己ホスト型サービスとクライアントで構成されています。</span><span class="sxs-lookup"><span data-stu-id="f5022-120">The sample consists of a self-hosted service and a client that runs within a console application.</span></span> <span data-ttu-id="f5022-121">コンソール アプリケーションが実行されると、クライアントはサービスに要求を発行し、応答からの適切な情報をコンソール ウィンドウに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f5022-121">As the console application runs, the client makes requests to the service and writes the pertinent information from the responses to the console window.</span></span>  
  
#### <a name="to-run-this-sample"></a><span data-ttu-id="f5022-122">このサンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="f5022-122">To run this sample</span></span>  
  
1.  <span data-ttu-id="f5022-123">高度な形式選択サンプルのソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="f5022-123">Open the solution for the Advanced Format Selection Sample.</span></span> <span data-ttu-id="f5022-124">サンプルを正しく実行するには、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を起動するときに、管理者として実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="f5022-124">When launching [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], you should run as an administrator for the sample to execute successfully.</span></span> <span data-ttu-id="f5022-125">これには、右クリックし、[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]アイコンをクリックして選択する**管理者として実行**コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="f5022-125">Do this by right-clicking the [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] icon and choosing **Run as Administrator** from the context menu.</span></span>  
  
2.  <span data-ttu-id="f5022-126">Ctrl キーと Shift キーを押しながら B キーを押してソリューションをビルドし、Ctrl キーを押しながら F5 キーを押してコンソール アプリケーションの AdvancedFormatSelection プロジェクトを、デバッグを行わずに実行します。</span><span class="sxs-lookup"><span data-stu-id="f5022-126">Press CTRL+SHIFT+B to build the solution and then press Ctrl-F5 to run the console application AdvancedFormatSelection project without debugging.</span></span> <span data-ttu-id="f5022-127">コンソール ウィンドウが表示されて、実行中のサービスの URI および実行中のサービスの HTML ヘルプ ページの URI が示されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-127">The console window appears and provides the URI of the running service and the URI of the HTML help page for the running service.</span></span>  
  
3.  <span data-ttu-id="f5022-128">サンプルが実行されると、クライアントは要求をサービスに送信し、応答をコンソール ウィンドウに書き込みます。</span><span class="sxs-lookup"><span data-stu-id="f5022-128">As the sample runs, the client sends requests to the service and writes the responses to the console window.</span></span> <span data-ttu-id="f5022-129">応答の形式は、XML、JSON、Atom、および XHTML のいずれかになります。</span><span class="sxs-lookup"><span data-stu-id="f5022-129">Notice the different formats of the responses: XML, JSON, Atom, and XHTML.</span></span>  
  
4.  <span data-ttu-id="f5022-130">.jpeg 形式の応答を要求できる URI を参照するよう要求されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-130">You are then prompted to browse to a URI in which you can request the response in a .jpeg format.</span></span> <span data-ttu-id="f5022-131">ブラウザーを開き、指定された URI を参照します。</span><span class="sxs-lookup"><span data-stu-id="f5022-131">Open a browser and browse to the given URI.</span></span>  
  
5.  <span data-ttu-id="f5022-132">任意のキーを押して、サンプルを終了します。</span><span class="sxs-lookup"><span data-stu-id="f5022-132">Press any key to terminate the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f5022-133">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="f5022-133">The samples may already be installed on your machine.</span></span> <span data-ttu-id="f5022-134">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="f5022-134">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="f5022-135">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="f5022-135">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="f5022-136">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="f5022-136">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\AdvancedFormatSelection`  
  
## <a name="see-also"></a><span data-ttu-id="f5022-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="f5022-137">See Also</span></span>
