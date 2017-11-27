---
title: "チュートリアル : バックグラウンド操作を使用するフォームの実装"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- threading [Windows Forms], forms
- BackgroundWorker component
- background tasks
- forms [Windows Forms], multithreading
- threading [Windows Forms], walkthroughs
- forms [Windows Forms], background operations
- threading [Windows Forms], background operations
- background operations
ms.assetid: 4691b796-9200-471a-89c3-ba4c7cc78c03
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 89a352baed4d07c3c935643e9962131a20af2802
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-a-form-that-uses-a-background-operation"></a><span data-ttu-id="fcbc4-102">チュートリアル : バックグラウンド操作を使用するフォームの実装</span><span class="sxs-lookup"><span data-stu-id="fcbc4-102">Walkthrough: Implementing a Form That Uses a Background Operation</span></span>
<span data-ttu-id="fcbc4-103">完了するには長い時間がかかる操作があると応答を停止する、ユーザー インターフェイス (UI) を設定したくない、または「ハング」しを使用できる場合、<xref:System.ComponentModel.BackgroundWorker>別のスレッドで操作を実行するクラス。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-103">If you have an operation that will take a long time to complete, and you do not want your user interface (UI) to stop responding or "hang," you can use the <xref:System.ComponentModel.BackgroundWorker> class to execute the operation on another thread.</span></span>  
  
 <span data-ttu-id="fcbc4-104">このチュートリアルを使用する方法について説明、 <xref:System.ComponentModel.BackgroundWorker> ""バック グラウンドで時間がかかる計算を実行するクラス、ユーザー インターフェイスに応答したままです。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-104">This walkthrough illustrates how to use the <xref:System.ComponentModel.BackgroundWorker> class to perform time-consuming computations "in the background," while the user interface remains responsive.</span></span>  <span data-ttu-id="fcbc4-105">このチュートリアルを完了すると、フィボナッチ数を非同期に計算するアプリケーションが作成されます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-105">When you are through, you will have an application that computes Fibonacci numbers asynchronously.</span></span> <span data-ttu-id="fcbc4-106">大きなフィボナッチ数の計算にはかなりの時間がかかることがありますが、この遅延によってメイン UI スレッドが中断されることはなく、計算中もフォームは応答性を維持します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-106">Even though computing a large Fibonacci number can take a noticeable amount of time, the main UI thread will not be interrupted by this delay, and the form will be responsive during the calculation.</span></span>  
  
 <span data-ttu-id="fcbc4-107">このチュートリアルでは、以下のタスクを行います。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-107">Tasks illustrated in this walkthrough include:</span></span>  
  
-   <span data-ttu-id="fcbc4-108">Windows ベースのアプリケーションの作成</span><span class="sxs-lookup"><span data-stu-id="fcbc4-108">Creating a Windows-based Application</span></span>  
  
-   <span data-ttu-id="fcbc4-109">作成する、<xref:System.ComponentModel.BackgroundWorker>フォーム</span><span class="sxs-lookup"><span data-stu-id="fcbc4-109">Creating a <xref:System.ComponentModel.BackgroundWorker> in Your Form</span></span>  
  
-   <span data-ttu-id="fcbc4-110">非同期イベント ハンドラーの追加</span><span class="sxs-lookup"><span data-stu-id="fcbc4-110">Adding Asynchronous Event Handlers</span></span>  
  
