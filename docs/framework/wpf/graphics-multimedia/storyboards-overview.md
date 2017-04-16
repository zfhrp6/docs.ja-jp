---
title: "ストーリーボードの概要 | Microsoft Docs"
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
  - "ストーリーボードの構文"
  - "構文, ストーリーボード"
  - "タイムライン"
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
caps.latest.revision: 31
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 26
---
# ストーリーボードの概要
ここでは、<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用してアニメーションを編成および適用する方法を示します。  <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを対話的に操作する方法について説明し、間接的なプロパティの対象化についての構文を示します。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要条件  
 このトピックを理解するには、さまざまな種類のアニメーションとその基本的な機能に精通している必要があります。  アニメーションの概要については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  また、添付プロパティの使用方法についても理解しておく必要があります。  添付プロパティの詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="whatisatimeline"></a>   
## ストーリーボードとは何か  
 タイムラインの型で役に立つのは、アニメーションだけではありません。  他にも一連のタイムラインの編成を容易にし、タイムラインをプロパティに適用するための Timeline クラスが提供されています。  コンテナー タイムラインは <xref:System.Windows.Media.Animation.TimelineGroup> クラスから派生し、<xref:System.Windows.Media.Animation.ParallelTimeline> と <xref:System.Windows.Media.Animation.Storyboard> があります。  
  
 <xref:System.Windows.Media.Animation.Storyboard> はコンテナー タイムラインの型で、含まれる複数のタイムラインの対象情報を持っています。  ストーリーボードには、その他のコンテナー タイムラインやアニメーションなど、任意の型の <xref:System.Windows.Media.Animation.Timeline> を格納できます。  <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、さまざまなオブジェクトおよびプロパティに影響を与える複数のタイムラインを 1 つのタイムライン ツリーに結合でき、複雑なタイミング動作の編成および制御が容易になります。  たとえば、次の 3 つのことを実行するボタンを必要としているとします。  
  
-   ユーザーに選択されると、拡張して色が変わる。  
  
-   クリックされると、縮小してから元のサイズに戻る。  
  
-   無効にされると、縮小し、50% の不透明度になる。  
  
 この場合、同じオブジェクトに適用するアニメーションのセットを複数用意し、ボタンの状態に応じてそれぞれ別の時間に再生します。  <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、アニメーションを編成し、これらをグループ化して 1 つ以上のオブジェクトに適用できます。  
  
<a name="wherecanyouuseastoryboard"></a>   
## ストーリーボードはどこで使用できるか  
 <xref:System.Windows.Media.Animation.Storyboard> を使用すると、アニメーション可能なクラスの[依存関係プロパティ](GTMT)をアニメーション化することができます \(クラスをアニメーション可能にする方法の詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください\)。  ただし、ストーリーボードはフレームワーク レベルの機能であるため、オブジェクトは <xref:System.Windows.FrameworkElement> の <xref:System.Windows.NameScope>、または <xref:System.Windows.FrameworkContentElement> に属している必要があります。  
  
 たとえば、<xref:System.Windows.Media.Animation.Storyboard> を使用すると、次の処理を実行できます。  
  
-   ボタン \(<xref:System.Windows.FrameworkElement> の型\) の背景を描画する <xref:System.Windows.Media.SolidColorBrush> \(非フレームワークの要素\) をアニメーション化します。  
  
-   <xref:System.Windows.Controls.Image> \(<xref:System.Windows.FrameworkElement>\) を使用して表示された <xref:System.Windows.Media.GeometryDrawing> \(非フレームワークの要素\) の塗りつぶしを描画する <xref:System.Windows.Media.SolidColorBrush> \(非フレームワークの要素\) をアニメーション化します。  
  
-   コード内で <xref:System.Windows.Media.SolidColorBrush> の名前がその <xref:System.Windows.FrameworkElement> を含めて登録された場合、<xref:System.Windows.FrameworkElement> を格納するクラスによって宣言された <xref:System.Windows.Media.SolidColorBrush> もアニメーション化します。  
  
 ただし、名前が <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> を含めて登録されていなかったり、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> のプロパティ設定で使用されなかった <xref:System.Windows.Media.SolidColorBrush> については、<xref:System.Windows.Media.Animation.Storyboard> を使用してアニメーション化することはできません。  
  
