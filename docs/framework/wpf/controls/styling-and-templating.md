---
title: スタイルとテンプレート
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- triggers [WPF]
- styles [WPF], referencing
- event triggers [WPF]
- styles [WPF], prerequisites
- styles [WPF], declaring
- styles [WPF], overview
- styles [WPF], extending
- styles [WPF], triggers
- styles [WPF], event triggers
ms.assetid: 481765e5-5467-4a75-9f7b-e10e2ac410d9
ms.openlocfilehash: e39afea9fe11cdab9e5a6623499a96468aa9d091
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="styling-and-templating"></a>スタイルとテンプレート
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]スタイルとテンプレートは、開発者および設計者が視覚的に説得力のある効果を作成し、製品の一貫した外観を作成できる、一連の機能 (スタイル、テンプレート、トリガー、およびストーリーボード) を表します。 開発者や設計者は、アプリケーション単位で広範囲に外観をカスタマイズできますが、アプリケーション内およびアプリケーション間で外観の保守および共有を可能にするには、強力なスタイルとテンプレートのモデルが必要です。 [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] はそのモデルを提供します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のスタイル モデルの他の機能は、表示とロジックの分離です。 つまり、設計者は、開発者が C# や Visual Basic を使用してプログラミング ロジックについて作業するのと同時に [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] のみを使用してアプリケーションの外観について作業できます。  
  
 この概要では、アプリケーションのスタイルとテンプレートの側面に焦点を当てています。データ バインディングの概念については説明しません。 データ バインディングの詳細については、「[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
 また、スタイルとテンプレートの再利用を使用できるようにするリソースを理解する必要もあります。 リソースの詳細については、「[XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 
  
<a name="styling_and_templating_sample"></a>   
## <a name="styling-and-templating-sample"></a>スタイルとテンプレートのサンプル  
 この概要で使用するコード例は、次の図に示すように単純な写真のサンプルに基づいています。  
  
 ![Styled ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
 この単純な写真のサンプルは、スタイルとテンプレートを使用して、視覚的に説得力のあるユーザー エクスペリエンスを作成します。 サンプルの 2 つ<xref:System.Windows.Controls.TextBlock>要素、および<xref:System.Windows.Controls.ListBox>イメージの一覧にバインドされているコントロール。 完全なサンプルについては、「[Introduction to Styling and Templating Sample](http://go.microsoft.com/fwlink/?LinkID=160010)」を参照してください。  
  
<a name="styling_basics"></a>   
## <a name="style-basics"></a>スタイルの基本  
 考えることができます、<xref:System.Windows.Style>プロパティ値のセットを 1 つ以上の要素に適用する便利な方法として。 たとえば、次<xref:System.Windows.Controls.TextBlock>要素と、既定の外観。  
  
 [!code-xaml[StylingIntroSample_snippet#TextBlocks](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#textblocks)]  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbefore.PNG "StylingIntro_TextBlocksBefore")  
  
 などのプロパティを設定して既定の外観を変更することができます<xref:System.Windows.Controls.Control.FontSize%2A>と<xref:System.Windows.Controls.Control.FontFamily%2A>、各<xref:System.Windows.Controls.TextBlock>要素の直後です。 ただし、する場合は、 <xref:System.Windows.Controls.TextBlock> 、一部のプロパティを共有する要素を作成することができます、<xref:System.Windows.Style>で、`Resources`のセクションで、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルを次のように。  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb1)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 設定すると、<xref:System.Windows.Style.TargetType%2A>に自分のスタイルの<xref:System.Windows.Controls.TextBlock>型、スタイルはすべてに適用、<xref:System.Windows.Controls.TextBlock>ウィンドウ内の要素。  
  
 これで、<xref:System.Windows.Controls.TextBlock>要素は次のように表示されます。  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-textblocksbasestyle.PNG "StylingIntro_TextBlocksBaseStyle")  
  
### <a name="extending-styles"></a>スタイルの拡張  
 場合、2 つ<xref:System.Windows.Controls.TextBlock>など一部のプロパティ値を共有する要素、<xref:System.Windows.Controls.Control.FontFamily%2A>し、中央揃え<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>がテキストに追加のプロパティの「マイ ピクチャ」もできます。 次に示すように、これは、最初のスタイルに基づいている新しいスタイルを作成することで実現できます。  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#tb2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#tb2)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 `x:Key` に以前のスタイルが指定されたことがわかります。 設定するスタイルを適用する、<xref:System.Windows.FrameworkElement.Style%2A>プロパティを<xref:System.Windows.Controls.TextBlock>を`x:Key`次に示すように、値します。  
  
 [!code-xaml[StylingIntroSnippet#UIText](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uitext)]  
  
 これは、<xref:System.Windows.Controls.TextBlock>スタイルようになりました、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A>の値<xref:System.Windows.HorizontalAlignment.Center>、<xref:System.Windows.Controls.TextBlock.FontFamily%2A>の値`Comic Sans MS`、 <xref:System.Windows.Controls.TextBlock.FontSize%2A> 26, の値と<xref:System.Windows.Controls.TextBlock.Foreground%2A>値に設定、<xref:System.Windows.Media.LinearGradientBrush>例を示します。 も優先される、<xref:System.Windows.Controls.Control.FontSize%2A>基本スタイルの値。 1 つ以上を使用する必要がある場合<xref:System.Windows.Setter>で同じプロパティを設定、 <xref:System.Windows.Style>、<xref:System.Windows.Setter>は宣言されている最後が優先されます。  
  
 新機能を次に示します、<xref:System.Windows.Controls.TextBlock>要素はのようになります。  
  
 ![スタイル設定された TextBlocks](../../../../docs/framework/wpf/controls/media/stylingintro-textblocks.png "StylingIntro_TextBlocks")  
  
 これは、`TitleText`スタイル拡張用に作成された、スタイル、<xref:System.Windows.Controls.TextBlock>型です。 `x:Key` の値を使用して `x:Key` を持つスタイルを拡張することも可能です。 例については、提示された例を参照してください、<xref:System.Windows.Style.BasedOn%2A>プロパティです。  
  
### <a name="relationship-of-the-targettype-property-and-the-xkey-attribute"></a>TargetType プロパティと X:key 属性の関係  
 最初の例に示すように、設定、<xref:System.Windows.Style.TargetType%2A>プロパティを`TextBlock`スタイルを割り当てずに、`x:Key`すべてに適用されるスタイル<xref:System.Windows.Controls.TextBlock>要素。 ここでは、`x:Key` は暗黙的に `{x:Type TextBlock}` に設定されます。 つまり、明示的に設定する場合、`x:Key`以外の値を何も`{x:Type TextBlock}`、<xref:System.Windows.Style>がすべてに適用されない<xref:System.Windows.Controls.TextBlock>要素に自動的にします。 代わりに、スタイルを適用する必要があります (を使用して、`x:Key`値) に、<xref:System.Windows.Controls.TextBlock>要素に明示的にします。 Resources セクションには、自分のスタイルと、設定しないかどうか、<xref:System.Windows.Style.TargetType%2A>して自分のスタイルのプロパティを提供する必要があります、`x:Key`です。  
  
 既定値を提供するだけでなく、 `x:Key`、<xref:System.Windows.Style.TargetType%2A>プロパティ set アクセス操作子のプロパティを適用する種類を指定します。 指定しない場合、 <xref:System.Windows.Style.TargetType%2A>、内のプロパティを修飾する必要があります、<xref:System.Windows.Setter>構文を使用してクラス名を持つオブジェクト`Property="ClassName.Property"`です。 設定の例ではなく`Property="FontSize"`、設定する必要があります<xref:System.Windows.Setter.Property%2A>に`"TextBlock.FontSize"`または`"Control.FontSize"`です。  
  
 また、多く [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールは、その他の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの組み合わせで構成されます。 型のすべてのコントロールに適用されるスタイルを作成する場合、予期しない結果になる可能性があります。 対象とするスタイルを作成する場合など、<xref:System.Windows.Controls.TextBlock>に入力、 <xref:System.Windows.Window>、スタイルをすべて適用<xref:System.Windows.Controls.TextBlock> ウィンドウで、コントロール場合でも、<xref:System.Windows.Controls.TextBlock>など、他のコントロールの一部である、<xref:System.Windows.Controls.ListBox>です。  
  
### <a name="styles-and-resources"></a>スタイルとリソース  
 派生した任意の要素のスタイルを使用することができます<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 スタイルを宣言する最も一般的な方法は、前の例で示したように [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルの `Resources` セクションのリソースとしてです。 スタイルはリソースであるため、すべてのリソースに適用されるスコープの規則に従います。スタイルを宣言する場所は、スタイルを適用できる場所に影響します。 たとえば、アプリケーションの定義 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルのルート要素でスタイルを宣言すると、そのスタイルは、アプリケーションのどこでも使用できます。 ナビゲーション アプリケーションを作成し、アプリケーションの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルのいずれかでスタイルを宣言すると、そのスタイルはその [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルでのみ使用できます。 リソースのスコープの規則の詳細については、「[XAML Resources](../../../../docs/framework/wpf/advanced/xaml-resources.md)」を参照してください。  
  
 また、スタイルとリソースの詳細については、この概要で後述する「[共有リソースとテーマ](#styling_themes)」
を参照してください。  
  
### <a name="setting-styles-programmatically"></a>プログラムによるスタイルの設定  
 プログラムによって要素に名前付きのスタイルを割り当てるには、リソースのコレクションからスタイルを取得し、要素に割り当てます<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。 リソースのコレクション内の項目は型の注<xref:System.Object>です。 したがって、するスタイルを取得したをキャストする必要があります、<xref:System.Windows.Style>に割り当てる前に、<xref:System.Windows.FrameworkElement.Style%2A>プロパティです。 例については、定義された設定に`TitleText`のスタイルを設定、<xref:System.Windows.Controls.TextBlock>という`textblock1`、次の操作します。  
  
 [!code-csharp[StylingIntroSample_snippet#Code](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml.cs#code)]
 [!code-vb[StylingIntroSample_snippet#Code](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StylingIntroSample_snippet/visualbasic/window1.xaml.vb#code)]  
  
 スタイルが適用されると、封印され、変更できなくなります。 既に適用されているスタイルを動的に変更する場合、新しいスタイルを作成して既存のスタイルを置き換える必要があります。 詳細については、<xref:System.Windows.Style.IsSealed%2A> プロパティを参照してください。  
  
 カスタム ロジックに基づいて適用するスタイルを選択するオブジェクトを作成できます。 例については、提示された例を参照してください、<xref:System.Windows.Controls.StyleSelector>クラスです。  
  
<a name="styling_binding_dynamicresource"></a>   
### <a name="bindings-dynamic-resources-and-event-handlers"></a>バインディング、動的リソース、およびイベント ハンドラー  
 `Setter.Value` プロパティを使用して、[バインディング マークアップ拡張機能](../../../../docs/framework/wpf/advanced/binding-markup-extension.md)または[DynamicResource マークアップ拡張機能](../../../../docs/framework/wpf/advanced/dynamicresource-markup-extension.md)を指定できます。 詳細については、指定された例を参照して、<xref:System.Windows.Setter.Value%2A?displayProperty=nameWithType>プロパティです。  
  
 ここまでは、この概要は、プロパティ値を設定する setterの使用のみを説明しています。 スタイルではイベント ハンドラーも指定できます。 詳細については、「<xref:System.Windows.EventSetter>」を参照してください。  
  
<a name="styling_datatemplates"></a>   
## <a name="data-templates"></a>データ テンプレート  
 このサンプル アプリケーションでは、<xref:System.Windows.Controls.ListBox>写真の一覧にバインドされているコントロール。  
  
 [!code-xaml[StylingIntroSnippet#UIListBox](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#uilistbox)]  
  
 これは、<xref:System.Windows.Controls.ListBox>現在、次のようになります。  
  
 ![テンプレートの適用前の ListBox](../../../../docs/framework/wpf/controls/media/stylingintro-listboxbefore.png "StylingIntro_ListBoxBefore")  
  
 ほとんどのコントロールはいくつかの型のコンテンツを持ち、そのコンテンツは多くの場合バインディング先のデータから取得されます。 このサンプルでは、データは写真のリストです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用する、<xref:System.Windows.DataTemplate>データの視覚表現を定義します。 基本的に、新機能に配置する、<xref:System.Windows.DataTemplate>レンダリングされたアプリケーション内でデータがどのようにを決定します。  
  
 サンプル アプリケーションでは、各カスタム `Photo` オブジェクトには、イメージのファイル パスを指定する文字列型の `Source` プロパティがあります。 現在のところ、写真オブジェクトは、ファイルのパスとして表示されます。  
  
 作成する、イメージとして表示される写真に関して、<xref:System.Windows.DataTemplate>リソースとして。  
  
 [!code-xaml[StylingIntroSnippet#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources)]  
[!code-xaml[StylingIntroSnippet#DataTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#datatemplate)]  
[!code-xaml[StylingIntroSnippet#Resources2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSnippet/CS/window1.xaml#resources2)]  
  
 注意して、<xref:System.Windows.DataTemplate.DataType%2A>プロパティによく似ています、<xref:System.Windows.Style.TargetType%2A>のプロパティ、<xref:System.Windows.Style>です。 場合、<xref:System.Windows.DataTemplate>リソース セクションで、指定した場合、<xref:System.Windows.DataTemplate.DataType%2A>プロパティ型を割り当てられませんと、 `x:Key`、<xref:System.Windows.DataTemplate>はその型が表示されるたびに適用します。 割り当てるオプションが常にある、<xref:System.Windows.DataTemplate>で、`x:Key`として設定し、`StaticResource`プロパティ<xref:System.Windows.DataTemplate>などの型、<xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティまたは<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティです。  
  
 基本的には、<xref:System.Windows.DataTemplate>上記の例で定義するがあるときに、`Photo`オブジェクトとして表示されるはず、<xref:System.Windows.Controls.Image>内で、<xref:System.Windows.Controls.Border>です。 この<xref:System.Windows.DataTemplate>、次のようなアプリケーション。  
  
 ![写真のイメージ](../../../../docs/framework/wpf/controls/media/stylingintro-photosasimages.png "StylingIntro_PhotosAsImages")  
  
 データ テンプレートのモデルでは、その他の機能を提供します。 たとえばを使用して他のコレクションを格納するコレクションのデータを表示する場合、<xref:System.Windows.Controls.HeaderedItemsControl>などを入力、<xref:System.Windows.Controls.Menu>または<xref:System.Windows.Controls.TreeView>が、<xref:System.Windows.HierarchicalDataTemplate>です。 別のデータ テンプレートの機能は、<xref:System.Windows.Controls.DataTemplateSelector>を選択することができます、<xref:System.Windows.DataTemplate>に基づいてカスタム ロジックを使用します。 詳細については、「[Data Templating Overview](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。ここでは、さまざまなデータ テンプレート機能を詳しく説明します。  
  
<a name="styling_controltemplates"></a>   
## <a name="control-templates"></a>コントロール テンプレート  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、<xref:System.Windows.Controls.ControlTemplate>コントロールのコントロールの外観を定義します。 構造体とコントロールの外観を変更するには、新しい定義することによって<xref:System.Windows.Controls.ControlTemplate>コントロール。 多くの場合、これによって、独自のカスタム コントロールを作成する必要がない程度に十分な柔軟性を得られます。 詳細については、「[Customizing the Appearance of an Existing Control by Creating a ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
<a name="styling_triggers"></a>   
## <a name="triggers"></a>トリガー  
 トリガーは、プロパティ値が変更されたときまたはイベントが発生したときに、プロパティを設定するかまたはアニメーションなどのアクションを開始します。 <xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、および<xref:System.Windows.DataTemplate>がすべて、 `Triggers` 、一連のトリガーを含めることができるプロパティです。 さまざまな種類のトリガーがあります。  
  
### <a name="property-triggers"></a>プロパティ トリガー  
 A<xref:System.Windows.Trigger>セット プロパティが値またはプロパティの値に基づいてアクションを開始するいいますプロパティ トリガーします。  
  
 プロパティ トリガーを使用する方法を示すためには、行うことができます各<xref:System.Windows.Controls.ListBoxItem>が選択されている場合を除き、部分的に透過的です。 次のスタイルを設定、<xref:System.Windows.UIElement.Opacity%2A>の値、<xref:System.Windows.Controls.ListBoxItem>に`0.5`です。 ときに、<xref:System.Windows.Controls.ListBoxItem.IsSelected%2A>プロパティは`true`、ただし、<xref:System.Windows.UIElement.Opacity%2A>に設定されている`1.0`:  
  
 [!code-xaml[StylingIntroSample_snippet#Triggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#triggers)]  
[!code-xaml[StylingIntroSample_snippet#EndTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#endtriggers)]  
  
 この例では、<xref:System.Windows.Trigger>プロパティの値を設定することに注意してください、<xref:System.Windows.Trigger>クラスもあります、<xref:System.Windows.TriggerBase.EnterActions%2A>と<xref:System.Windows.TriggerBase.ExitActions%2A>アクションを実行するトリガーを有効にするプロパティです。  
  
 注意して、<xref:System.Windows.FrameworkElement.MaxHeight%2A>のプロパティ、<xref:System.Windows.Controls.ListBoxItem>に設定されている`75`です。 次の図では、3 番目の項目が選択した項目です。  
  
 ![Styled ListView](../../../../docs/framework/wpf/controls/media/stylingintro-triggers.png "StylingIntro_triggers")  
  
### <a name="eventtriggers-and-storyboards"></a>Eventtrigger とストーリー ボード  
 トリガーの別の種類は、<xref:System.Windows.EventTrigger>一連のイベントの発生に基づく操作を開始します。 たとえば、次<xref:System.Windows.EventTrigger>オブジェクトを指定する、マウス ポインターが入ったときに、 <xref:System.Windows.Controls.ListBoxItem>、<xref:System.Windows.FrameworkElement.MaxHeight%2A>プロパティの値にアニメーションを付ける`90`経由で、 `0.2` 2 番目の期間。 この項目からマウスを遠ざけると、`1` 秒間、元の値に戻ります。 方法を指定する必要はありません、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>値を<xref:System.Windows.ContentElement.MouseLeave>アニメーション。 これは、アニメーションが元の値を追跡できるからです。  
  
 [!code-xaml[StylingIntroSample_snippet#EventTriggers](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StylingIntroSample_snippet/CSharp/Window1.xaml#eventtriggers)]  
  
 詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 次の図では、マウスは3 番目の項目を指しています。  
  
 ![スタイル サンプル スクリーン ショット](../../../../docs/framework/wpf/controls/media/stylingintro-eventtriggers.png "StylingIntro_EventTriggers")  
  
### <a name="multitriggers-datatriggers-and-multidatatriggers"></a>MultiTriggers、DataTriggers、および MultiDataTriggers  
 加え<xref:System.Windows.Trigger>と<xref:System.Windows.EventTrigger>トリガーの他の種類があります。 <xref:System.Windows.MultiTrigger> 複数の条件に基づくプロパティ値を設定できます。 使用する<xref:System.Windows.DataTrigger>と<xref:System.Windows.MultiDataTrigger>条件のプロパティがデータ バインドの場合。  
  
<a name="styling_themes"></a>   
## <a name="shared-resources-and-themes"></a>共有リソースとテーマ  
 一般的な Windows Presentation Foundation (WPF) アプリケーションには、アプリケーション全体で適用されている複数のユーザー インターフェイス (UI) リソースがあります。 ひとまとめにして、このリソースのセットをアプリケーションのテーマとみなすことができます。 Windows Presentation Foundation (WPF)、サポート パッケージ ユーザー インターフェイス (UI) リソースをテーマとしてとしてカプセル化されたリソース ディクショナリを使用して、<xref:System.Windows.ResourceDictionary>クラスです。  
  
 Windows Presentation Foundation (WPF) のテーマは、任意の要素のビジュアルをカスタマイズするため、スタイル設定および Windows Presentation Foundation (WPF) を公開するテンプレートのメカニズムを使用して定義されます。  
  
 Windows Presentation Foundation (WPF) テーマ リソースは、埋め込まれたリソース ディクショナリに格納されます。 これらのリソース ディクショナリは署名されたアセンブリ内に埋め込む必要があり、コード自体と同じアセンブリまたはサイド バイ サイド アセンブリで埋め込むことができます。 PresentationFramework.dll、Windows Presentation Foundation (WPF) コントロールを含むアセンブリの場合は、テーマのリソースは、サイド バイ サイド アセンブリの系列には。  
  
 テーマは、要素のスタイルを検索するときに最後に検索する場所になります。 通常、検索は、まず適切なリソースを検索する要素のツリーをウォークしてから、アプリケーションのリソース コレクションがないか調べ、最後に、システム クエリを実行します。 この方法によって、アプリケーション開発者は、テーマに到達する前に、ツリー レベルまたはアプリケーション レベルで任意のオブジェクトのスタイルを再定義できます。  
  
 複数のアプリケーションでテーマを再利用できる個別ファイルとしてリソース ディクショナリを定義できます。 また、同じ種類のリソースだが値が異なる複数のリソース ディクショナリを定義して、交換できるテーマを作成することもできます。 アプリケーションをスキニングする場合、これらのスタイルまたはその他のリソースをアプリケーション レベルで再定義することを推奨します。  
  
 スタイル テンプレートなど、複数のアプリケーションで、リソースのセットを共有するには、作成、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ファイルし、定義、<xref:System.Windows.ResourceDictionary>です。 たとえば、[ControlTemplates サンプルを使用したスタイル](http://go.microsoft.com/fwlink/?LinkID=160041)の一部を示す次の図を見てください。  
  
 ![コントロール テンプレートの例](../../../../docs/framework/wpf/controls/media/stylingintro-controltemplateexamples.png "StylingIntro_ControlTemplateExamples")  
  
 サンプルの [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルを確認すると、すべてのファイルに次の項目が含まれていることがわかります。  
  
 [!code-xaml[ControlTemplateExamples#MergedDictionaries](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ControlTemplateExamples/CS/resources/button.xaml#mergeddictionaries)]  
  
 共有は`shared.xaml`を定義する、<xref:System.Windows.ResourceDictionary>一貫性のある外観のサンプルでコントロールできるようにする一連のスタイル、およびブラシ リソースを格納しています。  
  
 詳細については、「[Merged Resource Dictionaries](../../../../docs/framework/wpf/advanced/merged-resource-dictionaries.md)」を参照してください。  
  
 カスタム コントロールのテーマを作成する場合、「[Control Authoring Overview](../../../../docs/framework/wpf/controls/control-authoring-overview.md)」の「外部のコントロール ライブラリ」セクションを参照してください。  
  
## <a name="see-also"></a>関連項目  
 [WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [方法: ControlTemplate によって生成された要素を検索する](../../../../docs/framework/wpf/controls/how-to-find-controltemplate-generated-elements.md)  
 [DataTemplate によって生成された要素を検索する](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)
