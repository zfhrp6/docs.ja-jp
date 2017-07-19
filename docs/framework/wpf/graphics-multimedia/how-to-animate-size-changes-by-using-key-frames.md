---
title: "方法 : キー フレームを使用してサイズの変更をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, キー フレームによるサイズ変更"
  - "キー フレーム, アニメーション化 (サイズ変更を)"
  - "サイズ変更, アニメーション化 (キー フレームを使用して)"
ms.assetid: 86bd2950-d4c9-4ec4-aa8d-7dc3ccadded4
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : キー フレームを使用してサイズの変更をアニメーション化する
この例では、キー フレームを使用してサイズの変更をアニメーション化する方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Media.ArcSegment> の <xref:System.Windows.Media.ArcSegment.Size%2A> プロパティをアニメーション化します。  このアニメーションは、次の方法で 3 つのキー フレームを使用します。  
  
1.  アニメーションの最初の 0.5 秒間は、<xref:System.Windows.Media.Animation.LinearSizeKeyFrame> クラスのインスタンスを使用して、円弧のサイズを徐々に大きくします。  <xref:System.Windows.Media.Animation.LinearSizeKeyFrame> のような線形キー フレームを使用すると、値の間に滑らかな線形トランジションが生成されます。  
  
2.  次の 0.5 秒間の終わりには、<xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> クラスのインスタンスを使用して、円弧のサイズを突然大きくします。  <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame> のような不連続キー フレームを使用すると、値と値の間は突然ジャンプします。つまり、サイズが滑らかに変化するのではなく、急に変化します。  
  
3.  最後の 2 秒間は、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame> クラスのインスタンスを使用して、円弧のサイズを大きくします。  <xref:System.Windows.Media.Animation.SplineSizeKeyFrame> のような[スプライン](GTMT) キー フレームでは、<xref:System.Windows.Media.Animation.SplineSizeKeyFrame.KeySpline%2A> プロパティの値に従って、値の間に可変遷移が作成されます。  この例では、円弧のサイズは最初はゆっくり大きくなりますが、時間セグメントの終点に向かって急激に大きくなります。  
  
 [!code-xml[keyframes_snip#SizeAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/SizeAnimationUsingKeyFramesExample.xaml#sizeanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.SizeAnimationUsingKeyFrames>   
 <xref:System.Windows.Media.ArcSegment.Size%2A>   
 <xref:System.Windows.Media.ArcSegment>   
 <xref:System.Windows.Media.Animation.LinearSizeKeyFrame>   
 <xref:System.Windows.Media.Animation.DiscreteSizeKeyFrame>   
 <xref:System.Windows.Media.Animation.SplineSizeKeyFrame>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)