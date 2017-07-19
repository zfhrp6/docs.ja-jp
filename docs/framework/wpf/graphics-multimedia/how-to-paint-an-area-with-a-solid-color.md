---
title: "方法 : 純色で領域を塗りつぶす | Microsoft Docs"
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
  - "ブラシ, 塗りつぶし (純色による)"
  - "描画, 純色を使用"
  - "純色, 塗りつぶし"
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 純色で領域を塗りつぶす
純色で領域を塗りつぶすには、<xref:System.Windows.Media.Brushes.Red%2A> や <xref:System.Windows.Media.Brushes.Blue%2A> などの定義済みのシステム ブラシを使用します。または、新しい <xref:System.Windows.Media.SolidColorBrush> を作成し、アルファ、赤、緑、および青の値を使用して <xref:System.Windows.Media.SolidColorBrush.Color%2A> を記述することもできます。  XAML では、16 進数表記を使用して純色で領域を塗りつぶすこともできます。  
  
 これらの各手法を使用して <xref:System.Windows.Shapes.Rectangle> を青で塗りつぶす例を次に示します。  
  
## 使用例  
 **定義済みブラシの使用**  
  
 次の例では、定義済みブラシ <xref:System.Windows.Media.Brushes.Blue%2A> を使用して、四角形を青で塗りつぶします。  
  
 [!code-xml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 **16 進数表記の使用**  
  
 次の例では、8 桁の 16 進数表記を使用して、四角形を青で塗りつぶします。  
  
 [!code-xml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 **ARGB 値の使用**  
  
 次の例では <xref:System.Windows.Media.SolidColorBrush> を作成し、その <xref:System.Windows.Media.SolidColorBrush.Color%2A> を青い色に対応する ARGB 値を使用して記述します。  
  
 [!code-xml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 色を記述するその他の方法については、<xref:System.Windows.Media.Color> 構造体を参照してください。  
  
 **関連トピック**  
  
 <xref:System.Windows.Media.SolidColorBrush> およびその他の例の詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」の概要を参照してください。  
  
 このコード例は、<xref:System.Windows.Media.SolidColorBrush> クラスのトピックで取り上げているコード例の一部分です。  サンプル全体については、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.Brushes>