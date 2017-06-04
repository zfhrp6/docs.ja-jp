---
title: "方法 : RectangleGeometry を使用して四角形を定義する | Microsoft Docs"
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
  - "クラス, RectangleGeometry"
  - "グラフィックス [WPF], 四角形"
  - "RectangleGeometry クラス"
  - "四角形, 作成 (RectangleGeometry クラスを使用して)"
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : RectangleGeometry を使用して四角形を定義する
この例では、<xref:System.Windows.Media.RectangleGeometry> クラスを使用して四角形を記述する方法を説明します。  
  
## 使用例  
 <xref:System.Windows.Media.RectangleGeometry> オブジェクトを作成してレンダリングする方法の例を次に示します。  四角形の相対位置およびサイズは、<xref:System.Windows.Rect> 構造体によって定義されます。  相対位置は `50,50`、高さと幅は両方とも `25` で、正方形が作成されます。  四角形の内部は <xref:System.Windows.Media.Brushes.LemonChiffon%2A> ブラシで塗りつぶし、アウトラインは太さ `1` の <xref:System.Windows.Media.Brushes.Black%2A> ストロークで描きます。  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.png "graphicsmm\_rectangle")  
RectangleGeometry  
  
 この例では、<xref:System.Windows.Shapes.Path> 要素を <xref:System.Windows.Media.RectangleGeometry> のレンダリングに使用しましたが、<xref:System.Windows.Media.RectangleGeometry> オブジェクトには他にもさまざまな使用方法があります。  たとえば、<xref:System.Windows.Media.RectangleGeometry> を使用して <xref:System.Windows.UIElement> の <xref:System.Windows.UIElement.Clip%2A> や <xref:System.Windows.Media.GeometryDrawing> の <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> を指定できます。  
  
 その他の単純な図形座標クラスとして、<xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.EllipseGeometry> などがあります。  これらの図形座標およびさらに複雑な図形座標は、<xref:System.Windows.Media.PathGeometry> または <xref:System.Windows.Media.StreamGeometry> を使用して作成することもできます。  
  
## 参照  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [複合図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)