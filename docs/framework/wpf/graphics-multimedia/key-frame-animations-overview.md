---
title: "キー フレーム アニメーションの概要"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], key-frame
- key frames [WPF], about key-frame animations
- multiple animation target values [WPF]
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: "29"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 38f0f6ac030af08039438b7e766c3f0f5bed7534
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="key-frame-animations-overview"></a>キー フレーム アニメーションの概要
このトピックでは、キー フレーム アニメーションの概要を説明します。 キー フレーム アニメーションでは、3 つ以上のターゲット値を使用してアニメーション化することができ、アニメーションの補間方式を制御できます。  
  
<a name="prerequisites"></a>   
## <a name="prerequisites"></a>必須コンポーネント  
 この概要を理解するのには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] アニメーションとタイムラインを理解しておく必要があります。 アニメーションの概要については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。 さらに、From/To/By アニメーションについて理解しておくと役に立ちます。 詳細については、「From/To/By アニメーションの概要」を参照してください。  
  
<a name="whatisakeyframeanimation"></a>   
## <a name="what-is-a-key-frame-animation"></a>キー フレーム アニメーションとは  
 From/To/By アニメーションと同じように、キー フレーム アニメーションも、ターゲット プロパティの値をアニメーション化します。 上でターゲット値間の遷移が作成、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>です。 ただし、From/To/By アニメーションは 2 つの値の間の遷移を作成しますが、キー フレーム アニメーションは、任意の数のターゲット値の間の遷移を作成できます。 From/To/By アニメーションとは異なり、キー フレーム アニメーションには、ターゲット値を設定する From、To、または By プロパティはありません。 キー フレーム アニメーションのターゲット値は、キー フレーム オブジェクトを使用して記述されます (このため、"キー フレーム アニメーション" という用語が使用されます)。 アニメーションのターゲット値を指定するキー フレームのオブジェクトを作成およびアニメーションに追加<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>コレクション。 アニメーションを実行すると、アニメーションが指定したフレームの間で遷移します。  
  
 複数のターゲット値のサポートに加え、一部のキー フレーム メソッドでは、複数の補間方式もサポートします。 アニメーションの補間方式は、1 つの値から次の値にどのように遷移するかを定義します。 補間には、離散、線形、およびスプラインの 3 つの種類があります。  
  
 キー フレーム アニメーションをアニメーション化するには、次の手順を完了します。  
  
-   アニメーションを宣言し、指定の<xref:System.Windows.Media.Animation.Timeline.Duration%2A>によって/アニメーションの場合と同様、します。  
  
-   各ターゲット値の適切な型のキー フレームの作成、その値を設定し、 <xref:System.Windows.Media.Animation.KeyTime>、アニメーションの追加と<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A>コレクション。  
  
-   From/To/By アニメーションと同じように、アニメーションをプロパティに関連付けます。 ストーリーボードを使用したアニメーションのプロパティへの適用の詳細については、「[ストーリー ボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>アニメーション化する、 <xref:System.Windows.Shapes.Rectangle> 4 つの異なる場所に要素。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
 などの From/を/、アニメーション、キー フレーム アニメーションに使用できるプロパティを使用して、<xref:System.Windows.Media.Animation.Storyboard>マークアップおよびコードでまたはを使用して、<xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A>コード内のメソッドです。 作成するキー フレーム アニメーションを使用することも、<xref:System.Windows.Media.Animation.AnimationClock>し、1 つまたは複数のプロパティに適用します。 アニメーションを適用するためのさまざまなメソッドの詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
<a name="animation_types"></a>   
## <a name="key-frame-animation-types"></a>キー フレーム アニメーションの種類  
 アニメーションはプロパティ値を生成するため、プロパティの型ごとに異なるアニメーションの種類があります。 受け取るプロパティをアニメーション化する、 <xref:System.Double> (要素のなど<xref:System.Windows.FrameworkElement.Width%2A>プロパティ) を生成するアニメーションを使用する<xref:System.Double>値。 受け取るプロパティをアニメーション化する、 <xref:System.Windows.Point>、生成されるアニメーションを使用する<xref:System.Windows.Point>値、およびなどです。  
  
 属しているキー フレーム アニメーション クラス、<xref:System.Windows.Media.Animation>名前空間され、次の命名規則に従います。  
  
 *\<Type>* `AnimationUsingKeyFrames`  
  
 ここで、*\<Type>*は、クラスがアニメーション化する値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] は、次のキー フレーム アニメーション クラスを提供します。  
  
