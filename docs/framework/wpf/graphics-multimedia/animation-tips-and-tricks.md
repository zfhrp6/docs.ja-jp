---
title: "アニメーションのヒントとテクニック"
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
helpviewer_keywords:
- troubleshooting [WPF], animation
- animations [WPF], FillBehavior property
- troubleshooting animation [WPF]
- animating objects [WPF], troubleshooting
- animation tips and tricks [WPF]
- tips and tricks [WPF], animation
- performance troubleshooting [WPF], animation
- animations [WPF], use of system resources
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 210f8ff8840f579d352cc579f80f38488b998c5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 01/19/2018
---
# <a name="animation-tips-and-tricks"></a>アニメーションのヒントとテクニック
アニメーションを使用するときに[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]がいくつかのヒント、およびアニメーションできるようにするトリックはパフォーマンスを向上させ、苛立ちを保存します。  
  
<a name="generalissuessection"></a>   
## <a name="general-issues"></a>一般的な問題  
  
### <a name="animating-the-position-of-a-scroll-bar-or-slider-freezes-it"></a>スクロール バーまたはスライダーの位置をアニメーション化するとフリーズする  
 スクロール バーやスライダーを持つアニメーションを使用しての位置をアニメーション化する場合、<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.HoldEnd>(既定値) の場合は、ユーザーが使用できなくにスクロール バーやスライダーを移動します。 原因は、アニメーションが終了しても、ターゲット プロパティの基底値をまだオーバーライドしているためです。 プロパティの現在の値をオーバーライドするアニメーションを停止するには、削除するか、付与、<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。 例および詳細については、次を参照してください。 [、プロパティの後にアニメーション化するように設定にストーリー ボード](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)です。  
  
### <a name="animating-the-output-of-an-animation-has-no-effect"></a>アニメーションの出力のアニメーション化の効果がない  
 別のアニメーションの出力であるオブジェクトをアニメーション化することはできません。 たとえば、使用する場合、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>アニメーション化する、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>から、<xref:System.Windows.Media.RadialGradientBrush>を<xref:System.Windows.Media.SolidColorBrush>のプロパティをアニメーション化することはできません、<xref:System.Windows.Media.RadialGradientBrush>または<xref:System.Windows.Media.SolidColorBrush>です。  
  
### <a name="cant-change-the-value-of-a-property-after-animating-it"></a>プロパティをアニメーション化した後にその値を変更できない  
 場合によっては、アニメーションが完了した後でも、アニメーション化の後にプロパティの値を変更できないように見えることがあります。 原因は、アニメーションが終了しても、プロパティの基底値をまだオーバーライドしているためです。 プロパティの現在の値をオーバーライドするアニメーションを停止するには、削除するか、付与、<xref:System.Windows.Media.Animation.FillBehavior>の<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。 例および詳細については、次を参照してください。 [、プロパティの後にアニメーション化するように設定にストーリー ボード](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)です。  
  
### <a name="changing-a-timeline-has-no-effect"></a>タイムラインを変更しても効果がない  
 ほとんど<xref:System.Windows.Media.Animation.Timeline>プロパティは、アニメーション可能なデータ バインドできます、アクティブなプロパティ値を変更する<xref:System.Windows.Media.Animation.Timeline>効果がないように見えます。 ときに、<xref:System.Windows.Media.Animation.Timeline>はの開始タイミング システムでのコピーを作成、<xref:System.Windows.Media.Animation.Timeline>作成を使用して、<xref:System.Windows.Media.Animation.Clock>オブジェクト。 元を変更しても、システムのコピーには影響しません。  
  
 <xref:System.Windows.Media.Animation.Timeline>に変更を反映するには、そのクロック必要がありますは再生成し、以前に作成したクロックを置き換えるために使用します。 クロックは、自動的には再生成されません。 タイムラインの変更を適用するいくつかの方法を次に示します。  
  
-   タイムラインがまたはに属している場合、 <xref:System.Windows.Media.Animation.Storyboard>、ストーリー ボードを使用して、再適用して変更を反映してこれを行うことができます、<xref:System.Windows.Media.Animation.BeginStoryboard>または<xref:System.Windows.Media.Animation.Storyboard.Begin%2A>メソッドです。 これには、アニメーションが再起動されるという副作用があります。 コードでは、使用することができます、<xref:System.Windows.Media.Animation.Storyboard.Seek%2A>ストーリー ボードを進める方法は、前の位置にバックアップします。  
  
-   プロパティを使用して、直接には、アニメーションを適用したかどうか、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを呼び出し、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>メソッドを再度変更されているアニメーションを渡すとします。  
  
-   クロック レベルで直接操作している場合は、新しいクロック セットを作成して適用し、それらを使って、生成されたクロックの以前のセットを置換します。  
  
 タイムラインと時計に関する詳細については、次を参照してください。[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)です。  
  
