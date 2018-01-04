---
title: "高度なエラー処理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7771b9a4d5a6c0fb4349894afd348e9dece27fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-error-handling"></a><span data-ttu-id="a9beb-102">高度なエラー処理</span><span class="sxs-lookup"><span data-stu-id="a9beb-102">Advanced Error Handling</span></span>
<span data-ttu-id="a9beb-103">このサンプルでは、[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] ルーティング サービスを示します。</span><span class="sxs-lookup"><span data-stu-id="a9beb-103">This sample demonstrates the [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] routing service.</span></span> <span data-ttu-id="a9beb-104">ルーティング サービスは、コンテンツ ベースのルーターをアプリケーションに簡単に追加できるようにする [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] コンポーネントです。</span><span class="sxs-lookup"><span data-stu-id="a9beb-104">The routing service is a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] component that makes it easy to include a content-based router in your application.</span></span> <span data-ttu-id="a9beb-105">このサンプルでは、トランザクションやその他のより複雑なメッセージ概念 (マルチキャストなど) を使用して、ルーティング サービスをエラーから自動的に回復する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="a9beb-105">This sample shows how the routing service intelligently recovers from errors, using transactions and other more complex messaging concepts such as multicasting.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="a9beb-106">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="a9beb-106">The samples may already be installed on your machine.</span></span> <span data-ttu-id="a9beb-107">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="a9beb-107">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="a9beb-108">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="a9beb-108">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="a9beb-109">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-109">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a><span data-ttu-id="a9beb-110">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="a9beb-110">Sample Details</span></span>  
 <span data-ttu-id="a9beb-111">このサンプルのルーティング サービスは、MSMQ キューからメッセージを読み取り、そのメッセージを 2 つのキュー リストにマルチキャストするように構成されています。</span><span class="sxs-lookup"><span data-stu-id="a9beb-111">In this sample, the routing service is configured to read a message from an MSMQ queue and multicast this message to two lists of queues.</span></span> <span data-ttu-id="a9beb-112">サービス キューに使用されるリストとログ キューに使用されるリストです。</span><span class="sxs-lookup"><span data-stu-id="a9beb-112">One list is used for service queues and another is used for logging queues.</span></span>  
  
 <span data-ttu-id="a9beb-113">既定では、ルーティング サービスで使用するように構成された MSMQ バインディングによってトランザクションの使用がサポートされるため、メッセージはトランザクション メッセージとなり、それぞれのリストの少なくとも 1 つのキューで受信されないと、ルーティング サービスから受信キュー (`InQ`) に、メッセージが正常にルーティングされたとは報告されません。</span><span class="sxs-lookup"><span data-stu-id="a9beb-113">Because, by default, the MSMQ binding that the routing service is configured to use supports the use of transactions, the routing service makes sure that the message is transactional and received by at least one queue in each list before reporting to the Inbound Queue (`InQ`) that the message was successfully routed.</span></span> <span data-ttu-id="a9beb-114">しがたって、両方のサービス キューまたは両方のログ キューが使用できない場合は、メッセージをルーティングできなかったこと、および受信キューで何らかの処理が必要であることが報告されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-114">Thus, in the case where both of the service queues or both of the logging queues are unavailable, the routing service reports that the message could not be routed and the inbound queue should take some action.</span></span> <span data-ttu-id="a9beb-115">この処理には、メッセージをシステム配信不能キューに移動することが含まれます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-115">This action consists of moving the message to the system dead letter queue.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="a9beb-116">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="a9beb-116">To use this sample</span></span>  
  
1.  > [!IMPORTANT]
    >  <span data-ttu-id="a9beb-117">このサンプルを実行する前に、MSMQ をインストールしてください。</span><span class="sxs-lookup"><span data-stu-id="a9beb-117">Install MSMQ before running this sample.</span></span> <span data-ttu-id="a9beb-118">MSMQ がインストールされていないと、サンプルの実行中に例外メッセージが返されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-118">If MSMQ is not installed, an exception message is returned when running the sample.</span></span> <span data-ttu-id="a9beb-119">MSMQ をインストールする手順についてはあります[をインストールするメッセージ キュー (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437)です。</span><span class="sxs-lookup"><span data-stu-id="a9beb-119">Instructions for installing MSMQ can be found at [Installing Message Queuing (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).</span></span>  
  
     <span data-ttu-id="a9beb-120">[!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] を使用して AdvancedErrorHandling.sln を開きます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-120">Using [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], open AdvancedErrorHandling.sln.</span></span>  
  
2.  <span data-ttu-id="a9beb-121">キーを押して**f5 キーを押して**または**CTRL + SHIFT + B**で[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]です。</span><span class="sxs-lookup"><span data-stu-id="a9beb-121">Press **F5** or **CTRL+SHIFT+B** in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].</span></span>  
  
    1.  <span data-ttu-id="a9beb-122">Ctrl キーと Shift キーを押しながら B キーを押してアプリケーションをビルドする場合は、./RoutingService/bin/debug/RoutingService.exe にあるアプリケーションを開始する必要があります。</span><span class="sxs-lookup"><span data-stu-id="a9beb-122">If you build the application with CTRL+SHIFT+B, you must start the application at ./RoutingService/bin/debug/RoutingService.exe.</span></span>  
  
