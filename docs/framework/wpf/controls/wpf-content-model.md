---
title: "WPF のコンテンツ モデル | Microsoft Docs"
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
  - "任意のコンテンツのクラス [WPF], コンテンツ モデル"
  - "コンテンツの表示 [WPF], コントロール"
  - "コンテンツ モデル [WPF], コントロール"
  - "ContentControl クラス [WPF], 表示 (コンテンツを)"
  - "コントロール [WPF], 表示 (テキストを)"
  - "コントロール [WPF], 書式設定 (テキストの)"
  - "表示 (コンテンツを) [WPF]"
  - "UIElement クラス [WPF], 表示 (コンテンツを)"
ms.assetid: 214da5ef-547a-4cf8-9b07-4aa8a0e52cdd
caps.latest.revision: 17
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 16
---
# WPF のコンテンツ モデル
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] は、コンテンツのさまざまな種類の表示が主な目的である、数多くのコントロール型やコントロールに似た型を提供するプレゼンテーション プラットフォームです。  使用するコントロールまたは派生元として使用するコントロールを決定するには、各コントロールで最適に表示できるオブジェクトの種類を理解しておくことが重要です。  
  
 このトピックでは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール型とコントロールに似た型のコンテンツ モデルについて説明します。  コンテンツ モデルでは、コントロールで使用できるコンテンツが表されます。また、各コンテンツ モデルのコンテンツ プロパティについても示します。  コンテンツ プロパティは、オブジェクトのコンテンツの格納に使用されるプロパティです。  
  
 [!INCLUDE[autoOutline](../Token/autoOutline_md.md)]  
  
<a name="classes_that_contain_arbitrary_content"></a>   
## 任意のコンテンツを格納するクラス  
 コントロールの中には、文字列、<xref:System.DateTime> オブジェクト、追加項目のコンテナーである <xref:System.Windows.UIElement> など、任意の型のオブジェクトを格納できるものがあります。  たとえば、<xref:System.Windows.Controls.Button> にはイメージおよびテキストを格納できます。また、<xref:System.Windows.Controls.CheckBox> には <xref:System.DateTime.Now%2A?displayProperty=fullName> の値を格納できます。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、任意のコンテンツを格納できるクラスが 4 つあります。  <xref:System.Windows.Controls.Control> から継承するクラスの一覧を次の表に示します。  
  
|任意のコンテンツを格納するクラス|Content|  
|----------------------|-------------|  
|<xref:System.Windows.Controls.ContentControl>|単一の任意のオブジェクト。|  
|<xref:System.Windows.Controls.HeaderedContentControl>|任意のオブジェクトであるヘッダーと単一の項目。|  
|<xref:System.Windows.Controls.ItemsControl>|任意のオブジェクトのコレクション。|  
|<xref:System.Windows.Controls.HeaderedItemsControl>|任意のオブジェクトであるヘッダーと項目のコレクション。|  
  
 これらのクラスから継承するコントロールは、同じ型のコンテンツを格納することができ、そのコンテンツを同じ方法で扱うことができます。  次の図は、イメージやテキストを格納する各コンテンツ モデルのコントロールを示しています。  
  
 ![Button、GroupBox、Listbax、TreeViewItem](../../../../docs/framework/wpf/controls/media/controlcontentmodelimagetextinto.PNG "ControlContentModelImageTextInto")  
  
### 単一の任意のオブジェクトを格納するコントロール  
 <xref:System.Windows.Controls.ContentControl> クラスには、任意のコンテンツの 1 つが格納されます。  コンテンツ プロパティは <xref:System.Windows.Controls.ContentControl.Content%2A> です。  次に示すのは <xref:System.Windows.Controls.ContentControl> から継承し、そのコンテンツ モデルを使用するコントロールです。  
  
-   <xref:System.Windows.Controls.Button>  
  
-   <xref:System.Windows.Controls.Primitives.ButtonBase>  
  
-   <xref:System.Windows.Controls.CheckBox>  
  
