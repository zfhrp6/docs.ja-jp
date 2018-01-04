---
title: "FlowChart と Pick の組み合わせを使用する StateMachine シナリオ"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 88d81395-f7a3-41d8-8439-20a425c538a6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 39ae1be025e3b888fff8b46ebbc45832c218dda7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="statemachine-scenario-using-a-combination-of-flowchart-and-pick"></a><span data-ttu-id="43ebe-102">FlowChart と Pick の組み合わせを使用する StateMachine シナリオ</span><span class="sxs-lookup"><span data-stu-id="43ebe-102">StateMachine Scenario Using a Combination of FlowChart and Pick</span></span>
<span data-ttu-id="43ebe-103">このサンプルでは、<xref:System.Activities.Statements.Flowchart> アクティビティと <xref:System.Activities.Statements.Pick> アクティビティを組み合わせて簡単なストップウォッチ シナリオを実装する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-103">This sample demonstrates how to implement a simple stopwatch scenario using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span> <span data-ttu-id="43ebe-104">このサンプルでは、Pick アクティビティ内で Receive と Send を使用して、ストップウォッチ イベントをリッスンします。</span><span class="sxs-lookup"><span data-stu-id="43ebe-104">It uses Receive and Send within the Pick activity to listen for stopwatch events.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43ebe-105">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="43ebe-105">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43ebe-106">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43ebe-106">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43ebe-107">このディレクトリが存在しない場合は、ダウンロード ページに移動して、すべての [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] サンプルおよび [!INCLUDE[wf1](../../../../includes/wf1-md.md)] サンプルをダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="43ebe-107">If this directory does not exist, go to (download page) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43ebe-108">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-108">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`  
  
## <a name="sample-details"></a><span data-ttu-id="43ebe-109">サンプルの詳細</span><span class="sxs-lookup"><span data-stu-id="43ebe-109">Sample Details</span></span>  
 <span data-ttu-id="43ebe-110">次の表に、このサンプルのプロジェクトを示します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-110">The following table lists the projects in this sample.</span></span>  
  
|<span data-ttu-id="43ebe-111">プロジェクト名</span><span class="sxs-lookup"><span data-stu-id="43ebe-111">Project Name</span></span>|<span data-ttu-id="43ebe-112">説明</span><span class="sxs-lookup"><span data-stu-id="43ebe-112">Description</span></span>|  
|-|-|  
|<span data-ttu-id="43ebe-113">StopWatchService</span><span class="sxs-lookup"><span data-stu-id="43ebe-113">StopWatchService</span></span>|<span data-ttu-id="43ebe-114">このプロジェクトには、<xref:System.Activities.Statements.Flowchart> アクティビティと <xref:System.Activities.Statements.Pick> アクティビティを組み合わせて使用するストップウォッチ サンプルのステート マシンの実装が含まれます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-114">This project contains the implementation of a state machine for the stopwatch sample using a combination of the <xref:System.Activities.Statements.Flowchart> and <xref:System.Activities.Statements.Pick> activities.</span></span><br /><br /> <span data-ttu-id="43ebe-115"><xref:System.Activities.Statements.Pick> アクティビティには、<xref:System.Activities.Statements.PickBranch>、<xref:System.Activities.Statements.Pick.Branches%2A>、および `GetStart` の各イベントをリッスンする 3 つの `GetStop` ステートメントが `GetOff` プロパティ内にあります。</span><span class="sxs-lookup"><span data-stu-id="43ebe-115">The <xref:System.Activities.Statements.Pick> activity has 3 <xref:System.Activities.Statements.PickBranch> statements within the <xref:System.Activities.Statements.Pick.Branches%2A> property that listen for `GetStart`, `GetStop` and `GetOff` events.</span></span> <span data-ttu-id="43ebe-116">受信イベントに基づいて、分岐のいずれかのトリガーがアクティブになり、対応する <xref:System.Activities.Statements.PickBranch.Action%2A> が起動されます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-116">Based on the incoming event, the triggers for one of the branches activate and the corresponding <xref:System.Activities.Statements.PickBranch.Action%2A> is triggered.</span></span> <span data-ttu-id="43ebe-117"><xref:System.Activities.Statements.PickBranch.Action%2A> プロパティには、遷移が正当な遷移であるかどうかを評価する <xref:System.Activities.Statements.Switch%601> ステートメントがあります。正当な遷移の場合、`currentState` プロパティが遷移中の状態に更新され、クライアントに送信されます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-117">In the <xref:System.Activities.Statements.PickBranch.Action%2A> property, there is a <xref:System.Activities.Statements.Switch%601> statement that evaluates whether the transition is a legitimate transition and if it is, the `currentState` property is updated to the transitioning state and sent to the client.</span></span><br /><br /> <span data-ttu-id="43ebe-118"><xref:System.Activities.Statements.FlowDecision> の最後にある <xref:System.Activities.Statements.Flowchart> アクティビティは、`currentState` プロパティを評価して、終了状態であるかどうかを確認します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-118">The <xref:System.Activities.Statements.FlowDecision> activity at the end of the <xref:System.Activities.Statements.Flowchart> evaluates the `currentState` property to determine whether the state is terminal.</span></span> <span data-ttu-id="43ebe-119">終了状態の場合、ワークフローは終了します。それ以外の場合は、<xref:System.Activities.Statements.Pick> アクティビティの先頭に戻ります。このアクティビティでは、ワークフローは他のストップウォッチ イベントを待機します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-119">If it is, the workflow ends; otherwise control loops back to the start of the <xref:System.Activities.Statements.Pick> activity where the workflow waits for more stopwatch events.</span></span>|  
|<span data-ttu-id="43ebe-120">StopWatchClient</span><span class="sxs-lookup"><span data-stu-id="43ebe-120">StopWatchClient</span></span>|<span data-ttu-id="43ebe-121">このプロジェクトは、簡単な Send アクティビティまたは Receive アクティビティを組み合わせてさまざまなストップウォッチ イベントを送信する簡単なシーケンシャル ワークフロー コンソール アプリケーションです。</span><span class="sxs-lookup"><span data-stu-id="43ebe-121">This is a simple sequential workflow console application that sends various stopwatch events with simple Send or Receive activity combinations.</span></span>|  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="43ebe-122">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="43ebe-122">To use this sample</span></span>  
  