-   <span data-ttu-id="fcbc4-111">進行状況の報告とキャンセルのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="fcbc4-111">Adding Progress Reporting and Support for Cancellation</span></span>  
  
 <span data-ttu-id="fcbc4-112">この例で使用するコード全体については、「[方法 : バックグラウンド操作を使用するフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-112">For a complete listing of the code used in this example, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="fcbc4-113">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-113">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="fcbc4-114">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-114">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="fcbc4-115">詳細については、「 [Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-115">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="fcbc4-116">プロジェクトの作成</span><span class="sxs-lookup"><span data-stu-id="fcbc4-116">Creating the Project</span></span>  
 <span data-ttu-id="fcbc4-117">まず、プロジェクトを作成し、フォームを設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-117">The first step is to create the project and to set up the form.</span></span>  
  
#### <a name="to-create-a-form-that-uses-a-background-operation"></a><span data-ttu-id="fcbc4-118">バックグラウンド操作を使用するフォームを作成するには</span><span class="sxs-lookup"><span data-stu-id="fcbc4-118">To create a form that uses a background operation</span></span>  
  
1.  <span data-ttu-id="fcbc4-119">`BackgroundWorkerExample` という Windows ベースのアプリケーション プロジェクトを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-119">Create a Windows-based application project called `BackgroundWorkerExample`.</span></span> <span data-ttu-id="fcbc4-120">詳細については、「[方法 : Windows アプリケーション プロジェクトを作成する](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-120">For details, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).</span></span>  
  
2.  <span data-ttu-id="fcbc4-121">**ソリューション エクスプローラー**で、**[Form1]** を右クリックし、ショートカット メニューの **[名前の変更]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-121">In **Solution Explorer**, right-click **Form1** and select **Rename** from the shortcut menu.</span></span> <span data-ttu-id="fcbc4-122">ファイル名を `FibonacciCalculator` に変更します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-122">Change the file name to `FibonacciCalculator`.</span></span> <span data-ttu-id="fcbc4-123">コード要素 "`Form1`" へのすべての参照の名前を変更するかどうかをたずねられたら、**[はい]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-123">Click the **Yes** button when you are asked if you want to rename all references to the code element '`Form1`'.</span></span>  
  
3.  <span data-ttu-id="fcbc4-124">ドラッグ、<xref:System.Windows.Forms.NumericUpDown>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-124">Drag a <xref:System.Windows.Forms.NumericUpDown> control from the **Toolbox** onto the form.</span></span> <span data-ttu-id="fcbc4-125">設定、<xref:System.Windows.Forms.NumericUpDown.Minimum%2A>プロパティを`1`と<xref:System.Windows.Forms.NumericUpDown.Maximum%2A>プロパティを`91`です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-125">Set the <xref:System.Windows.Forms.NumericUpDown.Minimum%2A> property to `1` and the <xref:System.Windows.Forms.NumericUpDown.Maximum%2A> property to `91`.</span></span>  
  
4.  <span data-ttu-id="fcbc4-126">2 つ追加<xref:System.Windows.Forms.Button>フォームのコントロールです。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-126">Add two <xref:System.Windows.Forms.Button> controls to the form.</span></span>  
  
5.  <span data-ttu-id="fcbc4-127">最初の名前を変更<xref:System.Windows.Forms.Button>コントロール`startAsyncButton`設定と、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`Start Async`です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-127">Rename the first <xref:System.Windows.Forms.Button> control `startAsyncButton` and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Start Async`.</span></span> <span data-ttu-id="fcbc4-128">2 番目の名前を変更<xref:System.Windows.Forms.Button>コントロール`cancelAsyncButton`、設定と、<xref:System.Windows.Forms.Control.Text%2A>プロパティを`Cancel Async`です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-128">Rename the second <xref:System.Windows.Forms.Button> control `cancelAsyncButton`, and set the <xref:System.Windows.Forms.Control.Text%2A> property to `Cancel Async`.</span></span> <span data-ttu-id="fcbc4-129">設定の<xref:System.Windows.Forms.Control.Enabled%2A>プロパティを`false`です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-129">Set its <xref:System.Windows.Forms.Control.Enabled%2A> property to `false`.</span></span>  
  
