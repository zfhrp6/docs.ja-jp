---
title: '方法: DataGrid コントロールを使用して検証を実装する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 20fcc8ebafb25e4e4f176447972e7637aaa5cd7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557876"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="feda3-102">方法: DataGrid コントロールを使用して検証を実装する</span><span class="sxs-lookup"><span data-stu-id="feda3-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="feda3-103"><xref:System.Windows.Controls.DataGrid>コントロールでは、セルと行の両方のレベルに検証を実行することができます。</span><span class="sxs-lookup"><span data-stu-id="feda3-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="feda3-104">セル レベルの検証、ユーザーが値を更新したときに、バインドされたデータ オブジェクトの個々 のプロパティを検証します。</span><span class="sxs-lookup"><span data-stu-id="feda3-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="feda3-105">行レベルの検証、ユーザーが行に変更をコミット時に、データ オブジェクト全体を検証します。</span><span class="sxs-lookup"><span data-stu-id="feda3-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="feda3-106">検証エラーのカスタマイズされた視覚的なフィードバックを提供したり、既定の視覚的フィードバックを使用する、<xref:System.Windows.Controls.DataGrid>コントロールを提供します。</span><span class="sxs-lookup"><span data-stu-id="feda3-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="feda3-107">次の手順の検証ルールを適用する方法について説明<xref:System.Windows.Controls.DataGrid>バインドし、視覚的なフィードバックをカスタマイズします。</span><span class="sxs-lookup"><span data-stu-id="feda3-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="feda3-108">個々 のセル値を検証するには</span><span class="sxs-lookup"><span data-stu-id="feda3-108">To validate individual cell values</span></span>  
  
-   <span data-ttu-id="feda3-109">列で使用されるバインディングの 1 つまたは複数の検証規則を指定します。</span><span class="sxs-lookup"><span data-stu-id="feda3-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="feda3-110">これがに似ていますが、単純なコントロールのデータの検証」の説明に従って[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)です。</span><span class="sxs-lookup"><span data-stu-id="feda3-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="feda3-111">次の例は、<xref:System.Windows.Controls.DataGrid>ビジネス オブジェクトのさまざまなプロパティにバインドされている 4 つの列を持つコントロール。</span><span class="sxs-lookup"><span data-stu-id="feda3-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="feda3-112">3 つの列の指定、<xref:System.Windows.Controls.ExceptionValidationRule>を設定して、<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A>プロパティを`true`です。</span><span class="sxs-lookup"><span data-stu-id="feda3-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="feda3-113">(非整数コース ID 列に) などの無効な値を入力すると、セルの周囲に赤い境界線が表示されます。</span><span class="sxs-lookup"><span data-stu-id="feda3-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="feda3-114">この既定の検証のフィードバックの次の手順に従ってを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="feda3-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="feda3-115">セルの検証フィードバックをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="feda3-115">To customize cell validation feedback</span></span>  
  
-   <span data-ttu-id="feda3-116">列の設定<xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A>スタイル プロパティは、列の編集コントロールに対して適切な。</span><span class="sxs-lookup"><span data-stu-id="feda3-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="feda3-117">使用することはできませんの編集コントロールは、実行時に作成される、ため、<xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType>添付プロパティの単純なコントロールの場合と同様にします。</span><span class="sxs-lookup"><span data-stu-id="feda3-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="feda3-118">次の例では、検証規則に 3 つの列で共有されるエラーのスタイルを追加することで、前の例を更新します。</span><span class="sxs-lookup"><span data-stu-id="feda3-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="feda3-119">無効な値を入力すると、スタイルがセルの背景色が変更され、ツールヒントを追加します。</span><span class="sxs-lookup"><span data-stu-id="feda3-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="feda3-120">検証エラーがあるかどうかを判断するトリガーの使用に注意してください。</span><span class="sxs-lookup"><span data-stu-id="feda3-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="feda3-121">現在のセルの専用エラー テンプレートがないために必要です。</span><span class="sxs-lookup"><span data-stu-id="feda3-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="feda3-122">広範囲にわたるカスタマイズを実装するには置き換えることで、<xref:System.Windows.Controls.DataGridColumn.CellStyle%2A>列で使用します。</span><span class="sxs-lookup"><span data-stu-id="feda3-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="feda3-123">1 つの行に複数の値を検証するには</span><span class="sxs-lookup"><span data-stu-id="feda3-123">To validate multiple values in a single row</span></span>  
  
1.  <span data-ttu-id="feda3-124">実装する<xref:System.Windows.Controls.ValidationRule>バインドされたデータ オブジェクトの複数のプロパティをチェックするサブクラスです。</span><span class="sxs-lookup"><span data-stu-id="feda3-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="feda3-125"><xref:System.Windows.Controls.ValidationRule.Validate%2A>メソッドの実装、キャスト、`value`パラメーター値を<xref:System.Windows.Data.BindingGroup>インスタンス。</span><span class="sxs-lookup"><span data-stu-id="feda3-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="feda3-126">データ オブジェクトにアクセスすることができます、<xref:System.Windows.Data.BindingGroup.Items%2A>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="feda3-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="feda3-127">次の例では、このプロセスを検証するかどうか、`StartDate`のプロパティの値、`Course`オブジェクトよりも前か、`EndDate`プロパティの値。</span><span class="sxs-lookup"><span data-stu-id="feda3-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  <span data-ttu-id="feda3-128">検証規則を追加、<xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>コレクション。</span><span class="sxs-lookup"><span data-stu-id="feda3-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="feda3-129"><xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>プロパティに直接アクセスを提供する、<xref:System.Windows.Data.BindingGroup.ValidationRules%2A>のプロパティ、<xref:System.Windows.Data.BindingGroup>コントロールによって使用されるすべてのバインディングをグループ化するインスタンス。</span><span class="sxs-lookup"><span data-stu-id="feda3-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="feda3-130">次の例のセット、 <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> XAML でのプロパティです。</span><span class="sxs-lookup"><span data-stu-id="feda3-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="feda3-131"><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>プロパティに設定されている<xref:System.Windows.Controls.ValidationStep.UpdatedValue>バインドされたデータ オブジェクトが更新された後にのみ検証が行われるようにします。</span><span class="sxs-lookup"><span data-stu-id="feda3-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="feda3-132">ユーザーは、開始日より前である終了日を指定する場合、行ヘッダーに赤の感嘆符 (!) が表示されます。</span><span class="sxs-lookup"><span data-stu-id="feda3-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="feda3-133">この既定の検証のフィードバックの次の手順に従ってを変更することができます。</span><span class="sxs-lookup"><span data-stu-id="feda3-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="feda3-134">行の検証フィードバックをカスタマイズするには</span><span class="sxs-lookup"><span data-stu-id="feda3-134">To customize row validation feedback</span></span>  
  
