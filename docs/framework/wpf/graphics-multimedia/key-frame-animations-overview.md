---
title: "キー フレーム アニメーションの概要 | Microsoft Docs"
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
  - "アニメーション, キー フレーム"
  - "キー フレーム [WPF], キー フレーム アニメーションの概要"
  - "複数のアニメーションのターゲット値"
ms.assetid: 10028f97-bb63-41fc-b8ad-663dac7ea203
caps.latest.revision: 29
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 24
---
# キー フレーム アニメーションの概要
ここでは、キー フレーム アニメーションについて説明します。  キー フレーム アニメーションでは、3 つ以上のターゲット値を使用してアニメーション化し、アニメーションの補間方式を制御することができます。  
  
 このトピックは、次のセクションで構成されています。  
  
<a name="autoTopLevelSectionsOUTLINE0"></a>   
-   [必要条件](#prerequisites)  
  
-   [キー フレーム アニメーションの使用](#keyframeanimations)  
  
-   [関連トピック](#seeAlsoToggle)  
  
<a name="prerequisites"></a>   
## 必要条件  
 この概要を理解するには、[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] のアニメーションおよびタイムラインに精通している必要があります。  アニメーションの概要については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。また、From\/To\/By アニメーションについても知っておくと役に立ちます。  詳細については、「[From\/To\/By アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/from-to-by-animations-overview.md)」を参照してください。  
  
<a name="whatisakeyframeanimation"></a>   
## キー フレーム アニメーションとは  
 From\/To\/By アニメーションと同様に、キー フレーム アニメーションは、ターゲット プロパティの値をアニメーション化します。  また、<xref:System.Windows.Media.Animation.Timeline.Duration%2A> 全体でのターゲット値間の遷移を作成します。  ただし、From\/To\/By アニメーションでは 2 つの値の間の遷移が作成されますが、単一のキー フレーム アニメーションでは、任意の数のターゲット値の間の遷移を作成できます。  From\/To\/By アニメーションとは異なり、キー フレーム アニメーションには、ターゲット値を設定するために使用する From、To、または By プロパティがありません。  キー フレーム アニメーションのターゲット値は、キー フレーム オブジェクトを使用して記述します \(そのため、"キー フレーム アニメーション" と呼ばれます\)。  キー フレーム アニメーションのターゲット値を指定するには、キー フレーム オブジェクトを作成してアニメーションの <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> コレクションに追加します。  実行時に、アニメーションは指定したフレーム間を遷移します。  
  
 一部のキー フレーム メソッドは、複数のターゲット値をサポートするだけでなく、複数の補間方式もサポートします。  アニメーションの補間方式によって、ある値から次の値へのアニメーションの遷移方法が定義されます。  補間には、[離散](GTMT)、[線形](GTMT)、および[スプライン](GTMT)の 3 種類があります。  
  
 キー フレーム アニメーションを使用してアニメーション化するには、次の手順を実行します。  
  
-   From\/To\/By アニメーションの場合と同様に、アニメーションを宣言してその <xref:System.Windows.Media.Animation.Timeline.Duration%2A> を指定します。  
  
-   ターゲット値ごとに、適切な型のキー フレームを作成し、その値と <xref:System.Windows.Media.Animation.KeyTime> を設定して、アニメーションの <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames.KeyFrames%2A> コレクションに追加します。  
  
-   From\/To\/By アニメーションの場合と同様に、アニメーションをプロパティに関連付けます。  ストーリーボードを使用してアニメーションをプロパティに適用する方法の詳細については、「[ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)」を参照してください。  
  
 次の例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> を使用して、<xref:System.Windows.Shapes.Rectangle> 要素を 4 つの異なる場所にアニメーション化します。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  -->  
  
 From\/To\/By アニメーションと同様に、キー フレーム アニメーションも、マークアップおよびコードで <xref:System.Windows.Media.Animation.Storyboard> を使用するかコードで <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用して、プロパティに適用することができます。  また、キー フレーム アニメーションを使用して <xref:System.Windows.Media.Animation.AnimationClock> を作成し、1 つ以上のプロパティに適用することもできます。  アニメーションを適用するさまざまな方法の詳細については、「[プロパティ アニメーションの手法の概要](../../../../docs/framework/wpf/graphics-multimedia/property-animation-techniques-overview.md)」を参照してください。  
  
<a name="animation_types"></a>   
## キー フレーム アニメーションの種類  
 アニメーションによってプロパティ値が生成されるため、さまざまなプロパティ型に対応するさまざまな種類のアニメーションが存在します。  <xref:System.Double> を受け取るプロパティ \(要素の <xref:System.Windows.FrameworkElement.Width%2A> プロパティなど\) をアニメーション化するには、<xref:System.Double> 値を生成するアニメーションを使用します。  <xref:System.Windows.Point> を受け取るプロパティをアニメーション化するには、<xref:System.Windows.Point> 値を生成するアニメーションを使用します。他も同様です。  
  
 キー フレーム アニメーション クラスは <xref:System.Windows.Media.Animation> 名前空間に属し、次の名前付け規則に従います。  
  
 *\<Type\>* `AnimationUsingKeyFrames`  
  
 ここで、*\<Type\>* はクラスによってアニメーション化される値の型です。  
  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] には、次のキー フレーム アニメーション クラスが用意されています。  
  
|プロパティの型|対応する From\/To\/By アニメーション クラス|サポートされている補間方式|  
|-------------|-----------------------------------|-------------------|  
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
## ターゲット値 \(キー フレーム\) およびキー時刻  
 さまざまな型のプロパティをアニメーション化するためにさまざまな種類のキー フレーム アニメーションが存在するのと同様に、キー フレーム オブジェクトにもさまざまな種類があります。このオブジェクトは、アニメーション化される値の型およびサポートされている補間方式ごとに 1 つずつあります。  キー フレームの種類は、次の名前付け規則に従います。  
  
 *\<InterpolationMethod\>\<Type\>* `KeyFrame`  
  
 ここで、*\<InterpolationMethod\>* はキー フレームで使用される補間方式で、*\<Type\>* はクラスによってアニメーション化される値の型です。  3 つすべての補間方式をサポートするキー フレーム アニメーションでは、3 種類のキー フレームを使用できます。  たとえば、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> では <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>、<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>、および <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> の 3 種類のキー フレームを使用できます   \(補間方式については、後のセクションで詳しく説明します\)。  
  
 キー フレームの主な目的は、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> および <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> を指定することです。  すべての種類のキー フレームで、これら 2 つのプロパティが提供されます。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> プロパティは、そのキー フレームのターゲット値を指定します。  
  
-   <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> プロパティは、\(アニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 内で\) キー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> に達する時刻を指定します。  
  
 キー フレーム アニメーションが開始されると、<xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> プロパティで定義された順序でキー フレームが反復処理されます。  
  
-   0 の時点にキー フレームが存在しない場合は、アニメーションによってターゲット プロパティの現在の値と最初のキー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> の間の遷移が作成されます。それ以外の場合は、アニメーションの出力値が最初のキー フレームの値になります。  
  
-   アニメーションでは、2 番目のキー フレームで指定された補間方式を使用して、最初のキー フレームと 2 番目のキー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> の間の遷移が作成されます。  遷移は最初のキー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> から開始され、2 番目のキー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> に到達した時点で終了します。  
  
-   アニメーションが続行され、後続の各キー フレームとその前のキー フレームの間の遷移が作成されます。  
  
-   最後に、アニメーションは、その <xref:System.Windows.Media.Animation.Timeline.Duration%2A> 以内で最大のキー時刻が指定されたキー フレームの値に遷移します。  
  
 アニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> が <xref:System.Windows.Duration.Automatic%2A> の場合、またはその <xref:System.Windows.Media.Animation.Timeline.Duration%2A> が最後のキー フレームの時刻と等しい場合、アニメーションは終了します。  アニメーションの <xref:System.Windows.Duration> が最後のキー フレームのキー時刻を超える場合、アニメーションは、その <xref:System.Windows.Duration> の最後に到達するまでキー フレームの値を保持します。  すべてのアニメーションと同様に、キー フレーム アニメーションは <xref:System.Windows.Media.Animation.Timeline.FillBehavior%2A> プロパティを使用して、アクティブな期間の末尾に到達したときに最終的な値を保持するかどうかを決定します。  詳細については、「[タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)」を参照してください。  
  
 次の例では、前の例で定義した <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> オブジェクトを使用して、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> および <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> プロパティの動作を示します。  
  
-   最初のキー フレームは、アニメーションの出力値を直ちに 0 に設定します。  
  
-   2 番目のキー フレームは、0 から 350 までアニメーション化します。  最初のキー フレームの終了時 \(0 秒の時点\) に開始され、2 秒間再生されて 0:0:2 の時点で終了します。  
  
-   3 番目のキー フレームは、350 から 50 までアニメーション化します。  2 番目のキー フレームの終了時 \(2 秒の時点\) に開始され、5 秒間再生されて 0:0:7 の時点で終了します。  
  
-   4 番目のキー フレームは、50 から 200 までアニメーション化します。  3 番目のキー フレームの終了時 \(7 秒の時点\) に開始され、1 秒間再生されて 0:0:8 の時点で終了します。  
  
-   アニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> プロパティが 10 秒に設定されているため、アニメーションは、0:0:10 の時点で終了するまでの 2 秒間その最終的な値を保持します。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#BasicKeyFrameExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyFramesIntroduction.xaml#basickeyframeexamplewholepage)]  -->  
  
<a name="interpolationmethods"></a>   
## 補間方式  
 これまでのセクションで、複数の補間方式をサポートするキー フレーム アニメーションもあることについて説明しました。  アニメーションの補間は、アニメーションが期間全体でどのように値の間を遷移するかを記述します。  アニメーションで使用するキー フレームの種類を選択することで、そのキー フレーム セグメントの補間方式を定義できます。  補間方式には、線形、離散、およびスプラインの 3 種類があります。  
  
### 線形補間  
 [線形補間](GTMT)では、アニメーションはセグメント期間において定率で進行します。  たとえば、キー フレーム セグメントが 5 秒間に 0 から 10 に遷移する場合、アニメーションは指定された時点で次の値を出力します。  
  
|Time|出力値|  
|----------|---------|  
|0|0|  
|1|2|  
|2|4|  
|3|6|  
|4|8|  
|4.25|8.5|  
|4.5|9|  
|5|10|  
  
### 離散補間  
 [離散補間](GTMT)では、補間なしでアニメーション機能がある値から次の値にジャンプします。  キー フレーム セグメントが 5 秒間に 0 から 10 に遷移する場合、アニメーションは指定された時点で次の値を出力します。  
  
|Time|出力値|  
|----------|---------|  
|0|0|  
|1|0|  
|2|0|  
|3|0|  
|4|0|  
|4.25|0|  
|4.5|0|  
|5|10|  
  
 セグメント期間の最後までアニメーションの出力値が変化しないことに注目してください。  
  
 [スプライン補間](GTMT)はより複雑です。  次のセクションを参照してください。  
  
<a name="anim_spline"></a>   
### スプライン補間  
 スプライン補間を使用すると、よりリアルなタイミング効果を実現できます。  アニメーションは現実に発生する効果を模倣するために使用されることが多いため、開発者は、オブジェクトの加速と減速を細かく制御し、タイミング セグメントを緻密に操作することが必要になる場合もあります。  スプライン キー フレームを使用すると、スプライン補間でアニメーション化することができます。  他のキー フレームでは、<xref:System.Windows.Media.Animation.IKeyFrame.Value%2A> および <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> を指定しますが、  スプライン キー フレームでは、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> も指定します。  <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> の単一のスプライン キー フレームの例を次に示します。  <xref:System.Windows.Media.Animation.KeySpline> プロパティに注目してください。このプロパティが、スプライン キー フレームと他の種類のキー フレームの違いです。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  -->  
  
 [3 次ベジエ曲線](GTMT)は、始点、終点、および 2 つの制御点によって定義されます。  スプライン キー フレームの <xref:System.Windows.Media.Animation.KeySpline> プロパティは、\(0,0\) から \(1,1\) に伸びるベジエ曲線の 2 つの制御点を定義します。  1 つ目の制御点はベジエ曲線の前半分の曲率を制御し、2 つ目の制御点はベジエ セグメントの残り半分の曲率を制御します。  作成された曲線は、そのスプライン キー フレームの変更率を示します。  曲線が急になるほどキー フレームの値の変更が速くなります。  曲線が平坦になるほどキー フレームの値の変更が遅くなります。  
  
 <xref:System.Windows.Media.Animation.KeySpline> を使用して、流れ落ちる水や跳ねるボールなどの物理的な軌道をシミュレートしたり、その他の "イーズイン" および "イーズアウト" 効果をモーション アニメーションに適用したりする場合があります。  背景のフェード効果やコントロール ボタンの戻り効果などのユーザー操作に関する効果の場合、スプライン補間を適用してアニメーションの変更率を特定の方法で加速または減速する場合もあります。  
  
 次の例は、<xref:System.Windows.Media.Animation.KeySpline> を 0,1 1,0 に指定し、次に示すベジエ曲線を作成します。  
  
 ![ベジエ曲線](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-0-1-1-0.png "graphicsmm\_keyspline\_0\_1\_1\_0")  
制御点が \(0.0, 1.0\) および \(1.0, 0.0\) のキー スプライン  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexample)]  -->  
  
 このキー フレームは、開始時にすばやくアニメーション化し、減速して再度加速し、終了します。  
  
 次の例は、<xref:System.Windows.Media.Animation.KeySpline> を 0.5,0.25 0.75,1.0 に指定し、次に示すベジエ曲線を作成します。  
  
 ![ベジエ曲線](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-keyspline-025-050-075-10.png "graphicsmm\_keyspline\_025\_050\_075\_10")  
