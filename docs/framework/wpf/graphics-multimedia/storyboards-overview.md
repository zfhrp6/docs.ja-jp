---
title: ストーリーボードの概要
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Storyboard syntax [WPF]
- syntax [WPF], Storyboard
- timelines [WPF]
ms.assetid: 1a698c3c-30f1-4b30-ae56-57e8a39811bd
ms.openlocfilehash: 36922dce795443a4c1136f6442eff1c297f3c641
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="storyboards-overview"></a>ストーリーボードの概要
このトピックは、使用する方法を示します<xref:System.Windows.Media.Animation.Storyboard>を整理し、アニメーションを適用するオブジェクト。 対話的に操作する方法を説明<xref:System.Windows.Media.Animation.Storyboard>オブジェクトおよび構文を対象とする間接的なプロパティについて説明します。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、さまざまな種類のアニメーションとその基本的な機能に精通している必要があります。 アニメーションの概要については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。 また、添付プロパティの使用方法についても理解しておく必要があります。 添付プロパティの詳細については、「[添付プロパティの概要](../../../../docs/framework/wpf/advanced/attached-properties-overview.md)」を参照してください。  
  
<a name="whatisatimeline"></a>   
## <a name="what-is-a-storyboard"></a>ストーリーボードとは何か  
 タイムラインの型で役に立つのは、アニメーションだけではありません。 他にも一連のタイムラインの編成を容易にし、タイムラインをプロパティに適用するための Timeline クラスが提供されています。 派生してコンテナー タイムライン、<xref:System.Windows.Media.Animation.TimelineGroup>クラス、および含める<xref:System.Windows.Media.Animation.ParallelTimeline>と<xref:System.Windows.Media.Animation.Storyboard>です。  
  
 A<xref:System.Windows.Media.Animation.Storyboard>が含まれているタイムラインの対象とする情報を提供するコンテナ タイムラインの型です。 ストーリー ボードの任意の型を含めることができます<xref:System.Windows.Media.Animation.Timeline>(その他のコンテナーのタイムラインやアニメーションなど)。 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、影響を与えるさまざまなオブジェクトおよびプロパティを 1 つのタイムライン ツリー、やすく整理し、複雑なタイミング動作を制御するためにタイムラインを結合できます。 たとえば、次の 3 つのことを実行するボタンを必要としているとします。  
  
-   ユーザーに選択されると、拡大して色が変わる。  
  
-   クリックされると、いったん縮小してから元のサイズに戻る。  
  
-   無効にされると、縮小し、50% の不透明度になる。  
  
 この場合、同じオブジェクトに適用するアニメーションのセットを複数用意し、ボタンの状態に応じてさまざまな場合に再生します。 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用すると、アニメーションを整理し、それらを 1 つまたは複数のオブジェクトをグループに適用できます。  
  
<a name="wherecanyouuseastoryboard"></a>   
## <a name="where-can-you-use-a-storyboard"></a>ストーリーボードはどこで使用できるか  
 A<xref:System.Windows.Media.Animation.Storyboard>アニメーション可能なクラスの依存関係プロパティをアニメーション化するために使用する (新機能により、クラスは、アニメーション化に関する詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md))。 ただし、storyboarding フレームワーク レベルの機能があるため、オブジェクトに属する必要があります、<xref:System.Windows.NameScope>の<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。  
  
 たとえば、使用する、<xref:System.Windows.Media.Animation.Storyboard>を次を行うには。  
  
-   アニメーション化する、<xref:System.Windows.Media.SolidColorBrush>ボタンの背景を描画する (非 framework 要素) (の型<xref:System.Windows.FrameworkElement>)、  
  
-   アニメーション化する、<xref:System.Windows.Media.SolidColorBrush>の塗りつぶしを描画する (非 framework 要素)、 <xref:System.Windows.Media.GeometryDrawing> (非 framework 要素) の表示を使用して、 <xref:System.Windows.Controls.Image> (<xref:System.Windows.FrameworkElement>)。  
  
-   コードでは、アニメーション、<xref:System.Windows.Media.SolidColorBrush>が含まれているクラスで宣言された、<xref:System.Windows.FrameworkElement>場合は、<xref:System.Windows.Media.SolidColorBrush>をその名前を登録<xref:System.Windows.FrameworkElement>です。  
  
 ただし、使用できません、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化する、<xref:System.Windows.Media.SolidColorBrush>名を登録しなかった、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>のプロパティを設定に使用されなかったか、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。  
  
