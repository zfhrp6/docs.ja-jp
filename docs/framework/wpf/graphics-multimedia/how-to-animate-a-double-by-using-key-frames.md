---
title: "方法 : キー フレームを使用して Double 値をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, Double をキー フレームで"
  - "倍精度, アニメーション化 (キー フレームを使用して)"
  - "キー フレーム, アニメーション化 (Double を)"
ms.assetid: 3a1a7dba-7694-4907-8a2f-3408baebfa82
caps.latest.revision: 16
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 15
---
# 方法 : キー フレームを使用して Double 値をアニメーション化する
この例では、<xref:System.Double> を受け取るプロパティの値をキー フレームを使用してアニメーション化する方法について説明します。  
  
## 使用例  
 次の例では、画面を横切るように四角形を移動します。  この例では、<xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> クラスを使用して、<xref:System.Windows.Shapes.Rectangle> に適用される <xref:System.Windows.Media.TranslateTransform> の <xref:System.Windows.Media.TranslateTransform.X%2A> プロパティをアニメーション化します。  無期限に繰り返すこのアニメーションでは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 3 秒間は、<xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> クラスのインスタンスを使用して、開始位置からパスに沿って 500 の位置まで、一定の速度で四角形を移動します。  <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame> のような線形キー フレームを使用すると、値の間に滑らかな線形トランジションが生成されます。  
  
2.  4 秒目の終わりに、<xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> クラスのインスタンスを使用して、四角形を突然次の位置まで移動します。  <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame> のような不連続キー フレームを使用すると、ある値から次の値へのジャンプが生成されます。  この例では、開始位置にあった四角形が突然 500 の位置に出現します。  
  
3.  最後の 2 秒間は、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> クラスのインスタンスを使用して、四角形を開始位置まで戻します。  <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame> のような[スプライン](GTMT) キー フレームでは、<xref:System.Windows.Media.Animation.SplineDoubleKeyFrame.KeySpline%2A> プロパティの値に従って、値の間に可変遷移が作成されます。  この例では、四角形の動きは最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/AltDoubleAnimationUsingKeyFramesExample.cs#altdoubleanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/altdoubleanimationusingkeyframesexample.vb#altdoubleanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#AltDoubleAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/AltDoubleAnimationUsingKeyFramesExample.xaml#altdoubleanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
 他のアニメーション例との一貫性を保つために、この例のコードでは、<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用して <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames> を適用しています。  ただし、コードで 1 つのアニメーションを適用する場合は、<xref:System.Windows.Media.Animation.Storyboard> よりも <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用する方が簡単です。  例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.DoubleAnimationUsingKeyFrames>   
 <xref:System.Windows.Shapes.Rectangle>   
 <xref:System.Windows.Media.Animation.LinearDoubleKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteDoubleKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineDoubleKeyFrame>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)