---
title: "TreeView の概要 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "Control クラス, TreeView"
  - "展開 (ノードを)"
  - "TreeView コントロール, TreeView コントロールの概要"
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
caps.latest.revision: 33
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 32
---
# TreeView の概要
<xref:System.Windows.Controls.TreeView> コントロールは、折りたたみ可能なノードを使用して、階層構造で情報を表示する手段を提供します。  ここでは、<xref:System.Windows.Controls.TreeView> および <xref:System.Windows.Controls.TreeViewItem> コントロールについて説明し、簡単な使用例を示します。  
  
   
  
<a name="Simple_TreeView_Control"></a>   
## TreeView とは  
 <xref:System.Windows.Controls.TreeView> は、<xref:System.Windows.Controls.TreeViewItem> コントロールを使用して項目を入れ子にする <xref:System.Windows.Controls.ItemsControl> です。  <xref:System.Windows.Controls.TreeView> を作成する例を次に示します。  
  
 [!code-xml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## TreeView の作成  
 <xref:System.Windows.Controls.TreeView> コントロールには、<xref:System.Windows.Controls.TreeViewItem> コントロールの階層が格納されます。  <xref:System.Windows.Controls.TreeViewItem> コントロールは、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> と <xref:System.Windows.Controls.ItemsControl.Items%2A> コレクションを持つ <xref:System.Windows.Controls.HeaderedItemsControl> です。  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] を使用して <xref:System.Windows.Controls.TreeView> を定義する場合は、<xref:System.Windows.Controls.TreeViewItem> コントロールの <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> コンテンツとそのコレクションを構成する項目を明示的に定義できます。  前の図は、このメソッドを示しています。  
  
 <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> をデータ ソースとして指定し、<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> と <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> を指定して <xref:System.Windows.Controls.TreeViewItem> のコンテンツを定義することもできます。  
  
 また、<xref:System.Windows.HierarchicalDataTemplate> オブジェクトを使用して、<xref:System.Windows.Controls.TreeViewItem> コントロールのレイアウトを定義できます。  詳細および使用例については、「[SelectedValue、SelectedValuePath、および SelectedItem を使用する](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 <xref:System.Windows.Controls.TreeViewItem> コントロールでない項目は、<xref:System.Windows.Controls.TreeView> コントロールが表示されるときに、<xref:System.Windows.Controls.TreeViewItem> コントロールで自動的に囲まれます。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## TreeViewItem の展開と折りたたみ  
 ユーザーが <xref:System.Windows.Controls.TreeViewItem> を展開すると、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> プロパティが `true` に設定されます。  また、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A> プロパティを `true` \(展開\) または `false` \(折りたたみ\) に設定すると、直接のユーザー アクションなしに <xref:System.Windows.Controls.TreeViewItem> を展開したり折りたたんだりすることができます。  このプロパティが変更されると、<xref:System.Windows.Controls.TreeViewItem.Expanded> イベントまたは <xref:System.Windows.Controls.TreeViewItem.Collapsed> イベントが発生します。  
  
 <xref:System.Windows.FrameworkElement.BringIntoView%2A> メソッドが <xref:System.Windows.Controls.TreeViewItem> コントロールで呼び出されると、<xref:System.Windows.Controls.TreeViewItem> とその親 <xref:System.Windows.Controls.TreeViewItem> コントロールが展開します。  <xref:System.Windows.Controls.TreeViewItem> が表示されない、またはその一部が表示されない場合、<xref:System.Windows.Controls.TreeView> がスクロールして、表示されるようになります。  
  
<a name="TreeViewItem_Selection"></a>   
## TreeViewItem の選択  
 ユーザーが <xref:System.Windows.Controls.TreeViewItem> コントロールをクリックして選択すると、<xref:System.Windows.Controls.TreeViewItem.Selected> イベントが発生し、その <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> プロパティが `true` に設定されます。  この <xref:System.Windows.Controls.TreeViewItem> は、<xref:System.Windows.Controls.TreeView> コントロールの <xref:System.Windows.Controls.TreeView.SelectedItem%2A> にもなります。  一方、選択項目が <xref:System.Windows.Controls.TreeViewItem> コントロールから変更されると、<xref:System.Windows.Controls.TreeViewItem.Unselected> イベントが発生し、その <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> プロパティが `false` に設定されます。  
  
 この <xref:System.Windows.Controls.TreeView> コントロールの <xref:System.Windows.Controls.TreeView.SelectedItem%2A> プロパティは読み取り専用プロパティであるめ、明示的に設定することはできません。  <xref:System.Windows.Controls.TreeView.SelectedItem%2A> プロパティが設定されるのは、ユーザーが <xref:System.Windows.Controls.TreeViewItem> コントロールをクリックするときか、または <xref:System.Windows.Controls.TreeViewItem.IsSelected%2A> プロパティが <xref:System.Windows.Controls.TreeViewItem> コントロールで `true` に設定されるときです。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A> の <xref:System.Windows.Controls.TreeView.SelectedValue%2A> を指定するには、<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A> プロパティを使用します。  詳細については、「[SelectedValue、SelectedValuePath、および SelectedItem を使用する](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItemChanged> イベントで、イベント ハンドラーを登録して、選択した <xref:System.Windows.Controls.TreeViewItem> を変更するタイミングを指定できます。  イベント ハンドラーに提供される <xref:System.Windows.RoutedPropertyChangedEventArgs%601> は、前の選択内容の <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A> を指定し、現在の選択内容の <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A> を指定します。  アプリケーションまたはユーザーが、前または現在の選択を行っていない場合、その値は `null` になります。  
  
<a name="TreeView_Style"></a>   
## TreeView のスタイル  
 <xref:System.Windows.Controls.TreeView> コントロールの既定のスタイルでは、<xref:System.Windows.Controls.ScrollViewer> コントロールを含む <xref:System.Windows.Controls.StackPanel> オブジェクト内に、コントロールが配置されます。  <xref:System.Windows.Controls.TreeView> の <xref:System.Windows.FrameworkElement.Width%2A> プロパティと <xref:System.Windows.FrameworkElement.Height%2A> プロパティを設定した場合は、これらの値を使用して <xref:System.Windows.Controls.TreeView> を表示する <xref:System.Windows.Controls.StackPanel> オブジェクトのサイズが変更されます。  表示するコンテンツが表示領域より大きい場合は、<xref:System.Windows.Controls.ScrollViewer> が自動的に表示されるので、ユーザーは <xref:System.Windows.Controls.TreeView> コンテンツ全体をスクロールできます。  
  
 <xref:System.Windows.Controls.TreeViewItem> コントロールの外観をカスタマイズするには、<xref:System.Windows.FrameworkElement.Style%2A> プロパティをカスタムの <xref:System.Windows.Style> に設定します。  
  
 <xref:System.Windows.FrameworkElement.Style%2A> を使用して、<xref:System.Windows.Controls.TreeViewItem> コントロールの <xref:System.Windows.Controls.Control.Foreground%2A> および <xref:System.Windows.Controls.Control.FontSize%2A> プロパティ値を設定する方法を次の例に示します。  
  
 [!code-xml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## TreeView 項目へのイメージおよび他のコンテンツの追加  
 複数のオブジェクトを <xref:System.Windows.Controls.TreeViewItem> の <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> コンテンツに含めることができます。  複数のオブジェクトを <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> コンテンツに含めるには、<xref:System.Windows.Controls.Panel> または <xref:System.Windows.Controls.StackPanel> などのレイアウト コントロールで囲まれるように配置します。  
  
 <xref:System.Windows.Controls.TreeViewItem> の <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> を、<xref:System.Windows.Controls.DockPanel> コントロールに囲まれた <xref:System.Windows.Controls.CheckBox> および <xref:System.Windows.Controls.TextBlock> として定義する方法を次の例に示します。  
  
 [!code-xml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 <xref:System.Windows.Controls.DockPanel> コントロールに囲まれた <xref:System.Windows.Controls.Image> と <xref:System.Windows.Controls.TextBlock> を含む <xref:System.Windows.DataTemplate> を定義する方法を次の例に示します。  <xref:System.Windows.DataTemplate> を使用して、<xref:System.Windows.Controls.TreeViewItem> の <xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A> または <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> を設定できます。  
  
 [!code-xml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## 参照  
 <xref:System.Windows.Controls.TreeView>   
 <xref:System.Windows.Controls.TreeViewItem>   
 [方法のトピック](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)   
 [WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)