---
title: DataGrid
ms.date: 03/30/2017
helpviewer_keywords:
- DataGrid column types [WPF]
- DataGrid scenarios [WPF]
- DataGrid control [WPF]
- controls [WPF], DataGrid
- DataGrid [WPF], common tasks for
- DataGrid [WPF], customizing the appearance of
- DataGrid columns [WPF], using
ms.assetid: bf89ea63-79b6-422b-bc9f-0485ad803216
ms.openlocfilehash: a8f267706c1ace02b091329360779711981d01e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557083"
---
# <a name="datagrid"></a>DataGrid
<xref:System.Windows.Controls.DataGrid>コントロールでは、表示および SQL データベース、LINQ クエリ、またはその他のバインド可能なデータ ソースからなど、さまざまなソースからデータを編集することができます。 詳しくは、「[バインディング ソースの概要](../../../../docs/framework/wpf/data/binding-sources-overview.md)」をご覧ください。  
  
 列がなど、コントロールのテキストを表示することができます、 <xref:System.Windows.Controls.ComboBox>、またはイメージ、ボタン、またはテンプレートに含まれるすべてのコンテンツなどその他の WPF コンテンツ。 使用することができます、<xref:System.Windows.Controls.DataGridTemplateColumn>テンプレートで定義されているデータを表示します。 次の表には、既定で用意されている列の型が一覧表示します。  
  
|生成された列の型|データの種類|  
|---------------------------|---------------|  
|<xref:System.Windows.Controls.DataGridTextColumn>|<xref:System.String>|  
|<xref:System.Windows.Controls.DataGridCheckBoxColumn>|<xref:System.Boolean>|  
|<xref:System.Windows.Controls.DataGridComboBoxColumn>|<xref:System.Enum>|  
|<xref:System.Windows.Controls.DataGridHyperlinkColumn>|<xref:System.Uri>|  
  
 <xref:System.Windows.Controls.DataGrid> セルのフォント、色、サイズなどの外観をカスタマイズできます。 <xref:System.Windows.Controls.DataGrid> 他の WPF コントロールのすべてのスタイルとテンプレートの機能をサポートしています。 <xref:System.Windows.Controls.DataGrid> 既定値と編集、並べ替え、および検証のカスタマイズ可能な動作にも含まれます。  
  
 次の表の一般的なタスク<xref:System.Windows.Controls.DataGrid>およびそれを達成する方法です。 関連する API を表示すると、詳細情報とサンプル コードが表示されます。  
  