|プロパティの型|対応するFrom/To/By アニメーションのクラス|サポートされる補間方式|  
|-------------------|------------------------------------------------|-------------------------------------|  
|<xref:System.Boolean>|<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>|離散|  
|<xref:System.Byte>|<xref:System.Windows.Media.Animation.ByteAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Color>|<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Decimal>|<xref:System.Windows.Media.Animation.DecimalAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Double>|<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Int16>|<xref:System.Windows.Media.Animation.Int16AnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Int32>|<xref:System.Windows.Media.Animation.Int32AnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Int64>|<xref:System.Windows.Media.Animation.Int64AnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Matrix>|<xref:System.Windows.Media.Animation.MatrixAnimationUsingKeyFrames>|離散|  
|<xref:System.Object>|<xref:System.Windows.Media.Animation.ObjectAnimationUsingKeyFrames>|離散|  
|<xref:System.Windows.Point>|<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Media3D.Quaternion>|<xref:System.Windows.Media.Animation.QuaternionAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Rect>|<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Media3D.Rotation3D>|<xref:System.Windows.Media.Animation.Rotation3DAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Single>|<xref:System.Windows.Media.Animation.SingleAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.String>|<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>|離散|  
|<xref:System.Windows.Size>|<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Thickness>|<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Media.Media3D.Vector3D>|<xref:System.Windows.Media.Animation.Vector3DAnimationUsingKeyFrames>|離散、線形、スプライン|  
|<xref:System.Windows.Vector>|<xref:System.Windows.Media.Animation.VectorAnimationUsingKeyFrames>|離散、線形、スプライン|  
  
<a name="animation_target_values"></a>   
## <a name="target-values-key-frames-and-key-times"></a>ターゲット値 (キー フレーム) とキー時刻  
 さまざまな種類のプロパティをアニメーション化するための多様な種類のキー フレーム アニメーションがあるように、さまざまな種類のキー フレーム オブジェクトがあります (アニメーション化される値の型とサポートされる補間方式ごとに 1 種類のオブジェクト)。 キー フレームの種類は、次の名前付け規則に従います。  
  
 *\<InterpolationMethod>\<Type>* `KeyFrame`  
  
 ここで、*\<InterpolationMethod>*は、キー フレームで使用される補間方式であり、*\<Type>*は、クラスがアニメーション化する値の型です。 3 つの補間方式のすべてをサポートするキー フレーム アニメーションでは、3 種類のキー フレームを使用できます。 次の 3 つのキー フレームの種類を使用するなど、 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>: <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>、 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>、および<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>です。 (補間方式については、後のセクションで詳しく説明します)。  
  
 キー フレームの主な目的を指定する、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>と<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>です。 すべての種類のキー フレームには、次の 2 つのプロパティがあります。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>プロパティは、そのキー フレームのターゲット値を指定します。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティでは、タイミングを指定します (アニメーションの内<xref:System.Windows.Media.Animation.Timeline.Duration%2A>) キー フレームの<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>に到達します。  
  
 キー フレーム アニメーションの開始時に、そのキー フレームによって定義された順序でを反復処理、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティです。  
  
-   アニメーションがターゲット プロパティの現在の値の間の遷移を作成時に 0 にキー フレームがない場合、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>最初のキー フレームです。 それ以外の場合、アニメーションの出力の最初のキー フレームの値の値になります。  
  
-   アニメーションの間の遷移を作成する、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>最初と 2 番目キー フレームの 2 つ目のキー フレームによって指定された補間メソッドを使用します。 最初のキー フレームの始まり、遷移<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>とが終了 2 番目のキー フレームの<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>に到達します。  
  
-   アニメーションは、前後のキー フレームの間の遷移を作成しながら続行されます。  
  
