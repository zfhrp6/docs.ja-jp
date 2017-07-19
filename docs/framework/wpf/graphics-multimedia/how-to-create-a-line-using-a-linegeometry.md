---
title: "方法 : LineGeometry を使用して線を作成する | Microsoft Docs"
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
  - "クラス, LineGeometry"
  - "グラフィックス [WPF], 線"
  - "LineGeometry クラス"
ms.assetid: 41231b22-1f74-4c26-a8e7-a55b29f8f6bd
caps.latest.revision: 7
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 7
---
# 方法 : LineGeometry を使用して線を作成する
<xref:System.Windows.Media.LineGeometry> クラスを使用して線を記述する方法を次の例に示します。  <xref:System.Windows.Media.LineGeometry> は、始点と終点によって定義されます。  
  
## 使用例  
 <xref:System.Windows.Media.LineGeometry> オブジェクトを作成してレンダリングする方法の例を次に示します。  線をレンダリングするには、<xref:System.Windows.Shapes.Path> 要素を使用します。  線には領域がないので、<xref:System.Windows.Shapes.Path> オブジェクトの <xref:System.Windows.Shapes.Shape.Fill%2A> は指定しません。代わりに、<xref:System.Windows.Shapes.Shape.Stroke%2A> プロパティと <xref:System.Windows.Shapes.Shape.StrokeThickness%2A> プロパティを使用します。  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmlinegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmlinegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMLineGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmlinegeometryexample)]  
  
 ![LineGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-line.png "graphicsmm\_line")  
\(10,20\) から \(100,130\) まで描画された LineGeometry  
  
 その他の単純な図形座標クラスとして、<xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.EllipseGeometry> などがあります。  これらの図形座標およびさらに複雑な図形座標は、<xref:System.Windows.Media.PathGeometry> または <xref:System.Windows.Media.StreamGeometry> を使用して作成することもできます。  詳細については、「[ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)」を参照してください。  
  
## 参照  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [複合図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)