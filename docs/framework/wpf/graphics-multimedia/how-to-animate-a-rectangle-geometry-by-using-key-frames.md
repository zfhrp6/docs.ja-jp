---
title: "方法 : キー フレームを使用して四角形のジオメトリをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, アニメーション化 (キー フレームで RectangleGeometry オブジェクトを)"
  - "キー フレーム, アニメーション化 (RectangleGeometry オブジェクトを)"
  - "RectangleGeometry オブジェクト, アニメーション化 (キー フレームを使用して)"
ms.assetid: a8b45ceb-0e32-4ba1-928f-df6d30db17c6
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : キー フレームを使用して四角形のジオメトリをアニメーション化する
次の例は、キー フレームを使用して <xref:System.Windows.Media.RectangleGeometry> の <xref:System.Windows.Media.RectangleGeometry.Rect%2A> プロパティにアニメーションを適用する方法を示しています。  
  
## 使用例  
 次のコード例では、<xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Media.RectangleGeometry> の <xref:System.Windows.Media.RectangleGeometry.Rect%2A> プロパティにアニメーションを適用しています。  このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 2 秒間では、<xref:System.Windows.Media.Animation.LinearRectKeyFrame> クラスのインスタンスを使用して、四角形の位置、幅、および高さが徐々に変化する様子をアニメーション化します。  <xref:System.Windows.Media.Animation.LinearRectKeyFrame> のような線形キー フレームを使用すると、値の間に滑らかな線形トランジションが生成されます。  
  
2.  次の 0.5 秒間の終わりには、<xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> クラスのインスタンスを使用して、四角形の高さを突然低くします。  <xref:System.Windows.Media.Animation.DiscreteRectKeyFrame> のような不連続のキー フレームは、値間で突然の変化を作成します。つまり、高さの減少は短時間で発生し、滑らかではありません。  
  
3.  最後の 2 秒間では、<xref:System.Windows.Media.Animation.SplineRectKeyFrame> クラスのインスタンスを使用して、四角形を元のサイズと位置に戻します。  <xref:System.Windows.Media.Animation.SplineRectKeyFrame> のような[スプライン](GTMT) キー フレームでは、<xref:System.Windows.Media.Animation.SplineRectKeyFrame.KeySpline%2A> プロパティの値に従って、値の間に可変遷移が作成されます。  この例では、変化は最初はゆっくりしていますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/RectAnimationUsingKeyFramesExample.cs#rectanimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/rectanimationusingkeyframesexample.vb#rectanimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#RectAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/RectAnimationUsingKeyFramesExample.xaml#rectanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.RectangleGeometry>   
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>   
 <xref:System.Windows.Media.Animation.RectAnimationUsingKeyFrames>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)