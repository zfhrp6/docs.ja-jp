---
title: '方法: DataGrid コントロールに行の詳細を追加する'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataTemplate [WPF], DataGrid
- row details [WPF], DataGrid
- DataGrid [WPF], row details
ms.assetid: 0bdc6f50-9b4c-483f-9df6-a47a1fde998b
ms.openlocfilehash: b6b0cc99c9833e514d2d52ecf139ab8e110f73e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33555952"
---
# <a name="how-to-add-row-details-to-a-datagrid-control"></a>方法: DataGrid コントロールに行の詳細を追加する
使用する場合、<xref:System.Windows.Controls.DataGrid>コントロール、行の詳細セクションを追加することによってデータの表示をカスタマイズすることができます。 行の詳細セクションを追加するには、必要に応じて表示されるか、折りたたまれる、テンプレート内のデータをグループ化することができます。 行の詳細を追加するなど、<xref:System.Windows.Controls.DataGrid>内の各行のデータの概要のみを表示する、<xref:System.Windows.Controls.DataGrid>が、ユーザーが行を選択したときに、他のデータ フィールドを表示します。 行の詳細セクション内のテンプレートを定義する、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>プロパティです。 次の図は、行の詳細セクションの例を示します。  
  
 ![行の詳細を表示する DataGrid](../../../../docs/framework/wpf/controls/media/ndp-rowdetails.png "NDP_RowDetails")  
  
 リソースとして、または、インライン XAML としては、行の詳細テンプレートを定義します。 次の手順では、両方の方法が表示されます。 リソースとして追加されるデータ テンプレートは、テンプレートを再作成しなくても、プロジェクト全体で使用できます。 インライン XAML からのみアクセス コントロールが定義されているように追加されるデータ テンプレートです。  
  
### <a name="to-display-row-details-by-using-inline-xaml"></a>インライン XAML を使用して行の詳細を表示するには  
  
1.  作成、<xref:System.Windows.Controls.DataGrid>データ ソースからデータを表示します。  
  
2.  <xref:System.Windows.Controls.DataGrid> 要素に、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A> 要素を追加します。  
  
3.  作成、<xref:System.Windows.DataTemplate>行の詳細セクションの外観を定義します。  
  
     次の XAML 示します、<xref:System.Windows.Controls.DataGrid>および定義する方法、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>インラインです。 <xref:System.Windows.Controls.DataGrid>表示 3 つの値の各の行の 3 つ以上の値、行が選択されているときにします。  
  
     [!code-xaml[DataGrid_RowDetails#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml#1)]  
  
     次のコードに表示されるデータを選択するために使用するクエリを示しています、<xref:System.Windows.Controls.DataGrid>です。 この例では、クエリは、顧客情報を含むエンティティからデータを選択します。  
  
     [!code-csharp[DataGrid_RowDetails#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/mainwindow.xaml.cs#2)]
     [!code-vb[DataGrid_RowDetails#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_rowdetails/vb/mainwindow.xaml.vb#2)]  
  
### <a name="to-display-row-details-by-using-a-resource"></a>リソースを使用して行の詳細を表示するには  
  
1.  作成、<xref:System.Windows.Controls.DataGrid>データ ソースからデータを表示します。  
  
2.  追加、<xref:System.Windows.FrameworkElement.Resources%2A>ルート要素の要素など、<xref:System.Windows.Window>コントロールまたは<xref:System.Windows.Controls.Page>制御、または追加、<xref:System.Windows.Application.Resources%2A>要素を<xref:System.Windows.Application>App.xaml (または Application.xaml) ファイル内のクラスです。  
  
3.  リソース要素で作成、<xref:System.Windows.DataTemplate>行の詳細セクションの外観を定義します。  
  
     次の XAML 示します、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>で定義されている、<xref:System.Windows.Application>クラスです。  
  
     [!code-xaml[DataGrid_RowDetails#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/app.xaml#3)]  
  
4.  <xref:System.Windows.DataTemplate>、設定、 [X:key ディレクティブ](../../../../docs/framework/xaml-services/x-key-directive.md)データ テンプレートを一意に識別する値にします。  
  
5.  <xref:System.Windows.Controls.DataGrid>要素、設定、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>前の手順で定義されたリソースへのプロパティです。 静的リソースとしてリソースを割り当てます。  
  
     次の XAML 示します、<xref:System.Windows.Controls.DataGrid.RowDetailsTemplate%2A>プロパティを前の例からリソースに設定します。  
  
     [!code-xaml[DataGrid_RowDetails#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_rowdetails/cs/window2.xaml#4)]  
  
### <a name="to-set-visibility-and-prevent-horizontal-scrolling-for-row-details"></a>表示を設定し、行の詳細を水平方向にスクロールを回避するには  
  
1.  必要に応じて、設定、<xref:System.Windows.Controls.DataGrid.RowDetailsVisibilityMode%2A>プロパティを<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode>値。  
  
     既定では、値に設定<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.VisibleWhenSelected>です。 設定することができます<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Visible>のすべての行の詳細を表示または<xref:System.Windows.Controls.DataGridRowDetailsVisibilityMode.Collapsed>すべての行の詳細を非表示にします。  
  
2.  必要に応じて、設定、<xref:System.Windows.Controls.DataGrid.AreRowDetailsFrozen%2A>プロパティを`true`を防ぐため、行の詳細セクションの水平方向にスクロールします。
