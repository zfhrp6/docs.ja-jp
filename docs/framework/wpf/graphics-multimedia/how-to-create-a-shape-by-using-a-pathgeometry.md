---
title: "方法 : PathGeometry を使用して図形を作成する | Microsoft Docs"
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
  - "クラス, PathGeometry"
  - "グラフィックス [WPF], 形状"
  - "PathGeometry クラス"
  - "形状, 作成 (PathGeometry クラスを使用して)"
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: 11
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 11
---
# 方法 : PathGeometry を使用して図形を作成する
この例では、<xref:System.Windows.Media.PathGeometry> クラスを使用して図形を作成する方法を示します。  <xref:System.Windows.Media.PathGeometry> オブジェクトは 1 つ以上の <xref:System.Windows.Media.PathFigure> オブジェクトで構成され、各 <xref:System.Windows.Media.PathFigure> は異なる "形状" または図形を表します。  各 <xref:System.Windows.Media.PathFigure> 自体は 1 つ以上の <xref:System.Windows.Media.PathSegment> オブジェクトで構成されており、このオブジェクトは形状または図形の接続されている部分を表します。  セグメントの種類には、<xref:System.Windows.Media.LineSegment>、<xref:System.Windows.Media.ArcSegment>、<xref:System.Windows.Media.BezierSegment> などがあります。  
  
## 使用例  
 次の例は、<xref:System.Windows.Media.PathGeometry> を使用して三角形を作成しています。  <xref:System.Windows.Media.PathGeometry> は <xref:System.Windows.Shapes.Path> 要素を使用して表示されています。  
  
 [!code-xml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 前の例で作成した図を次に示します。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.png "wcpsdk\_graphicsmm\_pathgeometry\_triangle")  
PathGeometry で作成された三角形  
  
 前の例では、比較的単純な図形である三角形の作成方法を示しました。  <xref:System.Windows.Media.PathGeometry> を使用すると、円弧や曲線などのさらに複雑な図形も作成できます。  「[楕円の円弧を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)」、「[3 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)」、および「[2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)」の例を参照してください。  
  
 この例は、より大きなサンプルの一部です。サンプル全体については、[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)を参照してください。  
  
## 参照  
 <xref:System.Windows.Shapes.Path>   
 <xref:System.Windows.Media.GeometryDrawing>   
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)