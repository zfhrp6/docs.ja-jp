---
title: "アニメーションの概要 | Microsoft Docs"
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
  - "ストーリー ボード [WPF] アニメーション"
  - "アニメーション [WPF], 概要"
ms.assetid: bd9ce563-725d-4385-87c9-d7ee38cf79ea
caps.latest.revision: 73
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 73
---
# アニメーションの概要
<a name="introduction"></a>[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)]魅力的なユーザー インターフェイスやドキュメントを作成するためのグラフィックスとレイアウトの機能の強力なセットを提供します。 アニメーションより傑作と使用可能な魅力的なユーザー インターフェイスを行うことができます。 背景色をアニメーション化することも、アニメーションを適用して<xref:System.Windows.Media.Transform>、劇的な画面の遷移を作成したり、役立つ視覚的な手掛かりを提供します。  
  
 この概要について説明する、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーションおよびタイミング システムです。 アニメーションに焦点を当てます[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]のストーリー ボードを使用して、オブジェクトです。  

<a name="introducinganimations"></a>   
## <a name="introducing-animations"></a>アニメーションの概要  
 アニメーションは、一連の最後からそれぞれに異なるイメージをすばやく切り替えることによって作成されるフィルターの種類です。 脳は、1 つの変化するシーンとしてイメージのグループを認識します。 映画では、この錯覚は&1; 秒あたりに多数の写真またはフレームを記録するカメラを使用して作成されます。 フレームを映写機で再生すると、見る人には動く画像として映ります。  
  
 コンピューター上のアニメーションは似ています。 たとえば、見えない四角形のフェードの描画を行うプログラムがとおり動作する可能性があります。  
  
-   プログラムでは、タイマーを作成します。  
  
-   プログラムでは、どれ時間だけが経過して設定された間隔でタイマーを確認します。  
  
-   プログラムは、タイマーをチェックインするたびに、どれ時間だけが経過時間に基づいて、四角形の不透明度の現在の値を計算します。  
  
-   プログラムは、新しい値を持つ四角形を更新し、再描画します。  
  
 前のバージョン[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、[!INCLUDE[TLA#tla_win](../../../../includes/tlasharptla-win-md.md)]開発者を作成し、タイミング システムを管理または特殊なカスタム ライブラリを使用する必要があります。                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]マネージ コードによって公開される効率的なタイミング システムを含むと[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]密接に統合されていると、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]フレームワークです。                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーションを簡単にコントロールやその他のグラフィカル オブジェクトをアニメーション化します。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]すべてのバック グラウンド処理のタイミング システムを管理して、画面を効率的に再描画を処理します。 それらの効果を実現するためのメカニズムではなく、作成する効果に重点を有効にするタイミング クラスを提供します。                  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]容易に、クラスが継承できるアニメーションの基本クラスを公開することで、独自のアニメーションを作成する、カスタマイズされたアニメーションを作成します。 これらのカスタム アニメーションは、標準のアニメーション クラスのパフォーマンスの利点の多くを取得します。  
  
<a name="thewpftimingsystem"></a>   
## <a name="wpf-property-animation-system"></a>WPF プロパティ アニメーション システム  
 タイミング システムに関するいくつかの重要な概念を理解している場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]アニメーションを使用する方が簡単にできることができます。 最も重要なは、 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]、個々 のプロパティにアニメーションを適用することでオブジェクトをアニメーション化します。 たとえば、拡張フレームワーク要素をするためには、アニメーション化する、<xref:System.Windows.FrameworkElement.Width%2A>と<xref:System.Windows.FrameworkElement.Height%2A>プロパティです。 アニメーション化するのには非表示オブジェクト、その<xref:System.Windows.UIElement.Opacity%2A>プロパティです。  
  
 アニメーション機能を持つをプロパティには、次の&3; つの要件を満たす必要があります。  
  
-   依存関係プロパティがあります。  
  
-   継承するクラスに属する必要があります<xref:System.Windows.DependencyObject>を実装し、 <xref:System.Windows.Media.Animation.IAnimatable>インターフェイスです。  
  
-   互換性のあるアニメーションの種類を使用可能なあります。 (場合[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]は提供されていない、独自に作成することができます。 参照してください、[カスタム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md))。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]持つ多くのオブジェクトを含む<xref:System.Windows.Media.Animation.IAnimatable>プロパティです。 などのコントロール<xref:System.Windows.Controls.Button>と<xref:System.Windows.Controls.TabControl>、さらに<xref:System.Windows.Controls.Panel>と<xref:System.Windows.Shapes.Shape>オブジェクトから継承<xref:System.Windows.DependencyObject>します。 それらのプロパティの大部分は、依存関係プロパティです。  
  
 使用できるアニメーションほぼ任意の場所をスタイルおよびコントロール テンプレートが含まれます。 アニメーションを視覚的にする必要はありません。このセクションで説明されている条件を満たしている場合、ユーザー インターフェイスの一部ではないオブジェクトをアニメーション化することができます。  
  
