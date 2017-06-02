---
title: "プロパティ アニメーションの手法の概要 | Microsoft Docs"
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
  - "アニメーション, プロパティ, 手法"
  - "プロパティ, 手法 (アニメーションの)"
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# プロパティ アニメーションの手法の概要
ここでは、ストーリーボード、ローカル アニメーション、クロック、フレーム単位のアニメーションなど、プロパティをアニメーション化するためのさまざまな方法を示します。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="prerequisites"></a>   
## 必要条件  
 このトピックを理解するには、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」で説明されている基本的なアニメーション機能に精通している必要があります。  
  
<a name="summary"></a>   
## アニメーション化のための各種方法  
 プロパティのアニメーション化には多数の異なるシナリオがあるため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] では、プロパティをアニメーション化するために複数の方法を利用できます。  
  
 それぞれの方法について、インスタンス単位、スタイル内、コントロール テンプレート内、またはデータ テンプレート内で使用できるかどうか、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で使用できるかどうか、およびアニメーションを対話的に制御できるかどうかを次の表に示します。  "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。  
  
|アニメーションの手法|シナリオ|XAML のサポート|対話的に制御可能|  
|----------------|----------|----------------|--------------|  
|ストーリーボード アニメーション|インスタンス単位、<xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.DataTemplate>|○|○|  
|ローカル アニメーション|インスタンス単位|Ｘ|Ｘ|  
|クロック アニメーション|インスタンス単位|Ｘ|○|  
|フレーム単位のアニメーション|インスタンス単位|Ｘ|N\/A|  
  
<a name="storyboard_animations"></a>   
## ストーリーボード アニメーション  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でアニメーションを定義して適用する場合、アニメーションを開始後に対話的に制御する場合、アニメーションの複雑なツリーを作成する場合、または <xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.DataTemplate> でアニメーション化する場合は、<xref:System.Windows.Media.Animation.Storyboard> を使用します。  <xref:System.Windows.Media.Animation.Storyboard> によってアニメーション化するオブジェクトについては、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> である必要があります。あるいは、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> を設定するために使用されている必要があります。  詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 <xref:System.Windows.Media.Animation.Storyboard> はコンテナー <xref:System.Windows.Media.Animation.Timeline> の特殊な型であり、含まれる複数のアニメーションの対象情報を持っています。  <xref:System.Windows.Media.Animation.Storyboard> を使用してアニメーション化するには、次の 3 つの手順を実行します。  
  
1.  <xref:System.Windows.Media.Animation.Storyboard> および 1 つ以上のアニメーションを宣言します。  
  
2.  <xref:System.Windows.Media.Animation.Storyboard.TargetName%2A> [添付プロパティ](GTMT)および <xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A> 添付プロパティを使用して、各アニメーションのターゲット オブジェクトおよびプロパティを指定します。  
  
3.  \(コードのみ\) <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> の <xref:System.Windows.NameScope> を定義します。  アニメーション化するオブジェクトの名前を、その <xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> に登録します。  
  
4.  <xref:System.Windows.Media.Animation.Storyboard> を開始します。  
  
 <xref:System.Windows.Media.Animation.Storyboard> を開始すると、アニメーションがアニメーション化するプロパティに適用され、開始されます。  <xref:System.Windows.Media.Animation.Storyboard> を開始するには、2 とおりの方法があります。<xref:System.Windows.Media.Animation.Storyboard> クラスによって提供される <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用するか、<xref:System.Windows.Media.Animation.BeginStoryboard> アクションを使用します。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] でアニメーション化するには、<xref:System.Windows.Media.Animation.BeginStoryboard> アクションを使用する以外に方法はありません。A <xref:System.Windows.Media.Animation.BeginStoryboard> アクションは、<xref:System.Windows.EventTrigger>、<xref:System.Windows.Trigger> プロパティ、または <xref:System.Windows.DataTrigger> で使用できます。  
  
 各 <xref:System.Windows.Media.Animation.Storyboard> の開始方法がサポートされているさまざまな場所、インスタンス単位、スタイル、コントロール テンプレート、およびデータ テンプレートを次の表に示します。  
  
