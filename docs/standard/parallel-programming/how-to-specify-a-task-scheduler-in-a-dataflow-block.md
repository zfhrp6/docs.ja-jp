---
title: "方法: データフロー ブロックのタスク スケジューラを指定する"
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
- TPL dataflow library, linking to task scheduler in TPL
- Task Parallel Library, dataflows
- task scheduler, linking from TPL
ms.assetid: 27ece374-ed5b-49ef-9cec-b20db34a65e8
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 20faebc8bda3b50c4f762615d84b7a449ae61c6f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: ja-JP
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-specify-a-task-scheduler-in-a-dataflow-block"></a><span data-ttu-id="23612-102">方法: データフロー ブロックのタスク スケジューラを指定する</span><span class="sxs-lookup"><span data-stu-id="23612-102">How to: Specify a Task Scheduler in a Dataflow Block</span></span>
<span data-ttu-id="23612-103">このドキュメントでは、アプリケーションでデータ フローを使用する場合に特定のタスク スケジューラを関連付ける方法を示します。</span><span class="sxs-lookup"><span data-stu-id="23612-103">This document demonstrates how to associate a specific task scheduler when you use dataflow in your application.</span></span> <span data-ttu-id="23612-104">この例では、Windows フォーム アプリケーションの <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> クラスを使用して、リーダー タスクがアクティブである場合と、ライター タスクがアクティブである場合を示します。</span><span class="sxs-lookup"><span data-stu-id="23612-104">The example uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair?displayProperty=nameWithType> class in a Windows Forms application to show when reader tasks are active and when a writer task is active.</span></span> <span data-ttu-id="23612-105">また、<xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> メソッドを使用してデータ フロー ブロックを有効にし、ユーザー インターフェイス スレッドで実行できるようにします。</span><span class="sxs-lookup"><span data-stu-id="23612-105">It also uses the <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> method to enable a dataflow block to run on the user-interface thread.</span></span>  
  
> [!TIP]
>  <span data-ttu-id="23612-106">TPL データ フローのライブラリ (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> 名前空間) は [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] と一緒に配布されません。</span><span class="sxs-lookup"><span data-stu-id="23612-106">The TPL Dataflow Library (<xref:System.Threading.Tasks.Dataflow?displayProperty=nameWithType> namespace) is not distributed with the [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].</span></span> <span data-ttu-id="23612-107">インストールする、<xref:System.Threading.Tasks.Dataflow>名前空間でプロジェクトを開く[!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)]、選択**NuGet パッケージの管理**プロジェクト メニューのおよびオンラインで検索から、`Microsoft.Tpl.Dataflow`パッケージ。</span><span class="sxs-lookup"><span data-stu-id="23612-107">To install the <xref:System.Threading.Tasks.Dataflow> namespace, open your project in [!INCLUDE[vs_dev11_long](../../../includes/vs-dev11-long-md.md)], choose **Manage NuGet Packages** from the Project menu, and search online for the `Microsoft.Tpl.Dataflow` package.</span></span>  
  
### <a name="to-create-the-windows-forms-application"></a><span data-ttu-id="23612-108">Windows フォーム アプリケーションを作成するには</span><span class="sxs-lookup"><span data-stu-id="23612-108">To Create the Windows Forms Application</span></span>  
  
1.  <span data-ttu-id="23612-109">作成、[!INCLUDE[csprcs](../../../includes/csprcs-md.md)]または Visual Basic **Windows フォーム アプリケーション**プロジェクト。</span><span class="sxs-lookup"><span data-stu-id="23612-109">Create a [!INCLUDE[csprcs](../../../includes/csprcs-md.md)] or Visual Basic **Windows Forms Application** project.</span></span> <span data-ttu-id="23612-110">以降の手順では、プロジェクトの名前は `WriterReadersWinForms` とします。</span><span class="sxs-lookup"><span data-stu-id="23612-110">In the following steps, the project is named `WriterReadersWinForms`.</span></span>  
  
2.  <span data-ttu-id="23612-111">メイン フォーム Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) のフォーム デザイナーで、4 つの <xref:System.Windows.Forms.CheckBox> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="23612-111">On the form designer for the main form, Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]), add four <xref:System.Windows.Forms.CheckBox> controls.</span></span> <span data-ttu-id="23612-112">設定、<xref:System.Windows.Forms.Control.Text%2A>プロパティを**リーダー 1**の`checkBox1`、**リーダー 2**の`checkBox2`、**リーダー 3**の`checkBox3`、および**ライター**の`checkBox4`します。</span><span class="sxs-lookup"><span data-stu-id="23612-112">Set the <xref:System.Windows.Forms.Control.Text%2A> property to **Reader 1** for `checkBox1`, **Reader 2** for `checkBox2`, **Reader 3** for `checkBox3`, and **Writer** for `checkBox4`.</span></span> <span data-ttu-id="23612-113">コントロールごとに、<xref:System.Windows.Forms.Control.Enabled%2A> プロパティを `False` に設定します。</span><span class="sxs-lookup"><span data-stu-id="23612-113">Set the <xref:System.Windows.Forms.Control.Enabled%2A> property for each control to `False`.</span></span>  
  
