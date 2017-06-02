---
title: "方法 : 結合したジオメトリを作成する | Microsoft Docs"
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
  - "結合 (ジオメトリを)"
  - "ジオメトリ, 結合"
  - "グラフィックス, 結合 (ジオメトリを)"
ms.assetid: 54c3277c-6b6e-4b25-91be-fda0bbc706b4
caps.latest.revision: 8
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 8
---
# 方法 : 結合したジオメトリを作成する
この例では、ジオメトリを結合する方法を示します。  2 つのジオメトリを結合するには、<xref:System.Windows.Media.CombinedGeometry> オブジェクトを使用します。  このオブジェクトの <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> プロパティを、結合する 2 つのジオメトリに設定し、<xref:System.Windows.Media.CombinedGeometry.GeometryCombineMode%2A> プロパティを `Union`、`Intersect`、`Exclude`、または `Xor` に設定して、ジオメトリの結合方法を決定します。  
  
 2 つ以上のジオメトリから複合ジオメトリを作成するには、<xref:System.Windows.Media.GeometryGroup> を使用します。  
  
## 使用例  
 次の例では、<xref:System.Windows.Media.CombinedGeometry> は `Exclude` のジオメトリ結合モードで定義されています。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> は同じ半径の円として定義されていますが、中心は 50 ずれています。  
  
 [!code-xml[GeometrySample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#21)]  
  
 ![除外組み合わせモードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-exclude.png "mil\_task\_combined\_geometry\_exclude")  
Combined Geometry Exclude  
  
 次のマークアップでは、<xref:System.Windows.Media.CombinedGeometry> は `Intersect` の結合モードで定義されています。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> は同じ半径の円として定義されていますが、中心は 50 ずれています。  
  
 [!code-xml[GeometrySample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#22)]  
  
 ![交差組み合わせモードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-intersect.png "mil\_task\_combined\_geometry\_intersect")  
Combined Geometry Intersect  
  
 次のマークアップでは、<xref:System.Windows.Media.CombinedGeometry> は `Union` の結合モードで定義されています。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> は同じ半径の円として定義されていますが、中心は 50 ずれています。  
  
 [!code-xml[GeometrySample#23](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#23)]  
  
 ![結合組み合わせモードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-union.png "mil\_task\_combined\_geometry\_union")  
Combined Geometry Union  
  
 次のマークアップでは、<xref:System.Windows.Media.CombinedGeometry> は `Xor` の結合モードで定義されています。  <xref:System.Windows.Media.CombinedGeometry.Geometry1%2A> および <xref:System.Windows.Media.CombinedGeometry.Geometry2%2A> は同じ半径の円として定義されていますが、中心は 50 ずれています。  
  
 [!code-xml[GeometrySample#24](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/combininggeometriesexample.xaml#24)]  
  
 ![Xor 組み合わせモードの結果](../../../../docs/framework/wpf/graphics-multimedia/media/mil-task-combined-geometry-xor.png "mil\_task\_combined\_geometry\_xor")  
Combined Geometry Xor