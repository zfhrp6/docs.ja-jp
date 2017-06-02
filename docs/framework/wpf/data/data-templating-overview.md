---
title: "データ テンプレートの概要 | Microsoft Docs"
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
  - "データ バインド、テンプレート"
  - "データ バインディング、テンプレート"
  - "データのテンプレート"
  - "データ テンプレート"
ms.assetid: 0f4d9f8c-0230-4013-bd7b-e8e7fed01b4a
caps.latest.revision: 25
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# データ テンプレートの概要
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]データ テンプレート モデルは、非常に柔軟に、データの表示を定義します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロールには、データの表示のカスタマイズをサポートする組み込みの機能があります。 このトピックは、まずを定義する方法を示します、 <xref:System.Windows.DataTemplate>し、カスタム ロジックと階層データを表示するためのサポートに基づくテンプレートの選択などその他のデータ転送の各機能を紹介します。  
  
   
  
<a name="Prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックでは、データ テンプレート機能に重点を置いていて、データ バインディングの概念の概要ではありません。 基本的なデータ バインディングの概念については、次を参照してください。、[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)します。  
  
 <xref:System.Windows.DataTemplate>データの表示については、によって提供される多くの機能の&1; つ、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]スタイルとテンプレートのモデルです。 概要については、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用する方法などのスタイルとテンプレートのモデル、<xref:System.Windows.Style>コントロールのプロパティを設定するには、「、[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)トピックです。  
  
 さらを理解する必要が`Resources`、使用できるようにオブジェクトなど、これは本質的に<xref:System.Windows.Style>と<xref:System.Windows.DataTemplate>再利用できるようにします。 リソースの詳細については、次を参照してください。 [XAML リソース](../../../../docs/framework/wpf/advanced/xaml-resources.md)します。  
  
