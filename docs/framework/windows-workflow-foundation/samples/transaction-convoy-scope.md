---
title: "トランザクション コンボイ スコープ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c9f05e59f0df6326fe3ba68e35d83e3eda880ee8
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/02/2017
---
# <a name="transaction-convoy-scope"></a><span data-ttu-id="507be-102">トランザクション コンボイ スコープ</span><span class="sxs-lookup"><span data-stu-id="507be-102">Transaction Convoy Scope</span></span>
<span data-ttu-id="507be-103">このサンプルでは、パラレルなコンボイ メッセージング アクティビティ パターンを <xref:System.ServiceModel.Activities.TransactedReceiveScope> と組み合わせて作成し、多数の操作をすべて同じトランザクションで任意の順序で行うことができるプロトコルをモデル化する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="507be-103">This sample demonstrates how to create a Parallel Convoy messaging activity pattern in conjunction with a <xref:System.ServiceModel.Activities.TransactedReceiveScope> to model a protocol where a number of operations can happen in any order all under the same transaction.</span></span> <span data-ttu-id="507be-104">また、トランザクションがサーバーにフローされないためにクライアントで使用できるトランザクションがない場合に、<xref:System.ServiceModel.Activities.TransactedReceiveScope> で自動的に新しいトランザクションを作成する方法も示します。</span><span class="sxs-lookup"><span data-stu-id="507be-104">This sample also demonstrates how a <xref:System.ServiceModel.Activities.TransactedReceiveScope> automatically creates a new transaction when one is not flowed to the server, so the client does not make use of any transactions.</span></span>  
  
 <span data-ttu-id="507be-105">このサンプルは、クライアントとサーバーを表す 2 つのワークフロー プロジェクトで構成されます。</span><span class="sxs-lookup"><span data-stu-id="507be-105">The sample consists of two workflow projects that represent the client and server.</span></span> <span data-ttu-id="507be-106">クライアント プロジェクトでは、最初にメッセージを送信してサーバー ワークフローをブートストラップするワークフローを実行します。このワークフローで、相関関係が初期化され、残りのメッセージング アクティビティのトランザクション スコープが開始されます。</span><span class="sxs-lookup"><span data-stu-id="507be-106">The client project runs a workflow that begins by sending a message to bootstrap the server workflow, which initializes a correlation and starts a transactional scope for the remainder of the messaging activities.</span></span> <span data-ttu-id="507be-107">クライアントの <xref:System.Activities.Statements.Sequence> アクティビティには、<xref:System.ServiceModel.Activities.Send> と <xref:System.ServiceModel.Activities.ReceiveReply> の最初のペアと、3 つの分岐がある <xref:System.Activities.Statements.Parallel> アクティビティが含まれます。</span><span class="sxs-lookup"><span data-stu-id="507be-107">The client <xref:System.Activities.Statements.Sequence> activity contains an initial <xref:System.ServiceModel.Activities.Send> and <xref:System.ServiceModel.Activities.ReceiveReply> pair and then a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="507be-108">各分岐で、一方向のメッセージがサーバーに送信されます。</span><span class="sxs-lookup"><span data-stu-id="507be-108">Each branch sends a one-way message to the server.</span></span> <span data-ttu-id="507be-109"><xref:System.Activities.Statements.Parallel.CompletionCondition%2A> アクティビティの <xref:System.Activities.Statements.Parallel> プロパティは、3 つすべての分岐を完了するように `false` に設定されています。</span><span class="sxs-lookup"><span data-stu-id="507be-109">The <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> property of the <xref:System.Activities.Statements.Parallel> activity is set to `false` so that all three branches complete.</span></span>  
  
 <span data-ttu-id="507be-110">サーバー ワークフローはクライアント ワークフローに似ていますが、メッセージング アクティビティが通信のサーバー側のものになり、すべての作業が同じトランザクションで実行されるように <xref:System.ServiceModel.Activities.TransactedReceiveScope> アクティビティ内に格納されています。</span><span class="sxs-lookup"><span data-stu-id="507be-110">The server workflow is similar to the client workflow except the messaging activities are oriented towards the server side of the communication and they are contained within a <xref:System.ServiceModel.Activities.TransactedReceiveScope> activity so that all work done executes under the same transaction.</span></span> <span data-ttu-id="507be-111">サーバーで最初のメッセージを受信すると、トランザクションが作成されます。トランザクションはこのスコープのアンビエント トランザクションになり、<xref:System.ServiceModel.Activities.TransactedReceiveScope> 本体のスコープ内のあらゆるアクティビティがこのトランザクションにアクセスできます。</span><span class="sxs-lookup"><span data-stu-id="507be-111">When the first message is received on the server, a transaction is created and is made ambient for the scope of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body so that any activity within this scope can access the transaction.</span></span> <span data-ttu-id="507be-112">その後、すべての受信が並行して実行されます。</span><span class="sxs-lookup"><span data-stu-id="507be-112">After this, all receives execute in parallel.</span></span> <span data-ttu-id="507be-113">並行アクティビティの完了条件の定義に従って、すべての受信が 1 回だけ実行される必要があります。</span><span class="sxs-lookup"><span data-stu-id="507be-113">All receives must execute exactly once as described by the completion condition on the parallel activity.</span></span> <span data-ttu-id="507be-114">暗黙的な永続化ポイントが <xref:System.ServiceModel.Activities.TransactedReceiveScope> 本体の末尾にあり、永続化操作も同じトランザクションで実行されます。</span><span class="sxs-lookup"><span data-stu-id="507be-114">An implicit persistence point exists at the end of the <xref:System.ServiceModel.Activities.TransactedReceiveScope> body and the persistence operation is also executed under the same transaction.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="507be-115">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="507be-115">To use this sample</span></span>  
  
1.  <span data-ttu-id="507be-116">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、ParallelConvoySample.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="507be-116">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the ParallelConvoySample.sln solution file.</span></span>  
  
2.  <span data-ttu-id="507be-117">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="507be-117">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="507be-118">どちらのプロジェクトも開始されるように設定されていることを確認します。</span><span class="sxs-lookup"><span data-stu-id="507be-118">Ensure both projects are set to start.</span></span>  
  
    1.  <span data-ttu-id="507be-119">**ソリューション エクスプ ローラー**、ソリューションを右クリックし  **スタートアップ プロジェクトの**します。</span><span class="sxs-lookup"><span data-stu-id="507be-119">In **Solution Explorer**, right-click the solution and select **Set Startup Projects**.</span></span>  
  
    2.  <span data-ttu-id="507be-120">選択**マルチ スタートアップ プロジェクト**の両方のプロジェクトのアクションに設定されていることを確認および**開始**です。</span><span class="sxs-lookup"><span data-stu-id="507be-120">Select **Multiple Startup Projects** and ensure the action for both projects is set to **Start**.</span></span>  
  
4.  <span data-ttu-id="507be-121">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="507be-121">To run the solution, press CTRL+F5.</span></span>  
  
     <span data-ttu-id="507be-122">サーバーで "`Server is running`" と出力され、サーバーの準備ができたことが示されます。</span><span class="sxs-lookup"><span data-stu-id="507be-122">The server prints `Server is running`, which indicates the server is ready.</span></span>  
  
     <span data-ttu-id="507be-123">クライアント コンソール ウィンドウで任意のキーを押してサンプルを開始します。</span><span class="sxs-lookup"><span data-stu-id="507be-123">Press any key in the client console window to start the sample.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="507be-124">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="507be-124">The samples may already be installed on your machine.</span></span> <span data-ttu-id="507be-125">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="507be-125">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="507be-126">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="507be-126">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="507be-127">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="507be-127">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`