3.  <span data-ttu-id="a9beb-123">コンソール ウィンドウで、Enter キーを押してクライアントを起動します。</span><span class="sxs-lookup"><span data-stu-id="a9beb-123">In the console window, press ENTER to start the client.</span></span>  
  
4.  <span data-ttu-id="a9beb-124">クライアントから、ケースごとに、キューに関するさまざまな統計情報が返されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-124">The client returns different statistics about the queues for each case.</span></span>  
  
    1.  <span data-ttu-id="a9beb-125">ケース 1 (エラーなし) の場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-125">The following is the output returned for case 1 (no failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  <span data-ttu-id="a9beb-126">ケース 3 (プライマリ サービス キューとプライマリ ログ キューのエラー) の場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-126">The following is the output returned for case 3 (primary service and logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  <span data-ttu-id="a9beb-127">ケース 4 (プライマリ サービス キューとプライマリおよびバックアップ ログ キューのエラー) の場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-127">The following is the output returned for case 4 (primary service queue and primary and backup logging queue failures).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  <span data-ttu-id="a9beb-128">ケース 2 (プライマリ サービス キューのエラー) の場合は、次の出力が返されます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-128">The following is the output returned for case 2 (primary service queue failure).</span></span>  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a><span data-ttu-id="a9beb-129">コードまたは App.config で構成可能</span><span class="sxs-lookup"><span data-stu-id="a9beb-129">Configurable Via Code or App.config</span></span>  
 <span data-ttu-id="a9beb-130">サンプルは、提供された時点では、App.config ファイルを使用してルーターの動作を定義するように構成されています。</span><span class="sxs-lookup"><span data-stu-id="a9beb-130">The sample ships configured to use an App.config file to define the router’s behavior.</span></span> <span data-ttu-id="a9beb-131">RoutingService\App.config ファイルの名前を別の名前に変更して認識されないようにし、RoutingService\Program.cs の `configDriven` フィールドの値を `false` に変更して、コードで定義された構成を使用することもできます。</span><span class="sxs-lookup"><span data-stu-id="a9beb-131">You can also change the name of the RoutingService\App.config file to something else so that it is not recognized and change the value of the `configDriven` field in RoutingService\Program.cs to `false` to use the configuration defined in the code.</span></span> <span data-ttu-id="a9beb-132">どちらの方法でも、ルーターの動作は同じになります。</span><span class="sxs-lookup"><span data-stu-id="a9beb-132">Either method results in the same behavior from the router.</span></span>  
  
### <a name="scenario"></a><span data-ttu-id="a9beb-133">シナリオ</span><span class="sxs-lookup"><span data-stu-id="a9beb-133">Scenario</span></span>  
 <span data-ttu-id="a9beb-134">このサンプルは、ルーティング サービスで高度なメッセージング機能 (トランザクションや受信コンテキストなど) を処理できること、およびそれらの機能を適切なエラー処理シナリオの一部として利用できることを示しています。</span><span class="sxs-lookup"><span data-stu-id="a9beb-134">This sample demonstrates that the routing service can handle advanced messaging capabilities, such as transactions and receive context, and that it can utilize these capabilities as a part of correctly handling error scenarios.</span></span>  
  
### <a name="real-world-scenario"></a><span data-ttu-id="a9beb-135">実際のシナリオ</span><span class="sxs-lookup"><span data-stu-id="a9beb-135">Real World Scenario</span></span>  
 <span data-ttu-id="a9beb-136">Contoso では、ルーティング サービスを介したトランザクションの受信を利用して、エラー状態のときでも、必要なすべてのサービスで情報を受信できるようにしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="a9beb-136">Contoso wants to utilize transactional receives through the routing service to ensure that all necessary services receive information even during error conditions.</span></span> <span data-ttu-id="a9beb-137">さらに、エラーを自動的に適切に処理し、エラー処理ロジックを利用してもメッセージを配信できない場合にはエラーが報告されるようにしたいと考えています。</span><span class="sxs-lookup"><span data-stu-id="a9beb-137">Furthermore, they would like errors to be handled correctly and automatically and failures to be reported in the case that a message is undeliverable even when error handling logic is utilized.</span></span> <span data-ttu-id="a9beb-138">そのために、計画的に特定のエンドポイントにフェールオーバーするようにルーティング サービスを構成し、必要に応じてトランザクションや受信コンテキストの作成、完了、ロールバック、中止などを行うことで、エラー状態をルーティング サービスで処理するようにしています。</span><span class="sxs-lookup"><span data-stu-id="a9beb-138">For this purpose, they configure the routing service to fail over to specific endpoints as expected and the routing service handles the error situations, which includes the creation, completion, and rollback/aborting of transactions/receive contexts as necessary.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a9beb-139">参照</span><span class="sxs-lookup"><span data-stu-id="a9beb-139">See Also</span></span>  
 [<span data-ttu-id="a9beb-140">AppFabric ホスティングと永続性のサンプル</span><span class="sxs-lookup"><span data-stu-id="a9beb-140">AppFabric Hosting and Persistence Samples</span></span>](http://go.microsoft.com/fwlink/?LinkId=193961)
