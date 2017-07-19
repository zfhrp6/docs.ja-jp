---
title: "方法 : PathGeometry 内に複数のサブパスを作成する | Microsoft Docs"
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
  - "グラフィックス [WPF], サブパス"
  - "複数のサブパス"
  - "PathGeometry クラス"
  - "サブパス"
ms.assetid: 104a862c-dde2-4e62-ac87-80660dd1681c
caps.latest.revision: 9
author: "dotnet-bot"
ms.author: "dotnetcontent"
manager: "wpickett"
caps.handback.revision: 9
---
# 方法 : PathGeometry 内に複数のサブパスを作成する
この例では、<xref:System.Windows.Media.PathGeometry> 内に複数のサブパスを作成する方法を示します。  複数のサブパスを作成するには、サブパスごとに <xref:System.Windows.Media.PathFigure> を作成します。  
  
## 使用例  
 次の例では、それぞれが三角形の 2 つのサブパスを作成します。  
  
 [!code-xml[GeometrySample#38](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#38)]  
  
 <xref:System.Windows.Shapes.Path> と [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] の属性構文を使用して複数のサブパスを作成する方法を次の例に示します。  それぞれが三角形を描画する 2 つのサブパスが作成されるように、各 `M` が新しいサブパスを作成します。  
  
 [!code-xml[GeometrySample#58](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/geometryattributesyntaxexample.xaml#58)]  
  
 \(この属性構文は、実際には <xref:System.Windows.Media.PathGeometry> の軽量バージョンである <xref:System.Windows.Media.StreamGeometry> を作成します。  詳細については、「[パス マークアップ構文](../../../../docs/framework/wpf/graphics-multimedia/path-markup-syntax.md)」のページを参照してください。\)  
  
## 参照  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)