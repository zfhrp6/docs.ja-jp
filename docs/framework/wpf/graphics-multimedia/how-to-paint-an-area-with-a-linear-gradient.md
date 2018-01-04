---
title: "方法 : 線形グラデーションを使用して領域を塗りつぶす"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- linear gradients [WPF], painting with
- brushes [WPF], painting with linear gradients
- painting [WPF], with linear gradients
ms.assetid: 00e0cd04-48c0-4ec5-850e-d321beb37a34
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: eec4ec2fc7ba99081eaafa6803d20c99bebc6c2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-linear-gradient"></a>方法 : 線形グラデーションを使用して領域を塗りつぶす
この例を使用する方法を示しています、<xref:System.Windows.Media.LinearGradientBrush>線形グラデーションで領域を塗りつぶすクラス。 次の例で、<xref:System.Windows.Shapes.Shape.Fill%2A>の<xref:System.Windows.Shapes.Rectangle>赤青の淡い緑から黄色から遷移対角線方向の線形グラデーションで塗りつぶされます。  
  
## <a name="example"></a>例  
 [!code-xaml[GradientBrushExamples_snip#DiagonalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#diagonalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#DiagonalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#diagonalgradient1csharp)]  
  
 次の図は、前述の例で作成したグラデーションを示します。  
  
 ![対角線方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-diagonallgb.jpg "graphicsmm_DiagonalLGB")  
  
 水平方向の線形グラデーションを作成するには、変更、<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>と<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>の<xref:System.Windows.Media.LinearGradientBrush>(0,0.5) に (1,0.5) とします。 次の例で、<xref:System.Windows.Shapes.Rectangle>が水平方向の線形グラデーションを使用して描画します。  
  
 [!code-xaml[GradientBrushExamples_snip#HorizontalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#horizontalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#HorizontalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#horizontalgradient1csharp)]  
  
 次の図は、前述の例で作成したグラデーションを示します。  
  
 ![水平方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-horizontallgb.jpg "graphicsmm_HorizontalLGB")  
  
 垂直方向の線形グラデーションを作成するには、変更、<xref:System.Windows.Media.LinearGradientBrush.StartPoint%2A>と<xref:System.Windows.Media.LinearGradientBrush.EndPoint%2A>の<xref:System.Windows.Media.LinearGradientBrush>(0.5,0) に (0.5,1) とします。 次の例で、<xref:System.Windows.Shapes.Rectangle>が垂直方向の線形グラデーションを使用して描画します。  
  
 [!code-xaml[GradientBrushExamples_snip#VerticalGradient1XAML](../../../../samples/snippets/xaml/VS_Snippets_Wpf/GradientBrushExamples_snip/XAML/LinearGradientBrushExample.xaml#verticalgradient1xaml)]  
  
 [!code-csharp[GradientBrushExamples_snip#VerticalGradient1CSharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GradientBrushExamples_snip/CSharp/LinearGradientBrushExample.cs#verticalgradient1csharp)]  
  
 次の図は、前述の例で作成したグラデーションを示します。  
  
 ![垂直方向の線形グラデーション](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-verticallgb.jpg "graphicsmm_VerticalLGB")  
  
> [!NOTE]
>  このトピックの例では、始点と終点を設定するための既定の座標系を使用します。 既定の座標システムは境界ボックスに対する相対: 0%、境界ボックスの場合は 0、1 は、境界ボックスの 100% を示します。 この座標系を変更するには設定して、<xref:System.Windows.Media.GradientBrush.MappingMode%2A>プロパティ値を<xref:System.Windows.Media.BrushMappingMode.Absolute?displayProperty=nameWithType>です。 絶対座標系は、境界ボックスに相対しません。 値は、ローカル空間に直接変換されます。  
  
 その他の例では、次を参照してください。[ブラシ サンプル](http://go.microsoft.com/fwlink/?LinkID=159973)です。 グラデーションおよびその他の種類のブラシの詳細については、次を参照してください。[純色、グラデーションの概要でペイント](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)です。
