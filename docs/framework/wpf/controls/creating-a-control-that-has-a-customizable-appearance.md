---
title: 外観をカスタマイズできるコントロールの作成
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], customizing
- VisualStateManager [WPF], managing the state of a control
- ControlTemplate [WPF], customizing appearance
- controls [WPF], defining the visual structure and behavior of
- customizing appearance [WPF], ControlTemplate
- managing control states [WPF], VisualStateManager
- VisualStateManager [WPF], best practice
ms.assetid: 9e356d3d-a3d0-4b01-a25f-2d43e4d53fe5
ms.openlocfilehash: 9f539e7dbb105591375857122d738fddd87f6776
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558279"
---
# <a name="creating-a-control-that-has-a-customizable-appearance"></a>外観をカスタマイズできるコントロールの作成
<a name="introduction"></a>
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] 外観をカスタマイズできるコントロールを作成する機能を提供します。 たとえばの外観を変更することができます、<xref:System.Windows.Controls.CheckBox>どのような設定を超えるプロパティには、新たに作成する<xref:System.Windows.Controls.ControlTemplate>です。 次の図は、 <xref:System.Windows.Controls.CheckBox> 、既定値を使用する<xref:System.Windows.Controls.ControlTemplate>と<xref:System.Windows.Controls.CheckBox>を使用するカスタム<xref:System.Windows.Controls.ControlTemplate>です。  
  
 ![既定のコントロール テンプレート付きのチェック ボックスです。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxdefault.png "NDP_CheckBoxDefault")  
既定のコントロール テンプレートを使用する CheckBox  
  
 ![カスタム コントロール テンプレート付きのチェック ボックスをオンします。] (../../../../docs/framework/wpf/controls/media/ndp-checkboxcustom.png "NDP_CheckBoxCustom")  
カスタム コントロール テンプレートを使用する CheckBox  
  
 従うと、パーツと状態モデル コントロールを作成するときに、コントロールの外観はカスタマイズ可能になります。 Microsoft Expression Blend などのデザイナー ツールは、このモデルをたどるときに自分の管理されるため、これらの種類のアプリケーションでカスタマイズ可能なパーツと状態のモデルをサポートします。  このトピックは、パーツと状態のモデルと独自のコントロールを作成するときにそれを追跡する方法について説明します。 このトピックは、カスタム コントロールの例を使用して`NumericUpDown`、このモデルの原理を説明するためにします。  `NumericUpDown`コントロール ユーザーを増やすことも、コントロールのボタンをクリックして軽減する数値の値が表示されます。  次の図は、`NumericUpDown`このトピックで説明されているコントロール。  
  
 ![NumericUpDown カスタム コントロールです。] (../../../../docs/framework/wpf/controls/media/ndp-numericupdown.png "NDP_NumericUPDown")  
カスタムの NumericUpDown コントロール  
  
 このトピックは、次のセクションで構成されています。  
  
