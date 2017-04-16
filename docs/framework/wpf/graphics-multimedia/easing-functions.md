---
title: "イージング関数 | Microsoft Docs"
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
  - "適用 (数式をアニメーションに) [WPF]"
  - "適用 (イージング関数をアニメーションに) [WPF]"
  - "アニメーションに適用する数学的数式 [WPF]"
  - "リアルな動きのアニメーション [WPF]"
  - "イージング関数 [WPF]"
  - "カスタマイズ (イージング関数を) [WPF]"
  - "定義であるイージング関数 [WPF]"
  - "カスタマイズのイージング関数 [WPF]"
  - "適用するアニメーション [WPF]"
ms.assetid: 075b9c2b-82c4-43fa-b3cd-de0b6236eb38
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# イージング関数
イージング関数を使用すると、独自の数式をアニメーションに適用することができます。 たとえば、現実的にバウンスまたは、春のと同様に動作するオブジェクトもかまいません。 またはを使用してキー フレーム アニメーションによって/でもこれらの効果を概算するが、大量の作業がかかり、アニメーション公式を使用するよりも正確さに欠けます。  
  
 継承することで、独自のカスタムのイージング関数を作成するだけでなく<xref:System.Windows.Media.Animation.EasingFunctionBase>、ランタイムによって提供される複数のイージング関数のいずれかを使用して、一般的な効果を作成することができます。  
  
-   <xref:System.Windows.Media.Animation.BackEase>: 指定したパスのアニメーション化を開始する前に、少しアニメーションの動きが取り消されます。  
  
-   <xref:System.Windows.Media.Animation.BounceEase>: 跳ね返り効果を作成します。  
  
-   <xref:System.Windows.Media.Animation.CircleEase>: 加速または減速循環関数を使用してアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.CubicEase>: 加速または減速の公式を使用するアニメーションを作成*f*( *t*) = *t*<sup>3</sup>します。  
  
-   <xref:System.Windows.Media.Animation.ElasticEase>: 伸び縮みするまで春のようなアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.ExponentialEase>: 加速または減速指数の式を使用してアニメーションを作成します。  
  
-   <xref:System.Windows.Media.Animation.PowerEase>: 加速または減速の公式を使用するアニメーションを作成*f*( *t*) = *t*<sup>p</sup> p に等しい、<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティです。  
  
-   <xref:System.Windows.Media.Animation.QuadraticEase>: 加速または減速の公式を使用するアニメーションを作成*f*( *t*) = *t*<sup>2</sup>します。  
  
-   <xref:System.Windows.Media.Animation.QuarticEase>: 加速または減速の公式を使用するアニメーションを作成*f*( *t*) = *t*<sup>4</sup>します。  
  
-   <xref:System.Windows.Media.Animation.QuinticEase>: アニメーションを加速または減速式を使用して作成*f*( *t*) = *t*<sup>5</sup>します。  
  
