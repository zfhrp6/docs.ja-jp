---
title: "方法 : 3 次ベジエ曲線を作成する | Microsoft Docs"
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
  - "ベジエ曲線, 3 次"
  - "作成, 3 次ベジエ曲線"
  - "3 次ベジエ曲線"
  - "曲線, 3 次ベジエ"
  - "グラフィックス, 3 次ベジエ曲線"
ms.assetid: 450a3a77-7c57-48b0-a008-0f6051add980
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 3 次ベジエ曲線を作成する
3 次ベジエ曲線を作成する方法を次の例に示します。  3 次ベジエ曲線を作成するには、<xref:System.Windows.Media.PathGeometry>、<xref:System.Windows.Media.PathFigure>、および <xref:System.Windows.Media.BezierSegment> の各クラスを使用します。  結果のジオメトリを表示するには、<xref:System.Windows.Shapes.Path> 要素を使用するか、<xref:System.Windows.Media.GeometryDrawing> または <xref:System.Windows.Media.DrawingContext> でジオメトリを使用します。  次の例では、3 次ベジエ曲線を \(10, 100\) から \(300, 100\) まで描画します。  曲線の制御点は \(100, 0\) と \(200, 200\) です。  
  
## 使用例  
 \[xaml\]  
  
 [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] では、省略されたマークアップ構文を使用してパスを記述できます。  
  
 [!code-xml[GeometrySample#53](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#53)]  
  
 \[xaml\]  
  
 [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] では、オブジェクト タグを使用して 3 次ベジエ曲線を描画することもできます。  次の例は、前の [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の例と同じです。  
  
 [!code-xml[GeometrySample#33](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#33)]  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)を参照してください。  
  
## 参照  
 [楕円の円弧を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)   
 [PathGeometry で LineSegment を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-linesegment-in-a-pathgeometry.md)   
 [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)   
 [2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)