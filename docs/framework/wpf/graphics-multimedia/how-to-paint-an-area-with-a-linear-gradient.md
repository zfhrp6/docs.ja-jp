---
title: "方法 : 線形グラデーションを使用して領域を塗りつぶす | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-wpf"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "ブラシ, 塗りつぶし (線形グラデーションによる)"
  - "線形グラデーション, 塗りつぶし"
  - "描画, 線形グラデーションでの"
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : 線形グラデーションを使用して領域を塗りつぶす
この例では、<xref:System.Windows.Media.LinearGradientBrush> クラスを使用して、線形グラデーションで領域を塗りつぶす方法を示します。  次の例では、黄色から赤、青、淡い緑と変化する斜めの線形グラデーションを使用して、<xref:System.Windows.Shapes.Rectangle> の <xref:System.Windows.Shapes.Shape.Fill%2A> を塗りつぶします。  
  
## 使用例  
 [!code-xml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 前の例で作成したグラデーションを次の図に示します。  
  
 ![対角線方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.png "graphicsmm\_DiagonalLGB")  
  
 水平方向の線形グラデーションを作成するには、<xref:System.Windows.Media.LinearGradientBrush> の <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> と <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> を \(0,0.5\) と \(1,0.5\) に変更します。  次の例では、水平方向の線形グラデーションを使用して、<xref:System.Windows.Shapes.Rectangle> を塗りつぶします。  
  
 [!code-xml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 前の例で作成したグラデーションを次の図に示します。  
  
 ![水平方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.png "graphicsmm\_HorizontalLGB")  
  
 垂直方向の線形グラデーションを作成するには、<xref:System.Windows.Media.LinearGradientBrush> の <xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A> と <xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A> を \(0.5,0\) と \(0.5,1\) に変更します。  次の例では、垂直方向の線形グラデーションを使用して、<xref:System.Windows.Shapes.Rectangle> を塗りつぶします。  
  
 [!code-xml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 前の例で作成したグラデーションを次の図に示します。  
  
 ![垂直方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.png "graphicsmm\_VerticalLGB")  
  
> [!NOTE]
>  このトピックのグラデーションの例では、開始点と終了点の設定に既定の座標系を使用しています。  既定の座標系は境界ボックスに対して相対的です。0 は境界ボックスの 0% を示し、1 は境界ボックスの 100% を示します。  この座標系を変更するには、<xref:System.Windows.Media.GradientBrush.MappingMode%2A> プロパティを <xref:System.Windows.Media.BrushMappingMode?displayProperty=fullName> という値に設定します。  絶対座標系は、境界ボックスに対して相対的ではありません。  値は、ローカル空間で直接解釈されます。  
  
 その他の例については、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  グラデーションとその他の種類のブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。