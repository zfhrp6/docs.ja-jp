---
title: タイミング動作の概要
ms.date: 03/30/2017
helpviewer_keywords:
- timing behaviors [WPF]
- behaviors [WPF], timing
ms.assetid: 5b714d46-bd46-48b8-b467-b4be89ba3091
ms.openlocfilehash: 31a6b7d3b92e886d9c90fc39d69f31cf72b99666
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
---
# <a name="timing-behaviors-overview"></a>タイミング動作の概要
このトピックには、アニメーション、およびその他のタイミング動作がについて説明します<xref:System.Windows.Media.Animation.Timeline>オブジェクト。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 このトピックを理解するには、基本的なアニメーション機能に精通している必要があります。 詳細については、次を参照してください。、[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)です。  
  
<a name="timelinetypes"></a>   
## <a name="timeline-types"></a>タイムラインの型  
 A<xref:System.Windows.Media.Animation.Timeline>時間のセグメントを表します。 用意されているプロパティを使用して、そのセグメントの長さ、開始時間、繰り返し回数、時間の進行の速度などを指定できます。  
  
 Timeline クラスを継承するクラスには、アニメーションやメディアの再生などの追加機能が用意されています。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] 次に示します<xref:System.Windows.Media.Animation.Timeline>型です。  
  
|タイムラインの型|説明|  
|-------------------|-----------------|  
|<xref:System.Windows.Media.Animation.AnimationTimeline>|抽象基本クラス<xref:System.Windows.Media.Animation.Timeline>プロパティのアニメーションの出力値を生成するオブジェクト。|  
|<xref:System.Windows.Media.MediaTimeline>|メディア ファイルから出力を生成します。|  
|<xref:System.Windows.Media.Animation.ParallelTimeline>|型<xref:System.Windows.Media.Animation.TimelineGroup>そのグループやコントロールの子<xref:System.Windows.Media.Animation.Timeline>オブジェクト。|  
|<xref:System.Windows.Media.Animation.Storyboard>|型<xref:System.Windows.Media.Animation.ParallelTimeline>が含まれているタイムライン オブジェクトの対象とする情報を提供します。|  
|<xref:System.Windows.Media.Animation.Timeline>|タイミング動作を定義する抽象基本クラス。|  
|<xref:System.Windows.Media.Animation.TimelineGroup>|抽象クラス<xref:System.Windows.Media.Animation.Timeline>他を含めることができるオブジェクト<xref:System.Windows.Media.Animation.Timeline>オブジェクト。|  
  
<a name="propertiesthatcontroltimelinelength"></a>   
## <a name="properties-that-control-the-length-of-a-timeline"></a>タイムラインの長さを制御するプロパティ  
 A<xref:System.Windows.Media.Animation.Timeline>を表しますが、時間のセグメントと、タイムラインの長さは、さまざまな方法で記述できます。 タイムラインの長さを示すいくつかの用語の定義を次の表に示します。  
  
|用語|説明|プロパティ||||  
|----------|-----------------|----------------|-|-|-|  
|単純継続時間|タイムラインが順方向の反復を 1 回完了するのに要する時間の長さ。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>||||  
|1 回の繰り返し|タイムラインとし、再生するにかかる時間の長さ、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティが true の場合、旧バージョンと 1 回再生します。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>, <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>||||  
|アクティブ期間|タイムラインで指定されたすべての繰り返しを完了するにかかる時間の長さ、<xref:System.Windows.Media.Animation.RepeatBehavior>プロパティです。|<xref:System.Windows.Media.Animation.Timeline.Duration%2A>、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>、<xref:System.Windows.Media.Animation.RepeatBehavior>||||  
  
