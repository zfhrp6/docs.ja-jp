---
title: "方法 : キー フレームを使用してブール値をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, ブール値 (キー フレームを使用してアニメーション化)"
  - "ブール値, アニメーション化 (キー フレームを使用して)"
  - "キー フレーム, アニメーション化 (ブール値を)"
ms.assetid: 4b0fac96-6231-4fcf-9775-4dd673ddc785
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : キー フレームを使用してブール値をアニメーション化する
この例では、<xref:System.Windows.Controls.Button> コントロールの Boolean プロパティ値をキー フレームを使用してアニメーション化する方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames> クラスを使用して、<xref:System.Windows.Controls.Button> コントロールの <xref:System.Windows.UIElement.IsEnabled%2A> プロパティをアニメーション化します。  この例のすべてのキー フレームでは、<xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> クラスのインスタンスを使用します。  <xref:System.Windows.Media.Animation.DiscreteBooleanKeyFrame> のような不連続のキー フレームは、値間で突然のジャンプを作成します。つまり、アニメーションの動きはぎくしゃくしています。  
  
 [!code-csharp[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/keyframes_snip/CSharp/BooleanAnimationUsingKeyFramesExample.cs#booleananimationusingkeyframeswholepage)]
 [!code-vb[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/keyframes_snip/visualbasic/booleananimationusingkeyframesexample.vb#booleananimationusingkeyframeswholepage)]
 [!code-xml[keyframes_snip#BooleanAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/BooleanAnimationUsingKeyFramesExample.xaml#booleananimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.BooleanAnimationUsingKeyFrames>   
 <xref:System.Windows.UIElement.IsEnabled%2A>   
 <xref:System.Windows.Controls.Button>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)