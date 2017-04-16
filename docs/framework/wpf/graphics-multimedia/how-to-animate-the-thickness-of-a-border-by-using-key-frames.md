---
title: "方法 : キー フレームを使用して境界線の太さをアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 境界線の太さ (キー フレームを使用してアニメーション化)"
  - "境界線の太さ, アニメーション化 (キー フレームを使用して)"
  - "キー フレーム, アニメーション化 (境界線の太さを)"
ms.assetid: 3a9cb463-0a63-407d-aae7-3fbb1a559947
caps.latest.revision: 12
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : キー フレームを使用して境界線の太さをアニメーション化する
この例では、<xref:System.Windows.Controls.Border> の <xref:System.Windows.Controls.Control.BorderThickness%2A> プロパティをアニメーション化する方法を説明します。  
  
## 使用例  
 次のコード例では、<xref:System.Windows.Media.Animation.ThicknessAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Controls.Border> の <xref:System.Windows.Controls.Control.BorderThickness%2A> プロパティにアニメーションを適用しています。  このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  最初の 0.5 秒間は、<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> クラスのインスタンスを使用して、境界線の太さを徐々に太くします。  この例では、<xref:System.Windows.Media.Animation.LinearThicknessKeyFrame> を使用して、値から値への滑らかで直線的な増加を作成します。  
  
2.  次の 0.5 秒間の終わりには、<xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> クラスのインスタンスを使用して、境界線の太さを突然太くします。  <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame> からこのような不連続のキー フレームを派生すると、値の間に急なジャンプを作成します。つまり、アニメーションの動きはぎくしゃくします。  
  
3.  最後の 2 秒間は、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> クラスのインスタンスを使用して、境界線の太さを細くします。  <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame> からこのような[スプライン](GTMT) キー フレームを派生すると、<xref:System.Windows.Media.Animation.SplineThicknessKeyFrame.KeySpline%2A> プロパティの値に従って、値の間に可変遷移が作成されます。  このキー フレームでは、アニメーションはゆっくりと始まりますが、時間セグメントの終点に向かって急激に速くなります。  
  
 [!code-xml[keyframes_snip#ThicknessAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/ThicknessAnimationUsingKeyFramesExample.xaml#thicknessanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.LinearThicknessKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteThicknessKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineThicknessKeyFrame>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)   
 [BorderThickness 値をアニメーション化する](../../../../docs/framework/wpf/controls/how-to-animate-a-borderthickness-value.md)