3.  <span data-ttu-id="23612-114">フォームに <xref:System.Windows.Forms.Timer> コントロールを追加します。</span><span class="sxs-lookup"><span data-stu-id="23612-114">Add a <xref:System.Windows.Forms.Timer> control to the form.</span></span> <span data-ttu-id="23612-115"><xref:System.Windows.Forms.Timer.Interval%2A> プロパティを `2500` に設定します。</span><span class="sxs-lookup"><span data-stu-id="23612-115">Set the <xref:System.Windows.Forms.Timer.Interval%2A> property to `2500`.</span></span>  
  
## <a name="adding-dataflow-functionality"></a><span data-ttu-id="23612-116">データ フロー機能の追加</span><span class="sxs-lookup"><span data-stu-id="23612-116">Adding Dataflow Functionality</span></span>  
 <span data-ttu-id="23612-117">このセクションでは、アプリケーションに参加するデータ フロー ブロックを作成する方法と、各データ フロー ブロックをタスク スケジューラとを関連付ける方法について説明します。</span><span class="sxs-lookup"><span data-stu-id="23612-117">This section describes how to create the dataflow blocks that participate in the application and how to associate each one with a task scheduler.</span></span>  
  
#### <a name="to-add-dataflow-functionality-to-the-application"></a><span data-ttu-id="23612-118">アプリケーションにデータ フロー機能を追加するには</span><span class="sxs-lookup"><span data-stu-id="23612-118">To Add Dataflow Functionality to the Application</span></span>  
  
1.  <span data-ttu-id="23612-119">プロジェクトで、System.Threading.Tasks.Dataflow.dll への参照を追加します。</span><span class="sxs-lookup"><span data-stu-id="23612-119">In your project, add a reference to System.Threading.Tasks.Dataflow.dll.</span></span>  
  
