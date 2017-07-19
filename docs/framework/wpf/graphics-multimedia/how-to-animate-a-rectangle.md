---
title: "方法 : 四角形をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 四角形"
  - "四角形, アニメーション化"
ms.assetid: 572ffb95-790d-4ace-adbf-b2ea8a90e75b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : 四角形をアニメーション化する
この例では、四角形のサイズと位置の変化をアニメーション化する方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.Animation.RectAnimation> クラスのインスタンスを使用して、<xref:System.Windows.Media.RectangleGeometry> の <xref:System.Windows.Media.RectangleGeometry.Rect%2A> プロパティをアニメーション化し、四角形のサイズと位置の変化をアニメーション化します。  
  
 [!code-csharp[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/RectAnimationExample.cs#rectanimationwholepage)]
 [!code-vb[BasicAnimations_snip#RectAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/RectAnimationExample.vb#rectanimationwholepage)]  
  
## 参照  
 <xref:System.Windows.Media.Animation.RectAnimation>   
 <xref:System.Windows.Media.RectangleGeometry.Rect%2A>   
 <xref:System.Windows.Media.RectangleGeometry>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)