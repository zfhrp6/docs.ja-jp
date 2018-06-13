---
title: '方法 : 子テーブルの選択行が現在位置を保持することを保証する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- master-details view
- row position [Windows Forms]
- parent/child view [Windows Forms]
- resetting child position
- data binding [.NET Framework], row selection
- caching [.NET Framework], child position
- child position
- master/details view [Windows Forms]
- child tables row selection
- current child position
ms.assetid: c5fa2562-43a4-46fa-a604-52d8526a87bd
ms.openlocfilehash: 96e1acb4629e4a9c0c4b3eb368f19147c9ce2b73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539891"
---
# <a name="how-to-ensure-the-selected-row-in-a-child-table-remains-at-the-correct-position"></a><span data-ttu-id="12e10-102">方法 : 子テーブルの選択行が現在位置を保持することを保証する</span><span class="sxs-lookup"><span data-stu-id="12e10-102">How to: Ensure the Selected Row in a Child Table Remains at the Correct Position</span></span>
<span data-ttu-id="12e10-103">多くの場合、Windows フォームでデータ バインディングを処理するときは、いわゆる親/子ビューまたはマスター/詳細ビューにデータを表示します。</span><span class="sxs-lookup"><span data-stu-id="12e10-103">Oftentimes when you work with data binding in Windows Forms, you will display data in what is called a parent/child or master/details view.</span></span> <span data-ttu-id="12e10-104">これは、同一ソースのデータが、2 つのコントロールに表示されるデータ バインディング シナリオを示します。</span><span class="sxs-lookup"><span data-stu-id="12e10-104">This refers to a data-binding scenario where data from the same source is displayed in two controls.</span></span> <span data-ttu-id="12e10-105">片方のコントロールで選択を変更すると、他方のコントロールに表示されるデータが変化します。</span><span class="sxs-lookup"><span data-stu-id="12e10-105">Changing the selection in one control causes the data displayed in the second control to change.</span></span> <span data-ttu-id="12e10-106">たとえば、第 1 のコントロールに顧客リストが含まれ、第 2 のコントロールに、第 1 のコントロールで選択された顧客に関連する注文リストが含まれます。</span><span class="sxs-lookup"><span data-stu-id="12e10-106">For example, the first control might contain a list of customers and the second a list of orders related to the selected customer in the first control.</span></span>  
  
 <span data-ttu-id="12e10-107">.NET Framework Version 2.0 以降、親/子ビューにデータを表示する場合は、子テーブルで現在選択されている行が、親テーブルの先頭行にリセットされないようにするために、追加の手順を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e10-107">Starting with the .NET Framework version 2.0, when you display data in a parent/child view you might have to take extra steps to make sure that the currently selected row in the child table is not reset to the first row of the table.</span></span> <span data-ttu-id="12e10-108">そのためには、子テーブルの位置をキャッシュし、親テーブルが変更された後で位置をリセットする必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e10-108">In order to do this, you will have to cache the child table position and reset it after the parent table changes.</span></span> <span data-ttu-id="12e10-109">通常、子テーブルのリセットは、親テーブルの行のフィールドが初めて変更されたときに発生します。</span><span class="sxs-lookup"><span data-stu-id="12e10-109">Typically the child reset occurs the first time a field in a row of the parent table changes.</span></span>  
  
### <a name="to-cache-the-current-child-position"></a><span data-ttu-id="12e10-110">子テーブルの現在位置をキャッシュするには</span><span class="sxs-lookup"><span data-stu-id="12e10-110">To Cache the Current Child Position</span></span>  
  
1.  <span data-ttu-id="12e10-111">子リストの位置を格納する整数変数と、子の位置をキャッシュするかどうかを示すブール変数を宣言します。</span><span class="sxs-lookup"><span data-stu-id="12e10-111">Declare an integer variable to store the child list position and a Boolean variable to store whether to cache the child position.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#4)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#4)]  
  
2.  <span data-ttu-id="12e10-112">バインディングの <xref:System.Windows.Forms.CurrencyManager> の <xref:System.Windows.Forms.CurrencyManager.ListChanged> イベントを処理し、<xref:System.ComponentModel.ListChangedType.Reset> の <xref:System.ComponentModel.ListChangedType> をチェックします。</span><span class="sxs-lookup"><span data-stu-id="12e10-112">Handle the <xref:System.Windows.Forms.CurrencyManager.ListChanged> event for the binding's <xref:System.Windows.Forms.CurrencyManager> and check for a <xref:System.ComponentModel.ListChangedType> of <xref:System.ComponentModel.ListChangedType.Reset>.</span></span>  
  