-   <xref:System.Windows.Controls.ComboBoxItem>  
  
-   <xref:System.Windows.Controls.ContentControl>  
  
-   <xref:System.Windows.Controls.Frame>  
  
-   <xref:System.Windows.Controls.GridViewColumnHeader>  
  
-   <xref:System.Windows.Controls.GroupItem>  
  
-   <xref:System.Windows.Controls.Label>  
  
-   <xref:System.Windows.Controls.ListBoxItem>  
  
-   <xref:System.Windows.Controls.ListViewItem>  
  
-   <xref:System.Windows.Navigation.NavigationWindow>  
  
-   <xref:System.Windows.Controls.RadioButton>  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton>  
  
-   <xref:System.Windows.Controls.ScrollViewer>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBarItem>  
  
-   <xref:System.Windows.Controls.Primitives.ToggleButton>  
  
-   <xref:System.Windows.Controls.ToolTip>  
  
-   <xref:System.Windows.Controls.UserControl>  
  
-   <xref:System.Windows.Window>  
  
 次の図は、<xref:System.Windows.Controls.ContentControl.Content%2A> が文字列、<xref:System.DateTime> オブジェクト、<xref:System.Windows.Shapes.Rectangle>、および <xref:System.Windows.Controls.Panel> \(<xref:System.Windows.Shapes.Ellipse> と <xref:System.Windows.Controls.TextBlock> を格納する\) が設定された 4 つのボタンを示しています。  
  
 ![4 つのボタン](../../../../docs/framework/wpf/controls/media/controlcontentmodelbuttons.png "ControlContentModelButtons")  
異なる型のコンテンツを持つ 4 つのボタン  
  
 <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティの設定方法の例については、<xref:System.Windows.Controls.ContentControl> のトピックを参照してください。  
  
### ヘッダーおよび単一の任意のオブジェクトを格納するコントロール  
 <xref:System.Windows.Controls.ContentControl> から継承される <xref:System.Windows.Controls.HeaderedContentControl> クラスは、ヘッダーを使用してコンテンツを表示します。  コンテンツ プロパティ <xref:System.Windows.Controls.ContentControl.Content%2A> を <xref:System.Windows.Controls.ContentControl> から継承し、<xref:System.Object> 型の <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> プロパティを定義します。その結果、ヘッダーとコンテンツの両者が任意のオブジェクトとなることができます。  
  
 次に示すのは <xref:System.Windows.Controls.HeaderedContentControl> から継承し、そのコンテンツ モデルを使用するコントロールです。  
  
-   <xref:System.Windows.Controls.Expander>  
  
-   <xref:System.Windows.Controls.GroupBox>  
  
-   <xref:System.Windows.Controls.TabItem>  
  
 次の図に、2 つの <xref:System.Windows.Controls.TabItem> オブジェクトを示します。  1 つ目の <xref:System.Windows.Controls.TabItem> には <xref:System.Windows.UIElement> オブジェクトが <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> および <xref:System.Windows.Controls.ContentControl.Content%2A> として付いています。  <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> は <xref:System.Windows.Shapes.Ellipse> と <xref:System.Windows.Controls.TextBlock> を格納する <xref:System.Windows.Controls.StackPanel> に設定されています。  <xref:System.Windows.Controls.ContentControl.Content%2A> は <xref:System.Windows.Controls.TextBlock> と <xref:System.Windows.Controls.Label> を格納する <xref:System.Windows.Controls.StackPanel> に設定されています。  2 つ目の <xref:System.Windows.Controls.TabItem> の場合、<xref:System.Windows.Controls.HeaderedContentControl.Header%2A> には文字列、<xref:System.Windows.Controls.ContentControl.Content%2A> には <xref:System.Windows.Controls.TextBlock> が付いています。  
  
 ![TabControl](../../../../docs/framework/wpf/controls/media/controlcontentmodelteabitem.PNG "ControlContentModelTeabItem")  
