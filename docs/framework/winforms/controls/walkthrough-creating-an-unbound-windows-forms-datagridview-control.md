---
title: "チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成"
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
- data [Windows Forms], displaying without binding to data source
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
- walkthroughs [Windows Forms], DataGridView control
ms.assetid: 5a8d6afa-1b4b-4b24-8db8-501086ffdebe
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d737959ee0ecab4c611cebf996741516fc7be031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-creating-an-unbound-windows-forms-datagridview-control"></a><span data-ttu-id="5dbdd-102">チュートリアル : バインドされていない Windows フォーム DataGridView コントロールの作成</span><span class="sxs-lookup"><span data-stu-id="5dbdd-102">Walkthrough: Creating an Unbound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5dbdd-103">頻繁にデータベースから発生していない表形式のデータを表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-103">You may frequently want to display tabular data that does not originate from a database.</span></span> <span data-ttu-id="5dbdd-104">たとえば、文字列の 2 次元配列の内容を表示することがあります。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-104">For example, you may want to show the contents of a two-dimensional array of strings.</span></span> <span data-ttu-id="5dbdd-105"><xref:System.Windows.Forms.DataGridView>クラスには、データ ソースにバインドせずにデータを表示する簡単で高度にカスタマイズ可能な方法が用意されています。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-105">The <xref:System.Windows.Forms.DataGridView> class provides an easy and highly customizable way to display data without binding to a data source.</span></span> <span data-ttu-id="5dbdd-106">このチュートリアルで作成する方法、<xref:System.Windows.Forms.DataGridView>制御および管理が追加および「バインドされていない」モードでの行の削除。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-106">This walkthrough shows how to populate a <xref:System.Windows.Forms.DataGridView> control and manage the addition and deletion of rows in "unbound" mode.</span></span> <span data-ttu-id="5dbdd-107">既定では、ユーザーは、新しい行を追加できます。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-107">By default, the user can add new rows.</span></span> <span data-ttu-id="5dbdd-108">行の追加を防ぐためには、設定、<xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A>プロパティは`false`します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-108">To prevent row addition, set the <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property is `false`.</span></span>  
  
 <span data-ttu-id="5dbdd-109">このトピックの「単一のリストとしてコードをコピーするに、を参照してください。[する方法: バインドされていない Windows フォームの DataGridView コントロールの作成](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-109">To copy the code in this topic as a single listing, see [How to: Create an Unbound Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="creating-the-form"></a><span data-ttu-id="5dbdd-110">フォームの作成</span><span class="sxs-lookup"><span data-stu-id="5dbdd-110">Creating the Form</span></span>  
  
#### <a name="to-use-an-unbound-datagridview-control"></a><span data-ttu-id="5dbdd-111">バインドされていない DataGridView コントロールを使用するには</span><span class="sxs-lookup"><span data-stu-id="5dbdd-111">To use an unbound DataGridView control</span></span>  
  
1.  <span data-ttu-id="5dbdd-112">派生するクラスを作成する<xref:System.Windows.Forms.Form>し、次の変数宣言が含まれていますと`Main`メソッドです。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-112">Create a class that derives from <xref:System.Windows.Forms.Form> and contains the following variable declarations and `Main` method.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#01)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#01](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#01)]  
    [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#02)]
    [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#02](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#02)]  
  
2.  <span data-ttu-id="5dbdd-113">実装する`SetupLayout`フォームのレイアウトを設定するフォームのクラス定義内のメソッドです。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-113">Implement a `SetupLayout` method in your form's class definition to set up the form's layout.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#20)]  
  
3.  <span data-ttu-id="5dbdd-114">作成、`SetupDataGridView`を設定するメソッド、<xref:System.Windows.Forms.DataGridView>およびプロパティの列です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-114">Create a `SetupDataGridView` method to set up the <xref:System.Windows.Forms.DataGridView> columns and properties.</span></span>  
  
     <span data-ttu-id="5dbdd-115">このメソッドは最初に、追加、<xref:System.Windows.Forms.DataGridView>コントロールをフォームの<xref:System.Windows.Forms.Control.Controls%2A>コレクション。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-115">This method first adds the <xref:System.Windows.Forms.DataGridView> control to the form's <xref:System.Windows.Forms.Control.Controls%2A> collection.</span></span> <span data-ttu-id="5dbdd-116">次に、表示する列の数が設定を使用して、<xref:System.Windows.Forms.DataGridView.ColumnCount%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-116">Next, the number of columns to be displayed is set using the <xref:System.Windows.Forms.DataGridView.ColumnCount%2A> property.</span></span> <span data-ttu-id="5dbdd-117">設定して、列ヘッダーの既定のスタイルを設定、 <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>、 <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>、および<xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A>のプロパティ、<xref:System.Windows.Forms.DataGridViewCellStyle>によって返される、<xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-117">The default style for the column headers is set by setting the <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A>, <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A>, and <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> properties of the <xref:System.Windows.Forms.DataGridViewCellStyle> returned by the <xref:System.Windows.Forms.DataGridView.ColumnHeadersDefaultCellStyle%2A> property.</span></span>  
  
     <span data-ttu-id="5dbdd-118">レイアウトと外観のプロパティが設定され、列名の割り当てられます。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-118">Layout and appearance properties are set, and then the column names are assigned.</span></span> <span data-ttu-id="5dbdd-119">このメソッドの終了時に、<xref:System.Windows.Forms.DataGridView>コントロールが事前設定する準備ができています。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-119">When this method exits, the <xref:System.Windows.Forms.DataGridView> control is ready to be populated.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#30](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#30)]  
  
4.  <span data-ttu-id="5dbdd-120">作成、`PopulateDataGridView`行を追加する方法、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-120">Create a `PopulateDataGridView` method to add rows to the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="5dbdd-121">各行は、曲とその関連情報を表します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-121">Each row represents a song and its associated information.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#40)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#40](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#40)]  
  
5.  <span data-ttu-id="5dbdd-122">インプレースのユーティリティ メソッドでは、イベント ハンドラーをアタッチできます。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-122">With the utility methods in place, you can attach event handlers.</span></span>  
  
     <span data-ttu-id="5dbdd-123">処理する、**追加**と**削除**ボタンの<xref:System.Windows.Forms.Control.Click>イベントと、フォームの<xref:System.Windows.Forms.Form.Load>イベント、および<xref:System.Windows.Forms.DataGridView>コントロールの<xref:System.Windows.Forms.DataGridView.CellFormatting>イベント。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-123">You will handle the **Add** and **Delete** buttons' <xref:System.Windows.Forms.Control.Click> events, the form's <xref:System.Windows.Forms.Form.Load> event, and the <xref:System.Windows.Forms.DataGridView> control's <xref:System.Windows.Forms.DataGridView.CellFormatting> event.</span></span>  
  
     <span data-ttu-id="5dbdd-124">ときに、**追加**ボタンの<xref:System.Windows.Forms.Control.Click>イベントが発生すると、新しい空の行を追加する、<xref:System.Windows.Forms.DataGridView>です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-124">When the **Add** button's <xref:System.Windows.Forms.Control.Click> event is raised, a new, empty row is added to the <xref:System.Windows.Forms.DataGridView>.</span></span>  
  
     <span data-ttu-id="5dbdd-125">ときに、**削除**ボタンの<xref:System.Windows.Forms.Control.Click>イベントは、選択した行が削除されたである場合を除き、ユーザーは、新しいレコードの行が新しい行を追加します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-125">When the **Delete** button's <xref:System.Windows.Forms.Control.Click> event is raised, the selected row is deleted, unless it is the row for new records, which enables the user add new rows.</span></span> <span data-ttu-id="5dbdd-126">この行は、最後の行では常に、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-126">This row is always the last row in the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
     <span data-ttu-id="5dbdd-127">ときに、フォームの<xref:System.Windows.Forms.Form.Load>のイベントが発生、 `SetupLayout`、 `SetupDataGridView`、および`PopulateDataGridView`ユーティリティ メソッドが呼び出されます。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-127">When the form's <xref:System.Windows.Forms.Form.Load> event is raised, the `SetupLayout`, `SetupDataGridView`, and `PopulateDataGridView` utility methods are called.</span></span>  
  
     <span data-ttu-id="5dbdd-128">ときに、<xref:System.Windows.Forms.DataGridView.CellFormatting>イベントが発生すると、各セルに、`Date`セルの値を解析できない場合を除き、列を長い形式の日付として書式設定します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-128">When the <xref:System.Windows.Forms.DataGridView.CellFormatting> event is raised, each cell in the `Date` column is formatted as a long date, unless the cell's value cannot be parsed.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#10)]  
  
## <a name="testing-the-application"></a><span data-ttu-id="5dbdd-129">アプリケーションのテスト</span><span class="sxs-lookup"><span data-stu-id="5dbdd-129">Testing the Application</span></span>  
 <span data-ttu-id="5dbdd-130">フォームをテストして、期待どおりに動作することを確認します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-130">You can now test the form to make sure it behaves as expected.</span></span>  
  
#### <a name="to-test-the-form"></a><span data-ttu-id="5dbdd-131">フォームをテストするには</span><span class="sxs-lookup"><span data-stu-id="5dbdd-131">To test the form</span></span>  
  
-   <span data-ttu-id="5dbdd-132">F5 キーを押してアプリケーションを実行します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-132">Press F5 to run the application.</span></span>  
  
     <span data-ttu-id="5dbdd-133">表示されます、<xref:System.Windows.Forms.DataGridView>に曲を表示するコントロール`PopulateDataGridView`です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-133">You will see a <xref:System.Windows.Forms.DataGridView> control that displays the songs listed in `PopulateDataGridView`.</span></span> <span data-ttu-id="5dbdd-134">新しい行を追加することができます、**行の追加** ボタン、およびするがで選択した行を削除、**行の削除**ボタンをクリックします。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-134">You can add new rows with the **Add Row** button, and you can delete selected rows with the **Delete Row** button.</span></span> <span data-ttu-id="5dbdd-135">バインドされていない<xref:System.Windows.Forms.DataGridView>コントロールは、データ ストアとそのデータは、任意の外部ソースに依存しないなど、<xref:System.Data.DataSet>または配列。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-135">The unbound <xref:System.Windows.Forms.DataGridView> control is the data store, and its data is independent of any external source, such as a <xref:System.Data.DataSet> or an array.</span></span>  
  
## <a name="next-steps"></a><span data-ttu-id="5dbdd-136">次の手順</span><span class="sxs-lookup"><span data-stu-id="5dbdd-136">Next Steps</span></span>  
 <span data-ttu-id="5dbdd-137">このアプリケーションでは、基本を理解、<xref:System.Windows.Forms.DataGridView>コントロールの機能です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-137">This application gives you a basic understanding of the <xref:System.Windows.Forms.DataGridView> control's capabilities.</span></span> <span data-ttu-id="5dbdd-138">動作と外観をカスタマイズすることができます、<xref:System.Windows.Forms.DataGridView>いくつかの方法で制御します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-138">You can customize the appearance and behavior of the <xref:System.Windows.Forms.DataGridView> control in several ways:</span></span>  
  
-   <span data-ttu-id="5dbdd-139">境界線とヘッダーのスタイルを変更します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-139">Change border and header styles.</span></span> <span data-ttu-id="5dbdd-140">詳細については、次を参照してください。[する方法: 境界と Windows フォーム DataGridView コントロールでのグリッド線のスタイルを変更する](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-140">For more information, see [How to: Change the Border and Gridline Styles in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/change-the-border-and-gridline-styles-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="5dbdd-141">有効にするか、ユーザー入力を制限、<xref:System.Windows.Forms.DataGridView>コントロール。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-141">Enable or restrict user input to the <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5dbdd-142">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールで防止行の追加および削除](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)、と[する方法: Windows フォーム DataGridView コントロールで列読み取り専用のため](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-142">For more information, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md), and [How to: Make Columns Read-Only in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="5dbdd-143">データベースに関連するエラーのユーザー入力を確認してください。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-143">Check user input for database-related errors.</span></span> <span data-ttu-id="5dbdd-144">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでのデータ入力中に発生したエラーの処理](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-144">For more information, see [Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md).</span></span>  
  
-   <span data-ttu-id="5dbdd-145">仮想モードを使用して、非常に大きなデータ セットを処理します。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-145">Handle very large data sets using virtual mode.</span></span> <span data-ttu-id="5dbdd-146">詳細については、次を参照してください。[チュートリアル: Windows フォーム DataGridView コントロールでの仮想モードを実装する](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-146">For more information, see [Walkthrough: Implementing Virtual Mode in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/implementing-virtual-mode-wf-datagridview-control.md).</span></span>  
  
-   <span data-ttu-id="5dbdd-147">セルの外観をカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-147">Customize the appearance of cells.</span></span> <span data-ttu-id="5dbdd-148">詳細については、次を参照してください。[する方法: Windows フォーム DataGridView コントロールのセルの外観をカスタマイズ](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md)と[する方法: Windows フォーム DataGridView コントロールの既定のセル スタイルの設定](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md)です。</span><span class="sxs-lookup"><span data-stu-id="5dbdd-148">For more information, see [How to: Customize the Appearance of Cells in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/customize-the-appearance-of-cells-in-the-datagrid.md) and [How to: Set Default Cell Styles for the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5dbdd-149">参照</span><span class="sxs-lookup"><span data-stu-id="5dbdd-149">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 [<span data-ttu-id="5dbdd-150">Windows フォーム DataGridView コントロールでのデータの表示</span><span class="sxs-lookup"><span data-stu-id="5dbdd-150">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5dbdd-151">方法: 連結されていない Windows フォーム DataGridView コントロールを作成する</span><span class="sxs-lookup"><span data-stu-id="5dbdd-151">How to: Create an Unbound Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-create-an-unbound-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="5dbdd-152">Windows フォーム DataGridView コントロールでのデータ表示モード</span><span class="sxs-lookup"><span data-stu-id="5dbdd-152">Data Display Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-display-modes-in-the-windows-forms-datagridview-control.md)
