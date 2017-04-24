---
title: "コントロールの作成の概要 | Microsoft Docs"
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
  - "作成の概要 (コントロールの)"
  - "コントロール, 作成の概要"
ms.assetid: 3d864748-cff0-4e63-9b23-d8e5a635b28f
caps.latest.revision: 32
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 29
---
# コントロールの作成の概要
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] コントロール モデルの機能拡張により、新しいコントロールを作成する必要性が大幅に削減されます。  ただし、場合によっては、カスタム コントロールを作成する必要があります。  ここでは、カスタム コントロールを作成する必要性を最小限に抑える機能と、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のさまざまなコントロール作成モデルについて説明します。  また、新しいコントロールを作成する方法も示します。  
  
   
  
<a name="when_to_write_a_new_control"></a>   
## 新しいコントロールを作成しないための方法  
 従来、カスタマイズの内容を既存のコントロールから取得する場合は、背景色、境界線の幅、フォントのサイズなど、コントロールの標準プロパティの変更は制限されていました。  このような定義済みのパラメーター以外の部分について、コントロールの外観や動作を拡張するには、新しいコントロールを作成する必要があり、一般的には、既存のコントロールを継承し、コントロールの描画を行うメソッドをオーバーライドしていました。  その方法は現在でも使用できますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、リッチ コンテンツ モデル、スタイル、テンプレート、およびトリガーを使用して、既存のコントロールをカスタマイズすることもできます。  これらの機能を使用して、新しいコントロールを作成せずにカスタム操作および一貫した操作を実現する方法には、次のようなものがあります。  
  
-   **リッチ コンテンツ。**標準の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの多くは、リッチ コンテンツをサポートします。  たとえば、<xref:System.Windows.Controls.Button> のコンテンツ プロパティは <xref:System.Object> 型なので、理論的には、<xref:System.Windows.Controls.Button> 上にはどのようなものでも表示できます。  ボタンにイメージとテキストを表示するには、イメージと <xref:System.Windows.Controls.TextBlock> を <xref:System.Windows.Controls.StackPanel> に追加し、その <xref:System.Windows.Controls.StackPanel> を <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティに設定します。  コントロールには、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のビジュアル要素と任意のデータを表示できるため、新しいコントロールを作成する必要性や、複雑な視覚化をサポートするために既存のコントロールを変更する必要性は少なくなります。  <xref:System.Windows.Controls.Button> のコンテンツ モデルおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のその他のコンテンツ モデルの詳細については、「[WPF のコンテンツ モデル](../../../../docs/framework/wpf/controls/wpf-content-model.md)」を参照してください。  
  
-   **スタイル。** <xref:System.Windows.Style> は、コントロールのプロパティを表す値のコレクションです。  スタイルを使用して、新しいコントロールを作成することなく、目的のコントロールの外観や動作の再利用可能な表現を作成できます。  たとえば、すべての <xref:System.Windows.Controls.TextBlock> コントロールに、赤色でフォント サイズ 14 の Arial フォントを設定するとします。  その場合、スタイルをリソースとして作成し、該当する適切なプロパティを設定します。  すると、アプリケーションに追加する各 <xref:System.Windows.Controls.TextBlock> は同じ外観となります。  
  
-   **データ テンプレート。** <xref:System.Windows.DataTemplate> を使用すると、コントロールでのデータの表示方法をカスタマイズできます。  たとえば、<xref:System.Windows.DataTemplate> を使用して、<xref:System.Windows.Controls.ListBox> でのデータの表示方法を指定できます。  この例については、「[データ テンプレートの概要](../../../../docs/framework/wpf/data/data-templating-overview.md)」を参照してください。  <xref:System.Windows.DataTemplate> では、データの表示形式のカスタマイズのほか、UI 要素を含めることができ、カスタム UI の柔軟性を高めることができます。  たとえば、<xref:System.Windows.DataTemplate> を使用して、各項目がチェック ボックスを持つ <xref:System.Windows.Controls.ComboBox> を作成できます。  
  