<a name="storyboardwalkthrough"></a>   
## <a name="example-make-an-element-fade-in-and-out-of-view"></a>例: 要素のフェードインとフェードアウトを行う  
 この例では、使用して、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]依存関係プロパティの値をアニメーション化するアニメーションです。 使用して、 <xref:System.Windows.Media.Animation.DoubleAnimation>、これは、型を生成するアニメーションの<xref:System.Double>をアニメーション化する、値、<xref:System.Windows.UIElement.Opacity%2A>のプロパティ、<xref:System.Windows.Shapes.Rectangle>します。 結果として、<xref:System.Windows.Shapes.Rectangle>ビューから消えます。  
  
 この例の最初の部分を作成、<xref:System.Windows.Shapes.Rectangle>要素。 以下の手順は、アニメーションを作成し、四角形に適用する方法を示します<xref:System.Windows.UIElement.Opacity%2A>プロパティです。  
  
 作成する方法を次に示します、<xref:System.Windows.Shapes.Rectangle>内の要素、 <xref:System.Windows.Controls.StackPanel> XAML でします。  
  
 [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_1)]  
  
 作成する方法を次に示します、<xref:System.Windows.Shapes.Rectangle>内の要素、 <xref:System.Windows.Controls.StackPanel>コードにします。  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_1)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_1)]  
  
<a name="opacity_animation_step1"></a>   
### <a name="part-1-create-a-doubleanimation"></a>第 1 部: DoubleAnimation を作成します。  
 フェードアウト要素を&1; つの方法がアニメーション化するのには、<xref:System.Windows.UIElement.Opacity%2A>プロパティです。 <xref:System.Windows.UIElement.Opacity%2A>プロパティの型は<xref:System.Double>、double 値を生成するアニメーションを作成する必要があります。 A <xref:System.Windows.Media.Animation.DoubleAnimation>はこのような&1; つのアニメーションです。 A <xref:System.Windows.Media.Animation.DoubleAnimation>&2; つの倍精度値間の遷移が作成されます。 設定した開始値を指定するには、その<xref:System.Windows.Media.Animation.DoubleAnimation.From%2A>プロパティです。 設定する終了値を指定するには、その<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>プロパティです。  
  
1.  Opacity の値を`1.0`完全に不透明なオブジェクトとの不透明度の値は、`0.0`完全に非表示になります。 To make the animation transition from                                  `1.0` to                                  `0.0` you set its                                  <xref:System.Windows.Media.Animation.DoubleAnimation.From%2A> property to                                  `1.0` and its                                  <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> property to                                  `0.0`. 作成する方法を次に示します、 <xref:System.Windows.Media.Animation.DoubleAnimation> XAML でします。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_2)]  
  
     作成する方法を次に示します、 <xref:System.Windows.Media.Animation.DoubleAnimation>コードにします。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_2)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_2)]  
  
2.  次に、指定する必要があります、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>します。 <xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションの開始値から、送信先の値に移動にかかる時間を指定します。 設定する方法を次に示します、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>XAML で&5; 秒にします。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_3)]  
  
     設定する方法を次に示します、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>コード内で&5; 秒にします。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_3)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_3)]  
  
3.  前のコードではから移行するアニメーションを示しました`1.0`に`0.0`、それが原因で、ターゲット要素から完全に不透明な完全に非表示にフェードアウトします。 一度フェードインが消えた後要素をクリックすると、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティをアニメーションの`true`です。 アニメーションを無限に繰り返すするためには、次のように設定します。 その<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>します。設定する方法を次に示します、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>と<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A> XAML でのプロパティです。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_4)]  
  
     設定する方法を次に示します、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>と<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>コード内のプロパティです。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Class1.cs#rectangleopacityfadeexamplecode_4)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/Class1.vb#rectangleopacityfadeexamplecode_4)]  
  