<a name="DataTemplating_Basic"></a>   
## <a name="data-templating-basics"></a>データ テンプレートの基本  
   
  
 その理由を示すために<xref:System.Windows.DataTemplate>が重要では、データ バインディングの例をしていきます。 私たちがこの例では、 <xref:System.Windows.Controls.ListBox>の一覧にバインドされた`Task`オブジェクトです。 各`Task`オブジェクトには、 `TaskName` (文字列)、 `Description` (文字列)、 `Priority` (int) と型のプロパティ`TaskType`、これは、`Enum`値を持つ`Home`と`Work`です。  
  
 [!code-xml[DataTemplatingIntro_snip#Resources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#resources)]  
[!code-xml[DataTemplatingIntro_snip#UI1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui1)]  
[!code-xml[DataTemplatingIntro_snip#UI2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#ui2)]  
  
<a name="without_a_datatemplate"></a>   
### <a name="without-a-datatemplate"></a>DataTemplate なし  
 なし、 <xref:System.Windows.DataTemplate>、当社<xref:System.Windows.Controls.ListBox>現在次のようにします。  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig1.png "DataTemplatingIntro_fig1")  
  
 ない場合の特定の手順では、何が起こっているか、 <xref:System.Windows.Controls.ListBox>既定の呼び出しによって`ToString`コレクションにオブジェクトを表示しようとするとします。 そのため場合、`Task`オブジェクトの上書き、 `ToString` 、メソッド、 <xref:System.Windows.Controls.ListBox>基になるコレクションに各ソース オブジェクトの文字列表現を表示します。  
  
 などの場合、`Task`クラスのオーバーライド、`ToString`メソッドこうすると、ここで`name`用のフィールド、`TaskName`プロパティ。  
  
 [!code-csharp[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Data.cs#tostring)]
 [!code-vb[DataTemplatingIntro_snip#ToString](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/data.vb#tostring)]  
  
 続いて、 <xref:System.Windows.Controls.ListBox>次のようになります。  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig2.png "DataTemplatingIntro_fig2")  
  
 ただし、制限があり、柔軟性は低いものです。 またにバインドする場合は、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データできませんをオーバーライドする`ToString`です。  
  
<a name="defining_simple_datatemplate"></a>   
### <a name="defining-a-simple-datatemplate"></a>単純な DataTemplate を定義します。  
 ソリューションは、定義する、 <xref:System.Windows.DataTemplate>します。 1 つの方法が設定するのには、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>のプロパティ、 <xref:System.Windows.Controls.ListBox>に、 <xref:System.Windows.DataTemplate>します。 指定した、 <xref:System.Windows.DataTemplate>データ オブジェクトの視覚的な構造になります。 次<xref:System.Windows.DataTemplate>は非常に単純です。 3 つの各項目が表示される指示を送るお<xref:System.Windows.Controls.TextBlock>内の要素、 <xref:System.Windows.Controls.StackPanel>します。 各<xref:System.Windows.Controls.TextBlock>要素がのプロパティにバインドされている、`Task`クラスです。  
  
 [!code-xml[DataTemplatingIntro_snip#Inline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#inline)]  
  
 このトピックの例の基になるデータのコレクションは、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)]オブジェクトです。 バインドする場合は、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]データは同じである、基本的な概念が、構文上のわずかな違いがあります。 例ではなく`Path=TaskName`、設定は<xref:System.Windows.Data.Binding.XPath%2A>に`@TaskName`(場合`TaskName`の属性です、[!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]ノード)。  
  
 これで、 <xref:System.Windows.Controls.ListBox>次のようになります。  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig3.png "DataTemplatingIntro_fig3")  
  
<a name="defining_datatemplate_as_a_resource"></a>   
### <a name="creating-the-datatemplate-as-a-resource"></a>DataTemplate をリソースとして作成します。  
 上記の例で定義した、 <xref:System.Windows.DataTemplate>インラインです。 次の例に示すように、再利用可能なオブジェクトにするためのリソース セクションで定義する方が一般的です。  
  
 [!code-xml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xml[DataTemplatingIntro_snip#AsResource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#asresource)]  
[!code-xml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 使用できるようになりました`myTaskTemplate`次の例のように、リソースとして。  
  
 [!code-xml[DataTemplatingIntro_snip#MyTaskTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#mytasktemplate)]  
  
 `myTaskTemplate` 、リソースを受け取るプロパティを持つその他のコントロールで使用することができますようになりました、 <xref:System.Windows.DataTemplate>型です。 に対して、上記で示される<xref:System.Windows.Controls.ItemsControl>などのオブジェクト、 <xref:System.Windows.Controls.ListBox>は、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>プロパティです。 <xref:System.Windows.Controls.ContentControl>オブジェクトの場合に、 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティです。  
  
<a name="Styling_DataType"></a>   
### <a name="the-datatype-property"></a>DataType プロパティ  
 <xref:System.Windows.DataTemplate>クラスには、 <xref:System.Windows.DataTemplate.DataType%2A>プロパティによく似ていますが、 <xref:System.Windows.Style.TargetType%2A>のプロパティ、<xref:System.Windows.Style>クラスです。 指定する代わりに、そのため、`x:Key`の<xref:System.Windows.DataTemplate>上記の例では、次を行うことができます。  
  
 [!code-xml[DataTemplatingIntro_snip#DataType](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#datatype)]  
  
 これは、 <xref:System.Windows.DataTemplate>すべてに自動的に適用される`Task`オブジェクトです。 ここで注意してください、`x:Key`が暗黙的に設定します。 そのため、これを割り当てる場合<xref:System.Windows.DataTemplate> 、`x:Key`値、暗黙的なをオーバーライドする`x:Key`と<xref:System.Windows.DataTemplate>自動的には適用されません。  
  
 バインドする場合、 <xref:System.Windows.Controls.ContentControl>のコレクションに`Task`オブジェクト、 <xref:System.Windows.Controls.ContentControl>上記は使いません<xref:System.Windows.DataTemplate>自動的にします。 これは、ためのバインディング、 <xref:System.Windows.Controls.ContentControl>コレクション全体または個々 のオブジェクトにバインドするかどうかを区別するためには情報が必要です。 場合、 <xref:System.Windows.Controls.ContentControl>の選択を追跡して、 <xref:System.Windows.Controls.ItemsControl>の種類を設定できます、<xref:System.Windows.Data.Binding.Path%2A>のプロパティ、 <xref:System.Windows.Controls.ContentControl>へのバインド"`/`"を現在のアイテムを興味のあることを示します。 例については、次を参照してください。[にバインドしてコレクションを選択に基づいて情報を表示](../../../../docs/framework/wpf/data/how-to-bind-to-a-collection-and-display-information-based-on-selection.md)します。 それ以外の場合、指定する必要があります、 <xref:System.Windows.DataTemplate>設定して明示的に、 <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>プロパティです。  
  
 <xref:System.Windows.DataTemplate.DataType%2A>がある場合、プロパティが特に便利ですが、 <xref:System.Windows.Data.CompositeCollection>データ オブジェクトのさまざまな種類のです。 例については、次を参照してください。 [Compositecollection](../../../../docs/framework/wpf/data/how-to-implement-a-compositecollection.md)します。  
  
<a name="adding_more_to_datatemplate"></a>   
## <a name="adding-more-to-the-datatemplate"></a>DataTemplate を複数追加します。  
 データが現在必要な情報が表示されますが、間違いなく改善の余地があります。 追加することで、プレゼンテーションを改善しましょう、<xref:System.Windows.Controls.Border>、<xref:System.Windows.Controls.Grid>、およびいくつか<xref:System.Windows.Controls.TextBlock>が表示されているデータを説明する要素。  
  
 [!code-xml[DataTemplatingIntro#AddingMore](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore)]  
[!code-xml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 次のスクリーン ショット、 <xref:System.Windows.Controls.ListBox>で修正された<xref:System.Windows.DataTemplate>:  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig4.png "DataTemplatingIntro_fig4")  
  
 設定することが<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>に<xref:System.Windows.HorizontalAlignment>上、 <xref:System.Windows.Controls.ListBox>アイテムの幅が全体の場所を取っているかどうかを確認します。  
  
 [!code-xml[DataTemplatingIntro_snip#Stretch](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#stretch)]  
  
 <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>プロパティに設定<xref:System.Windows.HorizontalAlignment>、 <xref:System.Windows.Controls.ListBox>今すぐ次のようにします。  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig5.png "DataTemplatingIntro_fig5")  
  
<a name="DataTrigger_to_Apply_Property_Values"></a>   
### <a name="use-datatriggers-to-apply-property-values"></a>DataTriggers を使用して、プロパティの値を適用するには  
 現在のプレゼンテーションには記載されているかどうか、`Task`ホーム タスクまたは office タスクです。 注意して、`Task`オブジェクトには、`TaskType`型のプロパティ`TaskType`、これは、列挙型値を持つ`Home`と`Work`です。  
  
 次の例では、 <xref:System.Windows.DataTrigger>設定、 <xref:System.Windows.Controls.Border.BorderBrush%2A>という名前の要素の`border`に`Yellow`場合、`TaskType`プロパティは`TaskType.Home`です。  
  
 [!code-xml[DataTemplatingIntro#DT](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#dt)]  
[!code-xml[DataTemplatingIntro#DataTrigger](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#datatrigger)]  
[!code-xml[DataTemplatingIntro#AddingMore2](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DataTemplatingIntro/xaml/window1.xaml#addingmore2)]  
  
 これで、アプリケーションは、次のようになります。 ホーム作業が黄色の枠線と共に表示され、水色の境界線で office タスクが表示されます。  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig6.png "DataTemplatingIntro_fig6")  
  
 この例では、 <xref:System.Windows.DataTrigger>を使用して、 <xref:System.Windows.Setter>プロパティ値を設定します。 トリガー クラスも持つ、 <xref:System.Windows.TriggerBase.EnterActions%2A>と<xref:System.Windows.TriggerBase.ExitActions%2A>アニメーションなどのアクションのセットを開始するためのプロパティです。 さらに、 <xref:System.Windows.MultiDataTrigger>複数のデータ バインドされたプロパティ値に基づいて、変更を適用できるようにするクラス。  
  
 バインドには、同じ効果を実現する方法も、 <xref:System.Windows.Controls.Border.BorderBrush%2A>プロパティを`TaskType`プロパティおよび使用する色を返す値コンバーターのに基づいて、`TaskType`値。 コンバーターを使用して上記の効果は、パフォーマンスの面で若干効率的です。 さらに、独自のコンバーターを作成する、柔軟性、独自のロジックを指定しているためです。 最終的には、どの手法を選択してでは、自分のシナリオと設定に依存します。 コンバーターを作成する方法については、次を参照してください。 <xref:System.Windows.Data.IValueConverter>します。  
  
<a name="what_belongs_in_datatemplate"></a>   
### <a name="what-belongs-in-a-datatemplate"></a>DataTemplate でどのようなものでしょうか。  
 内でトリガーを配置する前の例では、 <xref:System.Windows.DataTemplate>を使用して、 <xref:System.Windows.DataTemplate>.<xref:System.Windows.DataTemplate.Triggers%2A>プロパティです。 <xref:System.Windows.Setter>トリガーの要素のプロパティの値を設定します (、<xref:System.Windows.Controls.Border>要素) 内にある、 <xref:System.Windows.DataTemplate>します。 ただし場合、プロパティを`Setters`も問題が現在の範囲内にある要素のプロパティではない<xref:System.Windows.DataTemplate>を使用してプロパティを設定する適切な場合があります、<xref:System.Windows.Style>については、 <xref:System.Windows.Controls.ListBoxItem>クラス (にバインドするコントロールがある場合、 <xref:System.Windows.Controls.ListBox>)。 たい場合など、<xref:System.Windows.Trigger>をアニメーション化する、<xref:System.Windows.UIElement.Opacity%2A>値、アイテムのアイテムにマウスがポイントしたときにトリガーを定義する内で、 <xref:System.Windows.Controls.ListBoxItem>スタイル。 例については、次を参照してください。、[スタイルとテンプレート サンプルの概要](http://go.microsoft.com/fwlink/?LinkID=160010)します。  
  
 一般に、ことに注意、 <xref:System.Windows.DataTemplate>が、生成された各に適用される<xref:System.Windows.Controls.ListBoxItem> (詳細については、実際に適用される方法と場所は、次を参照してください。、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>ページです。)。 <xref:System.Windows.DataTemplate>はプレゼンテーション層とデータ オブジェクトの外観だけを考慮します。 ほとんどの場合、どのようなアイテムなどのプレゼンテーションの他のすべての側面とようになりますが選択されているか、または<xref:System.Windows.Controls.ListBox>の定義で、項目を lays が属していない、 <xref:System.Windows.DataTemplate>します。 例については、次を参照してください。、[スタイルとテンプレート、ItemsControl](#DataTemplating_ItemsControl)セクションです。  
  
<a name="Styling_StyleSelection"></a>   
## <a name="choosing-a-datatemplate-based-on-properties-of-the-data-object"></a>データ オブジェクトのプロパティに基づいてデータ テンプレートを選択します。  
 [DataType プロパティ](#Styling_DataType) セクションで、話し合い別のデータ オブジェクトのさまざまなデータ テンプレートを定義することができます。 ある場合に特に便利です、 <xref:System.Windows.Data.CompositeCollection>さまざまな種類のさまざまな種類の項目を含むコレクション。 [プロパティ値の適用を使用して DataTriggers](#DataTrigger_to_Apply_Property_Values)  セクションで、同じ種類のデータ オブジェクトのコレクションがある場合は、作成することを説明しました、 <xref:System.Windows.DataTemplate>し、トリガーを使用して、各データ オブジェクトのプロパティの値に基づいて変更を適用します。 ただし、トリガーでは、プロパティの値を適用またはアニメーションを開始することができますが、データ オブジェクトの構造を再構築する柔軟性が得られない。 一部のシナリオには、別に作成する必要があります<xref:System.Windows.DataTemplate>は同一のオブジェクト データの入力しますが、さまざまなプロパティがあります。  
  
 たとえば、`Task`オブジェクトには、`Priority`の値`1`、自分用の警告として処理するためにまったく異なる見た目にすることがあります。 この場合は、作成、 <xref:System.Windows.DataTemplate>高優先度を表示するため`Task`オブジェクトです。 次のコードを追加してみましょう<xref:System.Windows.DataTemplate> resources セクションにします。  
  
 [!code-xml[DataTemplatingIntro_snip#ImportantTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#importanttemplate)]  
  
 この例で、 <xref:System.Windows.DataTemplate>.<xref:System.Windows.FrameworkTemplate.Resources%2A>プロパティです。 内の要素が共有セクションに定義されているリソース、 <xref:System.Windows.DataTemplate>します。  
  
 選択するためのロジックを提供する<xref:System.Windows.DataTemplate>に基づいて、使用するのには、`Priority`値のデータ オブジェクトのサブクラスを作成<xref:System.Windows.Controls.DataTemplateSelector>させ、 <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>メソッドです。 次の例では、 <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>メソッドの値に基づいて、適切なテンプレートを返すロジックを提供する、`Priority`プロパティです。 返されるテンプレートは、エンベロープの資料を参照<xref:System.Windows.Window>要素。  
  
 [!code-csharp[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/TaskListDataTemplateSelector.cs#dtsclass)]
 [!code-vb[DataTemplatingIntro_snip#DTSClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/DataTemplatingIntro_snip/visualbasic/tasklistdatatemplateselector.vb#dtsclass)]  
  
 宣言できますし、`TaskListDataTemplateSelector`をリソースとして。  
  
 [!code-xml[DataTemplatingIntro_snip#R1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r1)]  
[!code-xml[DataTemplatingIntro_snip#DTS](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#dts)]  
[!code-xml[DataTemplatingIntro_snip#R2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#r2)]  
  
 テンプレート セレクター リソースを使用するには、それを割り当てる、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>のプロパティ、 <xref:System.Windows.Controls.ListBox>します。 <xref:System.Windows.Controls.ListBox>呼び出し、 <xref:System.Windows.Controls.DataTemplateSelector.SelectTemplate%2A>のメソッド、`TaskListDataTemplateSelector`の基になるコレクション内の項目ごとにします。 呼び出しは、アイテムのパラメーターとして、データ オブジェクトを渡します。 <xref:System.Windows.DataTemplate>によって返される、メソッドがそのデータ オブジェクトに適用されます。  
  
 [!code-xml[DataTemplatingIntro_snip#ItemTemplateSelector](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemtemplateselector)]  
  
 インプレースでのテンプレート セレクターで、 <xref:System.Windows.Controls.ListBox>次のように表示されます。  
  
 ![データ テンプレート サンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/datatemplatingintro-fig7.png "DataTemplatingIntro_fig7")  
  
 これには、この例の説明では終了します。 完全なサンプルを参照してください。[データ テンプレート サンプルの概要](http://go.microsoft.com/fwlink/?LinkID=160009)します。  
  
<a name="DataTemplating_ItemsControl"></a>   
## <a name="styling-and-templating-an-itemscontrol"></a>スタイルとテンプレート、ItemsControl  
 にもかかわらず、 <xref:System.Windows.Controls.ItemsControl>使用できる唯一のコントロール型ではない、 <xref:System.Windows.DataTemplate>にバインドする非常に一般的なシナリオでは、 <xref:System.Windows.Controls.ItemsControl>コレクションにします。 [DataTemplate に属しているどのような](#what_belongs_in_datatemplate)を説明したセクションの定義、 <xref:System.Windows.DataTemplate>がデータの表示で注意のみが必要です。 ないの使用に適した場合を知るために、 <xref:System.Windows.DataTemplate>によって提供されるさまざまなスタイルとテンプレートのプロパティを理解することが重要、 <xref:System.Windows.Controls.ItemsControl>します。 次の例は、これらの各プロパティの機能を示すために設計されています。 <xref:System.Windows.Controls.ItemsControl>この例では、同じバインドされている`Tasks`前の例のようにコレクションです。 デモの目的で、スタイルおよびテンプレートをこの例では、すべてインラインで宣言されてです。  
  
 [!code-xml[DataTemplatingIntro_snip#ItemsControlProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DataTemplatingIntro_snip/CSharp/Window1.xaml#itemscontrolproperties)]  
  
 以下は、例のスクリーン ショットが表示される場合です。  
  
 ![ItemsControl の例のスクリーン ショット](../../../../docs/framework/wpf/data/media/databinding-itemscontrolproperties.png "DataBinding_ItemsControlProperties")  
  
 注意して使用する代わりに、 <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>、使用することができます、 <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>します。 例については、前のセクションを参照してください。 使用する代わりに、同様に、 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>を使用するオプションがある、 <xref:System.Windows.Controls.ItemsControl.ItemContainerStyleSelector%2A>します。  
  
 2 つの他のスタイル関連プロパティ、 <xref:System.Windows.Controls.ItemsControl>ここでは表示されていない<xref:System.Windows.Controls.ItemsControl.GroupStyle%2A>と<xref:System.Windows.Controls.ItemsControl.GroupStyleSelector%2A>します。  
  
<a name="DataTemplating_HeirarchicalDataTemplate"></a>   
## <a name="support-for-hierarchical-data"></a>階層データのサポート  
 これまで説明してきました連結し、単一のコレクションを表示する方法について説明します。 あります他のコレクションを格納するコレクションがあります。 <xref:System.Windows.HierarchicalDataTemplate>クラスは併用できるように設計されています。 <xref:System.Windows.Controls.HeaderedItemsControl>などのデータを表示する型。 次の例で`ListLeagueList`の一覧は、`League`オブジェクトです。 各`League`オブジェクトには、`Name`およびさまざまな`Division`オブジェクトです。 各`Division`が、`Name`およびさまざまな`Team`オブジェクト、および各`Team`オブジェクトには、`Name`です。  
  
 [!code-xml[HierarchicalDataTemplateSnippet#HDT](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HierarchicalDataTemplateSnippet/CS/window1.xaml#hdt)]  
  
 使用する、例に示します<xref:System.Windows.HierarchicalDataTemplate>、その他のリストを含んでいるリストのデータを簡単に表示できます。 この例のスクリーン ショットを次に示します。  
  
 ![HierarchicalDataTemplate のサンプルのスクリーン ショット](../../../../docs/framework/wpf/data/media/databinding-hierarchicaldatatemplate.png "DataBinding_HierarchicalDataTemplate")  
  
## <a name="see-also"></a>関連項目  
 [データ バインディング](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)   
 [DataTemplate によって生成された要素を検索します。](../../../../docs/framework/wpf/data/how-to-find-datatemplate-generated-elements.md)   
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)   
 [データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)   
 [GridView 列ヘッダーのスタイルとテンプレートの概要](../../../../docs/framework/wpf/controls/gridview-column-header-styles-and-templates-overview.md)