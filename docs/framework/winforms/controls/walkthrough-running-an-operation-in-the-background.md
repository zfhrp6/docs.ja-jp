---
title: "チュートリアル : 操作をバックグラウンドで実行する"
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
helpviewer_keywords:
- background tasks
- forms [Windows Forms], multithreading
- forms [Windows Forms], background operations
- background threads
- BackgroundWorker class [Windows Forms], examples
- threading [Windows Forms], background operations
- background operations
ms.assetid: 1b9a4e0a-f134-48ff-a1be-c461446a31ba
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: de485eb0b9c67ee9c3c897b6521971f50aaf751c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-running-an-operation-in-the-background"></a><span data-ttu-id="7009a-102">チュートリアル : 操作をバックグラウンドで実行する</span><span class="sxs-lookup"><span data-stu-id="7009a-102">Walkthrough: Running an Operation in the Background</span></span>
<span data-ttu-id="7009a-103">完了に長い時間がかかる操作を実行しており、ユーザー インターフェイスで遅延が発生しないようにするには<xref:System.ComponentModel.BackgroundWorker> クラスを使用して別のスレッドで操作を実行できます。</span><span class="sxs-lookup"><span data-stu-id="7009a-103">If you have an operation that will take a long time to complete, and you do not want to cause delays in your user interface, you can use the <xref:System.ComponentModel.BackgroundWorker> class to run the operation on another thread.</span></span>  
  
 <span data-ttu-id="7009a-104">この例で使用するコードの完全な一覧については、次を参照してください。[する方法: バック グラウンドで操作を実行](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)です。</span><span class="sxs-lookup"><span data-stu-id="7009a-104">For a complete listing of the code used in this example, see [How to: Run an Operation in the Background](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7009a-105">実際に画面に表示されるダイアログ ボックスとメニュー コマンドは、アクティブな設定またはエディションによっては、ヘルプの説明と異なる場合があります。</span><span class="sxs-lookup"><span data-stu-id="7009a-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7009a-106">設定を変更するには、 **[ツール]** メニューの **[設定のインポートとエクスポート]** をクリックします。</span><span class="sxs-lookup"><span data-stu-id="7009a-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7009a-107">詳細については、「[Visual Studio での開発設定のカスタマイズ](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="7009a-107">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-run-an-operation-in-the-background"></a><span data-ttu-id="7009a-108">バック グラウンドで操作を実行するには</span><span class="sxs-lookup"><span data-stu-id="7009a-108">To run an operation in the background</span></span>  
  
1.  <span data-ttu-id="7009a-109">Windows フォーム デザイナーでアクティブなフォームにドラッグして 2 つ<xref:System.Windows.Forms.Button>から制御、**ツールボックス**には、フォーム、および設定、`Name`と<xref:System.Windows.Forms.Control.Text%2A>次の表に従って、ボタンのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="7009a-109">With your form active in the Windows Forms Designer, drag two <xref:System.Windows.Forms.Button> controls from the **Toolbox** to the form, and then set the `Name` and <xref:System.Windows.Forms.Control.Text%2A> properties of the buttons according to the following table.</span></span>  
  
    |<span data-ttu-id="7009a-110">ボタン</span><span class="sxs-lookup"><span data-stu-id="7009a-110">Button</span></span>|<span data-ttu-id="7009a-111">名前</span><span class="sxs-lookup"><span data-stu-id="7009a-111">Name</span></span>|<span data-ttu-id="7009a-112">テキスト</span><span class="sxs-lookup"><span data-stu-id="7009a-112">Text</span></span>|  
    |------------|----------|----------|  
    |`button1`|`startBtn`|<span data-ttu-id="7009a-113">**Start**</span><span class="sxs-lookup"><span data-stu-id="7009a-113">**Start**</span></span>|  
    |`button2`|`cancelBtn`|<span data-ttu-id="7009a-114">**キャンセル**</span><span class="sxs-lookup"><span data-stu-id="7009a-114">**Cancel**</span></span>|  
  
2.  <span data-ttu-id="7009a-115">開く、**ツールボックス**をクリックして、**コンポーネント**タブをクリックし、ドラッグ、<xref:System.ComponentModel.BackgroundWorker>コンポーネントをフォームにします。</span><span class="sxs-lookup"><span data-stu-id="7009a-115">Open the **Toolbox**, click the **Components** tab, and then drag the <xref:System.ComponentModel.BackgroundWorker> component onto your form.</span></span>  
  
     <span data-ttu-id="7009a-116">`backgroundWorker1`コンポーネントに表示されます、**コンポーネント トレイ**です。</span><span class="sxs-lookup"><span data-stu-id="7009a-116">The `backgroundWorker1` component appears in the **Component Tray**.</span></span>  
  
3.  <span data-ttu-id="7009a-117">**プロパティ**ウィンドウで、設定、<xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="7009a-117">In the **Properties** window, set the <xref:System.ComponentModel.BackgroundWorker.WorkerSupportsCancellation%2A> property to `true`.</span></span>  
  
4.  <span data-ttu-id="7009a-118">**プロパティ**ウィンドウの**イベント**ボタンをクリックし、ダブルクリック、<xref:System.ComponentModel.BackgroundWorker.DoWork>と<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベントをイベント ハンドラーを作成します。</span><span class="sxs-lookup"><span data-stu-id="7009a-118">In the **Properties** window, click on the **Events** button, and then double-click the <xref:System.ComponentModel.BackgroundWorker.DoWork> and <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> events to create event handlers.</span></span>  
  
5.  <span data-ttu-id="7009a-119">時間がかかる場合にコードを挿入、<xref:System.ComponentModel.BackgroundWorker.DoWork>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7009a-119">Insert your time-consuming code into the <xref:System.ComponentModel.BackgroundWorker.DoWork> event handler.</span></span>  
  
6.  <span data-ttu-id="7009a-120">操作に必要なすべてのパラメーターを抽出、<xref:System.ComponentModel.DoWorkEventArgs.Argument%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>パラメーター。</span><span class="sxs-lookup"><span data-stu-id="7009a-120">Extract any parameters required by the operation from the <xref:System.ComponentModel.DoWorkEventArgs.Argument%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs> parameter.</span></span>  
  
7.  <span data-ttu-id="7009a-121">計算の結果を割り当てる、<xref:System.ComponentModel.DoWorkEventArgs.Result%2A>のプロパティ、<xref:System.ComponentModel.DoWorkEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="7009a-121">Assign the result of the computation to the <xref:System.ComponentModel.DoWorkEventArgs.Result%2A> property of the <xref:System.ComponentModel.DoWorkEventArgs>.</span></span>  
  
     <span data-ttu-id="7009a-122">これができるように、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7009a-122">This is will be available to the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#2)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#2)]  
  
8.  <span data-ttu-id="7009a-123">操作の結果を取得するためのコードを挿入、<xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7009a-123">Insert code for retrieving the result of your operation in the <xref:System.ComponentModel.BackgroundWorker.RunWorkerCompleted> event handler.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#3)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#3)]  
  
9. <span data-ttu-id="7009a-124">`TimeConsumingOperation` メソッドを実装します。</span><span class="sxs-lookup"><span data-stu-id="7009a-124">Implement the `TimeConsumingOperation` method.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#4)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#4)]  
  
10. <span data-ttu-id="7009a-125">Windows フォーム デザイナーでダブルクリック`startButton`を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7009a-125">In the Windows Forms Designer, double-click `startButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
11. <span data-ttu-id="7009a-126">呼び出す、<xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A>メソッドで、<xref:System.Windows.Forms.Control.Click>イベントのハンドラーを`startButton`です。</span><span class="sxs-lookup"><span data-stu-id="7009a-126">Call the <xref:System.ComponentModel.BackgroundWorker.RunWorkerAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `startButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#5)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#5)]  
  
12. <span data-ttu-id="7009a-127">Windows フォーム デザイナーでダブルクリック`cancelButton`を作成する、<xref:System.Windows.Forms.Control.Click>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="7009a-127">In the Windows Forms Designer, double-click `cancelButton` to create the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
13. <span data-ttu-id="7009a-128">呼び出す、<xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A>メソッドで、<xref:System.Windows.Forms.Control.Click>イベントのハンドラーを`cancelButton`です。</span><span class="sxs-lookup"><span data-stu-id="7009a-128">Call the <xref:System.ComponentModel.BackgroundWorker.CancelAsync%2A> method in the <xref:System.Windows.Forms.Control.Click> event handler for `cancelButton`.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#6)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#6](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#6)]  
  
14. <span data-ttu-id="7009a-129">ファイルの上部にある、System.ComponentModel および System.Threading 名前空間をインポートします。</span><span class="sxs-lookup"><span data-stu-id="7009a-129">At the top of the file, import the System.ComponentModel and System.Threading namespaces.</span></span>  
  
     [!code-csharp[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/CS/Form1.cs#7)]
     [!code-vb[System.ComponentModel.BackgroundWorker.Example#7](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.ComponentModel.BackgroundWorker.Example/VB/Form1.vb#7)]  
  
15. <span data-ttu-id="7009a-130">ソリューションをビルド f6 キーを押してし、デバッガーの外部アプリケーションを実行するには、ctrl キーを押し-F5 キーを押します。</span><span class="sxs-lookup"><span data-stu-id="7009a-130">Press F6 to build the solution, and then press CTRL-F5 to run the application outside the debugger.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7009a-131">例外が発生、デバッガーでアプリケーションを実行する場合は F5 キーを押した場合、`TimeConsumingOperation`メソッドがキャッチされ、デバッガーによって表示されます。</span><span class="sxs-lookup"><span data-stu-id="7009a-131">If you press F5 to run the application under the debugger, the exception raised in the `TimeConsumingOperation` method is caught and displayed by the debugger.</span></span> <span data-ttu-id="7009a-132">デバッガー、外部アプリケーションを実行すると、 <xref:System.ComponentModel.BackgroundWorker> 、例外を処理し、キャッシュ内に、<xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A>のプロパティ、<xref:System.ComponentModel.RunWorkerCompletedEventArgs>です。</span><span class="sxs-lookup"><span data-stu-id="7009a-132">When you run the application outside the debugger, the <xref:System.ComponentModel.BackgroundWorker> handles the exception and caches it in the <xref:System.ComponentModel.AsyncCompletedEventArgs.Error%2A> property of the <xref:System.ComponentModel.RunWorkerCompletedEventArgs>.</span></span>  
  
1.  <span data-ttu-id="7009a-133">をクリックして、**開始**、非同期操作を実行するボタンをクリックし、をクリックして、**キャンセル**実行中の非同期操作を停止するボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="7009a-133">Click the **Start** button to run an asynchronous operation, and then click the **Cancel** button to stop a running asynchronous operation.</span></span>  
  
     <span data-ttu-id="7009a-134">各操作の結果は、<xref:System.Windows.Forms.MessageBox> に表示されます。</span><span class="sxs-lookup"><span data-stu-id="7009a-134">The outcome of each operation is displayed in a <xref:System.Windows.Forms.MessageBox>.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="7009a-135">次の手順</span><span class="sxs-lookup"><span data-stu-id="7009a-135">Next Steps</span></span>  
  
-   <span data-ttu-id="7009a-136">非同期操作の進行中に進行状況を報告するフォームを実装します。</span><span class="sxs-lookup"><span data-stu-id="7009a-136">Implement a form that reports progress as an asynchronous operation proceeds.</span></span> <span data-ttu-id="7009a-137">詳細については、次を参照してください。[する方法: バック グラウンド操作を使用してフォームを実装する](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)です。</span><span class="sxs-lookup"><span data-stu-id="7009a-137">For more information, see [How to: Implement a Form That Uses a Background Operation](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md).</span></span>  
  
-   <span data-ttu-id="7009a-138">コンポーネントの非同期パターンをサポートするクラスを実装します。</span><span class="sxs-lookup"><span data-stu-id="7009a-138">Implement a class that supports the Asynchronous Pattern for Components.</span></span> <span data-ttu-id="7009a-139">詳細については、次を参照してください。[イベント ベースの非同期パターンを実装する](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md)です。</span><span class="sxs-lookup"><span data-stu-id="7009a-139">For more information, see [Implementing the Event-based Asynchronous Pattern](../../../../docs/standard/asynchronous-programming-patterns/implementing-the-event-based-asynchronous-pattern.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7009a-140">関連項目</span><span class="sxs-lookup"><span data-stu-id="7009a-140">See Also</span></span>  
 <xref:System.ComponentModel.BackgroundWorker>  
 <xref:System.ComponentModel.DoWorkEventArgs>  
 [<span data-ttu-id="7009a-141">方法: バックグラウンド操作を使用するフォームを実装する</span><span class="sxs-lookup"><span data-stu-id="7009a-141">How to: Implement a Form That Uses a Background Operation</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-a-form-that-uses-a-background-operation.md)  
 [<span data-ttu-id="7009a-142">方法: バックグラウンドで操作を実行する</span><span class="sxs-lookup"><span data-stu-id="7009a-142">How to: Run an Operation in the Background</span></span>](../../../../docs/framework/winforms/controls/how-to-run-an-operation-in-the-background.md)  
 [<span data-ttu-id="7009a-143">BackgroundWorker コンポーネント</span><span class="sxs-lookup"><span data-stu-id="7009a-143">BackgroundWorker Component</span></span>](../../../../docs/framework/winforms/controls/backgroundworker-component.md)