6.  <span data-ttu-id="fcbc4-130">両方のイベント ハンドラーを作成、<xref:System.Windows.Forms.Button>コントロールの<xref:System.Windows.Forms.Control.Click>イベント。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-130">Create an event handler for both of the <xref:System.Windows.Forms.Button> controls' <xref:System.Windows.Forms.Control.Click> events.</span></span> <span data-ttu-id="fcbc4-131">詳細については、「[方法 : デザイナーを使用してイベント ハンドラーを作成する](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-131">For details, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
7.  <span data-ttu-id="fcbc4-132">ドラッグ、<xref:System.Windows.Forms.Label>から制御、**ツールボックス**をフォームに名前を変更および`resultLabel`です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-132">Drag a <xref:System.Windows.Forms.Label> control from the **Toolbox** onto the form and rename it `resultLabel`.</span></span>  
  
8.  <span data-ttu-id="fcbc4-133">ドラッグ、<xref:System.Windows.Forms.ProgressBar>から制御、**ツールボックス**フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-133">Drag a <xref:System.Windows.Forms.ProgressBar> control from the **Toolbox** onto the form.</span></span>  
  
## <a name="creating-a-backgroundworker-in-your-form"></a><span data-ttu-id="fcbc4-134">フォームでの BackgroundWorker の作成</span><span class="sxs-lookup"><span data-stu-id="fcbc4-134">Creating a BackgroundWorker in Your Form</span></span>  
 <span data-ttu-id="fcbc4-135">作成することができます、 <xref:System.ComponentModel.BackgroundWorker> 、非同期操作を使用するため、 **Windows** **フォーム デザイナー**です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-135">You can create the <xref:System.ComponentModel.BackgroundWorker> for your asynchronous operation using the **Windows** **Forms Designer**.</span></span>  
  
#### <a name="to-create-a-backgroundworker-with-the-designer"></a><span data-ttu-id="fcbc4-136">デザイナーを使用して BackgroundWorker を作成するには</span><span class="sxs-lookup"><span data-stu-id="fcbc4-136">To create a BackgroundWorker with the Designer</span></span>  
  
-   <span data-ttu-id="fcbc4-137">**コンポーネント**のタブ、**ツールボックス**、ドラッグ、<xref:System.ComponentModel.BackgroundWorker>フォーム上にします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-137">From the **Components** tab of the **Toolbox**, drag a <xref:System.ComponentModel.BackgroundWorker> onto the form.</span></span>  
  
## <a name="adding-asynchronous-event-handlers"></a><span data-ttu-id="fcbc4-138">非同期イベント ハンドラーの追加</span><span class="sxs-lookup"><span data-stu-id="fcbc4-138">Adding Asynchronous Event Handlers</span></span>  
 <span data-ttu-id="fcbc4-139">イベント ハンドラーを追加する準備が整いました、<xref:System.ComponentModel.BackgroundWorker>コンポーネントの非同期イベントです。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-139">You are now ready to add event handlers for the <xref:System.ComponentModel.BackgroundWorker> component's asynchronous events.</span></span> <span data-ttu-id="fcbc4-140">バックグラウンドで実行される時間のかかる操作 (フィボナッチ数の計算) は、これらのイベント ハンドラーのいずれかによって呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-140">The time-consuming operation that will run in the background, which computes Fibonacci numbers, is called by one of these event handlers.</span></span>  
  
#### <a name="to-implement-asynchronous-event-handlers"></a><span data-ttu-id="fcbc4-141">非同期イベント ハンドラーを実装するには</span><span class="sxs-lookup"><span data-stu-id="fcbc4-141">To implement asynchronous event handlers</span></span>  
  