-   **コントロール テンプレート。** [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の多くのコントロールでは、<xref:System.Windows.Controls.ControlTemplate> を使用してコントロールの構造と外観を定義します。これにより、コントロールの外観と機能を分離できます。コントロールの <xref:System.Windows.Controls.ControlTemplate> を再定義すると、外観を大きく変えることができます。  たとえば、信号機のような外観のコントロールが必要だとします。  このコントロールのユーザー インターフェイスと機能は単純です。  このコントロールは 3 つの円で構成され、1 度に点灯するのはそのうちの 1 つだけです。  これを実現する方法をしばらく考えた結果、一度に 1 つだけを選択するという機能は <xref:System.Windows.Controls.RadioButton> で実現できることに気付いたとします。しかし、<xref:System.Windows.Controls.RadioButton> の既定の外観は、信号機とは似ても似付きません。  <xref:System.Windows.Controls.RadioButton> では、外観の定義にコントロール テンプレートを使用しているため、コントロールの要件に合わせて <xref:System.Windows.Controls.ControlTemplate> を簡単に再定義でき、オプション ボタンで信号機を実現できます。  
  
    > [!NOTE]
    >  <xref:System.Windows.Controls.RadioButton> では <xref:System.Windows.DataTemplate> を使用できますが、この例は <xref:System.Windows.DataTemplate> では不十分です。  <xref:System.Windows.DataTemplate> は、コントロールのコンテンツの表示形式を定義するものです。  <xref:System.Windows.Controls.RadioButton> の場合、コンテンツとは、<xref:System.Windows.Controls.RadioButton> が選択されているかどうかを示す円の右側に表示される内容です。  信号機の例では、オプション ボタンは、"点灯" する円のみであることが必要です。信号機の場合、外観の要件が、<xref:System.Windows.Controls.RadioButton> の既定の外観とは大きく異なるため、<xref:System.Windows.Controls.ControlTemplate> を再定義する必要があります。  一般には、コントロールのコンテンツ \(またはデータ\) の定義には <xref:System.Windows.DataTemplate> を使用し、コントロールの構造の定義には <xref:System.Windows.Controls.ControlTemplate> を使用します。  
  
-   **トリガー。** <xref:System.Windows.Trigger> を使用すると、新しいコントロールを作成しなくても、コントロールの外観や動作を動的に変更できます。  たとえば、複数の <xref:System.Windows.Controls.ListBox> コントロールを使用するアプリケーションがあり、各 <xref:System.Windows.Controls.ListBox> の選択項目を赤色の太字で表示するとします。  すぐに思い付くのは、<xref:System.Windows.Controls.ListBox> を継承したクラスを作成し、<xref:System.Windows.Controls.Primitives.Selector.OnSelectionChanged%2A> メソッドをオーバーライドして選択項目の外観を変更するという方法ですが、<xref:System.Windows.Controls.ListBoxItem> のスタイルに、選択項目の外観を変更するトリガーを追加するという方法の方がより適切です。  トリガーを使用すると、プロパティ値の変更や、プロパティ値に基づいた処理を実行できます。  <xref:System.Windows.EventTrigger> により、イベントが発生したときに処理を実行できます。  
  
 スタイル、テンプレート、およびトリガーの詳細については、「[スタイルとテンプレート](../../../../docs/framework/wpf/controls/styling-and-templating.md)」を参照してください。  
  
 一般に、既存のコントロールと同じ機能を持ち外観が異なるコントロールが必要な場合は、このセクションで説明した方法のいずれかを使用して既存のコントロールの外観を変更できないかどうかをまず検討することをお勧めします。  
  
<a name="models_for_control_authoring"></a>   
## コントロール作成モデル  
 リッチ コンテンツ モデル、スタイル、テンプレート、およびトリガーを使用すると、新しいコントロールを作成する必要性は大幅に抑えられます。  ただし、場合によっては、新しいコントロールを作成する必要があります。その場合は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の各種のコントロール作成モデルを理解することが重要です。[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、コントロールを作成するための一般的なモデルが 3 つあり、各モデルがそれぞれ異なる機能と柔軟性レベルを持ちます。  3 つのモデルの基本クラスは、<xref:System.Windows.Controls.UserControl>、<xref:System.Windows.Controls.Control>、および <xref:System.Windows.FrameworkElement> です。  
  
### UserControl からの派生  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でコントロールを作成する方法で最も簡単なのは、<xref:System.Windows.Controls.UserControl> を派生する方法です。  <xref:System.Windows.Controls.UserControl> を継承したコントロールを作成するときには、<xref:System.Windows.Controls.UserControl> に既存のコンポーネントを追加し、コンポーネントに名前を付けて、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] でイベント ハンドラーを参照します。  次に、指定の要素を参照し、コードでイベント ハンドラーを定義します。  この開発モデルは、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] でのアプリケーション開発に使用されるモデルと非常によく似ています。  
  
 <xref:System.Windows.Controls.UserControl> は、正しく構築されていれば、リッチ コンテンツ、スタイル、およびトリガーの利点を活用できます。  しかし、<xref:System.Windows.Controls.UserControl> を継承したコントロールの場合、そのユーザーは、<xref:System.Windows.DataTemplate> や <xref:System.Windows.Controls.ControlTemplate> を使用して外観をカスタマイズできません。  <xref:System.Windows.Controls.Control> クラスまたはその派生クラス \(<xref:System.Windows.Controls.UserControl> を除く\) を派生して、テンプレートをサポートするカスタム コントロールを作成する必要があります。  
  
#### UserControl からの派生の利点  
 次のすべての項目に該当する場合は、<xref:System.Windows.Controls.UserControl> から派生することをお勧めします。  
  
-   アプリケーションの構築と同じ方法でコントロールを構築する必要がある場合。  
  
-   コントロールが既存のコンポーネントだけで構成されている場合。  
  
-   複雑なカスタマイズをサポートする必要がない場合。  
  
### Control からの派生  
 <xref:System.Windows.Controls.Control> クラスからの派生は、既存の [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールの多くで使用されるモデルです。  <xref:System.Windows.Controls.Control> クラスを継承したコントロールを作成するときには、テンプレートを使用してその外観を定義します。  それにより、操作ロジックと視覚的表現とが分離されます。  また、イベントではなくコマンドとバインディングを使用し、<xref:System.Windows.Controls.ControlTemplate> の要素の参照をできる限り避けることによって、UI とロジックを分離できます。コントロールの UI とロジックが適切に分離されていると、コントロールのユーザーがコントロールの <xref:System.Windows.Controls.ControlTemplate> を再定義して、その外観をカスタマイズできます。カスタム <xref:System.Windows.Controls.Control> の作成は <xref:System.Windows.Controls.UserControl> の作成ほど単純ではありませんが、カスタム <xref:System.Windows.Controls.Control> では高い柔軟性を得ることができます。  
  
#### Control からの派生の利点  
 次のいずれかの項目に該当する場合は、<xref:System.Windows.Controls.UserControl> クラスを使用するのではなく、<xref:System.Windows.Controls.Control> から派生することをお勧めします。  
  
-   コントロールの外観を、<xref:System.Windows.Controls.ControlTemplate> によりカスタマイズ可能にする必要がある場合。  
  
-   コントロールでさまざまなテーマをサポートする必要がある場合。  
  
### FrameworkElement からの派生  
 <xref:System.Windows.Controls.UserControl> または <xref:System.Windows.Controls.Control> から派生するコントロールは、既存の要素の構成に依存します。  多くの状況では、それで問題ありません。<xref:System.Windows.FrameworkElement> を継承するどのオブジェクトも <xref:System.Windows.Controls.ControlTemplate> に含めることができるためです。  しかし、場合によっては、単純な要素コンポジションでは、コントロールの外観で求められる機能を実現できないことがあります。  このような状況では、<xref:System.Windows.FrameworkElement> に基づいてコンポーネントを作成するのが適切な選択です。  
  
 <xref:System.Windows.FrameworkElement> に基づくコンポーネントを構築するには、ダイレクト レンダリングとカスタム要素コンポジションの 2 つの標準的な方法があります。  ダイレクト レンダリングでは、<xref:System.Windows.FrameworkElement> の <xref:System.Windows.UIElement.OnRender%2A> メソッドをオーバーライドし、コンポーネントのビジュアルを明示的に定義する <xref:System.Windows.Media.DrawingContext> 操作を提供します。  これは、<xref:System.Windows.Controls.Image> および <xref:System.Windows.Controls.Border> で使用される方法です。  カスタム要素コンポジションでは、<xref:System.Windows.Media.Visual> 型のオブジェクトを使用してコンポーネントの外観を構成します。  例については、「[DrawingVisual オブジェクトの使用](../../../../docs/framework/wpf/graphics-multimedia/using-drawingvisual-objects.md)」を参照してください。  たとえば、カスタム要素コンポジションを使用する [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] のコントロールとして、<xref:System.Windows.Controls.Primitives.Track> があります。  また、同じコントロールでダイレクト レンダリングとカスタム要素コンポジションの両方を使用することもできます。  
  
#### FrameworkElement からの派生の利点  
 次のいずれかの項目に該当する場合は、<xref:System.Windows.FrameworkElement> から派生することをお勧めします。  
  
-   コントロールの外観に関して、単純な要素コンポジションで提供されるよりも厳密な制御を必要とする場合。  
  
-   独自のレンダリング ロジックを定義してコントロールの外観を定義する必要がある場合。  
  
-   <xref:System.Windows.Controls.UserControl> および <xref:System.Windows.Controls.Control> を使用する方法では実現できない新しい方法で既存の要素を構成する必要がある場合。  
  
<a name="control_authoring_basics"></a>   
## コントロールの作成の基本  
 既に述べたように、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] の最も強力な機能の 1 つは、コントロールの基本的なプロパティの設定だけでなく、外観と動作を変更でき、しかもカスタム コントロールを作成する必要がないということです。スタイル、データ バインディング、およびトリガーの各機能は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] プロパティ システムおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント システムによって実現されています。以降のセクションでは、カスタム コントロールの作成に使用されたモデルに関係なく、これらの機能を使用できるようにする方法について説明します。カスタム コントロールのユーザーは、これらの機能を [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] に付属のコントロールと同じように使用できます。  
  
### 依存関係プロパティの使用  
 プロパティが依存関係プロパティの場合、以下が可能です。  
  
-   スタイルでプロパティを設定する。  
  
-   プロパティをデータ ソースにバインドする。  
  
-   プロパティの値として動的リソースを使用する。  
  
-   プロパティをアニメーション化する。  
  
 コントロールのプロパティでこれらの機能のいずれかをサポートすることが必要な場合は、依存関係プロパティとして実装する必要があります。  次に示す例では、次の処理を行うことによって、`Value` という名前の依存関係プロパティを定義します。  
  
-   `ValueProperty` という名前の <xref:System.Windows.DependencyProperty> 識別子を `public` `static` `readonly` フィールドとして定義します。  
  
-   <xref:System.Windows.DependencyProperty.Register%2A?displayProperty=fullName> を呼び出してプロパティ システムにプロパティ名を登録し、次の項目を指定します。  
  
    -   プロパティの名前。  
  
    -   プロパティの型。  
  
    -   プロパティを所有する型。  
  
    -   プロパティのメタデータ。  メタデータには、プロパティの既定値、<xref:System.Windows.CoerceValueCallback>、および <xref:System.Windows.PropertyChangedCallback> が含まれています。  
  
-   依存関係プロパティの登録に使用したのと同じ `Value` という名前で [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] ラッパー プロパティを定義し、プロパティの `get` アクセサーおよび `set` アクセサーを実装します。  この `get` アクセサーおよび `set` アクセサーは、それぞれ <xref:System.Windows.DependencyObject.GetValue%2A> と <xref:System.Windows.DependencyObject.SetValue%2A> を呼び出すだけです。  依存関係プロパティのアクセサーには、その他のロジックを含めないことをお勧めします。クライアントおよび [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、アクセサーを省略して、<xref:System.Windows.DependencyObject.GetValue%2A> および <xref:System.Windows.DependencyObject.SetValue%2A> を直接呼び出すことがあるためです。  たとえば、プロパティがデータ ソースにバインドされている場合、プロパティの `set` アクセサーは呼び出されません。  get アクセサーおよび set アクセサーに他のロジックを追加するのではなく、<xref:System.Windows.ValidateValueCallback>、<xref:System.Windows.CoerceValueCallback>、および <xref:System.Windows.PropertyChangedCallback> の各デリゲートを使用して、値が変更したときの対応やチェックを行います。  これらのコールバックの詳細については、「[依存関係プロパティのコールバックと検証](../../../../docs/framework/wpf/advanced/dependency-property-callbacks-and-validation.md)」を参照してください。  
  
-   <xref:System.Windows.CoerceValueCallback> に対応する、`CoerceValue` という名前のメソッドを定義します。  `CoerceValue` では、`Value` が `MinValue` 以上 `MaxValue` 以下であることを確認します。  
  
-   <xref:System.Windows.PropertyChangedCallback> に対応する、`OnValueChanged` という名前のメソッドを定義します。  `OnValueChanged` では、<xref:System.Windows.RoutedPropertyChangedEventArgs%601> オブジェクトを作成し、`ValueChanged` ルーティング イベントを発生させる準備をします。  ルーティング イベントについては、次のセクションで説明します。  
  
 [!code-csharp[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#dependencyproperty)]
 [!code-vb[UserControlNumericUpDown#DependencyProperty](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#dependencyproperty)]  
  
 詳細については、「[カスタム依存関係プロパティ](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)」を参照してください。  
  
### ルーティング イベントの使用  
 [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] プロパティの概念を追加の機能で拡張する[依存関係プロパティ](GTMT)と同様に、[ルーティング イベント](GTMT)は、標準の [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] イベントの概念を拡張します。  新しい [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] コントロールを作成する場合は、イベントをルーティング イベントとして実装することをお勧めします。ルーティング イベントは以下の機能をサポートしているためです。  
  
-   複数のコントロールの親でイベントを処理できます。  イベントがバブル イベントの場合、要素ツリーの単一の親がイベントをサブスクライブできます。  これにより、アプリケーション開発者は、複数のコントロールのイベントに 1 つのハンドラーで対応できます。  たとえば、<xref:System.Windows.Controls.ListBox> の各項目に含まれるコントロール \(<xref:System.Windows.DataTemplate> に含まれているため\) の場合、アプリケーション開発者は、コントロールのイベントに対応するイベント ハンドラーを <xref:System.Windows.Controls.ListBox> で定義できます。  いずれかのコントロールでイベントが発生すると、そのイベント ハンドラーが呼び出されます。  
  
-   ルーティング イベントは <xref:System.Windows.EventSetter> で使用できます。これにより、アプリケーション開発者は、イベントのハンドラーをスタイル内で指定できます。  
  
-   ルーティング イベントは <xref:System.Windows.EventTrigger> で使用できます。[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] によるプロパティのアニメーション化に有用です。  詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 次に示す例では、次の処理を行うことによって、ルーティング イベントを定義します。  
  
-   `ValueChangedEvent` という名前の <xref:System.Windows.RoutedEvent> 識別子を `public` `static` `readonly` フィールドとして定義します。  
  
-   <xref:System.Windows.EventManager.RegisterRoutedEvent%2A?displayProperty=fullName> メソッドを呼び出して、ルーティング イベントを登録します。  この例では、<xref:System.Windows.EventManager.RegisterRoutedEvent%2A> を呼び出すときに、次の情報を指定しています。  
  
    -   イベントの名前が `ValueChanged` であること。  
  
    -   ルーティング方法が <xref:System.Windows.RoutingStrategy> であること。ソース \(イベントを発生させたオブジェクト\) のイベント ハンドラーがまず呼び出された後、直近の親要素のイベント ハンドラー以降、ソースの親要素のイベント ハンドラーが順に呼び出されていくルーティング方法です。  
  
    -   イベント ハンドラーの型が <xref:System.Windows.RoutedPropertyChangedEventHandler%601> で、<xref:System.Decimal> 型で構築されていること。  
  
    -   イベントを所有する型が `NumericUpDown` であること。  
  
-   `ValueChanged` という名前のパブリック イベントを宣言し、イベント アクセサー宣言を含めます。  この例では、`add` アクセサー宣言で <xref:System.Windows.UIElement.AddHandler%2A> を、`remove` アクセサー宣言で <xref:System.Windows.UIElement.RemoveHandler%2A> を、それぞれ呼び出して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] イベント サービスを使用します。  
  
-   `ValueChanged` イベントを発生させるプロテクト仮想メソッド `OnValueChanged` を作成します。  
  
 [!code-csharp[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml.cs#routedevent)]
 [!code-vb[UserControlNumericUpDown#RoutedEvent](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDown/visualbasic/numericupdown.xaml.vb#routedevent)]  
  
 詳細については、「[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)」および「[カスタム ルーティング イベントを作成する](../../../../docs/framework/wpf/advanced/how-to-create-a-custom-routed-event.md)」を参照してください。  
  
### バインディングの使用  
 コントロールの UI とロジックとを分離するには、データ バインディングを使用する方法もあります。  これは、<xref:System.Windows.Controls.ControlTemplate> を使用してコントロールの外観を定義する場合に、特に重要になります。  データ バインディングを使用すると、コードから UI の特定の部分を参照する必要がなくなる場合があります。  コードが <xref:System.Windows.Controls.ControlTemplate> 内の要素を参照する場合、<xref:System.Windows.Controls.ControlTemplate> が変更されたときには、参照先の要素を新しい <xref:System.Windows.Controls.ControlTemplate> に含める必要があります。このため、<xref:System.Windows.Controls.ControlTemplate> 内の要素の参照を避けることをお勧めします。  
  
 次の例では、`NumericUpDown` コントロールの <xref:System.Windows.Controls.TextBlock> を更新し、名前を割り当てて、コード内で名前を使用してテキスト ボックスを参照しています。  
  
 [!code-xml[UserControlNumericUpDownSimple#UIRefMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml#uirefmarkup)]  
  
 [!code-csharp[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDownSimple/CSharp/NumericUpDown.xaml.cs#uirefcode)]
 [!code-vb[UserControlNumericUpDownSimple#UIRefCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/UserControlNumericUpDownSimple/VisualBasic/NumericUpDown.xaml.vb#uirefcode)]  
  
 次の例では、バインディングを使用して同じことを実現しています。  
  
 [!code-xml[UserControlNumericUpDown#Binding](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UserControlNumericUpDown/CSharp/NumericUpDown.xaml#binding)]  
  
 データ バインディングの詳細については、「[データ バインドの概要](../../../../docs/framework/wpf/data/data-binding-overview.md)」を参照してください。  
  
### デザイナーに対応したデザイン  
 [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] でカスタム WPF コントロールのサポート \(たとえば \[プロパティ\] ウィンドウでのプロパティ編集\) を利用するには、以下のガイドラインに従います。  [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)]向けの開発の詳細については、「[WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)」を参照してください。  
  
#### 依存関係プロパティ  
 「依存関係プロパティの使用」で述べたように、[!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] の `get` アクセサーおよび `set` アクセサーを実装します。デザイナーは、ラッパーを使用して依存関係プロパティの存在を検出する場合がありますが、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] およびコントロールのクライアントと同様に、プロパティを取得または設定するときに必ずしもアクセサーを呼び出す必要はありません。  
  
#### 添付プロパティ  
 以下のガイドラインに従って、カスタム コントロールに添付プロパティを実装する必要があります。  
  
-   *PropertyName* `Property` という形式の `public` `static` `readonly` <xref:System.Windows.DependencyProperty> を、<xref:System.Windows.DependencyProperty.RegisterAttached%2A> メソッドを使用して作成します。  <xref:System.Windows.DependencyProperty.RegisterAttached%2A> に渡すプロパティ名は *PropertyName* に一致する必要があります。  
  
-   `Set` *PropertyName* および `Get`*PropertyName* という名前の `public` `static` CLR メソッドのペアを実装します。  いずれのメソッドも、<xref:System.Windows.DependencyProperty> の派生クラスを最初の引数で受け取ります。  `Set`*PropertyName* メソッドでは、プロパティの登録データ型と同じ型の引数も受け取ります。  `Get`*PropertyName* メソッドでは、同じ型の値を返す必要があります。  `Set`*PropertyName* メソッドがない場合、プロパティは読み取り専用としてマークされます。  
  
-   `Set` *PropertyName* および `Get`*PropertyName* は、対象の依存関係オブジェクトの <xref:System.Windows.DependencyObject.GetValue%2A> メソッドおよび <xref:System.Windows.DependencyObject.SetValue%2A> メソッドのそれぞれに直接転送する必要があります。  デザイナーが添付プロパティにアクセスするときには、メソッド ラッパー経由で呼び出す場合と、対象の依存関係オブジェクトを直接呼び出す場合の両方があります。  
  
 添付プロパティの詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
### 共有リソースの定義と使用  
 アプリケーションと同じアセンブリにコントロールを含めることも、複数のアプリケーションが使用できる別のアセンブリにコントロールをパッケージ化することもできます。  このトピックで示す情報の大部分は、使用する方法に関係なく適用されます。  ただし、1 つだけ例外があります。  アプリケーションと同じアセンブリにコントロールを含める場合は、App.xaml ファイルにグローバル リソースを追加できます。  コントロールだけを含むアセンブリには <xref:System.Windows.Application> オブジェクトが関連付けられないため、App.xaml ファイルは使用できません。  
  
 アプリケーションがリソースを検索するときには、次に示す順序で 3 つのレベルを検索します。  
  
1.  要素レベル。  
  
     システムは、リソースを参照する要素から検索を開始し、ルート要素に到達するまで、論理上の親のリソースの検索を続けます。  
  
2.  アプリケーション レベル。  
  
     <xref:System.Windows.Application> オブジェクトで定義されたリソース。  
  
3.  テーマ レベル。  
  
     テーマ レベルのディクショナリは、Themes というサブフォルダーに格納されています。  Themes フォルダー内のファイルは、テーマに対応しています。  たとえば、Aero.NormalColor.xaml、Luna.NormalColor.xaml、Royale.NormalColor.xaml などのファイルがあります。  また、generic.xaml という名前のファイルが含まれている場合もあります。  システムがテーマ レベルでリソースを検索するときには、最初にテーマ固有のファイル内を検索し、その後で generic.xaml 内を検索します。  
  
 アプリケーションとは別のアセンブリ内にコントロールを含めるときには、グローバル リソースを要素レベルまたはテーマ レベルに配置する必要があります。  どちらに配置する場合も、それぞれの利点があります。  
  
#### 要素レベルでのリソース定義  
 要素レベルで共有リソースを定義するには、カスタムのリソース ディクショナリを作成し、それをコントロールのリソース ディクショナリに結合します。  このメソッドで定義する場合は、リソース ファイルに任意の名前を付けることができます。また、それをコントロールと同じフォルダーに配置できます。  要素レベルのリソースでは、単純な文字列をキーとして使用することもできます。  次の例では、Dictionary1.xaml という名前の、<xref:System.Windows.Media.LinearGradientBrush> リソース ファイルを作成します。  
  
 [!code-xml[SharedResources#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/Dictionary1.xaml#1)]  
  
 ディクショナリを定義したら、それをコントロールのリソース ディクショナリにマージする必要があります。  これを行うには、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] またはコードを使用します。  
  
 次の例では、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] を使用してリソース ディクショナリを結合します。  
  
 [!code-xml[SharedResources#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml#2)]  
  
 この方法の欠点は、参照するたびに <xref:System.Windows.ResourceDictionary> オブジェクトが作成されることです。  たとえば、ライブラリ内に 10 個のカスタム コントロールがあり、XAML を使用して各コントロール用の共有リソース ライブラリを結合する場合は、同一の <xref:System.Windows.ResourceDictionary> オブジェクトが 10 個作成されてしまいます。  これを回避するには、コード内でリソースを結合し、結果として作成される <xref:System.Windows.ResourceDictionary> を返す、静的クラスを作成します。  
  
 次の例では、共有の <xref:System.Windows.ResourceDictionary> を返すクラスを作成します。  
  
 [!code-csharp[SharedResources#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/SharedDictionaryManager.cs#3)]  
  
 次の例では、`InitilizeComponent` を呼び出す前に、共有リソースをコントロールのコンストラクター内でカスタム コントロールのリソースと結合します。  `SharedDictionaryManager.SharedDictionary` は静的プロパティであるため、<xref:System.Windows.ResourceDictionary> は 1 回だけ作成されます。  また、リソース ディクショナリが `InitializeComponent` の呼び出し前に結合されるため、コントロールはその [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] ファイルでリソースを使用できます。  
  
 [!code-csharp[SharedResources#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SharedResources/CS/ShapeResizer.xaml.cs#4)]  
  
#### テーマ レベルでのリソース定義  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、さまざまな Windows テーマ用にリソースを作成できます。  コントロールの作成者は、特定のテーマ用のリソースを定義して、使用するテーマに応じてコントロールの外観を変更できます。  たとえば、Windows クラシック テーマ \(Windows 2000 の既定のテーマ\) の <xref:System.Windows.Controls.Button> の外観は、Windows Luna テーマ \(Windows XP の既定のテーマ\) の <xref:System.Windows.Controls.Button> とは異なります。これは、<xref:System.Windows.Controls.Button> が各テーマ用に異なる <xref:System.Windows.Controls.ControlTemplate> を使用するためです。  
  
 テーマ固有のリソースは、固有のファイル名でリソース ディクショナリに保持されます。  これらのファイルは、コントロールが格納されているフォルダーのサブフォルダーである `Themes` フォルダー内に配置する必要があります。  次の表は、リソース ディクショナリ ファイルと、各ファイルに関連付けられているテーマを示しています。  
  
|リソース ディクショナリ ファイル名|Windows テーマ|  
|------------------------|-----------------|  
|`Classic.xaml`|Windows XP のクラシックな Windows 9x\/2000 の外観|  
|`Luna.NormalColor.xaml`|Windows XP の既定の青のテーマ|  
|`Luna.Homestead.xaml`|Windows XP のオリーブのテーマ|  
|`Luna.Metallic.xaml`|Windows XP のシルバーのテーマ|  
|`Royale.NormalColor.xaml`|Windows XP Media Center Edition の既定のテーマ|  
|`Aero.NormalColor.xaml`|Windows Vista の既定のテーマ|  
  
 すべてのテーマのリソースを定義する必要はありません。  特定のテーマについてリソースが定義されていない場合、コントロールはリソースの `Classic.xaml` をチェックします。  現在のテーマに対応するファイルまたは `Classic.xaml` にリソースが定義されていない場合、コントロールは汎用のリソースを使用します。汎用のリソースは、`generic.xaml` という名前のリソース ディクショナリ ファイルにあります。  `generic.xaml` ファイルは、テーマ固有のリソース ディクショナリ ファイルと同じフォルダー内にあります。  `generic.xaml` は特定の Windows テーマには対応していませんが、テーマ レベルのディクショナリです。  
  
 [テーマおよび UI オートメーションがサポートされた NumericUpDown カスタム コントロールのサンプル](http://go.microsoft.com/fwlink/?LinkID=160025)には、`NumericUpDown` コントロール用の 2 つのリソース ディクショナリが含まれています。1 つは generic.xaml に、もう 1 つは Luna.NormalColor.xaml にあります。  アプリケーションを実行し、Windows XP のシルバーのテーマと別のテーマとを切り替えて、2 つのコントロール テンプレートの違いを確認できます。  Windows Vista を使用している場合は、Luna.NormalColor.xaml を Aero.NormalColor.xaml という名前に変えて、Windows クラシック テーマと Windows Vista の既定のテーマの切り替えなど、2 つのテーマの切り替えを行うことができます。  
  
 テーマ固有のリソース ディクショナリ ファイルに <xref:System.Windows.Controls.ControlTemplate> を置くときには、次の例に示すように、コントロール用の静的コンストラクターを作成し、<xref:System.Windows.DependencyProperty.OverrideMetadata%28System.Type%2CSystem.Windows.PropertyMetadata%29> メソッドを <xref:System.Windows.FrameworkElement.DefaultStyleKey%2A> に対して呼び出す必要があります。  
  
 [!code-csharp[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/CSharp/NumericUpDown.cs#staticconstructor)]
 [!code-vb[CustomControlNumericUpDownOneProject#StaticConstructor](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDownOneProject/visualbasic/numericupdown.vb#staticconstructor)]  
  
##### テーマ リソース用のキーの定義と参照  
 要素レベルでリソースを定義するときには、文字列をキーとして割り当て、その文字列を使用してそのリソースにアクセスできます。  テーマ レベルでリソースを定義するときには、キーとして <xref:System.Windows.ComponentResourceKey> を使用する必要があります。  次の例では、generic.xaml でリソースを定義します。  
  
  
  
 次の例では、キーとして <xref:System.Windows.ComponentResourceKey> を指定して、リソースを参照します。  
  
  
  
##### テーマ リソースの場所の指定  
 コントロールのリソースを見つけるには、アセンブリにコントロール固有のリソースが含まれていることを、ホスト アプリケーションが認識する必要があります。  これを可能にするには、コントロールが含まれているアセンブリに <xref:System.Windows.ThemeInfoAttribute> を追加します。  <xref:System.Windows.ThemeInfoAttribute> には、汎用リソースの場所を指定する <xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> プロパティと、テーマ固有のリソースの場所を指定する <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> プロパティがあります。  
  
 次の例では、<xref:System.Windows.ThemeInfoAttribute.GenericDictionaryLocation%2A> プロパティと <xref:System.Windows.ThemeInfoAttribute.ThemeDictionaryLocation%2A> プロパティを <xref:System.Windows.ResourceDictionaryLocation> に設定して、汎用リソースとテーマ固有のリソースがコントロールと同じアセンブリに置かれていることを示します。  
  
 [!code-csharp[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/csharp/VS_Snippets_Wpf/CustomControlNumericUpDown/CSharp/CustomControlLibrary/Properties/AssemblyInfo.cs#themessection)]
 [!code-vb[CustomControlNumericUpDown#ThemesSection](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/CustomControlNumericUpDown/visualbasic/customcontrollibrary/my project/assemblyinfo.vb#themessection)]  
  
## 参照  
 [WPF デザイナー](http://msdn.microsoft.com/ja-jp/c6c65214-8411-4e16-b254-163ed4099c26)   
 [WPF におけるパッケージの URI](../../../../docs/framework/wpf/app-development/pack-uris-in-wpf.md)   
 [コントロールのカスタマイズ](../../../../docs/framework/wpf/controls/control-customization.md)