---
title: ListView の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 5a7e640b7398c2034933688ea6356ef14692f8f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="listview-overview"></a>ListView の概要
<xref:System.Windows.Controls.ListView>コントロールには、さまざまなレイアウトまたはビューにデータ項目のセットを表示するためのインフラストラクチャが用意されています。 たとえば、ユーザーは、テーブルにデータ項目を表示し、その列を並べ替えできます。  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>ListView とは  
 <xref:System.Windows.Controls.ListView>コントロールは、<xref:System.Windows.Controls.ItemsControl>から派生する<xref:System.Windows.Controls.ListBox>です。 通常、その項目はデータ コレクションのメンバーでありとして表される<xref:System.Windows.Controls.ListViewItem>オブジェクト。 A<xref:System.Windows.Controls.ListViewItem>は、<xref:System.Windows.Controls.ContentControl>単一の子要素のみを含めることができます。 ただし、その子要素は、任意のビジュアル要素にできます。  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>ListView の表示モードの定義  
 コンテンツの表示モードを指定する、<xref:System.Windows.Controls.ListView>コントロールを設定する、<xref:System.Windows.Controls.ListView.View%2A>プロパティです。 1 つのビュー モードを[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]提供は<xref:System.Windows.Controls.GridView>、カスタマイズ可能な列を持つテーブルのデータ項目のコレクションが表示されます。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.GridView>の<xref:System.Windows.Controls.ListView>従業員情報を表示するコントロール。  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例でのデータの表示方法を示しています。  
  
 ![GridView 出力を含む ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 継承するクラスを定義することで、カスタム ビュー モードを作成することができます、<xref:System.Windows.Controls.ViewBase>クラスです。 <xref:System.Windows.Controls.ViewBase>クラスには、カスタム ビューを作成する必要のあるインフラストラクチャが用意されています。 カスタム ビューを作成する方法の詳細については、[ Create a Custom View Mode for a ListView ](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)を参照してください。  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>ListView へのデータ バインディング  
 使用して、<xref:System.Windows.Controls.ItemsControl.Items%2A>と<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>の項目を指定するプロパティ、<xref:System.Windows.Controls.ListView>コントロール。 次の例のセット、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>プロパティと呼ばれるデータの収集を`EmployeeInfoDataSource`です。  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 <xref:System.Windows.Controls.GridView>、<xref:System.Windows.Controls.GridViewColumn>オブジェクトが指定されたデータ フィールドにバインドします。 次の例ではバインド、<xref:System.Windows.Controls.GridViewColumn>オブジェクトを指定して、データ フィールドに、<xref:System.Windows.Data.Binding>の<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>プロパティです。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 指定することも、<xref:System.Windows.Data.Binding>の一部として、<xref:System.Windows.DataTemplate>定義列のセルのスタイルを設定するために使用します。 次の例で、<xref:System.Windows.DataTemplate>で識別される、<xref:System.Windows.ResourceKey>設定、<xref:System.Windows.Data.Binding>の<xref:System.Windows.Controls.GridViewColumn>です。 注この例が定義されていない、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>これには、バインディングで指定されているためより優先されるため<xref:System.Windows.DataTemplate>です。  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>GridView を実装する ListView のスタイル設定  
 <xref:System.Windows.Controls.ListView>コントロールに含まれる<xref:System.Windows.Controls.ListViewItem>、表示されるデータ項目を表すオブジェクト。 次のプロパティを使用して、データ項目の内容とスタイルを定義できます。  
  
-   <xref:System.Windows.Controls.ListView>コントロールを使用して、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>、および<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>プロパティです。  
  
-   <xref:System.Windows.Controls.ListViewItem>コントロールを使用して、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>と<xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A>プロパティです。  
  
 セル間の配置の問題を回避する、 <xref:System.Windows.Controls.GridView>、使用しない、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>プロパティを設定したり、アイテムの幅に影響するコンテンツを追加、<xref:System.Windows.Controls.ListView>です。 たとえば、配置の問題発生する可能性が設定するときに、<xref:System.Windows.FrameworkElement.Margin%2A>プロパティに、 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>。 プロパティを指定するか、内のアイテムの幅に影響するコンテンツを定義する、<xref:System.Windows.Controls.GridView>のプロパティを使用して、<xref:System.Windows.Controls.GridView>クラスとその関連クラスなど<xref:System.Windows.Controls.GridViewColumn>です。  
  
 使用する方法の詳細についての<xref:System.Windows.Controls.GridView>し、そのサポート クラスを参照してください[GridView 概要](../../../../docs/framework/wpf/controls/gridview-overview.md)です。  
  
 定義した場合、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>の<xref:System.Windows.Controls.ListView>制御および定義、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、含める必要があります、<xref:System.Windows.Controls.ContentPresenter>の順序でスタイルで、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>正常に動作します。  
  
 使用しないでください、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>と<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>プロパティ<xref:System.Windows.Controls.ListView>を使用して表示されるコンテンツ、<xref:System.Windows.Controls.GridView>です。 列のコンテンツの配置を指定する、 <xref:System.Windows.Controls.GridView>、定義、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>です。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>同じ表示モードの共有  
 2 つ<xref:System.Windows.Controls.ListView>コントロールは、同時に同じ表示モードを共有することはできません。 1 つ以上に同じ表示モードを使用しようとする場合<xref:System.Windows.Controls.ListView>制御、例外が発生します。  
  
 1 つ以上同時に使用できる表示モードを指定する<xref:System.Windows.Controls.ListView>、テンプレートまたはスタイルを使用します。 ビューを定義する方法の例については<xref:System.Windows.FrameworkElement.Resources%2A>を参照してください[複数のビューのサンプルを含む ListView](http://go.microsoft.com/fwlink/?LinkID=160013)です。  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>カスタム表示モードの作成  
 表示と同様にカスタマイズされた<xref:System.Windows.Controls.GridView>から派生した、<xref:System.Windows.Controls.ViewBase>として表されるデータ項目を表示するためのツールを提供するクラスを抽象化<xref:System.Windows.Controls.ListViewItem>オブジェクト。  
  
 カスタム表示モードの例は、[ListView with Multiple Views Sample](http://go.microsoft.com/fwlink/?LinkID=160013)を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