-   [前提条件](#prerequisites)  
  
-   [パーツと状態モデル](#parts_and_states_model)  
  
-   [ControlTemplate の視覚的な構造およびコントロールの視覚的な動作の定義](#defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate)  
  
-   [コードで ControlTemplate のパーツを使用します。](#using_parts_of_the_controltemplate_in_code)  
  
-   [コントロールのコントラクトを提供します。](#providing_the_control_contract)  
  
-   [コード例を全体します。](#complete_example)  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 ここでは、新しいを作成する方法がわかっている<xref:System.Windows.Controls.ControlTemplate>の既存のコントロールに慣れてコントロール コントラクト上の要素とは何かで説明する概念を理解して[によって既存のコントロールの外観のカスタマイズ作成、ControlTemplate](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)です。  
  
> [!NOTE]
>  カスタマイズされた外観を持つことができるコントロールを作成するから継承するコントロールを作成する必要があります、<xref:System.Windows.Controls.Control>クラスまたは以外のサブクラスのいずれかの<xref:System.Windows.Controls.UserControl>します。  継承されたコントロール<xref:System.Windows.Controls.UserControl>をすばやく作成できるコントロールは使用されませんが、<xref:System.Windows.Controls.ControlTemplate>の外観をカスタマイズすることはできません。  
  
<a name="parts_and_states_model"></a>   
## <a name="parts-and-states-model"></a>パーツと状態モデル  
 パーツと状態のモデルでは、コントロールのビジュアルの動作と視覚的な構造を定義する方法を指定します。 モデルに従うパーツと状態には、次の操作を行う必要があります。  
  
-   視覚的な構造およびで視覚的な動作を定義、<xref:System.Windows.Controls.ControlTemplate>コントロールのです。  
  
-   コントロールのロジックは、コントロール テンプレートの部分を操作するとき、一部のベスト プラクティスに従います。  
  
-   新機能に含めるかを指定するコントロールのコントラクトを実現、<xref:System.Windows.Controls.ControlTemplate>です。  
  
 視覚的な構造およびで視覚的な動作を定義する場合、 <xref:System.Windows.Controls.ControlTemplate> 、コントロールのアプリケーションの作成者、視覚的な構造や動作を変更 visual、コントロールの新規作成することで<xref:System.Windows.Controls.ControlTemplate>コードを記述する代わりにします。   人の作成者がアプリケーションに通知するコントロールのコントラクトを指定する必要があります<xref:System.Windows.FrameworkElement>でのオブジェクトと状態を定義する必要があります、<xref:System.Windows.Controls.ControlTemplate>です。 内のパーツと対話するときのベスト プラクティスを従う必要があります、<xref:System.Windows.Controls.ControlTemplate>コントロールを適切に処理が完了していないように<xref:System.Windows.Controls.ControlTemplate>です。  アプリケーションの作成者が作成できる場合は、これら 3 つの原則に従うと、<xref:System.Windows.Controls.ControlTemplate>だけで、コントロールのように簡単にすることができます、コントロールのと共に出荷[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]です。  次のセクションでは、これらの推奨事項の詳細について説明します。  
  
<a name="defining_the_visual_structure_and_visual_behavior_of_a_control_in_a_controltemplate"></a>   
## <a name="defining-the-visual-structure-and-visual-behavior-of-a-control-in-a-controltemplate"></a>ControlTemplate の視覚的な構造およびコントロールの視覚的な動作の定義  
 コントロールの視覚的な構造とで視覚的な動作を定義する、パーツと状態モデルを使用して、カスタム コントロールを作成するときにその<xref:System.Windows.Controls.ControlTemplate>の代わりにそのロジックにします。  コントロールの視覚的な構造は、複合<xref:System.Windows.FrameworkElement>コントロールを構成するオブジェクト。  視覚的な動作は特定の状態にあるときに、コントロールが表示されます。   作成の詳細については、<xref:System.Windows.Controls.ControlTemplate>視覚的な構造およびコントロールの視覚的な動作を指定するを参照してください[、ControlTemplate を作成することで、既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)です。  
  
 例では、`NumericUpDown`コントロール、視覚的な構造には、2 つ<xref:System.Windows.Controls.Primitives.RepeatButton>コントロールと<xref:System.Windows.Controls.TextBlock>です。  コードでこれらのコントロールを追加した場合、`NumericUpDown`のコンス トラクターに、たとえば----コントロール、そのコントロールの位置は変更できません。  コントロールの視覚的な構造と視覚的な動作を定義するコードに、代わりでを定義する必要があります、<xref:System.Windows.Controls.ControlTemplate>です。  アプリケーション開発者は、ボタンの位置をカスタマイズして<xref:System.Windows.Controls.TextBlock>して、どのような動作が発生したときに`Value`が負の値ため、<xref:System.Windows.Controls.ControlTemplate>置き換えることができます。  
  
 次の例の視覚的な構造を示しています、`NumericUpDown`が含まれるコントロール、<xref:System.Windows.Controls.Primitives.RepeatButton>を増やすには`Value`、<xref:System.Windows.Controls.Primitives.RepeatButton>を削減する`Value`、および<xref:System.Windows.Controls.TextBlock>を表示する`Value`です。  
  
 [!code-xaml[VSMCustomControl#VisualStructure](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#visualstructure)]  
  
 視覚的な動作、`NumericUpDown`コントロールが負の値である場合、値が赤いフォントであります。  変更した場合、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>ときにコードで、`Value`は負の値、`NumericUpDown`赤い負の値は常に表示します。 内のコントロールの視覚的な動作を指定する、<xref:System.Windows.Controls.ControlTemplate>を追加して<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.Controls.ControlTemplate>です。  次の例は、<xref:System.Windows.VisualState>オブジェクトに対する、`Positive`と`Negative`状態です。  `Positive` および`Negative`(コントロールが常に 2 つのいずれかの) は相互に排他的なのでの例では、<xref:System.Windows.VisualState>を単一のオブジェクト<xref:System.Windows.VisualStateGroup>です。  コントロールに入るときに、 `Negative` 、状態、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>赤色に変わります。  コントロールがの場合、 `Positive` 、状態、<xref:System.Windows.Controls.TextBlock.Foreground%2A>が戻された元の値。  定義する<xref:System.Windows.VisualState>内のオブジェクト、<xref:System.Windows.Controls.ControlTemplate>で詳しく説明は[、ControlTemplate を作成することで、既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)です。  
  
> [!NOTE]
>  設定して、<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティのルートに<xref:System.Windows.FrameworkElement>の<xref:System.Windows.Controls.ControlTemplate>です。  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
<a name="using_parts_of_the_controltemplate_in_code"></a>   
## <a name="using-parts-of-the-controltemplate-in-code"></a>コードで ControlTemplate のパーツを使用します。  
 A<xref:System.Windows.Controls.ControlTemplate>省略があります。 作成者<xref:System.Windows.FrameworkElement>または<xref:System.Windows.VisualState>オブジェクト、意図的または誤って、のいずれかが、コントロールのロジックで正しく機能する部分が必要です。 パーツと状態のモデルでは、自分の管理に対応する必要がありますを指定します、<xref:System.Windows.Controls.ControlTemplate>をがな<xref:System.Windows.FrameworkElement>または<xref:System.Windows.VisualState>オブジェクト。  コントロールがエラーをスローしません、例外またはレポート場合、 <xref:System.Windows.FrameworkElement>、 <xref:System.Windows.VisualState>、または<xref:System.Windows.VisualStateGroup>が表示されない、<xref:System.Windows.Controls.ControlTemplate>です。 このセクションの内容と対話するための推奨事項を説明します<xref:System.Windows.FrameworkElement>オブジェクトし、状態を管理します。  
  
### <a name="anticipate-missing-frameworkelement-objects"></a>FrameworkElement のオブジェクトの不足を予測します。  
 定義するときに<xref:System.Windows.FrameworkElement>内のオブジェクト、<xref:System.Windows.Controls.ControlTemplate>コントロールのロジックは、それらの一部と対話する必要があります。  たとえば、`NumericUpDown`ボタンをサブスクライブするコントロール<xref:System.Windows.Controls.Primitives.ButtonBase.Click>増減するイベント`Value`設定と、<xref:System.Windows.Controls.TextBlock.Text%2A>のプロパティ、<xref:System.Windows.Controls.TextBlock>に`Value`です。 場合、カスタム<xref:System.Windows.Controls.ControlTemplate>省略、<xref:System.Windows.Controls.TextBlock>またはボタンが受け入れのコントロールでは、その機能の一部が失われますが、コントロールには、エラーは発生しないことを確認する必要があります。 たとえば場合、<xref:System.Windows.Controls.ControlTemplate>を変更するためのボタンが含まれていない`Value`、`NumericUpDown`その機能が使用するアプリケーションが失う、<xref:System.Windows.Controls.ControlTemplate>は引き続き実行します。  
  
 次の方法はありませんに、コントロールが適切に応答していることを確認<xref:System.Windows.FrameworkElement>オブジェクト。  
  
1.  設定、`x:Name`ごとに属性<xref:System.Windows.FrameworkElement>コード内で参照する必要があります。  
  
2.  それぞれのプライベート プロパティを定義<xref:System.Windows.FrameworkElement>と対話する必要があります。  
  
3.  サブスクライブし、すべてのイベントに、コントロールが処理されるサブスクリプションの解除、<xref:System.Windows.FrameworkElement>プロパティのアクセサーを設定します。  
  
4.  設定、<xref:System.Windows.FrameworkElement>プロパティで定義されている手順 2、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>メソッドです。 これは、できるだけ早くを<xref:System.Windows.FrameworkElement>で、<xref:System.Windows.Controls.ControlTemplate>はコントロールに使用できます。 使用して、`x:Name`の<xref:System.Windows.FrameworkElement>から取得する、<xref:System.Windows.Controls.ControlTemplate>です。  
  
5.  確認、<xref:System.Windows.FrameworkElement>は`null`そのメンバーにアクセスする前にします。  場合は`null`エラーを報告しません。  
  
 次の例に示す方法、`NumericUpDown`コントロールが対話<xref:System.Windows.FrameworkElement>上記の項目の推奨事項に従ってオブジェクト。  
  
 視覚的な構造の定義の例では、`NumericUpDown`内の制御、 <xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.Controls.Primitives.RepeatButton>を増加`Value`がその`x:Name`属性に設定`UpButton`です。  次の例と呼ばれるプロパティの宣言`UpButtonElement`を表す、<xref:System.Windows.Controls.Primitives.RepeatButton>に宣言されている、<xref:System.Windows.Controls.ControlTemplate>です。 `set`アクセサーを最初に、ボタンのアンサブスク ライブ<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント場合`UpDownElement`は`null`、次のプロパティを設定およびにサブスクライブし、<xref:System.Windows.Controls.Primitives.ButtonBase.Click>イベント。 プロパティ定義しますが、一方についてはここでは、表示されませんがも<xref:System.Windows.Controls.Primitives.RepeatButton>という`DownButtonElement`です。  
  
 [!code-csharp[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#upbuttonproperty)]
 [!code-vb[VSMCustomControl#UpButtonProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#upbuttonproperty)]  
  
 次の例は、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>の`NumericUpDown`コントロール。  この例では、<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>取得するメソッド、<xref:System.Windows.FrameworkElement>オブジェクトから、<xref:System.Windows.Controls.ControlTemplate>です。  例を防ぐことに注意してくださいであるのケース<xref:System.Windows.FrameworkElement.GetTemplateChild%2A>検索、<xref:System.Windows.FrameworkElement>予期された型が指定の名前を持つ。 持つ、指定した要素を無視することはお勧めも`x:Name`間違った型が、します。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 は、前の例に示すようなプラクティスを確認するときに実行する、コントロールが引き続き、<xref:System.Windows.Controls.ControlTemplate>がない、<xref:System.Windows.FrameworkElement>です。  
  
### <a name="use-the-visualstatemanager-to-manage-states"></a>使用して、VisualStateManager を管理状態  
 <xref:System.Windows.VisualStateManager>のコントロールの状態を追跡し、状態を切り替えるのために必要なロジックを実行します。 追加すると<xref:System.Windows.VisualState>オブジェクトを<xref:System.Windows.Controls.ControlTemplate>に追加する、<xref:System.Windows.VisualStateGroup>を追加し、<xref:System.Windows.VisualStateGroup>を<xref:System.Windows.VisualStateManager.VisualStateGroups%2A?displayProperty=nameWithType>添付プロパティできるように、<xref:System.Windows.VisualStateManager>へのアクセス権を持ちます。  
  
 次の例は、前の例を示すを繰り返し、<xref:System.Windows.VisualState>に対応するオブジェクト、`Positive`と`Negative`コントロールの状態。 <xref:System.Windows.Media.Animation.Storyboard>で、 `Negative` <xref:System.Windows.VisualState>オン、<xref:System.Windows.Controls.TextBlock.Foreground%2A>の<xref:System.Windows.Controls.TextBlock>赤です。   ときに、`NumericUpDown`コントロールが、`Negative`でストーリー ボードの状態、`Negative`状態を開始します。  次に、<xref:System.Windows.Media.Animation.Storyboard>で、`Negative`停止の状態に、制御が戻るとき、`Positive`状態です。  `Positive` <xref:System.Windows.VisualState>を格納する必要はありません、<xref:System.Windows.Media.Animation.Storyboard>ためと、<xref:System.Windows.Media.Animation.Storyboard>の`Negative`停止すると、<xref:System.Windows.Controls.TextBlock.Foreground%2A>元の色を返します。  
  
 [!code-xaml[VSMCustomControl#ValueStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/window1.xaml#valuestates)]  
  
 なお、 <xref:System.Windows.Controls.TextBlock> 、名前を付けたですが、<xref:System.Windows.Controls.TextBlock>コントロールのコントラクトには`NumericUpDown`コントロールのロジックを参照しないため、<xref:System.Windows.Controls.TextBlock>です。  参照される要素、<xref:System.Windows.Controls.ControlTemplate>名を付ける必要しますが、ないコントロール コントラクトの一部にするために、新しい<xref:System.Windows.Controls.ControlTemplate>のコントロールがその要素を参照する必要はありません。  たとえば、ユーザーが新たに作成した<xref:System.Windows.Controls.ControlTemplate>の`NumericUpDown`をことを示していないことができます`Value`を変更して負の値が、<xref:System.Windows.Controls.Control.Foreground%2A>です。  その場合、どちらも、コードでも<xref:System.Windows.Controls.ControlTemplate>参照、<xref:System.Windows.Controls.TextBlock>名前。  
  
 コントロールのロジックは、コントロールの状態を変更します。 次の例を`NumericUpDown`通話を制御、<xref:System.Windows.VisualStateManager.GoToState%2A>にメソッド、`Positive`状態に`Value`は 0 以上および`Negative`状態に`Value`が 0 未満です。  
  
 [!code-csharp[VSMCustomControl#ValueStateChange](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#valuestatechange)]
 [!code-vb[VSMCustomControl#ValueStateChange](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#valuestatechange)]  
  
 <xref:System.Windows.VisualStateManager.GoToState%2A>メソッドは、開始およびストーリーを適切に停止する必要なロジックを実行します。 コントロールを呼び出すと<xref:System.Windows.VisualStateManager.GoToState%2A>の状態を変更する、<xref:System.Windows.VisualStateManager>は次の実行します。  
  
-   場合、<xref:System.Windows.VisualState>にコントロールを移動するが、 <xref:System.Windows.Media.Animation.Storyboard>、ストーリー ボードを開始します。 場合はその後、<xref:System.Windows.VisualState>が、コントロールがから送信されたこと、 <xref:System.Windows.Media.Animation.Storyboard>、ストーリー ボードが終了します。  
  
-   コントロールが指定されている状態で既に場合<xref:System.Windows.VisualStateManager.GoToState%2A>は何も処理し、返します`true`です。  
  
-   指定されている状態が存在しない場合、<xref:System.Windows.Controls.ControlTemplate>の`control`、<xref:System.Windows.VisualStateManager.GoToState%2A>は何も処理し、返します`false`です。  
  
#### <a name="best-practices-for-working-with-the-visualstatemanager"></a>VisualStateManager を操作するためのベスト プラクティス  
 コントロールの状態を維持するために、次を実行することをお勧めします。  
  
-   プロパティを使用すると、その状態を追跡できます。  
  
-   状態の間で移行するヘルパー メソッドを作成します。  
  
 `NumericUpDown`コントロール、`Value`内にあるかどうかを追跡するプロパティ、`Positive`または`Negative`状態です。  `NumericUpDown`コントロールも定義、`Focused`と`UnFocused`状態、どのトラック、<xref:System.Windows.UIElement.IsFocused%2A>プロパティです。 必然的に、コントロールのプロパティに対応していない状態を使用する場合は、状態を追跡するプライベート プロパティを定義できます。  
  
 すべての状態を更新する 1 つのメソッドの呼び出しを集中管理、<xref:System.Windows.VisualStateManager>し管理性に優れたコードを保持します。 次の例は、`NumericUpDown`コントロールのヘルパー メソッド、`UpdateStates`です。 ときに`Value`0 以上、<xref:System.Windows.Controls.Control>では、`Positive`状態です。  ときに`Value`が 0 未満の値、コントロールが、`Negative`状態です。  ときに<xref:System.Windows.UIElement.IsFocused%2A>は`true`、コントロールが、`Focused`状態。 それ以外の場合、それでは、`Unfocused`状態です。  コントロールを呼び出すことができます`UpdateStates`するたびに、どのような状態の変更に関係なく、その状態を変更する必要があります。  
  
 [!code-csharp[VSMCustomControl#UpdateStates](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#updatestates)]
 [!code-vb[VSMCustomControl#UpdateStates](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#updatestates)]  
  
 状態名を渡す場合<xref:System.Windows.VisualStateManager.GoToState%2A>コントロールが既に状態にあるときに<xref:System.Windows.VisualStateManager.GoToState%2A>何もしない、コントロールの現在の状態を確認する必要はありません。  たとえば場合、`Value`別、負の値のストーリー ボードに 1 つの負の値から変更、`Negative`状態は中断されず、ユーザーには、コントロールの変更は表示されません。  
  
 <xref:System.Windows.VisualStateManager>使用<xref:System.Windows.VisualStateGroup>オブジェクトを呼び出すときに終了するには、どの状態を判断<xref:System.Windows.VisualStateManager.GoToState%2A>です。 コントロールがごとに 1 つの状態は常に<xref:System.Windows.VisualStateGroup>で定義されているその<xref:System.Windows.Controls.ControlTemplate>し同じから別の状態になったときにのみ、状態のまま<xref:System.Windows.VisualStateGroup>です。 たとえば、<xref:System.Windows.Controls.ControlTemplate>の`NumericUpDown`制御を定義、`Positive`と`Negative`<xref:System.Windows.VisualState>いずれかのオブジェクト<xref:System.Windows.VisualStateGroup>と`Focused`と`Unfocused`<xref:System.Windows.VisualState>別のオブジェクト。 (表示できます、`Focused`と`Unfocused`<xref:System.Windows.VisualState>で定義されている、[完全な例](#complete_example)からコントロールになると、このトピックのセクションで、`Positive`状態、`Negative`状態、またはその逆、コントロールのいずれかのまま、`Focused`または`Unfocused`状態です。  
  
 コントロールの状態が変わる可能性があります、3 つの一般的な場所があります。  
  
-   ときに、<xref:System.Windows.Controls.ControlTemplate>に適用される、<xref:System.Windows.Controls.Control>です。  
  
-   プロパティが変更されたとき。  
  
-   イベントの発生時です。  
  
 次の例では、更新の状態を示します、`NumericUpDown`このような場合のコントロールです。  
  
 内のコントロールの状態を更新する必要があります、<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>メソッド コントロールが適切に表示されるように状態、<xref:System.Windows.Controls.ControlTemplate>を適用します。 次の例では`UpdateStates`で<xref:System.Windows.FrameworkElement.OnApplyTemplate%2A>コントロールが、適切な状態であることを確認します。  たとえば、作成すること、`NumericUpDown`制御、および設定し、その<xref:System.Windows.Controls.Control.Foreground%2A>緑と`Value`-5 にします。  呼び出さない場合`UpdateStates`ときに、<xref:System.Windows.Controls.ControlTemplate>に適用される、`NumericUpDown`コントロール、コントロールに含まれていない、`Negative`状態と、値が赤ではなく緑です。  呼び出す必要があります`UpdateStates`コントロールを配置する、`Negative`状態です。  
  
 [!code-csharp[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#applytemplate)]
 [!code-vb[VSMCustomControl#ApplyTemplate](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#applytemplate)]  
  
 多くの場合、プロパティが変更されたときにコントロールの状態を更新する必要があります。 次の例は、全体を示しています。`ValueChangedCallback`メソッドです。 `ValueChangedCallback`時に呼び出される`Value`変更されると、このメソッドの呼び出し`UpdateStates`に備えて`Value`負の値またはその逆正の値から変更します。 呼び出すしてもかまいません。`UpdateStates`とき`Value`変更が、その場合は、コントロール状態は変化しないので、正または負の値のままです。  
  
 [!code-csharp[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#entirevaluechangedcallback)]
 [!code-vb[VSMCustomControl#EntireValueChangedCallback](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#entirevaluechangedcallback)]  
  
 また、イベントが発生したときに状態を更新する必要があります。 次の例を`NumericUpDown`呼び出し`UpdateStates`上、<xref:System.Windows.Controls.Control>を処理する、<xref:System.Windows.UIElement.GotFocus>イベント。  
  
 [!code-csharp[VSMCustomControl#OnGotFocus](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#ongotfocus)]
 [!code-vb[VSMCustomControl#OnGotFocus](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#ongotfocus)]  
  
 <xref:System.Windows.VisualStateManager>コントロールの状態を管理するのに役立ちます。 使用して、<xref:System.Windows.VisualStateManager>状態の間、コントロールを正しく遷移ことを確認します。  操作するためには、このセクションで説明した推奨事項に従うかどうか、<xref:System.Windows.VisualStateManager>コントロールのコードは読み取り可能な保守も容易に残ります。  
  
<a name="providing_the_control_contract"></a>   
## <a name="providing-the-control-contract"></a>コントロールのコントラクトを提供します。  
 コントロールのコントラクトを指定するように<xref:System.Windows.Controls.ControlTemplate>作成者、テンプレートに記述する内容がわかります。 コントロール コントラクトには、次の 3 つの要素があります。  
  
-   コントロールのロジックが使用する視覚的要素。  
  
-   コントロールの状態および各状態が所属するグループ。  
  
-   コントロールに対して視覚的に作用するパブリック プロパティ。  
  
 新たに作成できる人<xref:System.Windows.Controls.ControlTemplate>何かを認識する必要がある<xref:System.Windows.FrameworkElement>オブジェクトがコントロールのロジックを使用して、各オブジェクトの種類し、どのような名前がします。 A<xref:System.Windows.Controls.ControlTemplate>作成者もあり、コントロールで使用されることが考えられる各状態の名前を知っている必要があります<xref:System.Windows.VisualStateGroup>です。  
  
 返す、`NumericUpDown`例では、コントロールが必要ですが、<xref:System.Windows.Controls.ControlTemplate>次のものを<xref:System.Windows.FrameworkElement>オブジェクト。  
  
-   A<xref:System.Windows.Controls.Primitives.RepeatButton>と呼ばれる`UpButton`です。  
  
-   A<xref:System.Windows.Controls.Primitives.RepeatButton>と呼ばれる `DownButton.`  
  
 コントロールは、次の状態であることができます。  
  
-   の `ValueStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Positive`  
  
    -   `Negative`  
  
-   の `FocusStates`<xref:System.Windows.VisualStateGroup>  
  
    -   `Focused`  
  
    -   `Unfocused`  
  
 内容を指定する<xref:System.Windows.FrameworkElement>オブジェクト、コントロールが必要ですが、使用する、 <xref:System.Windows.TemplatePartAttribute>、予期された要素の型と名前を指定します。  使用するコントロールの状態を指定する、 <xref:System.Windows.TemplateVisualStateAttribute>、および状態の名前を指定する<xref:System.Windows.VisualStateGroup>に属しています。  Put、<xref:System.Windows.TemplatePartAttribute>と<xref:System.Windows.TemplateVisualStateAttribute>コントロールのクラス定義にします。  
  
 コントロールの外観に影響するパブリック プロパティは、コントロールのコントラクトの一部ではもです。  
  
 次の例を指定します、<xref:System.Windows.FrameworkElement>オブジェクトと状態を`NumericUpDown`コントロール。  
  
 [!code-csharp[VSMCustomControl#ControlContract](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controlcontract)]
 [!code-vb[VSMCustomControl#ControlContract](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controlcontract)]  
  
<a name="complete_example"></a>   
## <a name="complete-example"></a>コード例全体  
 次の例は、全体<xref:System.Windows.Controls.ControlTemplate>の`NumericUpDown`コントロール。  
  
 [!code-xaml[VSMCustomControl#NUDTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/themes/generic.xaml#nudtemplate)]  
  
 次の例は、ロジック、`NumericUpDown`です。  
  
 [!code-csharp[VSMCustomControl#ControlLogic](../../../../samples/snippets/csharp/VS_Snippets_Wpf/vsmcustomcontrol/csharp/numericupdown.cs#controllogic)]
 [!code-vb[VSMCustomControl#ControlLogic](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/vsmcustomcontrol/visualbasic/numericupdown.vb#controllogic)]  
  
## <a name="see-also"></a>関連項目  
 [ControlTemplate の作成による既存のコントロールの外観のカスタマイズ](../../../../docs/framework/wpf/controls/customizing-the-appearance-of-an-existing-control.md)  
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)
