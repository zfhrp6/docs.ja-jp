---
title: "HTTP 受信確認チャネル"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf8e62d99ffc0a7296d83685dfeb15993afff934
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="http-acknowledgement-channel"></a><span data-ttu-id="68521-102">HTTP 受信確認チャネル</span><span class="sxs-lookup"><span data-stu-id="68521-102">HTTP Acknowledgement Channel</span></span>
<span data-ttu-id="68521-103">HTTP 受信確認チャネルは、一方向メッセージング パターンを変える階層チャネルの例です。これにより、サービスでは、受信確認を自動的に送信するのではなく受信メッセージを承認または拒否できるようになります。</span><span class="sxs-lookup"><span data-stu-id="68521-103">The HTTP Acknowledgement Channel is an example of a layered channel that changes the one-way messaging pattern, allowing a service to acknowledge or refuse incoming messages rather than automatically sending an acknowledgement on receipt.</span></span> <span data-ttu-id="68521-104">また、HTTP 受信確認チャネルにより、サービスでは、メッセージが処理されるというビジネス レベルの保証がなされるまで受信確認を遅らせることができます。</span><span class="sxs-lookup"><span data-stu-id="68521-104">The HTTP Acknowledgement Channel also allows the service to delay acknowledgement until it can make a business-level guarantee that the message will be processed.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="68521-105">使用例</span><span class="sxs-lookup"><span data-stu-id="68521-105">Demonstrates</span></span>  
 <span data-ttu-id="68521-106"><xref:System.ServiceModel.Channels.ReceiveContext>、階層チャネルの例 (HTTP 受信確認チャネル)。</span><span class="sxs-lookup"><span data-stu-id="68521-106"><xref:System.ServiceModel.Channels.ReceiveContext>, Layered channel example (HTTP Acknowledgement channel).</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="68521-107">説明</span><span class="sxs-lookup"><span data-stu-id="68521-107">Discussion</span></span>  
 <span data-ttu-id="68521-108">HTTP 受信確認チャネルでは、<xref:System.ServiceModel.Channels.ReceiveContext> を実装して、HTTP 要求/応答メッセージング パターンを、受信確認の遅延が可能な一方向のパターンに変えます。</span><span class="sxs-lookup"><span data-stu-id="68521-108">The HTTP Acknowledgement Channel implements <xref:System.ServiceModel.Channels.ReceiveContext> to reshape the HTTP request-reply messaging pattern to a one-way pattern with delayed acknowledgement.</span></span> <span data-ttu-id="68521-109">この新しいパターンを使用すると、サービスでは、OK を示す HTTP ステータス コード 200 の形式で受信確認を送信することによって、メッセージ処理が完了するまでクライアントをブロックすることなく、メッセージ処理を保証できます。または、内部サーバー エラーを示す HTTP ステータス コード 500 の形式でエラー メッセージをクライアントに送信できます。</span><span class="sxs-lookup"><span data-stu-id="68521-109">Using this new pattern, a service can ensure message processing by sending an acknowledgement in the form of an HTTP OK status code of 200 without blocking the client until message processing completes or can send a failure message to the client in the form of an HTTP Internal Server error status code of 500.</span></span> <span data-ttu-id="68521-110">たとえば、サービスでは、メッセージをキューに書き込んだ後に受信確認を送信し、その後で、非同期にメッセージの処理を継続することもできます。</span><span class="sxs-lookup"><span data-stu-id="68521-110">For example, a service could send an acknowledgement after writing a message to a queue, and then continue processing the message asynchronously.</span></span> <span data-ttu-id="68521-111">このシナリオでは、クライアントは、サービスから受信確認を受け取るまで各メッセージを再送信する場合に、サービスによってメッセージが少なくとも一度は処理されたことを確認できます。</span><span class="sxs-lookup"><span data-stu-id="68521-111">In this scenario, a client could be assured its messages were processed at least once by the service, if it re-sent each message until it received an acknowledgement from the service.</span></span> <span data-ttu-id="68521-112">ただし、サービスで、メッセージ処理の保証なしに、HTTP を介した非同期の高速なメッセージ処理を行う必要がある場合は、<xref:System.ServiceModel.Channels.OneWayBindingElement> の方が適しています。</span><span class="sxs-lookup"><span data-stu-id="68521-112">Note that, if a service requires fast asynchronous message processing over HTTP without any message processing guarantees, then the <xref:System.ServiceModel.Channels.OneWayBindingElement> is a more appropriate choice.</span></span>  
  
 <span data-ttu-id="68521-113"><xref:System.ServiceModel.Channels.ReceiveContext> を使用すると、サービスでメッセージを処理できるかどうか判断している間、メッセージをそのままの状態にしておくことができます。</span><span class="sxs-lookup"><span data-stu-id="68521-113"><xref:System.ServiceModel.Channels.ReceiveContext> is used to hold the message in place while it is determined whether the message can be processed at the service.</span></span> <span data-ttu-id="68521-114">サービスでメッセージを正常に処理できることは、HTTP OK ステータス コードを送信する <xref:System.ServiceModel.Channels.ReceiveContext> オブジェクトで Complete を呼び出すことによって示されます。また、サービスでメッセージを処理できるかどうかは、HTTP 内部サーバー エラー ステータス コードを送信する <xref:System.ServiceModel.Channels.ReceiveContext> オブジェクトで `Abandon` の <xref:System.ServiceModel.Channels.ReceiveContext> メソッドを呼び出すことによって示されます。</span><span class="sxs-lookup"><span data-stu-id="68521-114">The ability of a service to successfully process the message is indicated by calling Complete on the <xref:System.ServiceModel.Channels.ReceiveContext> object that sends an HTTP OK status code and whether the service can process the message is indicated by calling <xref:System.ServiceModel.Channels.ReceiveContext>’s `Abandon` method on the <xref:System.ServiceModel.Channels.ReceiveContext> object, which sends an HTTP Internal Server error status code.</span></span>  
  
 <span data-ttu-id="68521-115">この例では、クライアントは従業員 ID を送信して処理情報を要求します。</span><span class="sxs-lookup"><span data-stu-id="68521-115">In this example, the client requests processing information by sending an employee ID.</span></span> <span data-ttu-id="68521-116">サービス側では、受信した従業員 ID が 50 を超える場合は、HTTP ステータス コード 500 (内部サーバー エラー) をクライアントに送信します。それ以外の場合は、処理を正常に実行できると想定し、HTTP ステータス コード 200 (成功) をクライアントに送信します。</span><span class="sxs-lookup"><span data-stu-id="68521-116">On the service end, if the employee ID received is greater than 50, the service sends an HTTP Status code of 500 (Internal Server Error) back to the client, otherwise it is assumed that the processing can be successfully done and sends an HTTP Status code of 200 (Successful) to the client.</span></span>  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="68521-117">サンプルをセットアップ、ビルド、および実行するには</span><span class="sxs-lookup"><span data-stu-id="68521-117">To set up, build, and run the sample</span></span>  
  