<a name="applyanimationswithastoryboard"></a>   
## <a name="how-to-apply-animations-with-a-storyboard"></a>ストーリーボードを使用してアニメーションを適用する方法  
 使用する、<xref:System.Windows.Media.Animation.Storyboard>の子タイムラインとして、アニメーションの追加を整理し、アニメーションの適用、<xref:System.Windows.Media.Animation.Storyboard>です。 <xref:System.Windows.Media.Animation.Storyboard>クラスを提供、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType>アタッチされるプロパティです。 これらのプロパティをアニメーションで設定して、アニメーションのターゲット オブジェクトとターゲット プロパティを指定します。  
  
 開始する、ターゲットにアニメーションを適用する、<xref:System.Windows.Media.Animation.Storyboard>トリガーの動作またはメソッドを使用します。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用する、<xref:System.Windows.Media.Animation.BeginStoryboard>オブジェクトを<xref:System.Windows.EventTrigger>、 <xref:System.Windows.Trigger>、または<xref:System.Windows.DataTrigger>です。 コードでは、使用することも、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドです。  
  
 次の表は、さまざまな場所を示しています。 ここで各<xref:System.Windows.Media.Animation.Storyboard>開始手法はサポートされて: インスタンスごとに、スタイル、コントロール テンプレート、およびデータ テンプレート。 "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。  
  
