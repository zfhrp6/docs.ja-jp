---
title: "方法: DataGrid コントロールを使用して検証を実装する | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "DataGrid [WPF], 検証"
  - "検証 [WPF], DataGrid"
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法: DataGrid コントロールを使用して検証を実装する
<xref:System.Windows.Controls.DataGrid> コントロールでは、セル レベルと行レベルの両方で検証を実行できます。  セル レベルの検証では、ユーザーが値を更新したときに、バインドされたデータ オブジェクトの個々のプロパティを検証します。  行レベルの検証では、ユーザーが行に対する変更をコミットしたときに、データ オブジェクト全体を検証します。  検証エラーに対してカスタマイズした視覚的フィードバックを提供したり、<xref:System.Windows.Controls.DataGrid> コントロールで提供される既定の視覚的フィードバックを使用したりすることもできます。  
  
 以下の手順では、検証規則を <xref:System.Windows.Controls.DataGrid> バインディングに適用し、視覚的フィードバックをカスタマイズする方法について説明します。  
  
### 個別のセル値を検証するには  
  
-   列で使用されるバインディングに対して 1 つ以上の検証規則を指定します。  これは、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」に説明されている単純なコントロールのデータの検証に似ています。  
  
     次の例では、ビジネス オブジェクトの別々のプロパティにバインドされた 4 つの列がある <xref:System.Windows.Controls.DataGrid> コントロールを示します。  そのうちの 3 つの列では、<xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> プロパティを `true` に設定して、<xref:System.Windows.Controls.ExceptionValidationRule> を指定しています。  
  
     [!code-xml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     ユーザーが無効な値 \(Course ID 列の整数以外など\) を入力すると、赤い枠線がセルの周囲に表示されます。  この既定の検証フィードバックは、次の手順に従って変更できます。  
  
### セルの検証フィードバックをカスタマイズするには  
  
-   列の <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> プロパティを、列の編集コントロールに適したスタイルに設定します。  編集コントロールは実行時に作成されるため、単純なコントロールのように <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=fullName> 添付プロパティを使用することはできません。  
  
     次の例では、前の例を更新して、検証規則のある 3 つの列で共有されるエラー スタイルを追加します。  ユーザーが無効な値を入力すると、スタイルによってセルの背景色が変更され、ツールヒントが追加されます。  トリガーを使用して検証エラーがあるかどうかを確認していることに注意してください。  現在はセル用のエラー テンプレートがないため、この処理が必要です。  
  
     [!code-xml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     列で使用される <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> を置き換えると、より広範囲なカスタマイズを実装できます。  
  
### 単一行の複数の値を検証するには  
  
1.  バインドされたデータ オブジェクトの複数のプロパティをチェックする <xref:System.Windows.Controls.ValidationRule> サブクラスを実装します。  <xref:System.Windows.Controls.ValidationRule.Validate%2A> メソッドの実装で、`value` パラメーターの値を <xref:System.Windows.Data.BindingGroup> インスタンスにキャストします。  その後、<xref:System.Windows.Data.BindingGroup.Items%2A> プロパティを使用してデータ オブジェクトにアクセスできます。  
  
     この処理によって `Course` オブジェクトの `StartDate` プロパティ値が `EndDate` プロパティ値より前かどうかを検証する例を次に示します。  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=fullName> コレクションに検証規則を追加します。  <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> プロパティは、コントロールで使用されるすべてのバインディングをグループ化する <xref:System.Windows.Data.BindingGroup> インスタンスの <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> プロパティへの直接アクセスを可能にします。  
  
     XAML に <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> プロパティを設定する例を次に示します。  <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> プロパティが <xref:System.Windows.Controls.ValidationStep> に設定されているため、検証はバインドされたデータ オブジェクトの更新後にのみ行われます。  
  
     [!code-xml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     ユーザーが、開始日より前の終了日を指定すると、赤い感嘆符 \(\!\) が行ヘッダーに表示されます。  この既定の検証フィードバックは、次の手順に従って変更できます。  
  
### 行の検証フィードバックをカスタマイズするには  
  
-   <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=fullName> プロパティを設定します。  このプロパティを使用して、個々の <xref:System.Windows.Controls.DataGrid> コントロールの行の検証フィードバックをカスタマイズできます。  暗黙の行スタイルを使用して <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=fullName> プロパティを設定することにより、複数のコントロールに影響を与えることもできます。  
  
     より視覚的なインジケーターで既定の行の検証フィードバックを置き換える例を次に示します。  ユーザーが無効な値を入力すると、赤い円で囲まれた白い感嘆符が行ヘッダーに表示されます。  これは、行とセルのどちらの検証エラーでも発生します。  関連付けられているエラー メッセージがツールヒントに表示されます。  
  
     [!code-xml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## 使用例  
 次の例では、セルおよび行の検証の詳細なデモンストレーションを示します。  `Course` クラスは、トランザクションをサポートするために、<xref:System.ComponentModel.IEditableObject> を実装するサンプル データ オブジェクトを提供します。  <xref:System.Windows.Controls.DataGrid> コントロールは、<xref:System.ComponentModel.IEditableObject> とやり取りして、ユーザーが Esc キーを押すことで変更を元に戻せるようにします。  
  
> [!NOTE]
>  Visual Basic を使用している場合は、MainWindow.xaml の最初の行で、`x:Class="DataGridValidation.MainWindow"` を `x:Class="MainWindow"` に置き換えてください。  
  
 検証をテストするには、次の操作を試します。  
  
-   Course ID 列に、整数以外の値を入力します。  
  
-   End Date 列に、Start Date より前の日付を入力します。  
  
-   Course ID、Start Date、または End Date の値を削除します。  
  
-   無効なセル値を元に戻すには、カーソルをセルに戻し、Esc キーを押します。  
  
-   現在のセルが編集モードのときに行全体の変更を元に戻すには、Esc キーを 2 回押します。  
  
-   検証エラーが発生した場合は、行ヘッダーのインジケーターの上にマウス ポインターを移動すると、関連するエラー メッセージが表示されます。  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## 参照  
 <xref:System.Windows.Controls.DataGrid>   
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)   
 [データ バインディング](../../../../docs/framework/wpf/data/data-binding-wpf.md)   
 [バインディングの検証の実装](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)   
 [カスタム オブジェクトに検証ロジックを実装する](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)