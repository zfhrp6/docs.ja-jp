---
title: "方法 : BorderThickness 値をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 変更 (境界線の太さの)"
  - "境界線の太さ, アニメーション化 (変更を)"
ms.assetid: fd021978-f74b-4e7b-a7f7-3987dcad9e0f
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : BorderThickness 値をアニメーション化する
この例は、<xref:System.Windows.Media.Animation.ThicknessAnimation> クラスを使用して境界線の太さ変更をアニメーション化する方法を示します。  
  
## 使用例  
 <xref:System.Windows.Media.Animation.ThicknessAnimation> を使用して境界線の太さをアニメーション化する例を次に示します。  この例では、<xref:System.Windows.Controls.Border> の <xref:System.Windows.Controls.Border.BorderThickness%2A> プロパティを使用します。  
  
 [!code-csharp[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/ThicknessAnimationExample.cs#thicknessanimationwholepage)]
 [!code-vb[BasicAnimations_snip#ThicknessAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/ThicknessAnimationExample.vb#thicknessanimationwholepage)]  
  
 サンプル全体については、[アニメーション サンプル ギャラリー](http://go.microsoft.com/fwlink/?LinkID=159969)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Animation.ThicknessAnimation>   
 <xref:System.Windows.Controls.Border.BorderThickness%2A>   
 <xref:System.Windows.Controls.Border>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)   
 [キー フレームを使用して境界線の太さをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-the-thickness-of-a-border-by-using-key-frames.md)