---
title: "方法 : SolidColorBrush の色または不透明度をアニメーション化する | Microsoft Docs"
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
  - "アニメーション, 色 (SolidColorBrush の)"
  - "アニメーション, 不透明度 (SolidColorBrush の)"
  - "色, アニメーション化"
  - "不透明, アニメーション化"
  - "SolidColorBrush, アニメーション化 (色を)"
  - "SolidColorBrush, アニメーション化 (不透明度を)"
ms.assetid: d9154354-843f-4713-bad1-35bb0ba6eaeb
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : SolidColorBrush の色または不透明度をアニメーション化する
この例では、<xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> および <xref:System.Windows.Media.Brush.Opacity%2A> をアニメーション化する方法を説明します。  
  
## 使用例  
 3 つのアニメーションを使用して、<xref:System.Windows.Media.SolidColorBrush> の <xref:System.Windows.Media.SolidColorBrush.Color%2A> と <xref:System.Windows.Media.Brush.Opacity%2A> をアニメーション化する例を次に示します。  
  
-   1 つ目のアニメーション <xref:System.Windows.Media.Animation.ColorAnimation> では、マウスが四角形の中に入ると、ブラシの色が <xref:System.Windows.Media.Colors.Gray%2A> に変更されます。  
  
-   2 つ目のアニメーションである、別の <xref:System.Windows.Media.Animation.ColorAnimation> では、マウスが四角形の外に出ると、ブラシの色が <xref:System.Windows.Media.Colors.Orange%2A> に変更されます。  
  
-   最後のアニメーション <xref:System.Windows.Media.Animation.DoubleAnimation> では、マウスの左ボタンをクリックすると、ブラシの不透明度が 0.0 に変更されます。  
  
 [!code-csharp[brushanimations_snip#SolidColorBrushAnimationExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushanimations_snip/CSharp/SolidColorBrushExample.cs#solidcolorbrushanimationexample)]  
  
 さまざまな種類のブラシをアニメーション化する方法を示した、より完全なサンプルについては、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  アニメーションの詳細については、「[アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)」を参照してください。  
  
 他のアニメーション例との一貫性を保つために、この例のコードでは、<xref:System.Windows.Media.Animation.Storyboard> オブジェクトを使用してアニメーションを適用しています。  ただし、コードで 1 つのアニメーションを適用する場合は、<xref:System.Windows.Media.Animation.Storyboard> よりも <xref:System.Windows.Media.Animation.Animatable.BeginAnimation%2A> メソッドを使用する方が簡単です。  例については、「[ストーリーボードを使用せずにプロパティをアニメーション化する](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-a-property-without-using-a-storyboard.md)」を参照してください。  
  
## 参照  
 [アニメーションの概要](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)   
 [ストーリーボードの概要](../../../../docs/framework/wpf/graphics-multimedia/storyboards-overview.md)   
 [ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)