-   最後で最大のキー時刻キー フレームの値をアニメーション遷移は同じか、またはアニメーションのより小さい<xref:System.Windows.Media.Animation.Timeline.Duration%2A>です。  
  
 場合、アニメーションの<xref:System.Windows.Media.Animation.Timeline.Duration%2A>は<xref:System.Windows.Duration.Automatic%2A>またはその<xref:System.Windows.Media.Animation.Timeline.Duration%2A>が最後のキー フレーム アニメーションの終了の時刻と等しい。 それ以外の場合、アニメーションの<xref:System.Windows.Duration>が最後のキー フレーム アニメーション保留リストの末尾に到達するまで、キー フレーム値のキー時刻よりも大きい、<xref:System.Windows.Duration>です。 すべてのアニメーションと同様に、キー フレーム アニメーションで使用されるその<xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A>かどうかが最終的な値保持のアクティブな期間の終了になったときに決定するプロパティです。 詳細については、「[タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)」を参照してください。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>オブジェクトを示すために前の例で定義されている方法、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>と<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティ作業します。  
  
-   最初のキー フレームは、アニメーションの出力値をただちに 0 に設定します。  
  
-   2 番目のキー フレームは、0 から 350 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 0 秒)、2 秒間再生され、時刻 = 0:0:2 で終わります。  
  
-   3 番目のキー フレームは、350 から 50 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 2 秒)、5 秒間再生され、時刻 = 0:0:7 で終わります。  
  
-   4 番目のキー フレームは、50 から 200 までアニメーション化されます。 3 番目のキー フレームが終わった時点で開始され (時刻 = 7 秒)、1 秒間再生され、時刻 = 0:0:8 で終わります。  
  
