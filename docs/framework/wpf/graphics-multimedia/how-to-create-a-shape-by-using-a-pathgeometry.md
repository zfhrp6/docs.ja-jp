---
title: '方法 : PathGeometry を使用して図形を作成する'
ms.date: 03/30/2017
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
ms.openlocfilehash: 6c77844b054dd89a0c3f3cbecd0725968df9ae71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560183"
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a>方法 : PathGeometry を使用して図形を作成する
この例を使用して、図形を作成する方法を示しています、<xref:System.Windows.Media.PathGeometry>クラスです。 <xref:System.Windows.Media.PathGeometry> 1 つまたは複数のオブジェクトが構成される<xref:System.Windows.Media.PathFigure>オブジェクトです。 各<xref:System.Windows.Media.PathFigure>異なる"図"または図形を表します。 各<xref:System.Windows.Media.PathFigure>自体は 1 つ以上ので構成される<xref:System.Windows.Media.PathSegment>それぞれ図や図形の接続の部分を表すオブジェクトします。 セグメントの種類には、 <xref:System.Windows.Media.LineSegment>、 <xref:System.Windows.Media.ArcSegment>、および<xref:System.Windows.Media.BezierSegment>です。  
  
## <a name="example"></a>例  
 次の例では、<xref:System.Windows.Media.PathGeometry>三角形を作成します。 <xref:System.Windows.Media.PathGeometry>を使用して、表示、<xref:System.Windows.Shapes.Path>要素。  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 前の例で作成した図を次に示します。  
  
 ![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")  
PathGeometry で作成された三角形  
  
 前の例では、比較的単純な図形、三角形を作成する方法を示しました。 A<xref:System.Windows.Media.PathGeometry>円弧、曲線などのより複雑な図形を作成するためにも使用します。 例については、次を参照してください。[楕円の円弧を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)、 [3 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)、および[2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)です。  
  
 この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。  
  
## <a name="see-also"></a>関連項目  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [ジオメトリの概要](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)
