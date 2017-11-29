---
title: "プロパティ アニメーションの手法の概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- animation [WPF], properties [WPF], methods for
- properties [WPF], methods for animating
ms.assetid: 74f61413-f8c0-4e75-bf04-951886426c8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1a8c196ea15617b13abe8311f8501ab32fd320c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 11/21/2017
---
# <a name="property-animation-techniques-overview"></a>プロパティ アニメーションの手法の概要
このトピックでは、ストーリーボード、ローカル アニメーション、クロック、フレームごとのアニメーションなど、プロパティをアニメーション化するさまざまなアプローチについて説明します。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」で説明されている基本のアニメーション機能に精通している必要があります。  
  
<a name="summary"></a>   
## <a name="different-ways-to-animate"></a>さまざまなアニメーション化方法  
 プロパティをアニメーション化するには多数のシナリオがあるため、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ではプロパティをアニメーション化するいくつかの方法が提供されます。  
  
 それぞれの方法について、インスタンス単位、スタイル内、コントロール テンプレート内、またはデータ テンプレート内で使用できるかどうか、[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] で使用できるかどうか、およびアニメーションを対話的に制御できるかどうかを次の表に示します。  "インスタンス単位" とは、スタイル、コントロール テンプレート、またはデータ テンプレート内のインスタンスではなく、オブジェクトのインスタンスに直接アニメーションまたはストーリーボードを適用する方法のことです。  
  
|アニメーションの手法|シナリオ|XAML のサポート|対話的に制御可能|  
|-------------------------|---------------|-------------------|--------------------------------|  
|ストーリー ボード アニメーション|インスタンスごとの<xref:System.Windows.Style>、 <xref:System.Windows.Controls.ControlTemplate>、<xref:System.Windows.DataTemplate>|はい|はい|  
|ローカル アニメーション|インスタンス単位|いいえ|いいえ|  
|クロック アニメーション|インスタンス単位|いいえ|はい|  
|フレーム単位のアニメーション|インスタンス単位|いいえ|N/A|  
  
<a name="storyboard_animations"></a>   
## <a name="storyboard-animations"></a>ストーリー ボード アニメーション  
 使用して、<xref:System.Windows.Media.Animation.Storyboard>を定義し、アニメーションを適用する場合[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]対話形式で、開始、アニメーションの複雑なツリーを作成またはでアニメーション化後、アニメーションの制御、 <xref:System.Windows.Style>、<xref:System.Windows.Controls.ControlTemplate>または<xref:System.Windows.DataTemplate>です。 オブジェクトをアニメーションを実行するため、 <xref:System.Windows.Media.Animation.Storyboard>、する必要があります、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>を設定するために使用する必要がありますか、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 詳しくは、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」をご覧ください。  
  
 A<xref:System.Windows.Media.Animation.Storyboard>特殊な種類のコンテナーは、<xref:System.Windows.Media.Animation.Timeline>が含まれているアニメーションの対象とする情報を提供します。 使用してアニメーション化、 <xref:System.Windows.Media.Animation.Storyboard>、次の 3 つの手順を完了します。  
  
1.  宣言、<xref:System.Windows.Media.Animation.Storyboard>と 1 つまたは複数のアニメーション。  
  
2.  使用して、<xref:System.Windows.Media.Animation.Storyboard.TargetName%2A>と<xref:System.Windows.Media.Animation.Storyboard.TargetProperty%2A>ターゲット オブジェクトを指定するプロパティとそれぞれのアニメーションのプロパティを添付します。  
  
3.  (コードのみ)定義、<xref:System.Windows.NameScope>の<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 使用してアニメーション化するオブジェクトの名前を登録<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。  
  
4.  開始、<xref:System.Windows.Media.Animation.Storyboard>です。  
  
 以降、<xref:System.Windows.Media.Animation.Storyboard>アニメーション化するプロパティにアニメーションを適用し、それらを開始します。 開始する 2 つの方法、 <xref:System.Windows.Media.Animation.Storyboard>: 使用することができます、<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>によって提供されるメソッド、<xref:System.Windows.Media.Animation.Storyboard>を使用するか、クラス、<xref:System.Windows.Media.Animation.BeginStoryboard>アクション。 唯一の方法でアニメーション化する[!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]を使用して、<xref:System.Windows.Media.Animation.BeginStoryboard>アクション。 A<xref:System.Windows.Media.Animation.BeginStoryboard>でアクションを使用できます、 <xref:System.Windows.EventTrigger>、プロパティ<xref:System.Windows.Trigger>、または<xref:System.Windows.DataTrigger>です。  
  
 次の表は、さまざまな場所を示しています。 ここで各<xref:System.Windows.Media.Animation.Storyboard>開始手法はサポートされて: インスタンスごとに、スタイル、コントロール テンプレート、およびデータ テンプレート。  
  
