---
title: "方法 : PathGeometry を使用して図形を作成する"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- shapes [WPF], creating with PathGeometry class
- graphics [WPF], shapes
ms.assetid: 49a4a8b7-e738-45be-8dac-b54a6d8f5b21
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 784a8df792ca4dc05e36f5b7e9ec93b02e0e639f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: ja-JP
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-shape-by-using-a-pathgeometry"></a><span data-ttu-id="826f4-102">方法 : PathGeometry を使用して図形を作成する</span><span class="sxs-lookup"><span data-stu-id="826f4-102">How to: Create a Shape by Using a PathGeometry</span></span>
<span data-ttu-id="826f4-103">この例を使用して、図形を作成する方法を示しています、<xref:System.Windows.Media.PathGeometry>クラスです。</span><span class="sxs-lookup"><span data-stu-id="826f4-103">This example shows how to create a shape using the <xref:System.Windows.Media.PathGeometry> class.</span></span> <span data-ttu-id="826f4-104"><xref:System.Windows.Media.PathGeometry>1 つまたは複数のオブジェクトが構成される<xref:System.Windows.Media.PathFigure>オブジェクトです。 各<xref:System.Windows.Media.PathFigure>異なる"図"または図形を表します。</span><span class="sxs-lookup"><span data-stu-id="826f4-104"><xref:System.Windows.Media.PathGeometry> objects are composed of one or more <xref:System.Windows.Media.PathFigure> objects; each <xref:System.Windows.Media.PathFigure> represents a different "figure" or shape.</span></span> <span data-ttu-id="826f4-105">各<xref:System.Windows.Media.PathFigure>自体は 1 つ以上ので構成される<xref:System.Windows.Media.PathSegment>それぞれ図や図形の接続の部分を表すオブジェクトします。</span><span class="sxs-lookup"><span data-stu-id="826f4-105">Each <xref:System.Windows.Media.PathFigure> is itself composed of one or more <xref:System.Windows.Media.PathSegment> objects, each representing a connected portion of the figure or shape.</span></span> <span data-ttu-id="826f4-106">セグメントの種類には、 <xref:System.Windows.Media.LineSegment>、 <xref:System.Windows.Media.ArcSegment>、および<xref:System.Windows.Media.BezierSegment>です。</span><span class="sxs-lookup"><span data-stu-id="826f4-106">Segment types include <xref:System.Windows.Media.LineSegment>, <xref:System.Windows.Media.ArcSegment>, and <xref:System.Windows.Media.BezierSegment>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="826f4-107">例</span><span class="sxs-lookup"><span data-stu-id="826f4-107">Example</span></span>  
 <span data-ttu-id="826f4-108">次の例では、<xref:System.Windows.Media.PathGeometry>三角形を作成します。</span><span class="sxs-lookup"><span data-stu-id="826f4-108">The following example uses a <xref:System.Windows.Media.PathGeometry> to create a triangle.</span></span> <span data-ttu-id="826f4-109"><xref:System.Windows.Media.PathGeometry>を使用して、表示、<xref:System.Windows.Shapes.Path>要素。</span><span class="sxs-lookup"><span data-stu-id="826f4-109">The  <xref:System.Windows.Media.PathGeometry> is displayed using a <xref:System.Windows.Shapes.Path> element.</span></span>  
  
 [!code-xaml[GeometrySample#49](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GeometrySample/CS/pathgeometryexample.xaml#49)]  
  
 <span data-ttu-id="826f4-110">前の例で作成した図を次に示します。</span><span class="sxs-lookup"><span data-stu-id="826f4-110">The following illustration shows the shape created in the previous example.</span></span>  
  
 <span data-ttu-id="826f4-111">![PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span><span class="sxs-lookup"><span data-stu-id="826f4-111">![A PathGeometry](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-pathgeometry-triangle.gif "wcpsdk_graphicsmm_pathgeometry_triangle")</span></span>  
<span data-ttu-id="826f4-112">PathGeometry で作成された三角形</span><span class="sxs-lookup"><span data-stu-id="826f4-112">A triangle created with a PathGeometry</span></span>  
  
 <span data-ttu-id="826f4-113">前の例では、比較的単純な図形、三角形を作成する方法を示しました。</span><span class="sxs-lookup"><span data-stu-id="826f4-113">The previous example showed how to create a relatively simple shape, a triangle.</span></span> <span data-ttu-id="826f4-114">A<xref:System.Windows.Media.PathGeometry>円弧、曲線などのより複雑な図形を作成するためにも使用します。</span><span class="sxs-lookup"><span data-stu-id="826f4-114">A <xref:System.Windows.Media.PathGeometry> can also be used to create more complex shapes, including arcs and curves.</span></span> <span data-ttu-id="826f4-115">例については、次を参照してください。[楕円の円弧を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md)、 [3 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md)、および[2 次ベジエ曲線を作成する](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md)です。</span><span class="sxs-lookup"><span data-stu-id="826f4-115">For examples, see [Create an Elliptical Arc](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-an-elliptical-arc.md), [Create a Cubic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-cubic-bezier-curve.md), and [Create a Quadratic Bezier Curve](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-quadratic-bezier-curve.md).</span></span>  
  
 <span data-ttu-id="826f4-116">この例は、より大きなサンプルの一部です。完全なサンプルについては、「[ジオメトリのサンプル](http://go.microsoft.com/fwlink/?LinkID=159989)」を参照してください。</span><span class="sxs-lookup"><span data-stu-id="826f4-116">This example is part of larger sample; for the complete sample, see the [Geometries Sample](http://go.microsoft.com/fwlink/?LinkID=159989).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="826f4-117">参照</span><span class="sxs-lookup"><span data-stu-id="826f4-117">See Also</span></span>  
 <xref:System.Windows.Shapes.Path>  
 <xref:System.Windows.Media.GeometryDrawing>  
 [<span data-ttu-id="826f4-118">ジオメトリの概要</span><span class="sxs-lookup"><span data-stu-id="826f4-118">Geometry Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/geometry-overview.md)  
 [<span data-ttu-id="826f4-119">ジオメトリのサンプル</span><span class="sxs-lookup"><span data-stu-id="826f4-119">Geometries Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159989)
