---
title: "方法 : キー フレームを使用して色をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 色をキー フレームで"
  - "色, アニメーション化 (キー フレームを使用して)"
  - "キー フレーム, アニメーション化 (色を)"
ms.assetid: ab04ffa6-4de9-4d5b-a3b4-4e35d5b2ef35
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : キー フレームを使用して色をアニメーション化する
次の例は、キー フレームを使用して <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> をアニメーション化する方法を示しています。  
  
## 使用例  
 次のコード例では、<xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> プロパティにアニメーションを適用しています。  このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 2 秒間は、<xref:System.Windows.Media.Animation.LinearColorKeyFrame> クラスのインスタンスを使用して、緑から赤へ徐々に色を変更します。  <xref:System.Windows.Media.Animation.LinearColorKeyFrame> のような線形キー フレームを使用すると、値の間に滑らかな線形トランジションが生成されます。  
  
2.  次の 0.5 秒間の終わりには、<xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> クラスのインスタンスを使用して、赤から黄色へすばやく色を変更します。  <xref:System.Windows.Media.Animation.DiscreteColorKeyFrame> のような不連続のキー フレームは、値間で突然の変化を作成します。つまり、この部分のアニメーションの色の変化は短時間で発生し、滑らかではありません。  
  
3.  最後の 2 秒間は、<xref:System.Windows.Media.Animation.SplineColorKeyFrame> クラスのインスタンスを使用して、色を再度変更します \(この例では黄色から緑へ戻ります\)。  <xref:System.Windows.Media.Animation.SplineColorKeyFrame> のような[スプライン](GTMT) キー フレームでは、<xref:System.Windows.Media.Animation.SplineColorKeyFrame.KeySpline%2A> プロパティの値に従って、値の間に可変遷移が作成されます。  この例では、色の変化は最初はゆっくりと進行しますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-csharp[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/ColorAnimationUsingKeyFramesExample.cs#coloranimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/coloranimationusingkeyframesexample.vb#coloranimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#ColorAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ColorAnimationUsingKeyFramesExample.xaml#coloranimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.SolidColorBrush.Color%2A>   
 <xref:System.Windows.Media.SolidColorBrush>   
 <xref:System.Windows.Media.Animation.ColorAnimationUsingKeyFrames>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)