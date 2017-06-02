---
title: "方法 : TileBrush を使用してさまざまなタイル パターンを作成する | Microsoft Docs"
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
  - "作成, TileBrush を使用したタイル パターン"
  - "タイル パターン, 作成"
  - "TileBrush, 作成 (タイル パターンを)"
ms.assetid: 5aa46632-3527-4668-9d8d-0375c8af28aa
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : TileBrush を使用してさまざまなタイル パターンを作成する
この例では、<xref:System.Windows.Media.TileBrush> の <xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティを使用してパターンを作成する方法を示します。  
  
 <xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティを使用すると、<xref:System.Windows.Media.TileBrush> のコンテンツの繰り返し方法 \(並べて表示して出力領域を塗りつぶす\) を指定することができます。  パターンを作成するには、<xref:System.Windows.Media.TileBrush.TileMode%2A> を <xref:System.Windows.Media.TileMode>、<xref:System.Windows.Media.TileMode>、<xref:System.Windows.Media.TileMode>、または <xref:System.Windows.Media.TileMode> に設定します。  また、塗りつぶす領域よりもパターンが小さい場合を考慮し、<xref:System.Windows.Media.TileBrush> の <xref:System.Windows.Media.TileBrush.Viewport%2A> を設定する必要があります。これを設定しない場合は、<xref:System.Windows.Media.TileBrush.TileMode%2A> の設定にかかわらず、単一のタイルだけが生成されます。  
  
## 使用例  
 次の例では、5 つの <xref:System.Windows.Media.DrawingBrush> オブジェクトを作成し、それぞれ異なる <xref:System.Windows.Media.TileBrush.TileMode%2A> 設定を与え、5 つの四角形を描画するために使用します。  この例では <xref:System.Windows.Media.DrawingBrush> クラスを使用して <xref:System.Windows.Media.TileBrush.TileMode%2A> の動作を示していますが、<xref:System.Windows.Media.TileBrush.TileMode%2A> プロパティは、すべての <xref:System.Windows.Media.TileBrush> オブジェクト、つまり <xref:System.Windows.Media.ImageBrush>、<xref:System.Windows.Media.VisualBrush>、および <xref:System.Windows.Media.DrawingBrush> に対してもまったく同じように動作します。  
  
 この例が生成する出力を次の図に示します。  
  
 ![TileBrush を並べて表示する例の出力結果](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-drawingbrushtilemodeexample.png "graphicsmm\_DrawingBrushTileModeExample")  
TileMode プロパティで作成されたタイル パターン  
  
 [!code-csharp[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/TileModeExample.cs#graphicsmmdrawingbrushtilemodeexample)]
 [!code-vb[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/tilemodeexample.vb#graphicsmmdrawingbrushtilemodeexample)]
 [!code-xml[BrushesIntroduction_snip#GraphicsMMDrawingBrushTileModeExample](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/TileModeExample.xaml#graphicsmmdrawingbrushtilemodeexample)]  
  
## 参照  
 [TileBrush のタイル サイズを設定する](../../../../docs/framework/wpf/graphics-multimedia/how-to-set-the-tile-size-for-a-tilebrush.md)   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)