---
title: "ControlTemplate の作成による既存のコントロールの外観のカスタマイズ | Microsoft Docs"
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
  - "コントロール コントラクト [WPF]"
  - "コントロール [WPF], 外観 (状態に応じた)"
  - "コントロール [WPF], 視覚的な構造の変更"
  - "ControlTemplate [WPF], カスタマイズ (既存のコントロールを)"
  - "スキンの適用 (コントロールに) [WPF]"
  - "テンプレート [WPF], カスタム (既存のコントロール用)"
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
<a name="introduction"></a> <xref:System.Windows.Controls.ControlTemplate> を使用して、コントロールの視覚的な構造および動作を指定します。  コントロールの外観をカスタマイズするには、コントロールの新しい <xref:System.Windows.Controls.ControlTemplate> を作成します。  <xref:System.Windows.Controls.ControlTemplate> を作成すると、既存のコントロールの機能を変更せずに外観だけを変更できます。  たとえば、アプリケーションのボタンを既定の四角形から丸い形に変更しても、今までどおりそのボタンで <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントが発生します。  
  
 このトピックでは、<xref:System.Windows.Controls.ControlTemplate> の各部分について説明し、<xref:System.Windows.Controls.Button> の単純な <xref:System.Windows.Controls.ControlTemplate> を作成する例を示します。さらに、コントロールの外観をカスタマイズできるように、コントロールのコントロール コントラクトについて詳しく解説します。  <xref:System.Windows.Controls.ControlTemplate> は [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で作成できるため、コードを一切記述しないでコントロールの外観を変更できます。  カスタム コントロールのテンプレートを作成するためにデザイナーを、 Microsoft Expression Blend などの使用できます。  このトピックでは、<xref:System.Windows.Controls.Button> の外観をカスタマイズする [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例を示し、トピックの最後では完全な例を示します。  Expression Blend の使用方法の詳細については、「[テンプレートをサポートするコントロールのスタイル処理](http://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
 次の図は、このトピックで作成する <xref:System.Windows.Controls.ControlTemplate> を使用した <xref:System.Windows.Controls.Button> を示しています。  
  
 ![カスタム コントロール テンプレート付きのボタン](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP\_ButtonNormal")  
カスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い境界線付きのボタン](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP\_ButtonMouseOver")  
カスタム コントロール テンプレートを使用したボタンにマウス ポインターを置いた図  
  
   
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックは、「[コントロール](../../../../docs/framework/wpf/controls/index.md)」で説明した、コントロールとスタイルを作成して使用する方法を理解していることを前提としています。  このトピックで紹介する概念は、<xref:System.Windows.Controls.UserControl> 以外の <xref:System.Windows.Controls.Control> クラスから継承する要素に適用されます。  <xref:System.Windows.Controls.ControlTemplate> は、<xref:System.Windows.Controls.UserControl> に適用できません。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## ControlTemplate の作成が必要な場合  
 コントロールには <xref:System.Windows.Controls.Border.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>、<xref:System.Windows.Controls.Control.FontFamily%2A> など、多数のプロパティがあり、これらのプロパティを設定することでコントロールの外観をさまざまな面から指定できますが、プロパティの設定から変更できることは限られています。  たとえば、<xref:System.Windows.Controls.CheckBox> の <xref:System.Windows.Controls.Control.Foreground%2A> プロパティを青に、<xref:System.Windows.Controls.Control.FontStyle%2A> プロパティをイタリックに設定できます。  
  
 コントロールの新しい <xref:System.Windows.Controls.ControlTemplate> を作成できなければ、どの [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ベースのアプリケーションでもすべてのコントロールで同じ一般的な外観を使用することになり、独自の外観と操作性を備えたアプリケーションを作成することは難しくなります。  既定では、すべての <xref:System.Windows.Controls.CheckBox> には同じ特性があります。  たとえば、<xref:System.Windows.Controls.CheckBox> のコンテンツは常に選択インジケーターの右側に配置され、<xref:System.Windows.Controls.CheckBox> がオンになっていることを示すためにチェック マークが必ず使用されます。  
  
 <xref:System.Windows.Controls.ControlTemplate> を作成すると、コントロールの外観に、コントロールのその他のプロパティの設定を変更するだけでは不可能なカスタマイズを施すことができるようになります。  <xref:System.Windows.Controls.CheckBox> の例では、チェック ボックスのコンテンツを選択インジケーターの上に配置し、<xref:System.Windows.Controls.CheckBox> がオンになるように "X" を使用します。  このような変更は、<xref:System.Windows.Controls.CheckBox> の <xref:System.Windows.Controls.ControlTemplate> で指定します。  
  
 既定の <xref:System.Windows.Controls.ControlTemplate> を使用する <xref:System.Windows.Controls.CheckBox> を次の図に示します。  
  
 ![既定のコントロール テンプレート付きのチェック ボックス](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP\_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 次の図は、<xref:System.Windows.Controls.CheckBox> でカスタムの <xref:System.Windows.Controls.ControlTemplate> を使用して、<xref:System.Windows.Controls.CheckBox> のコンテンツを選択インジケーターの上に配置し、<xref:System.Windows.Controls.CheckBox> がオンのときに X を表示するようすを示しています。  
  
 ![カスタム コントロール テンプレート付きのチェック ボックス](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP\_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 このサンプルの <xref:System.Windows.Controls.CheckBox> の <xref:System.Windows.Controls.ControlTemplate> は比較的複雑なため、このトピックでは簡単な例を使用して <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ControlTemplate> を作成します。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## コントロールの視覚的な構造の変更  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では通常、コントロールは複合 <xref:System.Windows.FrameworkElement> オブジェクトです。  <xref:System.Windows.Controls.ControlTemplate> を作成する場合は、<xref:System.Windows.FrameworkElement> オブジェクトを組み合わせて 1 つのコントロールを作成します。  1 つの <xref:System.Windows.Controls.ControlTemplate> には、ルート要素として <xref:System.Windows.FrameworkElement> が 1 つだけ必要です。  通常、このルート要素には他の <xref:System.Windows.FrameworkElement> オブジェクトが含まれます。  オブジェクトを組み合わせて、コントロールの視覚的な構造を構成します。  
  
 <xref:System.Windows.Controls.Button> に対するカスタム <xref:System.Windows.Controls.ControlTemplate> を作成する例を次に示します。  <xref:System.Windows.Controls.ControlTemplate> を使用して <xref:System.Windows.Controls.Button> の視覚的な構造を作成します。  この例では、ボタン上にマウス ポインターを置いても、クリックしてもボタンの外観は変化しません。  状態に応じて外観が変化するボタンについては、このトピックで後述します。  
  
 この例では、次のパーツで視覚的な構造を構成しています。  
  
-   `RootElement` という名前の <xref:System.Windows.Controls.Border>。テンプレートのルート <xref:System.Windows.FrameworkElement> として機能します。  
  
-   `RootElement` の子である <xref:System.Windows.Controls.Grid>。  
  
-   ボタンのコンテンツを表示する <xref:System.Windows.Controls.ContentPresenter>。  <xref:System.Windows.Controls.ContentPresenter> を使用すると、あらゆる型のオブジェクトを表示できます。  
  
 [!code-xml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### TemplateBinding を使用してコントロールのプロパティの機能を維持する方法  
 新しい <xref:System.Windows.Controls.ControlTemplate> を作成した場合でも、パブリック プロパティを使用して、コントロールの外観を変更することができます。  [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) のマークアップ拡張機能は、<xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティを、コントロールによって定義されたパブリック プロパティにバインドする機能です。  [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) を使用すると、コントロールのプロパティを有効にして、テンプレートに対するパラメーターとして機能させることができます。  つまり、コントロールのプロパティを設定したときに、その値が [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) を持つ要素に渡されます。  
  
 前の例では、[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) のマークアップ拡張機能を使用して、<xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティを、ボタンによって定義されたパブリック プロパティにバインドしていますが、次の例では、その一部を繰り返しています。  
  
 [!code-xml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 この例では、<xref:System.Windows.Controls.Grid> で <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=fullName> プロパティ テンプレートを <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> にバインドします。  <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=fullName> がテンプレート バインディングされているため、同じ <xref:System.Windows.Controls.ControlTemplate> を使用する複数のボタンを作成し、ボタンごとに異なる値を <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> に設定できます。  <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> が <xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティにテンプレート バインディングされていないと、ボタンの <xref:System.Windows.Controls.Control.Background%2A?displayProperty=fullName> を設定してもボタンの外観に影響しません。  
  
 2 つのプロパティの名前は同じである必要はありません。  前の例では、<xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=fullName> プロパティが、<xref:System.Windows.Controls.ContentPresenter> の <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=fullName> プロパティにテンプレート バインディングされています。  これにより、ボタンのコンテンツを水平方向に配置できます。  <xref:System.Windows.Controls.ContentPresenter> には `HorizontalContentAlignment` という名前のプロパティがありませんが、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=fullName> を <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=fullName> にバインドすることができます。  プロパティをテンプレート バインディングするときは、ターゲットとソースのプロパティが同じ型であることを確認してください。  
  
 <xref:System.Windows.Controls.Control> クラスを使用して、設定時にコントロールに適用するコントロール テンプレートで使用する必要があるいくつかのプロパティを定義します。  <xref:System.Windows.Controls.ControlTemplate> でのプロパティの使用方法は、プロパティによって異なります。  <xref:System.Windows.Controls.ControlTemplate> では、次のいずれかの方法でプロパティを使用する必要があります。  
  
-   <xref:System.Windows.Controls.ControlTemplate> テンプレート内の要素をプロパティにバインドします。  
  
-   <xref:System.Windows.Controls.ControlTemplate> テンプレート内の要素は、親 <xref:System.Windows.FrameworkElement> からプロパティを継承します。  
  
 コントロールによって <xref:System.Windows.Controls.Control> クラスから継承される視覚プロパティを次の表に示します。  また、コントロールの既定のコントロール テンプレートで継承されたプロパティ値を使用するかどうか、およびテンプレート バインディングする必要があるかどうかも示します。  
  
|プロパティ|使用のメソッド|  
|-----------|-------------|  
|<xref:System.Windows.Controls.Control.Background%2A>|テンプレート バインディング|  
|<xref:System.Windows.Controls.Control.BorderThickness%2A>|テンプレート バインディング|  
|<xref:System.Windows.Controls.Control.BorderBrush%2A>|テンプレート バインディング|  
|<xref:System.Windows.Controls.Control.FontFamily%2A>|プロパティの継承またはテンプレート バインディング|  
|<xref:System.Windows.Controls.Control.FontSize%2A>|プロパティの継承またはテンプレート バインディング|  
|<xref:System.Windows.Controls.Control.FontStretch%2A>|プロパティの継承またはテンプレート バインディング|  
|<xref:System.Windows.Controls.Control.FontWeight%2A>|プロパティの継承またはテンプレート バインディング|  
|<xref:System.Windows.Controls.Control.Foreground%2A>|プロパティの継承またはテンプレート バインディング|  
|<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A>|テンプレート バインディング|  
|<xref:System.Windows.Controls.Control.Padding%2A>|テンプレート バインディング|  
|<xref:System.Windows.Controls.Control.VerticalContentAlignment%2A>|テンプレート バインディング|  
  
 表には、<xref:System.Windows.Controls.Control> クラスから継承される視覚プロパティのみを示しています。  表内のプロパティとは別に、コントロールによって、親フレームワーク要素から <xref:System.Windows.FrameworkElement.DataContext%2A>、<xref:System.Windows.FrameworkElement.Language%2A>、および <xref:System.Windows.Controls.TextBlock.TextDecorations%2A> の各プロパティも継承される場合があります。  
  
 また、<xref:System.Windows.Controls.ContentPresenter> が <xref:System.Windows.Controls.ContentControl> の <xref:System.Windows.Controls.ControlTemplate> に存在する場合は、<xref:System.Windows.Controls.ContentPresenter> は自動的に <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> プロパティおよび <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティにバインドされます。  同様に、<xref:System.Windows.Controls.ItemsControl> の <xref:System.Windows.Controls.ControlTemplate> に存在する <xref:System.Windows.Controls.ItemsPresenter> は自動的に <xref:System.Windows.Controls.ItemsControl.Items%2A> プロパティおよび <xref:System.Windows.Controls.ItemsPresenter> プロパティにバインドされます。  
  
 次の例では、前の例で定義した <xref:System.Windows.Controls.ControlTemplate> を使用するボタンを 2 つ作成します。  この例では、各ボタンの <xref:System.Windows.Controls.Control.Background%2A>、<xref:System.Windows.Controls.Control.Foreground%2A>、および <xref:System.Windows.Controls.Control.FontSize%2A> の各プロパティを設定します。  <xref:System.Windows.Controls.Control.Background%2A> プロパティは <xref:System.Windows.Controls.ControlTemplate> にテンプレート バインディングされているため、そのプロパティの設定は有効です。  <xref:System.Windows.Controls.Control.Foreground%2A> プロパティおよび <xref:System.Windows.Controls.Control.FontSize%2A> プロパティはテンプレート バインディングされていなくても、値を継承するため、それらのプロパティの設定は有効です。  
  
 [!code-xml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![2 つのボタン &#40;青色のボタンと紫色のボタン&#41;](../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP\_ButtonTwo")  
背景色が異なる 2 つのボタン  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## 状態に応じたコントロールの外観の変化  
 既定の外観のボタンと前の例のボタンの違いは、既定のボタンが別の状態になったときにわずかに変化することです。  たとえば、既定のボタンの外観はボタンをクリックしたときやマウス ポインターをボタンの上に置いたときに変化します。  <xref:System.Windows.Controls.ControlTemplate> によってコントロールの機能は変更されませんが、コントロールの視覚的な動作は変更されます。  視覚的な動作とは、コントロールが特定の状態になったときの外観のことです。  コントロールの機能と視覚的な動作との違いを理解するために、ボタンの例について考えてみます。  ボタンの機能とはクリックされたときに <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントを発生させることですが、ボタンの視覚的な動作とはボタンをポイントまたはクリックしたときのボタンの外観の変化のことです。  
  
 <xref:System.Windows.VisualState> を使用して、特定の状態のときのコントロールの外観を指定します。  <xref:System.Windows.VisualState> には、<xref:System.Windows.Controls.ControlTemplate> 内の要素の外観を変化させる <xref:System.Windows.Media.Animation.Storyboard> が含まれています。  <xref:System.Windows.VisualStateManager> を使用することで、コントロールのロジックにより状態が変化するため、この変化をコードで記述する必要はありません。  コントロールが <xref:System.Windows.VisualState.Name%2A?displayProperty=fullName> プロパティで指定された状態になると、<xref:System.Windows.Media.Animation.Storyboard> が開始されます。  コントロールがその状態から移行すると、<xref:System.Windows.Media.Animation.Storyboard> は停止します。  
  
 マウス ポインターをボタンの上に置いたときに <xref:System.Windows.Controls.Button> の外観を変化させる <xref:System.Windows.VisualState> の例を次に示します。  <xref:System.Windows.Media.Animation.Storyboard> によって `BorderBrush` の色が変化することで、ボタンの境界線の色が変化します。  このトピックの冒頭にある <xref:System.Windows.Controls.ControlTemplate> の例を参照すると、`BorderBrush` が <xref:System.Windows.Controls.Border> の <xref:System.Windows.Controls.Border.Background%2A> に割り当てた <xref:System.Windows.Media.SolidColorBrush> の名前であることがわかります。  
  
 [!code-xml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 このコントロールで、コントロール コントラクトの一部として状態を定義します。詳細については、このトピックの「[コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法](#customizing_other_controls_by_understanding_the_control_contract)」で後述します。  次の表は、<xref:System.Windows.Controls.Button> に指定される状態の一覧です。  
  
|VisualState 名|VisualStateGroup 名|Description|  
|-------------------|------------------------|-----------------|  
|Normal|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|Pressed|CommonStates|コントロールが押されています。|  
|Disabled|CommonStates|コントロールが無効になっています。|  
|Focused|FocusStates|コントロールにフォーカスがあります。|  
|Unfocused|FocusStates|コントロールにフォーカスがありません。|  
  
 <xref:System.Windows.Controls.Button> では、2 つの状態グループが定義されています \(`Normal`、`MouseOver`、`Pressed` および `Disabled` の各状態を含む `CommonStates` グループと   `Focused` 状態および `Unfocused` 状態を含む `FocusStates` グループ\)。  同じ状態グループ内の状態を同時に複数指定することはできません。  コントロールは常に 1 グループにつき 1 つの状態になります。  たとえば、<xref:System.Windows.Controls.Button> には、マウス ポインターが置かれていないときでもフォーカスを設定できます。そのため、`Focused` 状態の <xref:System.Windows.Controls.Button> は `MouseOver`、`Pressed`、または `Normal` の状態になります。  
  
 <xref:System.Windows.VisualState> オブジェクトを <xref:System.Windows.VisualStateGroup> オブジェクトに追加します。  <xref:System.Windows.VisualStateGroup> オブジェクトを <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 添付プロパティに追加します。  次の例では、`Normal`、`MouseOver`、`Pressed` の各状態の <xref:System.Windows.VisualState> オブジェクトを定義します。これらの状態は、すべて `CommonStates` グループに属しています。  各 <xref:System.Windows.VisualState> の <xref:System.Windows.VisualState.Name%2A> は、前の表に記載された名前と一致します。  `Disabled` 状態および `FocusStates` グループの状態は、例を簡潔にするために省略していますが、このトピックの最後で紹介している完全なコード例には含まれています。  
  
> [!NOTE]
>  <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 添付プロパティを <xref:System.Windows.Controls.ControlTemplate> のルート <xref:System.Windows.FrameworkElement> に設定してください。  
  
 [!code-xml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![カスタム コントロール テンプレート付きのボタン](../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP\_ButtonNormal")  
通常の状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い境界線付きのボタン](../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP\_ButtonMouseOver")  
マウス オーバー状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![押されたボタンの透明な境界線](../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP\_ButtonPressed")  
押された状態のカスタム コントロール テンプレートを使用しているボタン  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールの視覚的な状態については、「[コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)」を参照してください。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## 状態間を遷移するときのコントロールの動作の指定  
 前の例では、ボタンをクリックしたときにもボタンの外観は変化しますが、ボタンを 1 秒間押したままにしない限り変化しません。  既定では、アニメーションが開始されるまでに 1 秒かかります。  多くの場合、ユーザーがボタンをクリックして離すまでの時間はそれよりもかなり短いため、<xref:System.Windows.Controls.ControlTemplate> を既定の状態のままにしておくと視覚的フィードバックが効果的になりません。  
  
 アニメーションを開始するまでの時間を指定して、コントロールをある状態から別の状態に円滑に遷移させるには、<xref:System.Windows.VisualTransition> オブジェクトを <xref:System.Windows.Controls.ControlTemplate> に追加します。  <xref:System.Windows.VisualTransition> を作成する場合は、次のうちの 1 つ以上を指定します。  
  
-   状態間の遷移を開始するまでの時間。  
  
-   遷移時に発生するコントロールの外観への追加の変更。  
  
-   <xref:System.Windows.VisualTransition> を適用する状態。  
  
### 遷移の継続時間の指定  
 <xref:System.Windows.VisualTransition.GeneratedDuration%2A> プロパティを設定すると、遷移に要する時間を指定できます。  前の例では、<xref:System.Windows.VisualState> は、ボタンを押したときにボタンの境界線が透明に変化するようになっていますが、ボタンをすばやく押して離した場合、アニメーションが開始されるまでの時間が長すぎるため認識されません。  <xref:System.Windows.VisualTransition> を使用して、コントロールが押された状態に遷移するために要する時間を指定できます。  次の例では、コントロールが押された状態に遷移するまでの時間を 1\/100 秒に指定しています。  
  
 [!code-xml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### 遷移時にコントロールの外観の変更を指定する方法  
 <xref:System.Windows.VisualTransition> には、コントロールの状態が遷移するときに開始される <xref:System.Windows.Media.Animation.Storyboard> が含まれています。  たとえば、コントロールが `MouseOver` 状態から `Normal` 状態に遷移する場合に特定のアニメーションが実行されるように指定することができます。  次の例では、ユーザーがマウス ポインターをボタンの外に移動したときに、ボタンの境界線が 1.5 秒で青色、黄色、黒の順に変化するように指定する <xref:System.Windows.VisualTransition> を作成します。  
  
 [!code-xml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### VisualTransition を適用するタイミングの指定  
 <xref:System.Windows.VisualTransition> を特定の状態にだけ適用するように制限することも、コントロールが状態間を遷移するときに常に適用することもできます。  前の例ではコントロールが `MouseOver` 状態から `Normal` 状態に遷移したときに <xref:System.Windows.VisualTransition> が適用され、その前の例ではコントロールが `Pressed` 状態に遷移したときに <xref:System.Windows.VisualTransition> が適用されます。  <xref:System.Windows.VisualTransition.To%2A> プロパティと <xref:System.Windows.VisualTransition.From%2A> プロパティを設定すると、<xref:System.Windows.VisualTransition> を適用するタイミングを制限できます。  最も制限的なものから制限が最も少ない制限レベルについて次の表に示します。  
  
|制限の種類|From の値|To の値|  
|-----------|-------------|-----------|  
|指定した状態から別の指定した状態まで|<xref:System.Windows.VisualState> の名前|<xref:System.Windows.VisualState> の名前|  
|任意の状態から指定した状態まで|設定しない|<xref:System.Windows.VisualState> の名前|  
|指定した状態から任意の状態まで|<xref:System.Windows.VisualState> の名前|設定しない|  
|任意の状態から別の任意の状態まで|設定しない|設定しない|  
  
 同じ状態を参照する <xref:System.Windows.VisualStateGroup> で複数の <xref:System.Windows.VisualTransition> オブジェクトを保持できますが、それらのオブジェクトは前の表で指定した順序に従って使用されます。  次の例は、2 つの <xref:System.Windows.VisualTransition> オブジェクトを示しています。  `Pressed` 状態から `MouseOver` 状態にコントロールを遷移させる場合は、<xref:System.Windows.VisualTransition.From%2A> および <xref:System.Windows.VisualTransition.To%2A> の両方が設定されている <xref:System.Windows.VisualTransition> が使用されます。  `Pressed` 状態にない状態から `MouseOver` 状態にコントロールを遷移させる場合は、別の状態が使用されます。  
  
 [!code-xml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup> には、<xref:System.Windows.VisualStateGroup> の <xref:System.Windows.VisualState> オブジェクトに適用する <xref:System.Windows.VisualTransition> オブジェクトを含む <xref:System.Windows.VisualStateGroup.Transitions%2A> プロパティがあります。  <xref:System.Windows.Controls.ControlTemplate> の作成者は、自由に <xref:System.Windows.VisualTransition> を含めることができます。  ただし、<xref:System.Windows.VisualTransition.To%2A> プロパティおよび <xref:System.Windows.VisualTransition.From%2A> プロパティに設定した状態の名前が <xref:System.Windows.VisualStateGroup> に含まれていない場合、<xref:System.Windows.VisualTransition> は無視されます。  
  
 `CommonStates` の <xref:System.Windows.VisualStateGroup> を次の例に示します。  この例では、次のボタンの各遷移に対して <xref:System.Windows.VisualTransition> を定義しています。  
  
-   `Pressed` 状態への遷移。  
  
-   `MouseOver` 状態への遷移。  
  
-   `Pressed` 状態から `MouseOver` 状態への遷移。  
  
-   `MouseOver` 状態から `Normal` 状態への遷移。  
  
 [!code-xml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法  
 <xref:System.Windows.Controls.ControlTemplate> を使用して、その視覚的な構造 \(<xref:System.Windows.FrameworkElement> オブジェクトを使用\) および視覚的な動作 \(<xref:System.Windows.VisualState> オブジェクトを使用\) を指定するコントロールでは、パーツ コントロール モデルを使用しています。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 に含まれる多くのコントロールには、このモデルが採用されています。  <xref:System.Windows.Controls.ControlTemplate> の作成者は、コントロール コントラクトを通じて伝えられるパーツに注意する必要があります。  コントロール コントラクトのパーツについて理解すると、パーツ コントロール モデルを採用しているすべてのコントロールの外観をカスタマイズできます。  
  
 コントロール コントラクトには、3 つの要素があります。  
  
-   コントロールのロジックが使用する視覚的要素。  
  
-   コントロールの状態と各状態が属するグループ。  
  
-   コントロールに対して視覚的に作用するパブリック プロパティ。  
  
### コントロール コントラクトの視覚的要素  
 コントロールのロジックは、<xref:System.Windows.Controls.ControlTemplate> 内の <xref:System.Windows.FrameworkElement> と対話することがあります。  たとえば、コントロールによる要素のイベント処理が考えられます。  コントロールは、<xref:System.Windows.Controls.ControlTemplate> から特定の <xref:System.Windows.FrameworkElement> を探すとき、その情報を <xref:System.Windows.Controls.ControlTemplate> の作成者に伝達します。  探している要素の型および名前を伝達する手段として、コントロールは <xref:System.Windows.TemplatePartAttribute> を使用します。  <xref:System.Windows.Controls.Button> のコントロール コントラクト内に <xref:System.Windows.FrameworkElement> パーツはありませんが、<xref:System.Windows.Controls.ComboBox> などの他のコントロールにはあります。  
  
 <xref:System.Windows.Controls.ComboBox> クラスで指定する <xref:System.Windows.TemplatePartAttribute> オブジェクトを次の例に示します。  <xref:System.Windows.Controls.ComboBox> のロジックは、<xref:System.Windows.Controls.ControlTemplate> 内で `PART_EditableTextBox` という名前の <xref:System.Windows.Controls.TextBox> および `PART_Popup` という名前の <xref:System.Windows.Controls.Primitives.Popup> を探します。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 <xref:System.Windows.Controls.ComboBox> クラスの <xref:System.Windows.TemplatePartAttribute> オブジェクトによって指定された要素を含む、<xref:System.Windows.Controls.ComboBox> の簡略化した <xref:System.Windows.Controls.ControlTemplate> を次の例に示します。  
  
 [!code-xml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### コントロール コントラクトの状態  
 コントロールの状態もコントロール コントラクトの一部です。  <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ControlTemplate> を作成する例では、<xref:System.Windows.Controls.Button> の状態に応じて外観を指定する方法を示しています。  指定したそれぞれの状態に対して <xref:System.Windows.VisualState> を作成し、<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A> を共有するすべての <xref:System.Windows.VisualState> オブジェクトを、このトピックの「[状態に応じたコントロールの外観の変化](#changing_the_appearance_of_a_control_depending_on_its_state)」で説明したように <xref:System.Windows.VisualStateGroup> に配置します。  サードパーティ コントロールは <xref:System.Windows.TemplateVisualStateAttribute>のコントロール テンプレート作成のためにコントロールの状態を公開することをデザイナーのツールが、 Expression Blend など、使用する使用して状態を指定する必要があります。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールのコントロール コントラクトについては、「[コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)」を参照してください。  
  
### コントロール コントラクトのプロパティ  
 コントロールに視覚的な影響を与えるパブリック プロパティもコントロール コントラクトに含まれています。  これらのプロパティを設定すると、<xref:System.Windows.Controls.ControlTemplate> を新たに作成せずに、コントロールの外観を変更できます。  また、[TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) のマークアップ拡張機能を使用して、<xref:System.Windows.Controls.ControlTemplate> 内の要素のプロパティを、<xref:System.Windows.Controls.Button> によって定義されたパブリック プロパティにバインドすることもできます。  
  
 次の例では、ボタンのコントロール コントラクトを示します。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 <xref:System.Windows.Controls.ControlTemplate> を作成する場合は、既存の <xref:System.Windows.Controls.ControlTemplate> を利用して、変更を加える方が簡単です。  次のいずれかの方法で、既存の <xref:System.Windows.Controls.ControlTemplate> を変更できます。  
  
-   Expression Blend などのデザイナーを使用します。デザイナーには、コントロール テンプレートを作成するためのグラフィカル ユーザー インターフェイスが用意されています。  詳細については、「[テンプレートをサポートするコントロールのスタイル処理](http://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
-   既定の <xref:System.Windows.Controls.ControlTemplate> を取得して、編集します。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属する既定のコントロール テンプレートについては、[既定の WPF テーマ](http://go.microsoft.com/fwlink/?LinkID=158252)を参照してください。  
  
<a name="complete_example"></a>   
## コード例全体  
 次に示す例は、このトピックで説明した <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ControlTemplate> の完全版です。  
  
 [!code-xml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## 参照  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)