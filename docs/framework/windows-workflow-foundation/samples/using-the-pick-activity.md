---
title: "Pick アクティビティの使用"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b89be812-a247-4025-b0e3-ffb20db027a6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 01cad73bfe5e741c104a8c8e5e9d66f7564c7067
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="using-the-pick-activity"></a><span data-ttu-id="61c37-102">Pick アクティビティの使用</span><span class="sxs-lookup"><span data-stu-id="61c37-102">Using the Pick Activity</span></span>
<span data-ttu-id="61c37-103">このサンプルでは、<xref:System.Activities.Statements.Pick> アクティビティを使用する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="61c37-103">This sample demonstrates how to use the <xref:System.Activities.Statements.Pick> activity.</span></span>  
  
 <span data-ttu-id="61c37-104"><xref:System.Activities.Statements.Pick> アクティビティでは、イベント ベースの制御モデリングを提供します。</span><span class="sxs-lookup"><span data-stu-id="61c37-104">The <xref:System.Activities.Statements.Pick> activity provides event-based control modeling.</span></span> <span data-ttu-id="61c37-105">このアクティビティの動作は C# の `switch` ステートメントに似ています。`switch` ステートメントでは、その分岐のうち 1 つだけが実行されます。</span><span class="sxs-lookup"><span data-stu-id="61c37-105">It behaves similar to the C# `switch` statement, which executes only one of the branches in the `switch` statement.</span></span> <span data-ttu-id="61c37-106">ただし、値に基づいて分岐が実行される `switch` ステートメントと異なり、<xref:System.Activities.Statements.Pick> アクティビティでは、アクティビティの完了の状態に基づいて分岐を実行します。</span><span class="sxs-lookup"><span data-stu-id="61c37-106">Unlike the `switch` statement in which a branch is executed based upon on a value, the <xref:System.Activities.Statements.Pick> activity executes a branch based upon how an activity completes.</span></span>  
  
 <span data-ttu-id="61c37-107">このサンプルでは、指定した時間内にコンソールでユーザー名を入力するようユーザーに求めます。</span><span class="sxs-lookup"><span data-stu-id="61c37-107">This sample prompts a user to type in their name on the console within a given time period.</span></span> <span data-ttu-id="61c37-108">このサンプルの <xref:System.Activities.Statements.Pick> アクティビティには、ユーザーが 5 秒以内にユーザー名を入力したかどうかに基づいて実行される 2 つの分岐があります。</span><span class="sxs-lookup"><span data-stu-id="61c37-108">The <xref:System.Activities.Statements.Pick> activity in the sample has two branches that are executed based upon whether the user types in their name within 5 seconds or not.</span></span> <span data-ttu-id="61c37-109">ユーザーが 5 秒以内にユーザー名を入力した場合は、カスタムの `ReadLine` アクティビティを含む最初の分岐が実行されます。それ以外の場合は、<xref:System.Activities.Statements.Delay> アクティビティを含むもう 1 つの分岐が実行されます。</span><span class="sxs-lookup"><span data-stu-id="61c37-109">If the user types in their name within 5 seconds, the first branch is executed, which contains a custom `ReadLine` activity; otherwise the other branch is executed, which contains a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="61c37-110">コンソールでユーザー名を入力すると、そのユーザー名がコンソールに出力されます。</span><span class="sxs-lookup"><span data-stu-id="61c37-110">Once a user’s name is typed in on the console, the user’s name is printed on the console.</span></span> <span data-ttu-id="61c37-111">5 秒以内に入力しないと、操作はタイムアウトします。</span><span class="sxs-lookup"><span data-stu-id="61c37-111">If an input is not entered within 5 seconds, the operation is timed out.</span></span>  
  
## <a name="demonstrates"></a><span data-ttu-id="61c37-112">使用例</span><span class="sxs-lookup"><span data-stu-id="61c37-112">Demonstrates</span></span>  
 <span data-ttu-id="61c37-113"><xref:System.Activities.Statements.Pick> アクティビティ。</span><span class="sxs-lookup"><span data-stu-id="61c37-113"><xref:System.Activities.Statements.Pick> activity.</span></span>  
  
