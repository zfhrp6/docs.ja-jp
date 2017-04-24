---
title: "ListView の概要 | Microsoft Docs"
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
  - "コントロール, ListView"
  - "ListView コントロール [WPF], ListView コントロールの概要"
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# ListView の概要
<xref:System.Windows.Controls.ListView> コントロールは、一連のデータ項目を異なるレイアウトまたはビューで表示するためのインフラストラクチャを提供します。  たとえば、データ項目をテーブルで表示し、さらに列の並べ替えも行う場合です。  
  
   
  
<a name="WhatisaListView"></a>   
## ListView とは  
 <xref:System.Windows.Controls.ListView> コントロールは、<xref:System.Windows.Controls.ListBox> から派生した <xref:System.Windows.Controls.ItemsControl> です。  通常、その項目はデータ コレクションのメンバーであり、<xref:System.Windows.Controls.ListViewItem> オブジェクトとして表されます。  <xref:System.Windows.Controls.ListViewItem> は <xref:System.Windows.Controls.ContentControl> であり、格納できる子要素は 1 つだけです。  ただし、その子要素はどのようなビジュアル要素でもかまいません。  
  
<a name="DefiningaListViewView"></a>   
## ListView の表示モードの定義  
 <xref:System.Windows.Controls.ListView> コントロールのコンテンツの表示モードを指定するには、<xref:System.Windows.Controls.ListView.View%2A> プロパティを設定します。  [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] に用意されている表示モードの 1 つに <xref:System.Windows.Controls.GridView> があります。このモードでは、カスタマイズ可能な列を持つテーブルにデータ項目のコレクションが表示されます。  
  
 従業員情報を表示する <xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.GridView> を定義する方法を次の例に示します。  
  
 [!code-xml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 次の図は、前の例でデータがどのように表示されるのかを示したものです。  
  
 ![GridView 出力を含む ListView](../../../../docs/framework/wpf/controls/media/listviewgridview.png "ListViewGridView")  
  
 <xref:System.Windows.Controls.ViewBase> クラスを継承するクラスを定義することで、カスタム表示モードを作成できます。  <xref:System.Windows.Controls.ViewBase> クラスは、カスタム ビューを作成するために必要なインフラストラクチャを提供します。  カスタム ビューの作成方法の詳細については、「[ListView のカスタム表示モードを作成する](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md)」を参照してください。  
  
<a name="BindingDatatoaListView"></a>   
## ListView へのデータのバインド  
 <xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティと <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティを使用して、<xref:System.Windows.Controls.ListView> コントロールの項目を指定します。  次の例では、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> プロパティを `EmployeeInfoDataSource` という名前のデータ コレクションに設定します。  
  
 [!code-xml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 <xref:System.Windows.Controls.GridView> では、<xref:System.Windows.Controls.GridViewColumn> オブジェクトが指定したデータ フィールドにバインドされます。  次の例では、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> プロパティに <xref:System.Windows.Data.Binding> を指定することで、<xref:System.Windows.Controls.GridViewColumn> オブジェクトをデータ フィールドにバインドします。  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 また、列のセルにスタイルを設定するために使用する <xref:System.Windows.DataTemplate> 定義の一部として、<xref:System.Windows.Data.Binding> を指定することもできます。  次の例では、<xref:System.Windows.ResourceKey> で識別される <xref:System.Windows.DataTemplate> で、<xref:System.Windows.Controls.GridViewColumn> に <xref:System.Windows.Data.Binding> を設定します。  この例では、<xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> を定義していないことに注意してください。これを定義すると、<xref:System.Windows.DataTemplate> によって指定されているバインディングがオーバーライドされます。  
  
 [!code-xml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## GridView を実装する ListView へのスタイルの設定  
 <xref:System.Windows.Controls.ListView> コントロールに含まれる <xref:System.Windows.Controls.ListViewItem> オブジェクトは、表示されるデータ項目を表します。  次のプロパティを使用して、データ項目のコンテンツとスタイルを定義できます。  
  
-   <xref:System.Windows.Controls.ListView> コントロールでは、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、<xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>、および <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> プロパティを使用します。  
  
-   <xref:System.Windows.Controls.ListViewItem> コントロールでは、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> および <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> プロパティを使用します。  
  
 <xref:System.Windows.Controls.GridView> におけるセル間の配置の問題を回避するため、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> を使用して <xref:System.Windows.Controls.ListView> の項目の幅に影響を与えるプロパティやコンテンツを設定または追加しないようにしてください。  たとえば、<xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> で <xref:System.Windows.FrameworkElement.Margin%2A> プロパティを設定すると、配置の問題が発生する可能性があります。  <xref:System.Windows.Controls.GridView> 内の項目の幅に影響を与えるプロパティやコンテンツを指定または定義するには、<xref:System.Windows.Controls.GridView> クラスのプロパティ、およびそれに関連するクラス \(<xref:System.Windows.Controls.GridViewColumn> など\) を使用してください。  
  
 <xref:System.Windows.Controls.GridView> およびそのサポート クラスの使用方法について、詳しくは「[GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)」を参照してください。  
  
 <xref:System.Windows.Controls.ListView> コントロールの <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> を定義し、さらに <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> も定義する場合、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> が正しく動作するには、スタイルに <xref:System.Windows.Controls.ContentPresenter> を含める必要があります。  
  
 <xref:System.Windows.Controls.GridView> を使用して表示する <xref:System.Windows.Controls.ListView> のコンテンツには、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> および <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> プロパティを使用しないでください。  <xref:System.Windows.Controls.GridView> の列のコンテンツの配置を指定するには、<xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> を定義します。  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## 同じ表示モードの共有  
 2 つの <xref:System.Windows.Controls.ListView> コントロールが同じ表示モードを同時に共有することはできません。  複数の <xref:System.Windows.Controls.ListView> コントロールで同じ表示モードを使用しようとすると、例外が発生します。  
  
 複数の <xref:System.Windows.Controls.ListView> で同時に使用できる表示モードを指定するには、テンプレートまたはスタイルを使用します。  <xref:System.Windows.FrameworkElement.Resources%2A> としてビューを定義する方法の例については、[複数のビューを持つ ListView のサンプル](http://go.microsoft.com/fwlink/?LinkID=160013)を参照してください。  
  
<a name="CreatingaCustomView"></a>   
## カスタム表示モードの作成  
 <xref:System.Windows.Controls.GridView> のようなカスタマイズされたビューは、<xref:System.Windows.Controls.ViewBase> 抽象クラスから派生します。この抽象クラスは、<xref:System.Windows.Controls.ListViewItem> オブジェクトとして表されるデータ項目を表示するためのツールを提供します。  
  
 カスタム表示モードの例については、[複数のビューを持つ ListView のサンプル](http://go.microsoft.com/fwlink/?LinkID=160013)を参照してください。  
  
## 参照  
 <xref:System.Windows.Controls.GridView>   
 <xref:System.Windows.Controls.ListView>   
 <xref:System.Windows.Controls.ListViewItem>   
 <xref:System.Windows.Data.Binding>   
 [GridView の概要](../../../../docs/framework/wpf/controls/gridview-overview.md)   
 [方法のトピック](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)   
 [コントロール](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)