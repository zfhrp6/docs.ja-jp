---
title: ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- control contract [WPF]
- controls [WPF], visual structure changes
- ControlTemplate [WPF], customizing for existing controls
- skinning controls [WPF]
- controls [WPF], appearance specified by state
- templates [WPF], custom for existing controls
ms.assetid: 678dd116-43a2-4b8c-82b5-6b826f126e31
ms.openlocfilehash: bbdc79fabf8dbe344baae66d718d79ac6375db7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="customizing-the-appearance-of-an-existing-control-by-creating-a-controltemplate"></a>ControlTemplate の作成による既存のコントロールの外観のカスタマイズ
<a name="introduction"></a> A<xref:System.Windows.Controls.ControlTemplate>視覚的な構造とコントロールの視覚的な動作を指定します。 コントロールの外観をカスタマイズするには、新しい it を付けることで<xref:System.Windows.Controls.ControlTemplate>です。 作成するときに、 <xref:System.Windows.Controls.ControlTemplate>、その機能を変更することがなく、既存のコントロールの外観を置き換えます。 たとえば、することができます、ボタン、アプリケーションで、既定の正方形ではなくラウンドただし、ボタンが発生するが、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。  
  
 このトピックのさまざまな部分を説明します、 <xref:System.Windows.Controls.ControlTemplate>、単純な作成方法を示します<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>、およびその外観をカスタマイズするには、コントロールのコントロールのコントラクトを理解する方法について説明します。 作成するため、<xref:System.Windows.Controls.ControlTemplate>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、任意のコードを記述することがなく、コントロールの外観を変更することができます。 また、カスタム コントロール テンプレートを作成するために、Microsoft Expression Blend などのデザイナーを使用することもできます。 このトピックの例を示しています、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]の外観をカスタマイズする、<xref:System.Windows.Controls.Button>し、トピックの最後に完全な例を一覧表示します。 Expression Blend の使用方法の詳細については、「[テンプレートをサポートするコントロールのスタイル処理](http://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
 次の図に示さ、<xref:System.Windows.Controls.Button>を使用して、<xref:System.Windows.Controls.ControlTemplate>は、このトピックで作成します。  
  
 ![カスタム コントロール テンプレート付きのボタンをクリックします。] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
カスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い境界線付きのボタンをクリックします。] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
カスタム コントロール テンプレートを使用したボタンにマウス ポインターを置いた状態  
  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックは、「[コントロール](../../../../docs/framework/wpf/controls/index.md)」で説明したコントロールとスタイルの作成方法および使用方法を理解していることを前提としています。 このトピックで説明する概念はから継承した要素に適用、<xref:System.Windows.Controls.Control>クラスを除き、<xref:System.Windows.Controls.UserControl>です。 適用することはできません、<xref:System.Windows.Controls.ControlTemplate>を<xref:System.Windows.Controls.UserControl>です。  
  