-   <span data-ttu-id="feda3-135"><xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> プロパティを設定します。</span><span class="sxs-lookup"><span data-stu-id="feda3-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="feda3-136">このプロパティでは、個々 の行の検証のフィードバックをカスタマイズすることができます<xref:System.Windows.Controls.DataGrid>コントロール。</span><span class="sxs-lookup"><span data-stu-id="feda3-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="feda3-137">複数のコントロールを設定する、暗黙の行のスタイルを使用しても影響、<xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>プロパティです。</span><span class="sxs-lookup"><span data-stu-id="feda3-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="feda3-138">次の例は、既定行の検証のフィードバックをより見やすくインジケーターに置き換えます。</span><span class="sxs-lookup"><span data-stu-id="feda3-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="feda3-139">無効な値を入力すると、行ヘッダーに、赤い円と白い感嘆符が表示されます。</span><span class="sxs-lookup"><span data-stu-id="feda3-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="feda3-140">これは、行とセルの両方の検証エラーが発生します。</span><span class="sxs-lookup"><span data-stu-id="feda3-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="feda3-141">ツールヒントには、関連するエラー メッセージが表示されます。</span><span class="sxs-lookup"><span data-stu-id="feda3-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="feda3-142">例</span><span class="sxs-lookup"><span data-stu-id="feda3-142">Example</span></span>  
 <span data-ttu-id="feda3-143">次の例では、セルと行の検証の完了のデモを提供します。</span><span class="sxs-lookup"><span data-stu-id="feda3-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="feda3-144">`Course`クラスを実装するサンプル データ オブジェクトを提供する<xref:System.ComponentModel.IEditableObject>トランザクションをサポートします。</span><span class="sxs-lookup"><span data-stu-id="feda3-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="feda3-145"><xref:System.Windows.Controls.DataGrid>コントロールが対話<xref:System.ComponentModel.IEditableObject>をユーザーが esc キーを押して変更を元に戻すを有効にします。</span><span class="sxs-lookup"><span data-stu-id="feda3-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="feda3-146">Visual Basic で MainWindow.xaml の最初の行を使用している場合は置き換えます`x:Class="DataGridValidation.MainWindow"`で`x:Class="MainWindow"`です。</span><span class="sxs-lookup"><span data-stu-id="feda3-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="feda3-147">検証をテストするには、次を試してください。</span><span class="sxs-lookup"><span data-stu-id="feda3-147">To test the validation, try the following:</span></span>  
  
-   <span data-ttu-id="feda3-148">コース ID 列で整数以外の値を入力します。</span><span class="sxs-lookup"><span data-stu-id="feda3-148">In the Course ID column, enter a non-integer value.</span></span>  
  
-   <span data-ttu-id="feda3-149">終了日列で、開始日より前の日付を入力します。</span><span class="sxs-lookup"><span data-stu-id="feda3-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
-   <span data-ttu-id="feda3-150">コース ID、開始日または終了日の値を削除します。</span><span class="sxs-lookup"><span data-stu-id="feda3-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
-   <span data-ttu-id="feda3-151">無効なセル値を元に戻すには、セルに戻し、カーソルを置くし、ESC キーを押します。</span><span class="sxs-lookup"><span data-stu-id="feda3-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
-   <span data-ttu-id="feda3-152">現在のセルが編集モードの場合は、全体の行の変更を元に戻す、ESC キーを 2 回押します。</span><span class="sxs-lookup"><span data-stu-id="feda3-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
-   <span data-ttu-id="feda3-153">検証エラーが発生したときに、関連するエラー メッセージを表示する行ヘッダーのインジケーターの上にマウス ポインターを移動します。</span><span class="sxs-lookup"><span data-stu-id="feda3-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="feda3-154">関連項目</span><span class="sxs-lookup"><span data-stu-id="feda3-154">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="feda3-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="feda3-155">DataGrid</span></span>](../../../../docs/framework/wpf/controls/datagrid.md)  
 [<span data-ttu-id="feda3-156">データ バインディング</span><span class="sxs-lookup"><span data-stu-id="feda3-156">Data Binding</span></span>](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [<span data-ttu-id="feda3-157">バインディングの検証の実装</span><span class="sxs-lookup"><span data-stu-id="feda3-157">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="feda3-158">カスタム オブジェクトに検証ロジックを実装する</span><span class="sxs-lookup"><span data-stu-id="feda3-158">Implement Validation Logic on Custom Objects</span></span>](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
