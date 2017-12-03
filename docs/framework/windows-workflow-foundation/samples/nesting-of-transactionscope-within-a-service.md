---
title: "サービス内での TransactionScope の入れ子化"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7455f2b45e47a6d72118055bd891f7c297b56483
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="nesting-of-transactionscope-within-a-service"></a><span data-ttu-id="c3321-102">サービス内での TransactionScope の入れ子化</span><span class="sxs-lookup"><span data-stu-id="c3321-102">Nesting of TransactionScope within a service</span></span>
<span data-ttu-id="c3321-103">このサンプルは、サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティ インスタンスを処理する方法を示す 2 つのシナリオで構成されます。</span><span class="sxs-lookup"><span data-stu-id="c3321-103">This sample consists of two scenarios that run showing how to handle <xref:System.Activities.Statements.TransactionScope> activity instances within a service.</span></span> <span data-ttu-id="c3321-104">トランザクションでは、まず <xref:System.Activities.Statements.TransactionScope> を使用してクライアント上に新しいトランザクションを作成し、<xref:System.ServiceModel.Activities.TransactedReceiveScope> を使用してサーバー上でトランザクションを受信し、トランザクションの有効期間のスコープを設定します。</span><span class="sxs-lookup"><span data-stu-id="c3321-104">First the transaction is initiated using the <xref:System.Activities.Statements.TransactionScope> activity to create a new transaction on the client and <xref:System.ServiceModel.Activities.TransactedReceiveScope> to receive and scope the lifetime of the transaction on the server.</span></span> <span data-ttu-id="c3321-105">サービス内の最初のシナリオでは、2 つ目の <xref:System.Activities.Statements.TransactionScope> アクティビティを実行して、サービス内で <xref:System.Activities.Statements.TransactionScope> アクティビティを入れ子にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="c3321-105">The first scenario within the service runs a secondary <xref:System.Activities.Statements.TransactionScope> activity to demonstrate the nesting of the <xref:System.Activities.Statements.TransactionScope> activities within the service.</span></span> <span data-ttu-id="c3321-106">2 番目のシナリオでは、入れ子になった <xref:System.Activities.Statements.TransactionScope> アクティビティ内でタイムアウトがどのように機能するかを示します。</span><span class="sxs-lookup"><span data-stu-id="c3321-106">The second scenario shows how time-outs are respected within the nested <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="client-application"></a><span data-ttu-id="c3321-107">クライアント アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c3321-107">Client Application</span></span>  
 <span data-ttu-id="c3321-108">クライアント アプリケーションは、<xref:System.Activities.Statements.TransactionScope> アクティビティの開始、分散トランザクション ID の出力、サーバーへのメッセージの送信、トランザクションのフロー、応答の受信、分散トランザクション ID の再出力、および完了処理を行うワークフローを実行します。</span><span class="sxs-lookup"><span data-stu-id="c3321-108">The client application runs a workflow that starts a <xref:System.Activities.Statements.TransactionScope> activity, prints the distributed transaction ID, sends a message to the server, flows the transaction, receives the reply, prints the distributed transaction ID again and completes.</span></span> <span data-ttu-id="c3321-109">クライアント アプリケーションは、このワークフローをサービス シナリオごとに 1 回だけ実行します。</span><span class="sxs-lookup"><span data-stu-id="c3321-109">It does this once for each service scenario.</span></span>  
  
