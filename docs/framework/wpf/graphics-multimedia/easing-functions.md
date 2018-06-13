---
title: イージング関数
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- applying mathematical formulas to animations [WPF]
- applying easing functions to animations [WPF]
- mathematical formulas [WPF], applying to animations
- animations [WPF], realistic movement
- easing functions [WPF]
- customizing easing functions [WPF]
- easing functions [WPF], definition
- easing functions [WPF], customizing
- animations [WPF], applying
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
ms.openlocfilehash: 3ce7c1824dc53c154ba1091ea62c1b8950b757c1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33557564"
---
# <a name="easing-functions"></a>イージング関数
イージング関数を使うと、独自の数式をアニメーションに適用することができます。 たとえば、オブジェクトをリアルにバウンドさせたり、バネに乗っているように動作させたりすることができます。 キー フレーム アニメーションや From/To/By アニメーションを使ってこれらの効果を近似することもできますが、大量の作業が必要であり、アニメーションは数式を使うほど正確ではありません。  
  
 継承することで、独自のカスタム イージング関数を作成するだけでなく<xref:System.Windows.Media.Animation.EasingFunctionBase>、ランタイムによって提供されるいくつかのイージング関数のいずれかを使用して、一般的な効果を作成することができます。  
  
-   <xref:System.Windows.Media.Animation.BackEase>: 取り消されますアニメーションの動き若干指定したパスにアニメーション化を開始する前にします。  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: バウンス効果を作成します。  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: 加速または減速循環関数を使用するアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>3</sup>です。  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: するまでに前後に動く spring のようなアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: 加速または減速指数の式を使用するアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>p</sup> p は、 <xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティです。  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>2</sup>です。  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>4</sup>です。  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: 加速または減速の公式を使用するアニメーションを作成する*f*(*t*) = *t*<sup>5</sup>です。  
  
-   <xref:System.Windows.Media.Animation.SineEase>: 加速または減速サイン (正弦) 式を使用するアニメーションを作成します。  
  
 これらのイージング関数の動作は、次のサンプルを使って調べることができます。  
  
 [このサンプルを実行する](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 アニメーションにイージング関数を適用するには、使用、`EasingFunction`アニメーションのプロパティをアニメーションに適用するイージング関数を指定します。 次の例に適用されます、<xref:System.Windows.Media.Animation.BounceEase>イージング関数を<xref:System.Windows.Media.Animation.DoubleAnimation>跳ね返り効果を作成します。  
  
 [このサンプルを実行する](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xaml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 前の例では、イージング関数を From/To/By アニメーションに適用しました。 キー フレーム アニメーションにこれらのイージング関数を適用することもできます。 次の例では、キー フレームとそれらに関連付けられたイージング関数を使って、四角形が上方に縮まり、遅くなり、下方に延び (落下するように)、停止するアニメーションを作成します。  
  
 [このサンプルを実行する](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xaml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 使用することができます、<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>イージング関数の動作、つまり、変更するプロパティを変更する方法、アニメーションの補間します。 3 つの値を与えることができますがある<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseIn>: 補間には、イージング関数に関連付けられた数式が次に示します。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseOut>: 補間に依存しているイージング機能に関連付けられている式の出力-100% の補間します。  
  
-   <xref:System.Windows.Media.Animation.EasingMode.EaseInOut>: 補間を使用して<xref:System.Windows.Media.Animation.EasingMode.EaseIn>アニメーションの前半のおよび<xref:System.Windows.Media.Animation.EasingMode.EaseOut>後半を 2 番目のです。  
  
 下のグラフのさまざまな値を示す<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>場所*f*(*x*)、アニメーションの進行状況を表すと*t*時間を表します。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/backease-graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/bounceease-graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/circleease-graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/cubicease-graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![異なる EasingMode の ElasticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/elasticease-graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![異なる EasingMode の ExponentialEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/exponentialease-graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![異なる EasingMode の QuarticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![異なる EasingMode の QuadraticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![異なる EasingMode の QuarticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quarticease-graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![異なる EasingMode の QuinticEase のグラフ。](../../../../docs/framework/wpf/graphics-multimedia/media/quinticease-graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![異なる EasingMode 値の SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  使用することができます<xref:System.Windows.Media.Animation.PowerEase>と同じ動作を作成する<xref:System.Windows.Media.Animation.CubicEase>、 <xref:System.Windows.Media.Animation.QuadraticEase>、 <xref:System.Windows.Media.Animation.QuarticEase>、および<xref:System.Windows.Media.Animation.QuinticEase>を使用して、<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティです。 たとえば、使用する場合<xref:System.Windows.Media.Animation.PowerEase>の代替として<xref:System.Windows.Media.Animation.CubicEase>を指定、 <xref:System.Windows.Media.Animation.PowerEase.Power%2A> 3 の値。  
  
 継承することで、独自のカスタム イージング関数を作成するだけでなく、実行時に含まれるイージング関数を使用して、<xref:System.Windows.Media.Animation.EasingFunctionBase>です。 次の例では、簡単なカスタム イージング関数を作成する方法を示します。 イージング関数をオーバーライドすることで動作する方法を独自の数値演算ロジックを追加することができます、<xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>メソッドです。  
  
 [このサンプルを実行する](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xaml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]
