---
title: "アニメーションのヒントとテクニック | Microsoft Docs"
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
  - "アニメーション化 (オブジェクトを) [WPF], トラブルシューティング"
  - "アニメーションのヒントとテクニック [WPF]"
  - "アニメーション [WPF], FillBehavior プロパティ"
  - "アニメーション [WPF], システム リソースの使用"
  - "パフォーマンスのトラブルシューティング [WPF], アニメーション"
  - "ヒントとテクニック [WPF], アニメーション"
  - "トラブルシューティング [WPF], アニメーション"
  - "トラブルシューティング (アニメーションの) [WPF]"
ms.assetid: e467796b-d5d4-45a6-a108-8c5d7ff69a0f
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# アニメーションのヒントとテクニック
ここでは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] でアニメーションを扱うときに、パフォーマンスを向上させ、不満を解消するのに役立つ多くのヒントとテクニックについて説明します。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
<a name="generalissuessection"></a>   
## 一般的な問題  
  
### スクロール バーやスライダーの位置をアニメーション化するとフリーズする  
 スクロール バーまたはスライダーの位置のアニメーション化に <xref:System.Windows.Media.Animation.FillBehavior> が <xref:System.Windows.Media.Animation.FillBehavior> \(既定値\) であるアニメーションを使用すると、ユーザーはスクロール バーまたはスライダーを使用できなくなります。  これは、アニメーションが完了した後も、ターゲット プロパティの基本値を上書きしているためです。  アニメーションがプロパティの現在値を上書きしないようにするには、アニメーションを削除するか、アニメーションの <xref:System.Windows.Media.Animation.FillBehavior> に <xref:System.Windows.Media.Animation.FillBehavior> を指定します。  詳細および使用例については、「[ストーリーボードを使用してアニメーション化した後にプロパティを設定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)」を参照してください。  
  
### アニメーションの出力をアニメーション化したのに効果がない  
 別のアニメーションの出力であるオブジェクトをアニメーション化することはできません。  たとえば、<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames> を使用して <xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を <xref:System.Windows.Media.RadialGradientBrush> から <xref:System.Windows.Media.SolidColorBrush> にアニメーション化する場合、<xref:System.Windows.Media.RadialGradientBrush> または <xref:System.Windows.Media.SolidColorBrush> のプロパティはどちらもアニメーション化できません。  
  
### アニメーション化した後でプロパティの値を変更できない  
 状況によっては、プロパティをアニメーション化した後で、アニメーションが完了しても、そのプロパティの値を変更できないように見えることがあります。  これは、アニメーションが完了した後も、プロパティの基本値を上書きしているためです。  アニメーションがプロパティの現在値を上書きしないようにするには、アニメーションを削除するか、アニメーションの <xref:System.Windows.Media.Animation.FillBehavior> に <xref:System.Windows.Media.Animation.FillBehavior> を指定します。  詳細および使用例については、「[ストーリーボードを使用してアニメーション化した後にプロパティを設定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-a-property-after-animating-it-with-a-storyboard.md)」を参照してください。  
  
### タイムラインを変更したのに効果がない  
 ほとんどの <xref:System.Windows.Media.Animation.Timeline> プロパティはアニメーション化とデータ バインドが可能ですが、アクティブな <xref:System.Windows.Media.Animation.Timeline> のプロパティ値を変更しても効果がないように見えます。  これは、<xref:System.Windows.Media.Animation.Timeline> が開始されると、タイミング システムが <xref:System.Windows.Media.Animation.Timeline> のコピーを作成し、それを使用して <xref:System.Windows.Media.Animation.Clock> オブジェクトを作成するためです。  元のアニメーションを変更してもシステムのコピーには影響しません。  
  
 <xref:System.Windows.Media.Animation.Timeline> に変更を反映するには、クロックを再生成し、前に作成したクロックと置き換える必要があります。  クロックは自動的に再生成されるわけではありません。  タイムラインの変更を適用するいくつかの方法を次に示します。  
  