制御点が \(0.25, 0.5\) および \(0.75, 1.0\) のキー スプライン  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SingleSplineKeyFrameExampleInline3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#singlesplinekeyframeexampleinline3)]  -->  
  
 ベジエ曲線の曲率がほとんど変化しないため、このキー フレームはほぼ定率でアニメーション化されます。終了が近づくと少し減速します。  
  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> を使用して四角形の位置をアニメーション化する例を次に示します。  <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> で <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> オブジェクトが使用されるため、キー フレームの各値の間の遷移でスプライン補間が使用されます。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SplinedInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#SplinedInterpolationExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#splinedinterpolationexample)]  -->  
  
 スプライン補間は理解しにくいため、さまざまな設定を試してみることをお勧めします。  [キー スプライン アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160011)を使用すると、キー スプラインの値を変更して、アニメーションに表れる結果を確認することができます。  
  
<a name="combininginterpolationmethods"></a>   
### 補間方式の組み合わせ  
 補間の種類が異なるキー フレームを 1 つのキー フレーム アニメーションで使用することができます。  補間の種類が異なる 2 つのキー フレーム アニメーションが交互に発生する場合、2 番目のキー フレームの補間方式を使用して、最初の値から 2 番目の値への遷移が作成されます。  
  
 次の例では、線形、スプライン、および離散補間を使用する <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> が作成されます。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#ComboInterpolationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/InterpolationMethodsExample.xaml#combointerpolationexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#ComboInterpolationExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/InterpolationMethodsExample.xaml#combointerpolationexample)]  -->  
  
