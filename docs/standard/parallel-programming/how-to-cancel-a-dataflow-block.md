---
title: "方法: データフロー ブロックをキャンセルする"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Task Parallel Library, dataflows
- dataflow blocks, canceling in TPL
- TPL dataflow library,canceling dataflow blocks
ms.assetid: fbddda0d-da3b-4ec8-a1d6-67ab8573fcd7
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4d6fbde31cd4b4b5d0c6404b8baf23230f2bda77
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-cancel-a-dataflow-block"></a><span data-ttu-id="9d0e8-102">方法: データフロー ブロックをキャンセルする</span><span class="sxs-lookup"><span data-stu-id="9d0e8-102">How to: Cancel a Dataflow Block</span></span>
<span data-ttu-id="9d0e8-103">このドキュメントでは、アプリケーションでキャンセルを有効にする方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-103">This document demonstrates how to enable cancellation in your application.</span></span> <span data-ttu-id="9d0e8-104">この例では、Windows フォームを使用して、データフロー パイプラインで作業項目がアクティブである場所と、キャンセルの影響を示します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-104">This example uses Windows Forms to show where work items are active in a dataflow pipeline and also the effects of cancellation.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="9d0e8-105">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-105">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="9d0e8-106">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-106">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="9d0e8-107">Windows フォーム アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="9d0e8-107">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="9d0e8-108">C# または Visual Basic の **Windows フォーム アプリケーション** プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-108">Create a C# or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="9d0e8-109">以降の手順では、プロジェクトの名前は `CancellationWinForms` とします。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-109">In the following steps, the project is named `CancellationWinForms`.</span></span>  
  
2.  <span data-ttu-id="9d0e8-110">メイン フォーム Form1.cs のフォーム デザイナーで (の Form1.vb [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)])、追加、<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-110">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add a <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
3.  <span data-ttu-id="9d0e8-111">追加、<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-111">Add a <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="9d0e8-112">設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>と<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**作業項目の追加**です。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-112">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text> and the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Add Work Items**.</span></span>  
  
4.  <span data-ttu-id="9d0e8-113">1 秒あたりの追加<xref:System.Windows.Forms.ToolStripButton>コントロールを<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-113">Add a second <xref:System.Windows.Forms.ToolStripButton> control to the <xref:System.Windows.Forms.ToolStrip> control.</span></span> <span data-ttu-id="9d0e8-114">設定、<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>プロパティを<xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>、<xref:System.Windows.Forms.ToolStripItem.Text%2A>プロパティを**キャンセル**、および<xref:System.Windows.Forms.ToolStripItem.Enabled%2A>プロパティを`False`です。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-114">Set the <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> property to <xref:System.Windows.Forms.ToolStripItemDisplayStyle.Text>, the <xref:System.Windows.Forms.ToolStripItem.Text%2A> property to **Cancel**, and the <xref:System.Windows.Forms.ToolStripItem.Enabled%2A> property to `False`.</span></span>  
  
5.  <span data-ttu-id="9d0e8-115">次の 4 つの追加<xref:System.Windows.Forms.ToolStripProgressBar>オブジェクトを<xref:System.Windows.Forms.ToolStrip>コントロール。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-115">Add four <xref:System.Windows.Forms.ToolStripProgressBar> objects to the <xref:System.Windows.Forms.ToolStrip> control.</span></span>  
  
## <a name="creating-the-dataflow-pipeline"></a><span data-ttu-id="9d0e8-116">データフロー パイプラインの作成</span><span class="sxs-lookup"><span data-stu-id="9d0e8-116">Creating the Dataflow Pipeline</span></span>  
 <span data-ttu-id="9d0e8-117">このセクションでは、作業項目を処理して進行状況バーを更新するデータフロー パイプラインを作成する方法を示します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-117">This section describes how to create the dataflow pipeline that processes work items and updates the progress bars.</span></span>  
  
#### <a name="to-create-the-dataflow-pipeline"></a><span data-ttu-id="9d0e8-118">データフロー パイプラインを作成するには</span><span class="sxs-lookup"><span data-stu-id="9d0e8-118">To Create the Dataflow Pipeline</span></span>  
  
