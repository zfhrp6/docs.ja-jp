---
title: コントロールの作成の概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], authoring overview
- authoring overview for controls [WPF]
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
ms.openlocfilehash: a6c2c796819924cdbd15d6eefffe10a607bad9bc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="control-authoring-overview"></a>コントロールの作成の概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コントロール モデルの機能拡張により、新しいコントロールを作成する必要性が大幅に削減されます。 ただし、場合によっては、カスタム コントロールを作成する必要があります。 このトピックでは、カスタム コントロールを作成する必要性を最小限に抑える機能と、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまなコントロール作成モデルについて説明します。 また、新しいコントロールを作成する方法も示します。  
  
 
  
<a name="when_to_write_a_new_control"></a>   
## <a name="alternatives-to-writing-a-new-control"></a>新しいコントロールの作成に代わる方法  
 従来は、既存のコントロールをカスタマイズする場合、背景色、境界線の幅、フォントのサイズなど、コントロールの標準プロパティを変更するなどの範囲に制限されていました。 これらの定義済みのパラメーター以外に、コントロールの外観や動作にまでカスタマイズを拡張しようとすると、通常、既存のコントロールを継承し、コントロールを描画するメソッドをオーバーライドして、新しいコントロールを作成する必要がありました。  その方法は今でも選択できますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の場合、リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用して、既存のコントロールをカスタマイズできます。 新しいコントロールを作成しなくても、これらの機能を使用して、カスタマイズされた一貫性のあるエクスペリエンスを得られる方法としては、次のような例が挙げられます。  
  