1.  <span data-ttu-id="43ebe-123">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、StateMachineWithPick.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-123">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open StateMachineWithPick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="43ebe-124">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-124">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="43ebe-125">StopWatchService.exe を開始[!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)].exe ファイルを右クリックしを選択すると、管理者として**管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="43ebe-125">Start the StopWatchService.exe from [!INCLUDE[fileExplorer](../../../../includes/fileexplorer-md.md)] as an administrator by right clicking the .exe file and selecting **Run as administrator**.</span></span>  
  
    1.  <span data-ttu-id="43ebe-126">StateMachineWithPick\CS\StopWatchService\bin\Debug フォルダーに移動します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-126">Navigate to the StateMachineWithPick\CS\StopWatchService\bin\Debug folder.</span></span>  
  
    2.  <span data-ttu-id="43ebe-127">StopWatchService.exe ファイルを右クリックし **管理者として実行**です。</span><span class="sxs-lookup"><span data-stu-id="43ebe-127">Right-click the StopWatchService.exe file and select **Run as administrator**.</span></span>  
  
4.  <span data-ttu-id="43ebe-128">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] 内から StopWatchClient クライアント アプリケーションを開始します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-128">Start the StopWatchClient client application from within [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].</span></span>  
  
    1.  <span data-ttu-id="43ebe-129">**ソリューション エクスプ ローラー**、select、 **StopWatchClient**プロジェクトを右クリックして**スタートアップ プロジェクトとして設定**です。</span><span class="sxs-lookup"><span data-stu-id="43ebe-129">In **Solution Explorer**, select the **StopWatchClient** project and right-click **Set as StartUp Project**.</span></span>  
  
    2.  <span data-ttu-id="43ebe-130">ソリューションを実行するには、Ctrl キーを押しながら F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="43ebe-130">To run the solution, press CTRL+F5.</span></span>  
  
5.  <span data-ttu-id="43ebe-131">状態遷移を確認するには、StopWatchService.exe のコンソール ウィンドウに切り替えます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-131">Switch back to the console window for the StopWatchService.exe to view the state transitions.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="43ebe-132">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="43ebe-132">The samples may already be installed on your machine.</span></span> <span data-ttu-id="43ebe-133">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="43ebe-133">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="43ebe-134">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="43ebe-134">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="43ebe-135">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="43ebe-135">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\StateMachineWithPick`