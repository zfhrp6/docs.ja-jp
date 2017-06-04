---
title: "方法 : GeometryDrawing を作成する | Microsoft Docs"
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
  - "クラス, GeometryDrawing"
  - "GeometryDrawing クラス"
  - "グラフィックス, GeometryDrawing クラス"
  - "レンダリング可能な図形"
  - "形状, レンダリング可能"
ms.assetid: 11d3c096-91ba-4d41-9bba-aeac0db70f97
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : GeometryDrawing を作成する
この例では、<xref:System.Windows.Media.GeometryDrawing> を作成して表示する方法を示します。  <xref:System.Windows.Media.GeometryDrawing> を使用すると、<xref:System.Windows.Media.Pen> と <xref:System.Windows.Media.Brush> を <xref:System.Windows.Media.Geometry> に関連付けることで、塗りつぶしとアウトラインを使用して図形を作成できます。  <xref:System.Windows.Media.GeometryDrawing.Geometry%2A> は図形の構造を記述し、<xref:System.Windows.Media.GeometryDrawing.Brush%2A> は図形の塗りつぶしを記述し、<xref:System.Windows.Media.GeometryDrawing.Pen%2A> は図形のアウトラインを記述します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.GeometryDrawing> を使用して図形をレンダリングします。  図形は、1 つの <xref:System.Windows.Media.GeometryGroup> と 2 つの <xref:System.Windows.Media.EllipseGeometry> オブジェクトによって示されます。  図形の内部は <xref:System.Windows.Media.LinearGradientBrush> で塗りつぶし、図形のアウトラインは <xref:System.Windows.Media.Brushes.Black%2A> <xref:System.Windows.Media.Pen> で描画します。  <xref:System.Windows.Media.GeometryDrawing> は、<xref:System.Windows.Media.ImageDrawing> と <xref:System.Windows.Controls.Image> 要素を使用して表示されます。  
  
 [!code-csharp[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/GeometryDrawingExample.cs#geometrydrawingexamplewholepage)]
 [!code-xml[DrawingMiscSnippets_snip#GeometryDrawingExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/DrawingMiscSnippets_snip/XAML/GeometryDrawingExample.xaml#geometrydrawingexamplewholepage)]  
  
 結果として作成される <xref:System.Windows.Media.GeometryDrawing> を次の図に示します。  
  
 ![2 つの楕円の GeometryDrawing](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-geodraw.png "graphicsmm\_geodraw")  
  
 さらに複雑な描画を作成するには、<xref:System.Windows.Media.DrawingGroup> を使用して、複数の描画オブジェクトを 1 つの複合描画に結合できます。  
  
## 参照  
 <xref:System.Windows.Media.DrawingGroup>   
 [Drawing オブジェクトの概要](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)   
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [複合描画を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-drawing.md)