---
title: "方法: DataGrid コントロールに行の詳細を追加する | Microsoft Docs"
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
  - "DataGrid [WPF], 行の詳細"
  - "DataTemplate [WPF], DataGrid"
  - "行の詳細 [WPF], DataGrid"
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法: DataGrid コントロールに行の詳細を追加する
<xref:System.Windows.Controls.DataGrid> コントロールを使用するときに、行の詳細セクションを追加して、データ表示をカスタマイズできます。  行の詳細セクションを追加すると、テンプレート内のデータをグループ化して、必要に応じて表示と非表示を切り替えることができます。  たとえば、<xref:System.Windows.Controls.DataGrid> 内の各行の概要のみを表示する <xref:System.Windows.Controls.DataGrid> に行の詳細を追加して、ユーザーが行を選択したときに詳細なデータ フィールドが表示されるようにします。  <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> プロパティの行の詳細セクションに対して、テンプレートを定義します。  次の図に、行の詳細セクションの例を示します。  
  
 ![行の詳細を表示する DataGrid](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP\_RowDetails")  
  
 行の詳細テンプレートは、インライン XAML またはリソースとして定義します。  両方の手順について次に示します。  リソースとして追加されたテンプレートは、テンプレートを再作成しなくてもプロジェクト全体で使用できます。  インライン XAML として追加されたデータ テンプレートは、それが定義されているコントロールからのみアクセスできます。  
  
### インライン XAML を使用して行の詳細を表示するには  
  
1.  データ ソースのデータを表示する <xref:System.Windows.Controls.DataGrid> を作成します。  
  
2.  <xref:System.Windows.Controls.DataGrid> 要素に、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 要素を追加します。  
  
3.  行の詳細セクションの外観を定義する <xref:System.Windows.DataTemplate> を作成します。  
  
     次の XAML は、<xref:System.Windows.Controls.DataGrid>、および <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> をインラインで定義する方法を示しています。  <xref:System.Windows.Controls.DataGrid> は、各行内の 3 つの値、および行が選択されたときにさらに表示される 3 つの値を表示します。  
  
     [!code-xml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     次のコードは、<xref:System.Windows.Controls.DataGrid> に表示されるデータを選択する際に使用されるクエリを示しています。  この例では、クエリによって、顧客情報を含むエンティティのデータが選択されます。  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### リソースを使用して行の詳細を表示するには  
  
1.  データ ソースのデータを表示する <xref:System.Windows.Controls.DataGrid> を作成します。  
  
2.  <xref:System.Windows.FrameworkElement.Resources%2A> 要素を <xref:System.Windows.Window> コントロールや <xref:System.Windows.Controls.Page> コントロールなどのルート要素に追加するか、または <xref:System.Windows.Application.Resources%2A> 要素を App.xaml \(または Application.xaml\) ファイル内の <xref:System.Windows.Application> クラスに追加します。  
  
3.  リソース要素に、行の詳細セクションの外観を定義する <xref:System.Windows.DataTemplate> を作成します。  
  
     次の XAML は、<xref:System.Windows.Application> クラスに定義された <xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> を示しています。  
  
     [!code-xml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <xref:System.Windows.DataTemplate> で、[x:Key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md) に、データ テンプレートを一意に識別する値を設定します。  
  
5.  <xref:System.Windows.Controls.DataGrid> 要素で、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> プロパティを、前の手順で定義したリソースに設定します。  リソースを静的リソースとして割り当てます。  
  
     次の XAML は、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> プロパティが前の例のリソースに設定された状態を示しています。  
  
     [!code-xml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### 行の詳細の表示を設定し、水平方向にスクロールできないようにするには  
  
1.  必要に応じて、<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A> プロパティを <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> の値に設定します。  
  
     既定では、値は <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> に設定されます。  すべての行の詳細を表示するには、この値を <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> に設定し、すべての行の詳細を非表示にするには、この値を <xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode> に設定します。  
  
2.  必要に応じて、<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A> プロパティを `true` に設定して、行の詳細セクションを水平方向にスクロールできないようにします。