<a name="applyanimationswithastoryboard"></a>   
## ストーリーボードを使用してアニメーションを適用する方法  
 <xref:System.Windows.Media.Animation.Storyboard> を使用してアニメーションを編成および適用するには、<xref:System.Windows.Media.Animation.Storyboard> の子タイムラインとしてアニメーションを追加します。  <xref:System.Windows.Media.Animation.Storyboard> クラスは、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> および <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=fullName> の添付プロパティを提供します。  これらのプロパティをアニメーションで設定して、アニメーションのターゲット オブジェクトとターゲット プロパティを指定します。  
  
 これらのターゲットにアニメーションを適用するには、トリガー アクションまたはメソッドを使用して <xref:System.Windows.Media.Animation.Storyboard> を開始します。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、<xref:System.Windows.Media.Animation.BeginStoryboard> オブジェクトを <xref:System.Windows.EventTrigger>、<xref:System.Windows.Trigger>、または <xref:System.Windows.DataTrigger> で使用します。  コード内で <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用することもできます。  
  
 各 <xref:System.Windows.Media.Animation.Storyboard> の開始方法がサポートされているさまざまな場所、インスタンス単位、スタイル、コントロール テンプレート、およびデータ テンプレートを次の表に示します。  "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。  
  
|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|  
|----------------------|--------------|----------|-------------------|----------------|-------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.EventTrigger>|○|○|○|○|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.Trigger> プロパティ|Ｘ|○|○|○|[プロパティ値が変化したときにアニメーションをトリガーする](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.DataTrigger>|Ｘ|○|○|○|[How to: Trigger an Animation When Data Changes](http://msdn.microsoft.com/ja-jp/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|○|Ｘ|Ｘ|Ｘ|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard> を使用して、<xref:System.Windows.Shapes.Rectangle> 要素の <xref:System.Windows.FrameworkElement.Width%2A> と、その <xref:System.Windows.Shapes.Rectangle> の描画に使用する <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> をアニメーション化します。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 以下のセクションでは、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> および <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> の添付プロパティについて詳しく説明します。  
  
<a name="targetingelementsandfreezables"></a>   
## フレームワーク要素、フレームワーク コンテンツ要素、およびフリーズ可能オブジェクトの対象化  
 アニメーションでは、そのターゲットを見つけるために、アニメーション化するターゲットの名前およびプロパティを認識する必要があることについては前のセクションで説明しました。  アニメーション化するプロパティを指定することは簡単で、アニメーション化するプロパティの名前で <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=fullName> を設定するだけです。  アニメーション化するプロパティが含まれるオブジェクトの名前を指定するには、アニメーションで <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName> プロパティを設定します。  
  
 <xref:System.Windows.Setter.TargetName%2A> プロパティを機能させるには、ターゲット オブジェクトに名前が付いていなければなりません。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> に名前を割り当てるのは、<xref:System.Windows.Freezable> オブジェクトに名前を割り当てることとは異なります。  
  
 フレームワーク要素は、<xref:System.Windows.FrameworkElement> クラスを継承するそれらのクラスです。  フレームワーク要素の例としては、<xref:System.Windows.Window>、<xref:System.Windows.Controls.DockPanel>、<xref:System.Windows.Controls.Button>、<xref:System.Windows.Shapes.Rectangle> などがあります。  基本的に、ウィンドウ、パネル、およびコントロールはすべて要素です。  フレームワーク コンテンツ要素は、<xref:System.Windows.FrameworkContentElement> クラスを継承するそれらのクラスです。  フレームワーク コンテンツ要素の例としては、<xref:System.Windows.Documents.FlowDocument> や <xref:System.Windows.Documents.Paragraph> などがあります。  型がフレームワーク要素またはフレームワーク コンテンツ要素であるかどうかが明確でない場合は、Name プロパティが含まれているかどうかを確認します。  含まれている場合は、フレームワーク要素またはフレームワーク コンテンツ要素の可能性があります。  確認するには、その型のページの「継承階層」をチェックしてください。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でフレームワーク要素またはフレームワーク コンテンツ要素の対象化を有効にするには、その <xref:System.Windows.FrameworkElement.Name%2A> プロパティを設定します。  また、コード内で <xref:System.Windows.NameScope.RegisterName%2A> メソッドを使用して、各要素の名前を <xref:System.Windows.NameScope> を作成した要素を含めて登録する必要があります。  
  
 次の例では、前の例からの続きとして、<xref:System.Windows.Shapes.Rectangle> に `MyRectangle` \(<xref:System.Windows.FrameworkElement> の型\) という名前を割り当てています。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 名前が割り当てられると、その要素のプロパティはアニメーション化できます。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> 型は、<xref:System.Windows.Freezable> クラスを継承するそれらのクラスです。  <xref:System.Windows.Freezable> の例としては、<xref:System.Windows.Media.SolidColorBrush>、<xref:System.Windows.Media.RotateTransform>、<xref:System.Windows.Media.GradientStop> などがあります。  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でアニメーションによる <xref:System.Windows.Freezable> の対象化を有効にするには、[x:Name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)を使用して名前を割り当てます。  コード内で <xref:System.Windows.NameScope.RegisterName%2A> メソッドを使用して、<xref:System.Windows.NameScope> を作成した要素を含めてその名前を登録する必要があります。  
  
 次の例では、<xref:System.Windows.Freezable> オブジェクトに名前を割り当てます。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 これで、オブジェクトをアニメーションのターゲットにすることができます。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトは、名前スコープを使用して <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> プロパティを解決します。  WPF 名前スコープの詳細については、「[WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)」を参照してください。  <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> プロパティが省略されている場合、アニメーションは、アニメーションが定義されている要素、スタイルの場合にはスタイルが設定されている要素をターゲットにします。  
  
 場合によっては、<xref:System.Windows.Freezable> オブジェクトに名前を割り当てることができないことがあります。  たとえば、<xref:System.Windows.Freezable> がリソースとして宣言されたり、スタイル内でプロパティ値の設定に使用された場合は、名前を割り当てることができません。  名前が割り当てられていないため、それを直接ターゲットにすることができません。ただし、間接的にターゲットにすることはできます。  以下のセクションでは、間接的な対象化の使用方法について説明します。  
  
<a name="pathsyntaxforchangeable"></a>   
## 間接的な対象化  
 <xref:System.Windows.Freezable> がリソースとして宣言されたり、スタイル内でプロパティ値の設定に使用されたときなど、アニメーションで <xref:System.Windows.Freezable> を直接ターゲットにできない場合があります。  この場合、直接ターゲットにできなくても、<xref:System.Windows.Freezable> オブジェクトをアニメーション化することができます。  <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> プロパティに <xref:System.Windows.Freezable> の名前を設定するのではなく、<xref:System.Windows.Freezable> が "属している" 要素の名前を指定します。たとえば、四角形要素の <xref:System.Windows.Shapes.Shape.Fill%2A> の設定に使用された <xref:System.Windows.Media.SolidColorBrush> は、その四角形に属しています。  ブラシをアニメーション化するには、設定に <xref:System.Windows.Freezable> が使用されたフレームワーク要素またはフレームワーク コンテンツ要素のプロパティで開始され、アニメーション化する <xref:System.Windows.Freezable> プロパティで終了するプロパティのチェーンを使用して、アニメーションの <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> を設定します。  
  
  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 <xref:System.Windows.Freezable> が固定されている場合は、複製が作成され、その複製がアニメーション化されることに注意してください。  この場合、元のオブジェクトは実際にはアニメーション化されないため、元のオブジェクトの <xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A> プロパティは引き続き `false` を返します。  複製の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
 また、間接的なプロパティの対象化を使用した場合、存在しないオブジェクトはターゲットにできないことに注意してください。  たとえば、実際にボタンの背景の設定に <xref:System.Windows.Media.LinearGradientBrush> を使用した場合、特定のボタンの <xref:System.Windows.Controls.Control.Background%2A> に <xref:System.Windows.Media.SolidColorBrush> が設定されており、その色をアニメーション化しようとしたとします。  この場合、例外はスローされませんが、<xref:System.Windows.Media.LinearGradientBrush> が <xref:System.Windows.Media.SolidColorBrush.Color%2A> プロパティの変化に反応しないため、アニメーション効果を表示できません。  
  
 以下のセクションでは、間接的なプロパティの対象化についての構文について詳しく説明します。  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### XAML で Freezable のプロパティを間接的に対象化する  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でフリーズ可能オブジェクトのプロパティをターゲットにするには、次の構文を使用します。  
  
||  
|-|  
|*ElementPropertyName*`.`*FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName* は、<xref:System.Windows.Freezable> を使用して設定される <xref:System.Windows.FrameworkElement> のプロパティです。  
  
-   *FreezablePropertyName* は、アニメーション化する <xref:System.Windows.Freezable> のプロパティです。  
  
 次の項目の設定に使用された <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> をアニメーション化する方法を次のコード例に示します。  
  
 四角形要素の <xref:System.Windows.Shapes.Shape.Fill%2A>。  
  
  
  
 コレクションまたはアレイに含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。  
  
 コレクションに含まれるフリーズ可能オブジェクトをターゲットにするには、次のパス構文を使用します。  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 ここで、*CollectionIndex* はアレイまたはコレクションに含まれるオブジェクトのインデックスです。  
  
 たとえば、ある四角形の <xref:System.Windows.Media.TransformGroup> リソースが <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用されていて、その変換の 1 つをアニメーション表示しようとしているとします。  
  
  
  
 次のコードは、前の例で示した <xref:System.Windows.Media.RotateTransform> の <xref:System.Windows.Media.RotateTransform.Angle%2A> プロパティをアニメーション化する方法を示しています。  
  
  
  
<a name="targetingpropertyofchangeableincode"></a>   
### コード内で Freezable のプロパティを間接的に対象化する  
 コード内で <xref:System.Windows.PropertyPath> オブジェクトを作成します。  <xref:System.Windows.PropertyPath> を作成する場合は、<xref:System.Windows.PropertyPath.Path%2A> と <xref:System.Windows.PropertyPath.PathParameters%2A> を指定します。  
  
 <xref:System.Windows.PropertyPath.PathParameters%2A> を作成するには、依存関係プロパティ識別子フィールドのリストが含まれる <xref:System.Windows.DependencyProperty> 型の配列を作成します。  最初の識別子フィールドは、<xref:System.Windows.Freezable> を使用して設定された <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> のプロパティ用です。  次の識別子フィールドは、ターゲットにする <xref:System.Windows.Freezable> のプロパティを表します。  これは、<xref:System.Windows.Freezable> を <xref:System.Windows.FrameworkElement> オブジェクトに接続するプロパティのチェーンと考えてください。  
  
 四角形要素の <xref:System.Windows.Shapes.Shape.Fill%2A> を設定するために使用された <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> をターゲットにする依存関係プロパティのチェーンの例を次に示します。  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 <xref:System.Windows.PropertyPath.Path%2A> も指定する必要があります。  <xref:System.Windows.PropertyPath.Path%2A> は、<xref:System.Windows.PropertyPath.Path%2A> にその <xref:System.Windows.PropertyPath.PathParameters%2A> の解釈方法を伝える <xref:System.String> です。  これには、次の構文を使います。  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex*`).(`*FreezablePropertyArrayIndex*`)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex* は、<xref:System.Windows.Freezable> を使用して設定された <xref:System.Windows.FrameworkElement> オブジェクトのプロパティの識別子を格納する <xref:System.Windows.DependencyProperty> 配列のインデックスです。  
  
-   *FreezablePropertyArrayIndex* は、ターゲットにするプロパティの識別子を格納する <xref:System.Windows.DependencyProperty> 配列のインデックスです。  
  
 前の例で定義した <xref:System.Windows.PropertyPath.PathParameters%2A> を含む <xref:System.Windows.PropertyPath.Path%2A> の例を次に示します。  
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 次の例では、前の例のコードを組み合わせて、四角形要素の <xref:System.Windows.Shapes.Shape.Fill%2A> を設定するために使用された <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> をアニメーション化します。  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 コレクションまたはアレイに含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。  たとえば、ある四角形の <xref:System.Windows.Media.TransformGroup> リソースが <xref:System.Windows.UIElement.RenderTransform%2A> プロパティに適用されていて、その変換の 1 つをアニメーション表示しようとしているとします。  
  
 [!code-xml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 コレクションに含まれる <xref:System.Windows.Freezable> をターゲットにするには、次のパス構文を使用します。  
  
||  
|-|  
|`(`*OwnerPropertyArrayIndex*`).(` *CollectionChildrenPropertyArrayIndex*`)` `[`*CollectionIndex* `].(`*FreezablePropertyArrayIndex*`)`|  
  
 ここで、*CollectionIndex* はアレイまたはコレクションに含まれるオブジェクトのインデックスです。  
  
 <xref:System.Windows.Media.RotateTransform> の <xref:System.Windows.Media.RotateTransform.Angle%2A> プロパティ \(<xref:System.Windows.Media.TransformGroup> 内の 2 番目の変換\) をターゲットにするには、次の <xref:System.Windows.PropertyPath.Path%2A> および <xref:System.Windows.PropertyPath.PathParameters%2A> を使用します。  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 <xref:System.Windows.Media.TransformGroup> 内に含まれた <xref:System.Windows.Media.RotateTransform> の <xref:System.Windows.Media.RotateTransform.Angle%2A> をアニメーション化するための完全なコード例を次に示します。  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### 開始点として Freezable を使用して間接的に対象化する  
 前のセクションで、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> で開始し、<xref:System.Windows.Freezable> サブプロパティへのプロパティ チェーンを作成することによって、<xref:System.Windows.Freezable> を間接的にターゲットにする方法について説明しました。  また、開始点として <xref:System.Windows.Freezable> を使用して、その <xref:System.Windows.Freezable> サブプロパティの 1 つを間接的にターゲットにすることができます。  間接的な対象化で開始点として <xref:System.Windows.Freezable> を使用する場合、適用する制限が 1 つ追加されます。つまり、開始 <xref:System.Windows.Freezable> と、間接的にターゲットにされたサブプロパティまでの各 <xref:System.Windows.Freezable> は固定できません。  
  
<a name="controllable_storyboards"></a>   
## XAML での対話形式でのストーリーボードの制御  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] 内でストーリーボードを開始するには、<xref:System.Windows.Media.Animation.BeginStoryboard> トリガー アクションを使用します。  <xref:System.Windows.Media.Animation.BeginStoryboard> は、アニメーション化するオブジェクトおよびプロパティにアニメーションを分配し、ストーリーボードを開始します。  \(このプロセスの詳細については、「[アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)」を参照してください\)。<xref:System.Windows.Media.Animation.BeginStoryboard> は、<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A> プロパティを指定することによって名前を設定すると、制御可能なストーリーボードになります。  ストーリーボードは、開始されると対話的に制御できます。  ストーリーボードを制御するためにイベント トリガーで使用する、制御可能なストーリーボード アクションの一覧を次に示します。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: ストーリーボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: 一時停止されたストーリーボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio> : ストーリーボードの速度を変更します。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: ストーリーボードがある場合は、それを区間の最後に進めます。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: ストーリーボードを停止します。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard> : ストーリーボードを削除します。  
  
 次の例では、制御可能なストーリーボード アクションを使用して、ストーリーボードを対話的に制御しています。  
  
 [!code-xml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## コードを使用した対話形式でのストーリーボードの制御  
 トリガー アクションを使用してアニメーション化する方法については、前の例で説明しました。  コード内で <xref:System.Windows.Media.Animation.Storyboard> クラスの対話型メソッドを使用することにより、ストーリーボードを制御することもできます。  コード内で <xref:System.Windows.Media.Animation.Storyboard> を対話型にするには、ストーリーボードの <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドの適切なオーバーロードを使用し、制御可能にするために `true` を指定する必要があります。  詳細については、「<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>」を参照してください。  
  
 <xref:System.Windows.Media.Animation.Storyboard> の開始後の操作に使用できるメソッドの一覧を次に示します。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 これらのメソッドを使用する利点は、<xref:System.Windows.Trigger> オブジェクトまたは <xref:System.Windows.TriggerAction> オブジェクトを作成する必要がなく、必要なのは操作対象の制御可能な <xref:System.Windows.Media.Animation.Storyboard> への参照だけであることです。  
  
 **メモ :**  <xref:System.Windows.Media.Animation.Clock> で実行され、そのため <xref:System.Windows.Media.Animation.Storyboard> でも実行されるすべての対話形式のアクションは、次の描画の少し前に発生する、タイミング エンジンの次の目盛りで実行されます。  たとえば、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A> メソッドを使用してアニメーション内の別のポイントにジャンプするとき、プロパティ値は直ちには変わらず、値はタイミング エンジンの次の目盛りで変わります。  
  
 <xref:System.Windows.Media.Animation.Storyboard> クラスの対話型メソッドを使用して、アニメーションを適用および制御する方法を次の例に示します。  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## スタイル内でアニメーション化を行う  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、<xref:System.Windows.Style> 内でアニメーションを定義できます。  <xref:System.Windows.Style> 内の <xref:System.Windows.Media.Animation.Storyboard> によってアニメーション化することは、他の場所の <xref:System.Windows.Media.Animation.Storyboard> を使用することと同じですが、次の 3 点が異なります。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> を指定しない場合、<xref:System.Windows.Media.Animation.Storyboard> は、常に <xref:System.Windows.Style> が適用される要素をターゲットにします。  <xref:System.Windows.Freezable> オブジェクトをターゲットにするには、間接的な対象化を使用する必要があります。  間接的な対象化の詳細については、「[間接的な対象化](#pathsyntaxforchangeable)」を参照してください。  
  
-   <xref:System.Windows.EventTrigger> または <xref:System.Windows.Trigger> の <xref:System.Windows.EventTrigger.SourceName%2A> は指定できません。  
  
-   <xref:System.Windows.Media.Animation.Storyboard> またはアニメーションのプロパティ値を設定する際に、動的リソース参照またはデータ バインディング式は使用できません。  これは、<xref:System.Windows.Style> 内のものはすべてスレッド セーフである必要があり、タイミング システムはこれらをスレッド セーフにする <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> オブジェクトである必要があるからです。  <xref:System.Windows.Media.Animation.Storyboard> は、それ自身またはその子タイムラインに動的リソース参照またはデータ バインディング式が含まれている場合、固定できません。  フリーズおよびその他の <xref:System.Windows.Freezable> 機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、<xref:System.Windows.Media.Animation.Storyboard> またはアニメーション イベントのイベント ハンドラーを宣言できません。  
  
 スタイル内でストーリーボードを定義する方法の例については、「[スタイル内でアニメーション化を行う](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md)」の例を参照してください。  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## ControlTemplate 内でアニメーション化を行う  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、<xref:System.Windows.Controls.ControlTemplate> 内でアニメーションを定義できます。  <xref:System.Windows.Controls.ControlTemplate> 内の <xref:System.Windows.Media.Animation.Storyboard> によってアニメーション化することは、他の場所の <xref:System.Windows.Media.Animation.Storyboard> を使用することと同じですが、次の 2 点が異なります。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> が参照できるのは、<xref:System.Windows.Controls.ControlTemplate> の子オブジェクトだけです。  <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> が指定されていない場合、アニメーションは <xref:System.Windows.Controls.ControlTemplate> が適用される要素をターゲットにします。  
  
-   <xref:System.Windows.EventTrigger> または <xref:System.Windows.Trigger> の <xref:System.Windows.EventTrigger.SourceName%2A> が参照できるのは、<xref:System.Windows.Controls.ControlTemplate> の子オブジェクトだけです。  
  
-   <xref:System.Windows.Media.Animation.Storyboard> またはアニメーションのプロパティ値を設定する際に、動的リソース参照またはデータ バインディング式は使用できません。  これは、<xref:System.Windows.Controls.ControlTemplate> 内のものはすべてスレッド セーフである必要があり、タイミング システムはこれらをスレッド セーフにする <xref:System.Windows.Freezable.Freeze%2A> <xref:System.Windows.Media.Animation.Storyboard> オブジェクトである必要があるからです。  <xref:System.Windows.Media.Animation.Storyboard> は、それ自身またはその子タイムラインに動的リソース参照またはデータ バインディング式が含まれている場合、固定できません。  フリーズおよびその他の <xref:System.Windows.Freezable> 機能の詳細については、「[Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)」を参照してください。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、<xref:System.Windows.Media.Animation.Storyboard> またはアニメーション イベントのイベント ハンドラーを宣言できません。  
  
 <xref:System.Windows.Controls.ControlTemplate> でストーリーボードを定義する方法の例については、「[ControlTemplate 内でアニメーション化を行う](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)」の例を参照してください。  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## プロパティ値が変化したときにアニメーション化を行う  
 スタイル内およびコントロール テンプレート内では、トリガー オブジェクトを使用して、プロパティが変化したときにストーリーボードを開始します。  使用例については、「[プロパティ値が変化したときにアニメーションをトリガーする](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)」および「[ControlTemplate 内でアニメーション化を行う](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)」を参照してください。  
  
 プロパティの <xref:System.Windows.Trigger> オブジェクトによって適用されるアニメーションの動作は、<xref:System.Windows.EventTrigger> アニメーション、または <xref:System.Windows.Media.Animation.Storyboard> メソッドを使用して開始されるアニメーションより複雑です。  他の <xref:System.Windows.Trigger> オブジェクトによって定義されるアニメーションで "ハンドオフ" しますが、<xref:System.Windows.EventTrigger> およびメソッドでトリガーされるアニメーションで構成されます。  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)   
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)