1.  <span data-ttu-id="fcbc4-142">**プロパティ** ウィンドウで、<xref:System.ComponentModel.BackgroundWorker>が選択されているコンポーネントをクリックして、**イベント**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-142">In the **Properties** window, with the <xref:System.ComponentModel.BackgroundWorker> component still selected, click the **Events** button.</span></span> <span data-ttu-id="fcbc4-143">ダブルクリックして、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントをイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-143">Double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span> <span data-ttu-id="fcbc4-144">イベント ハンドラーの使用方法の詳細については、「[方法 : デザイナーを使用してイベント ハンドラーを作成する](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-144">For more information about how to use event handlers, see [How to: Create Event Handlers Using the Designer](http://msdn.microsoft.com/en-us/8461e9b8-14e8-406f-936e-3726732b23d2).</span></span>  
  
2.  <span data-ttu-id="fcbc4-145">フォームで `ComputeFibonacci` という新しいメソッドを作成します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-145">Create a new method, called `ComputeFibonacci`, in your form.</span></span> <span data-ttu-id="fcbc4-146">このメソッドがバックグラウンドで実行され、実際の処理を行います。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-146">This method does the actual work, and it will run in the background.</span></span> <span data-ttu-id="fcbc4-147">このコードは、フィボナッチ アルゴリズムの再帰的実装を示しています。これは、非常に非効率であり、数が大きくなるにつれて、完了までの所要時間が急激に増大します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-147">This code demonstrates the recursive implementation of the Fibonacci algorithm, which is notably inefficient, taking exponentially longer time to complete for larger numbers.</span></span> <span data-ttu-id="fcbc4-148">ここでは、アプリケーションで長時間の遅延が発生する可能性のある操作を示すために、このコードを使用しています。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-148">It is used here for illustrative purposes, to show an operation that can introduce long delays in your application.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#10)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#10)]
     [!code-vb[System.ComponentModel.BackgroundWorker#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#10)]  
  
3.  <span data-ttu-id="fcbc4-149"><xref:System.ComponentModel.BackgroundWorker.DoWork> 、イベント ハンドラー呼び出しを追加して、`ComputeFibonacci`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-149">In the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler, add a call to the `ComputeFibonacci` method.</span></span> <span data-ttu-id="fcbc4-150">最初のパラメーターを受け取る`ComputeFibonacci`から、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-150">Take the first parameter for `ComputeFibonacci` from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="fcbc4-151"><xref:System.ComponentModel.BackgroundWorker>と<xref:System.ComponentModel.DoWorkEventArgs>パラメーターは、進行状況レポートとキャンセルを後で使用するをサポートします。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-151">The <xref:System.ComponentModel.BackgroundWorker> and <xref:System.ComponentModel.DoWorkEventArgs> parameters will be used later for progress reporting and cancellation support.</span></span> <span data-ttu-id="fcbc4-152">戻り値を割り当てる`ComputeFibonacci`を<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-152">Assign the return value from `ComputeFibonacci` to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span> <span data-ttu-id="fcbc4-153">この結果は使用可能になります、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-153">This result will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="fcbc4-154"><xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラーを参照していません、`backgroundWorker1`これの特定のインスタンスにこのイベント ハンドラーを結合すると、変数を直接インスタンス<xref:System.ComponentModel.BackgroundWorker>です。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-154">The <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler does not reference the `backgroundWorker1` instance variable directly, as this would couple this event handler to a specific instance of <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="fcbc4-155">代わりへの参照、<xref:System.ComponentModel.BackgroundWorker>これが発生するイベントがから復元される、`sender`パラメーター。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-155">Instead, a reference to the <xref:System.ComponentModel.BackgroundWorker> that raised this event is recovered from the `sender` parameter.</span></span> <span data-ttu-id="fcbc4-156">これは、フォームが少なくとも 1 つをホストするときに重要な<xref:System.ComponentModel.BackgroundWorker>します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-156">This is important when the form hosts more than one <xref:System.ComponentModel.BackgroundWorker>.</span></span> <span data-ttu-id="fcbc4-157">内のユーザー インターフェイス オブジェクトを操作していない重要なも、<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-157">It is also important not to manipulate any user-interface objects in your <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span> <span data-ttu-id="fcbc4-158">代わりに、ユーザー インターフェイスを介しての通信、<xref:System.ComponentModel.BackgroundWorker>イベント。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-158">Instead, communicate to the user interface through the <xref:System.ComponentModel.BackgroundWorker> events.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#5)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#5)]  
  
4.  <span data-ttu-id="fcbc4-159">`startAsyncButton`コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、非同期操作を開始するコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-159">In the `startAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that starts the asynchronous operation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#13)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#13)]
     [!code-vb[System.ComponentModel.BackgroundWorker#13](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#13)]  
  
5.  <span data-ttu-id="fcbc4-160"><xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> 、イベント ハンドラーに計算の結果を割り当てる、`resultLabel`コントロール。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-160">In the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler, assign the result of the calculation to the `resultLabel` control.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#6)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#6)]  
  
## <a name="adding-progress-reporting-and-support-for-cancellation"></a><span data-ttu-id="fcbc4-161">進行状況の報告とキャンセルのサポートの追加</span><span class="sxs-lookup"><span data-stu-id="fcbc4-161">Adding Progress Reporting and Support for Cancellation</span></span>  
 <span data-ttu-id="fcbc4-162">時間のかかる非同期操作では、多くの場合、進行状況をユーザーに報告し、ユーザーが操作をキャンセルできるようにすることが望まれます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-162">For asynchronous operations that will take a long time, it is often desirable to report progress to the user and to allow the user to cancel the operation.</span></span> <span data-ttu-id="fcbc4-163"><xref:System.ComponentModel.BackgroundWorker>クラスとして、バック グラウンド操作が実行の進行状況を投稿することができますイベントを提供します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-163">The <xref:System.ComponentModel.BackgroundWorker> class provides an event that allows you to post progress as your background operation proceeds.</span></span> <span data-ttu-id="fcbc4-164">呼び出しを検出するために、ワーカーのコードを許可するフラグも用意されています。<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>され自体を中断します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-164">It also provides a flag that allows your worker code to detect a call to <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> and interrupt itself.</span></span>  
  
#### <a name="to-implement-progress-reporting"></a><span data-ttu-id="fcbc4-165">進行状況の報告を実装するには</span><span class="sxs-lookup"><span data-stu-id="fcbc4-165">To implement progress reporting</span></span>  
  
1.  <span data-ttu-id="fcbc4-166">**[プロパティ]** ウィンドウで `backgroundWorker1` を選択します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-166">In the **Properties**, window, select `backgroundWorker1`.</span></span> <span data-ttu-id="fcbc4-167"><xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> と <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> プロパティを `true` に設定します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-167">Set the <xref:System.ComponentModel.BackgroundWorker.WorkerReportsProgress%2A> and <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> properties to `true`.</span></span>  
  
2.  <span data-ttu-id="fcbc4-168">`FibonacciCalculator` フォームで 2 つの変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-168">Declare two variables in the `FibonacciCalculator` form.</span></span> <span data-ttu-id="fcbc4-169">これらの変数を使用して進行状況を追跡します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-169">These will be used to track progress.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#14)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#14)]
     [!code-vb[System.ComponentModel.BackgroundWorker#14](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#14)]  
  
3.  <span data-ttu-id="fcbc4-170"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged> イベントのイベント ハンドラーを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-170">Add an event handler for the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event.</span></span> <span data-ttu-id="fcbc4-171"><xref:System.ComponentModel.BackgroundWorker.ProgressChanged>イベント ハンドラー、update、<xref:System.Windows.Forms.ProgressBar>で、<xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A>のプロパティ、<xref:System.ComponentModel.ProgressChangedEventArgs>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-171">In the <xref:System.ComponentModel.BackgroundWorker.ProgressChanged> event handler, update the <xref:System.Windows.Forms.ProgressBar> with the <xref:System.ComponentModel.ProgressChangedEventArgs.ProgressPercentage%2A> property of the <xref:System.ComponentModel.ProgressChangedEventArgs> parameter.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#7)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#7)]  
  
#### <a name="to-implement-support-for-cancellation"></a><span data-ttu-id="fcbc4-172">キャンセルのサポートを実装するには</span><span class="sxs-lookup"><span data-stu-id="fcbc4-172">To implement support for cancellation</span></span>  
  
1.  <span data-ttu-id="fcbc4-173">`cancelAsyncButton`コントロールの<xref:System.Windows.Forms.Control.Click>イベント ハンドラー、非同期操作をキャンセルするコードを追加します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-173">In the `cancelAsyncButton` control's <xref:System.Windows.Forms.Control.Click> event handler, add the code that cancels the asynchronous operation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#4)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#4)]  
  
2.  <span data-ttu-id="fcbc4-174">`ComputeFibonacci` メソッドの次のコード フラグメントは、進行状況の報告とキャンセルのサポートを示しています。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-174">The following code fragments in the `ComputeFibonacci` method report progress and support cancellation.</span></span>  
  
     [!code-cpp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#11)]
     [!code-csharp[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#11)]
     [!code-vb[System.ComponentModel.BackgroundWorker#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#11)]  
    [!code-cpp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CPP/fibonacciform.cpp#12)]
    [!code-csharp[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/CS/fibonacciform.cs#12)]
    [!code-vb[System.ComponentModel.BackgroundWorker#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker/VB/fibonacciform.vb#12)]  
  
## <a name="checkpoint"></a><span data-ttu-id="fcbc4-175">チェックポイント</span><span class="sxs-lookup"><span data-stu-id="fcbc4-175">Checkpoint</span></span>  
 <span data-ttu-id="fcbc4-176">この時点で、フィボナッチ電卓アプリケーションをコンパイルして実行できます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-176">At this point, you can compile and run the Fibonacci Calculator application.</span></span>  
  
#### <a name="to-test-your-project"></a><span data-ttu-id="fcbc4-177">プロジェクトをテストするには</span><span class="sxs-lookup"><span data-stu-id="fcbc4-177">To test your project</span></span>  
  
-   <span data-ttu-id="fcbc4-178">F5 キーを押してアプリケーションをコンパイルし、実行します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-178">Press F5 to compile and run the application.</span></span>  
  
     <span data-ttu-id="fcbc4-179">計算の実行中は、バック グラウンドで表示されます、<xref:System.Windows.Forms.ProgressBar>完了するまで計算の進行状況を表示します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-179">While the calculation is running in the background, you will see the <xref:System.Windows.Forms.ProgressBar> displaying the progress of the calculation toward completion.</span></span> <span data-ttu-id="fcbc4-180">また、保留中の操作をキャンセルすることもできます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-180">You can also cancel the pending operation.</span></span>  
  
     <span data-ttu-id="fcbc4-181">数値が小さい場合、計算に時間はかかりませんが、数値が大きくなると、大幅な遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-181">For small numbers, the calculation should be very fast, but for larger numbers, you should see a noticeable delay.</span></span> <span data-ttu-id="fcbc4-182">30 以上の値を入力した場合、コンピューターの速度によっては数秒の遅延が発生します。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-182">If you enter a value of 30 or greater, you should see a delay of several seconds, depending on the speed of your computer.</span></span> <span data-ttu-id="fcbc4-183">値が 40 を超えると、計算が終了するまでに数分から数時間かかることがあります。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-183">For values greater than 40, it may take minutes or hours to finish the calculation.</span></span> <span data-ttu-id="fcbc4-184">電卓が大きなフィボナッチ数を計算している間も、フォームの移動、最小化、最大化を自由に行うことができ、フォームを閉じることもできます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-184">While the calculator is busy computing a large Fibonacci number, notice that you can freely move the form around, minimize, maximize, and even dismiss it.</span></span> <span data-ttu-id="fcbc4-185">これは、メイン UI スレッドが計算の終了を待機していないためです。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-185">This is because the main UI thread is not waiting for the calculation to finish.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="fcbc4-186">次の手順</span><span class="sxs-lookup"><span data-stu-id="fcbc4-186">Next Steps</span></span>  
 <span data-ttu-id="fcbc4-187">使用するフォームを実装している、<xref:System.ComponentModel.BackgroundWorker>バック グラウンドで計算を実行するためのコンポーネントの非同期操作の他の使用法を調べることができます。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-187">Now that you have implemented a form that uses a <xref:System.ComponentModel.BackgroundWorker> component to execute a computation in the background, you can explore other possibilities for asynchronous operations:</span></span>  
  
-   <span data-ttu-id="fcbc4-188">複数回使用<xref:System.ComponentModel.BackgroundWorker>並行処理のいくつかのオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-188">Use multiple <xref:System.ComponentModel.BackgroundWorker> objects for several simultaneous operations.</span></span>  
  
-   <span data-ttu-id="fcbc4-189">マルチスレッド アプリケーションをデバッグする方法については、「[方法 : [スレッド] ウィンドウを使用する](/visualstudio/debugger/how-to-use-the-threads-window)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-189">To debug your multithreaded application, see [How to: Use the Threads Window](/visualstudio/debugger/how-to-use-the-threads-window).</span></span>  
  
-   <span data-ttu-id="fcbc4-190">非同期プログラミング モデルをサポートする独自のコンポーネントを実装する。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-190">Implement your own component that supports the asynchronous programming model.</span></span> <span data-ttu-id="fcbc4-191">詳細については、「[イベント ベースの非同期パターンの概要](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-191">For more information, see [Event-based Asynchronous Pattern Overview](../../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-overview.md).</span></span>  
  
    > [!CAUTION]
    >  <span data-ttu-id="fcbc4-192">どのような種類のマルチスレッドを使用している場合でも、非常に深刻で複雑なバグを引き起こしてしまう可能性があります。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-192">When using multithreading of any sort, you potentially expose yourself to very serious and complex bugs.</span></span> <span data-ttu-id="fcbc4-193">マルチスレッドを使用するソリューションを実装する前に、「[マネージ スレッド処理の実施](../../../../docs/standard/threading/managed-threading-best-practices.md)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="fcbc4-193">Consult the [Managed Threading Best Practices](../../../../docs/standard/threading/managed-threading-best-practices.md) before implementing any solution that uses multithreading.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fcbc4-194">関連項目</span><span class="sxs-lookup"><span data-stu-id="fcbc4-194">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 [<span data-ttu-id="fcbc4-195">マネージ スレッド処理の実施</span><span class="sxs-lookup"><span data-stu-id="fcbc4-195">Managed Threading Best Practices</span></span>](../../../../docs/standard/threading/managed-threading-best-practices.md)  
 [<span data-ttu-id="fcbc4-196">コンポーネントのマルチスレッド</span><span class="sxs-lookup"><span data-stu-id="fcbc4-196">Multithreading in Components</span></span>](http://msdn.microsoft.com/library/2fc31e68-fb71-4544-b654-0ce720478779)  
 [<span data-ttu-id="fcbc4-197">NOT IN BUILD: Visual Basic でのマルチ スレッド</span><span class="sxs-lookup"><span data-stu-id="fcbc4-197">NOT IN BUILD: Multithreading in Visual Basic</span></span>](http://msdn.microsoft.com/en-us/c731a50c-09c1-4468-9646-54c86b75d269)  
 [<span data-ttu-id="fcbc4-198">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="fcbc4-198">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="fcbc4-199">チュートリアル: 操作をバックグラウンドで実行する</span><span class="sxs-lookup"><span data-stu-id="fcbc4-199">Walkthrough: Running an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/walkthrough-running-an-operation-in-the-background.md)  
 [<span data-ttu-id="fcbc4-200">BackgroundWorker コンポーネント</span><span class="sxs-lookup"><span data-stu-id="fcbc4-200">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