|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|  
|----------------------|--------------|----------|-------------------|----------------|-------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.EventTrigger>|○|○|○|○|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.Trigger> プロパティ|Ｘ|○|○|○|[プロパティ値が変化したときにアニメーションをトリガーする](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard> および <xref:System.Windows.DataTrigger>|Ｘ|○|○|○|[How to: Trigger an Animation When Data Changes](http://msdn.microsoft.com/ja-jp/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|○|Ｘ|Ｘ|Ｘ|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 <xref:System.Windows.Media.Animation.Storyboard> オブジェクトの詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
## ローカル アニメーション  
 ローカル アニメーションは、任意の <xref:System.Windows.Media.Animation.Animatable> オブジェクトの[依存関係プロパティ](GTMT)をアニメーション化するための便利な方法を提供します。  プロパティに適用するアニメーションが 1 つだけであり、アニメーションを開始後に対話的に制御する必要がない場合は、ローカル アニメーションを使用します。  <xref:System.Windows.Media.Animation.Storyboard> アニメーションとは異なり、ローカル アニメーションは、<xref:System.Windows.FrameworkElement> または <xref:System.Windows.FrameworkContentElement> に関連付けられていないオブジェクトをアニメーション化できます。  この種類のアニメーションには <xref:System.Windows.NameScope> を定義する必要はありません。  
  
 ローカル アニメーションはコードだけで使用できます。スタイル、コントロール テンプレート、またはデータ テンプレート内では定義できません。  ローカル アニメーションは、開始後に対話的に制御できません。  
  
 ローカル アニメーションを使用してアニメーション化するには、次の手順を実行します。  
  
1.  <xref:System.Windows.Media.Animation.AnimationTimeline> オブジェクトを作成します。  
  
2.  アニメーション化するオブジェクトの <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用して、指定するプロパティに <xref:System.Windows.Media.Animation.AnimationTimeline> を適用します。  
  
 <xref:System.Windows.Controls.Button> の幅および背景色をアニメーション化する方法を次の例に示します。  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## クロック アニメーション  
 <xref:System.Windows.Media.Animation.Storyboard> を使用せずにアニメーション化する際に、複雑なタイミング ツリーを作成する場合、またはアニメーションを開始後に対話的に制御する場合は、<xref:System.Windows.Media.MediaPlayer.Clock%2A> オブジェクトを使用します。  Clock オブジェクトを使用すると、任意の <xref:System.Windows.Media.Animation.Animatable> オブジェクトの[依存関係プロパティ](GTMT)をアニメーション化できます。  
  
 <xref:System.Windows.Media.Animation.Clock> オブジェクトは、スタイル、コントロール テンプレート、またはデータ テンプレート内で直接アニメーション化するために使用することはできません   \(アニメーションとタイミング システムは、実際に <xref:System.Windows.Media.Animation.Clock> オブジェクトを使用して、スタイル、コントロール テンプレート、およびデータ テンプレート内でアニメーション化しますが、そのためには、これらの <xref:System.Windows.Media.Animation.Clock> オブジェクトを <xref:System.Windows.Media.Animation.Storyboard> から作成する必要があります。  <xref:System.Windows.Media.Animation.Storyboard> オブジェクトと <xref:System.Windows.Media.Animation.Clock> オブジェクトの関係の詳細については、「[アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)」を参照してください。  
  
 プロパティに 1 つの <xref:System.Windows.Media.Animation.Clock> を適用するには、次の手順を実行します。  
  
1.  <xref:System.Windows.Media.Animation.AnimationTimeline> オブジェクトを作成します。  
  
2.  <xref:System.Windows.Media.Animation.AnimationTimeline> の <xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A> メソッドを使用して <xref:System.Windows.Media.Animation.AnimationClock> を作成します。  
  
3.  アニメーション化するオブジェクトの <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> メソッドを使用して、指定するプロパティに <xref:System.Windows.Media.Animation.AnimationClock> を適用します。  
  
 <xref:System.Windows.Media.Animation.AnimationClock> を作成し、2 つの類似するプロパティにこれを適用する方法を次の例に示します。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 タイミング ツリーを作成し、これを使用してプロパティをアニメーション化するには、次の手順を実行します。  
  
1.  <xref:System.Windows.Media.Animation.ParallelTimeline> オブジェクトと <xref:System.Windows.Media.Animation.AnimationTimeline> オブジェクトを使用して、タイミング ツリーを作成します。  
  
2.  ルート <xref:System.Windows.Media.Animation.ParallelTimeline> の <xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A> を使用して <xref:System.Windows.Media.Animation.ClockGroup> を作成します。  
  
3.  <xref:System.Windows.Media.Animation.ClockGroup> の <xref:System.Windows.Media.Animation.ClockGroup.Children%2A> を反復処理し、その子 <xref:System.Windows.Media.Animation.Clock> オブジェクトを適用します。  子 <xref:System.Windows.Media.Animation.AnimationClock> ごとに、アニメーション化するオブジェクトの <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A> メソッドを使用して、指定するプロパティに <xref:System.Windows.Media.Animation.AnimationClock> を適用します。  
  
 Clock オブジェクトの詳細については、「[アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)」を参照してください。  
  
## フレーム単位アニメーション : アニメーションとタイミング システムのバイパス  
 この方法は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要がある場合に使用します。  この方法の 1 つのシナリオは、アニメーションの各ステップで、オブジェクトの最後の一連のやり取りに基づいてオブジェクトの再計算が必要になる物理アニメーションです。  
  
 フレーム単位アニメーションは、スタイル、コントロール テンプレート、またはデータ テンプレート内で定義できません。  
  
 フレームごとにアニメーション化するには、アニメーション化するオブジェクトを格納しているオブジェクトの <xref:System.Windows.Media.CompositionTarget.Rendering> イベントで登録します。  このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。  [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] が[ビジュアル ツリー](GTMT)の永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームの表現時間を取得するには、このイベントに関連付けられている <xref:System.EventArgs> を、<xref:System.Windows.Media.RenderingEventArgs> としてキャストできます。これにより、現在のフレームのレンダリング時間を取得するために使用できる <xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A> プロパティが提供されます。  
  
 詳細については、<xref:System.Windows.Media.CompositionTarget.Rendering> のページを参照してください。  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)   
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)