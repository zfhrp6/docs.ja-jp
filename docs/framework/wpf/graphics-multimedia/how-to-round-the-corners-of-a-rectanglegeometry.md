---
title: "方法 : RectangleGeometry の角に丸みを付ける | Microsoft Docs"
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
  - "角, 丸め処理"
  - "グラフィックス, 丸み付け (RectangleGeometry の角の)"
  - "RectangleGeometry クラス, 丸み付け (角の)"
  - "丸み付け (RectangleGeometry の角の)"
ms.assetid: 926644bc-1357-4c0b-ac81-694bd090ae87
caps.latest.revision: 4
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 4
---
# 方法 : RectangleGeometry の角に丸みを付ける
<xref:System.Windows.Media.RectangleGeometry> の角に丸みを付けるには、<xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> プロパティと <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> プロパティに 0 より大きい値を設定します。  値が大きいほど、四角形の角は丸くなります。  
  
## 使用例  
 <xref:System.Windows.Media.RectangleGeometry.RadiusX%2A> と <xref:System.Windows.Media.RectangleGeometry.RadiusY%2A> の設定が異なる複数の <xref:System.Windows.Media.RectangleGeometry> オブジェクトを次の例に示します。  <xref:System.Windows.Media.RectangleGeometry> オブジェクトは、<xref:System.Windows.Shapes.Path> 要素を使用して表示されます。  
  
 [!code-xml[GeometryOverviewSamples_snip#GraphicsMMRoundedRectangleGeometryExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/RectangleGeometryRoundedCornerExample.xaml#graphicsmmroundedrectanglegeometryexamplewholepage)]  
  
 ![RadiusX&#47;RadiusY 設定が異なる四角形](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rounded.png "graphicsmm\_rounded")  
角を丸くした四角形  
  
## 参照  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)   
 [複合図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)   
 [PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)