<a name="duration"></a>   
### <a name="the-duration-property"></a>Duration プロパティ  
 既に述べたように、タイムラインは時間のセグメントを表します。 そのセグメントの長さは、タイムラインのによって決まります<xref:System.Windows.Media.Animation.Timeline.Duration%2A>です。 タイムラインは、期間の最後に到達すると、再生を停止します。 タイムラインに子タイムラインがある場合は、子も再生を停止します。 アニメーションの場合、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションにかかる時間の遷移の終了値をその開始値からを指定します。 タイムラインの期間と呼ぶことがその*単純な期間*、1 つのイテレーションの期間と繰り返しを含む、アニメーションの再生時間の長さの合計とを区別します。 有限の時刻の値または特別な値を使用して期間を指定することができます<xref:System.Windows.Duration.Automatic%2A>または<xref:System.Windows.Duration.Forever%2A>です。 アニメーションの継続時間に解決する必要があります、<xref:System.Windows.Duration.TimeSpan%2A>値であるため、値の間に移行できます。  
  
 次の例は、<xref:System.Windows.Media.Animation.DoubleAnimation>で、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 5 秒間です。  
  
 [!code-xaml[animation_ovws_snippet#AnimationWith5SecondDurationInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#animationwith5seconddurationinline)]  
  
 コンテナー タイムラインなど<xref:System.Windows.Media.Animation.Storyboard>と<xref:System.Windows.Media.Animation.ParallelTimeline>の既定の時間が指定されて<xref:System.Windows.Duration.Automatic%2A>、つまり、これらは、最後の子が停止したときに自動的に終了します。 次の例は、<xref:System.Windows.Media.Animation.Storyboard>が<xref:System.Windows.Media.Animation.Timeline.Duration%2A>5 秒間、すべての子にかかる時間の長さに解決される<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトが完了します。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelineexampleinline)]  
  
 設定して、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>するコンテナ タイムラインの<xref:System.Windows.Duration.TimeSpan%2A>長いまたはその子よりも短い再生を強制できます値、<xref:System.Windows.Media.Animation.Timeline>オブジェクトで再生します。 設定した場合、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>コンテナ タイムラインの子のサイズよりも小さい値に<xref:System.Windows.Media.Animation.Timeline>オブジェクト、子<xref:System.Windows.Media.Animation.Timeline>オブジェクトを実行するコンテナ タイムラインの再生を停止します。 次の例のセット、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>の<xref:System.Windows.Media.Animation.Storyboard>3 秒間に、前の例からです。 その結果、最初の<xref:System.Windows.Media.Animation.DoubleAnimation>ターゲット四角形の幅を 60 にアニメーション化されたときに、3 秒後に処理を停止します。  
  
 [!code-xaml[animation_ovws_snippet#ContainerTimelineWithShorterDurationExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#containertimelinewithshorterdurationexampleinline)]  
  
<a name="repeatinganimations"></a>   
### <a name="the-repeatbehavior-property"></a>RepeatBehavior プロパティ  
 <xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>一定時間の再生が繰り返される回数を制御します。 使用して、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティ、何回タイムラインの再生を指定することができます (イテレーション<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>) またはを再生時間の長さの合計 (繰り返し<xref:System.Windows.Media.Animation.RepeatBehavior.Duration%2A>)。 いずれの場合も、アニメーションは、要求されたカウントまたは期間を満たすのに必要な回数だけ実行を繰り返します。 既定では、タイムラインがのイテレーション数をある`1.0`つまり、1 回再生し、はまったく繰り返されません。  
  
 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>反復回数を指定することによって、2 回一定時間の再生します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior2xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior2xexampleinline)]  
  
 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>一定時間の半分を再生します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehavior05xExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehavior05xexampleinline)]  
  
 設定した場合、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>のプロパティ、<xref:System.Windows.Media.Animation.Timeline>に<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>、<xref:System.Windows.Media.Animation.Timeline>対話形式またはタイミング システムで停止するまで繰り返されます。 次の例では、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.DoubleAnimation>無期限に再生します。  
  
 [!code-xaml[animation_ovws_snippet#TBRepeatBehaviorForeverExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbrepeatbehaviorforeverexampleinline)]  
  
 たとえば、次を参照してください。[アニメーションを繰り返す](../../../../docs/framework/wpf/graphics-multimedia/how-to-repeat-an-animation.md)です。  
  
<a name="autoreverseproperty"></a>   
### <a name="the-autoreverse-property"></a>AutoReverse プロパティ  
 <xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティを指定するかどうか、<xref:System.Windows.Media.Animation.Timeline>前方各イテレーションの最後に逆方向に再生されます。 次の例を設定、<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>のプロパティ、<xref:System.Windows.Media.Animation.DoubleAnimation>に`true`その結果、100、0 とゼロに 100 をアニメーション化します。 合計 10 秒間再生されます。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverseexampleinline)]  
  
 使用する場合、<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>を指定する値、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>の<xref:System.Windows.Media.Animation.Timeline>と<xref:System.Windows.Media.Animation.Timeline.AutoReverse%2A>プロパティの<xref:System.Windows.Media.Animation.Timeline>は`true`、1 つの繰り返しから成る 1 つ前方反復処理後に 1 つ下位のイテレーション。  次の例のセット、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>の<xref:System.Windows.Media.Animation.DoubleAnimation>を前の例から、<xref:System.Windows.Media.Animation.RepeatBehavior.Count%2A>の 2 つです。 その結果、 <xref:System.Windows.Media.Animation.DoubleAnimation> 20 秒の再生: に対する、5 秒の旧バージョンと、5 秒間の転送を 5 秒間に、もう一度転送し、旧バージョンとを 5 秒間です。  
  
 [!code-xaml[animation_ovws_snippet#TBAutoReverseRepeatExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbautoreverserepeatexampleinline)]  
  
 コンテナーのタイムラインに子がある場合<xref:System.Windows.Media.Animation.Timeline>オブジェクトを実行するコンテナ タイムラインが反転します。 その他の例では、次を参照してください。[を指定するかどうか、タイムラインを自動的に反転](../../../../docs/framework/wpf/graphics-multimedia/how-to-specify-whether-a-timeline-automatically-reverses.md)です。  
  
<a name="timelinebegin"></a>   
## <a name="the-begintime-property"></a>BeginTime プロパティ  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>プロパティでは、タイムラインを開始するときに指定することができます。  タイムラインの開始時間は、親タイムラインを基準とした相対値になります。 開始時間を 0 秒に設定すると、タイムラインはその親が開始されると直ちに開始されます。その他の値に設定すると、親タイムラインの再生開始時点と子タイムラインの再生時点の間のオフセットが作成されます。 たとえば、開始時間を 2 秒に設定すると、タイムラインは、その親が 2 秒の時点に到達すると再生を開始します。 既定では、すべてのタイムラインの開始時間は 0 秒です。 タイムラインの設定も開始する時刻が`null`タイムラインが起動できなくなります。 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]を使用して null を指定する、 [X:null マークアップ拡張機能](../../../../docs/framework/xaml-services/x-null-markup-extension.md)します。  
  
 ために、タイムラインが繰り返されますたびに、適用される開始時間、<xref:System.Windows.Media.Animation.Timeline.RepeatBehavior%2A>設定します。 アニメーションを作成する場合は、 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 10 秒および<xref:System.Windows.Media.Animation.RepeatBehavior>の<xref:System.Windows.Media.Animation.RepeatBehavior.Forever%2A>アニメーションは、初めてのではなく連続する各繰り返し再生される前に、10 秒遅延にするとします。 ただし、アニメーションの親タイムラインの再開または繰り返しが行われた場合は、10 秒の遅延が発生します。  
  
 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A>プロパティは、タイムラインをずらすことに役立ちます。 次の例を作成、 <xref:System.Windows.Media.Animation.Storyboard> 2 つの子を持つ<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクト。 最初のアニメーションが、 <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 、5 秒間の 2 番目と、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>を 3 秒です。 例のセット、 <xref:System.Windows.Media.Animation.Timeline.BeginTime%2A> 、2 つ目の<xref:System.Windows.Media.Animation.DoubleAnimation>5 (秒単位) をそのためこと再生が開始後、最初に<xref:System.Windows.Media.Animation.DoubleAnimation>を終了します。  
  
 [!code-xaml[animation_ovws_snippet#TBBeginTimeExampleInline](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbbegintimeexampleinline)]  
  
<a name="fillbehaviorproperty"></a>   
## <a name="the-fillbehavior-property"></a>FillBehavior プロパティ  
 ときに、<xref:System.Windows.Media.Animation.Timeline>がその合計のアクティブな期間の最後に達すると、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティは、停止するか、最後の値を保持するかどうかを指定します。 アニメーションを<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>"値を保持する"出力: アニメーション化されているプロパティは、アニメーションの最後の値を保持します。 値<xref:System.Windows.Media.Animation.FillBehavior.Stop>終了後、ターゲット プロパティに影響を与えず、アニメーションが停止するとします。  
  
 次の例を作成、 <xref:System.Windows.Media.Animation.Storyboard> 2 つの子を持つ<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクト。 両方<xref:System.Windows.Media.Animation.DoubleAnimation>オブジェクトをアニメーション化する、<xref:System.Windows.FrameworkElement.Width%2A>の<xref:System.Windows.Shapes.Rectangle>0 ~ 100 です。 <xref:System.Windows.Shapes.Rectangle>要素がアニメーション化されていない<xref:System.Windows.FrameworkElement.Width%2A>500 [デバイス非依存ピクセル] の値。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>最初の<xref:System.Windows.Media.Animation.DoubleAnimation>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>既定値です。 四角形の幅が後に 100 に保持する結果として、<xref:System.Windows.Media.Animation.DoubleAnimation>を終了します。  
  
-   <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> 2 番目のプロパティ<xref:System.Windows.Media.Animation.DoubleAnimation>に設定されている<xref:System.Windows.Media.Animation.FillBehavior.Stop>です。 その結果、 <xref:System.Windows.FrameworkElement.Width%2A> 、2 つ目の<xref:System.Windows.Shapes.Rectangle>500 の後に元に戻します、<xref:System.Windows.Media.Animation.DoubleAnimation>を終了します。  
  
 [!code-xaml[animation_ovws_snippet#TBFillBehaviorExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/animation_ovws_snippet/CS/TimingBehaviorsExample1.xaml#tbfillbehaviorexample)]  
  
<a name="speedproperties"></a>   
## <a name="properties-that-control-the-speed-of-a-timeline"></a>タイムラインの速度を制御するプロパティ  
 <xref:System.Windows.Media.Animation.Timeline>クラスの速度を指定する 3 つのプロパティを提供します。  
  
-   <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A> – 指定の時間の進行を親に対してそのレート、<xref:System.Windows.Media.Animation.Timeline>です。 1 より大きい値の処理速度の向上、<xref:System.Windows.Media.Animation.Timeline>とその子<xref:System.Windows.Media.Animation.Timeline>オブジェクト以外の値は 0 ~ 1 速度が低下することです。 1 つの値が示す<xref:System.Windows.Media.Animation.Timeline>親と同じ速度で進行します。 <xref:System.Windows.Media.Animation.Timeline.SpeedRatio%2A>コンテナ タイムラインの設定は、その子の<xref:System.Windows.Media.Animation.Timeline>オブジェクトもします。  
  
-   <xref:System.Windows.Media.Animation.Timeline.AccelerationRatio%2A> – の割合を指定する、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>タイムラインの費やした加速します。 例については、次を参照してください。[する方法: 加速または減速アニメーション](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md)です。 
  
-   <xref:System.Windows.Media.Animation.Timeline.DecelerationRatio%2A> -指定の割合、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>タイムラインの費やした減速します。 例については、次を参照してください。[する方法: 加速または減速アニメーション](../../../../docs/framework/wpf/graphics-multimedia/how-to-accelerate-or-decelerate-an-animation.md)です。  
  
## <a name="see-also"></a>関連項目  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)  
 [タイミング イベントの概要](../../../../docs/framework/wpf/graphics-multimedia/timing-events-overview.md)  
 [方法トピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)  
 [アニメーションのタイミング動作のサンプル](http://go.microsoft.com/fwlink/?LinkID=159970)