<a name="opacity_animation_step2"></a>   
### <a name="part-2-create-a-storyboard"></a>第 2 部: ストーリー ボードの作成  
 作成するオブジェクトにアニメーションを適用するに、<xref:System.Windows.Media.Animation.Storyboard>を使用して、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>オブジェクトを指定するプロパティとアニメーション化するプロパティをアタッチします。  
  
1.  作成、<xref:System.Windows.Media.Animation.Storyboard>し、その子として、アニメーションを追加します。 作成する方法を次に示します、<xref:System.Windows.Media.Animation.Storyboard>XAML でします。  
  
     <!-- TODO: review snippet reference [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_5)]  -->  
  
     作成する、<xref:System.Windows.Media.Animation.Storyboard>コードでは、宣言、<xref:System.Windows.Media.Animation.Storyboard>クラス レベルの変数です。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_100)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_100)]  
  
     初期化して、<xref:System.Windows.Media.Animation.Storyboard>し、その子として、アニメーションを追加します。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_101)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_101](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_101)]  
  
2.  <xref:System.Windows.Media.Animation.Storyboard>アニメーションを適用する場所を知っていなければなりません。 使用して、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A?displayProperty=fullName>添付プロパティをアニメーション化するオブジェクトを指定します。 次のターゲットの名前を設定する方法を示しています、 <xref:System.Windows.Media.Animation.DoubleAnimation>に`MyRectangle`XAML でします。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_6)]  
  
     ターゲットの名前を設定する方法を次に示します、 <xref:System.Windows.Media.Animation.DoubleAnimation>に`MyRectangle`コードにします。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_102)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_102](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_102)]  
  
3.  使用して、<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>添付プロパティをアニメーション化するプロパティを指定します。 アニメーションを構成する方法を次に示しますターゲットに、<xref:System.Windows.UIElement.Opacity%2A>のプロパティ、<xref:System.Windows.Shapes.Rectangle>XAML でします。  
  
     [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml_7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/Window1.xaml#rectangleopacityfadeexamplexaml_7)]  
  
     アニメーションを構成する方法を次に示しますターゲットに、<xref:System.Windows.UIElement.Opacity%2A>のプロパティ、<xref:System.Windows.Shapes.Rectangle>コードにします。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_103)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_103](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_103)]  
  
 詳細については<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>構文とその他の例を参照してください、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)します。  
  
<a name="opacity_animation_step3"></a>   
### <a name="part-3-xaml-associate-the-storyboard-with-a-trigger"></a>パート 3 (XAML): トリガーでストーリー ボードの関連付け  
 最も簡単な方法を適用し、開始、<xref:System.Windows.Media.Animation.Storyboard>で[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]イベント トリガーを使用することです。                          このセクションに関連付ける方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>XAML でのトリガーです。  
  
1.  作成、 <xref:System.Windows.Media.Animation.BeginStoryboard>オブジェクトし、ストーリー ボードを関連付けます。 A <xref:System.Windows.Media.Animation.BeginStoryboard>の種類は、 <xref:System.Windows.TriggerAction>を適用し、開始、<xref:System.Windows.Media.Animation.Storyboard>します。  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_3)]  
  
2.  作成、 <xref:System.Windows.EventTrigger>を追加し、 <xref:System.Windows.Media.Animation.BeginStoryboard>にその<xref:System.Windows.EventTrigger.Actions%2A>コレクションです。 設定、 <xref:System.Windows.EventTrigger.RoutedEvent%2A>のプロパティ、 <xref:System.Windows.EventTrigger>をルーティングされたイベントを開始するには<xref:System.Windows.Media.Animation.Storyboard>します。 (ルーティング イベントの詳細については、次を参照してください、[ルーティング イベントの概要](../../../../docs/framework/wpf/advanced/routed-events-overview.md)。)。  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_2)]  
  
3.  追加、 <xref:System.Windows.EventTrigger>に、<xref:System.Windows.FrameworkElement.Triggers%2A>四角形のコレクション。  
  
     [!code-xml[animation_ovws_snippet#RectangleOpacityFadeExampleInline_1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/RectangleOpacityFadeExample.xaml#rectangleopacityfadeexampleinline_1)]  
  
<a name="opacity_animation_step3code"></a>   
### <a name="part-3-code-associate-the-storyboard-with-an-event-handler"></a>イベント ハンドラーを持つストーリー ボードの作業 3 (コード): 関連付け  
 最も簡単な方法を適用し、開始、<xref:System.Windows.Media.Animation.Storyboard>コードでは、イベント ハンドラーを使用します。 このセクションに関連付ける方法を示しています、<xref:System.Windows.Media.Animation.Storyboard>をコードでイベント ハンドラーです。  
  
1.  登録、 <xref:System.Windows.FrameworkElement.Loaded>四角形のイベントです。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_104)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_104](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_104)]  
  