## <a name="discussion"></a><span data-ttu-id="61c37-114">説明</span><span class="sxs-lookup"><span data-stu-id="61c37-114">Discussion</span></span>  
 <span data-ttu-id="61c37-115">このサンプルには、デザイナー ワークフローとコード化されたワークフローがあります。</span><span class="sxs-lookup"><span data-stu-id="61c37-115">The sample includes a Designer workflow and coded workflow.</span></span>  
  
 <span data-ttu-id="61c37-116">デザイナー ワークフロー</span><span class="sxs-lookup"><span data-stu-id="61c37-116">Designer Workflow</span></span>  
 <span data-ttu-id="61c37-117">このサンプルのデザイナー バージョンでは、デザイナーでワークフローを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="61c37-117">The Designer version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="61c37-118">次のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="61c37-118">The following files are included:</span></span>  
  
-   <span data-ttu-id="61c37-119">Program.cs: サンプル ワークフローを実行する `Main` 関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="61c37-119">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="61c37-120">ReadString.cs: コンソールからの入力を読み取るカスタム アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="61c37-120">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
-   <span data-ttu-id="61c37-121">Sequence1.xaml: Pick を使用する、デザイナーで作成されたワークフローです。</span><span class="sxs-lookup"><span data-stu-id="61c37-121">Sequence1.xaml: A workflow created using the designer that uses Pick.</span></span>  
  
 <span data-ttu-id="61c37-122">コード化されたワークフロー</span><span class="sxs-lookup"><span data-stu-id="61c37-122">Coded Workflow</span></span>  
 <span data-ttu-id="61c37-123">このサンプルのコード化されたバージョンでは、デザイナーでワークフローを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="61c37-123">The coded version of the sample demonstrates how to create a workflow in the designer.</span></span> <span data-ttu-id="61c37-124">次のファイルがあります。</span><span class="sxs-lookup"><span data-stu-id="61c37-124">The following files are included:</span></span>  
  
-   <span data-ttu-id="61c37-125">Program.cs: サンプル ワークフローを実行する `Main` 関数が含まれています。</span><span class="sxs-lookup"><span data-stu-id="61c37-125">Program.cs : Includes the `Main` function that executes the sample workflow.</span></span>  
  
-   <span data-ttu-id="61c37-126">ReadString.cs: コンソールからの入力を読み取るカスタム アクティビティです。</span><span class="sxs-lookup"><span data-stu-id="61c37-126">ReadString.cs: A custom activity that reads some input from the console.</span></span>  
  
#### <a name="to-use-this-sample"></a><span data-ttu-id="61c37-127">このサンプルを使用するには</span><span class="sxs-lookup"><span data-stu-id="61c37-127">To use this sample</span></span>  
  
1.  <span data-ttu-id="61c37-128">[!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] を使用して、Pick.sln ソリューション ファイルを開きます。</span><span class="sxs-lookup"><span data-stu-id="61c37-128">Using [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], open the Pick.sln solution file.</span></span>  
  
2.  <span data-ttu-id="61c37-129">ソリューションをビルドするには、Ctrl キーと Shift キーを押しながら B キーを押します。</span><span class="sxs-lookup"><span data-stu-id="61c37-129">To build the solution, press CTRL+SHIFT+B.</span></span>  
  
3.  <span data-ttu-id="61c37-130">ソリューションを実行するには、F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="61c37-130">To run the solution, press F5.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="61c37-131">サンプルは、既にコンピューターにインストールされている場合があります。</span><span class="sxs-lookup"><span data-stu-id="61c37-131">The samples may already be installed on your machine.</span></span> <span data-ttu-id="61c37-132">続行する前に、次の (既定の) ディレクトリを確認してください。</span><span class="sxs-lookup"><span data-stu-id="61c37-132">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="61c37-133">このディレクトリが存在しない場合は、「 [.NET Framework 4 向けの Windows Communication Foundation (WCF) および Windows Workflow Foundation (WF) のサンプル](http://go.microsoft.com/fwlink/?LinkId=150780) 」にアクセスして、 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] および [!INCLUDE[wf1](../../../../includes/wf1-md.md)] のサンプルをすべてダウンロードしてください。</span><span class="sxs-lookup"><span data-stu-id="61c37-133">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) to download all [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="61c37-134">このサンプルは、次のディレクトリに格納されます。</span><span class="sxs-lookup"><span data-stu-id="61c37-134">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\Pick`