## <a name="server-application"></a><span data-ttu-id="c3321-110">サーバー アプリケーション</span><span class="sxs-lookup"><span data-stu-id="c3321-110">Server Application</span></span>  
 <span data-ttu-id="c3321-111">サーバー プロジェクトは、クライアントからのメッセージをリッスンするためのエンドポイントを作成する <xref:System.ServiceModel.Activities.WorkflowServiceHost> でホストされます。</span><span class="sxs-lookup"><span data-stu-id="c3321-111">The server project is hosted in <xref:System.ServiceModel.Activities.WorkflowServiceHost>, which creates the endpoint to listen for the message from the client.</span></span> <span data-ttu-id="c3321-112">ワークフローの中心は、クライアントからフローされたトランザクションを受信し、分散トランザクション ID を出力して、2 つ目の <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティを実行する <xref:System.Activities.Statements.TransactionScope> です。</span><span class="sxs-lookup"><span data-stu-id="c3321-112">The workflow is centered on the <xref:System.ServiceModel.Activities.TransactedReceiveScope>, which receives the flowed transaction from the client, prints the distributed transaction ID and then executes a second <xref:System.Activities.Statements.TransactionScope> activity.</span></span> <span data-ttu-id="c3321-113">最初のシナリオでは、トランザクションは正常に完了します。</span><span class="sxs-lookup"><span data-stu-id="c3321-113">In the first scenario, the transaction is completed successfully.</span></span> <span data-ttu-id="c3321-114">2 番目のシナリオでは、<xref:System.Activities.Statements.TransactionScope> アクティビティの本体は 5 秒の遅延で、トランザクションのタイムアウトは 2 秒に設定されています。</span><span class="sxs-lookup"><span data-stu-id="c3321-114">In the second scenario, the body of the <xref:System.Activities.Statements.TransactionScope> activity is a five-second delay and the time-out for the transaction is set to two seconds.</span></span> <span data-ttu-id="c3321-115">トランザクションがタイムアウトすると、トランザクションは中止されます。</span><span class="sxs-lookup"><span data-stu-id="c3321-115">When the transaction times out the transaction is aborted.</span></span>  
  
#### <a name="to-run-the-sample"></a><span data-ttu-id="c3321-116">サンプルを実行するには</span><span class="sxs-lookup"><span data-stu-id="c3321-116">To run the sample</span></span>  
  
1.  <span data-ttu-id="c3321-117">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] で TransactionServiceExample.sln ソリューションを開きます。</span><span class="sxs-lookup"><span data-stu-id="c3321-117">Open the TransactionServiceExample.sln solution in [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
2.  <span data-ttu-id="c3321-118">ソリューションをビルドするには、ctrl キーと shift キーを押しながら B キーを押してまたは選択**ソリューションのビルド**から、**ビルド**メニュー。</span><span class="sxs-lookup"><span data-stu-id="c3321-118">To build the solution, press CTRL+SHIFT+B or select **Build Solution** from the **Build** menu.</span></span>  
  
3.  <span data-ttu-id="c3321-119">ビルドが成功した後、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。</span><span class="sxs-lookup"><span data-stu-id="c3321-119">Once the build has succeeded, right-click the solution and select **Set Startup Projects**.</span></span> <span data-ttu-id="c3321-120">ダイアログ ボックスから選択**マルチ スタートアップ プロジェクト**両方のプロジェクトのアクションを確認してください**開始**です。</span><span class="sxs-lookup"><span data-stu-id="c3321-120">From the dialog box, select **Multiple Startup Projects** and ensure the action for both projects is **Start**.</span></span>  
  
4.  <span data-ttu-id="c3321-121">F5 キーを押すか、選択**デバッグの開始**から、**デバッグ**メニュー。</span><span class="sxs-lookup"><span data-stu-id="c3321-121">Press F5 or select **Start Debugging** from the **Debug** menu.</span></span> <span data-ttu-id="c3321-122">または、ctrl キーを押しながら f5 キーを押してまたは選択**デバッグなしで開始**から、**デバッグ**] メニューの [デバッグなしで実行します。</span><span class="sxs-lookup"><span data-stu-id="c3321-122">Alternatively, you can press CTRL+F5 or select **Start Without Debugging** from the **Debug** menu to run without debugging.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="c3321-123">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="c3321-123">The samples may already be installed on your machine.</span></span> <span data-ttu-id="c3321-124">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="c3321-124">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="c3321-125">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="c3321-125">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="c3321-126">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="c3321-126">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