2.  イベント ハンドラーを宣言します。 イベント ハンドラーで使用して、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>ストーリー ボードを適用するメソッドです。  
  
     [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode_105)]
     [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode_105](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode_105)]  
  
### <a name="complete-example"></a>コード例全体  
 XAML でビューから消えますを四角形を作成する方法を次に示します。  
  
 [!code-xml[animation_ovws2#RectangleOpacityFadeExampleXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml#rectangleopacityfadeexamplexaml)]  
  
 表示と非表示のコードにフェードする四角形を作成する方法を次に示します。  
  
 [!code-csharp[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws2/CSharp/MainWindow.xaml.cs#rectangleopacityfadeexamplecode)]
 [!code-vb[animation_ovws2#RectangleOpacityFadeExampleCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws2/VisualBasic/MainWindow.xaml.vb#rectangleopacityfadeexamplecode)]  
  
<a name="animationtypes"></a>   
## <a name="animation-types"></a>アニメーションの種類  
 アニメーションは、プロパティの値を生成するため、プロパティの種類別のアニメーションの種類が存在します。 受け取るプロパティをアニメーション化する、<xref:System.Double>など、<xref:System.Windows.FrameworkElement.Width%2A>、要素のプロパティを生成するアニメーションを使用して<xref:System.Double>値。 受け取るプロパティをアニメーション化する、<xref:System.Windows.Point>、生成されるアニメーションを使用して<xref:System.Windows.Point>値、およびなどです。 種類のプロパティの数のためには、いくつかのアニメーション クラスは、 <xref:System.Windows.Media.Animation>名前空間。 幸いにも、それらはそれらを区別しやすく厳密な名前付け規則に従います。  
  
-   \<                         *型*> アニメーション  
  
     「から/に/者」または"basic"アニメーションと呼ばれ、これらをアニメーション化を開始し、移行先の値の間、または、開始値にオフセット値を追加することで。  
  
    -   開始値を指定するには、アニメーションの From プロパティを設定します。  
  
    -   終了値を指定するには、アニメーションの To プロパティを設定します。  
  
    -   オフセットの値を指定するには、アニメーションの By プロパティを設定します。  
  
     この概要の例は、最も簡単に使用されるため、これらのアニメーションを使用します。 From/を/、アニメーションは From/To/By アニメーションの概要で詳細に説明します。  
  
-   \<                         *型*> AnimationUsingKeyFrames  
  
     キー フレーム アニメーションは、任意の数のターゲット値を指定しても、補間方法を制御するので、/アニメーションよりも強力です。 一部の種類は、キー フレーム アニメーションをアニメーション化するだけです。 キー フレーム アニメーションがで詳しく説明されている、[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)します。  
  
-   \<                         *型*> AnimationUsingPath  
  
     パス アニメーションを使用すると、ジオメトリック パスをアニメーション化された値を生成するために使用できます。  
  
-   \<                         *型*> AnimationBase  
  
     実装するときにアニメーション化する抽象クラス、 <> \</>*型*> 値。 このクラスの基本クラスとして機能<>*型*> アニメーションと<>*型*> AnimationUsingKeyFrames クラスです。 ユーザー独自のアニメーションを作成する場合にのみ、これらのクラスを直接扱う必要があります。 それ以外の場合を使用して、 <> \</>*型*> アニメーションまたはキーフレーム<>*型*> アニメーションです。  
  
 ほとんどの場合、使用する場合は、 <> \</>*型*> などのアニメーション クラス<xref:System.Windows.Media.Animation.DoubleAnimation>と<xref:System.Windows.Media.Animation.ColorAnimation>します。  
  
 次の表は、いくつかの一般的なアニメーションの種類と使用するいくつかのプロパティを示します。  
  
|プロパティの型|対応する (から/に/By) 基本アニメーション|対応するキー フレーム アニメーション|対応するパスのアニメーション|使用例|  
|-------------------|----------------------------------------------------|---------------------------------------|----------------------------------|-------------------|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimation>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|なし|Animate the                                  <xref:System.Windows.Media.SolidColorBrush.Color%2A> of a                                  <xref:System.Windows.Media.SolidColorBrush> or a                                  <xref:System.Windows.Media.GradientStop>.|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimation>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingPath>|Animate the                                  <xref:System.Windows.FrameworkElement.Width%2A> of a                                  <xref:System.Windows.Controls.DockPanel> or the                                  <xref:System.Windows.FrameworkElement.Height%2A> of a                                  <xref:System.Windows.Controls.Button>.|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimation>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|<xref:System.Windows.Media.Animation.PointAnimationUsingPath>|アニメーション化する、 <xref:System.Windows.Media.EllipseGeometry.Center%2A>の位置、 <xref:System.Windows.Media.EllipseGeometry>します。|  
|<xref:System.String>|なし|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|なし|Animate the                                  <xref:System.Windows.Controls.TextBlock.Text%2A> of a                                  <xref:System.Windows.Controls.TextBlock> or the                                  <xref:System.Windows.Controls.ContentControl.Content%2A> of a                                  <xref:System.Windows.Controls.Button>.|  
  
<a name="animationsaretimelines"></a>   
### <a name="animations-are-timelines"></a>アニメーションはタイムライン  
 すべてのアニメーションの型を継承、<xref:System.Windows.Media.Animation.Timeline>クラスはそのため、すべてのアニメーション タイムラインの特殊な型です。 A<xref:System.Windows.Media.Animation.Timeline>時間のセグメントを定義します。 指定できます、*タイミング動作*のタイムラインの: その<xref:System.Windows.Media.Animation.Timeline.Duration%2A>の繰り返しと偶数の速さ時間の進行が何回です。  
  
 アニメーションがあるため、<xref:System.Windows.Media.Animation.Timeline>時間のセグメントもを表します。 しかし時間の指定されたセグメントで進行状況に合わせて出力値が、アニメーションによっても計算 (または<xref:System.Windows.Media.Animation.Timeline.Duration%2A>)。 アニメーション、または「再生」、関連付けられているプロパティを更新します。  
  
 次の&3; つのタイミングを頻繁に使用されるプロパティは、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>、および<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>します。  
  
#### <a name="the-duration-property"></a>Duration プロパティ  
 既に述べたようには、タイムラインは、時間のセグメントを表します。 そのセグメントの長さはによって決まります、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>通常を使用して指定されると、タイムラインの<xref:System.Windows.Duration.TimeSpan%2A>値。 タイムラインには、その期間の最後に達すると、イテレーションが完了しました。  
  
 アニメーションを使用してその<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティを現在の値を決定します。 指定しない場合、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>値、アニメーションの既定値は、1 秒間を使用します。  
  
 次の構文の簡略版を示しています、[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]属性の構文、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティです。  
  
||  
|-|  
|*hours* `:` *minutes* `:` *seconds*|  
  
 次の表にいくつか示します<xref:System.Windows.Duration>設定とその結果として得られる値です。  
  
|設定|結果の値|  
|-------------|---------------------|  
|0:0:5.5|5.5 秒です。|  
|0:30:5.5|30 分、5.5 秒です。|  
|1:30:5.5|1 時間、30 分、および 5.5 秒です。|  
  
 指定する方法の&1; つ、<xref:System.Windows.Duration>コードでは使用する、 <xref:System.TimeSpan.FromSeconds%2A>を作成する方法、 <xref:System.TimeSpan>を宣言し、新しい<xref:System.Windows.Duration>が使用している構造体<xref:System.TimeSpan>します。  
  
 詳細については<xref:System.Windows.Duration>値と完全な[!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]構文を参照してください、<xref:System.Windows.Duration>構造体。  
  
#### <a name="autoreverse"></a>AutoReverse  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティは、タイムラインの末尾に達した後再生旧バージョンとするかどうかを指定します。 その<xref:System.Windows.Media.Animation.Timeline.Duration%2A>します。 このアニメーションのプロパティを設定する場合`true`の末尾に達すると、アニメーションを反転させますその<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、開始値に戻す終了値から再生します。 このプロパティは、既定では、`false`です。  
  
#### <a name="repeatbehavior"></a>RepeatBehavior  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティは、タイムラインの再生回数を指定します。 既定では、タイムラインがのイテレーション数をある`1.0`つまり、いずれかを果たすことが時間し、はまったく繰り返されません。  
  
 これらのプロパティおよびその他の詳細については、次を参照してください。、[タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)します。  
  
<a name="applyanimationstoproperty"></a>   
## <a name="applying-an-animation-to-a-property"></a>プロパティにアニメーションを適用します。  
 前のセクションでは、さまざまな種類のアニメーションとタイミング プロパティについて説明します。 このセクションでは、アニメーションをアニメーション化するプロパティに適用する方法を示します。                  <xref:System.Windows.Media.Animation.Storyboard>オブジェクト プロパティにアニメーションを適用する&1; つの方法を提供します。 A<xref:System.Windows.Media.Animation.Storyboard>は、*コンテナー タイムライン*が含まれているアニメーションのターゲットの情報を提供します。  
  
### <a name="targeting-objects-and-properties"></a>ターゲット オブジェクトとプロパティ  
 <xref:System.Windows.Media.Animation.Storyboard>クラスには、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>アタッチされるプロパティです。 これらのプロパティを設定するには、アニメーションを指示できますアニメーションにアニメーションを作成します。 ただし、アニメーションは、オブジェクトをターゲット、前にオブジェクト必要があります通常する名前を指定します。  
  
 名前が割り当てられて、 <xref:System.Windows.FrameworkElement>に名前の割り当てとは異なります、 <xref:System.Windows.Freezable>オブジェクトです。 ほとんどのコントロールとパネルは framework 要素です。ただし、ブラシ、変換、およびジオメトリなどのほとんどの純粋なグラフィカル オブジェクトは、freezable オブジェクトです。 わからないことを確認するかどうか、型の場合、 <xref:System.Windows.FrameworkElement>または<xref:System.Windows.Freezable>を参照してください、**継承階層**のリファレンス ドキュメントのセクションです。  
  
-   させる、 <xref:System.Windows.FrameworkElement>をアニメーションのターゲットを名前を設定してその<xref:System.Windows.FrameworkElement.Name%2A>プロパティです。 コードでは、必要がありますも使用する、 <xref:System.Windows.FrameworkElement.RegisterName%2A>が所属するページに要素名を登録する方法です。  
  
-   させる、 <xref:System.Windows.Freezable>オブジェクトをアニメーションのターゲットで[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用する、 [X:name ディレクティブ](../../../../docs/framework/xaml-services/x-name-directive.md)名前を指定します。 使用するだけのコードでは、 <xref:System.Windows.FrameworkElement.RegisterName%2A>が所属するページで、オブジェクトを登録します。  
  
 以降のセクションでは、内の要素の名前を付ける例を示す[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]とコードです。 名前付けおよびターゲット設定の詳細については、次を参照してください。、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)します。  
  
### <a name="applying-and-starting-storyboards"></a>適用して、ストーリー ボードの開始  
 ストーリー ボードを起動する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]、関連付けること、 <xref:System.Windows.EventTrigger>します。 <xref:System.Windows.EventTrigger>は、特定のイベントが発生したときに実行するアクションを記述するオブジェクト。 これらのアクションのいずれかを指定できます、 <xref:System.Windows.Media.Animation.BeginStoryboard>アクションを使用して、ストーリー ボードを開始します。 イベント トリガーは、アプリケーションが特定のイベントに応答する方法を指定することができるのでイベント ハンドラーに概念は似ています。 イベント トリガーで完全に記述するイベント ハンドラーとは異なり[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]; 他のコードは必要ありません。  
  
 開始する、<xref:System.Windows.Media.Animation.Storyboard>コードでは、使用することができます、 <xref:System.Windows.EventTrigger>か使用して、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>のメソッド、<xref:System.Windows.Media.Animation.Storyboard>クラスです。  
  
<a name="controllingstoryboards"></a>   
## <a name="interactively-control-a-storyboard"></a>ストーリー ボードを対話的に制御します。  
 前の例で開始する方法、<xref:System.Windows.Media.Animation.Storyboard>イベントが発生します。 対話形式で制御することができます、<xref:System.Windows.Media.Animation.Storyboard>開始後に: 一時停止、再開、停止、保留期間に進めること、シーク、および削除できます、<xref:System.Windows.Media.Animation.Storyboard>します。 詳細については、対話的に制御する方法を示す例の<xref:System.Windows.Media.Animation.Storyboard>を参照してください、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)します。  
  
<a name="fillbehaviorsection"></a>   
## <a name="what-happens-after-an-animation-ends"></a>アニメーションの終了後どうなりますか。  
 <xref:System.Windows.Media.Animation.FillBehavior>プロパティは、それが終了すると、タイムラインの動作を指定します。 既定では、タイムラインが開始<xref:System.Windows.Media.Animation.ClockState>終了します。 あるアニメーション<xref:System.Windows.Media.Animation.ClockState>その最終的な出力値を保持します。  
  
 <xref:System.Windows.Media.Animation.DoubleAnimation>前の例では終了しませんので、 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>にプロパティが設定されている<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>します。 次の例では、類似のアニメーションを使用して、四角形をアニメーション化します。 前の例とは異なり、 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>と<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>このアニメーションのプロパティは既定値のままです。 したがって、アニメーションは 0 まで 5 秒間で 1 から進行して停止します。  
  
 [!code-xml[animation_ovws_snippet#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/FillBehaviorExample.xaml#fillbehaviorexamplerectangleinline)]  
  
 [!code-csharp[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_procedural_snip/CSharp/FillBehaviorExample.cs#fillbehaviorexamplerectangleinline)]
 [!code-vb[animation_ovws_procedural_snip#FillBehaviorExampleRectangleInline](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animation_ovws_procedural_snip/visualbasic/fillbehaviorexample.vb#fillbehaviorexamplerectangleinline)]  
  
 その<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>が、これは既定値から変更されていない<xref:System.Windows.Media.Animation.FillBehavior>アニメーションを保持して、最終的な値は 0、それが終了するとします。 したがって、<xref:System.Windows.UIElement.Opacity%2A>の四角形は、アニメーションの後の 0 から終了します。 設定した場合、<xref:System.Windows.UIElement.Opacity%2A>、別の値に四角形のコードが何効果、アニメーションがまだに影響を与えるため、<xref:System.Windows.UIElement.Opacity%2A>プロパティです。  
  
 コードでアニメーションのプロパティの制御を回復する方法の&1; つを使用して、 <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッド null を指定して、 <xref:System.Windows.Media.Animation.AnimationTimeline>パラメーター。 詳細と例では、次を参照してください。[設定、プロパティの後のアニメーション ストーリー ボードを](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)します。  
  
 持つプロパティの値を設定するが、 <xref:System.Windows.Media.Animation.ClockState>または<xref:System.Windows.Media.Animation.ClockState>アニメーションは効果がない、プロパティの値は変更できます。 詳細については、次を参照してください。、[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)します。  
  
<a name="databindingAndAnimatingAnimationsSection"></a>   
## <a name="data-binding-and-animating-animations"></a>データ バインドやアニメーションをアニメーション化  
 ほとんどのアニメーション プロパティは、データ バインドやアニメーション化を指定できます。たとえば、アニメーション化できます、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>のプロパティ、 <xref:System.Windows.Media.Animation.DoubleAnimation>します。 ただし、タイミング システムが動作する方法のため、データ バインドやアニメーションのアニメーションが他のデータと同様に動作しない場合はバインドされているか、オブジェクトをアニメーション化します。 その動作を理解するには、アニメーションをプロパティに適用する意味を理解すると役立ちます。  
  
 アニメーション化する方法を説明しました。 前のセクションで例を参照してください、<xref:System.Windows.UIElement.Opacity%2A>四角形のです。 そのイベント トリガーを適用前の例では、四角形が読み込まれるときに、<xref:System.Windows.Media.Animation.Storyboard>します。 タイミング システムのコピーを作成する、<xref:System.Windows.Media.Animation.Storyboard>およびそのアニメーションです。 これらのコピーが固定されている (読み取り専用に行われます) と<xref:System.Windows.Media.Animation.Clock>からオブジェクトが作成されます。 これらのクロックは、対象のプロパティをアニメーション化する実際の作業を実行します。  
  
 タイミング システム用の時計の作成、 <xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトとで指定されたプロパティに適用し、 <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>の<xref:System.Windows.Media.Animation.DoubleAnimation>します。 タイミング システムにクロックを適用する場合は、<xref:System.Windows.UIElement.Opacity%2A>「続きとしてです」というオブジェクトのプロパティ。  
  
 クロックはの作成もされますが、<xref:System.Windows.Media.Animation.Storyboard>クロックは、任意のプロパティには適用されません。 その目的は、その子のクロックに作成される、時計を制御する、 <xref:System.Windows.Media.Animation.DoubleAnimation>します。  
  
 データ バインドやアニメーションの変更を反映するアニメーション、その時計を再生成する必要があります。 クロックは、自動的のするは再生成されません。 アニメーションの変更を反映するために、そのストーリー ボードを再適用を使用して、 <xref:System.Windows.Media.Animation.BeginStoryboard>または<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドです。 これらのメソッドのいずれかを使用すると、アニメーションが再起動されます。 コードでは、使用することができます、 <xref:System.Windows.Media.Animation.Storyboard.Seek%2A>ストーリー ボードをシフトするメソッドは、前の位置にバックアップします。  
  
 データの例には、アニメーションがバインドされている、参照してください[キー スプライン アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160011)します。                  アニメーションとタイミング システムの動作の詳細については、次を参照してください。[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)します。  
  
<a name="otherWaysToAnimateSection"></a>   
## <a name="other-ways-to-animate"></a>その他の方法をアニメーション化します。  
 この概要の例では、ストーリー ボードを使用してアニメーション化する方法を示します。 コードを使用すると、その他のいくつかの方法でアニメーション化できます。 詳細については、次を参照してください。、[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)します。  
  
<a name="animation_samples"></a>   
## <a name="animation-samples"></a>アニメーションのサンプル  
 次の例では、アプリケーションにアニメーションの追加を開始できます。  
  
-   [From、To、およびアニメーションのターゲット値のサンプルで](http://go.microsoft.com/fwlink/?LinkID=159988)  
  
     別の/を/で設定を示します。  
  
-   [アニメーションのタイミング動作のサンプル](http://go.microsoft.com/fwlink/?LinkID=159970)  
  
     アニメーションの動作のタイミングを制御するさまざまな方法を示します。 このサンプルも示していますバインドする方法、アニメーションの終了値。  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a>関連トピック  
  
|タイトル|説明|  
|-----------|-----------------|  
|[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)|タイミング システムの使用方法について説明します<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>クラスで、アニメーションを作成することです。|  
|[アニメーションのヒントと秘訣](../../../../docs/framework/wpf/graphics-multimedia/animation-tips-and-tricks.md)|アニメーションでは、パフォーマンスなどの問題を解決するための役に立つヒントを一覧表示します。|  
|[カスタム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/custom-animations-overview.md)|キー フレームで、アニメーション クラス、またはフレームごとのコールバックを使用してアニメーション システムを拡張する方法について説明します。|  
|From/To/By アニメーションの概要|2 つの値の間を遷移するアニメーションを作成する方法について説明します。|  
|[キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)|補間方法を制御する機能など、複数のターゲット値を持つアニメーションを作成する方法について説明します。|  
|[イージング関数](../../../../docs/framework/wpf/graphics-multimedia/easing-functions.md)|数式をバウンスなどの現実的な動作を実現する、アニメーションに適用する方法について説明します。|  
|[パス アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/path-animations-overview.md)|移動または複雑なパスに沿ってオブジェクトを回転する方法について説明します。|  
|[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)|プロパティのアニメーションのストーリー ボードを使用して、ローカル アニメーション、時計、およびアニメーションのフレームごとのについて説明します。|  
|[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)|複数のタイムラインでストーリー ボードを使用して、複雑なアニメーションを作成する方法について説明します。|  
|[タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)|説明、<xref:System.Windows.Media.Animation.Timeline>型およびアニメーションで使用されるプロパティです。|  
|[タイミング イベントの概要](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)|使用できるイベントについて説明します、<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Clock>など、タイムラインの時点でコードを実行するためのオブジェクトを開始、一時停止、再開、スキップ、または停止します。|  
|[操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)|アプリケーションでのアニメーションおよびタイムラインを使用するためのコード例を示します。|  
|[クロックの操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/clocks-how-to-topics.md)|使用するコード例を含む、<xref:System.Windows.Media.Animation.Clock>アプリケーション内のオブジェクト。|  
|[キー フレームの操作方法に関するトピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)|アプリケーションでキー フレーム アニメーションを使用するためのコード例を示します。|  
|[パス アニメーションに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/path-animation-how-to-topics.md)|パス アニメーションを使用して、アプリケーションのためのコード例が含まれています。|  
  
<a name="reference"></a>   
## <a name="reference"></a>参照  
 <xref:System.Windows.Media.Animation.Timeline>  
  
 <xref:System.Windows.Media.Animation.Storyboard>  
  
 <xref:System.Windows.Media.Animation.BeginStoryboard>  
  
 <xref:System.Windows.Media.Animation.Clock>