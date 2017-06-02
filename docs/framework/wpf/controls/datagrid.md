---
title: "DataGrid | Microsoft Docs"
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
  - "コントロール [WPF], DataGrid"
  - "DataGrid [WPF], 一般的なタスク"
  - "DataGrid [WPF], カスタマイズ (外観を)"
  - "DataGrid の列型 [WPF]"
  - "DataGrid の列 [WPF], 使用"
  - "DataGrid コントロール [WPF]"
  - "DataGrid のシナリオ [WPF]"
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# DataGrid
<xref:System.Windows.Controls.DataGrid> コントロールでは、SQL データベース、LINQ クエリ、バインドできる他のデータ ソースなどのさまざまなソースのデータを表示および編集できます。  詳細については、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」を参照してください。  
  
 列には、テキスト、<xref:System.Windows.Controls.ComboBox> などのコントロール、イメージやボタンなどのその他の WPF コンテンツ、またはテンプレートに格納されるコンテンツを表示できます。  <xref:System.Windows.Controls.DataGridTemplateColumn> を使用して、テンプレートに定義されたデータを表示できます。  既定で提供される列の型を次の表に示します。  
  
|生成された列の型|\[データ型\]|  
|--------------|--------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> では、セルのフォント、色、サイズなどの表示形式をカスタマイズできます。  <xref:System.Windows.Controls.DataGrid> では、他の WPF コントロールのスタイルとテンプレート機能のすべてをサポートしています。  <xref:System.Windows.Controls.DataGrid> には、編集、並べ替え、および検証に関する、既定の動作とカスタマイズできる動作も用意されています。  
  
 次の表に、<xref:System.Windows.Controls.DataGrid> に共通のタスクの一部と、それらの実行方法を示します。  関連する API を表示することによって、詳細やサンプル コードを参照できます。  
  
|シナリオ|方法|  
|----------|--------|  
|背景色の変更|<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A> プロパティを 2 以上に設定し、<xref:System.Windows.Media.Brush> を <xref:System.Windows.Controls.DataGrid.RowBackground%2A> および <xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A> プロパティに割り当てます。|  
|セルと行の選択動作の定義|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> プロパティおよび <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> プロパティを設定します。|  
|ヘッダー、セル、および行の視覚的な外観のカスタマイズ|新しい <xref:System.Windows.Style> を <xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>、<xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>、<xref:System.Windows.Controls.DataGrid.CellStyle%2A>、または <xref:System.Windows.Controls.DataGrid.RowStyle%2A> プロパティに適用します。|  
|サイズ変更オプションの設定|<xref:System.Windows.FrameworkElement.Height%2A>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>、<xref:System.Windows.FrameworkElement.MinHeight%2A>、<xref:System.Windows.FrameworkElement.Width%2A>、<xref:System.Windows.FrameworkElement.MaxWidth%2A>、または <xref:System.Windows.FrameworkElement.MinWidth%2A> の各プロパティを設定します。  詳細については、「[DataGrid コントロールのサイズ変更方法](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)」を参照してください。|  
|選択されたアイテムへのアクセス|選択されたセルを取得するには <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> プロパティをチェックし、選択された行を取得するには <xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A> プロパティをチェックします。  詳細については、<xref:System.Windows.Controls.DataGrid.SelectedCells%2A> を参照してください。|  
|エンド ユーザーとの対話をカスタマイズ|<xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A> プロパティ、<xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A> プロパティ、<xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A> プロパティ、<xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A> プロパティ、<xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A> プロパティおよび <xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A> プロパティを設定します。|  
|自動生成された列のキャンセルまたは変更|<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn> イベントを処理します。|  
|列の固定|<xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> プロパティを 1 に設定し、<xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A> プロパティを 0 に設定することによって列を左端の位置に移動します。|  
|データ ソースとしての XML データの使用|<xref:System.Windows.Controls.DataGrid> の <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> を、項目のコレクションを表す XPath クエリにバインドします。  <xref:System.Windows.Controls.DataGrid> に各列を作成します。  バインディングの XPath を、項目のソースのプロパティを取得するクエリに設定することによって各列をバインドします。  例については、「<xref:System.Windows.Controls.DataGridTextColumn>」を参照してください。|  
  
## 関連トピック  
  
|Title|Description|  
|-----------|-----------------|  
|[チュートリアル: DataGrid コントロールで SQL Server データベースのデータを表示する](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|新しい WPF プロジェクトを設定し、Entity Framework の要素を追加し、ソースを設定し、<xref:System.Windows.Controls.DataGrid> にデータを表示する方法について説明します。|  
|[方法: DataGrid コントロールに行の詳細を追加する](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid> の行の詳細を作成する方法について説明します。|  
|[方法: DataGrid コントロールを使用して検証を実装する](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid> のセルと行の値を検証し、検証フィードバックを表示する方法について説明します。|  
|[DataGrid コントロールの既定のキーボード動作とマウス動作](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|キーボードとマウスを使用して <xref:System.Windows.Controls.DataGrid> コントロールと対話する方法について説明します。|  
|[方法: DataGrid コントロールでデータをグループ化、並べ替え、およびフィルター処理する](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|グループ化、並べ替え、フィルターなどを適用することによって、さまざまな角度から <xref:System.Windows.Controls.DataGrid> でデータを表示する方法について説明します。|  
|[DataGrid コントロールのサイズ変更方法](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|<xref:System.Windows.Controls.DataGrid> での絶対サイズ設定および自動サイズ設定を制御する方法について説明します。|  
  
## 参照  
 <xref:System.Windows.Controls.DataGrid>   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)   
 [コントロール](../../../../docs/framework/wpf/controls/index.md)   
 [WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)