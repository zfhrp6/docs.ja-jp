---
title: "スタイルとテンプレート | Microsoft Docs"
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
  - "トリガー"
  - "スタイルを参照します。"
  - "イベント トリガー"
  - "スタイル、前提条件"
  - "スタイルを宣言します。"
  - "スタイル, 概要"
  - "拡張スタイル"
  - "トリガーのスタイル"
  - "スタイル、イベント トリガー"
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
caps.latest.revision: 34
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 33
---
# スタイルとテンプレート
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]スタイルとテンプレートは、一連の開発者および設計者は、視覚的に説得力のある効果を作成し、それらの製品の一貫した外観を作成できるようにする機能 (スタイル、テンプレート、トリガー、およびストーリー ボード) を参照してください。 開発者や設計者は、アプリケーションの単位で広範囲に外観をカスタマイズできますが、強力なスタイルとテンプレートのモデルは内およびアプリケーション間での外観の保守や共有を許可する必要があります。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]そのモデルを提供します。  
  
 他の機能、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スタイルのモデルは、プレゼンテーションとロジックの分離。 つまり、デザイナーは、のみを使用してアプリケーションの外観に操作できること[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]c# または Visual Basic を使用して開発者の作業はプログラミング ロジックを同時にします。  
  
 この概要では、アプリケーションのスタイルとテンプレートの側面に焦点を当てていますを任意のデータ バインディングの概念については説明しません。 データ バインディングについては、次を参照してください。[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)します。  
  
 また、スタイルとテンプレートの再利用を使用できるように、リソースを理解する必要もあります。 リソースの詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)します。  
  
   
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>スタイルとテンプレート サンプル  
 この概要で使用するコード例は、次の図に示すように単純な写真のサンプルに基づいています。  
  
 ![ListView のスタイル](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 この単純な写真のサンプルでは、スタイルとテンプレートを使用して、視覚的に説得力のあるユーザー エクスペリエンスを作成します。 サンプルには&2; つ<xref:System.Windows.Controls.TextBlock>要素および<xref:System.Windows.Controls.ListBox>イメージの一覧にバインドされているコントロール。 完全なサンプルを参照してください。[スタイルとテンプレート サンプルの概要](http://go.microsoft.com/fwlink/?LinkID=160010)します。  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>スタイルの基本  
 考えることができます、<xref:System.Windows.Style>プロパティ値のセットを&1; つ以上の要素に適用する便利な方法として。 たとえば、次<xref:System.Windows.Controls.TextBlock>要素と、既定の外観。  
  
 [!code-xml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.png "StylingIntro_TextBlocksBefore")  
  
 などのプロパティを設定して既定の外観を変更する<xref:System.Windows.Controls.Control.FontSize%2A>と<xref:System.Windows.Controls.Control.FontFamily%2A>、各<xref:System.Windows.Controls.TextBlock>要素の直後です。 ただし、する場合は、 <xref:System.Windows.Controls.TextBlock>をいくつかのプロパティを共有する要素を作成、<xref:System.Windows.Style>で、`Resources`のセクション、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルを次のように。  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 設定すると、 <xref:System.Windows.Style.TargetType%2A>に自分のスタイルの<xref:System.Windows.Controls.TextBlock>すべてに種類、スタイルが適用されている、 <xref:System.Windows.Controls.TextBlock>ウィンドウ内の要素。  
  
 これで、 <xref:System.Windows.Controls.TextBlock>要素は次のように表示されます。  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.png "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>スタイルの拡張  
 場合、2 つ<xref:System.Windows.Controls.TextBlock>など、いくつかのプロパティ値を共有する要素、 <xref:System.Windows.Controls.Control.FontFamily%2A>で、中央揃えに<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>テキストの追加のプロパティに「マイ ピクチャ」もできます。 次に示すように、最初のスタイルに基づいている新しいスタイルを作成することで実現できます。  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 以前のスタイルが指定された通知、`x:Key`です。 設定するスタイルを適用する、<xref:System.Windows.FrameworkElement.Style%2A>プロパティを<xref:System.Windows.Controls.TextBlock>に、`x:Key`値に設定する次のようにします。  
  
 [!code-xml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 これ<xref:System.Windows.Controls.TextBlock>スタイルには、今すぐ、 <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>の値<xref:System.Windows.HorizontalAlignment>、 <xref:System.Windows.Controls.TextBlock.FontFamily%2A>の値`Comic Sans MS`、 <xref:System.Windows.Controls.TextBlock.FontSize%2A> 26 の値と<xref:System.Windows.Controls.TextBlock.Foreground%2A>値に設定、 <xref:System.Windows.Media.LinearGradientBrush>の例に示すようにします。 これは、上書きに注意してください、 <xref:System.Windows.Controls.Control.FontSize%2A>の基本のスタイルの値。 1 つ以上を使用する必要がある場合<xref:System.Windows.Setter>で同じプロパティを設定、<xref:System.Windows.Style>、 <xref:System.Windows.Setter>が宣言されている最後が優先されます。  
  
 どのような次の表示、 <xref:System.Windows.Controls.TextBlock>要素のようになります。  
  
 ![テキスト ブロック スタイルが適用された](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 これは、`TitleText`スタイル拡張用に作成されたスタイル、 <xref:System.Windows.Controls.TextBlock>型です。 スタイルを拡張することも、`x:Key`を使用して、`x:Key`値。 例については、使用されている例を参照してください、 <xref:System.Windows.Style.BasedOn%2A>プロパティです。  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType プロパティおよび X:key 属性の関係  
 最初の例に示すように設定、 <xref:System.Windows.Style.TargetType%2A>プロパティを`TextBlock`スタイルを割り当てることがなく、`x:Key`すべてに適用されるスタイル<xref:System.Windows.Controls.TextBlock>要素。 ここで、`x:Key`に暗黙的に設定されている`{x:Type TextBlock}`します。 これは、ため、明示的に設定する場合、`x:Key`以外の値が決まって`{x:Type TextBlock}`、<xref:System.Windows.Style>すべてに適用できません<xref:System.Windows.Controls.TextBlock>要素に自動的にします。 代わりに、スタイルを適用する必要があります (を使用して、`x:Key`値) に、 <xref:System.Windows.Controls.TextBlock>要素に明示的にします。 自分のスタイルは、resources セクションには、その設定しないでください、 <xref:System.Windows.Style.TargetType%2A>に対して自分のスタイル プロパティを提供する必要があります、`x:Key`です。  
  
 既定値を提供するだけでなく、 `x:Key`、 <xref:System.Windows.Style.TargetType%2A>プロパティ set アクセス操作子のプロパティを適用する種類を指定します。 指定しない場合、 <xref:System.Windows.Style.TargetType%2A>、内のプロパティを修飾する必要があります、 <xref:System.Windows.Setter>構文を使用してクラス名を持つオブジェクト`Property="ClassName.Property"`します。 たとえば、設定ではなく`Property="FontSize"`、設定する必要があります<xref:System.Windows.Setter.Property%2A>に`"TextBlock.FontSize"`または`"Control.FontSize"`です。  
  
 なお、それほど多く[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールは、その他の組み合わせで構成されます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールです。 型のすべてのコントロールに適用されるスタイルを作成する場合は、予期しない結果を得る可能性があります。 対象とするスタイルを作成する場合など、 <xref:System.Windows.Controls.TextBlock>入力、<xref:System.Windows.Window>、スタイルはすべてに適用<xref:System.Windows.Controls.TextBlock>  ウィンドウで、コントロール場合でも、 <xref:System.Windows.Controls.TextBlock>など、他のコントロールの一部では、 <xref:System.Windows.Controls.ListBox>します。  
  
### <a name="styles-and-resources"></a>スタイルとリソース  
 派生した任意の要素のスタイルを使用する<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>します。 スタイルを宣言する最も一般的な方法は、内のリソースとして、`Resources`セクション、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルは、前の例に示すようにします。 スタイルはリソースであるため、すべてのリソースに適用されるスコープの規則に従いますここで、スタイルを適用できる位置に影響を与えますスタイルを宣言します。 たとえば、アプリケーション定義のルート要素にスタイルを宣言する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイル、スタイルは、アプリケーションのどこにでも使用できます。 ナビゲーション アプリケーションを作成し、アプリケーションのいずれかでスタイルを宣言する場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]するだけで、ファイル、スタイルを使用できます[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルです。 スコープのリソースの規則の詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)します。  
  
 詳細については、スタイルとリソースを検索するさらに、[共有リソースとテーマ](#styling_themes)この概要で後述します。  
  
### <a name="setting-styles-programmatically"></a>プログラムによるスタイルの設定  
 プログラムを使用して要素を名前付きのスタイルを割り当てるには、するリソースのコレクションからスタイルを取得し、要素に割り当てる<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。 型のリソース コレクション内の項目がある注意<xref:System.Object>します。 そのため、取得したスタイルをキャストする必要があります、<xref:System.Windows.Style>に割り当てる前に、<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。 例については、定義された設定に`TitleText`に対するスタイル、 <xref:System.Windows.Controls.TextBlock>という名前`textblock1`、次の操作します。  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 スタイルが適用されると、それが封印されているをして変更することはできませんれます。 既に適用されているスタイルを動的に変更する場合に既存のものを置き換える新しいスタイルを作成する必要があります。 詳細については、次を参照してください。、 <xref:System.Windows.Style.IsSealed%2A>プロパティです。  
  
 カスタム ロジックに基づいてを適用するスタイルを選択するオブジェクトを作成することができます。 例については、使用されている例を参照してください、 <xref:System.Windows.Controls.StyleSelector>クラスです。  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>バインディング、動的リソース、およびイベント ハンドラー  
 使用できる、`Setter.Value`プロパティを指定する、[バインド マークアップ拡張機能の選択](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)または[DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)です。 詳細についてに付属する例を参照してください、 <xref:System.Windows.Setter.Value%2A?displayProperty=fullName>プロパティです。  
  
 ここまでは、この概要は、プロパティ値を設定する set アクセス操作子の使用のみを説明します。 スタイルのイベント ハンドラーを指定することもできます。 詳細については、次を参照してください。 <xref:System.Windows.EventSetter>します。  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>データ テンプレート  
 このサンプル アプリケーションでは、 <xref:System.Windows.Controls.ListBox>写真のリストにバインドされているコントロール。  
  
 [!code-xml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 これは、 <xref:System.Windows.Controls.ListBox>現在、次のようになります。  
  
 ![テンプレートの適用前に、の ListBox](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 ほとんどのコントロールはいくつかの種類のコンテンツを使用し、そのコンテンツは多くの場合にバインドするデータから取得しています。 このサンプルでは、データは、写真のリストです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用する、 <xref:System.Windows.DataTemplate>データのビジュアル表現を定義します。 基本的には、どのようなに配置すること、 <xref:System.Windows.DataTemplate>レンダリングされたアプリケーション内でデータがどのようにを決定します。  
  
 サンプル アプリケーションでは、各カスタム`Photo`オブジェクトには、`Source`イメージのファイル パスを指定する文字列型のプロパティです。 現在のところ、photo オブジェクトは、ファイルのパスとして表示されます。  
  
 イメージとして表示する写真を作成する、 <xref:System.Windows.DataTemplate>をリソースとして。  
  
 [!code-xml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 注意して、<xref:System.Windows.DataTemplate.DataType%2A>プロパティによく似ていますが、 <xref:System.Windows.Style.TargetType%2A>のプロパティ、<xref:System.Windows.Style>します。 場合、 <xref:System.Windows.DataTemplate>リソース セクションで、指定した場合、<xref:System.Windows.DataTemplate.DataType%2A>プロパティ型を割り当てないでくださいと、 `x:Key`、 <xref:System.Windows.DataTemplate>その型が表示されるたびに適用します。 割り当てるオプションが常にある、 <xref:System.Windows.DataTemplate>で、`x:Key`として設定し、`StaticResource`プロパティ<xref:System.Windows.DataTemplate>などの型、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティまたは<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティです。  
  
 基本的には、 <xref:System.Windows.DataTemplate>上の例ではされるように定義があるときに、`Photo`オブジェクトとして表示する必要があります、<xref:System.Windows.Controls.Image>内で、<xref:System.Windows.Controls.Border>します。 この<xref:System.Windows.DataTemplate>、次のようなアプリケーション。  
  
 ![フォト イメージ](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 データ テンプレートのモデルでは、その他の機能を提供します。 使用して他のコレクションを格納するコレクションのデータを表示する場合など、 <xref:System.Windows.Controls.HeaderedItemsControl>などの入力、<xref:System.Windows.Controls.Menu>または<xref:System.Windows.Controls.TreeView>がある、 <xref:System.Windows.HierarchicalDataTemplate>します。 別のデータ テンプレートの機能は、 <xref:System.Windows.Controls.DataTemplateSelector>を選択できます、 <xref:System.Windows.DataTemplate>に基づいてカスタム ロジックを使用します。 詳細については、次を参照してください。[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)、別のデータ転送の各機能の詳細情報について提供します。  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>コントロール テンプレート  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、 <xref:System.Windows.Controls.ControlTemplate>コントロールのコントロールの外観を定義します。 構造とコントロールの外観を変更するには、新しい定義することで<xref:System.Windows.Controls.ControlTemplate>コントロールです。 多くの場合、これは十分な柔軟性できるように、独自のカスタム コントロールを作成する必要はありません。 詳細については、次を参照してください。 [ControlTemplate を作成することで、既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)します。  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>トリガー  
 トリガーのプロパティを設定するか、プロパティ値が変更されたときにいずれかのイベントが発生したときに、アニメーションなどの操作を開始します。 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、および<xref:System.Windows.DataTemplate>すべてである、`Triggers`プロパティを一連のトリガーを含むことができます。 さまざまな種類のトリガーがあります。  
  
### <a name="property-triggers"></a>プロパティ トリガー  
 A<xref:System.Windows.Trigger>セット プロパティが値またはプロパティの値に基づいてアクションを開始すると、プロパティ トリガー呼びます。  
  
 プロパティ トリガーを使用する方法を示すためには、行うことができますそれぞれ<xref:System.Windows.Controls.ListBoxItem>が選択されている場合を除き、部分的に透明です。 次のスタイル設定、<xref:System.Windows.UIElement.Opacity%2A>の値、 <xref:System.Windows.Controls.ListBoxItem>に`0.5`します。 ときに、 <xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>プロパティは、 `true`、ただし、<xref:System.Windows.UIElement.Opacity%2A>に設定されている`1.0`:  
  
 [!code-xml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 この例では、<xref:System.Windows.Trigger>プロパティの値を設定することに注意してください、<xref:System.Windows.Trigger>クラスもあります、 <xref:System.Windows.TriggerBase.EnterActions%2A>と<xref:System.Windows.TriggerBase.ExitActions%2A>の操作を実行するためのトリガーを有効にするプロパティです。  
  
 注意して、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>のプロパティ、 <xref:System.Windows.Controls.ListBoxItem>に設定されている`75`します。 次の図では、3 番目の項目には、選択した項目です。  
  
 ![ListView のスタイル](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>Eventtrigger とストーリー ボード  
 トリガーの別の種類は、 <xref:System.Windows.EventTrigger>一連のイベントの発生に基づいてアクションを開始します。 たとえば、次<xref:System.Windows.EventTrigger>オブジェクトを指定する、マウス ポインターが入ったときに、 <xref:System.Windows.Controls.ListBoxItem>、 <xref:System.Windows.FrameworkElement.MaxHeight%2A>の値にプロパティをアニメーション化`90`経由で、 `0.2`&2; 番目の期間。 アイテムから離れた場所でマウスが移動するとき、プロパティは、一定の期間元の値を返します`1`2 番目です。 方法を指定する必要はありません、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>の値として、 <xref:System.Windows.ContentElement.MouseLeave>アニメーションです。 これは、アニメーションが元の値を追跡することが原因です。  
  
 [!code-xml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)します。  
  
 次の図には、マウスをポイントして、3 番目の項目にいます。  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers、DataTriggers、および MultiDataTriggers  
 他に、<xref:System.Windows.Trigger>と<xref:System.Windows.EventTrigger>トリガーの他の種類があります。 <xref:System.Windows.MultiTrigger>複数の条件に基づくプロパティ値を設定することができます。 使用する<xref:System.Windows.DataTrigger>と<xref:System.Windows.MultiDataTrigger>条件のプロパティがデータ バインドします。  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>共有リソースとテーマ  
 標準的な[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]アプリケーションは、アプリケーション全体でインストールされている複数のユーザー インターフェイス (UI) リソースを必要があります。 集合的に、このリソースのセットには、アプリケーションのテーマを検討できます。 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]では、パッケージのユーザー インターフェイス (UI) のリソースをテーマとしてとしてカプセル化されたリソース ディクショナリを使用して、 <xref:System.Windows.ResourceDictionary>クラスです。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]スタイルとテンプレートのメカニズムを使用してテーマを定義する[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]任意の要素のビジュアルをカスタマイズするために公開します。  
  
 [!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]テーマのリソースは、埋め込みリソース ディクショナリに格納されます。 署名されたアセンブリ内にこれらのリソース ディクショナリを埋め込む必要があり、いずれかの埋め込み可能コード自体と同じアセンブリまたはサイド バイ サイド アセンブリします。 PresentationFramework.dll、含まれているアセンブリの場合[!INCLUDE[TLA#tla_wpf](../../../../includes/tlasharptla-wpf-md.md)]コントロール、テーマのリソースは、一連のサイド バイ サイド アセンブリのです。  
  
 テーマは、要素のスタイルを検索するときに最後の場所になります。 通常、検索は適切なリソースを検索する要素のツリーをウォークしてからアプリケーションのリソース コレクションがないか調べ、最後に、システム クエリを実行します。 これは、方法により、アプリケーション開発者は、テーマに到達する前に、ツリーまたはアプリケーション レベルで任意のオブジェクトのスタイルを再定義します。  
  
 リソース ディクショナリは、複数のアプリケーションでテーマを再利用するための個々 のファイルとして定義できます。 同じ種類のリソースの値が異なる複数のリソース ディクショナリを定義することによって、交換できるテーマを作成することもできます。 これらのスタイルまたはその他のリソースをアプリケーション レベルで再定義するは、アプリケーションをスキニングの推奨されるアプローチです。  
  
 複数のアプリケーションでのスタイルおよびテンプレートを含むリソースのセットを共有するを作成、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルし、定義、 <xref:System.Windows.ResourceDictionary>します。 たとえばの一部を示しています次の図を見て、[サンプル全体について](http://go.microsoft.com/fwlink/?LinkID=160041):。  
  
 ![テンプレートの例の制御](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 確認する場合、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]サンプル内のファイル、すべてのファイルは、以下である確認は。  
  
 [!code-xml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 共有は`shared.xaml`を定義する、 <xref:System.Windows.ResourceDictionary>一貫性のある外観のサンプルでコントロールできるようにする一連のスタイルおよびブラシ リソースを格納しています。  
  
 詳細については、次を参照してください。[リソース ディクショナリのトピックとマージ](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)します。  
  
 カスタム コントロールのテーマを作成する場合、は、外部のコントロール ライブラリ セクションを参照して、[コントロールの作成の概要](../../../../docs/framework/wpf/controls/control-authoring-overview.md)します。  
  
## <a name="see-also"></a>関連項目  
 [WPF におけるパッケージの Uri](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [方法: ControlTemplate によって生成された要素を検索](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)   
 [DataTemplate によって生成された要素を検索します。](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)