---
title: "方法 : PointAnimation を使用してオブジェクトの位置をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, PointAnimation"
  - "クラス, PointAnimation"
  - "グラフィックス [WPF], アニメーション"
  - "PointAnimation クラス"
ms.assetid: 42310977-cc90-438a-8a47-0345898e01be
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : PointAnimation を使用してオブジェクトの位置をアニメーション化する
この例では、<xref:System.Windows.Media.Animation.PointAnimation> クラスを使用して、<xref:System.Windows.Shapes.Path> に沿ってオブジェクトをアニメーション化する方法を示します。  
  
## 使用例  
 次の例では、画面上のある点から別の点まで、<xref:System.Windows.Shapes.Path> に沿って楕円を移動します。  この例は、<xref:System.Windows.Media.Animation.PointAnimation> を使用して <xref:System.Windows.Media.EllipseGeometry.Center%2A> プロパティをアニメーション化することで、<xref:System.Windows.Media.EllipseGeometry> の位置をアニメーション化します。  
  
 [!code-csharp[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BasicAnimations_snip/CSharp/PointAnimationExample.cs#pointanimationwholepage)]
 [!code-vb[BasicAnimations_snip#PointAnimationWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BasicAnimations_snip/VisualBasic/PointAnimationExample.vb#pointanimationwholepage)]  
  
## 参照  
 <xref:System.Windows.Media.Animation.PointAnimation>   
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.EllipseGeometry>   
 <xref:System.Windows.Media.EllipseGeometry.Center%2A>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [グラフィックスとマルチメディア](../../../../docs/framework/wpf/graphics-multimedia/index.md)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/graphics-how-to-topics.md)   
 [Animation and Timing](http://msdn.microsoft.com/ja-jp/7d83765b-d5ae-41b1-b423-80206e1124aa)   
 [方法のトピック](../../../../docs/framework/wpf/graphics-multimedia/animation-and-timing-how-to-topics.md)