3.  <span data-ttu-id="12e10-113"><xref:System.Windows.Forms.CurrencyManager> の現在位置をチェックします。</span><span class="sxs-lookup"><span data-stu-id="12e10-113">Check the current position of the <xref:System.Windows.Forms.CurrencyManager>.</span></span> <span data-ttu-id="12e10-114">それがリストの最初のエントリ (通常は 0) よりも大きい場合は、変数に保存します。</span><span class="sxs-lookup"><span data-stu-id="12e10-114">If it is greater than first entry in the list (typically 0), save it to a variable.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#2)]  
  
4.  <span data-ttu-id="12e10-115">親リストの親現在位置マネージャーの <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="12e10-115">Handle the parent list's <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> event for the parent currency manager.</span></span> <span data-ttu-id="12e10-116">ハンドラーで、キャッシュ シナリオではないことを示すブール値を設定します。</span><span class="sxs-lookup"><span data-stu-id="12e10-116">In the handler, set the Boolean value to indicate it is not a caching scenario.</span></span> <span data-ttu-id="12e10-117"><xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> が発生した場合、親の変更はリストの位置の変更であり、項目値の変更ではありません。</span><span class="sxs-lookup"><span data-stu-id="12e10-117">If the <xref:System.Windows.Forms.BindingManagerBase.CurrentChanged> occurs, the change to the parent is a list position change and not an item value change.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#5)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#5)]  
  
### <a name="to-reset-the-child-position"></a><span data-ttu-id="12e10-118">子の位置をリセットするには</span><span class="sxs-lookup"><span data-stu-id="12e10-118">To Reset the Child Position</span></span>  
  
1.  <span data-ttu-id="12e10-119">子のバインディングの <xref:System.Windows.Forms.CurrencyManager> の <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> イベントを処理します。</span><span class="sxs-lookup"><span data-stu-id="12e10-119">Handle the <xref:System.Windows.Forms.BindingManagerBase.PositionChanged> event for the child binding's <xref:System.Windows.Forms.CurrencyManager>.</span></span>  
  