|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.EventTrigger>|[はい]|はい|はい|[はい]|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> プロパティ名 <xref:System.Windows.Trigger>|×|はい|はい|[はい]|[プロパティ値が変化したときにアニメーションをトリガーする](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.DataTrigger>|×|はい|はい|[はい]|[方法: データが変化したときにアニメーションをトリガーする](http://msdn.microsoft.com/library/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|[はい]|いいえ|Ｘ|×|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 次の例では、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化する、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>要素および<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を描画するために使用<xref:System.Windows.Shapes.Rectangle>です。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#1)]  
  
 [!code-csharp[storyboards_ovw_snip#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#100)]  
  
 次のセクションでは、説明、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>添付プロパティの詳細についてです。  
  
<a name="targetingelementsandfreezables"></a>   
## <a name="targeting-framework-elements-framework-content-elements-and-freezables"></a>フレームワーク要素、フレームワーク コンテンツ要素、およびフリーズ可能オブジェクトの対象化  
 アニメーションでは、そのターゲットを見つけるために、ターゲットの名前とアニメーション化するプロパティを認識する必要があることについては前のセクションで説明しました。 アニメーション化するプロパティを指定するは簡単: 単設定<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A?displayProperty=nameWithType>アニメーション化するプロパティの名前に置き換えます。  プロパティを設定してアニメーション化するオブジェクトの名前を指定する、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=nameWithType>アニメーションのプロパティです。  
  
 <xref:System.Windows.Setter.TargetName%2A>プロパティを機能させる、対象のオブジェクトには名前が必要です。 名前が割り当てられて、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]に名の割り当てとは異なる、<xref:System.Windows.Freezable>オブジェクト。  
  
 フレームワーク要素はこれらのクラスから継承する、<xref:System.Windows.FrameworkElement>クラスです。 フレームワーク要素の例として、 <xref:System.Windows.Window>、 <xref:System.Windows.Controls.DockPanel>、 <xref:System.Windows.Controls.Button>、および<xref:System.Windows.Shapes.Rectangle>です。 基本的に、ウィンドウ、パネル、およびコントロールはすべて要素です。 フレームワーク コンテンツ要素はこれらのクラスから継承する、<xref:System.Windows.FrameworkContentElement>クラスです。 フレームワークのコンテンツ要素の例として、<xref:System.Windows.Documents.FlowDocument>と<xref:System.Windows.Documents.Paragraph>です。 型がフレームワーク要素またはフレームワーク コンテンツ要素であるかどうかが明確でない場合は、Name プロパティが含まれているかどうかを確認します。 含まれている場合は、フレームワーク要素またはフレームワーク コンテンツ要素と考えられます。 確かめるには、その型のページの「継承階層」を参照してください。  
  
 フレームワーク要素またはのコンテンツ要素のフレームワークのターゲット設定を有効にする[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、設定したその<xref:System.Windows.FrameworkElement.Name%2A>プロパティです。 コードでは、する必要がありますを使用して、<xref:System.Windows.NameScope.RegisterName%2A>作成した要素を持つ要素の名前を登録するメソッド、<xref:System.Windows.NameScope>です。  
  
 次の例は、前の例では、名前を割り当てます`MyRectangle`、 <xref:System.Windows.Shapes.Rectangle>、一種<xref:System.Windows.FrameworkElement>です。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#2)]  
  
 [!code-csharp[storyboards_ovw_snip#102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#102)]  
  
 名前が割り当てられると、その要素のプロパティはアニメーション化できます。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#5)]  
  
 [!code-csharp[storyboards_ovw_snip#105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#105)]  
  
 <xref:System.Windows.Freezable> 種類は、これらのクラスから継承する、<xref:System.Windows.Freezable>クラスです。 例として<xref:System.Windows.Freezable>含める<xref:System.Windows.Media.SolidColorBrush>、 <xref:System.Windows.Media.RotateTransform>、および<xref:System.Windows.Media.GradientStop>です。  
  
 ターゲット設定を有効にする、<xref:System.Windows.Freezable>にアニメーションによって[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用する、 [X:name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)名前を指定します。 コードで使用する、<xref:System.Windows.NameScope.RegisterName%2A>作成した要素に名前を登録する方法、<xref:System.Windows.NameScope>です。  
  
 次の例では、名前、<xref:System.Windows.Freezable>オブジェクト。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#3)]  
  
 [!code-csharp[storyboards_ovw_snip#103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#103)]  
  
 これで、オブジェクトをアニメーションのターゲットにすることができます。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/StoryboardsExample.xaml#7)]  
  
 [!code-csharp[storyboards_ovw_snip#107](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/StoryboardsExample.cs#107)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトの名前スコープを使用して解決するのには、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティです。 WPF 名前スコープの詳細については、「[WPF XAML 名前スコープ](../../../../docs/framework/wpf/advanced/wpf-xaml-namescopes.md)」を参照してください。 場合、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティを省略すると、アニメーション、またはで要素定義は、スタイルの場合、スタイル設定された要素を対象とします。  
  
 名前を割り当てられない場合があります、<xref:System.Windows.Freezable>オブジェクト。 たとえば場合、<xref:System.Windows.Freezable>リソースとして宣言またはスタイルのプロパティ値を設定するために使用されている名前を指定することはできません。 名前が割り当てられていないため、それを直接ターゲットにすることができません。ただし、間接的にターゲットにすることはできます。 以下のセクションでは、間接的な対象化の使用方法について説明します。  
  
<a name="pathsyntaxforchangeable"></a>   
## <a name="indirect-targeting"></a>間接的な対象化  
 時間がある、<xref:System.Windows.Freezable>ときなど、アニメーションを直接対象にすることはできません、<xref:System.Windows.Freezable>リソースとして宣言されているか、スタイルのプロパティ値を設定するために使用します。 このような場合、直接ターゲットにできない場合でもまだをアニメーション化できます、<xref:System.Windows.Freezable>オブジェクト。 設定ではなく、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>プロパティの名前を持つ、 <xref:System.Windows.Freezable>、する要素の名前が、付与、 <xref:System.Windows.Freezable> 「属しています」。 たとえば、<xref:System.Windows.Media.SolidColorBrush>を設定するため、<xref:System.Windows.Shapes.Shape.Fill%2A>四角形の要素はその四角形に属します。 ブラシをアニメーション化するにはアニメーションの設定は<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>framework 要素またはフレームワーク コンテンツ要素のプロパティに開始されるプロパティのチェーンで、<xref:System.Windows.Freezable>で終わります設定に使用した、<xref:System.Windows.Freezable>プロパティをアニメーション化します。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#33)]  
  
 [!code-csharp[storyboards_ovw_snip#134](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#134)]  
  
 なお場合、<xref:System.Windows.Freezable>が固定されると、複製になります、およびその複製はアニメーション化します。 この場合、元のオブジェクトの<xref:System.Windows.Media.Animation.Animatable.HasAnimatedProperties%2A>プロパティを返し続けます`false`元のオブジェクトが実際にはアニメーションで表示されないため、します。 複製の詳細については、次を参照してください。、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
 また、間接的なプロパティの対象化を使用するとき、存在しないオブジェクトを対象化する可能性があることに注意してください。 たとえばと思うかもしれませんを<xref:System.Windows.Controls.Control.Background%2A>で設定した特定のボタンの<xref:System.Windows.Media.SolidColorBrush>実際にその色をアニメーション化しようと、<xref:System.Windows.Media.LinearGradientBrush>ボタンの背景を設定するために使用されました。 このような場合は、例外はスローされません。アニメーションが視覚的効果があるために失敗した<xref:System.Windows.Media.LinearGradientBrush>への変更に反応しません、<xref:System.Windows.Media.SolidColorBrush.Color%2A>プロパティです。  
  
 以下のセクションでは、間接的なプロパティの対象化の構文について詳しく説明します。  
  
<a name="xamlsyntaxchangeableproperty"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-xaml"></a>XAML でフリーズ可能オブジェクトのプロパティを間接的に対象化する  
 Freezable のプロパティを対象とする[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、次の構文を使用します。  
  
||  
|-|  
|*ElementPropertyName* `.` *FreezablePropertyName*|  
  
 Where  
  
-   *ElementPropertyName*のプロパティ、<xref:System.Windows.FrameworkElement>を<xref:System.Windows.Freezable>を設定するために使用し、  
  
-   *FreezablePropertyName*のプロパティ、<xref:System.Windows.Freezable>アニメーション化します。  
  
 次のコードは、アニメーション化する方法を示しています、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を設定するため、  
  
 <xref:System.Windows.Shapes.Shape.Fill%2A> 四角形の要素。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#32](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#32)]  
  
 コレクションまたは配列に含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。  
  
 コレクションに含まれるフリーズ可能オブジェクトをターゲットにするには、次のパス構文を使用します。  
  
||  
|-|  
|*ElementPropertyName* `.Children[` *CollectionIndex* `].` *FreezablePropertyName*|  
  
 ここで*ここ*配列またはコレクション内のオブジェクトのインデックスです。  
  
 たとえば、四角形が含まれていること、<xref:System.Windows.Media.TransformGroup>リソースに適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ、およびするが含まれている変換のいずれかのアニメーションを設定します。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#34](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#34)]  
  
 次のコードは、アニメーション化する方法を示しています、<xref:System.Windows.Media.RotateTransform.Angle%2A>のプロパティ、<xref:System.Windows.Media.RotateTransform>前の例に示すようにします。  
  
 [!code-xaml[storyboards_ovw_snip_XAML#35](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip_XAML/CS/IndirectTargetingExample.xaml#35)]  
  
<a name="targetingpropertyofchangeableincode"></a>   
### <a name="indirectly-targeting-a-property-of-a-freezable-in-code"></a>コードでフリーズ可能オブジェクトのプロパティを間接的に対象化する  
 作成するコードでは、<xref:System.Windows.PropertyPath>オブジェクト。 作成するときに、<xref:System.Windows.PropertyPath>を指定する、<xref:System.Windows.PropertyPath.Path%2A>と<xref:System.Windows.PropertyPath.PathParameters%2A>です。  
  
 作成する<xref:System.Windows.PropertyPath.PathParameters%2A>、型の配列を作成する<xref:System.Windows.DependencyProperty>依存関係プロパティ識別子フィールドのリストを格納します。 プロパティの識別子の最初のフィールドは、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>を<xref:System.Windows.Freezable>を設定するために使用します。 次の識別子フィールドのプロパティを表す、<xref:System.Windows.Freezable>ターゲットにします。 接続しているプロパティのチェーンとないということ、<xref:System.Windows.Freezable>を<xref:System.Windows.FrameworkElement>オブジェクト。  
  
 対象とする依存関係プロパティのチェーンの例を次に示します、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を設定するため、<xref:System.Windows.Shapes.Shape.Fill%2A>長方形要素のです。  
  
 [!code-csharp[storyboards_ovw_snip#135](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#135)]  
  
 指定する必要があります、<xref:System.Windows.PropertyPath.Path%2A>です。 A<xref:System.Windows.PropertyPath.Path%2A>は、<xref:System.String>ことが示されます、<xref:System.Windows.PropertyPath.Path%2A>を解釈する方法、<xref:System.Windows.PropertyPath.PathParameters%2A>です。 次の構文が使用されます。  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *FreezablePropertyArrayIndex* `)`|  
  
 Where  
  
-   *OwnerPropertyArrayIndex*のインデックス、<xref:System.Windows.DependencyProperty>の識別子を含む配列、<xref:System.Windows.FrameworkElement>オブジェクトのプロパティを<xref:System.Windows.Freezable>を設定するために使用し、  
  
-   *FreezablePropertyArrayIndex*のインデックス、<xref:System.Windows.DependencyProperty>をターゲットにプロパティの識別子を格納する配列。  
  
 次の例は、<xref:System.Windows.PropertyPath.Path%2A>に付属する、<xref:System.Windows.PropertyPath.PathParameters%2A>前の例で定義されています。
  
 [!code-csharp[storyboards_ovw_snip#PropertyChainAndPath](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#propertychainandpath)]  
  
 次の例は、アニメーション化する前の例のコードを組み合わせた、<xref:System.Windows.Media.SolidColorBrush.Color%2A>の<xref:System.Windows.Media.SolidColorBrush>を設定するため、<xref:System.Windows.Shapes.Shape.Fill%2A>長方形要素のです。  
  
 [!code-csharp[storyboards_ovw_snip#137](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#137)]  
  
 コレクションまたは配列に含まれるフリーズ可能オブジェクトをターゲットにしなければならない場合があります。 たとえば、四角形が含まれていること、<xref:System.Windows.Media.TransformGroup>リソースに適用されるその<xref:System.Windows.UIElement.RenderTransform%2A>プロパティ、およびするが含まれている変換のいずれかのアニメーションを設定します。  
  
 [!code-xaml[storyboards_ovw_snip#142](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml#142)]  
  
 ターゲットに、<xref:System.Windows.Freezable>コレクション内に、次のパス構文を使用します。  
  
||  
|-|  
|`(` *OwnerPropertyArrayIndex* `).(` *CollectionChildrenPropertyArrayIndex* `)` `[` *CollectionIndex* `].(` *FreezablePropertyArrayIndex* `)`|  
  
 ここで*ここ*配列またはコレクション内のオブジェクトのインデックスです。  
  
 ターゲットに、<xref:System.Windows.Media.RotateTransform.Angle%2A>のプロパティ、 <xref:System.Windows.Media.RotateTransform>、2 番目の変換で、 <xref:System.Windows.Media.TransformGroup>、以下を使用するよう<xref:System.Windows.PropertyPath.Path%2A>と<xref:System.Windows.PropertyPath.PathParameters%2A>です。  
  
 [!code-csharp[storyboards_ovw_snip#139](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#139)]  
  
 次の例では、アニメーションの完全なコード、<xref:System.Windows.Media.RotateTransform.Angle%2A>の<xref:System.Windows.Media.RotateTransform>内に含まれる、<xref:System.Windows.Media.TransformGroup>です。  
  
 [!code-csharp[storyboards_ovw_snip#138](../../../../samples/snippets/csharp/VS_Snippets_Wpf/storyboards_ovw_snip/CSharp/IndirectTargetingExample.xaml.cs#138)]  
  
### <a name="indirectly-targeting-with-a-freezable-as-the-starting-point"></a>開始点として Freezable を使用して間接的に対象化する  
 前のセクションでは、直接アニメーション化する方法を説明した、<xref:System.Windows.Freezable>を使用して開始、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>プロパティ チェーンを作成して、<xref:System.Windows.Freezable>サブ プロパティです。 使用することも、<xref:System.Windows.Freezable>からポイントし、直接の対象としていないのいずれかの<xref:System.Windows.Freezable>サブプロパティです。 使用する場合、その他の制限が適用されます、<xref:System.Windows.Freezable>間接の対象とするための出発点として: 開始<xref:System.Windows.Freezable>あらゆる<xref:System.Windows.Freezable>と間接的に対象となるサブ プロパティとする必要がありますは固定表示されません。  
  
<a name="controllable_storyboards"></a>   
## <a name="interactively-controlling-a-storyboard-in-xaml"></a>XAML での対話形式でのストーリーボードの制御  
 ストーリー ボードを起動する[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]を使用する、<xref:System.Windows.Media.Animation.BeginStoryboard>アクションをトリガーします。 <xref:System.Windows.Media.Animation.BeginStoryboard> オブジェクトとプロパティをストーリー ボードを起動するアニメーションを配布します。 (詳細については、このプロセスは、次を参照してください、[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)。)。提供する場合、<xref:System.Windows.Media.Animation.BeginStoryboard>名前を指定してその<xref:System.Windows.Media.Animation.BeginStoryboard.Name%2A>プロパティ、おくことで制御可能なストーリー ボードです。 ストーリーボードが開始すると対話的に制御できます。 制御可能なストーリーボード アクションの一覧を次に示します。これらをイベント トリガーで使用して、ストーリーボードを制御します。  
  
-   <xref:System.Windows.Media.Animation.PauseStoryboard>: ストーリー ボードを一時停止します。  
  
-   <xref:System.Windows.Media.Animation.ResumeStoryboard>: 一時停止しているストーリー ボードを再開します。  
  
-   <xref:System.Windows.Media.Animation.SetStoryboardSpeedRatio>: ストーリー ボードの速度を変更します。  
  
-   <xref:System.Windows.Media.Animation.SkipStoryboardToFill>: 1 つがある場合は、その保留期間の終了をストーリー ボードを進めます。  
  
-   <xref:System.Windows.Media.Animation.StopStoryboard>: ストーリー ボードを停止します。  
  
-   <xref:System.Windows.Media.Animation.RemoveStoryboard>: ストーリー ボードを削除します。  
  
 次の例では、制御可能なストーリーボード アクションを使用して、ストーリーボードを対話的に制御しています。  
  
 [!code-xaml[animation_ovws_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snip/CS/ControllableStoryboardExample.xaml#controllablestoryboardexamplewholepage)]  
  
<a name="controllable_storyboards_procedural"></a>   
## <a name="interactively-controlling-a-storyboard-by-using-code"></a>コードを使用した対話形式でのストーリーボードの制御  
 トリガー アクションを使用してアニメーション化する方法については、前の例で説明しました。 コードではの対話型のメソッドを使用してストーリー ボードを制御することも、<xref:System.Windows.Media.Animation.Storyboard>クラスです。 <xref:System.Windows.Media.Animation.Storyboard>をコードで対話できる、ストーリー ボードの適切なオーバー ロードを使用する必要があります<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドを指定して`true`制御可能にします。 参照してください、<xref:System.Windows.Media.Animation.Storyboard.Begin%28System.Windows.FrameworkElement%2CSystem.Boolean%29>詳細ページ。  
  
 次の一覧を操作するために使用する方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>が開始した後。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Pause%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Resume%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.SkipToFill%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Stop%2A>  
  
-   <xref:System.Windows.Media.Animation.Storyboard.Remove%2A>  
  
 これらのメソッドを使用する利点は、作成する必要がある<xref:System.Windows.Trigger>または<xref:System.Windows.TriggerAction>オブジェクト以外の場合は、制御可能なへの参照を必要なだけする<xref:System.Windows.Media.Animation.Storyboard>を操作します。  
  
 **注:** で行われたすべての対話型操作、 <xref:System.Windows.Media.Animation.Clock>、およびでも、<xref:System.Windows.Media.Animation.Storyboard>タイミング エンジンは、[次へ] のレンダリングの直前に発生するは、次の目盛り上で行われます。 使用する場合など、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>アニメーション、プロパティの値に別のポイントにジャンプするメソッドはすぐに変更されません、代わりに、値が変更されたタイミング エンジンの次のタイマー刻みで。  
  
 次の例は、適用の対話型のメソッドを使用してアニメーションを制御する方法を示しています。、<xref:System.Windows.Media.Animation.Storyboard>クラスです。  
  
 [!code-csharp[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/ControllableStoryboardExample.cs#controllablestoryboardexamplewholepage)]
 [!code-vb[animation_ovws_procedural_snip#ControllableStoryboardExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/controllablestoryboardexample.vb#controllablestoryboardexamplewholepage)]  
  
<a name="usingstoryboardsinstyles"></a>   
## <a name="animate-in-a-style"></a>スタイル内でアニメーション化を行う  
 使用することができます<xref:System.Windows.Media.Animation.Storyboard>でアニメーションを定義するオブジェクト、<xref:System.Windows.Style>です。 アニメーション化、<xref:System.Windows.Media.Animation.Storyboard>で、<xref:System.Windows.Style>使用と似ています、<xref:System.Windows.Media.Animation.Storyboard>次の 3 つの例外で、他の場所。  
  
-   指定しない、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>;<xref:System.Windows.Media.Animation.Storyboard>先の要素は常にターゲット、<xref:System.Windows.Style>を適用します。 ターゲットに<xref:System.Windows.Freezable>オブジェクト、間接的なターゲットを使用する必要があります。 間接的な対象化の詳細については、次を参照してください。、[間接の対象とする](#pathsyntaxforchangeable)セクションです。  
  
-   指定することはできません、<xref:System.Windows.EventTrigger.SourceName%2A>の<xref:System.Windows.EventTrigger>または<xref:System.Windows.Trigger>です。  
  
-   動的リソース参照やデータ バインディング式を使用して設定することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーションのプロパティの値。 内部のすべて、 <xref:System.Windows.Style> 、スレッド セーフである必要がありますタイミング システムにする必要があります<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>スレッド セーフであるようにするオブジェクト。 A<xref:System.Windows.Media.Animation.Storyboard>またはその子タイムラインに動的なリソースの参照やデータ バインディング式が含まれている場合に固定することはできません。 固定やその他の詳細については<xref:System.Windows.Freezable>機能を参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、用のイベント ハンドラーを宣言することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーション イベント。  
  
 スタイルのストーリー ボードを定義する方法を示す例は、次を参照してください。、[スタイルでアニメーション](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-style.md)例です。  
  
<a name="defineAStoryboardInAControlTemplateSection"></a>   
## <a name="animate-in-a-controltemplate"></a>ControlTemplate 内でアニメーション化を行う  
 使用することができます<xref:System.Windows.Media.Animation.Storyboard>でアニメーションを定義するオブジェクト、<xref:System.Windows.Controls.ControlTemplate>です。 アニメーション化、<xref:System.Windows.Media.Animation.Storyboard>で、<xref:System.Windows.Controls.ControlTemplate>使用と似ています、<xref:System.Windows.Media.Animation.Storyboard>次の 2 つの例外で、他の場所。  
  
-   <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>の子オブジェクトはのみ参照、<xref:System.Windows.Controls.ControlTemplate>です。 場合<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>が指定されていない、アニメーションを対象とする要素、<xref:System.Windows.Controls.ControlTemplate>を適用します。  
  
-   <xref:System.Windows.EventTrigger.SourceName%2A>の<xref:System.Windows.EventTrigger>または<xref:System.Windows.Trigger>の子オブジェクトはのみ参照、<xref:System.Windows.Controls.ControlTemplate>です。  
  
-   動的リソース参照やデータ バインディング式を使用して設定することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーションのプロパティの値。 内部のすべて、 <xref:System.Windows.Controls.ControlTemplate> 、スレッド セーフである必要がありますタイミング システムにする必要があります<xref:System.Windows.Freezable.Freeze%2A><xref:System.Windows.Media.Animation.Storyboard>スレッド セーフであるようにするオブジェクト。 A<xref:System.Windows.Media.Animation.Storyboard>またはその子タイムラインに動的なリソースの参照やデータ バインディング式が含まれている場合に固定することはできません。 固定やその他の詳細については<xref:System.Windows.Freezable>機能を参照してください、 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)です。  
  
-   [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、用のイベント ハンドラーを宣言することはできません<xref:System.Windows.Media.Animation.Storyboard>またはアニメーション イベント。  
  
 内のストーリー ボードを定義する方法を示す例については、<xref:System.Windows.Controls.ControlTemplate>を参照してください、 [、ControlTemplate のアニメーション](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)例です。  
  
<a name="animateWhenAPropertyValueChanges"></a>   
## <a name="animate-when-a-property-value-changes"></a>プロパティ値が変化したときにアニメーション化を行う  
 スタイル内およびコントロール テンプレート内では、トリガー オブジェクトを使用して、プロパティが変化したときにストーリーボードを開始します。 例については、次を参照してください。 [、アニメーションときに、プロパティ値の変更をトリガー](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)と[、ControlTemplate のアニメーション](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-in-a-controltemplate.md)です。  
  
 プロパティによって適用されたアニメーション<xref:System.Windows.Trigger>オブジェクトよりも複雑な方法で動作しますが<xref:System.Windows.EventTrigger>アニメーションまたはアニメーションを使用して開始<xref:System.Windows.Media.Animation.Storyboard>メソッドです。  「ハンドオフ」アニメーションを使用して他の定義、<xref:System.Windows.Trigger>使用して、オブジェクトが作成<xref:System.Windows.EventTrigger>およびアニメーションのメソッドによってトリガーされます。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)  
 [Freezable オブジェクトの概要](../../../../docs/framework/wpf/advanced/freezable-objects-overview.md)