|シナリオ|方法|  
|--------------|--------------|  
|代替背景色|設定、<xref:System.Windows.Controls.ItemsControl.AlternationIndex%2A>を 2 以上のプロパティを割り当てます、<xref:System.Windows.Media.Brush>を<xref:System.Windows.Controls.DataGrid.RowBackground%2A>と<xref:System.Windows.Controls.DataGrid.AlternatingRowBackground%2A>プロパティです。|  
|セルおよび行の選択の動作を定義します。|<xref:System.Windows.Controls.DataGrid.SelectionMode%2A> プロパティと <xref:System.Windows.Controls.DataGrid.SelectionUnit%2A> プロパティを設定します。|  
|ヘッダー、セル、および行の外観をカスタマイズします。|新しい適用<xref:System.Windows.Style>を<xref:System.Windows.Controls.DataGrid.ColumnHeaderStyle%2A>、 <xref:System.Windows.Controls.DataGrid.RowHeaderStyle%2A>、 <xref:System.Windows.Controls.DataGrid.CellStyle%2A>、または<xref:System.Windows.Controls.DataGrid.RowStyle%2A>プロパティです。|  
|サイズ変更オプションを設定します。|設定、 <xref:System.Windows.FrameworkElement.Height%2A>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>、 <xref:System.Windows.FrameworkElement.MinHeight%2A>、 <xref:System.Windows.FrameworkElement.Width%2A>、 <xref:System.Windows.FrameworkElement.MaxWidth%2A>、または<xref:System.Windows.FrameworkElement.MinWidth%2A>プロパティです。 詳細については、次を参照してください。 [DataGrid コントロールのサイズ変更オプション](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)です。|  
|項目にアクセスするを選択|チェック、 <xref:System.Windows.Controls.DataGrid.SelectedCells%2A> 、選択したセルを取得するプロパティと<xref:System.Windows.Controls.Primitives.MultiSelector.SelectedItems%2A>選択した行を取得するプロパティです。 詳細については、「<xref:System.Windows.Controls.DataGrid.SelectedCells%2A>」を参照してください。|  
|エンドユーザーとの対話をカスタマイズします。|設定、 <xref:System.Windows.Controls.DataGrid.CanUserAddRows%2A>、 <xref:System.Windows.Controls.DataGrid.CanUserDeleteRows%2A>、 <xref:System.Windows.Controls.DataGrid.CanUserReorderColumns%2A>、 <xref:System.Windows.Controls.DataGrid.CanUserResizeColumns%2A>、 <xref:System.Windows.Controls.DataGrid.CanUserResizeRows%2A>、および<xref:System.Windows.Controls.DataGrid.CanUserSortColumns%2A>プロパティです。|  
|キャンセルまたは自動的に生成された列の変更|処理、<xref:System.Windows.Controls.DataGrid.AutoGeneratingColumn>イベント。|  
|列を固定します。|設定、 <xref:System.Windows.Controls.DataGrid.FrozenColumnCount%2A> 1 を設定して、左端の位置に移動、列のプロパティ、<xref:System.Windows.Controls.DataGridColumn.DisplayIndex%2A>プロパティを 0 にします。|  
|XML データをデータ ソースとして使用します。|バインド、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>上、<xref:System.Windows.Controls.DataGrid>項目のコレクションを表す XPath クエリにします。 内の各列を作成、<xref:System.Windows.Controls.DataGrid>です。 項目のソースのプロパティを取得するクエリへのバインドで、XPath を設定して各列をバインドします。 例については、「<xref:System.Windows.Controls.DataGridTextColumn>」を参照してください。|  
  
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[チュートリアル: DataGrid コントロールで SQL Server データベースのデータを表示する](../../../../docs/framework/wpf/controls/walkthrough-display-data-from-a-sql-server-database-in-a-datagrid-control.md)|Entity Framework 要素を追加、新しい WPF プロジェクトの設定をソースを設定し、内のデータを表示する方法について説明します、<xref:System.Windows.Controls.DataGrid>です。|  
|[方法: DataGrid コントロールに行の詳細を追加する](../../../../docs/framework/wpf/controls/how-to-add-row-details-to-a-datagrid-control.md)|行の詳細を作成する方法について説明します、<xref:System.Windows.Controls.DataGrid>です。|  
|[方法: DataGrid コントロールを使用して検証を実装する](../../../../docs/framework/wpf/controls/how-to-implement-validation-with-the-datagrid-control.md)|内の値を検証する方法について説明<xref:System.Windows.Controls.DataGrid>セルと行、および検証のフィードバックを表示します。|  
|[DataGrid コントロールの既定のキーボード動作とマウス動作](../../../../docs/framework/wpf/controls/default-keyboard-and-mouse-behavior-in-the-datagrid-control.md)|対話する方法について説明します、<xref:System.Windows.Controls.DataGrid>キーボードとマウスを使用して制御します。|  
|[方法: DataGrid コントロールでデータをグループ化、並べ替え、およびフィルター処理する](../../../../docs/framework/wpf/controls/how-to-group-sort-and-filter-data-in-the-datagrid-control.md)|データを表示する方法について説明、<xref:System.Windows.Controls.DataGrid>によってグループ化、並べ替え、およびデータのフィルター処理のさまざまな方法でします。|  
|[DataGrid コントロールのサイズ変更方法](../../../../docs/framework/wpf/controls/sizing-options-in-the-datagrid-control.md)|絶対と自動サイズ変更を制御する方法について説明します、<xref:System.Windows.Controls.DataGrid>です。|  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.DataGrid>  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)  
 [コントロール](../../../../docs/framework/wpf/controls/index.md)  
 [WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)