2.  <span data-ttu-id="12e10-120">子テーブルの位置を、前の手順で保存したキャッシュ位置にリセットします。</span><span class="sxs-lookup"><span data-stu-id="12e10-120">Reset the child table position to the cached position saved in the previous procedure.</span></span>  
  
     [!code-csharp[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.CurrencyManagerReset#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#3)]  
  
## <a name="example"></a><span data-ttu-id="12e10-121">例</span><span class="sxs-lookup"><span data-stu-id="12e10-121">Example</span></span>  
 <span data-ttu-id="12e10-122">子テーブルの <xref:System.Windows.Forms.CurrencyManager> の現在位置を保存し、親テーブルの編集が完了した後でその位置をリセットする方法を次の例に示します。</span><span class="sxs-lookup"><span data-stu-id="12e10-122">The following example demonstrates how to save the current position on the <xref:System.Windows.Forms.CurrencyManager>.for a child table and reset the position after an edit is completed on the parent table.</span></span> <span data-ttu-id="12e10-123">この例には、<xref:System.Windows.Forms.BindingSource> コンポーネントを使用して <xref:System.Data.DataSet> 内の 2 つのテーブルにバインドされた 2 つの <xref:System.Windows.Forms.DataGridView> コントロールが含まれます。</span><span class="sxs-lookup"><span data-stu-id="12e10-123">This example contains two <xref:System.Windows.Forms.DataGridView> controls bound to two tables in a <xref:System.Data.DataSet> using a <xref:System.Windows.Forms.BindingSource> component.</span></span> <span data-ttu-id="12e10-124">この 2 つのテーブルの間にリレーションシップが確立され、そのリレーションシップが <xref:System.Data.DataSet> に追加されます。</span><span class="sxs-lookup"><span data-stu-id="12e10-124">A relation is established between the two tables and the relation is added to the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="12e10-125">子テーブル内の位置は、デモを目的として、3 行目に初期設定されています。</span><span class="sxs-lookup"><span data-stu-id="12e10-125">The position in the child table is initially set to the third row for demonstration purposes.</span></span>  
  
 [!code-csharp[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.CurrencyManagerReset#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.CurrencyManagerReset/VB/Form1.vb#1)]  
  
 <span data-ttu-id="12e10-126">このコード例をテストするには、次の手順を実行します。</span><span class="sxs-lookup"><span data-stu-id="12e10-126">To test the code example, perform the following steps:</span></span>  
  
1.  <span data-ttu-id="12e10-127">例を実行します。</span><span class="sxs-lookup"><span data-stu-id="12e10-127">Run the example.</span></span>  
  
2.  <span data-ttu-id="12e10-128">**[Cache and reset position]** (位置をキャッシュしてリセットする) チェック ボックスがオンであることを確認します。</span><span class="sxs-lookup"><span data-stu-id="12e10-128">Make sure the **Cache and reset position** check box is selected.</span></span>  
  
3.  <span data-ttu-id="12e10-129">**[Clear parent field]** (親フィールドのクリア) ボタンをクリックして、親テーブルのフィールドを変更します。</span><span class="sxs-lookup"><span data-stu-id="12e10-129">Click the **Clear parent field** button to cause a change in a field of the parent table.</span></span> <span data-ttu-id="12e10-130">子テーブル内の選択行が変更されないことに注目してください。</span><span class="sxs-lookup"><span data-stu-id="12e10-130">Notice that the selected row in the child table does not change.</span></span>  
  
4.  <span data-ttu-id="12e10-131">例をいったん閉じてから、例を再実行します。</span><span class="sxs-lookup"><span data-stu-id="12e10-131">Close and run the example again.</span></span> <span data-ttu-id="12e10-132">リセット動作は親行が初めて変更された場合のみ発生するので、この操作を実行する必要があります。</span><span class="sxs-lookup"><span data-stu-id="12e10-132">You need to do this because the reset behavior occurs only on the first change in the parent row.</span></span>  
  
5.  <span data-ttu-id="12e10-133">**[Cache and reset position]** (位置をキャッシュしてリセットする) チェック ボックスをオフにします。</span><span class="sxs-lookup"><span data-stu-id="12e10-133">Clear the **Cache and reset position** check box.</span></span>  
  
6.  <span data-ttu-id="12e10-134">**[Clear parent field]** (親フィールドのクリア) ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="12e10-134">Click the **Clear parent field** button.</span></span> <span data-ttu-id="12e10-135">子テーブル内の選択行が 1 行目に変更されることに注目してください。</span><span class="sxs-lookup"><span data-stu-id="12e10-135">Notice that the selected row in the child table changes to the first row.</span></span>  
  
## <a name="compiling-the-code"></a><span data-ttu-id="12e10-136">コードのコンパイル</span><span class="sxs-lookup"><span data-stu-id="12e10-136">Compiling the Code</span></span>  
 <span data-ttu-id="12e10-137">この例で必要な要素は次のとおりです。</span><span class="sxs-lookup"><span data-stu-id="12e10-137">This example requires:</span></span>  
  
-   <span data-ttu-id="12e10-138">System、System.Data、System.Drawing、System.Windows.Forms、および System.XML の各アセンブリへの参照。</span><span class="sxs-lookup"><span data-stu-id="12e10-138">References to the System, System.Data, System.Drawing, System.Windows.Forms, and System.XML assemblies.</span></span>  
  
 <span data-ttu-id="12e10-139">Visual Basic または Visual c# のコマンドラインからこの例をビルドする方法については、次を参照してください。[コマンドラインからのビルド](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md)または[コマンド ライン ビルドで csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md)です。</span><span class="sxs-lookup"><span data-stu-id="12e10-139">For information about how to build this example from the command line for Visual Basic or Visual C#, see [Building from the Command Line](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) or [Command-line Building With csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md).</span></span> <span data-ttu-id="12e10-140">この例では、Visual Studio は、新しいプロジェクトにコードを貼り付けることによってもビルドできます。</span><span class="sxs-lookup"><span data-stu-id="12e10-140">You can also build this example in Visual Studio by pasting the code into a new project.</span></span>  <span data-ttu-id="12e10-141">また、「 [方法: 完成した Windows フォーム コードの例を Visual Studio を使ってコンパイルして実行する](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\))」も参照してください。</span><span class="sxs-lookup"><span data-stu-id="12e10-141">Also see [How to: Compile and Run a Complete Windows Forms Code Example Using Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12e10-142">関連項目</span><span class="sxs-lookup"><span data-stu-id="12e10-142">See Also</span></span>  
 [<span data-ttu-id="12e10-143">方法: 複数のコントロールを 1 つのデータ ソースにバインドして同期状態を保つ</span><span class="sxs-lookup"><span data-stu-id="12e10-143">How to: Ensure Multiple Controls Bound to the Same Data Source Remain Synchronized</span></span>](../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md)  
 [<span data-ttu-id="12e10-144">BindingSource コンポーネント</span><span class="sxs-lookup"><span data-stu-id="12e10-144">BindingSource Component</span></span>](../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [<span data-ttu-id="12e10-145">データ連結と Windows フォーム</span><span class="sxs-lookup"><span data-stu-id="12e10-145">Data Binding and Windows Forms</span></span>](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