Header プロパティで異なる型を使用する TabControl  
  
 <xref:System.Windows.Controls.TabItem> オブジェクトを作成する方法の例については、<xref:System.Windows.Controls.HeaderedContentControl> のトピックを参照してください。  
  
### 任意のオブジェクトのコレクションを格納するコントロール  
 <xref:System.Windows.Controls.Control> から継承する <xref:System.Windows.Controls.ItemsControl> クラスには、文字列、オブジェクト、他の要素などの複数の項目を格納できます。  このクラスのコンテンツ プロパティは <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> と <xref:System.Windows.Controls.ItemsControl.Items%2A> です。  <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> は通常、データ収集時に <xref:System.Windows.Controls.ItemsControl> を取得するために使用されます。  コレクションを使用して <xref:System.Windows.Controls.ItemsControl> を取得しない場合は、<xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティを使用して項目を追加できます。  
  
 次に示すのは <xref:System.Windows.Controls.ItemsControl> から継承し、そのコンテンツ モデルを使用するコントロールです。  
  
-   <xref:System.Windows.Controls.Menu>  
  
-   <xref:System.Windows.Controls.Primitives.MenuBase>  
  
-   <xref:System.Windows.Controls.ContextMenu>  
  
-   <xref:System.Windows.Controls.ComboBox>  
  
-   <xref:System.Windows.Controls.ItemsControl>  
  
-   <xref:System.Windows.Controls.ListBox>  
  
-   <xref:System.Windows.Controls.ListView>  
  
-   <xref:System.Windows.Controls.TabControl>  
  
-   <xref:System.Windows.Controls.TreeView>  
  
-   <xref:System.Windows.Controls.Primitives.Selector>  
  
-   <xref:System.Windows.Controls.Primitives.StatusBar>  
  
 次の図は、これらの型の項目を含む <xref:System.Windows.Controls.ListBox> を示しています。  
  
-   文字列  
  
-   <xref:System.DateTime> オブジェクト。  
  
-   <xref:System.Windows.UIElement>。  
  
-   <xref:System.Windows.Shapes.Ellipse> と <xref:System.Windows.Controls.TextBlock> が格納された <xref:System.Windows.Controls.Panel>。  
  
 ![4 種類の内容を含む ListBox](../../../../docs/framework/wpf/controls/media/controlcontentmodellistbox2.PNG "ControlContentModelListBox2")  
さまざまな種類のオブジェクトを格納する ListBox  
  
### ヘッダーと任意のオブジェクトのコレクションを格納するコントロール  
 <xref:System.Windows.Controls.ItemsControl> から継承する <xref:System.Windows.Controls.HeaderedItemsControl> クラスには、文字列、オブジェクト、ヘッダー、他の要素などの複数の項目を格納できます。  このクラスは <xref:System.Windows.Controls.ItemsControl> のコンテンツ プロパティである <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> と <xref:System.Windows.Controls.ItemsControl.Items%2A> を継承し、任意のオブジェクトとなるように <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> プロパティを定義します。  
  
 次に示すのは <xref:System.Windows.Controls.HeaderedItemsControl> から継承し、そのコンテンツ モデルを使用するコントロールです。  
  
-   <xref:System.Windows.Controls.MenuItem>  
  
-   <xref:System.Windows.Controls.ToolBar>  
  
-   <xref:System.Windows.Controls.TreeViewItem>  
  
<a name="classes_that_contain_a_collection_of_uielement_objects"></a>   
## UIElement オブジェクトのコレクションを格納するクラス  
 <xref:System.Windows.Controls.Panel> クラスは、子である <xref:System.Windows.UIElement> オブジェクトの配置および配列を行います。  コンテンツ プロパティは <xref:System.Windows.Controls.Panel.Children%2A> です。  
  
 次に示すのは <xref:System.Windows.Controls.Panel> クラスから継承し、そのコンテンツ モデルを使用するクラスです。  
  
-   <xref:System.Windows.Controls.Canvas>  
  