-   **リッチ コンテンツ。** 標準の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの多くがリッチ コンテンツをサポートしています。 コンテンツのプロパティなど、<xref:System.Windows.Controls.Button>の種類は<xref:System.Object>、理論に何も表示されることができます、<xref:System.Windows.Controls.Button>です。  イメージを追加するには、イメージとテキストの表示 ボタンと<xref:System.Windows.Controls.TextBlock>を<xref:System.Windows.Controls.StackPanel>を割り当てると、<xref:System.Windows.Controls.StackPanel>を<xref:System.Windows.Controls.ContentControl.Content%2A>プロパティです。 コントロールには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の視覚的要素と任意のデータを表示できるため、複雑な視覚化をサポートするために、新しいコントロールを作成したり、既存のコントロールを変更したりする必要性が少なくなります。 コンテンツ モデルの詳細については<xref:System.Windows.Controls.Button>でその他のコンテンツをモデル化と[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を参照してください[WPF コンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)です。  
  
-   **スタイル** A<xref:System.Windows.Style>コントロールのプロパティを表す値のコレクションです。 スタイルを使用すると、新しいコントロールを作成しなくても、必要なコントロールの外観と動作を備えた再利用可能な表現を作成できます。 たとえば、すべての必要な<xref:System.Windows.Controls.TextBlock>コントロールを 14 文字のフォント サイズ、赤、Arial フォントにします。 そこで、リソースとしてスタイルを作成し、それに応じて、適切なプロパティを設定します。 ごと、<xref:System.Windows.Controls.TextBlock>同じ外観を持つは、アプリケーションに追加することです。  
  
-   **データ テンプレート。** A<xref:System.Windows.DataTemplate>コントロールでデータを表示する方法をカスタマイズすることができます。 たとえば、<xref:System.Windows.DataTemplate>でデータを表示する方法を指定するために使用する、<xref:System.Windows.Controls.ListBox>です。  この例については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。  データの外観のカスタマイズに加え、<xref:System.Windows.DataTemplate>提供する柔軟性のカスタム Ui に UI 要素を含めることができます。  たとえばを使用して、 <xref:System.Windows.DataTemplate>、作成することができます、<xref:System.Windows.Controls.ComboBox>で各項目には、チェック ボックスが含まれています。  
  
-   **コントロール テンプレート。** 多くのコントロールで[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して、<xref:System.Windows.Controls.ControlTemplate>コントロールの構造とコントロールの機能とコントロールの外観を分ける、外観を定義します。 再定義コントロールの外観を変更することができますが大幅にその<xref:System.Windows.Controls.ControlTemplate>です。  たとえば、信号機のような外観のコントロールが必要だとします。 このコントロールのユーザー インターフェイスと機能は単純です。  コントロールは 3 つの円で構成され、一度に点灯するのはそのうちの 1 つだけです。 一部のリフレクションの後に、ことを理解可能性があります、<xref:System.Windows.Controls.RadioButton>の 1 つだけが、時刻の既定の外観で選択されている機能を提供、<xref:System.Windows.Controls.RadioButton>信号のライトを何も表示されないようです。  <xref:System.Windows.Controls.RadioButton>の外観を定義する、コントロール テンプレートを使用して簡単に再定義する、<xref:System.Windows.Controls.ControlTemplate>コントロールの要件に合わせてラジオ ボタンを使用して、信号を作成します。  
  
    > [!NOTE]
    >  ただし、<xref:System.Windows.Controls.RadioButton>を使用できます、 <xref:System.Windows.DataTemplate>、<xref:System.Windows.DataTemplate>この例では十分ではありません。  <xref:System.Windows.DataTemplate>コントロールのコンテンツの外観を定義します。 場合、 <xref:System.Windows.Controls.RadioButton>、コンテンツを表す円の右側に表示されているものかどうか、<xref:System.Windows.Controls.RadioButton>が選択されています。  信号機の例では、オプション ボタンに必要なのは "点灯" する円だけです。 信号機の外観要件はそのための既定の外観と異なるため、 <xref:System.Windows.Controls.RadioButton>、再定義する必要がある、<xref:System.Windows.Controls.ControlTemplate>です。  一般に、<xref:System.Windows.DataTemplate>コントロールとのコンテンツ (またはデータ) を定義するために使用<xref:System.Windows.Controls.ControlTemplate>コントロールを構成する方法を定義するために使用します。  
  
-   **トリガー。** A<xref:System.Windows.Trigger>新しいコントロールを作成することがなく、コントロールの動作と外観を動的に変更することができます。 たとえば、複数<xref:System.Windows.Controls.ListBox>アプリケーションではコントロールの各項目を検索および<xref:System.Windows.Controls.ListBox>は、選択したときに太字と赤であります。 継承するクラスを作成する場合、最初の性質があります<xref:System.Windows.Controls.ListBox>をオーバーライドし、 <xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> 、選択したアイテムがより適切な方法の外観を変更する方法は、トリガーのスタイルを追加する、<xref:System.Windows.Controls.ListBoxItem>の外観を変更します。選択された項目。 トリガーを使用すると、プロパティ値を変更したり、プロパティ値に基づいた処理を実行したりできます。 <xref:System.Windows.EventTrigger>イベントが発生したときにアクションを実行することができます。  
  
 スタイル、テンプレート、トリガーの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
 一般に、既存のコントロールと同じ機能を持ち、外観が異なるコントロールが必要な場合は、このセクションで説明した方法のいずれかを使用して、既存のコントロールの外観を変更できないかどうかをまず検討することをお勧めします。  
  
<a name="models_for_control_authoring"></a>   
## <a name="models-for-control-authoring"></a>コントロール作成モデル  
 リッチ コンテンツ モデル、スタイル、テンプレート、トリガーを使用すると、新しいコントロールを作成する必要性が最小限に抑えられます。 ただし、新しいコントロールを作成する必要がある場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の各種のコントロール作成モデルを理解することが重要です。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、コントロールを作成するための一般的なモデルが 3 つあり、各モデルはそれぞれ異なる機能と柔軟性レベルを備えています。 基本クラスは、3 つのモデル<xref:System.Windows.Controls.UserControl>、 <xref:System.Windows.Controls.Control>、および<xref:System.Windows.FrameworkElement>です。  
  
### <a name="deriving-from-usercontrol"></a>UserControl からの派生  
 最も簡単な方法でコントロールを作成する[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]から派生するは<xref:System.Windows.Controls.UserControl>します。 継承されるコントロールをビルドすると<xref:System.Windows.Controls.UserControl>に既存のコンポーネントを追加する、<xref:System.Windows.Controls.UserControl>内のイベント ハンドラーを参照し、コンポーネントを名前[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]です。 次に、指定の要素を参照し、コードでイベント ハンドラーを定義します。 この開発モデルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのアプリケーション開発に使用されるモデルとよく似ています。  
  
 正しく構成されている場合、<xref:System.Windows.Controls.UserControl>豊富なコンテンツ、スタイル、およびトリガーの利点を活用がかかることができます。 ただし、コントロールから継承している場合<xref:System.Windows.Controls.UserControl>、コントロールを使用するユーザーは使用できません、<xref:System.Windows.DataTemplate>または<xref:System.Windows.Controls.ControlTemplate>その外観をカスタマイズします。  派生する必要がある、<xref:System.Windows.Controls.Control>クラスまたはその派生クラスのいずれか (以外の<xref:System.Windows.Controls.UserControl>) テンプレートをサポートするカスタム コントロールを作成します。  
  
#### <a name="benefits-of-deriving-from-usercontrol"></a>UserControl からの派生の利点  
 派生することを検討してください<xref:System.Windows.Controls.UserControl>次のすべてに該当する場合。  
  
-   アプリケーションの構築と同じ方法でコントロールをビルドする必要がある場合。  
  
-   コントロールが既存のコンポーネントのみで構成されている場合。  
  
-   複雑なカスタマイズをサポートする必要がない場合。  
  
### <a name="deriving-from-control"></a>Control からの派生  
 派生する、<xref:System.Windows.Controls.Control>クラスは、既存のほとんどで使用されるモデル[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]コントロール。 継承するコントロールを作成する場合、<xref:System.Windows.Controls.Control>クラス テンプレートを使用して、外観を定義します。 これにより、操作ロジックと視覚的表現とが分離されます。 イベントと回避の参照要素ではなくコマンドとバインディングを使用して、ロジックと UI の分離を確認できますも、<xref:System.Windows.Controls.ControlTemplate>可能な場合です。  コントロールのユーザーがコントロールの再定義できます、コントロールのロジックと UI が適切に分離された場合は、<xref:System.Windows.Controls.ControlTemplate>その外観をカスタマイズします。 カスタムのビルドが<xref:System.Windows.Controls.Control>ビルドだけでは、 <xref:System.Windows.Controls.UserControl>、カスタム<xref:System.Windows.Controls.Control>に最大限の柔軟性を提供します。  
  
#### <a name="benefits-of-deriving-from-control"></a>Control からの派生の利点  
 派生することを検討してください<xref:System.Windows.Controls.Control>を使用せずに、<xref:System.Windows.Controls.UserControl>クラスの次のいずれかの場合。  
  
-   使用してカスタマイズできるように、コントロールの外観をする、<xref:System.Windows.Controls.ControlTemplate>です。  
  
-   コントロールがさまざまなテーマをサポートする必要がある場合。  
  
### <a name="deriving-from-frameworkelement"></a>FrameworkElement からの派生  
 派生したコントロール<xref:System.Windows.Controls.UserControl>または<xref:System.Windows.Controls.Control>既存の要素の作成に依存します。 多くのシナリオでは、これは、適切な解決のためから継承する任意のオブジェクト<xref:System.Windows.FrameworkElement>にすることができます、<xref:System.Windows.Controls.ControlTemplate>です。 しかし、場合によっては、単純な要素コンポジションでは、コントロールの外観に必要な機能を実現できないことがあります。 このようなシナリオに基づいて、コンポーネント<xref:System.Windows.FrameworkElement>最適な選択肢です。  
  
 構築するための 2 つの標準的な方法がある<xref:System.Windows.FrameworkElement>-コンポーネントをベース: レンダリングとカスタム要素のコンポジションをダイレクトします。 直接レンダリングでは、オーバーライドでは、<xref:System.Windows.UIElement.OnRender%2A>メソッドの<xref:System.Windows.FrameworkElement>を提供する<xref:System.Windows.Media.DrawingContext>コンポーネント ビジュアルを明示的に定義する操作。 これで使用されるメソッド<xref:System.Windows.Controls.Image>と<xref:System.Windows.Controls.Border>です。 カスタム要素の合成では、型のオブジェクトを使用して<xref:System.Windows.Media.Visual>コンポーネントの外観を構成します。 例については、「[DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。 <xref:System.Windows.Controls.Primitives.Track> 内のコントロールの例は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]カスタム要素コンポジションを使用します。 同じコントロールでダイレクト レンダリングとカスタム要素コンポジションを混在させることもできます。  
  
#### <a name="benefits-of-deriving-from-frameworkelement"></a>FrameworkElement からの派生の利点  
 派生することを検討してください<xref:System.Windows.FrameworkElement>以下のいずれかの場合。  
  
-   コントロールの外観について、単純な要素コンポジションが提供する以上の厳密な制御を必要とする場合。  
  
-   独自のレンダリング ロジックを定義して、コントロールの外観を定義する必要がある場合。  
  
-   何ができる以外にも斬新な方法で既存の要素を構成する<xref:System.Windows.Controls.UserControl>と<xref:System.Windows.Controls.Control>です。  
  
<a name="control_authoring_basics"></a>   
## <a name="control-authoring-basics"></a>コントロール作成の基本  
 既に説明したように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の最も強力な機能の 1 つは、コントロールの基本的なプロパティ設定だけでは不可能な外観や動作の変更を実現し、しかもカスタム コントロールを作成する必要がないということです。 スタイル設定、データ バインディング、トリガーの各機能は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント システムによって実現されています。 以降のセクションでは、カスタム コントロールのユーザーが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属のコントロールと同じように、これらの機能を使用できるようにするために、カスタム コントロールの作成に使用するモデルに関係なく、従う必要があるプラクティスについて説明します。  
  
### <a name="use-dependency-properties"></a>依存関係プロパティの使用  
 プロパティが依存関係プロパティである場合、以下の操作が可能です。  
  
-   スタイルのプロパティを設定する。  
  
-   プロパティをデータ ソースにバインドする。  
  
-   プロパティの値として、動的リソースを使用する。  
  
-   プロパティ名をアニメーション化する。  
  
 コントロールのプロパティがこれらの機能のいずれかをサポートす必要がある場合、それを依存関係プロパティとして実装する必要があります。 次の例では、以下の処理を実行して、`Value` という名前の依存関係プロパティを定義します。  
  
-   定義、<xref:System.Windows.DependencyProperty>という名前の識別子`ValueProperty`として、 `public` `static` `readonly`フィールドです。  
  
-   プロパティ名をシステムに登録、プロパティ、呼び出すことによって<xref:System.Windows.DependencyProperty.Register%2A?displayProperty=nameWithType>を次を指定する。  
  
    -   プロパティの名前。  
  
    -   プロパティの型。  
  
    -   プロパティを所有する型。  
  
    -   プロパティのメタデータ。 メタデータにはプロパティの既定値が含まれています、<xref:System.Windows.CoerceValueCallback>と<xref:System.Windows.PropertyChangedCallback>です。  
  
-   プロパティの `get` アクセサーと `set` アクセサーを実装することにより、依存関係プロパティの登録名と同じ `Value` という名前で [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ラッパー プロパティを定義します。 なお、`get`と`set`アクセサーだけを呼び出す<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>それぞれします。 依存関係プロパティのアクセサーでは、含まれていないことの追加ロジックためにお勧めクライアントと[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アクセサーと呼び出しをバイパスできます<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>直接です。 たとえば、プロパティがデータ ソースにバインドされている場合、プロパティの `set` アクセサーは呼び出されません。  Get に対する追加のロジックを追加する代わりに、set アクセサーは、使用、 <xref:System.Windows.ValidateValueCallback>、<xref:System.Windows.CoerceValueCallback>と<xref:System.Windows.PropertyChangedCallback>デリゲートに応答したり、変更するときに値を確認します。  これらのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
-   メソッドを定義する、<xref:System.Windows.CoerceValueCallback>という`CoerceValue`です。 `CoerceValue` によって、`Value` は `MinValue` 以上で `MaxValue` 以下になります。  
  
-   メソッドを定義する、 <xref:System.Windows.PropertyChangedCallback>、名前付き`OnValueChanged`します。 `OnValueChanged` 作成、<xref:System.Windows.RoutedPropertyChangedEventArgs%601>オブジェクトを発生させる準備、`ValueChanged`ルーティングされたイベント。 ルーティング イベントについては、次のセクションで説明します。  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
### <a name="use-routed-events"></a>ルーティング イベントの使用  
 依存関係プロパティが [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティの概念を追加機能によって拡張するのと同様に、ルーティング イベントは、標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントの概念を拡張します。 新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロール作成する場合、イベントをルーティング イベントとして実装することをお勧めします。ルーティング イベントは以下の機能をサポートしているためです。  
  
-   複数のコントロールの親でイベントを処理できます。 イベントがバブル イベントの場合、要素ツリー内の単一の親はイベントをサブスクライブできます。 これにより、アプリケーション開発者は、複数のコントロールのイベントに 1 つのハンドラーで対応できます。 たとえば、コントロール内の各項目の一部である場合、 <xref:System.Windows.Controls.ListBox> (に含まれているため、 <xref:System.Windows.DataTemplate>)、アプリケーション開発者に、コントロールのイベントのイベント ハンドラーを定義できます、<xref:System.Windows.Controls.ListBox>です。 いずれかのコントロールでイベントが発生するたびに、そのイベント ハンドラーが呼び出されます。  
  
-   ルーティング イベントを使用して、 <xref:System.Windows.EventSetter>、アプリケーション開発者は、スタイル内のイベントのハンドラーを指定できます。  
  
-   ルーティング イベントを使用して、 <xref:System.Windows.EventTrigger>、これを使用してプロパティをアニメーション化するのに便利[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]です。 詳しくは、「 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」をご覧ください。  
  
 次に示す例では、以下の処理を実行して、ルーティング イベントを定義します。  
  
-   定義、<xref:System.Windows.RoutedEvent>という名前の識別子`ValueChangedEvent`として、 `public` `static` `readonly`フィールドです。  
  
-   ルーティング イベントを呼び出すことで登録、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=nameWithType>メソッドです。 この例を呼び出すときに、次の情報を指定します<xref:System.Windows.EventManager.RegisterRoutedEvent%2A>:  
  
    -   イベントの名前が `ValueChanged` であること。  
  
    -   ルーティングの戦略は<xref:System.Windows.RoutingStrategy.Bubble>ソース (イベントを発生させるオブジェクト) でイベント ハンドラーが最初に、呼び出されることを意味して、以降に最も近いイベント ハンドラーで連続してソースの親要素のイベント ハンドラーが呼び出されますし、親要素です。  
  
    -   イベント ハンドラーの種類は<xref:System.Windows.RoutedPropertyChangedEventHandler%601>で構築された、<xref:System.Decimal>型です。  
  
    -   イベントを所有する型が `NumericUpDown` であること。  
  
-   `ValueChanged` という名前のパブリック イベントを宣言し、イベント アクセサー宣言を含めます。 呼び出しの例<xref:System.Windows.UIElement.AddHandler%2A>で、`add`アクセサーの宣言と<xref:System.Windows.UIElement.RemoveHandler%2A>で、`remove`アクセサーの宣言を使用する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]イベント サービス。  
  
-   `ValueChanged`イベントを発生させる、保護された仮想メソッド `OnValueChanged` を作成します。  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」および「[カスタム ルーティング イベントを作成する](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)」を参照してください。  
  
### <a name="use-binding"></a>バインディングの使用  
 コントロールの UI とロジックを分離するには、データ バインディングを使用する方法もあります。 これを使用して、コントロールの外観を定義する場合に特に重要な<xref:System.Windows.Controls.ControlTemplate>します。 データ バインディングを使用すると、コードから UI の特定の部分を参照する必要性がなくなる場合があります。 含まれる要素の参照を回避することをお勧め、<xref:System.Windows.Controls.ControlTemplate>ときに、コードが内にある要素を参照しているため、<xref:System.Windows.Controls.ControlTemplate>と<xref:System.Windows.Controls.ControlTemplate>変更されると、新たに含まれる参照される要素のニーズ<xref:System.Windows.Controls.ControlTemplate>です。  
  
 次の例の更新プログラム、<xref:System.Windows.Controls.TextBlock>の`NumericUpDown`コントロールにその名前を割り当てると、コード内の名前で、テキスト ボックスを参照します。  
  
 [!code-xaml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 次の例では、バインディングを使用して同じことを実現しています。  
  
 [!code-xaml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 データ バインディングの詳細については、「[データ バインディングの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
### <a name="design-for-designers"></a>デザイナーに対応したデザイン  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] でカスタム WPF コントロールのサポート (たとえば、[プロパティ] ウィンドウでのプロパティ編集) を利用するには、以下のガイドラインに従います。  [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] 向けの開発の詳細については、「[WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)」を参照してください。  
  
#### <a name="dependency-properties"></a>依存関係プロパティ  
 「依存関係プロパティの使用」で説明したように、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の `get` アクセサーと `set` アクセサーを実装します。 デザイナーは、ラッパーを使用して依存関係プロパティの存在を検出する場合がありますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] およびコントロールのクライアントと同様、プロパティを取得または設定するときにアクセサーを呼び出す必要はありません。  
  
#### <a name="attached-properties"></a>アタッチされるプロパティ  
 以下のガイドラインに従って、カスタム コントロールに添付プロパティを実装する必要があります。  
  
-   `public` `static` `readonly` <xref:System.Windows.DependencyProperty>フォームの*PropertyName* `Property`を使用して作成された、<xref:System.Windows.DependencyProperty.RegisterAttached%2A>メソッドです。 渡されるプロパティ名<xref:System.Windows.DependencyProperty.RegisterAttached%2A>と一致する必要があります*PropertyName*です。  
  
-   `Set` *PropertyName* および `Get` *PropertyName* という名前の `public``static` CLR メソッドのペアを実装します。 どちらの方法はから派生するクラスを受け入れる必要があります<xref:System.Windows.DependencyProperty>の最初の引数として。 また、`Set` *PropertyName* メソッドでは、プロパティの登録データ型と同じ型の引数も受け取ります。 `Get` *PropertyName*メソッドでは、同じ型の値を返す必要があります。 `Set` *PropertyName*メソッドがない場合、プロパティは読み取り専用としてマークされます。  
  
-   `Set` *PropertyName*と`Get` *PropertyName*に直接ルーティングする必要があります、<xref:System.Windows.DependencyObject.GetValue%2A>と<xref:System.Windows.DependencyObject.SetValue%2A>オブジェクトのメソッド、対象の依存関係に、それぞれします。 デザイナーが添付プロパティにアクセスするには、メソッド ラッパー経由で呼び出す場合もあれば、対象の依存関係オブジェクトを直接呼び出す場合もあります。  
  
 添付プロパティの詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
### <a name="define-and-use-shared-resources"></a>共有リソースの定義と使用  
 アプリケーションと同じアセンブリにコントロールを含めることも、複数のアプリケーションが使用できる別のアセンブリにコントロールをパッケージ化することもできます。 このトピックで説明した情報の大部分は、使用する方法に関係なく適用されます。  ただし、1 つだけ例外があります。  アプリケーションと同じアセンブリ内にコントロールを配置する場合、App.xaml ファイルにグローバル リソースを自由に追加できます。 コントロールのみを含むアセンブリがありませんが、<xref:System.Windows.Application>オブジェクトに関連付けられている、App.xaml ファイルが使用できないようにします。  
  
 アプリケーションがリソースを検索するときは、次に示す順序で 3 つのレベルを検索します。  
  
1.  要素レベル。  
  
     システムは、リソースを参照する要素から検索を開始し、ルート要素に到達するまで、論理上の親のリソースの検索を継続します。  
  
2.  アプリケーション レベル。  
  
     定義されているリソース、<xref:System.Windows.Application>オブジェクト。  
  
3.  テーマ レベル。  
  
     テーマ レベルのディクショナリは、Themes という名前のサブフォルダーに格納されています。  Themes フォルダー内のファイルはテーマに対応しています。  たとえば、Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml などのファイルがあります。  generic.xaml という名前のファイルが含まれている場合もあります。  システムがテーマ レベルでリソースを検索するとき、最初にテーマ固有のファイル内を検索し、次に generic.xaml 内を検索します。  
  
 アプリケーションとは別のアセンブリ内にコントロールを含めるときは、グローバル リソースを要素レベルまたはテーマ レベルに配置する必要があります。 どちらに配置する場合も、それぞれの利点があります。  
  
#### <a name="defining-resources-at-the-element-level"></a>要素レベルでのリソース定義  
 カスタムのリソース ディクショナリを作成し、それをコントロールのリソース ディクショナリと結合することによって、共有リソースを要素レベルで定義できます。  このメソッドで定義する場合は、リソース ファイルに任意の名前を付けて、コントロールと同じフォルダーに配置できます。 要素レベルでのリソースでは、単純な文字列をキーとして使用することもできます。 次の例を作成、 <xref:System.Windows.Media.LinearGradientBrush> Dictionary1.xaml をという名前のリソース ファイル。  
  
 [!code-xaml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 ディクショナリを定義したら、それをコントロールのリソース ディクショナリにマージする必要があります。  これには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードを使用します。  
  
 次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してリソース ディクショナリを結合します。  
  
 [!code-xaml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 この方法の欠点は、<xref:System.Windows.ResourceDictionary>オブジェクトが参照するたびに作成します。  たとえば、10 のカスタム コントロールをライブラリにある XAML を使用して各コントロールの共有リソース ディクショナリをマージしていてする 10 個まで作成と同じ<xref:System.Windows.ResourceDictionary>オブジェクト。  コード内のリソースを結合して、その結果を返す静的クラスを作成することでこの問題を回避できます<xref:System.Windows.ResourceDictionary>です。  
  
 次の例は、共有を表すクラスを作成<xref:System.Windows.ResourceDictionary>です。  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 次の例では、`InitializeComponent` を呼び出す前に、共有リソースをコントロールのコンス トラクター内でカスタム コントロールのリソースと結合します。  `SharedDictionaryManager.SharedDictionary`静的プロパティ、<xref:System.Windows.ResourceDictionary>が 1 回だけ作成します。 `InitializeComponent` が呼び出される前に、リソース ディクショナリが結合されため、コントロールは [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイル内でリソースを使用できます。  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### <a name="defining-resources-at-the-theme-level"></a>テーマ レベルでのリソース定義  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、さまざまな Windows テーマ用にリソースを作成できます。  コントロールの作成者は、特定のテーマ用のリソースを定義して、使用するテーマに応じてコントロールの外観を変更できます。 などの外観、 <xref:System.Windows.Controls.Button> Windows クラシックのテーマ (Windows 2000 の既定のテーマ) とは異なります、 <xref:System.Windows.Controls.Button> Windows Luna テーマ (Windows XP の既定のテーマ) のため、<xref:System.Windows.Controls.Button>別使用<xref:System.Windows.Controls.ControlTemplate>各テーマ。  
  
 テーマ固有のリソースは、固有のファイル名でリソース ディクショナリに保持されます。 これらのファイルは、コントロールが格納されているフォルダーのサブフォルダーである `Themes` フォルダー内に配置する必要があります。 次の表は、リソース ディクショナリ ファイルと、各ファイルに関連付けられているテーマを示しています。  
  
|リソース ディクショナリ ファイル名|Windows テーマ|  
|-----------------------------------|-------------------|  
|`Classic.xaml`|Windows XP のクラシックな Windows 9x/2000 の外観|  
|`Luna.NormalColor.xaml`|Windows XP の既定の青のテーマ|  
|`Luna.Homestead.xaml`|Windows XP のオリーブのテーマ|  
|`Luna.Metallic.xaml`|Windows XP のシルバーのテーマ|  
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition の既定テーマ|  
|`Aero.NormalColor.xaml`|Windows Vista の既定テーマ|  
  
 すべてのテーマのリソースを定義する必要はありません。 特定のテーマについてリソースが定義されていない場合、コントロールはリソースの `Classic.xaml` を確認します。 現在のテーマに対応するファイルや `Classic.xaml` でリソースが定義されていない場合、コントロールは汎用のリソースを使用します。汎用のリソースは、`generic.xaml` という名前のリソース ディクショナリ ファイルにあります。  `generic.xaml` ファイルは、テーマ固有のリソース ディクショナリ ファイルと同じフォルダーに配置されています。 `generic.xaml` は、特定の Windows テーマには対応していませんが、テーマ レベルのディクショナリであることに変わりありません。  
  
 [テーマおよび UI オートメーションがサポートされた NumericUpDown カスタム コントロールのサンプル](http://go.microsoft.com/fwlink/?LinkID=160025)には、`NumericUpDown` コントロール用の 2 つのリソース ディクショナリが含まれています。1 つは generic.xaml で、もう 1 つは Luna.NormalColor.xaml です。  アプリケーションを実行し、Windows XP のシルバーのテーマと別のテーマを切り替えて、2 つのコントロール テンプレートの違いを確認できます。 (Windows Vista を使用している場合は、Luna.NormalColor.xaml を Aero.NormalColor.xaml という名前に変更し、Windows クラシック テーマと Windows Vista の既定のテーマなど、2 つのテーマを切り替えることができます)。  
  
 配置すると、<xref:System.Windows.Controls.ControlTemplate>テーマ固有のリソース ディクショナリ ファイルのいずれかを制御および呼び出しのための静的コンス トラクターを作成する必要があります、<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29>メソッドを<xref:System.Windows.FrameworkElement.DefaultStyleKey%2A>の次の例に示すようにします。  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### <a name="defining-and-referencing-keys-for-theme-resources"></a>テーマ リソース用のキーの定義と参照  
 要素レベルでリソースを定義するときに、文字列をキーとして割り当て、その文字列を使用してリソースにアクセスできます。 テーマのレベルでリソースを定義するときに行う必要があります、<xref:System.Windows.ComponentResourceKey>キーとして。  次の例では、generic.xaml でリソースを定義します。  
  
 [!code-xaml[ThemeResourcesControlLibrary#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/Themes/generic.xaml#5)]  
  
 次の例では、リソースを参照を指定して、<xref:System.Windows.ComponentResourceKey>キーとして。  
  
 [!code-xaml[ThemeResourcesControlLibrary#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ThemeResourcesControlLibrary/CS/NumericUpDown.xaml#6)]  
  
##### <a name="specifying-the-location-of-theme-resources"></a>テーマ リソースの場所の指定  
 コントロールのリソースを見つけるには、アセンブリにコントロール固有のリソースが含まれていることを、ホスト アプリケーションが認識する必要があります。 追加することによって行うことができます、<xref:System.Windows.ThemeInfoAttribute>コントロールが含まれているアセンブリにします。 <xref:System.Windows.ThemeInfoAttribute>が、<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>汎用のリソースの場所を指定するプロパティと<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>テーマ固有のリソースの場所を指定するプロパティです。  
  
 次の例のセット、<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A>と<xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A>プロパティ<xref:System.Windows.ResourceDictionaryLocation.SourceAssembly>、汎用的なテーマ固有のリソースが、コントロールと同じアセンブリであるを指定します。  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## <a name="see-also"></a>関連項目  
 [WPF デザイナー](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)  
 [WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)  
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)
