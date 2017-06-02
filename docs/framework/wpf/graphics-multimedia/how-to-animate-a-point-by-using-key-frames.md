---
title: "方法 : キー フレームを使用して点をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 点をキー フレームで"
  - "キー フレーム, アニメーション化 (点を)"
  - "点, アニメーション化 (キー フレームを使用して)"
ms.assetid: d2e2ef10-0773-4133-856e-d41c09f60ded
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : キー フレームを使用して点をアニメーション化する
<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Point> をアニメーション化する方法を次の例に示します。  
  
## 使用例  
 次の例では、三角形のパスに沿って楕円を移動します。  この例では、<xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Media.EllipseGeometry> の <xref:System.Windows.Media.EllipseGeometry.Center%2A> プロパティをアニメーション化します。  このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 0.5 秒間は、<xref:System.Windows.Media.Animation.LinearPointKeyFrame> クラスのインスタンスを使用して、開始位置から一定の速度で、パスに沿って楕円を移動します。  <xref:System.Windows.Media.Animation.LinearPointKeyFrame> のようなリニア キー フレームは、値間の滑らかな線形補間を作成します。  
  
2.  次の 0.5 秒間の終わりには、<xref:System.Windows.Media.Animation.DiscretePointKeyFrame> クラスのインスタンスを使用して、楕円をパスに沿って次の位置にいきなり移動します。  <xref:System.Windows.Media.Animation.DiscretePointKeyFrame> のような不連続キー フレームを使用すると、ある値から次の値へのジャンプが生成されます。  
  
3.  最後の 2 秒間は、<xref:System.Windows.Media.Animation.SplinePointKeyFrame> クラスのインスタンスを使用して、楕円を開始位置まで戻します。  <xref:System.Windows.Media.Animation.SplinePointKeyFrame> のような[スプライン](GTMT) キー フレームでは、<xref:System.Windows.Media.Animation.SplinePointKeyFrame.KeySpline%2A> プロパティの値に従って、値間の可変遷移が作成されます。  この例では、アニメーションは最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/PointAnimationUsingKeyFramesExample.cs#pointanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/pointanimationusingkeyframesexample.vb#pointanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#PointAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/PointAnimationUsingKeyFramesExample.xaml#pointanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
 他のアニメーション例との一貫性を保つために、この例のコードでは、<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用して <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames> を適用しています。  ただし、コードで 1 つのアニメーションを適用する場合は、<xref:System.Windows.Media.Animation.Storyboard> よりも <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用する方が簡単です。  例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.PointAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.EllipseGeometry.Center%2A?displayProperty=fullName>   
 <xref:System.Windows.Media.EllipseGeometry>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)