-   <xref:System.Windows.Controls.DockPanel>  
  
-   <xref:System.Windows.Controls.Grid>  
  
-   <xref:System.Windows.Controls.Primitives.TabPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarOverflowPanel>  
  
-   <xref:System.Windows.Controls.Primitives.ToolBarPanel>  
  
-   <xref:System.Windows.Controls.Primitives.UniformGrid>  
  
-   <xref:System.Windows.Controls.StackPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingPanel>  
  
-   <xref:System.Windows.Controls.VirtualizingStackPanel>  
  
-   <xref:System.Windows.Controls.WrapPanel>  
  
 詳細については、「[パネルの概要](../../../../docs/framework/wpf/controls/panels-overview.md)」を参照してください。  
  
<a name="classes_that_affects_the_appearance_of_a_uielement"></a>   
## UIElement の外観に影響するクラス  
 <xref:System.Windows.Controls.Decorator> クラスは、単一の子である <xref:System.Windows.UIElement> 上またはその周囲に視覚的な効果を適用します。  コンテンツ プロパティは <xref:System.Windows.Controls.Decorator.Child%2A> です。  次に示すのは <xref:System.Windows.Controls.Decorator> から継承し、そのコンテンツ モデルを使用するクラスです。  
  
-   <xref:System.Windows.Documents.AdornerDecorator>  
  
-   <xref:System.Windows.Controls.Border>  
  
-   <xref:System.Windows.Controls.Primitives.BulletDecorator>  
  
-   <xref:Microsoft.Windows.Themes.ButtonChrome>  
  
-   <xref:Microsoft.Windows.Themes.ClassicBorderDecorator>  
  
-   <xref:System.Windows.Controls.InkPresenter>  
  
-   <xref:Microsoft.Windows.Themes.ListBoxChrome>  
  
-   <xref:Microsoft.Windows.Themes.SystemDropShadowChrome>  
  
-   <xref:System.Windows.Controls.Viewbox>  
  
 周囲を <xref:System.Windows.Controls.Border> で装飾した <xref:System.Windows.Controls.TextBox> を次の図に示します。  
  
 ![境界線が黒の TextBox](../../../../docs/framework/wpf/controls/media/layout-border-around-textbox.png "Layout\_Border\_around\_TextBox")  
境界線のある TextBlock  
  
<a name="classes_that_provides_visual_feedback_about_a_uielement"></a>   
## UIElement の視覚的フィードバックを提供するクラス  
 <xref:System.Windows.Documents.Adorner> クラスは、ユーザーに視覚上の手掛かりを示します。  たとえば、<xref:System.Windows.Documents.Adorner> を使用すると、要素に機能ハンドルを追加したり、コントロールに関する状態情報を提供したりできます。  <xref:System.Windows.Documents.Adorner> クラスでは、独自の装飾を作成できるようにするフレームワークが用意されています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、実装済みの装飾は用意されていません。  詳細については、「[装飾の概要](../../../../docs/framework/wpf/controls/adorners-overview.md)」を参照してください。  
  
<a name="classes_that_enable_users_to_enter_text"></a>   
## ユーザーがテキストを入力できるようにするクラス  
 WPF には、ユーザーがテキストを入力できるようにするための主要なコントロールが 3 つ用意されています。  各コントロールは、テキストをそれぞれの形式で表示できます。  次の表に、これら 3 つのテキスト関連のコントロールを、テキストの表示形式およびテキストを格納するプロパティと共に示します。  
  
|Control|テキストの表示形式|コンテンツ プロパティ|  
|-------------|---------------|-----------------|  
|<xref:System.Windows.Controls.TextBox>|書式なしテキスト|<xref:System.Windows.Controls.TextBox.Text%2A>|  
|<xref:System.Windows.Controls.RichTextBox>|書式設定されたテキスト|<xref:System.Windows.Controls.RichTextBox.Document%2A>|  
|<xref:System.Windows.Controls.PasswordBox>|非表示のテキスト \(マスクされた文字\)|<xref:System.Windows.Controls.PasswordBox.Password%2A>|  
  
