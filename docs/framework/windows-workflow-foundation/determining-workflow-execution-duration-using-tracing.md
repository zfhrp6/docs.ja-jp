---
title: "トレースを使用したワークフロー実行時間の決定"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f04ad0fd-edc7-4cbc-8979-356f2a1131c4
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acdc4f7d58eb0f5737adb59b113ea24d723d3b61
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="determining-workflow-execution-duration-using-tracing"></a><span data-ttu-id="7fd1e-102">トレースを使用したワークフロー実行時間の決定</span><span class="sxs-lookup"><span data-stu-id="7fd1e-102">Determining Workflow Execution Duration Using Tracing</span></span>
<span data-ttu-id="7fd1e-103">このトピックでは、ワークフロー トレースを使用して、正常に完了した自己ホスト型ワークフローの実行所要時間を決定する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-103">This topic demonstrates how to determine the time it takes for a successfully completed, self-hosted workflow to execute by using workflow tracing.</span></span>  
  
### <a name="to-determine-workflow-application-execution-duration-by-using-workflow-tracing"></a><span data-ttu-id="7fd1e-104">ワークフロー トレースを使用してワークフロー アプリケーションの実行時間を決定するには</span><span class="sxs-lookup"><span data-stu-id="7fd1e-104">To determine workflow application execution duration by using workflow tracing</span></span>  
  
1.  <span data-ttu-id="7fd1e-105">[!INCLUDE[vs2010](../../../includes/vs2010-md.md)] を開きます。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-105">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span>  <span data-ttu-id="7fd1e-106">選択**ファイル**、**新しい**、**プロジェクト**です。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-106">Select **File**, **New**, **Project**.</span></span>  <span data-ttu-id="7fd1e-107">**C#**、select、**ワークフロー**ノード。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-107">Under **C#**, select the **Workflow** node.</span></span>  <span data-ttu-id="7fd1e-108">選択**ワークフロー コンソール アプリケーション**テンプレートの一覧からです。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-108">Select **Workflow Console Application** from the list of templates.</span></span>  <span data-ttu-id="7fd1e-109">新しいプロジェクトの名前`WorkflowDurationTracing` をクリック**OK**です。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-109">Name the new project `WorkflowDurationTracing` and click **OK**.</span></span>  
  
2.  <span data-ttu-id="7fd1e-110">Workflow1.xaml を開きます。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-110">Open Workflow1.xaml.</span></span>  <span data-ttu-id="7fd1e-111"><xref:System.Activities.Statements.Delay> アクティビティをデザイナー画面にドラッグします。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-111">Drag a <xref:System.Activities.Statements.Delay> activity onto the designer surface.</span></span> <span data-ttu-id="7fd1e-112">00:00:10 (10 秒) という値をアクティビティの "実行時間" プロパティに割り当てます。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-112">Assign the value 00:00:10 (ten seconds) to the Duration property of the activity.</span></span>  
  
3.  <span data-ttu-id="7fd1e-113">クリックしてイベント ビューアーを開いて**開始**、**実行**、」と入力して`eventvwr.exe`です。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-113">Open Event Viewer by clicking **Start**, **Run**, and entering `eventvwr.exe`.</span></span>  
  
4.  <span data-ttu-id="7fd1e-114">ワークフロー トレースを有効にしていない場合は展開**Applications and Services Logs**、 **Microsoft**、 **Windows**、**アプリケーション サーバー-アプリケーション**.</span><span class="sxs-lookup"><span data-stu-id="7fd1e-114">If you haven’t enabled workflow tracing, expand **Applications and Services Logs**, **Microsoft**, **Windows**, **Application Server-Applications**.</span></span> <span data-ttu-id="7fd1e-115">選択**ビュー**、 **分析およびデバッグ ログ**です。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-115">Select **View**, **Show Analytic and Debug Logs**.</span></span> <span data-ttu-id="7fd1e-116">右クリック**デバッグ**選択**ログの有効化**です。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-116">Right-click **Debug** and select **Enable Log**.</span></span> <span data-ttu-id="7fd1e-117">ワークフローが実行された後にトレースを表示できるように、イベント ビューアーを開いたままにしておきます。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-117">Leave Event Viewer open so that traces can be viewed after the workflow is run.</span></span>  
  
5.  <span data-ttu-id="7fd1e-118">Ctrl + Shift + B キーを押してワークフロー アプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-118">Execute the workflow application by pressing CTRL+SHIFT+B.</span></span>  
  
6.  <span data-ttu-id="7fd1e-119">イベント ビューアーで、1009 の ID を持つ最近のイベント、および次のようなメッセージを探します。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-119">In Event Viewer, find a recent event with ID 1009 and a message similar to the following.</span></span> <span data-ttu-id="7fd1e-120">メッセージがログに記録された時刻を書き留めます。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-120">Make a note of the time that the message was logged.</span></span>  
  
 <span data-ttu-id="7fd1e-121">**Parent Activity '、DisplayName: '、InstanceId: ' スケジュール済み子アクティビティ 'WorkflowDurationTracking.Workflow1'、DisplayName: 'Workflow1'、InstanceId: '1' です。**</span><span class="sxs-lookup"><span data-stu-id="7fd1e-121">**Parent Activity '', DisplayName: '', InstanceId: '' scheduled child Activity 'WorkflowDurationTracking.Workflow1', DisplayName: 'Workflow1', InstanceId: '1'.**</span></span>  
  
7.  <span data-ttu-id="7fd1e-122">さらに、1001 の ID を持つ最近のイベント、および次のようなメッセージを探します。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-122">Find another recent event with ID 1001 and a message similar to the following.</span></span>  <span data-ttu-id="7fd1e-123">このメッセージのログに記録された値から前のメッセージの時刻を差し引いてワークフロー実行時間を決定します。この時間は約 10 秒になります。</span><span class="sxs-lookup"><span data-stu-id="7fd1e-123">Subtract the previous message time from this message’s Logged value to determine workflow execution duration, which should be around 10 seconds.</span></span>  
  
 <span data-ttu-id="7fd1e-124">**WorkflowInstance Id: ' 1bbac57b-3322-498e-9e27-8833fda3a5bf' が Closed 状態で完了しました。**</span><span class="sxs-lookup"><span data-stu-id="7fd1e-124">**WorkflowInstance Id: '1bbac57b-3322-498e-9e27-8833fda3a5bf' has completed in the Closed state.**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7fd1e-125">関連項目</span><span class="sxs-lookup"><span data-stu-id="7fd1e-125">See Also</span></span>  
 [<span data-ttu-id="7fd1e-126">ワークフロー トレース</span><span class="sxs-lookup"><span data-stu-id="7fd1e-126">Workflow Tracing</span></span>](../../../docs/framework/windows-workflow-foundation/workflow-tracing.md)  
 [<span data-ttu-id="7fd1e-127">Windows Server App Fabric の監視</span><span class="sxs-lookup"><span data-stu-id="7fd1e-127">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="7fd1e-128">アプリケーション App Fabric の監視</span><span class="sxs-lookup"><span data-stu-id="7fd1e-128">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