|ストーリーボードが開始される場所|インスタンス単位|スタイル|コントロール テンプレート|データ テンプレート|例|  
|--------------------------------|-------------------|-----------|----------------------|-------------------|-------------|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>および<xref:System.Windows.EventTrigger>|はい|はい|はい|はい|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>プロパティ名<xref:System.Windows.Trigger>|いいえ|はい|はい|はい|[プロパティ値が変化したときにアニメーションをトリガーする](../../../../docs/framework/wpf/graphics-multimedia/how-to-trigger-an-animation-when-a-property-value-changes.md)|  
|<xref:System.Windows.Media.Animation.BeginStoryboard>および<xref:System.Windows.DataTrigger>|いいえ|はい|はい|はい|[方法: データが変化したときにアニメーションをトリガーする](http://msdn.microsoft.com/en-us/a736bb3a-2ae5-479a-a33a-75a27055d863)|  
|<xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッド|はい|いいえ|いいえ|いいえ|[ストーリーボードを使ってプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-by-using-a-storyboard.md)|  
  
 詳細については<xref:System.Windows.Media.Animation.Storyboard>、オブジェクトを参照してください、[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)です。  
  
## <a name="local-animations"></a>ローカル アニメーション  
 任意の依存関係プロパティをアニメーション化する便利な手段を提供するローカル アニメーション<xref:System.Windows.Media.Animation.Animatable>オブジェクト。 プロパティに適用するアニメーションが 1 つだけであり、アニメーションを開始後に対話的に制御する必要がない場合は、ローカル アニメーションを使用します。 異なり、<xref:System.Windows.Media.Animation.Storyboard>アニメーション、ローカルのアニメーションに関連付けられていないオブジェクトのアニメーションできます、<xref:System.Windows.FrameworkElement>または<xref:System.Windows.FrameworkContentElement>です。 する必要はありません定義、<xref:System.Windows.NameScope>この種類のアニメーションのです。  
  
 ローカル アニメーションはコードだけで使用できます。スタイル、コントロール テンプレート、またはデータ テンプレート内では定義できません。 ローカル アニメーションは、開始後に対話的に制御できません。  
  
 ローカル アニメーションを使用してアニメーション化するには、次の手順を実行します。  
  
1.  作成、<xref:System.Windows.Media.Animation.AnimationTimeline>オブジェクト。  
  
2.  使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>を適用するアニメーション化するオブジェクトのメソッド、<xref:System.Windows.Media.Animation.AnimationTimeline>を指定するプロパティです。  
  
 次の例の幅と背景色をアニメーション化する方法を示しています、<xref:System.Windows.Controls.Button>です。  
  
 [!code-cpp[animateproperty#11](../../../../samples/snippets/cpp/VS_Snippets_Wpf/animateproperty/CPP/LocalAnimationExample.cpp#11)]
 [!code-csharp[animateproperty#11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animateproperty/CSharp/LocalAnimationExample.cs#11)]
 [!code-vb[animateproperty#11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/animateproperty/VisualBasic/LocalAnimationExample.vb#11)]  
  
## <a name="clock-animations"></a>クロック アニメーション  
 使用して<xref:System.Windows.Media.MediaPlayer.Clock%2A>オブジェクトを使用せずにアニメーション化する時に、<xref:System.Windows.Media.Animation.Storyboard>複雑なタイミング ツリーを作成または開始してから、アニメーションを対話的に制御するとします。 クロック オブジェクトを使用するには任意の依存関係プロパティをアニメーション化する<xref:System.Windows.Media.Animation.Animatable>オブジェクト。  
  
 使用することはできません<xref:System.Windows.Media.Animation.Clock>オブジェクト直接スタイルでアニメーション化を制御するテンプレート、またはデータのテンプレートです。 (実際には、アニメーションおよびタイミング システムを使用して<xref:System.Windows.Media.Animation.Clock>スタイル、コントロール テンプレート、およびデータ テンプレートがアニメーション化するオブジェクトは、それを作成する必要があります<xref:System.Windows.Media.Animation.Clock>からのオブジェクト、<xref:System.Windows.Media.Animation.Storyboard>です。 間のリレーションシップの詳細については<xref:System.Windows.Media.Animation.Storyboard>オブジェクトおよび<xref:System.Windows.Media.Animation.Clock>、オブジェクトを参照してください、[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md))。  
  
 1 つを適用する<xref:System.Windows.Media.Animation.Clock>プロパティには次の手順を実行します。  
  
1.  作成、<xref:System.Windows.Media.Animation.AnimationTimeline>オブジェクト。  
  
2.  使用して、<xref:System.Windows.Media.Animation.AnimationTimeline.CreateClock%2A>のメソッド、<xref:System.Windows.Media.Animation.AnimationTimeline>を作成する、<xref:System.Windows.Media.Animation.AnimationClock>です。  
  
3.  使用して、<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>を適用するアニメーション化するオブジェクトのメソッド、<xref:System.Windows.Media.Animation.AnimationClock>を指定するプロパティにします。  
  
 次の例を作成する方法を示しています、<xref:System.Windows.Media.Animation.AnimationClock>し、同様の 2 つのプロパティに適用します。  
  
 [!code-csharp[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/csharp/VS_Snippets_Wpf/timingbehaviors_procedural_snip/CSharp/AnimationClockExample.cs#graphicsmmcreateanimationclockwholeclass)]
 [!code-vb[timingbehaviors_procedural_snip#GraphicsMMCreateAnimationClockWholeClass](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/timingbehaviors_procedural_snip/visualbasic/animationclockexample.vb#graphicsmmcreateanimationclockwholeclass)]  
  
 タイミング ツリーを作成し、これを使用してプロパティをアニメーション化するには、次の手順を実行します。  
  
1.  使用して<xref:System.Windows.Media.Animation.ParallelTimeline>と<xref:System.Windows.Media.Animation.AnimationTimeline>タイミング ツリーを作成するオブジェクト。  
  
2.  使用して、<xref:System.Windows.Media.Animation.TimelineGroup.CreateClock%2A>ルートの<xref:System.Windows.Media.Animation.ParallelTimeline>を作成する、<xref:System.Windows.Media.Animation.ClockGroup>です。  
  
3.  反復処理する、<xref:System.Windows.Media.Animation.ClockGroup.Children%2A>の<xref:System.Windows.Media.Animation.ClockGroup>とその子を適用<xref:System.Windows.Media.Animation.Clock>オブジェクト。 各<xref:System.Windows.Media.Animation.AnimationClock>子を使用して、<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%2A>を適用するアニメーション化するオブジェクトのメソッド、<xref:System.Windows.Media.Animation.AnimationClock>を指定するプロパティを  
  
 Clock オブジェクトについて詳しくは、「[アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)」をご覧ください。  
  
## <a name="per-frame-animation-bypass-the-animation-and-timing-system"></a>フレーム単位アニメーション: アニメーションとタイミング システムのバイパス  
 この方法は、[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] アニメーション システムを完全にバイパスする必要がある場合に使用します。 この方法の 1 つのシナリオは、アニメーションの各ステップで、オブジェクトの最後の一連のやり取りに基づいてオブジェクトの再計算が必要になる物理アニメーションです。  
  
 フレーム単位アニメーションは、スタイル、コントロール テンプレート、またはデータ テンプレート内で定義できません。  
  
 フレームごと、アニメーション化するに登録する、<xref:System.Windows.Media.CompositionTarget.Rendering>をアニメーション化するオブジェクトを含むオブジェクトのイベントです。 このイベント ハンドラー メソッドは、フレームごとに 1 回呼び出されます。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] がビジュアル ツリーの永続化されたレンダリング データを構成ツリーにマーシャリングするたびに、イベント ハンドラー メソッドが呼び出されます。  
  
 イベント ハンドラーでは、アニメーション効果に必要なあらゆる計算を実行し、これらの値を使用してアニメーション化するオブジェクトのプロパティを設定します。  
  
 現在のフレームのプレゼンテーションの時間を取得する、<xref:System.EventArgs>これに関連付けられているイベントとしてキャストできます<xref:System.Windows.Media.RenderingEventArgs>、的な<xref:System.Windows.Media.RenderingEventArgs.RenderingTime%2A>を現在のフレームを取得するのに使用できるプロパティの時間をレンダリングします。  
  
 詳細については、次を参照してください。、<xref:System.Windows.Media.CompositionTarget.Rendering>ページ。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [依存関係プロパティの概要](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