### <a name="fillbehaviorstop-doesnt-work-as-expected"></a>FillBehavior.Stop が期待どおりに動作しない  
 あります設定するときに、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティを<xref:System.Windows.Media.Animation.FillBehavior.Stop>場合などの効果がないとみなさアニメーション"オフ"を渡します別があるため、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A>の設定<xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace>です。  
  
 次の例を作成、 <xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Shapes.Rectangle>と<xref:System.Windows.Media.TranslateTransform>です。 <xref:System.Windows.Media.TranslateTransform>を移動するアニメーション化する、<xref:System.Windows.Shapes.Rectangle>周囲、<xref:System.Windows.Controls.Canvas>です。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 このセクションの例では、いくつかのケースを示すために上記のオブジェクトを使用している、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティが期待どおりに動作しません。  
  
#### <a name="fillbehaviorstop-and-handoffbehavior-with-multiple-animations"></a>複数のアニメーションでの FillBehavior="Stop" と HandoffBehavior  
 思えますアニメーションを無視するよう、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>プロパティと 2 番目のアニメーションに置き換えられます。 次の例は、2 つ作成されますがかかる<xref:System.Windows.Media.Animation.Storyboard>オブジェクトし、同じアニメーション化するために使用<xref:System.Windows.Media.TranslateTransform>前の例に示すようにします。  
  
 最初の<xref:System.Windows.Media.Animation.Storyboard>、 `B1`、アニメーション、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> 350 を 0、右側に四角形 350 ピクセルに移動します。 アニメーションがその期間の終わりに達したし、再生が停止時に、<xref:System.Windows.Media.TranslateTransform.X%2A>プロパティは元の値を 0 に戻ります。 その結果、四角形は右に 350 ピクセル移動し、元の位置に移動します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 2 番目<xref:System.Windows.Media.Animation.Storyboard>、 `B2`、アニメーション化も、<xref:System.Windows.Media.TranslateTransform.X%2A>の同じプロパティ<xref:System.Windows.Media.TranslateTransform>です。 のみ、<xref:System.Windows.Media.Animation.DoubleAnimation.To%2A>このアニメーションのプロパティ<xref:System.Windows.Media.Animation.Storyboard>がアニメーションをアニメーション化するプロパティの現在の値を使用して、その開始値として設定します。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 最初の 2 番目のボタンをクリックすると<xref:System.Windows.Media.Animation.Storyboard>を再生する予定であると、次の動作。  
  
1.  最初のストーリー ボードを終了し、アニメーションがあるために、元の位置に四角形を送信、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>の<xref:System.Windows.Media.Animation.FillBehavior.Stop>します。  
  
2.  2 つ目のストーリーボードが反映され、現在位置である 0 から 500 にアニメーション化します。  
  
 **しかし、これは行われません。** 代わりに、四角形は戻らずに、右に移動し続けます。 その理由は、2 番目のアニメーションは最初のアニメーションの現在の値を開始値として使い、その値から 500 までアニメーション化するためです。 に、2 番目のアニメーションが最初を置換するときに、 <xref:System.Windows.Media.Animation.HandoffBehavior.SnapshotAndReplace> <xref:System.Windows.Media.Animation.HandoffBehavior>を使用する、<xref:System.Windows.Media.Animation.FillBehavior>最初のアニメーションは重要ではありません。  
  
#### <a name="fillbehavior-and-the-completed-event"></a>FillBehavior と完了イベント  
 次の例では、別のシナリオ、 <xref:System.Windows.Media.Animation.FillBehavior.Stop> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>効果がないように見えます。 例では、ストーリーを使用して、もう一度、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> 350 に 0 です。 ただし、今度は例では、登録、<xref:System.Windows.Media.Animation.Timeline.Completed>イベント。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed>イベント ハンドラーが起動別<xref:System.Windows.Media.Animation.Storyboard>を 500 に現在の値から同じプロパティをアニメーション化します。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 2 番目を定義するマークアップを次に示します<xref:System.Windows.Media.Animation.Storyboard>リソースとして。  
  
 [!code-xaml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 実行すると、 <xref:System.Windows.Media.Animation.Storyboard>、予定であると、<xref:System.Windows.Media.TranslateTransform.X%2A>のプロパティ、 <xref:System.Windows.Media.TranslateTransform> 、アニメーション化する 0 から 350 をからに戻し 0 の完了後に (があるため、<xref:System.Windows.Media.Animation.FillBehavior>の設定<xref:System.Windows.Media.Animation.FillBehavior.Stop>)、し、0 から 500 にアニメーション化します。 代わりに、 <xref:System.Windows.Media.TranslateTransform> 350 を 500 にし、0 からアニメーション化します。  
  
 順序が原因である[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)]イベントを発生させ、プロパティが無効にしない限り、プロパティの値はキャッシュされないために再計算します。 <xref:System.Windows.Media.Animation.Timeline.Completed>ルート タイムラインで、トリガーされたために、最初に処理イベント (最初<xref:System.Windows.Media.Animation.Storyboard>)。 この時点で、<xref:System.Windows.Media.TranslateTransform.X%2A>プロパティは、まだ無効されていないためまだそのアニメーション化された値を返します。 2 番目<xref:System.Windows.Media.Animation.Storyboard>はその開始値とキャッシュされた値を使用し、アニメーションを開始します。  
  