-   <xref:System.Windows.Media.Animation.SineEase>: 加速または減速サイン (正弦) 式を使用してアニメーションを作成します。  
  
 次の例を使ってイージング関数の動作を調べることができます。  
  
 [このサンプルを実行します。](http://go.microsoft.com/fwlink/?LinkId=139798&sref=easing_functions_gallery)  
  
 イージング関数をアニメーションに適用するには、使用、`EasingFunction`アニメーションのプロパティがアニメーションに適用するイージング関数を指定します。 次の例では、適用、 <xref:System.Windows.Media.Animation.BounceEase>イージング関数を<xref:System.Windows.Media.Animation.DoubleAnimation>跳ね返り効果を作成します。  
  
 [このサンプルを実行します。](http://go.microsoft.com/fwlink/?LinkId=139798&sref=BounceEase)  
  
 [!code-xml[BounceEase_snippet#BounceEase](../../../../samples/snippets/csharp/VS_Snippets_Wpf/bounceease_snippet/CS/window1.xaml#bounceease)]  
  
 前の例では、イージング関数を From/に/によって適用したアニメーションです。 キー フレーム アニメーションにこれらのイージング関数を適用することもできます。 次の例では、コントラクトから上位に向かって停止、速度が低下し、下方向 (よう減少) を展開し、停止し、上で移動する四角形のアニメーションを作成するイージングそれらに関連付けられている関数をキー フレームを使用する方法を示します。  
  
 [このサンプルを実行します。](http://go.microsoft.com/fwlink/?LinkId=139798&sref=EasingFunctionDoubleKeyFrame)  
  
 [!code-xml[EasingFunctionDoubleKeyFrame_snippet#EasingFunctionDoubleKeyFrame](../../../../samples/snippets/csharp/VS_Snippets_Wpf/easingfunctiondoublekeyframe_snippet/CS/window1.xaml#easingfunctiondoublekeyframe)]  
  
 使用することができます、 <xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>イージング関数の動作について、つまりを変更するプロパティを変更するアニメーションの補間します。 渡すことができる&3; つの値がある<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A>:  
  
-   <xref:System.Windows.Media.Animation.EasingMode>: に従ってイージング関数に関連付けられている数式を補間します。  
  
-   <xref:System.Windows.Media.Animation.EasingMode>: に従ってイージング関数に関連付けられている計算式の出力結果を差し引き、100% の補間を補間します。  
  
-   <xref:System.Windows.Media.Animation.EasingMode>: 補間を使用して<xref:System.Windows.Media.Animation.EasingMode>アニメーションの最初の半分についておよび<xref:System.Windows.Media.Animation.EasingMode>後半のです。  
  
 次のグラフのそれぞれの値を示す<xref:System.Windows.Media.Animation.EasingFunctionBase.EasingMode%2A> 、 *f*( *x*) アニメーションの進行状況を表すと*t*時間を表します。  
  
 <xref:System.Windows.Media.Animation.BackEase>  
  
 ![BackEase EasingMode のグラフ。] (../Image/BackEase_Graph.png "BackEase_Graph")  
  
 <xref:System.Windows.Media.Animation.BounceEase>  
  
 ![BounceEase EasingMode のグラフ] (../Image/BounceEase_Graph.png "BounceEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CircleEase>  
  
 ![CircleEase EasingMode のグラフ] (../Image/CircleEase_Graph.png "CircleEase_Graph")  
  
 <xref:System.Windows.Media.Animation.CubicEase>  
  
 ![CubicEase EasingMode のグラフ] (../Image/CubicEase_Graph.png "CubicEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ElasticEase>  
  
 ![ElasticEase の異なる easingmode のグラフ] (../Image/ElasticEase_Graph.png "ElasticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.ExponentialEase>  
  
 ![異なる easingmode の ExponentialEase のグラフ。] (../Image/ExponentialEase_Graph.png "ExponentialEase_Graph")  
  
 <xref:System.Windows.Media.Animation.PowerEase>  
  
 ![異なる easingmode のグラフ QuarticEase] (../Image/QuarticEase_Graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuadraticEase>  
  
 ![異なる easingmode のグラフの QuadraticEase](../../../../docs/framework/wpf/graphics-multimedia/media/quadraticease-graph.png "QuadraticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuarticEase>  
  
 ![異なる easingmode のグラフ QuarticEase] (../Image/QuarticEase_Graph.png "QuarticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.QuinticEase>  
  
 ![異なる easingmode のグラフ QuinticEase] (../Image/QuinticEase_Graph.png "QuinticEase_Graph")  
  
 <xref:System.Windows.Media.Animation.SineEase>  
  
 ![異なる EasingMode 値の SineEase](../../../../docs/framework/wpf/graphics-multimedia/media/sineease-graph.png "SineEase_Graph")  
  
> [!NOTE]
>  使用することができます<xref:System.Windows.Media.Animation.PowerEase>と同じ動作を作成する<xref:System.Windows.Media.Animation.CubicEase>、 <xref:System.Windows.Media.Animation.QuadraticEase>、 <xref:System.Windows.Media.Animation.QuarticEase>、および<xref:System.Windows.Media.Animation.QuinticEase>を使用して、<xref:System.Windows.Media.Animation.PowerEase.Power%2A>プロパティです。 例では、使用する場合の<xref:System.Windows.Media.Animation.PowerEase>の代わりに<xref:System.Windows.Media.Animation.CubicEase>、指定、<xref:System.Windows.Media.Animation.PowerEase.Power%2A>3 の値。  
  
 継承することで、独自のイージング関数を作成する実行時に含まれるイージング関数を使用するだけでなく<xref:System.Windows.Media.Animation.EasingFunctionBase>します。 次の例では、単純なカスタム イージング関数を作成する方法を示します。 イージング関数の動作をオーバーライドすることで、独自の数値演算ロジックを追加する、 <xref:System.Windows.Media.Animation.EasingFunctionBase.EaseInCore%2A>メソッドです。  
  
 [このサンプルを実行します。](http://go.microsoft.com/fwlink/?LinkId=139798&sref=CustomEasingFunction)  
  
 [!code-csharp[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/customlog10easingfunction.cs#customeasingfunction)]
 [!code-vb[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/customeasingfunction/visualbasic/customlog10easingfunction.vb#customeasingfunction)]
 [!code-xml[CustomEasingFunction#CustomEasingFunction](../../../../samples/snippets/csharp/VS_Snippets_Wpf/customeasingfunction/csharp/window1.xaml#customeasingfunction)]