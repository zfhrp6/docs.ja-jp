---
title: "方法 : 放射状グラデーションを使用して領域を塗りつぶす | Microsoft Docs"
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
  - "ブラシ, 放射状グラデーションによる塗りつぶし"
  - "描画, 放射状グラデーションを使用"
  - "放射状グラデーション, 塗りつぶし"
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : 放射状グラデーションを使用して領域を塗りつぶす
この例では、<xref:System.Windows.Media.RadialGradientBrush> クラスを使用して、放射状グラデーションで領域を塗りつぶす方法を示します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.RadialGradientBrush> を使用して、黄色から赤、青、淡い緑と変化する放射状グラデーションで、四角形を塗りつぶします。  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 前の例のグラデーションを次の図に示します。  グラデーションの終了位置が強調表示されています。  
  
 ![放射状グラデーションのグラデーション ストップ](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk\_graphicsmm\_4gradientstops\_rg")  
  
> [!NOTE]
>  このトピックの例では、制御点の設定に既定の座標系を使用しています。  既定の座標系は境界ボックスに対して相対的です。0 は境界ボックスの 0% を示し、1 は境界ボックスの 100% を示します。  この座標系を変更するには、<xref:System.Windows.Media.GradientBrush.MappingMode%2A> プロパティを <xref:System.Windows.Media.BrushMappingMode> という値に設定します。  絶対座標系は、境界ボックスに対して相対的ではありません。  値は、ローカル空間で直接解釈されます。  
  
 その他の <xref:System.Windows.Media.RadialGradientBrush> の例については、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  グラデーションとその他の種類のブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。