-   <xref:System.Windows.Media.Animation.Timeline.Duration%2A>アニメーションのプロパティは、10 秒に設定された、アニメーションの終了前に 2 つの秒の最終的な値を保持する時間 = 0:0:10。  
  
 [!code-xaml[keyframes_ovw_snippet#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  
  
<a name="interpolationmethods"></a>   
## <a name="interpolation-methods"></a>補間方式  
 前のセクションで、一部のキー フレーム アニメーションでは複数の補間方式がサポートされることに言及しました。 アニメーションの補間は、その継続時間中にアニメーションがどのように遷移するかを表します。 アニメーションで使用するキー フレームの種類を選択することで、そのキー フレーム セグメントの補間方式を定義できます。 補間方式には、線形、離散、およびスプラインの 3 つの種類があります。  
  
### <a name="linear-interpolation"></a>線形補間  
 線形補間では、アニメーションは、セグメントの継続期間中、一定の率で進行します。 たとえば、キー フレーム セグメントが 5 秒間で 0 から 10 に遷移する場合、アニメーションは、指定された時間に次の値を出力します。  
  
|時刻|出力値|  
|----------|------------------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### <a name="discrete-interpolation"></a>離散補間  
 離散補間では、アニメーション関数は、1 つの値から次の値に補間なしでジャンプします。 キー フレーム セグメントが 5 秒間で 0 から 10 に遷移する場合、アニメーションは、指定された時間で次の値を出力します。  
  
|時間|出力値|  
|----------|------------------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 アニメーションの出力値は、セグメント期間の最後の最後に達するまで変化しないことに注意してください。  
  
 スプライン補間はさらに複雑です。 次のセクションで説明します。  
  
<a name="anim_spline"></a>   
### <a name="splined-interpolation"></a>スプライン補間  
 スプライン補間を使用して、リアルなタイミング効果を実現できます。 アニメーションは現実世界で起こる効果を模倣するために使用されることが多いため、開発者は、オブジェクトの加速と減速を細かく制御し、タイミング セグメントを緻密に操作することが必要になる場合があります。 スプライン キーフレームでは、スプライン補間を使用してアニメーション化できます。 指定した他のキー フレーム、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A>と<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>です。 スプライン キー フレームの場合と指定することも、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A>です。 次の例では、1 つスプライン キー フレームの<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>です。 通知、 <xref:System.Windows.Media.Animation.KeySpline> ; プロパティは、どのスプライン キー フレームのキー フレームの他の種類と異なるです。  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 3 次ベジエ曲線は、開始点、終点、および 2 つの制御点によって定義されます。 <xref:System.Windows.Media.Animation.KeySpline>スプライン キー フレームのプロパティが (0, 0) から (1, 1) までのベジエ曲線の 2 つの制御点を定義します。 最初の制御点は、ベジエ曲線の前半分の曲率を制御し、2 つ目の制御点は、後半分の曲率を制御します。 結果として得られる曲線は、そのスプライン キー フレームの変化率を表します。 曲線が急であればあるほど、キー フレームの値は急激に変化します。 曲線が平坦になると、キー フレームの値は緩やかに変化します。  
  
 使用する場合があります<xref:System.Windows.Media.Animation.KeySpline>をウォーター フォール、ボールなどの物理的な軌道をシミュレートするか、他の「で容易になります」および「が容易になります」効果モーション アニメーションを適用します。 背景のフェードやコントロール ボタンの復帰などのユーザー操作効果では、スプライン補間を適用して、アニメーションの変化率を特定の方法で加速したり減速したりできます。  
  
 次の例を指定します、 <xref:System.Windows.Media.Animation.KeySpline> 0, 1 1, 0、次のベジエ曲線を作成するのです。  
  
 ![ベジエ曲線](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm_keyspline_0_1_1_0")  
制御点が (0.0, 1.0) および (1.0, 0.0) のキー スプライン  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  
  
 このキー フレームは、開始されると速いスピードでアニメーション化され、その後スピードが低下し、終了前に再びスピードが上がります。  
  
 次の例を指定します、<xref:System.Windows.Media.Animation.KeySpline>の 0.5,0.25 0.75,1.0 は、次のベジエ曲線を作成します。  
  
 ![ベジエ曲線](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm_keyspline_025_050_075_10")  
制御点が (0.25, 0.5) および (0.75, 1.0) のキー スプライン  
  
 [!code-xaml[keyframes_ovw_snippet#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  
  
 ベジエ曲線の曲率がほとんど変化しないため、このキー フレームは、ほぼ一定の率でアニメーション化され、最後の最後にわずかに減速します。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>四角形の位置をアニメーション化します。 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>使用<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>オブジェクトをそれぞれのキー フレーム値の間の遷移がスプライン補間を使用します。  
  
 [!code-xaml[keyframes_ovw_snippet#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  
  
 スプライン補間は理解するのが難しいことがあります。さまざまな設定で実験すると理解しやすくなります。 [キー スプライン アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160011)を使用して、キー スプライン値を変更し、その結果をアニメーションで確認することができます。  
  
<a name="combininginterpolationmethods"></a>   
### <a name="combining-interpolation-methods"></a>補間方式の組み合わせ  
 補間の種類が異なるキー フレームを 1 つのキー フレーム アニメーションで使用できます。 補間の種類が異なる 2 つのキー フレーム アニメーションが連続する場合は、2 番目のキー フレームの補間方式を使用して、最初の値から 2 番目の値への遷移が作成されます。  
  
 次の例で、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>を使用して線形、スプライン、および離散補間を作成します。  
  
 [!code-xaml[keyframes_ovw_snippet#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  
  
<a name="keytimes"></a>   
## <a name="more-about-duration-and-key-times"></a>継続時間とキー時刻の詳細  
 キー フレーム アニメーションにあるその他のアニメーションと同様に、<xref:System.Windows.Duration>プロパティです。 アニメーションを指定するだけでなく<xref:System.Windows.Duration>、各キー フレームにその期間のどの部分が指定されたを指定する必要があります。 記述することで、これを行う、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>アニメーションのキー フレームの各します。 各キー フレームの<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>そのキー フレームの終了を指定します。  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A>プロパティがキーの時間の再生時間を指定していません。 キー フレームが再生される時間の長さは、そのキー フレームの終了時刻、前のキー フレームの終了時刻、およびアニメーションの継続時間によって決まります。 時間の値、パーセンテージ、または特殊な値として、キー時刻を指定することがあります<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>です。  
  
 次の一覧で、キー時刻を指定するさまざまな方法について説明します。  
  
### <a name="timespan-values"></a>TimeSpan 値  
 使用することは<xref:System.TimeSpan>に指定する値、<xref:System.Windows.Media.Animation.KeyTime>です。 値は、0 以上、アニメーションの継続時間以下にする必要があります。 次の例は、継続時間が 10 秒で、キー時刻が時刻値として指定されている 4 つのキー フレームがあるアニメーションを示しています。  
  
-   最初のキー フレームは、最初の 3 秒間で基準値から 100 までアニメーション化され、時刻 = 0:0:03 で終わります。  
  
-   2 番目のキー フレームは、100 から 200 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 3 秒)、5 秒間再生され、時刻 = 0:0:8 で終わります。  
  
-   3 番目のキー フレームは、200 から 500 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 8 秒)、1 秒間再生され、時刻 = 0:0:9 で終わります。  
  
-   4 番目のキー フレームは、500 から 600 までアニメーション化されます。 3 番目のキー フレームが終わった時点で開始され (時刻 = 9 秒)、1 秒間再生され、時刻 = 0:0:10 で終わります。  
  
 [!code-xaml[keyframes_ovw_snippet#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#timespankeytimeexample)]  
  
### <a name="percentage-values"></a>パーセント値  
 キー フレームのアニメーションの割合で終了する割合値を指定<xref:System.Windows.Media.Animation.Timeline.Duration%2A>です。 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、後ろに `%` 記号が付いた数値として指定します。 使用するコードでは、<xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A>メソッドに渡すと、<xref:System.Double>割合を示すです。 値は、0 以上、100 パーセント以下にする必要があります。 次の例は、継続時間が 10 秒で、キー時刻がパーセントとして指定されている 4 つのキー フレームがあるアニメーションを示しています。  
  
-   最初のキー フレームは、最初の 3 秒間で基準値から 100 までアニメーション化され、時刻 = 0:0:3 で終わります。  
  
-   2 番目のキー フレームは、100 から 200 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 3 秒)、5 秒間再生され、時刻 = 0:0:8 (0.8 * 10 = 8) で終わります。  
  
-   3 番目のキー フレームは、200 から 500 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 8 秒)、1 秒間再生され、時刻 = 0:0:9 (0.9 * 10 = 9) で終わります。  
  
-   4 番目のキー フレームは、500 から 600 までアニメーション化されます。 3 番目のキー フレームが終わった時点で開始され (時刻 = 9 秒)、1 秒間再生され、時刻 = 0:0:10 (1 * 10 = 10)で終わります。  
  
 [!code-xaml[keyframes_ovw_snippet#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  
  
### <a name="special-value-uniform"></a>特殊な値 Uniform  
 使用して<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>各キー フレームの同じ時間に対処するときにタイムアウトします。  
  
 A<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>キー時刻使用可能な時間均等で除算を各キー フレームの終了時刻を特定のキー フレームの数。 次の例では、期間が 10 秒のアニメーションととして指定されたタイムアウトにキーを持つ 4 つのキー フレーム<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>です。  
  
-   最初のキー フレームは、最初の 2.5 秒間で基準値から 100 までアニメーション化され、時刻 = 0:0:2.5 で終わります。  
  
-   2 番目のキー フレームは、100 から 200 までアニメーション化されます。 最初のキー フレームが終わった時点で開始され (時刻 = 0:0:2.5 秒)、2.5 秒間再生され、時刻 = 0:0:5 で終わります。  
  
-   3 番目のキー フレームは、200 から 500 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 5 秒)、2.5 秒間再生され、時刻 = 0:0:7.5 で終わります。  
  
-   4 番目のキー フレームは、500 から 600 までアニメーション化されます。 2 番目のキー フレームが終わった時点で開始され (時刻 = 7.5 秒)、2.5 秒間再生され、時刻 = 0:0:10 で終わります。  
  
 [!code-xaml[keyframes_ovw_snippet#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  
  
### <a name="special-value-paced"></a>特殊な値 Paced  
 使用して<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>一定の割合でアニメーション化するときにタイムアウトします。  
  
 A<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>キー時刻は、各フレームの存続期間を決定するキー フレームのそれぞれの長さに従って使用可能な時間を割り当てます。  これにより、アニメーションの速さ (ペース) を一定に保つ動作が提供されます。  次の例では、期間が 10 秒のアニメーションととして指定されたタイムアウトにキーを持つ 3 つのキー フレーム<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>です。  
  
 [!code-xaml[keyframes_ovw_snippet#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snippet/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  
  
 最後のキー フレームのキー時刻がある場合、注意してください。<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>または<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>、解決された、キー時刻を 100% に設定されます。 マルチ フレーム アニメーションの最初のキー フレームが Paced の場合、解決されたキー時刻は 0 に設定されます  (キー フレーム コレクションにキー フレームが 1 つだけ含まれているときに、それが Paced が設定されたキー フレームの場合は、解決されたキー時刻は 100% に設定されます)。  
  
 1 つのキー フレーム アニメーション内の異なるキー フレームで異なるキー時刻を使用できます。  
  
<a name="combiningkeytimes"></a>   
## <a name="combining-key-times-out-of-order-key-frames"></a>キー時刻と順不同のキー フレームの組み合わせ  
 キー フレームを使用するには異なる<xref:System.Windows.Media.Animation.KeyTime>同じアニメーション内の型の値します。 さらに、キー フレームは再生する順序で追加することをお勧めしますが、それは必須ではありません。 アニメーションとタイミング システムは、順不同のキー フレームを解決できます。 キー時刻が無効なキー フレームは無視されます。  
  
 キー フレーム アニメーションのキー フレームのキー時刻が解決される手順を次に示します。  
  
1.  解決するには<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>値。  
  
2.  アニメーションの*合計補間時間*を決定します。これは、キー フレーム アニメーションが順方向の反復を完了するまでにかかる合計時間です。  
  
    1.  場合、アニメーションの<xref:System.Windows.Media.Animation.Timeline.Duration%2A>は<xref:System.Windows.Duration.Automatic%2A>または<xref:System.Windows.Duration.Forever%2A>、合計補間の時間のアニメーションの値は、<xref:System.Windows.Media.Animation.Timeline.Duration%2A>プロパティです。  
  
    2.  それ以外の場合、合計補間の時間が最大<xref:System.TimeSpan><xref:System.Windows.Media.Animation.KeyTime>に存在する場合、そのキー フレームの間で指定された値。  
  
    3.  それ以外の場合、合計補間時間は 1 秒間です。  
  
3.  解決するのには、合計補間の時刻の値を使用して<xref:System.Windows.Media.Animation.KeyTimeType.Percent><xref:System.Windows.Media.Animation.KeyTime>値。  
  
4.  前の手順で解決されていなければ、最後のキー フレームを解決します。 場合、<xref:System.Windows.Media.Animation.KeyTime>キー フレームは、最後の<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A>または<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>、解決された時刻、合計補間の時間に等しくなります。  
  
     場合、<xref:System.Windows.Media.Animation.KeyTime>が最初のキー フレームの<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>このアニメーションが複数のキー フレームの解決とその<xref:System.Windows.Media.Animation.KeyTime>0 です値の 1 つだけのキー フレームがある場合、その<xref:System.Windows.Media.Animation.KeyTime>値は<xref:System.Windows.Media.Animation.KeyTime.Paced%2A>、合計値に解決される。前の手順で説明されている補間時間。  
  
5.  解決するには残り<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>値: それぞれ指定が、使用可能な時間の均等な割合。  このプロセス中に未解決の<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>値が一時的として扱われます<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A><xref:System.Windows.Media.Animation.KeyTime>値、および一時的な解決時間を取得します。  
  
6.  解決するには、<xref:System.Windows.Media.Animation.KeyTime>キー フレームの値は解決されている最も近い場所に宣言されているキー フレームを使用してキー時刻を指定しない<xref:System.Windows.Media.Animation.KeyTime>値。  
  
7.  解決するには残り<xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>値。 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A><xref:System.Windows.Media.Animation.KeyTime>を使用して、<xref:System.Windows.Media.Animation.KeyTime>の近隣の値のキー フレームの解決時間を決定します。  目標は、アニメーションの速度がこのキー フレームの解決時間近くで一定であることを保証することです。  
  
8.  つまり解決された時刻 (主キー) の順序と (セカンダリ キー) の宣言の順序でのキー フレームを並べ替え、安定した並べ替えに使用するが、解決済みのキー フレームに基づく<xref:System.Windows.Media.Animation.KeyTime>値。  
  
## <a name="see-also"></a>参照  
 <xref:System.Windows.Media.Animation.KeyTime>  
 <xref:System.Windows.Media.Animation.KeySpline>  
 <xref:System.Windows.Media.Animation.Timeline>  
 [キー スプライン アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160011)  
 [キーフレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)  
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)  
 [タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)