-   タイムラインが <xref:System.Windows.Media.Animation.Storyboard> の場合またはこれに属している場合、<xref:System.Windows.Media.Animation.BeginStoryboard> または <xref:System.Windows.Media.Animation.Storyboard.Begin%2A> メソッドを使用してストーリーボードを再適用することで、タイムラインに変更を反映させることができます。  ただし、この場合、アニメーションが再起動されるという影響があります。  コード内で <xref:System.Windows.Media.Animation.Storyboard.Seek%2A> メソッドを使用すると、ストーリーボードを以前の位置に戻すことができます。  
  
-   <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用して、アニメーションをプロパティに直接適用した場合は、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> を再度呼び出し、変更されたアニメーションを渡します。  
  
-   クロック レベルで直接作業している場合は、クロックの新しいセットを作成して適用し、これらのクロックを使用して生成済みのクロックの以前のセットを置き換えます。  
  
 タイムラインとクロックの詳細については、「[アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)」を参照してください。  
  
### FillBehavior.Stop が予期したとおりに動作しない  
 あるアニメーションから別のアニメーションへの "引き継ぎ" のときなど、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティを <xref:System.Windows.Media.Animation.FillBehavior> にしても効果がないように見えることがあります。これは、<xref:System.Windows.Media.Animation.BeginStoryboard.HandoffBehavior%2A> 設定が <xref:System.Windows.Media.Animation.HandoffBehavior> になっているためです。  
  
 <xref:System.Windows.Controls.Canvas>、<xref:System.Windows.Shapes.Rectangle>、および <xref:System.Windows.Media.TranslateTransform> を作成する例を次に示します。  <xref:System.Windows.Media.TranslateTransform> は、<xref:System.Windows.Shapes.Rectangle> が <xref:System.Windows.Controls.Canvas> を動き回るようにアニメーション化されます。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipAnimatedObject](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipanimatedobject)]  
  
 このセクションの例では、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティが予期していたとおりには動作しないいくつかのケースについて、前のオブジェクトを使用して説明します。  
  
#### アニメーションが複数の場合の FillBehavior\="Stop" と HandoffBehavior  
 あるアニメーションが別のアニメーションに置き換わるときに、<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティが無視されているように見えることがあります。  これに関して、<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを 2 つ作成し、それらを使用して、前の例で示された <xref:System.Windows.Media.TranslateTransform> をアニメーション化する例について考えてみます。  
  
 最初の <xref:System.Windows.Media.Animation.Storyboard> である `B1` は、<xref:System.Windows.Media.TranslateTransform> の <xref:System.Windows.Media.TranslateTransform.X%2A> プロパティを 0 から 350 までアニメーション化します。これにより、四角形が 350 ピクセル左へ動きます。  アニメーションが終わって再生が完了すると、<xref:System.Windows.Media.TranslateTransform.X%2A> プロパティは元の値の 0 に戻ります。  その結果、四角形は右に 350 ピクセル移動し、元の位置に戻ります。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB1Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb1button)]  
  
 2 番目の <xref:System.Windows.Media.Animation.Storyboard> である `B2` も、同じ <xref:System.Windows.Media.TranslateTransform> の <xref:System.Windows.Media.TranslateTransform.X%2A> プロパティをアニメーション化します。  <xref:System.Windows.Media.Animation.Storyboard> のアニメーションで設定されているのは <xref:System.Windows.Media.Animation.DoubleAnimation.To%2A> プロパティのみなので、アニメーションは開始値としてこのプロパティの現在の値を使用します。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardB2Button](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardb2button)]  
  
 最初の <xref:System.Windows.Media.Animation.Storyboard> の再生中に 2 番目のボタンをクリックした場合は、次のように動作すると予期する可能性があります。  
  
1.  アニメーションの <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> が <xref:System.Windows.Media.Animation.FillBehavior> なので、最初のストーリーボードが完了すると、四角形が元の位置に戻る。  
  
