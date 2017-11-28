---
title: "チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装"
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
- data [Windows Forms], managing large data sets
- DataGridView control [Windows Forms], virtual mode
- virtual mode [Windows Forms], walkthroughs
- DataGridView control [Windows Forms], large data sets
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 74eb5276-5ab8-4ce0-8005-dae751d85f7c
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 31806d3ed13776e26634914b48bc887297ea4dab
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="walkthrough-implementing-virtual-mode-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="333d1-102">チュートリアル : Windows フォーム DataGridView コントロールでの仮想モードの実装</span><span class="sxs-lookup"><span data-stu-id="333d1-102">Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="333d1-103">非常に大量の表形式データを表示する場合、<xref:System.Windows.Forms.DataGridView>コントロールを設定できます、<xref:System.Windows.Forms.DataGridView.VirtualMode%2A>プロパティを`true`と明示的にそのデータ ストアとコントロールの相互作用を管理します。</span><span class="sxs-lookup"><span data-stu-id="333d1-103">When you want to display very large quantities of tabular data in a <xref:System.Windows.Forms.DataGridView> control, you can set the <xref:System.Windows.Forms.DataGridView.VirtualMode%2A> property to `true` and explicitly manage the control's interaction with its data store.</span></span> <span data-ttu-id="333d1-104">このような状況で、コントロールのパフォーマンスを微調整できます。</span><span class="sxs-lookup"><span data-stu-id="333d1-104">This lets you fine-tune the performance of the control in this situation.</span></span>  
  
 <span data-ttu-id="333d1-105"><xref:System.Windows.Forms.DataGridView>コントロールには、カスタム データ ストアとの対話を処理できるいくつかのイベントが用意されています。</span><span class="sxs-lookup"><span data-stu-id="333d1-105">The <xref:System.Windows.Forms.DataGridView> control provides several events that you can handle to interact with a custom data store.</span></span> <span data-ttu-id="333d1-106">このチュートリアルでは、これらのイベント ハンドラーを実装するプロセスを説明します。</span><span class="sxs-lookup"><span data-stu-id="333d1-106">This walkthrough guides you through the process of implementing these event handlers.</span></span> <span data-ttu-id="333d1-107">このトピックのコード例では、わかりやすくするための非常に単純なデータ ソースを使用します。</span><span class="sxs-lookup"><span data-stu-id="333d1-107">The code example in this topic uses a very simple data source for illustration purposes.</span></span> <span data-ttu-id="333d1-108">実稼働設定をキャッシュ内に表示し、処理する必要がある行のみをロードするは通常<xref:System.Windows.Forms.DataGridView>とやり取りして、キャッシュを更新するイベントです。</span><span class="sxs-lookup"><span data-stu-id="333d1-108">In a production setting, you will typically load only the rows you need to display into a cache, and handle <xref:System.Windows.Forms.DataGridView> events to interact with and update the cache.</span></span> <span data-ttu-id="333d1-109">詳細については、次を参照してください[Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みで仮想モードの実装。](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span><span class="sxs-lookup"><span data-stu-id="333d1-109">For more information, see [Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)</span></span>  
  
 <span data-ttu-id="333d1-110">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: Windows フォーム DataGridView コントロールで仮想モードを実装する](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="333d1-110">To copy the code in this topic as a single listing, see [How to: Implement Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="333d1-111">フォームの作成</span><span class="sxs-lookup"><span data-stu-id="333d1-111">Creating the Form</span></span>  
  
#### <a name="to-implement-virtual-mode"></a><span data-ttu-id="333d1-112">仮想モードを実装するには</span><span class="sxs-lookup"><span data-stu-id="333d1-112">To implement virtual mode</span></span>  
  
1.  <span data-ttu-id="333d1-113">派生するクラスを作成する<xref:System.Windows.Forms.Form>が含まれています、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="333d1-113">Create a class that derives from <xref:System.Windows.Forms.Form> and contains a <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="333d1-114">次のコードには、基本的な初期化が含まれています。</span><span class="sxs-lookup"><span data-stu-id="333d1-114">The following code contains some basic initialization.</span></span> <span data-ttu-id="333d1-115">後の手順で使用されるいくつかの変数を宣言して、提供、`Main`メソッド、およびクラス コンス トラクターでの単純なフォーム レイアウトを提供します。</span><span class="sxs-lookup"><span data-stu-id="333d1-115">It declares some variables that will be used in later steps, provides a `Main` method, and provides a simple form layout in the class constructor.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#001)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#001)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#001](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#001)]  
    [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#002)]
    [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#002)]
    [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#002](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#002)]  
  
2.  <span data-ttu-id="333d1-116">フォームの用のハンドラーを実装<xref:System.Windows.Forms.Form.Load>を初期化するイベント、<xref:System.Windows.Forms.DataGridView>を制御し、サンプルの値を使用してデータ ストアを追加します。</span><span class="sxs-lookup"><span data-stu-id="333d1-116">Implement a handler for your form's <xref:System.Windows.Forms.Form.Load> event that initializes the <xref:System.Windows.Forms.DataGridView> control and populates the data store with sample values.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#110)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#110)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#110](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#110)]  
  
3.  <span data-ttu-id="333d1-117">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CellValueNeeded>データ ストアから要求されたセルの値を取得するイベントまたは`Customer`現在編集中のオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="333d1-117">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValueNeeded> event that retrieves the requested cell value from the data store or the `Customer` object currently in edit.</span></span>  
  
     <span data-ttu-id="333d1-118">このイベントが発生するたびに、<xref:System.Windows.Forms.DataGridView>コントロールがセルを描画する必要があります。</span><span class="sxs-lookup"><span data-stu-id="333d1-118">This event occurs whenever the <xref:System.Windows.Forms.DataGridView> control needs to paint a cell.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#120)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#120)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#120)]  
  
4.  <span data-ttu-id="333d1-119">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CellValuePushed>で編集されたセル値を格納するイベント、`Customer`編集された行を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="333d1-119">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CellValuePushed> event that stores an edited cell value in the `Customer` object representing the edited row.</span></span> <span data-ttu-id="333d1-120">このイベントは、ユーザーがセル値の変更をコミットするたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="333d1-120">This event occurs whenever the user commits a cell value change.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#130)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#130](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#130)]  
  
5.  <span data-ttu-id="333d1-121">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.NewRowNeeded>新たに作成するイベント`Customer`を新しく作成された行を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="333d1-121">Implement a handler for the <xref:System.Windows.Forms.DataGridView.NewRowNeeded> event that creates a new `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="333d1-122">このイベントは、ユーザーが新しいレコードの行を入力するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="333d1-122">This event occurs whenever the user enters the row for new records.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#140)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#140)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#140)]  
  
6.  <span data-ttu-id="333d1-123">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.RowValidated>新しいまたは変更された行をデータ ストアに保存するイベントです。</span><span class="sxs-lookup"><span data-stu-id="333d1-123">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowValidated> event that saves new or modified rows to the data store.</span></span>  
  
     <span data-ttu-id="333d1-124">このイベントは、ユーザーが、現在の行を変更するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="333d1-124">This event occurs whenever the user changes the current row.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#150)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#150)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#150](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#150)]  
  
7.  <span data-ttu-id="333d1-125">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベントを示すかどうか、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>イベントは、ユーザーが ESC キーを押して編集モードで 2 回または 1 回は編集モードの外部で行バージョンを再設定を示すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="333d1-125">Implement a handler for the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event that indicates whether the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event will occur when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span>  
  
     <span data-ttu-id="333d1-126">既定では、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>しない限り、現在の行内のセルが変更されたときに、行バージョンを再設定時に発生、<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>プロパティに設定されている`true`で、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="333d1-126">By default, <xref:System.Windows.Forms.DataGridView.CancelRowEdit> occurs upon row reversion when any cells in the current row have been modified unless the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property is set to `true` in the <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span> <span data-ttu-id="333d1-127">このイベントは、実行時にコミットのスコープを決定する場合に便利です。</span><span class="sxs-lookup"><span data-stu-id="333d1-127">This event is useful when the commit scope is determined at run time.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#160)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#160)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#160](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#160)]  
  
8.  <span data-ttu-id="333d1-128">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.CancelRowEdit>の値を破棄するイベント、`Customer`現在の行を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="333d1-128">Implement a handler for the <xref:System.Windows.Forms.DataGridView.CancelRowEdit> event that discards the values of the `Customer` object representing the current row.</span></span>  
  
     <span data-ttu-id="333d1-129">このイベントは、ユーザーが ESC キーを押して編集モードで 2 回または 1 回は編集モードの外部で行バージョンを再設定を示すときに発生します。</span><span class="sxs-lookup"><span data-stu-id="333d1-129">This event occurs when the user signals row reversion by pressing ESC twice in edit mode or once outside of edit mode.</span></span> <span data-ttu-id="333d1-130">このイベントは、現在の行のセルが修正されていない場合、またはの値、<xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType>プロパティに設定された`false`で、<xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>イベント ハンドラー。</span><span class="sxs-lookup"><span data-stu-id="333d1-130">This event does not occur if no cells in the current row have been modified or if the value of the <xref:System.Windows.Forms.QuestionEventArgs.Response%2A?displayProperty=nameWithType> property has been set to `false` in a <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded> event handler.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#170)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#170)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#170](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#170)]  
  
9. <span data-ttu-id="333d1-131">ハンドラーを実装、<xref:System.Windows.Forms.DataGridView.UserDeletingRow>既存を削除するイベント`Customer`データ ストアからオブジェクトまたは破棄され、保存されていない`Customer`を新しく作成された行を表すオブジェクト。</span><span class="sxs-lookup"><span data-stu-id="333d1-131">Implement a handler for the <xref:System.Windows.Forms.DataGridView.UserDeletingRow> event that deletes an existing `Customer` object from the data store or discards an unsaved `Customer` object representing a newly created row.</span></span>  
  
     <span data-ttu-id="333d1-132">このイベントは、ユーザーは、行ヘッダーをクリックして、DEL キーを押して行を削除するたびに発生します。</span><span class="sxs-lookup"><span data-stu-id="333d1-132">This event occurs whenever the user deletes a row by clicking a row header and pressing the DELETE key.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#180)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#180)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#180](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#180)]  
  
10. <span data-ttu-id="333d1-133">単純な実装`Customers`このコード例で使用されるデータ項目を表すクラス。</span><span class="sxs-lookup"><span data-stu-id="333d1-133">Implement a simple `Customers` class to represent the data items used by this code example.</span></span>  
  
     [!code-cpp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CPP/virtualmode.cpp#200)]
     [!code-csharp[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/CS/virtualmode.cs#200)]
     [!code-vb[System.Windows.Forms.DataGridView.VirtualMode#200](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.VirtualMode/VB/virtualmode.vb#200)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="333d1-134">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="333d1-134">Testing the Application</span></span>  
 <span data-ttu-id="333d1-135">フォームをテストして、期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="333d1-135">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="333d1-136">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="333d1-136">To test the form</span></span>  
  
-   <span data-ttu-id="333d1-137">アプリケーションをコンパイルして実行します。</span><span class="sxs-lookup"><span data-stu-id="333d1-137">Compile and run the application.</span></span>  
  
     <span data-ttu-id="333d1-138">表示されます、<xref:System.Windows.Forms.DataGridView>コントロールが次の 3 つの顧客レコードを格納します。</span><span class="sxs-lookup"><span data-stu-id="333d1-138">You will see a <xref:System.Windows.Forms.DataGridView> control populated with three customer records.</span></span> <span data-ttu-id="333d1-139">行の複数のセルの値を変更し、編集モードで 2 回クリック 1 回、および元の値に行全体を戻すには編集モードの外部では、esc キーを押してできます。</span><span class="sxs-lookup"><span data-stu-id="333d1-139">You can modify the values of multiple cells in a row and press ESC twice in edit mode and once outside of edit mode to revert the entire row to its original values.</span></span> <span data-ttu-id="333d1-140">変更、追加、または、コントロール内の行を削除するときに`Customer`データ ストア内のオブジェクトの変更、追加、または同時に削除します。</span><span class="sxs-lookup"><span data-stu-id="333d1-140">When you modify, add, or delete rows in the control, `Customer` objects in the data store are modified, added, or deleted as well.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="333d1-141">次の手順</span><span class="sxs-lookup"><span data-stu-id="333d1-141">Next Steps</span></span>  
 <span data-ttu-id="333d1-142">このアプリケーションでの仮想モードを実装する必要がありますを処理するイベントの基本を理解、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="333d1-142">This application gives you a basic understanding of the events you must handle to implement virtual mode in the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="333d1-143">さまざまな方法で、この基本的なアプリケーションを改善することができます。</span><span class="sxs-lookup"><span data-stu-id="333d1-143">You can improve this basic application in a number of ways:</span></span>  
  
-   <span data-ttu-id="333d1-144">外部データベースから値をキャッシュするデータ ストアを実装します。</span><span class="sxs-lookup"><span data-stu-id="333d1-144">Implement a data store that caches values from an external database.</span></span> <span data-ttu-id="333d1-145">キャッシュは、取得し、クライアント コンピューターで少量のメモリを消費しているときに表示するために必要なことのみが含まれるように、必要に応じて値を破棄する必要があります。</span><span class="sxs-lookup"><span data-stu-id="333d1-145">The cache should retrieve and discard values as necessary so that it only contains what is necessary for display while consuming a small amount of memory on the client computer.</span></span>  
  
-   <span data-ttu-id="333d1-146">要件に応じて、データ ストアのパフォーマンスを微調整します。</span><span class="sxs-lookup"><span data-stu-id="333d1-146">Fine-tune the performance of the data store depending on your requirements.</span></span> <span data-ttu-id="333d1-147">たとえば、補正するためにクライアント コンピューターのメモリ制限ではなく、低速ネットワーク接続を大きなサイズのキャッシュを使用し、データベース クエリの数を最小限に抑えることができます。</span><span class="sxs-lookup"><span data-stu-id="333d1-147">For example, you might want to compensate for slow network connections rather than client-computer memory limitations by using a larger cache size and minimizing the number of database queries.</span></span>  
  
 <span data-ttu-id="333d1-148">外部データベースから値をキャッシュの詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで Just-In-Time データ読み込みによる仮想モードを実装する](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="333d1-148">For more information about caching values from an external database, see [How to: Implement Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/virtual-mode-with-just-in-time-data-loading-in-the-datagrid.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="333d1-149">関連項目</span><span class="sxs-lookup"><span data-stu-id="333d1-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.VirtualMode%2A>  
 <xref:System.Windows.Forms.DataGridView.CellValueNeeded>  
 <xref:System.Windows.Forms.DataGridView.CellValuePushed>  
 <xref:System.Windows.Forms.DataGridView.NewRowNeeded>  
 <xref:System.Windows.Forms.DataGridView.RowValidated>  
 <xref:System.Windows.Forms.DataGridView.RowDirtyStateNeeded>  
 <xref:System.Windows.Forms.DataGridView.CancelRowEdit>  
 <xref:System.Windows.Forms.DataGridView.UserDeletingRow>  
 [<span data-ttu-id="333d1-150">Windows フォーム DataGridView コントロールでのパフォーマンス チューニング</span><span class="sxs-lookup"><span data-stu-id="333d1-150">Performance Tuning in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/performance-tuning-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="333d1-151">Windows フォーム DataGridView コントロールを拡張するための推奨される手順</span><span class="sxs-lookup"><span data-stu-id="333d1-151">Best Practices for Scaling the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="333d1-152">Windows フォーム DataGridView コントロールでの Just-In-Time データ読み込みによる仮想モードの実装</span><span class="sxs-lookup"><span data-stu-id="333d1-152">Implementing Virtual Mode with Just-In-Time Data Loading in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/implementing-virtual-mode-jit-data-loading-in-the-datagrid.md)  
 [<span data-ttu-id="333d1-153">方法: Windows フォーム DataGridView コントロールで仮想モードを実装する</span><span class="sxs-lookup"><span data-stu-id="333d1-153">How to: Implement Virtual Mode in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-implement-virtual-mode-in-the-windows-forms-datagridview-control.md)
