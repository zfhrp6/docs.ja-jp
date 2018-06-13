---
title: TreeView の概要
ms.date: 03/30/2017
helpviewer_keywords:
- expanding node [WPF]
- TreeView control [WPF], about TreeView control
- Control class [WPF], TreeView
ms.assetid: 62212512-5a5c-4864-949e-b6a6a3a52c02
ms.openlocfilehash: f8c49013bc34671ec590f0bd9f84a0f2cf3f9aaf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557785"
---
# <a name="treeview-overview"></a>TreeView の概要
<xref:System.Windows.Controls.TreeView>コントロールは、折りたたみ可能なノードを使用して、階層構造で情報を表示する方法を提供します。 このトピックでは、<xref:System.Windows.Controls.TreeView>と<xref:System.Windows.Controls.TreeViewItem>コントロール、およびそれらの使用を単純な例を示します。  
  
  
<a name="Simple_TreeView_Control"></a>   
## <a name="what-is-a-treeview"></a>TreeViewとは  
 <xref:System.Windows.Controls.TreeView> <xref:System.Windows.Controls.ItemsControl>を使用して、項目をネストする<xref:System.Windows.Controls.TreeViewItem>コントロール。 次の例を作成、<xref:System.Windows.Controls.TreeView>です。  
  
 [!code-xaml[TreeViewSnips#EmbeddedTVIs](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#embeddedtvis)]  
  
<a name="Creating_a_TreeView"></a>   
## <a name="creating-a-treeview"></a>TreeView の作成  
 <xref:System.Windows.Controls.TreeView>コントロールの階層に含まれる<xref:System.Windows.Controls.TreeViewItem>コントロール。 A<xref:System.Windows.Controls.TreeViewItem>コントロールは、<xref:System.Windows.Controls.HeaderedItemsControl>を持つ、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>と<xref:System.Windows.Controls.ItemsControl.Items%2A>コレクション。  
  
 定義する場合、<xref:System.Windows.Controls.TreeView>を使用して[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]、明示的に定義することができます、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のコンテンツ、<xref:System.Windows.Controls.TreeViewItem>コントロールとそのコレクションを構成する項目。 前の図では、この方法を示しています。  
  
 指定することも、<xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>データとしてソースを指定し、<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>と<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>を定義する、<xref:System.Windows.Controls.TreeViewItem>コンテンツ。  
  
 レイアウトを定義する、<xref:System.Windows.Controls.TreeViewItem>コントロールを使用することも<xref:System.Windows.HierarchicalDataTemplate>オブジェクト。 詳細と例については、「[Use SelectedValue, SelectedValuePath, and SelectedItem](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 項目がない場合、<xref:System.Windows.Controls.TreeViewItem>コントロール、それが自動的にで囲まれた、<xref:System.Windows.Controls.TreeViewItem>タイミングを制御、<xref:System.Windows.Controls.TreeView>コントロールが表示されます。  
  
<a name="Expanding_and_Collapsing_a_TreeViewItem"></a>   
## <a name="expanding-and-collapsing-a-treeviewitem"></a>TreeViewItem の展開と折りたたみ  
 場合は、ユーザーが展開され、 <xref:System.Windows.Controls.TreeViewItem>、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>プロパティに設定されている`true`です。 展開または折りたたむことができますも、<xref:System.Windows.Controls.TreeViewItem>を設定して、ユーザーが直接操作しなくても、<xref:System.Windows.Controls.TreeViewItem.IsExpanded%2A>プロパティを`true`(展開) または`false`(折りたたみ)。 このプロパティが変更されたときに、<xref:System.Windows.Controls.TreeViewItem.Expanded>または<xref:System.Windows.Controls.TreeViewItem.Collapsed>イベントが発生します。  
  
 ときに、<xref:System.Windows.FrameworkElement.BringIntoView%2A>でメソッドが呼び出さ、<xref:System.Windows.Controls.TreeViewItem>コントロール、<xref:System.Windows.Controls.TreeViewItem>とその親<xref:System.Windows.Controls.TreeViewItem>コントロールを展開します。 場合、<xref:System.Windows.Controls.TreeViewItem>は非表示または部分的に表示される、<xref:System.Windows.Controls.TreeView>表示するのにスクロールします。  
  
<a name="TreeViewItem_Selection"></a>   
## <a name="treeviewitem-selection"></a>TreeViewItem の選択  
 ユーザーがクリックしたとき、<xref:System.Windows.Controls.TreeViewItem>して選択し、コントロール、<xref:System.Windows.Controls.TreeViewItem.Selected>イベントが発生して、その<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティに設定されている`true`です。 <xref:System.Windows.Controls.TreeViewItem>にもなります、<xref:System.Windows.Controls.TreeView.SelectedItem%2A>の<xref:System.Windows.Controls.TreeView>コントロール。 逆に、選択範囲が変更された時点から、<xref:System.Windows.Controls.TreeViewItem>コントロール、その<xref:System.Windows.Controls.TreeViewItem.Unselected>イベントが発生したとその<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティに設定されている`false`です。  
  
 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティを<xref:System.Windows.Controls.TreeView>コントロールは読み取り専用プロパティをそのため、設定することはできません明示的にします。 <xref:System.Windows.Controls.TreeView.SelectedItem%2A>プロパティが設定されて、ユーザーがクリックした場合、<xref:System.Windows.Controls.TreeViewItem>コントロール場合や、<xref:System.Windows.Controls.TreeViewItem.IsSelected%2A>プロパティに設定されている`true`上、<xref:System.Windows.Controls.TreeViewItem>コントロール。  
  
 使用して、<xref:System.Windows.Controls.TreeView.SelectedValuePath%2A>プロパティを指定する、<xref:System.Windows.Controls.TreeView.SelectedValue%2A>の<xref:System.Windows.Controls.TreeView.SelectedItem%2A>です。 詳細については、「[SelectedValue、SelectedValuePath、および SelectedItem を使用する](../../../../docs/framework/wpf/controls/how-to-use-selectedvalue-selectedvaluepath-and-selecteditem.md)」を参照してください。  
  
 イベント ハンドラーに登録することができます、 <xref:System.Windows.Controls.TreeView.SelectedItemChanged> 、選択した時期を決定するためにイベント<xref:System.Windows.Controls.TreeViewItem>変更します。 <xref:System.Windows.RoutedPropertyChangedEventArgs%601>ハンドラーが指定のイベントに提供される、 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.OldValue%2A>、直前の選択は、 <xref:System.Windows.RoutedPropertyChangedEventArgs%601.NewValue%2A>、これは、現在の選択します。 アプリケーションまたはユーザーが以前または現在の選択を行っていない場合、どちらの値も `null` にできます。  
  
<a name="TreeView_Style"></a>   
## <a name="treeview-style"></a>TreeView のスタイル  
 既定のスタイル、<xref:System.Windows.Controls.TreeView>コントロールの配置内で、<xref:System.Windows.Controls.StackPanel>オブジェクトを含む、<xref:System.Windows.Controls.ScrollViewer>コントロール。 設定すると、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>のプロパティ、 <xref:System.Windows.Controls.TreeView>、これらの値のサイズを使用して、<xref:System.Windows.Controls.StackPanel>を表示するオブジェクト、<xref:System.Windows.Controls.TreeView>です。 表示領域よりも大きい場合は、コンテンツを表示する、<xref:System.Windows.Controls.ScrollViewer>自動的に表示をユーザーがスクロールできるように、<xref:System.Windows.Controls.TreeView>コンテンツ。  
  
 外観をカスタマイズする、<xref:System.Windows.Controls.TreeViewItem>コントロールを設定、<xref:System.Windows.FrameworkElement.Style%2A>プロパティをカスタム<xref:System.Windows.Style>です。  
  
 次の例は、設定する方法を示します、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.FontSize%2A>プロパティの値を<xref:System.Windows.Controls.TreeViewItem>コントロールを使用して、<xref:System.Windows.FrameworkElement.Style%2A>です。  
  
 [!code-xaml[TreeViewSimple#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSimple/CS/Window1.xaml#8)]  
  
<a name="Adding_Images_and_oOther_Content_to_TreeView_Items"></a>   
## <a name="adding-images-and-other-content-to-treeview-items"></a>TreeView 項目へのイメージとその他のコンテンツの追加  
 1 つ以上のオブジェクトを含めることができます、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>のコンテンツ、<xref:System.Windows.Controls.TreeViewItem>です。 複数のオブジェクトを含める<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>など、レイアウト コントロール内のオブジェクトを囲む、コンテンツ、<xref:System.Windows.Controls.Panel>または<xref:System.Windows.Controls.StackPanel>です。  
  
 次の例は、定義する方法を示します、<xref:System.Windows.Controls.HeaderedItemsControl.Header%2A>の<xref:System.Windows.Controls.TreeViewItem>として、<xref:System.Windows.Controls.CheckBox>と<xref:System.Windows.Controls.TextBlock>両方で囲むこと、<xref:System.Windows.Controls.DockPanel>コントロール。  
  
 [!code-xaml[TreeViewSnips#TVIHeader](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewSnips/CSharp/Window1.xaml#tviheader)]  
  
 次の例は、定義する方法を示します、<xref:System.Windows.DataTemplate>を格納している、<xref:System.Windows.Controls.Image>と<xref:System.Windows.Controls.TextBlock>で囲まれている、<xref:System.Windows.Controls.DockPanel>コントロール。 使用することができます、<xref:System.Windows.DataTemplate>を設定する、<xref:System.Windows.Controls.HeaderedItemsControl.HeaderTemplate%2A>または<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>の<xref:System.Windows.Controls.TreeViewItem>です。  
  
 [!code-xaml[TreeViewDataBinding#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TreeViewDataBinding/CSharp/Window1.xaml#6)]  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Controls.TreeView>  
 <xref:System.Windows.Controls.TreeViewItem>  
 [方法トピック](../../../../docs/framework/wpf/controls/treeview-how-to-topics.md)  
 [WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)