2.  2 番目のストーリーボードが反映され、現在の位置の 0 から 500 へ動く。  
  
 実際はこのように動作しません。四角形は元の位置に戻らず、右へ移動し続けます。  これは、2 番目のアニメーションが、最初のアニメーションの現在値を開始値として使用し、その値から 500 へとアニメーション化するためです。  <xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior> の使用により 2 番目のアニメーションが最初のアニメーションと置き換わるとき、最初のアニメーションの <xref:System.Windows.Media.Animation.FillBehavior> は影響しません。  
  
#### FillBehavior と Completed イベント  
 次の例では、<xref:System.Windows.Media.Animation.FillBehavior> <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> の効果がないように見える別のシナリオについて説明します。  この例でも、Storyboard を使用して <xref:System.Windows.Media.TranslateTransform> の <xref:System.Windows.Media.TranslateTransform.X%2A> プロパティを 0 から 350 までアニメーション化します。  ただし、今回は <xref:System.Windows.Media.Animation.Timeline.Completed> イベントを登録します。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardCButton](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipstoryboardcbutton)]  
  
 <xref:System.Windows.Media.Animation.Timeline.Completed> イベント ハンドラーは、同じプロパティを現在値から 500 へとアニメーション化する別の <xref:System.Windows.Media.Animation.Storyboard> を開始します。  
  
 [!code-csharp[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml.cs#fillbehaviortipstoryboardc1completedhandler)]
 [!code-vb[AnimationTipsAndTricksSample_snip#FillBehaviorTipStoryboardC1CompletedHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/VisualBasic/FillBehaviorTip.xaml.vb#fillbehaviortipstoryboardc1completedhandler)]  
  
 次のマークアップは、2 番目の <xref:System.Windows.Media.Animation.Storyboard> をリソースとして定義します。  
  
 [!code-xml[AnimationTipsAndTricksSample_snip#FillBehaviorTipResources](../../../../samples/snippets/csharp/VS_Snippets_Wpf/AnimationTipsAndTricksSample_snip/CSharp/FillBehaviorTip.xaml#fillbehaviortipresources)]  
  
 <xref:System.Windows.Media.Animation.Storyboard> を実行すると、<xref:System.Windows.Media.TranslateTransform> の <xref:System.Windows.Media.TranslateTransform.X%2A> プロパティが 0 から 350 までアニメーション化され、完了すると 0 に戻り \(<xref:System.Windows.Media.Animation.FillBehavior> 設定が <xref:System.Windows.Media.Animation.FillBehavior> であるため\)、それから 0 から 500 へとアニメーション化されると予期する可能性があります。  しかし、実際には、<xref:System.Windows.Media.TranslateTransform> は 0 から 350 までアニメーション化されてから、500 へとアニメーション化されます。  
  
 これは、[!INCLUDE[TLA2#tla_wpf](../../../../includes/tla2sharptla-wpf-md.md)] がイベントを生成する順序と、プロパティが無効化されない限り、プロパティ値はキャッシュされても再計算されないことが原因です。  <xref:System.Windows.Media.Animation.Timeline.Completed> イベントは、ルート タイムライン \(最初の <xref:System.Windows.Media.Animation.Storyboard>\) によってトリガーされることにより、最初に処理されます。  この時点では、<xref:System.Windows.Media.TranslateTransform.X%2A> プロパティはまだ無効化されていないので、アニメーション化された値を引き続き返します。  2 番目の <xref:System.Windows.Media.Animation.Storyboard> はキャッシュされた値を開始値として使用して、アニメーションを開始します。  
  
<a name="performancesection"></a>   
## パフォーマンス  
  
### ページの外に移動した後もアニメーションが実行され続ける  
 アニメーションの実行を続けている <xref:System.Windows.Controls.Page> の外に移動した後も、実行中のアニメーションは <xref:System.Windows.Controls.Page> のガベージ コレクションが実行されるまで再生され続けます。  使用しているナビゲーション システムに応じて、ページの外に移動した後もページが永続的にメモリに残り、その間アニメーションでリソースを消費し続けることがあります。  この現象は、常に実行される \("アンビエント"\) アニメーションがページに含まれている場合に最も顕著です。  
  
 このため、ページ外へ移動するときに <xref:System.Windows.FrameworkElement.Unloaded> イベントを使用してアニメーションを削除することをお勧めします。  
  
 アニメーションを削除する方法はいくつかあります。  <xref:System.Windows.Media.Animation.Storyboard> に属するアニメーションを削除するには、次のテクニックを使用できます。  
  
-   イベント トリガーで開始した <xref:System.Windows.Media.Animation.Storyboard> を削除するには、「[How to: Remove a Storyboard](http://msdn.microsoft.com/ja-jp/7fe39531-de2f-46a0-a69f-b783d04235ee)」を参照してください。  
  
-   <xref:System.Windows.Media.Animation.Storyboard> を削除するコードを使用するには、<xref:System.Windows.Media.Animation.Storyboard.Remove%2A> メソッドを参照してください。  
  
 次のテクニックは、アニメーションの開始方法に関係なく使用できます。  
  
-   アニメーションを特定のプロパティから削除するには、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> メソッドを使用します。  アニメーション化するプロパティを最初のパラメーターとして指定し、`null` を 2 番目のパラメーターとして指定します。  これにより、プロパティからすべてのアニメーション クロックが削除されます。  
  
 プロパティをアニメーション化するさまざまな方法の詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
### Compose HandoffBehavior を使用するとシステム リソースが消費される  
 <xref:System.Windows.Media.Animation.Storyboard>、<xref:System.Windows.Media.Animation.AnimationTimeline>、または <xref:System.Windows.Media.Animation.AnimationClock> を、<xref:System.Windows.Media.Animation.HandoffBehavior> <xref:System.Windows.Media.Animation.HandoffBehavior> を使用してプロパティに適用すると、そのプロパティに前に関連付けられていたすべての <xref:System.Windows.Media.Animation.Clock> オブジェクトがリソースを消費し続けます。タイミング システムは、これらのクロックを自動的には削除しません。  
  
 <xref:System.Windows.Media.Animation.HandoffBehavior> を使用して多数のクロックを適用するときにパフォーマンスの問題が発生しないようにするには、アニメーション化されたプロパティから構成するクロックを完了後に削除してください。  クロックを削除するには、いくつかの方法があります。  
  
-   プロパティからすべてのクロックを削除するには、アニメーション化されたオブジェクトの <xref:System.Windows.Media.Animation.Animatable.ApplyAnimationClock%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationClock%29> メソッドまたは <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%28System.Windows.DependencyProperty%2CSystem.Windows.Media.Animation.AnimationTimeline%29> メソッドを使用します。  アニメーション化するプロパティを最初のパラメーターとして指定し、`null` を 2 番目のパラメーターとして指定します。  これにより、プロパティからすべてのアニメーション クロックが削除されます。  
  
-   クロックのリストから特定の <xref:System.Windows.Media.Animation.AnimationClock> を削除するには、<xref:System.Windows.Media.Animation.AnimationClock> の <xref:System.Windows.Media.Animation.Clock.Controller%2A> プロパティを使用して <xref:System.Windows.Media.Animation.ClockController> を取得し、<xref:System.Windows.Media.Animation.ClockController> の <xref:System.Windows.Media.Animation.ClockController.Remove%2A> メソッドを呼び出します。  これは、一般にクロックの <xref:System.Windows.Media.Animation.Clock.Completed> イベント ハンドラーで行われます。  <xref:System.Windows.Media.Animation.ClockController> により制御できるのは、ルート クロックのみである点に注意してください。子クロックの <xref:System.Windows.Media.Animation.Clock.Controller%2A> プロパティは `null` を返します。  クロックの有効期間が無期限の場合、<xref:System.Windows.Media.Animation.Clock.Completed> イベントが発生しない点にも注意してください。  その場合、ユーザーは <xref:System.Windows.Media.Animation.ClockController.Remove%2A> をいつ呼び出すかを決定する必要があります。  
  
 これは、主に有効期間が長いオブジェクトにおけるアニメーションの問題です。  オブジェクトがガベージ コレクションされると、そのクロックも切断されてガベージ コレクションされます。  
  
 クロック オブジェクトの詳細については、「[アニメーションとタイミング システムの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-system-overview.md)」を参照してください。  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)