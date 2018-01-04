---
title: "方法 : RectangleGeometry を使用して四角形を定義する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [WPF], rectangles
- rectangles [WPF], creating with RectangleGeometry class
ms.assetid: e40b8a8e-54b8-416b-a9f2-be6dca9fdf0b
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3a8254bd60da379d006bc50ab3a935cd83b83d0a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-define-a-rectangle-using-a-rectanglegeometry"></a>方法 : RectangleGeometry を使用して四角形を定義する
この例を使用する方法を説明する、<xref:System.Windows.Media.RectangleGeometry>四角形を記述するクラス。  
  
## <a name="example"></a>例  
 次の例は、作成して表示する方法を示しています、<xref:System.Windows.Media.RectangleGeometry>です。  相対的な位置と四角形の寸法がによって定義されている、<xref:System.Windows.Rect>構造体。 相対の位置は`50,50`高さと幅の両方が、`25`正方形を作成します。 四角形の内部を描画すると、<xref:System.Windows.Media.Brushes.LemonChiffon%2A>でペイント ブラシ、アウトライン、<xref:System.Windows.Media.Brushes.Black%2A>ストロークの太さを`1`です。  
  
 [!code-xaml[GeometryOverviewSamples_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_snip/CS/GeometryExamples.xaml#graphicsmmrectanglegeometryexample)]  
  
 [!code-csharp[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/CSharp/GeometryExamples.cs#graphicsmmrectanglegeometryexample)]
 [!code-vb[GeometryOverviewSamples_procedural_snip#GraphicsMMRectangleGeometryExample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GeometryOverviewSamples_procedural_snip/visualbasic/geometryexamples.vb#graphicsmmrectanglegeometryexample)]  
  
 ![RectangleGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rectangle.gif "graphicsmm_rectangle")  
RectangleGeometry  
  
 この例を使用、<xref:System.Windows.Shapes.Path>要素を表示するために、<xref:System.Windows.Media.RectangleGeometry>を使用する他の多くの方法がある<xref:System.Windows.Media.RectangleGeometry>オブジェクト。 たとえば、<xref:System.Windows.Media.RectangleGeometry>を指定するために使用する、<xref:System.Windows.UIElement.Clip%2A>の<xref:System.Windows.UIElement>または<xref:System.Windows.Media.GeometryDrawing.Geometry%2A>の<xref:System.Windows.Media.GeometryDrawing>です。  
  
 その他の単純なジオメトリ クラスに含まれる<xref:System.Windows.Media.LineGeometry>と<xref:System.Windows.Media.EllipseGeometry>です。 複雑なものと同様にこれらの図形も作成できますを使用して、<xref:System.Windows.Media.PathGeometry>または<xref:System.Windows.Media.StreamGeometry>です。  
  
## <a name="see-also"></a>参照  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [複合図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-composite-shape.md)  
 [PathGeometry を使用して図形を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-shape-by-using-a-pathgeometry.md)
