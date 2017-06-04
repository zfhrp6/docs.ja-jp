---
title: "外観をカスタマイズできるコントロールの作成 | Microsoft Docs"
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
  - "コントロール [WPF], カスタマイズ"
  - "コントロール [WPF], 定義 (視覚的な構造と視覚的な動作を)"
  - "ControlTemplate [WPF], カスタマイズ (外観を)"
  - "カスタマイズ (外観を) [WPF], ControlTemplate"
  - "管理 (コントロールの状態を) [WPF], VisualStateManager"
  - "VisualStateManager [WPF], ベスト プラクティス"
  - "VisualStateManager [WPF], 管理 (コントロールの状態を)"
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 外観をカスタマイズできるコントロールの作成
<a name="introduction"></a> [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] では、外観をカスタマイズできるコントロールを作成できます。  たとえば、新しい <xref:System.Windows.Controls.ControlTemplate> を作成すると、<xref:System.Windows.Controls.CheckBox> の外観に対して、プロパティの設定だけではできないような変更を加えることができます。  次の図は、既定の <xref:System.Windows.Controls.ControlTemplate> を使用する <xref:System.Windows.Controls.CheckBox> と、カスタムの <xref:System.Windows.Controls.ControlTemplate> を使用する <xref:System.Windows.Controls.CheckBox> を示しています。  
  
 ![既定のコントロール テンプレート付きのチェック ボックス](../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP\_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 ![カスタム コントロール テンプレート付きのチェック ボックス](../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP\_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 Parts and States モデルに従って作成されたコントロールは、その外観をカスタマイズできます。  Parts and States モデルは、Microsoft Expression Blend などのデザイナー ツールでサポートされるため、Parts and States モデルに従って作成されたコントロールであれば、これらのデザイナー ツールでカスタマイズできます。  このトピックでは、Parts and States モデルとは何か、また、このモデルに従ってどのように独自のコントロールを作成するのかについて説明します。  また、カスタム コントロールの例として、`NumericUpDown` を使用しながら、このモデルの考え方を説明します。  `NumericUpDown` は数値を表示するコントロールです。ユーザーは、このコントロールのボタンをクリックして数値を増減させることができます。  次の図は、このトピックで説明する `NumericUpDown` コントロールを示しています。  
  
 ![NumericUpDown カスタム コントロール](../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP\_NumericUPDown")  
カスタムの NumericUpDown コントロール  
  
 このトピックは、次のセクションで構成されています。  
  
-   [必要条件](#prerequisites)  
  
-   [Parts and States モデル](#parts_and_states_model)  
  
-   [コントロールの視覚的な構造と視覚的な動作を ControlTemplate で定義する](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [コードから ControlTemplate のパーツを使用する際はベスト プラクティスに従う](#using_parts_of_the_controltemplate_in_code)  
  
-   [コントロール コントラクトを提供する](#providing_the_control_contract)  
  
-   [コード例全体](#complete_example)  
  
<a name="prerequisites"></a>   
## 必要条件  
 このトピックでは、読者が既存のコントロールに新しい <xref:System.Windows.Controls.ControlTemplate> を作成する方法を知っていること、コントロール コントラクトの要素に精通していること、および「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」で説明されている概念を理解していることを前提としています。  
  
> [!NOTE]
>  外観をカスタマイズできるコントロールを作成するには、<xref:System.Windows.Controls.Control> クラスまたはそのサブクラス \(<xref:System.Windows.Controls.UserControl> を除く\) を継承するコントロールを作成する必要があります。  <xref:System.Windows.Controls.UserControl> を継承するコントロールはすばやく作成できますが、<xref:System.Windows.Controls.ControlTemplate> が使用されていないため、外観をカスタマイズすることはできません。  
  
<a name="parts_and_states_model"></a>   
## Parts and States モデル  
 Parts and States モデルでは、コントロールの視覚的な構造と視覚的な動作をどのように定義するかを指定します。  Parts and States モデルに準拠するには、次の作業が必要となります。  
  
-   コントロールの視覚的な構造と視覚的な動作を <xref:System.Windows.Controls.ControlTemplate> で定義する。  
  
-   コントロールのロジックと \(コントロール テンプレートの\) パーツとの接点となる部分を、特定のベスト プラクティスに従って定義する。  
  
-   <xref:System.Windows.Controls.ControlTemplate> に含まれる必要のある事柄を規定した "コントロール コントラクト" を提供する。  
  
 コントロールの視覚的な構造と視覚的な動作が <xref:System.Windows.Controls.ControlTemplate> で定義されている限り、アプリケーション作成者は、コードを記述しなくても、新しい <xref:System.Windows.Controls.ControlTemplate> を作成して、コントロールの視覚的な構造と視覚的な動作を変更できます。  ここで、<xref:System.Windows.Controls.ControlTemplate> で定義されている必要のある <xref:System.Windows.FrameworkElement> のオブジェクトおよび状態を、アプリケーション作成者に対して伝えるコントロール コントラクトを提供する必要があります。  不完全な <xref:System.Windows.Controls.ControlTemplate> が適用されても適切に動作するように、<xref:System.Windows.Controls.ControlTemplate> のパーツとの接点となる部分に関しては、いくつかのベスト プラクティスに従う必要があります。  この 3 つの原則を踏まえてコントロールを作成しておくことで、アプリケーション作成者は、そのコントロールの <xref:System.Windows.Controls.ControlTemplate> を、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属のコントロールに対して作成する場合と同じように簡単に作成できます。  これらの推奨事項については、以下のセクションで詳しく説明します。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## コントロールの視覚的な構造と視覚的な動作を ControlTemplate で定義する  
 Parts and States モデルに従ってカスタム コントロールを作成するときは、コントロールの視覚的な構造と視覚的な動作をコントロールのロジックではなく <xref:System.Windows.Controls.ControlTemplate> で定義します。  コントロールの視覚的な構造は、そのコントロールを構成するさまざまな <xref:System.Windows.FrameworkElement> オブジェクトの複合体と考えることができます。  視覚的な動作とは、コントロールが特定の状態になったときにどのように表示されるかということです。  <xref:System.Windows.Controls.ControlTemplate> を作成して、コントロールの視覚的な構造と視覚的な動作を指定する方法の詳細については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」を参照してください。  
  
 `NumericUpDown` コントロールの場合、視覚的な構造には、2 つの <xref:System.Windows.Controls.Primitives.RepeatButton> コントロールと、1 つの <xref:System.Windows.Controls.TextBlock> が含まれます。  これらのコントロールを、`NumericUpDown` コントロールのコード \(コンストラクターなど\) で追加した場合、コントロールの位置を変更できなくなります。  コントロールの視覚的な構造と視覚的な動作は、コードではなく <xref:System.Windows.Controls.ControlTemplate> で定義する必要があります。  このように設計することで、アプリケーション開発者は、<xref:System.Windows.Controls.ControlTemplate> を置き換えて、ボタンや <xref:System.Windows.Controls.TextBlock> の位置をカスタマイズし、`Value` が負数になったときの動作を指定できます。  
  
 次の例は、`NumericUpDown` コントロールの視覚的な構造を示しています。このコントロールには、`Value` を増加させるための <xref:System.Windows.Controls.Primitives.RepeatButton>、`Value` を減少させるための <xref:System.Windows.Controls.Primitives.RepeatButton>、および `Value` を表示するための <xref:System.Windows.Controls.TextBlock> が含まれています。  
  
 [!code-xml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 この `NumericUpDown` コントロールは、負の値を赤色のフォントで表示するという、視覚的な動作を持ちます。  `Value` が負数のときに <xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.TextBlock.Foreground%2A> を変更するという処理をコードで記述した場合、`NumericUpDown` は負の値を赤色でしか表示できなくなります。  コントロールの視覚的な動作は <xref:System.Windows.Controls.ControlTemplate> で <xref:System.Windows.Controls.ControlTemplate> に <xref:System.Windows.VisualState> オブジェクトを追加して指定します。  次の例は、`Positive` または `Negative` の状態に対応する <xref:System.Windows.VisualState> オブジェクトを示しています。  `Positive` と `Negative` は同時に指定できない \(同時に 2 つの状態であることはできない\) ため、この例では <xref:System.Windows.VisualState> オブジェクトを単一の <xref:System.Windows.VisualStateGroup> にまとめています。  コントロールが `Negative` 状態に移行した場合、<xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.TextBlock.Foreground%2A> が赤色に変化します。  コントロールが `Positive` 状態の場合、<xref:System.Windows.Controls.TextBlock.Foreground%2A> が元の値に戻ります。  <xref:System.Windows.Controls.ControlTemplate> で <xref:System.Windows.VisualState> オブジェクトを定義する方法については、「[ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)」で詳しく説明しています。  
  
> [!NOTE]
>  <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 添付プロパティを <xref:System.Windows.Controls.ControlTemplate> のルート <xref:System.Windows.FrameworkElement> に設定してください。  
  
 [!code-xml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## コードから ControlTemplate のパーツを使用する際はベスト プラクティスに従う  
 <xref:System.Windows.Controls.ControlTemplate> の作成者が必ずしも <xref:System.Windows.FrameworkElement> オブジェクトや <xref:System.Windows.VisualState> オブジェクトを厳密に定義するとは限りません。意図的に、または間違いによって、それらのオブジェクトが省略される可能性があります。しかし、カスタム コントロールのロジックでは、これらのパーツが適切に機能することが必要となる場合があります。  <xref:System.Windows.Controls.ControlTemplate> からの <xref:System.Windows.FrameworkElement> や <xref:System.Windows.VisualState> オブジェクトの欠落に対応できることは、Parts and States モデルがコントロールに対して求めている条件の 1 つでもあります。  <xref:System.Windows.FrameworkElement>、<xref:System.Windows.VisualState>、<xref:System.Windows.VisualStateGroup> などが <xref:System.Windows.Controls.ControlTemplate> に存在しない場合でも、カスタム コントロールが例外をスローする、またはエラーを報告することのないようにする必要があります。  このセクションでは、<xref:System.Windows.FrameworkElement> オブジェクトとの対話や状態の管理に関するベスト プラクティスについて説明します。  
  
### FrameworkElement オブジェクトが存在しない可能性を想定する  
 <xref:System.Windows.Controls.ControlTemplate> で <xref:System.Windows.FrameworkElement> オブジェクトを定義する場合、カスタム コントロールのロジックの中で、そのいくつかのオブジェクトとの対話が必要になることがあります。  たとえば、`NumericUpDown` コントロールは、ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントをサブスクライブして `Value` を増減させ、<xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.TextBlock.Text%2A> プロパティを `Value` に設定します。  カスタム <xref:System.Windows.Controls.ControlTemplate> で <xref:System.Windows.Controls.TextBlock> やボタンが省略され、そのコントロールのいくつかの機能が失われていても、コントロールは使用できます。ただし、そのような場合でも、コントロールがエラーを発生させないようにする必要があります。  たとえば、<xref:System.Windows.Controls.ControlTemplate> に `Value` を変更するためのボタンが存在しないと、`NumericUpDown` はその機能を果たせなくなりますが、それによって、<xref:System.Windows.Controls.ControlTemplate> を使用しているアプリケーションの実行が中断されることは避ける必要があります。  
  
 <xref:System.Windows.FrameworkElement> オブジェクトの欠落に適切に対処するためのベスト プラクティスを次に示します。  
  
1.  コード内で参照する必要のある各 <xref:System.Windows.FrameworkElement> に `x:Name` 属性を設定します。  
  
2.  対話する必要のある各 <xref:System.Windows.FrameworkElement> についてプライベート プロパティを定義します。  
  
3.  カスタム コントロールで処理するイベントのサブスクライブとアンサブスクライブを、<xref:System.Windows.FrameworkElement> プロパティの set アクセサーで行います。  
  
4.  手順 2. で定義した <xref:System.Windows.FrameworkElement> プロパティを、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> メソッドで設定します。  これが、コントロールから <xref:System.Windows.Controls.ControlTemplate> の <xref:System.Windows.FrameworkElement> にアクセスできる最も早いタイミングです。  <xref:System.Windows.FrameworkElement> を <xref:System.Windows.Controls.ControlTemplate> から取得する際は、`x:Name` を使用します。  
  
5.  <xref:System.Windows.FrameworkElement> が `null` でないことを、そのメンバーにアクセスする前に確認します。  `null` であったとしても、エラーを報告しないようにします。  
  
 以上の推奨事項に従って作成された `NumericUpDown` コントロールの例を次に示します。<xref:System.Windows.FrameworkElement> オブジェクトの扱いに注目しながら参照してください。  
  
 この例では、`NumericUpDown` コントロールの視覚的な構造が <xref:System.Windows.Controls.ControlTemplate> で定義されています。`Value` を増やすための <xref:System.Windows.Controls.Primitives.RepeatButton> は、その `x:Name` 属性が `UpButton` に設定されています。  次の例を見ると、<xref:System.Windows.Controls.ControlTemplate> で定義された <xref:System.Windows.Controls.Primitives.RepeatButton> を表す `UpButtonElement` というプロパティが宣言されていることがわかります。  `set` アクセサーでは、まず、`UpDownElement` が `null` 以外の場合に、ボタンの <xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントをアンサブスクライブし、そのプロパティを設定した後、<xref:System.Windows.Controls.Primitives.ButtonBase.Click> イベントをサブスクライブしています。  ここでは示していませんが、他の <xref:System.Windows.Controls.Primitives.RepeatButton> プロパティも `DownButtonElement` という名前で定義されています。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 次の例は、`NumericUpDown` コントロールの <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> を示しています。  この例では、<xref:System.Windows.Controls.ControlTemplate> から <xref:System.Windows.FrameworkElement> オブジェクトを取得するために、<xref:System.Windows.FrameworkElement.GetTemplateChild%2A> メソッドが使用されています。  <xref:System.Windows.FrameworkElement.GetTemplateChild%2A> で、想定外の型の名前が指定された <xref:System.Windows.FrameworkElement> が見つかった場合の対策がなされている点に注目してください。  また、指定された `x:Name` を持つ要素でも、型が間違っている場合は無視しています。これも 1 つのベスト プラクティスです。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 <xref:System.Windows.Controls.ControlTemplate> に <xref:System.Windows.FrameworkElement> が存在していなくても、前の例に示したベスト プラクティスに従っていれば、コントロールの実行が妨げられることはありません。  
  
### VisualStateManager を使用して状態を管理する  
 <xref:System.Windows.VisualStateManager> はコントロールの状態を追跡し、状態間の遷移に必要なロジックを実行します。  <xref:System.Windows.Controls.ControlTemplate> に <xref:System.Windows.VisualState> オブジェクトを追加する場合は、それらを <xref:System.Windows.VisualStateGroup> に追加し、さらに、その <xref:System.Windows.VisualStateGroup> を <xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=fullName> 添付プロパティに追加して、<xref:System.Windows.VisualStateManager> からアクセスできるようにします。  
  
 次の例は、前の例に続き、コントロールの `Positive` 状態および `Negative` 状態に対応する <xref:System.Windows.VisualState> オブジェクトを示しています。  `Negative` <xref:System.Windows.VisualState> の <xref:System.Windows.Media.Animation.Storyboard> は、<xref:System.Windows.Controls.TextBlock> の <xref:System.Windows.Controls.TextBlock.Foreground%2A> を赤色に変化させます。  `NumericUpDown` コントロールが `Negative` 状態になると、`Negative` 状態のストーリーボードが開始されます。  `Negative` 状態の <xref:System.Windows.Media.Animation.Storyboard> は、コントロールが `Positive` 状態に戻ると停止します。  `Negative` の <xref:System.Windows.Media.Animation.Storyboard> が停止した場合、<xref:System.Windows.Controls.TextBlock.Foreground%2A> が元の色に戻るため、`Positive` <xref:System.Windows.VisualState> には、必ずしも <xref:System.Windows.Media.Animation.Storyboard> が存在している必要はありません。  
  
 [!code-xml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 <xref:System.Windows.Controls.TextBlock> には名前が付けられますが、<xref:System.Windows.Controls.TextBlock> は `NumericUpDown` のコントロール コントラクトに存在しないことに注意してください。これは、コントロールのロジックが <xref:System.Windows.Controls.TextBlock> を参照しないためです。  名前を持つ要素は <xref:System.Windows.Controls.ControlTemplate> で参照されますが、コントロール コントラクトの一部である必要はありません。コントロールの新しい <xref:System.Windows.Controls.ControlTemplate> は、その要素を参照する必要がないことがあるためです。  たとえば、`NumericUpDown` の新しい <xref:System.Windows.Controls.ControlTemplate> を作成する人が、<xref:System.Windows.Controls.Control.Foreground%2A> を変更して、その `Value` が負数であることを示さなかったとします。  この場合、コードも <xref:System.Windows.Controls.ControlTemplate> も <xref:System.Windows.Controls.TextBlock> を名前で参照しません。  
  
 コントロールの状態は、コントロールのロジックで変更します。  次の例では、`Value` が 0 以上の場合は `Positive` 状態に移行し、`Value` が 0 未満の場合は `Negative` 状態に移行するというロジックを、`NumericUpDown` コントロールから <xref:System.Windows.VisualStateManager.GoToState%2A> メソッドを呼び出して実現しています。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A> メソッドは、ストーリーボードを開始または停止するために必要なロジックを実行します。  コントロールがその状態を変化させるために <xref:System.Windows.VisualStateManager.GoToState%2A> を呼び出すと、<xref:System.Windows.VisualStateManager> によって次の処理が実行されます。  
  
-   これから移行しようとしている <xref:System.Windows.VisualState> に <xref:System.Windows.Media.Animation.Storyboard> が存在する場合は、そのストーリーボードを開始します。  さらに、移行前の <xref:System.Windows.VisualState> に <xref:System.Windows.Media.Animation.Storyboard> が存在する場合は、そのストーリーボードを終了します。  
  
-   コントロールが既に指定された状態である場合、<xref:System.Windows.VisualStateManager.GoToState%2A> は何も実行せずに、`true` を返します。  
  
-   `control` の <xref:System.Windows.Controls.ControlTemplate> に存在しない状態が指定された場合、<xref:System.Windows.VisualStateManager.GoToState%2A> は何も実行せずに、`false` を返します。  
  
#### VisualStateManager の使用上のベスト プラクティス  
 コントロールの状態を管理する際は、次のようにすることをお勧めします。  
  
-   プロパティを使用してその状態を追跡する。  
  
-   状態を遷移させるためのヘルパー メソッドを作成する。  
  
 `NumericUpDown` コントロールは、その `Value` プロパティを使用してその状態 \(`Positive` または `Negative`\) を追跡します。  また、`NumericUpDown` コントロールは `Focused` および `UnFocused` の状態を定義することで、<xref:System.Windows.UIElement.IsFocused%2A> プロパティも追跡します。  コントロールのプロパティに元から対応していない状態を使用する場合は、プライベート プロパティを定義して状態を追跡できます。  
  
 単一のメソッドですべての状態を更新して <xref:System.Windows.VisualStateManager> への呼び出しを集中化することで、コードを管理できる状態に保ちます。  次の例は、`NumericUpDown` コントロールのヘルパー メソッド `UpdateStates` です。  `Value` が 0 以上の場合、<xref:System.Windows.Controls.Control> は `Positive` 状態になります。  `Value` が 0 未満の場合、コントロールは `Negative` 状態になります。  <xref:System.Windows.UIElement.IsFocused%2A> が `true` の場合、コントロールは `Focused` 状態になり、それ以外の場合は `Unfocused` 状態になります。  コントロールは、どの状態への変更であるかに関係なく、状態を変更する必要があるときは常に `UpdateStates` を呼び出すことができます。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 特定の状態の名前を <xref:System.Windows.VisualStateManager.GoToState%2A> に渡した場合、コントロールが既にその状態になっていれば、<xref:System.Windows.VisualStateManager.GoToState%2A> は何も実行しません。したがって、コントロールの現在の状態を確認する必要はありません。  たとえば、`Value` が負数から別の負数に変化した場合、`Negative` 状態のストーリーボードは中断されず、ユーザーから見てもコントロールの外観は変化しません。  
  
 <xref:System.Windows.VisualStateManager> は、<xref:System.Windows.VisualStateManager.GoToState%2A> が呼び出されたときに、どの状態を終了させればよいかを、<xref:System.Windows.VisualStateGroup> オブジェクトを使って判断します。  <xref:System.Windows.VisualStateGroup> は <xref:System.Windows.Controls.ControlTemplate> に定義されており、コントロールは、それぞれの VisualStateGroup につき必ず 1 つの状態を持ちます。この状態が失われるのは、同じ <xref:System.Windows.VisualStateGroup> 内の別の状態に移行するときだけです。  たとえば、`NumericUpDown` コントロールの <xref:System.Windows.Controls.ControlTemplate> には、`Positive` と `Negative` という <xref:System.Windows.VisualState> オブジェクトと、`Focused` と `Unfocused` という <xref:System.Windows.VisualState> オブジェクトが、それぞれ異なる <xref:System.Windows.VisualStateGroup> に定義されています   \(`Focused` と `Unfocused` <xref:System.Windows.VisualState> が定義されているところは、このトピックの「[コード例全体](#complete_example)」で参照できます\)。コントロールの状態が `Positive` から `Negative` に \(または逆の状態に\) 変化した場合、コントロールは `Focused` または `Unfocused` の状態のままになります。  
  
 一般に、コントロールの状態が変化するタイミングとしては、次の 3 つが考えられます。  
  
-   <xref:System.Windows.Controls.Control> に <xref:System.Windows.Controls.ControlTemplate> が適用されたとき。  
  
-   プロパティが変化したとき。  
  
-   イベントが発生したとき。  
  
 それぞれのケースで `NumericUpDown` コントロールの状態を更新する例を次に示します。  
  
 コントロールの状態は <xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> メソッドで更新する必要があります。これにより、<xref:System.Windows.Controls.ControlTemplate> の適用時にコントロールが正しい状態で表示されます。  次の例では、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A> で `UpdateStates` を呼び出して、コントロールを適切な状態に移行させています。  たとえば、`NumericUpDown` コントロールを作成し、その <xref:System.Windows.Controls.Control.Foreground%2A> を緑色に設定し、`Value` を \-5 に設定したとします。  `NumericUpDown` コントロールに <xref:System.Windows.Controls.ControlTemplate> を適用する際に `UpdateStates` を呼び出さなかった場合、コントロールの状態が `Negative` に移行せず、値が赤色ではなく緑色で表示されます。  コントロールを `Negative` 状態に移行させるには、`UpdateStates` を呼び出す必要があります。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 プロパティが変更された場合にコントロールの状態を更新するケースも珍しくありません。  次の例は、`ValueChangedCallback` メソッド全体のコードを示しています。  `ValueChangedCallback` は `Value` が変化するたびにメソッドで呼び出されるため、`UpdateStates` の呼び出しは、`Value` が正から負に \(または負から正に\) 変化したときに行われます。  正数であるか負数であるかにかかわらず `Value` が変化したときに常に `UpdateStates` を呼び出すことができます \(正負の変化がなければ、コントロールの状態は変化しないため\)。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 イベントの発生時に状態を更新するケースもあります。  次の例では、`NumericUpDown` が <xref:System.Windows.Controls.Control> の `UpdateStates` を呼び出して、<xref:System.Windows.UIElement.GotFocus> イベントを処理しています。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager> を使用すると、コントロールの状態を簡単に管理できます。  <xref:System.Windows.VisualStateManager> を使用すると、コントロールの状態を正しく遷移させることができます。  このセクションで述べた推奨事項に従って <xref:System.Windows.VisualStateManager> を使用すると、コントロールのコードが読みやすくなり、コードの保守性が向上します。  
  
<a name="providing_the_control_contract"></a>   
## コントロール コントラクトを提供する  
 コントロール コントラクトが提供されている場合、<xref:System.Windows.Controls.ControlTemplate> 作成者は、これから作成しようとしているテンプレートに何を定義するのかを知ることができます。  コントロール コントラクトには、3 つの要素があります。  
  
-   コントロールのロジックが使用する視覚的要素。  
  
-   コントロールの状態と各状態が属するグループ。  
  
-   コントロールに対して視覚的に作用するパブリック プロパティ。  
  
 新しい <xref:System.Windows.Controls.ControlTemplate> の作成者が、まず必要とする情報は、コントロールのロジックに使用されている <xref:System.Windows.FrameworkElement> オブジェクトと、それぞれのオブジェクトの型および名前です。  また、<xref:System.Windows.Controls.ControlTemplate> の作成者は、さらにコントロールに想定されているすべての状態の名前と、それぞれの状態がどの <xref:System.Windows.VisualStateGroup> に属しているかを知っておく必要があります。  
  
 前の `NumericUpDown` コントロールの場合、<xref:System.Windows.Controls.ControlTemplate> には次の <xref:System.Windows.FrameworkElement> オブジェクトが必要です。  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton> \(`UpButton`\)  
  
-   <xref:System.Windows.Controls.Primitives.RepeatButton> \(`DownButton.`\)  
  
 コントロールに想定されている状態は次のとおりです。  
  
-   `ValueStates` <xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   `FocusStates` <xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 コントロールに必要な <xref:System.Windows.FrameworkElement> オブジェクトを指定するには、<xref:System.Windows.TemplatePartAttribute> を使用して、必要な要素の名前と型を指定します。  コントロールに想定されている状態を指定するには、<xref:System.Windows.TemplateVisualStateAttribute> を使用して、状態の名前とその所属先の <xref:System.Windows.VisualStateGroup> を指定します。  <xref:System.Windows.TemplatePartAttribute> および <xref:System.Windows.TemplateVisualStateAttribute> は、コントロールのクラス定義に記述します。  
  
 コントロールの外観に影響するパブリック プロパティもコントロール コントラクトの一部です。  
  
 次の例では、`NumericUpDown` コントロールの <xref:System.Windows.FrameworkElement> オブジェクトおよび状態を指定しています。  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## コード例全体  
 次の例は、`NumericUpDown` コントロールの完全な <xref:System.Windows.Controls.ControlTemplate> です。  
  
 [!code-xml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 `NumericUpDown` のロジックの例を次に示します。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## 参照  
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)   
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)