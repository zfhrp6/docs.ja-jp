---
title: "方法 : 複合図形を作成する | Microsoft Docs"
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
  - "複合図形"
  - "グラフィックス, 複合図形"
  - "形状, 複合"
ms.assetid: 8e5c7ef4-d7ed-4c43-afc9-ca01325c300b
caps.latest.revision: 10
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 10
---
# 方法 : 複合図形を作成する
この例では、<xref:System.Windows.Media.Geometry> オブジェクトを使用して複合図形を作成し、<xref:System.Windows.Shapes.Path> 要素を使用してこれらを表示する方法を示します。  次の例は、<xref:System.Windows.Media.LineGeometry>、<xref:System.Windows.Media.EllipseGeometry>、および <xref:System.Windows.Media.RectangleGeometry> を、<xref:System.Windows.Media.GeometryGroup> と共に使用して、複合図形を作成します。  次に、<xref:System.Windows.Shapes.Path> 要素を使用してジオメトリを描画します。  
  
## 使用例  
 [!code-xml[GeometrySample#19](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#19)]  
  
 [!code-csharp[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/CSharp/CompositeShapeExample.cs#compositeshapecodeexampleinline1)]
 [!code-vb[GeometriesMiscSnippets_procedural_snip#CompositeShapeCodeExampleInline1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometriesMiscSnippets_procedural_snip/visualbasic/compositeshapeexample.vb#compositeshapecodeexampleinline1)]  
  
 前の例で作成した図を次に示します。  
  
 ![GeometryGroup を使用して作成された複合ジオメトリ](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-compositegeometryexample1.png "wcpsdk\_graphicsmm\_compositegeometryexample1")  
複合ジオメトリ  
  
 多角形や曲線のセグメントを持つ図形など、より複雑な図形は、<xref:System.Windows.Media.PathGeometry> を使用して作成できます。  <xref:System.Windows.Media.PathGeometry> を使用して図形を作成する方法の例については、「[PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)」を参照してください。  この例では <xref:System.Windows.Shapes.Path> 要素を使用して画面に図形をレンダリングしますが、<xref:System.Windows.Media.Geometry> オブジェクトも、<xref:System.Windows.Media.GeometryDrawing> または <xref:System.Windows.Media.DrawingContext> のコンテンツの記述に使用することができます。  またこれらは、クリッピングとヒット テストに使用することもできます。  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)を参照してください。