<a name="classes_that_display_text"></a>   
## テキストを表示するクラス  
 書式なしのテキストまたは書式設定されたテキストを表示できるクラスはいくつかあります。  短いテキストを表示する場合は、<xref:System.Windows.Controls.TextBlock> を使用します。  長いテキストを表示する場合は、<xref:System.Windows.Controls.FlowDocumentReader> コントロール、<xref:System.Windows.Controls.FlowDocumentPageViewer> コントロールまたは <xref:System.Windows.Controls.FlowDocumentScrollViewer> コントロールを使用します。  
  
 <xref:System.Windows.Controls.TextBlock> には、<xref:System.Windows.Controls.TextBlock.Text%2A> および <xref:System.Windows.Controls.TextBlock.Inlines%2A> という 2 つのコンテンツ プロパティがあります。  表示するテキストに一貫性のある書式を適用する場合は、<xref:System.Windows.Controls.TextBlock.Text%2A> プロパティの使用が適しています。  テキスト全体で異なる書式を使用する場合は、<xref:System.Windows.Controls.TextBlock.Inlines%2A> プロパティを使用します。  <xref:System.Windows.Controls.TextBlock.Inlines%2A> プロパティは、テキストの書式を指定する <xref:System.Windows.Documents.Inline> オブジェクトのコレクションです。  
  
 <xref:System.Windows.Controls.FlowDocumentReader>、<xref:System.Windows.Controls.FlowDocumentPageViewer>、および <xref:System.Windows.Controls.FlowDocumentScrollViewer> クラスのコンテンツ プロパティを次の表に示します。  
  
|Control|コンテンツ プロパティ|コンテンツ プロパティの型|  
|-------------|-----------------|-------------------|  
|<xref:System.Windows.Controls.FlowDocumentPageViewer>|Document|<xref:System.Windows.Documents.IDocumentPaginatorSource>|  
|<xref:System.Windows.Controls.FlowDocumentReader>|Document|<xref:System.Windows.Documents.FlowDocument>|  
|<xref:System.Windows.Controls.FlowDocumentScrollViewer>|Document|<xref:System.Windows.Documents.FlowDocument>|  
  
 <xref:System.Windows.Documents.FlowDocument> では <xref:System.Windows.Documents.IDocumentPaginatorSource> インターフェイスを実装します。このため、3 つのクラスはすべて <xref:System.Windows.Documents.FlowDocument> をコンテンツとして受け取ることができます。  
  
<a name="classes_that_format_text"></a>   
## テキストの書式を設定するクラス  
 <xref:System.Windows.Documents.TextElement> およびその関連クラスでは、テキストの書式を設定できます。  <xref:System.Windows.Documents.TextElement> オブジェクトには、<xref:System.Windows.Controls.TextBlock> オブジェクトおよび <xref:System.Windows.Documents.FlowDocument> オブジェクトでテキストを格納し、その書式を設定できます。  <xref:System.Windows.Documents.TextElement> オブジェクトの主要な型は <xref:System.Windows.Documents.Block> 要素および <xref:System.Windows.Documents.Inline> 要素の 2 つです。  <xref:System.Windows.Documents.Block> 要素は、段落や一覧などの 1 つのテキスト ブロックを表します。  <xref:System.Windows.Documents.Inline> 要素は、ブロック内のテキストの部分を表します。  多くの <xref:System.Windows.Documents.Inline> クラスでは、テキストに適用される書式を指定します。  それぞれの <xref:System.Windows.Documents.TextElement> には独自のコンテンツ モデルがあります。  詳細については、「[TextElement コンテンツ モデルの概要](../../../../docs/framework/wpf/advanced/textelement-content-model-overview.md)」を参照してください。  
  
## 参照  
 [詳細設定](../../../../docs/framework/wpf/advanced/index.md)