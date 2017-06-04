---
title: "方法 : ブラシを変換する | Microsoft Docs"
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
  - "ブラシ, 回転 (コンテンツを)"
  - "ブラシ, Transform プロパティ"
  - "回転 (ブラシのコンテンツを)"
ms.assetid: ebada2f9-f01f-4863-9ea2-c2e4e51610f1
caps.latest.revision: 13
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 12
---
# 方法 : ブラシを変換する
この例では、2 つの変換プロパティ <xref:System.Windows.Media.Brush.RelativeTransform%2A> と <xref:System.Windows.Media.Brush.Transform%2A> を使用して <xref:System.Windows.Media.Brush> オブジェクトを変換する方法を示します。  
  
 次の例では、<xref:System.Windows.Media.RotateTransform> を使用して、<xref:System.Windows.Media.ImageBrush> のコンテンツを 45°回転します。  
  
 次の図は、それぞれ、<xref:System.Windows.Media.RotateTransform> を適用していない状態、<xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティに適用した状態、および <xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.Brush.Transform%2A> プロパティに適用した状態の <xref:System.Windows.Media.ImageBrush> を示しています。  
  
 ![ブラシ RelativeTransform と変換の設定](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-transformandrelativetransform.png "wcpsdk\_graphicsmm\_transformandrelativetransform")  
  
## 使用例  
 最初の例では、<xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.ImageBrush> の <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティに適用しています。  <xref:System.Windows.Media.RotateTransform> オブジェクトの <xref:System.Windows.Media.RotateTransform.CenterX%2A> プロパティおよび <xref:System.Windows.Media.RotateTransform.CenterY%2A> プロパティは、コンテンツの中心点の相対座標である 0.5 に設定されています。  その結果、<xref:System.Windows.Media.ImageBrush> のコンテンツはその中心を軸にして回転します。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushrelativetransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushrelativetransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushRelativeTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushrelativetransformexample)]  
  
 2 番目の例でも、<xref:System.Windows.Media.RotateTransform> を <xref:System.Windows.Media.ImageBrush> に適用していますが、<xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティの代わりに <xref:System.Windows.Media.Brush.Transform%2A> プロパティを使用しています。  
  
 ブラシをその中心を軸に回転するために、<xref:System.Windows.Media.RotateTransform> オブジェクトの <xref:System.Windows.Media.RotateTransform.CenterX%2A> プロパティおよび <xref:System.Windows.Media.RotateTransform.CenterY%2A> プロパティを絶対座標に設定しています。  このブラシは 175 × 90 [ピクセル](GTMT)の四角形を塗りつぶすため、四角形の中心点は \(87.5, 45\) になります。  
  
 [!code-csharp[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/BrushTransformExample.cs#imagebrushtransformexample)]
 [!code-vb[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/brushtransformexample.vb#imagebrushtransformexample)]
 [!code-xml[BrushesIntroduction_snip#ImageBrushTransformExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/BrushTransformExample.xaml#imagebrushtransformexample)]  
  
 <xref:System.Windows.Media.Brush.RelativeTransform%2A> プロパティと <xref:System.Windows.Media.Brush.Transform%2A> プロパティの機能の詳細については、「[ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)」を参照してください。  
  
 サンプル全体については、[ブラシのサンプル](http://go.microsoft.com/fwlink/?LinkID=159973)を参照してください。  ブラシの詳細については、「[純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)」を参照してください。  
  
## 参照  
 [ブラシの変換の概要](../../../../docs/framework/wpf/graphics-multimedia/brush-transformation-overview.md)   
 [純色およびグラデーションによる塗りつぶしの概要](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md)   
 [変換の概要](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)