<a name="keytimes"></a>   
## 継続時間およびキー時刻の詳細  
 他のアニメーションと同様に、キー フレーム アニメーションにも <xref:System.Windows.Duration> プロパティがあります。  アニメーションの <xref:System.Windows.Duration> の指定に加えて、その継続時間のどの部分を各キー フレームに割り当てるかを指定する必要があります。  指定するには、アニメーションの各キー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> を記述します。  各キー フレームの <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> は、そのキー フレームが終了する時刻を指定します。  
  
 <xref:System.Windows.Media.Animation.IKeyFrame.KeyTime%2A> プロパティは、キー時刻の再生時間を指定するわけではありません。  キー フレームが再生される時間は、そのキー フレームが終了する時刻、前のキー フレームが終了した時刻、およびアニメーションの継続時間によって決まります。  キー時刻は、時間を表す値、割合、あるいは特殊な値 \(<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> または <xref:System.Windows.Media.Animation.KeyTime.Paced%2A>\) で指定できます。  
  
 キー時刻を指定するさまざまな方法を次に示します。  
  
### TimeSpan 値  
 <xref:System.TimeSpan> 値を使用して <xref:System.Windows.Media.Animation.KeyTime> を指定できます。  この値は 0 以上でアニメーションの継続時間以下でなければなりません。  継続時間が 10 秒のアニメーションとキー時刻が時間を表す値として指定される 4 つのキー フレームの例を次に示します。  
  