2.  <span data-ttu-id="23612-120">Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) が次の `using` ステートメント ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の `Imports`) を含むことを確認します。</span><span class="sxs-lookup"><span data-stu-id="23612-120">Ensure that Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]) contains the following `using` statements (`Imports` in [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#1)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#1](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#1)]  
  
3.  <span data-ttu-id="23612-121"><xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> データ メンバーを `Form1` クラスに追加します。</span><span class="sxs-lookup"><span data-stu-id="23612-121">Add a <xref:System.Threading.Tasks.Dataflow.BroadcastBlock%601> data member to the `Form1` class.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#2)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#2](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#2)]  
  
4.  <span data-ttu-id="23612-122">`Form1` コンストラクターで、`InitializeComponent` の呼び出しの後に、<xref:System.Windows.Forms.CheckBox> オブジェクトの状態を切り替える <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="23612-122">In the `Form1` constructor, after the call to `InitializeComponent`, create an <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object that toggles the state of <xref:System.Windows.Forms.CheckBox> objects.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#3)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#3](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#3)]  
  
5.  <span data-ttu-id="23612-123">`Form1` コンストラクターで、1 つの <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> オブジェクトと 4 つの <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクト (各 <xref:System.Windows.Forms.CheckBox> オブジェクトに 1 つの <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクト) を作成します。</span><span class="sxs-lookup"><span data-stu-id="23612-123">In the `Form1` constructor, create a <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object and four <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> objects, one <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object for each <xref:System.Windows.Forms.CheckBox> object.</span></span> <span data-ttu-id="23612-124">それぞれの <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> オブジェクトに対して <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを指定します。このオブジェクトの <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> プロパティは、リーダーの場合は <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> プロパティに設定し、ライターの場合は <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> プロパティに設定します。</span><span class="sxs-lookup"><span data-stu-id="23612-124">For each <xref:System.Threading.Tasks.Dataflow.ActionBlock%601> object, specify a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ConcurrentScheduler%2A> property for the readers, and the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair.ExclusiveScheduler%2A> property for the writer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#4)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#4](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#4)]  
  
6.  <span data-ttu-id="23612-125">`Form1` コンストラクターで、<xref:System.Windows.Forms.Timer> オブジェクトを開始します。</span><span class="sxs-lookup"><span data-stu-id="23612-125">In the `Form1` constructor, start the <xref:System.Windows.Forms.Timer> object.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#5)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#5](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#5)]  
  
7.  <span data-ttu-id="23612-126">メイン フォームのフォーム デザイナーで、タイマーの <xref:System.Windows.Forms.Timer.Tick> イベントのイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="23612-126">On the form designer for the main form, create an event handler for the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
8.  <span data-ttu-id="23612-127">タイマーに <xref:System.Windows.Forms.Timer.Tick> イベントを実装します。</span><span class="sxs-lookup"><span data-stu-id="23612-127">Implement the <xref:System.Windows.Forms.Timer.Tick> event for the timer.</span></span>  
  
     [!code-csharp[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#6)]
     [!code-vb[TPLDataflow_WriterReadersWinForms#6](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#6)]  
  
 <span data-ttu-id="23612-128">`toggleCheckBox` データ フロー ブロックはユーザー インターフェイスで機能するので、この操作をユーザー インターフェイス スレッドで実行することが重要です。</span><span class="sxs-lookup"><span data-stu-id="23612-128">Because the `toggleCheckBox` dataflow block acts on the user interface, it is important that this action occur on the user-interface thread.</span></span> <span data-ttu-id="23612-129">これを実現するため、構築時にこのオブジェクトは <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> プロパティが <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType> に設定された <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> オブジェクトを提供します。</span><span class="sxs-lookup"><span data-stu-id="23612-129">To accomplish this, during construction this object provides a <xref:System.Threading.Tasks.Dataflow.ExecutionDataflowBlockOptions> object that has the <xref:System.Threading.Tasks.Dataflow.DataflowBlockOptions.TaskScheduler%2A> property set to <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="23612-130"><xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> メソッドは、現行の同期コンテキストで作業を実行する <xref:System.Threading.Tasks.TaskScheduler> オブジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="23612-130">The <xref:System.Threading.Tasks.TaskScheduler.FromCurrentSynchronizationContext%2A> method creates a <xref:System.Threading.Tasks.TaskScheduler> object that performs work on the current synchronization context.</span></span> <span data-ttu-id="23612-131">`Form1` コンストラクターはユーザー インターフェイス スレッドから呼び出されるので、`toggleCheckBox` データ フロー ブロックに対するアクションも、ユーザー インターフェイス スレッドで実行されます。</span><span class="sxs-lookup"><span data-stu-id="23612-131">Because the `Form1` constructor is called from the user-interface thread, the action for the `toggleCheckBox` dataflow block also runs on the user-interface thread.</span></span>  
  
 <span data-ttu-id="23612-132">この例では、<xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> クラスを使用していくつかのデータ フロー ブロックが同時に実行できるようにし、別の 1 つのデータ フロー ブロックが、同じ <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> オブジェクトで実行するその他すべてのデータ フロー ブロックに対して排他的に実行するようにします。</span><span class="sxs-lookup"><span data-stu-id="23612-132">This example also uses the <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> class to enable some dataflow blocks to act concurrently, and another dataflow block to act exclusive with respect to all other dataflow blocks that run on the same <xref:System.Threading.Tasks.ConcurrentExclusiveSchedulerPair> object.</span></span> <span data-ttu-id="23612-133">この手法は、複数のデータ フロー ブロックが 1 つのリソースを共有し、一部のデータ フロー ブロックがそのリソースへの排他アクセスを必要とする場合に、手動でそのリソースへのアクセスを同期する必要がなくなるため、便利です。</span><span class="sxs-lookup"><span data-stu-id="23612-133">This technique is useful when multiple dataflow blocks share a resource and some require exclusive access to that resource, because it eliminates the requirement to manually synchronize access to that resource.</span></span> <span data-ttu-id="23612-134">手動で同期する必要がなくなることで、コードの効率性が向上する可能性があります。</span><span class="sxs-lookup"><span data-stu-id="23612-134">The elimination of manual synchronization can make code more efficient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="23612-135">例</span><span class="sxs-lookup"><span data-stu-id="23612-135">Example</span></span>  
 <span data-ttu-id="23612-136">次の例は、Form1.cs ([!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)] の Form1.vb) のコード全体を示しています。</span><span class="sxs-lookup"><span data-stu-id="23612-136">The following example shows the complete code for Form1.cs (Form1.vb for [!INCLUDE[vbprvb](../../../includes/vbprvb-md.md)]).</span></span>  
  
 [!code-csharp[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/csharp/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/cs/writerreaderswinforms/form1.cs#100)]
 [!code-vb[TPLDataflow_WriterReadersWinForms#100](../../../samples/snippets/visualbasic/VS_Snippets_Misc/tpldataflow_writerreaderswinforms/vb/writerreaderswinforms/form1.vb#100)]  
  
## <a name="see-also"></a><span data-ttu-id="23612-137">関連項目</span><span class="sxs-lookup"><span data-stu-id="23612-137">See Also</span></span>  
 [<span data-ttu-id="23612-138">データフロー</span><span class="sxs-lookup"><span data-stu-id="23612-138">Dataflow</span></span>](../../../docs/standard/parallel-programming/dataflow-task-parallel-library.md)