1.  <span data-ttu-id="68521-118">管理者特権で [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="68521-118">Open [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] with Administrator privileges.</span></span>  
  
2.  <span data-ttu-id="68521-119">開く、 **HttpAckChannel**ソリューションです。</span><span class="sxs-lookup"><span data-stu-id="68521-119">Open the **HttpAckChannel** solution.</span></span>  
  
3.  <span data-ttu-id="68521-120">新しいインスタンスを開始、**サービス**でプロジェクトを右クリックしてプロジェクト**ソリューション エクスプ ローラー**を選択して**デバッグ**、**新しいインスタンスを開始する** 、コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="68521-120">Start a new instance of the **Service** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, **Start new instance** from the context menu.</span></span>  
  
4.  <span data-ttu-id="68521-121">新しいインスタンスを開始、**クライアント**でプロジェクトを右クリックしてプロジェクト**ソリューション エクスプ ローラー**を選択して**デバッグ**、および**新しいインスタンスを開始する** 、コンテキスト メニュー。</span><span class="sxs-lookup"><span data-stu-id="68521-121">Start a new instance of the **Client** project by right clicking the project in **Solution Explorer**, and selecting **Debug**, and **Start new instance** from the context menu.</span></span>  
  
5.  <span data-ttu-id="68521-122">サービスが開始されたら、クライアント ウィンドウで Enter キーを押して、クライアントからサービスにメッセージを送信します。</span><span class="sxs-lookup"><span data-stu-id="68521-122">Once the service has started, press ENTER in the client window to let the client send a message to the service.</span></span>  
  
6.  <span data-ttu-id="68521-123">最初のメッセージがサービスで処理され、サービスからクライアントに HTTP OK ステータス コードが送信されます。</span><span class="sxs-lookup"><span data-stu-id="68521-123">The first message is processed on the service, and it sends an HTTP OK status code back to the client.</span></span>  
  
7.  <span data-ttu-id="68521-124">2 番目のメッセージは失敗し、サービスからクライアントに HTTP 内部サーバー エラー ステータス コードが送信されます。これにより、<xref:System.ServiceModel.CommunicationException> がクライアントで発生します。</span><span class="sxs-lookup"><span data-stu-id="68521-124">The second message is unsuccessful, and it sends an HTTP Internal Server error status code back to the client, which raises a <xref:System.ServiceModel.CommunicationException> on the client.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="68521-125">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="68521-125">The samples may already be installed on your machine.</span></span> <span data-ttu-id="68521-126">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="68521-126">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="68521-127">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="68521-127">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="68521-128">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="68521-128">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
