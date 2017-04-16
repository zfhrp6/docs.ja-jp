---
title: "方法 : TileBrush のタイル サイズを設定する | Microsoft Docs"
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
  - "TileBrush, サイズ (タイルの)"
  - "Viewport プロパティ (TileBrush の)"
ms.assetid: 04f41090-1b46-4e36-832f-d27d28708b8c
caps.latest.revision: 15
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : TileBrush のタイル サイズを設定する
この例では、<xref:System.Windows.Media.TileBrush> のタイル サイズを設定する方法について説明します。  既定では、<xref:System.Windows.Media.TileBrush> は、描画する領域を完全に塗りつぶす 1 つのタイルを生成します。  <xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティと <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> プロパティを設定することで、この動作をオーバーライドできます。  
  
 <xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティは、<xref:System.Windows.Media.TileBrush> のタイル サイズを指定します。  既定では、<xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティの値は、描画する領域のサイズを基準にした相対値です。  <xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティでタイル サイズの絶対値を指定するには、<xref:System.Windows.Media.TileBrush.ViewportUnits%2A> プロパティを <xref:System.Windows.Media.BrushMappingMode> に設定します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.TileBrush> の一種である <xref:System.Windows.Media.ImageBrush> を使用して、四角形をタイルで塗りつぶします。  各タイルを、出力領域 \(四角形\) の 50% x 50% に設定しています。  結果として、四角形はイメージの 4 つの投影で塗りつぶされます。  
  
 この例が生成する出力を次の図に示します。  
  
 ![イメージ ブラシを並べて表示する例](../../../../docs/framework/wpf/graphics-multimedia/media/0.png "0")  
  
 [!code-csharp[UsingImageBrush_snip#RelativeTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#relativetilesizeexample)]  
  
 次の例では、<xref:System.Windows.Media.ImageBrush> を作成し、その <xref:System.Windows.Media.TileBrush.Viewport%2A> を `0,0,25,25` に、また <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> を <xref:System.Windows.Media.BrushMappingMode> に設定して、そのイメージ ブラシを使用して別の四角形を塗りつぶします。  結果として、幅が 25 [ピクセル](GTMT)で高さが 25 [ピクセル](GTMT)のタイルが生成されます。  
  
 この例が生成する出力を次の図に示します。  
  
 ![ビューポート 0,0,0.25,0.25 で並べて表示される TileBrush](../../../../docs/framework/wpf/graphics-multimedia/media/25x25viewport.png "25x25viewport")  
  
 [!code-csharp[UsingImageBrush_snip#AbsoluteTileSizeExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/UsingImageBrush_snip/CSharp/TileSizeExample.cs#absolutetilesizeexample)]  
  
 前の例は、大きなサンプルの一部です。  サンプル全体については、[ImageBrush のサンプル](http://go.microsoft.com/fwlink/?LinkID=160005)を参照してください。  
  
 この例では <xref:System.Windows.Media.ImageBrush> クラスを使用していますが、<xref:System.Windows.Media.TileBrush.Viewport%2A> プロパティと <xref:System.Windows.Media.TileBrush.ViewportUnits%2A> プロパティは、他の <xref:System.Windows.Media.TileBrush> オブジェクト、つまり <xref:System.Windows.Media.DrawingBrush> と <xref:System.Windows.Media.VisualBrush> に対してもまったく同じように動作します。  <xref:System.Windows.Media.ImageBrush> およびその他の <xref:System.Windows.Media.TileBrush> オブジェクトの詳細については、「[イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)」を参照してください。  
  
## 参照  
 <xref:System.Windows.Media.TileBrush>   
 [イメージ、描画、およびビジュアルによる塗りつぶし](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)   
 [TileBrush を使用してさまざまなタイル パターンを作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-different-tile-patterns-with-a-tilebrush.md)