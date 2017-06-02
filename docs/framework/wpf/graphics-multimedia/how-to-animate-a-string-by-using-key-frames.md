---
title: "方法 : キー フレームを使用して文字列をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 文字列をキー フレームで"
  - "キー フレーム, アニメーション化 (文字列を)"
  - "文字列, アニメーション化 (キー フレームを使用して)"
ms.assetid: c62bc9fd-c09a-4227-bce0-0a1ab82049dd
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : キー フレームを使用して文字列をアニメーション化する
この例では、文字列 \(この例では <xref:System.Windows.Controls.Button> コントロールの <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティ\) をキー フレームを使用してアニメーション化する方法について説明します。  
  
## 使用例  
 次のコード例では、<xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames> クラスを使用して <xref:System.Windows.Controls.Button> の <xref:System.Windows.Controls.ContentControl.Content%2A> プロパティにアニメーションを適用しています。  
  
 キー フレームを使用して作成する文字列のアニメーションでは不連続のキー フレームしか使用できないため、この例のすべてのキー フレームでは、<xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> クラスのインスタンスを使用します。  <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame> のような不連続のキー フレームは、値間で突然のジャンプを作成します。つまり、アニメーションの変化は短時間で発生し、滑らかではありません。  
  
 [!code-xml[keyframes_snip#StringAnimationUsingKeyFramesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/keyframes_snip/XAML/StringAnimationUsingKeyFramesExample.xaml#stringanimationusingkeyframeswholepage)]  
  
 サンプル全体については、[キー フレーム アニメーションのサンプル](http://go.microsoft.com/fwlink/?LinkID=160012)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.StringAnimationUsingKeyFrames>   
 <xref:System.Windows.Controls.ContentControl.Content%2A>   
 <xref:System.Windows.Controls.Button>   
 <xref:System.Windows.Media.Animation.DiscreteStringKeyFrame>   
 [キー フレーム アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animations-overview.md)   
 [キー フレームに関する「方法」トピック](../../../../docs/framework/wpf/graphics-multimedia/key-frame-animation-how-to-topics.md)