1.  <span data-ttu-id="9d0e8-119">プロジェクトで、System.Threading.Tasks.Dataflow.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="9d0e8-120">Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) が次の `using` ステートメント ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `Imports`) を含むことを確認します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_CancellationWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="9d0e8-121">`Form1` クラスの内部の型として `WorkItem` クラスを追加します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-121">Add the `WorkItem` class as an inner type of the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_CancellationWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="9d0e8-122">`Form1` クラスに次のデータ メンバーを追加します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-122">Add the following data members to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_CancellationWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="9d0e8-123">次の `CreatePipeline` メソッドを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-123">Add the following method, `CreatePipeline`, to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_CancellationWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#4)]  
  
 <span data-ttu-id="9d0e8-124">`incrementProgress` と `decrementProgress` のデータフロー ブロックはユーザー インターフェイスで機能するので、これらの操作をユーザー インターフェイス スレッドで実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-124">Because the `incrementProgress` and `decrementProgress` dataflow blocks act on the user interface, it is important that these actions occur on the user-interface thread.</span></span> <span data-ttu-id="9d0e8-125">これを実現する、構築時にこれらのオブジェクトが各提供、<xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions>を持つオブジェクトを<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A>プロパティに設定<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>です。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-125">To accomplish this, during construction these objects each provide a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="9d0e8-126"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-126">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="9d0e8-127">`Form1` コンストラクターはユーザー インターフェイス スレッドから呼び出されるので、`incrementProgress` および `decrementProgress` データフロー ブロックに対するアクションも、ユーザー インターフェイス スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-127">Because the `Form1` constructor is called from the user-interface thread, the actions for the `incrementProgress` and `decrementProgress` dataflow blocks also run on the user-interface thread.</span></span>  
  
 <span data-ttu-id="9d0e8-128">この例では設定、<xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティ、パイプラインのメンバーを作成するときにします。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-128">This example sets the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property when it constructs the members of the pipeline.</span></span> <span data-ttu-id="9d0e8-129"><xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A>プロパティが完全にデータ フロー ブロックの実行をキャンセル、ユーザーが操作をキャンセルし、次がパイプラインに多くの作業項目を追加した後、全体のパイプラインを再作成する必要があります。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-129">Because the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.CancellationToken%2A> property permanently cancels dataflow block execution, the whole pipeline must be recreated after the user cancels the operation and then wants to add more work items to the pipeline.</span></span> <span data-ttu-id="9d0e8-130">操作をキャンセルした後も他の作業を実行できるようにデータフロー ブロックをキャンセルする方法もあります。例については、「[チュートリアル: Windows フォーム アプリケーションでのデータフローの使用](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-130">For an example that demonstrates an alternative way to cancel a dataflow block so that other work can be performed after an operation is canceled, see [Walkthrough: Using Dataflow in a Windows Forms Application](../../../docs/standard/parallel-programming/walkthrough-using-dataflow-in-a-windows-forms-application.md).</span></span>  
  
## <a name="connecting-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="9d0e8-131">ユーザー インターフェイスへのデータフロー パイプラインの接続</span><span class="sxs-lookup"><span data-stu-id="9d0e8-131">Connecting the Dataflow Pipeline to the User Interface</span></span>  
 <span data-ttu-id="9d0e8-132">このセクションでは、ユーザー インターフェイスにデータフロー パイプラインを接続する方法を説明します。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-132">This section describes how to connect the dataflow pipeline to the user interface.</span></span> <span data-ttu-id="9d0e8-133">パイプラインの作成とパイプラインへの作業項目の追加は、どちらも **[作業項目の追加]** ボタンのインベント ハンドラーによって制御されます。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-133">Both creating the pipeline and adding work items to the pipeline are controlled by the event handler for the **Add Work Items** button.</span></span> <span data-ttu-id="9d0e8-134">キャンセルは **[キャンセル]** ボタンによって開始されます。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-134">Cancellation is initiated by the **Cancel** button.</span></span> <span data-ttu-id="9d0e8-135">ユーザーがこのいずれかのボタンをクリックすると、適切な操作が非同期的に開始されます。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-135">When the user clicks either of these buttons, the appropriate action is initiated in an asynchronous manner.</span></span>  
  
#### <a name="to-connect-the-dataflow-pipeline-to-the-user-interface"></a><span data-ttu-id="9d0e8-136">ユーザー インターフェイスにデータフロー パイプラインを接続するには</span><span class="sxs-lookup"><span data-stu-id="9d0e8-136">To Connect the Dataflow Pipeline to the User Interface</span></span>  
  
1.  <span data-ttu-id="9d0e8-137">メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**作業項目の追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-137">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
2.  <span data-ttu-id="9d0e8-138">実装、<xref:System.Windows.Forms.ToolStripItem.Click>イベントを**作業項目の追加**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-138">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event for the **Add Work Items** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_CancellationWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#5)]  
  
3.  <span data-ttu-id="9d0e8-139">メイン フォームのフォーム デザイナーでのイベント ハンドラーを作成、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント ハンドラー、**キャンセル**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-139">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
4.  <span data-ttu-id="9d0e8-140">実装、<xref:System.Windows.Forms.ToolStripItem.Click>のイベント ハンドラー、**キャンセル**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-140">Implement the <xref:System.Windows.Forms.ToolStripItem.Click> event handler for the **Cancel** button.</span></span>  
  
     [!code-csharp[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_CancellationWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#6)]  
  
## <a name="example"></a><span data-ttu-id="9d0e8-141">例</span><span class="sxs-lookup"><span data-stu-id="9d0e8-141">Example</span></span>  
 <span data-ttu-id="9d0e8-142">次の例は、Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) のコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-142">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_cancellationwinforms/cs/cancellationwinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_CancellationWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_cancellationwinforms/vb/cancellationwinforms/form1.vb#100)]  
  
 <span data-ttu-id="9d0e8-143">次の図は、実行中のアプリケーションを示しています。</span><span class="sxs-lookup"><span data-stu-id="9d0e8-143">The following illustration shows the running application.</span></span>  
  
 <span data-ttu-id="9d0e8-144">![Windows フォーム アプリケーション](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span><span class="sxs-lookup"><span data-stu-id="9d0e8-144">![The Windows Forms Application](../../../docs/standard/parallel-programming/media/tpldataflow-cancellation.png "TPLDataflow_Cancellation")</span></span>  
  
## <a name="robust-programming"></a><span data-ttu-id="9d0e8-145">信頼性の高いプログラミング</span><span class="sxs-lookup"><span data-stu-id="9d0e8-145">Robust Programming</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9d0e8-146">関連項目</span><span class="sxs-lookup"><span data-stu-id="9d0e8-146">See Also</span></span>  
 [<span data-ttu-id="9d0e8-147">データフロー</span><span class="sxs-lookup"><span data-stu-id="9d0e8-147">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