<a name="when_you_should_create_a_controltemplate"></a>   
## <a name="when-you-should-create-a-controltemplate"></a>ControlTemplate の作成が必要な場合  
 コントロールなど、多くのプロパティがあります<xref:System.Windows.Controls.Border.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、および<xref:System.Windows.Controls.Control.FontFamily%2A>コントロールの外観のさまざまな側面を指定する設定できますが、これらのプロパティを設定して行うことができます、変更は制限されます。 たとえば、設定することができます、<xref:System.Windows.Controls.Control.Foreground%2A>青にプロパティと<xref:System.Windows.Controls.Control.FontStyle%2A>上に斜体、<xref:System.Windows.Controls.CheckBox>です。  
  
 新規作成することができない<xref:System.Windows.Controls.ControlTemplate>、コントロールのすべてのコントロールですべて[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]-ベースのアプリケーションで同じの一般的な外観で、カスタムのルック アンド フィールでアプリケーションを作成する機能が制限されることが必要があります。 既定では、すべて<xref:System.Windows.Controls.CheckBox>は類似の特性があります。 内容など、<xref:System.Windows.Controls.CheckBox>選択インジケーターの右側には常にチェック マークは常に示すために使用して、<xref:System.Windows.Controls.CheckBox>が選択されています。  
  
 作成する、<xref:System.Windows.Controls.ControlTemplate>はどのようなその他のプロパティを設定コントロール以外のコントロールの外観をカスタマイズする場合。 例では、<xref:System.Windows.Controls.CheckBox>します選択インジケーター上に配置する チェック ボックスの内容、およびすることを示す X、<xref:System.Windows.Controls.CheckBox>が選択されています。 これらの変更を指定する、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.CheckBox>です。  
  
 次の図は、 <xref:System.Windows.Controls.CheckBox> 、既定値を使用する<xref:System.Windows.Controls.ControlTemplate>です。  
  
 ![既定のコントロール テンプレート付きのチェック ボックスです。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 次の図は、<xref:System.Windows.Controls.CheckBox>を使用するカスタム<xref:System.Windows.Controls.ControlTemplate>のコンテンツを配置する、<xref:System.Windows.Controls.CheckBox>選択インジケーターと表示に X の上ときに、<xref:System.Windows.Controls.CheckBox>が選択されています。  
  
 ![カスタム コントロール テンプレート付きのチェック ボックスをオンします。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 <xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.CheckBox>このサンプルでは比較的複雑なため、このトピックの内容を作成する簡単な例を使用して、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>です。  
  
<a name="changing_the_visual_structure_of_a_control"></a>   
## <a name="changing-the-visual-structure-of-a-control"></a>コントロールの視覚的な構造の変更  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、コントロールは、多くの場合、複合<xref:System.Windows.FrameworkElement>オブジェクト。 作成するときに、 <xref:System.Windows.Controls.ControlTemplate>、結合する<xref:System.Windows.FrameworkElement>を 1 つのコントロールをビルドするオブジェクト。 A <xref:System.Windows.Controls.ControlTemplate> 1 つだけ持たなければなりません<xref:System.Windows.FrameworkElement>のルート要素として。 ルート要素に通常含まれるその他の<xref:System.Windows.FrameworkElement>オブジェクト。 複数のオブジェクトを組み合わせて、コントロールの視覚的な構造を構成します。  
  
 次の例では、カスタム<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>です。 <xref:System.Windows.Controls.ControlTemplate>の視覚的な構造を作成、<xref:System.Windows.Controls.Button>です。 この例では、ボタンの上にマウス ポインターを移動しても、ボタンをクリックしても、その外観は変化しません。 状態に応じて外観が変化するボタンについては、このトピックで後述します。  
  
 この例では、以下のパーツで視覚的な構造を構成しています。  
  
-   A<xref:System.Windows.Controls.Border>という`RootElement`テンプレートのルートとして機能する<xref:System.Windows.FrameworkElement>です。  
  
-   A<xref:System.Windows.Controls.Grid>の子である`RootElement`です。  
  
-   A<xref:System.Windows.Controls.ContentPresenter>ボタンのコンテンツを表示します。 <xref:System.Windows.Controls.ContentPresenter>を表示するオブジェクトの任意の型を有効にします。  
  
 [!code-xaml[VSMButtonTemplate#BasicTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#basictemplate)]  
  
### <a name="preserving-the-functionality-of-a-controls-properties-by-using-templatebinding"></a>TemplateBinding を使用してコントロールのプロパティの機能を維持する方法  
 新規に作成するときに<xref:System.Windows.Controls.ControlTemplate>、まだするコントロールの外観を変更するパブリック プロパティを使用する可能性があります。 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)マークアップ拡張機能内にある要素のプロパティのバインド、<xref:System.Windows.Controls.ControlTemplate>コントロールによって定義されているパブリック プロパティにします。 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) を使用すると、コントロールのプロパティをテンプレートのパラメーターとして機能させることができます。 つまり、コントロールのプロパティを設定すると、その値は [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md) が機能している要素に渡されます。  
  
 次の例を使用する前の例の一部を繰り返す、 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)内にある要素のプロパティをバインドするマークアップ拡張機能、<xref:System.Windows.Controls.ControlTemplate>ボタンによって定義されているパブリック プロパティにします。  
  
 [!code-xaml[VSMButtonTemplate#TemplateBinding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#templatebinding)]  
  
 この例では、<xref:System.Windows.Controls.Grid>がその<xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>プロパティ テンプレートにバインド<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>です。 <xref:System.Windows.Controls.Panel.Background%2A?displayProperty=nameWithType>がバインドされているテンプレートでは、同じものを使用する複数のボタンを作成することができます<xref:System.Windows.Controls.ControlTemplate>設定と、<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>ボタンごとに異なる値にします。 場合<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>テンプレートではありませんが内の要素のプロパティにバインドされていた、 <xref:System.Windows.Controls.ControlTemplate>、設定、<xref:System.Windows.Controls.Control.Background%2A?displayProperty=nameWithType>のボタンがないため影響ボタンの外観にします。  
  
 2 つのプロパティの名前は同じである必要はありません。 前の例で、<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>のプロパティ、<xref:System.Windows.Controls.Button>にテンプレートがバインドされて、<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>のプロパティ、<xref:System.Windows.Controls.ContentPresenter>です。 これにより、ボタンのコンテンツを水平方向に配置できます。 <xref:System.Windows.Controls.ContentPresenter> という名前のプロパティを持たない`HorizontalContentAlignment`が<xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A?displayProperty=nameWithType>にバインドできる<xref:System.Windows.FrameworkElement.HorizontalAlignment%2A?displayProperty=nameWithType>です。 プロパティをテンプレート バインディングするときは、ターゲットとソースのプロパティが同じ型であることを確認してください。  
  
 <xref:System.Windows.Controls.Control>クラスに設定している場合は、コントロールに影響を与えるコントロール テンプレートで使用する必要がありますをいくつかのプロパティを定義します。 どのように<xref:System.Windows.Controls.ControlTemplate>使用して、プロパティ、プロパティに依存します。 <xref:System.Windows.Controls.ControlTemplate>で、次の方法のいずれかのプロパティを使用する必要があります。  
  
-   内の要素、<xref:System.Windows.Controls.ControlTemplate>テンプレートがプロパティにバインドします。  
  
-   内の要素、<xref:System.Windows.Controls.ControlTemplate>プロパティを親から継承<xref:System.Windows.FrameworkElement>です。  
  
 次の表から、コントロールから継承された visual プロパティ、<xref:System.Windows.Controls.Control>クラスです。 また、コントロールの既定のコントロール テンプレートで継承されたプロパティ値を使用するかどうか、テンプレート バインディングする必要があるかどうかも示します。  
  
|プロパティ|使用するメソッド|  
|--------------|------------------|  
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
  
 テーブルから継承されたビジュアルのプロパティのみを一覧表示、<xref:System.Windows.Controls.Control>クラスです。 別の表に、プロパティ、コントロールに継承も可能性があります、 <xref:System.Windows.FrameworkElement.DataContext%2A>、 <xref:System.Windows.FrameworkElement.Language%2A>、および<xref:System.Windows.Controls.TextBlock.TextDecorations%2A>フレームワークの親要素からのプロパティです。  
  
 また場合、<xref:System.Windows.Controls.ContentPresenter>では、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ContentControl>、<xref:System.Windows.Controls.ContentPresenter>に自動的にバインドされます、<xref:System.Windows.Controls.ContentControl.ContentTemplate%2A>と<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティです。 同様に、<xref:System.Windows.Controls.ItemsPresenter>内にある、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ItemsControl>に自動的にバインドされます、<xref:System.Windows.Controls.ItemsControl.Items%2A>と<xref:System.Windows.Controls.ItemsPresenter>プロパティです。  
  
 次の例では、2 つのボタンを使用する、<xref:System.Windows.Controls.ControlTemplate>前の例で定義されています。 例のセット、 <xref:System.Windows.Controls.Control.Background%2A>、 <xref:System.Windows.Controls.Control.Foreground%2A>、および<xref:System.Windows.Controls.Control.FontSize%2A>各ボタンのプロパティです。 設定、<xref:System.Windows.Controls.Control.Background%2A>プロパティは、有効でバインドされているテンプレートになっているため、<xref:System.Windows.Controls.ControlTemplate>です。 場合でも、<xref:System.Windows.Controls.Control.Foreground%2A>と<xref:System.Windows.Controls.Control.FontSize%2A>プロパティがバインドされているテンプレートではありません、その値が継承されるため、効果に設定します。  
  
 [!code-xaml[VSMButtonTemplate#ButtonDeclaration](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#buttondeclaration)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![2 つのボタン青、紫の 1 つです。] (../../../../docs/framework/wpf/controls/media/ndp-buttontwo.png "NDP_ButtonTwo")  
背景色が異なる 2 つのボタン  
  
<a name="changing_the_appearance_of_a_control_depending_on_its_state"></a>   
## <a name="changing-the-appearance-of-a-control-depending-on-its-state"></a>状態に応じたコントロールの外観の変化  
 既定の外観のボタンと前の例のボタンの違いは、既定のボタンが別の状態になったときにわずかに変化することです。 たとえば、ボタンをクリックしたときやマウス ポインターをボタンの上に置いたときに、既定のボタンは外観が変化します。 ただし、<xref:System.Windows.Controls.ControlTemplate>機能は変わりません、コントロールのコントロールの視覚的な動作は変更します。 視覚的な動作とは、コントロールが特定の状態にあるときの外観を指しています。 コントロールの機能と視覚的な動作の違いを理解するために、ボタンの例について考えてみます。 ボタンの機能がさせるには、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>がクリックされたときに、ボタンの視覚的な動作が指すまたは押されたときの外観を変更します。  
  
 使用する<xref:System.Windows.VisualState>オブジェクトを特定の状態にあるときに、コントロールの外観を指定します。 A<xref:System.Windows.VisualState>が含まれています、<xref:System.Windows.Media.Animation.Storyboard>内にある要素の外観を変更する、<xref:System.Windows.Controls.ControlTemplate>です。 コントロールのロジックを使用して状態を変更するために発生するコードを記述する必要はありません、<xref:System.Windows.VisualStateManager>です。 コントロールがで指定されている状態に入ったとき、 <xref:System.Windows.VisualState.Name%2A?displayProperty=nameWithType> 、プロパティ、<xref:System.Windows.Media.Animation.Storyboard>を開始します。 コントロールの状態の終了時に、<xref:System.Windows.Media.Animation.Storyboard>を停止します。  
  
 次の例は、<xref:System.Windows.VisualState>の外観を変更する、<xref:System.Windows.Controls.Button>が上にマウス ポインターの場合。 <xref:System.Windows.Media.Animation.Storyboard>の色を変更することで、ボタンの境界線の色を変更、`BorderBrush`です。 参照する場合、<xref:System.Windows.Controls.ControlTemplate>例、このトピックの先頭を取り消しは`BorderBrush`の名前を指定、<xref:System.Windows.Media.SolidColorBrush>に割り当てられている、<xref:System.Windows.Controls.Border.Background%2A>の<xref:System.Windows.Controls.Border>です。  
  
 [!code-xaml[VSMButtonTemplate#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#4)]  
  
 このコントロールは、コントロール コントラクトの一部として状態を定義する役割を果たします。詳細については、このトピックの「[コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法](#customizing_other_controls_by_understanding_the_control_contract)」で後述します。 次の表は、指定されている状態を一覧表示、<xref:System.Windows.Controls.Button>です。  
  
|VisualState 名|VisualStateGroup 名|説明|  
|----------------------|---------------------------|-----------------|  
|標準|CommonStates|既定の状態です。|  
|MouseOver|CommonStates|マウス ポインターがコントロール上に配置されています。|  
|押されている|CommonStates|コントロールが押されています。|  
|無効|CommonStates|コントロールが無効になっています。|  
|フォーカスされている|FocusStates|コントロールにフォーカスがあります。|  
|フォーカスされていない|FocusStates|コントロールにフォーカスがありません。|  
  
 <xref:System.Windows.Controls.Button> 2 つの状態グループを定義します。`CommonStates`グループが含まれています、 `Normal`、 `MouseOver`、 `Pressed`、および`Disabled`状態です。 `FocusStates` グループには、`Focused` 状態と `Unfocused` 状態が含まれます。 同じ状態グループ内の状態を同時に複数指定することはできません。 コントロールが取り得る状態は、常に 1 グループにつき 1 つです。 たとえば、<xref:System.Windows.Controls.Button>マウス ポインターがない場合でも上に、そのため、フォーカスを持つことができます、<xref:System.Windows.Controls.Button>で、`Focused`の状態は、 `MouseOver`、 `Pressed`、または`Normal`状態です。  
  
 追加する<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.VisualStateGroup>オブジェクト。 追加する<xref:System.Windows.VisualStateGroup>オブジェクトを<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティ。 次の例では定義、<xref:System.Windows.VisualState>オブジェクトに対する、 `Normal`、 `MouseOver`、および`Pressed`がすべての状態、`CommonStates`グループ。 <xref:System.Windows.VisualState.Name%2A>各<xref:System.Windows.VisualState>前の表に名前と一致します。 `Disabled` の状態および `FocusStates` グループの状態は、例を簡潔にするために省略していますが、このトピックの最後で紹介している完全なコード例には含まれています。  
  
> [!NOTE]
>  設定して、<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティのルートに<xref:System.Windows.FrameworkElement>の<xref:System.Windows.Controls.ControlTemplate>です。  
  
 [!code-xaml[VSMButtonTemplate#VisualStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualstates)]  
  
 前の例では、次の図のような出力を生成します。  
  
 ![カスタム コントロール テンプレート付きのボタンをクリックします。] (../../../../docs/framework/wpf/controls/media/ndp-buttonnormal.png "NDP_ButtonNormal")  
通常状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![赤い境界線付きのボタンをクリックします。] (../../../../docs/framework/wpf/controls/media/ndp-buttonmouseover.png "NDP_ButtonMouseOver")  
マウス オーバー状態のカスタム コントロール テンプレートを使用しているボタン  
  
 ![罫線は、押されたボタンに透過的です。] (../../../../docs/framework/wpf/controls/media/ndp-buttonpressed.png "NDP_ButtonPressed")  
押された状態のカスタム コントロール テンプレートを使用しているボタン  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールの視覚的な状態については、「[コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)」を参照してください。  
  
<a name="specifying_the_behavior_of_a_control_when_it_transitions_between_states"></a>   
## <a name="specifying-the-behavior-of-a-control-when-it-transitions-between-states"></a>状態間を遷移するときのコントロールの動作の指定  
 前の例では、ボタンをクリックしたときにもボタンの外観が変化しましたが、ボタンを 1 秒間押したままにしない限り、効果を確認できません。 既定では、アニメーションが開始されるまでに 1 秒かかります。 を、ユーザーがクリックしてボタンを離すとはるかに短時間でする可能性があるため、視覚的なフィードバックは有効になりませんのままにする場合、<xref:System.Windows.Controls.ControlTemplate>既定の状態。  
  
 追加することで 1 つの状態から別のコントロールをスムーズに遷移が発生するアニメーションにかかる時間を指定する<xref:System.Windows.VisualTransition>オブジェクトを<xref:System.Windows.Controls.ControlTemplate>です。 作成するときに、<xref:System.Windows.VisualTransition>次の 1 つ以上を指定します。  
  
-   状態間の遷移を開始するまでに要する時間。  
  
-   遷移時に発生するコントロールの外観への追加の変更。  
  
-   どの状態、<xref:System.Windows.VisualTransition>に適用されます。  
  
### <a name="specifying-the-duration-of-a-transition"></a>遷移の継続時間の指定  
 設定して、移行にかかる時間を指定することができます、<xref:System.Windows.VisualTransition.GeneratedDuration%2A>プロパティです。 前の例は、<xref:System.Windows.VisualState>ボタンが押されたが、アニメーション、ボタンが押された迅速にし、解放された場合に顕著な時間がかかるときにボタンの境界線が透過的なられることを指定します。 使用することができます、<xref:System.Windows.VisualTransition>の時間を指定する、コントロールにかかる押された状態に遷移します。 次の例では、コントロールが押された状態になるのに要する時間を 1/100 秒に指定しています。  
  
 [!code-xaml[VSMButtonTemplate#PressedTransition](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#pressedtransition)]  
  
### <a name="specifying-changes-to-the-controls-appearance-during-a-transition"></a>遷移時にコントロールの外観の変更を指定する方法  
 <xref:System.Windows.VisualTransition>が含まれています、<xref:System.Windows.Media.Animation.Storyboard>状態の間でコントロールが遷移するときに開始します。 たとえば、コントロールが `MouseOver` 状態から `Normal` 状態に遷移する場合に、特定のアニメーションが実行されるように指定できます。 次の例を作成、<xref:System.Windows.VisualTransition>ボタンからマウス ポインターを動かしたときにボタンの境界線での変化を水色に、黄、しを黒に 1.5 秒を指定します。  
  
 [!code-xaml[VSMButtonTemplate#8](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#8)]  
  
### <a name="specifying-when-a-visualtransition-is-applied"></a>VisualTransition を適用するタイミングの指定  
 A <xref:System.Windows.VisualTransition> 、特定の状態のみに適用する制限できます。 または、適用できるコントロールの状態遷移にいつします。 前の例で、<xref:System.Windows.VisualTransition>からコントロールになるときに適用されます、`MouseOver`状態、`Normal`状態です。 例では、その前に、<xref:System.Windows.VisualTransition>コントロールに入るときに適用されます、`Pressed`状態です。 時間を制限する、<xref:System.Windows.VisualTransition>設定が適用される、<xref:System.Windows.VisualTransition.To%2A>と<xref:System.Windows.VisualTransition.From%2A>プロパティです。 次の表では、制限が最も厳しいレベルから最も緩いレベルまでを一覧にして示しています。  
  
|制限の種類|値します。|値|  
|-------------------------|-------------------|-----------------|  
|指定した状態から別の指定した状態まで|名前、 <xref:System.Windows.VisualState>|名前、 <xref:System.Windows.VisualState>|  
|任意の状態から指定された状態まで|未設定|名前、 <xref:System.Windows.VisualState>|  
|指定した状態から任意の状態まで|名前、 <xref:System.Windows.VisualState>|未設定|  
|他の状態のいずれかの状態から|未設定|未設定|  
  
 複数<xref:System.Windows.VisualTransition>内のオブジェクト、<xref:System.Windows.VisualStateGroup>を参照する、同じ状態が、前の表に示す順序で使用されます。 次の例では、2 つ<xref:System.Windows.VisualTransition>オブジェクト。 コントロールが遷移すると、`Pressed`状態、 `MouseOver` 、状態、<xref:System.Windows.VisualTransition>両方を持つ<xref:System.Windows.VisualTransition.From%2A>と<xref:System.Windows.VisualTransition.To%2A>セットを使用します。 コントロールが `Pressed` ではない状態から `MouseOver` 状態に遷移するときには、別の状態を使用します。  
  
 [!code-xaml[VSMButtonTemplate#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#7)]  
  
 <xref:System.Windows.VisualStateGroup>が、<xref:System.Windows.VisualStateGroup.Transitions%2A>プロパティを含む、<xref:System.Windows.VisualTransition>オブジェクトに適用する、<xref:System.Windows.VisualState>内のオブジェクト、<xref:System.Windows.VisualStateGroup>です。 として、<xref:System.Windows.Controls.ControlTemplate>の作成者は自由にいずれかを含める<xref:System.Windows.VisualTransition>します。 ただし場合、<xref:System.Windows.VisualTransition.To%2A>と<xref:System.Windows.VisualTransition.From%2A>プロパティに追加されていない状態の名前に設定されて、 <xref:System.Windows.VisualStateGroup>、<xref:System.Windows.VisualTransition>は無視されます。  
  
 次の例は、<xref:System.Windows.VisualStateGroup>の`CommonStates`です。 例では、定義、<xref:System.Windows.VisualTransition>ボタンの次の各遷移にします。  
  
-   `Pressed` 状態への遷移。  
  
-   `MouseOver` 状態への遷移。  
  
-   `Pressed` 状態から `MouseOver` 状態への遷移。  
  
-   `MouseOver` 状態から `Normal` 状態への遷移。  
  
 [!code-xaml[VSMButtonTemplate#VisualTransitions](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/buttonstages.xaml#visualtransitions)]  
  
<a name="customizing_other_controls_by_understanding_the_control_contract"></a>   
## <a name="customizing-other-controls-by-understanding-the-control-contract"></a>コントロール コントラクトについて理解しその他のコントロールをカスタマイズする方法  
 使用するコントロールを<xref:System.Windows.Controls.ControlTemplate>その視覚的な構造を指定する (を使用して<xref:System.Windows.FrameworkElement>オブジェクト) と視覚的な動作 (を使用して<xref:System.Windows.VisualState>オブジェクト) パーツ コントロールのモデルを使用します。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 4 に含まれるコントロールの多くは、このモデルを採用しています。 部分を<xref:System.Windows.Controls.ControlTemplate>注意すべき作成者ニーズがされるコントロール コントラクトを通じて伝達されます。 コントロール コントラクトのパーツについて理解すると、パーツ コントロール モデルを採用するあらゆるコントロールの外観をカスタマイズできます。  
  
 コントロール コントラクトには、次の 3 つの要素があります。  
  
-   コントロールのロジックが使用する視覚的要素。  
  
-   コントロールの状態および各状態が所属するグループ。  
  
-   コントロールに対して視覚的に作用するパブリック プロパティ。  
  
### <a name="visual-elements-in-the-control-contract"></a>コントロール コントラクトの視覚的要素  
 コントロールのロジックと対話することがあります、<xref:System.Windows.FrameworkElement>内にある、<xref:System.Windows.Controls.ControlTemplate>です。 たとえば、コントロールがその要素のイベントを処理する場合などです。 ときに、コントロールが必要ですが、特定の検索に<xref:System.Windows.FrameworkElement>で、 <xref:System.Windows.Controls.ControlTemplate>、その情報を伝える必要があります、<xref:System.Windows.Controls.ControlTemplate>作成者です。 コントロールを使用して、<xref:System.Windows.TemplatePartAttribute>に伝えるための型が必要な要素と要素の名前にする必要があります。 <xref:System.Windows.Controls.Button>いない<xref:System.Windows.FrameworkElement>ように、コントロール コントラクトは、他のコントロールでパーツ、 <xref:System.Windows.Controls.ComboBox>、操作を行います。  
  
 次の例は、<xref:System.Windows.TemplatePartAttribute>で指定されたオブジェクト、<xref:System.Windows.Controls.ComboBox>クラスです。 ロジック<xref:System.Windows.Controls.ComboBox>が期待する、<xref:System.Windows.Controls.TextBox>という名前`PART_EditableTextBox`と<xref:System.Windows.Controls.Primitives.Popup>という`PART_Popup`でその<xref:System.Windows.Controls.ControlTemplate>です。  
  
 [!code-csharp[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#comboboxcontract)]
 [!code-vb[VSMButtonTemplate#ComboBoxContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#comboboxcontract)]  
  
 次の例は、簡略化された<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.ComboBox>で指定されている要素を含む、<xref:System.Windows.TemplatePartAttribute>でオブジェクトを<xref:System.Windows.Controls.ComboBox>クラスです。  
  
 [!code-xaml[VSMButtonTemplate#ComboBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/window1.xaml#comboboxtemplate)]  
  
### <a name="states-in-the-control-contract"></a>コントロール コントラクトの状態  
 コントロールの状態もコントロール コントラクトの一部です。 作成する例、<xref:System.Windows.Controls.ControlTemplate>の<xref:System.Windows.Controls.Button>の外観を指定する方法を示します、<xref:System.Windows.Controls.Button>の状態によって異なります。 作成する、<xref:System.Windows.VisualState>各状態を指定し、すべての<xref:System.Windows.VisualState>オブジェクトを共有する、<xref:System.Windows.TemplateVisualStateAttribute.GroupName%2A>で、 <xref:System.Windows.VisualStateGroup>」の説明に従って、[の状態でコントロールによっての外観を変更する](#changing_the_appearance_of_a_control_depending_on_its_state)この以前トピックです。 サード パーティ製コントロールを使用して状態を指定する必要があります、 <xref:System.Windows.TemplateVisualStateAttribute>、コントロール テンプレートを作成するためのコントロールの状態を公開する、Expression Blend などのデザイナー ツールを有効にします。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属するコントロールのコントロール コントラクトについては、「[コントロールのスタイルとテンプレート](../../../../docs/framework/wpf/controls/control-styles-and-templates.md)」を参照してください。  
  
### <a name="properties-in-the-control-contract"></a>コントロール コントラクトのプロパティ  
 コントロールに視覚的な影響を与えるパブリック プロパティも、コントロール コントラクトに含まれています。 新たに作成することがなく、コントロールの外観を変更するこれらのプロパティを設定することができます<xref:System.Windows.Controls.ControlTemplate>です。 使用することも、 [TemplateBinding](../../../../docs/framework/wpf/advanced/templatebinding-markup-extension.md)内にある要素のプロパティをバインドするマークアップ拡張機能、<xref:System.Windows.Controls.ControlTemplate>によって定義されているパブリック プロパティに、<xref:System.Windows.Controls.Button>です。  
  
 次の例では、ボタンのコントロール コントラクトを示します。  
  
 [!code-csharp[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/controlcontracts.cs#buttoncontract)]
 [!code-vb[VSMButtonTemplate#ButtonContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmbuttontemplate/visualbasic/window1.xaml.vb#buttoncontract)]  
  
 作成するときに、 <xref:System.Windows.Controls.ControlTemplate>、既存の作業を開始する最も簡単なは多くの場合、<xref:System.Windows.Controls.ControlTemplate>し、変更することです。 既存を変更するには、次のいずれかを行うことができます<xref:System.Windows.Controls.ControlTemplate>:  
  
-   Expression Blend などのデザイナーを使用します。デザイナーには、コントロール テンプレートを作成するためのグラフィカル ユーザー インターフェイスが用意されています。 詳細については、「[テンプレートをサポートするコントロールのスタイル処理](http://go.microsoft.com/fwlink/?LinkId=161153)」を参照してください。  
  
-   既定値を取得<xref:System.Windows.Controls.ControlTemplate>し編集することです。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属する既定のコントロール テンプレートについては、「[デフォルトの WPF テーマ](http://go.microsoft.com/fwlink/?LinkID=158252)」を参照してください。  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>コード例全体  
 次の例は、完全な<xref:System.Windows.Controls.Button><xref:System.Windows.Controls.ControlTemplate>このトピックで説明されています。  
  
 [!code-xaml[VSMButtonTemplate#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmbuttontemplate/csharp/skinnedbutton.xaml#3)]  
  
## <a name="see-also"></a>関連項目  
 [スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)