<a name="performancesection"></a>   
## <a name="performance"></a>パフォーマンス  
  
### <a name="animations-continue-to-run-after-navigating-away-from-a-page"></a>アニメーションがページからの移動後も実行され続ける  
 外に移動するときに、<xref:System.Windows.Controls.Page>実行中のアニメーションが含まれる、それらのアニメーションは再生まで引き続き、<xref:System.Windows.Controls.Page>ガベージ コレクトされます。 使っているナビゲーション システムによっては、離れた後のページが無期限にメモリに残り、その間、そのアニメーションでリソースが消費されることがあります。 これは、ページに常時実行 ("アンビエント") アニメーションが含まれる場合に最も顕著です。  
  
 このため、使用することをお勧めは、<xref:System.Windows.FrameworkElement.Unloaded>ページから移動するときに、アニメーションを削除するイベントです。  
  
 アニメーションを削除する別の方法もあります。 属するアニメーションを削除する、次の手法を使用できます、<xref:System.Windows.Media.Animation.Storyboard>です。  
  
-   削除する、<xref:System.Windows.Media.Animation.Storyboard>イベント トリガーを開始してを参照してください[する方法: ストーリー ボードを削除する](http://msdn.microsoft.com/library/7fe39531-de2f-46a0-a69f-b783d04235ee)です。  
  
-   コードを使用して削除する、<xref:System.Windows.Media.Animation.Storyboard>を参照してください、<xref:System.Windows.Media.Animation.Storyboard.Remove%2A>メソッドです。  
  
 次の手法は、アニメーションの開始方法に関係なく使用できます。  
  
-   アニメーションを特定のプロパティから削除するには、使用、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>メソッドです。 最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。 これにより、すべてのアニメーション クロックがプロパティから削除されます。  
  
 プロパティをアニメーション化するさまざまな方法の詳細については、次を参照してください。[プロパティ アニメーションの技術概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)です。  
  
### <a name="using-the-compose-handoffbehavior-consumes-system-resources"></a>HandoffBehavior を使うとシステム リソースが消費される  
 適用すると、 <xref:System.Windows.Media.Animation.Storyboard>、 <xref:System.Windows.Media.Animation.AnimationTimeline>、または<xref:System.Windows.Media.Animation.AnimationClock>を使用してプロパティを<xref:System.Windows.Media.Animation.HandoffBehavior.Compose> <xref:System.Windows.Media.Animation.HandoffBehavior>、any<xref:System.Windows.Media.Animation.Clock>以前そのプロパティに関連付けられているオブジェクトがシステム リソースを消費引き続き; タイミング システムはありませんこれらの時計を自動的に削除します。  
  
 使用してクロックの数が多いを適用するときに、パフォーマンスの問題を回避する<xref:System.Windows.Media.Animation.HandoffBehavior.Compose>、完了した後、アニメーションのプロパティから作成クロックを削除する必要があります。 クロックを削除する方法はいくつかあります。  
  
-   プロパティからすべてのクロックを削除するには、使用、<xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29>または<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29>アニメーション オブジェクトのメソッドです。 最初のパラメーターとしてアニメーション化されているプロパティを指定し、 `null` 2 つ目として。 これにより、すべてのアニメーション クロックがプロパティから削除されます。  
  
-   固有の仕様を削除する<xref:System.Windows.Media.Animation.AnimationClock>にクロックのリストを使用して、<xref:System.Windows.Media.Animation.Clock.Controller%2A>のプロパティ、<xref:System.Windows.Media.Animation.AnimationClock>を取得する、<xref:System.Windows.Media.Animation.ClockController>を呼び出す、<xref:System.Windows.Media.Animation.ClockController.Remove%2A>のメソッド、<xref:System.Windows.Media.Animation.ClockController>です。 これは、通常、<xref:System.Windows.Media.Animation.Clock.Completed>クロックのイベント ハンドラー。 唯一のルート クロックできますで制御されることに注意してください、 <xref:System.Windows.Media.Animation.ClockController>;<xref:System.Windows.Media.Animation.Clock.Controller%2A>子クロックのプロパティを返します`null`です。 なお、<xref:System.Windows.Media.Animation.Clock.Completed>クロックの有効期間が forever の場合、イベントは呼び出されません。  ユーザーの必要がありますを呼び出すタイミングを決定する場合は、<xref:System.Windows.Media.Animation.ClockController.Remove%2A>です。  
  
 これは主に、有効期間が長いオブジェクトでのアニメーションの問題です。  オブジェクトがガベージ コレクションされる場合は、そのクロックも切断されて、ガベージ コレクションされます。  
  
 クロック オブジェクトに関する詳細については、次を参照してください。[アニメーションおよびタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)です。  
  
## <a name="see-also"></a>参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