-   最初のキー フレームは、最初の 3 秒間に基準値から 100 までアニメーション化し、0:0:03 の時点で終了します。  
  
-   2 番目のキー フレームは、100 から 200 までアニメーション化します。  最初のキー フレームの終了時 \(3 秒の時点\) に開始され、5 秒間再生されて 0:0:8 の時点で終了します。  
  
-   3 番目のキー フレームは、200 から 500 までアニメーション化します。  2 番目のキー フレームの終了時 \(8 秒の時点\) に開始され、1 秒間再生されて 0:0:9 の時点で終了します。  
  
-   4 番目のキー フレームは、500 から 600 までアニメーション化します。  3 番目のキー フレームの終了時 \(9 秒の時点\) に開始され、1 秒間再生されて 0:0:10 の時点で終了します。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#TimeSpanKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#timespankeytimeexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#TimeSpanKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#timespankeytimeexample)]  -->  
  
### 割合の値  
 割合の値は、キー フレームがアニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> に対する特定の割合の時点で終了するように指定します。  [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、数値の後に `%` 記号が続く形式で割合を指定します。  コードでは、<xref:System.Windows.Media.Animation.KeyTime.FromPercent%2A> メソッドを使用して、割合を示す <xref:System.Double> を渡します。  この値は 0 以上、100% 以下でなければなりません。  継続時間が 10 秒のアニメーションとキー時刻が割合として指定される 4 つのキー フレームの例を次に示します。  
  
-   最初のキー フレームは、最初の 3 秒間に基準値から 100 までアニメーション化し、0:0:3 の時点で終了します。  
  
-   2 番目のキー フレームは、100 から 200 までアニメーション化します。  最初のキー フレームの終了時 \(3 秒の時点\) に開始され、5 秒間再生されて 0:0:8 \(0.8 × 10 \= 8\) の時点で終了します。  
  
-   3 番目のキー フレームは、200 から 500 までアニメーション化します。  2 番目のキー フレームの終了時 \(8 秒の時点\) に開始され、1 秒間再生されて 0:0:9 \(0.9 × 10 \= 9\) の時点で終了します。  
  
-   4 番目のキー フレームは、500 から 600 までアニメーション化します。  3 番目のキー フレームの終了時 \(9 秒の時点\) に開始され、1 秒間再生されて 0:0:10 \(1 × 10 \= 10\) の時点で終了します。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#PercentageKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#percentagekeytimeexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#PercentageKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#percentagekeytimeexample)]  -->  
  
### 特殊な値 Uniform  
 各キー フレームの時間が同じになるようにするには、<xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> タイミングを使用します。  
  
 <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> キー時刻では、時間がキー フレームの数で均等に分割され、各キー フレームの終了時間が決まります。  継続時間が 10 秒のアニメーションとキー時刻が <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> として指定される 4 つのキー フレームの例を次に示します。  
  
-   最初のキー フレームは、最初の 2.5 秒間に基準値から 100 までアニメーション化し、0:0:2.5 の時点で終了します。  
  
-   2 番目のキー フレームは、100 から 200 までアニメーション化します。  最初のキー フレームの終了時 \(2.5 秒の時点\) に開始され、約 2.5 秒間再生されて 0:0:5 の時点で終了します。  
  
-   3 番目のキー フレームは、200 から 500 までアニメーション化します。  2 番目のキー フレームの終了時 \(5 秒の時点\) に開始され、2.5 秒間再生されて 0:0:7.5 の時点で終了します。  
  
-   4 番目のキー フレームは、500 から 600 までアニメーション化します。  2 番目のキー フレームの終了時 \(7.5 秒の時点\) に開始され、2.5 秒間再生されて 0:0:1 の時点で終了します。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#UniformKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#uniformkeytimeexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#UniformKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#uniformkeytimeexample)]  -->  
  
### 特殊な値 Paced  
 定率でアニメーション化するには、<xref:System.Windows.Media.Animation.KeyTime.Paced%2A> タイミングを使用します。  
  
 <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> キー時刻では、各キー フレームの長さに基づいて時間が割り当てられ、各フレームの継続時間が決まります。  これにより、アニメーションの速度 \(ペース\) が一定になります。  継続時間が 10 秒のアニメーションとキー時刻が <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> として指定される 3 つのキー フレームの例を次に示します。  
  
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#PacedKeyTimeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_ovw_snip/CS/KeyTimesExample.xaml#pacedkeytimeexample)]  -->
 <!-- TODO: review snippet reference [!code-xml[keyframes_ovw_snip#PacedKeyTimeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_ovw_snip/XAML/KeyTimesExample.xaml#pacedkeytimeexample)]  -->  
  
 最後のキー フレームのキー時刻が <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> または <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> の場合、解決されたキー時刻は 100% に設定されます。  マルチフレーム アニメーションの最初のキー フレームが Paced の場合、解決されたキー時刻は 0 に設定されます。  キー フレーム コレクションに含まれるキー フレームが 1 つだけで、Paced キー フレームである場合、解決されたキー時刻は 100% に設定されます。  
  
 1 つのキー フレーム アニメーション内の異なるキー フレームでは、異なるキー時刻を使用できます。  
  
<a name="combiningkeytimes"></a>   
## キー時刻と順序がバラバラのキー フレームの組み合わせ  
 種類が異なる <xref:System.Windows.Media.Animation.KeyTime> の値を持つキー フレームを 1 つのアニメーションで使用することができます。  また、キー フレームは再生順に追加することをお勧めしますが、必須ではありません。  アニメーションおよびタイミング システムでは、順序がバラバラのキー フレームを解決できます。  キー時刻が無効なキー フレームは無視されます。  
  
 キー フレーム アニメーションのキー フレームのキー時刻を解決するための手順を次に示します。  
  
1.  <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> 値を解決します。  
  
2.  アニメーションの合計補間時間 \(キー フレーム アニメーションが順方向の反復を完了するのに要する合計時間\) を決定します。  
  
    1.  アニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> が <xref:System.Windows.Duration.Automatic%2A> または <xref:System.Windows.Duration.Forever%2A> ではない場合、合計補間時間はアニメーションの <xref:System.Windows.Media.Animation.Timeline.Duration%2A> プロパティの値になります。  
  
    2.  それ以外の場合、合計補間時間は、キー フレーム間に指定された <xref:System.TimeSpan> <xref:System.Windows.Media.Animation.KeyTime> 値の中で最大の値になります \(存在する場合\)。  
  
    3.  最大値が存在しない場合、合計補間時間は 1 秒です。  
  
3.  合計補間時間の値を使用して、<xref:System.Windows.Media.Animation.KeyTimeType> <xref:System.Windows.Media.Animation.KeyTime> 値を解決します。  
  
4.  最後のキー フレームを解決します \(前の手順で解決していない場合\)。  最後のキー フレームの <xref:System.Windows.Media.Animation.KeyTime> が <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> または <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> の場合、解決された時間は合計補間時間と等しくなります。  
  
     最初のキー フレームの <xref:System.Windows.Media.Animation.KeyTime> が <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> で、このアニメーションに複数のキー フレームが含まれる場合、その <xref:System.Windows.Media.Animation.KeyTime> 値は 0 に解決されます。含まれるキー フレームが 1 つだけで、<xref:System.Windows.Media.Animation.KeyTime> 値が <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> の場合、その値は、前の手順で説明したように合計補間時間に解決されます。  
  
5.  残りの <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> 値を解決します。これらの値には、それぞれ均等な時間が割り当てられます。  この処理の間、未解決の <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> 値は一時的に <xref:System.Windows.Media.Animation.KeyTime.Uniform%2A> <xref:System.Windows.Media.Animation.KeyTime> 値として扱われ、一時的に解決された時間が割り当てられます。  
  
6.  キー時刻が指定されていないキー フレームの <xref:System.Windows.Media.Animation.KeyTime> 値を、そのキー フレームの最も近くで宣言されている、解決された <xref:System.Windows.Media.Animation.KeyTime> 値を持つキー フレームを使用して解決します。  
  
7.  残りの <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> 値を解決します。  <xref:System.Windows.Media.Animation.KeyTime.Paced%2A> <xref:System.Windows.Media.Animation.KeyTime> では、隣接するキー フレームの <xref:System.Windows.Media.Animation.KeyTime> 値を使用して時間が解決されます。  これにより、アニメーションの速度がこのキー フレームの解決された時間を基に一定になります。  
  
8.  キー フレームを解決された時間 \(主キー\) の順に並べ替え、宣言 \(2 次キー\) の順に並べ替えます。つまり、解決されたキー フレームの <xref:System.Windows.Media.Animation.KeyTime> 値に基づく安定ソートを使用します。  
  
## 参照  
 <xref:System.Windows.Media.Animation.KeyTime>   
 <xref:System.Windows.Media.Animation.KeySpline>   
 <xref:System.Windows.Media.Animation.Timeline>   
 [キー スプライン アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160011)   
 [KeyFrame アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)   
 [タイミング動作の概要](../../../../docs/framework/wpf/graphics-multimedia/timing-behaviors-overview.md)