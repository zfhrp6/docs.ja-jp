---
title: "方法 : グラデーション ストップの位置または色をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 色 (GradientStop オブジェクトの)"
  - "アニメーション, 位置 (GradientStop オブジェクトの)"
  - "色, アニメーション化"
  - "GradientStop オブジェクト, アニメーション化 (色を)"
  - "GradientStop オブジェクト, アニメーション化 (位置を)"
  - "位置, アニメーション化"
ms.assetid: 6f5b8b47-6c32-4b8e-98ee-fdf6515ec843
caps.latest.revision: 5
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 5
---
# 方法 : グラデーション ストップの位置または色をアニメーション化する
この例では、<xref:System.Windows.Media.GradientStop> オブジェクトの <xref:System.Windows.Media.GradientStop.Color%2A> および <xref:System.Windows.Media.GradientStop.Offset%2A> をアニメーション表示する方法を説明します。  
  
## 使用例  
 <xref:System.Windows.Media.LinearGradientBrush> の内部に 3 つのグラデーション終了位置をアニメーション化する例を次に示します。  この例では、それぞれが異なるグラデーション終了位置をアニメーション化する 3 つのアニメーションを使用しています。  
  
-   最初のアニメーション <xref:System.Windows.Media.Animation.DoubleAnimation> は、最初のグラデーション終了位置の <xref:System.Windows.Media.GradientStop.Offset%2A> を 0.0 から 1.0 までアニメーション化し、0.0 まで戻します。  その結果、グラデーションの最初の色は、四角形の左側から右側の方向に変化し、左側に戻ります。  
  
-   2 番目のアニメーション <xref:System.Windows.Media.Animation.ColorAnimation> は、2 番目のグラデーション終了位置の <xref:System.Windows.Media.GradientStop.Color%2A> を <xref:System.Windows.Media.Colors.Purple%2A> から <xref:System.Windows.Media.Colors.Yellow%2A> の方向にアニメーション化し、<xref:System.Windows.Media.Colors.Purple%2A> に戻します。  その結果、グラデーションの中間の色は、紫色から黄色に変化し、紫色に戻ります。  
  
-   3 番目のアニメーションである、もう 1 つの <xref:System.Windows.Media.Animation.ColorAnimation> は、3 番目のグラデーション終了位置の <xref:System.Windows.Media.GradientStop.Color%2A> の不透明度を \-1 だけアニメーション化した後、元に戻ります。  その結果、グラデーションの3 番目の色は消えていき、再び不透明になります。  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/GradientStopAnimationExample.cs#graphicsmmgradientanimationexampleswholepage)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/gradientstopanimationexample.vb#graphicsmmgradientanimationexampleswholepage)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMGradientAnimationExamplesWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/GradientStopAnimationExample.xaml#graphicsmmgradientanimationexampleswholepage)]  
  
 この例では <xref:System.Windows.Media.LinearGradientBrush> を使用していますが、このプロセスは、<xref:System.Windows.Media.RadialGradientBrush> 内部で <xref:System.Windows.Media.GradientStop> オブジェクトをアニメーション化する場合でも同じです。  
  
 その他の例については、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.GradientStop>   
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)